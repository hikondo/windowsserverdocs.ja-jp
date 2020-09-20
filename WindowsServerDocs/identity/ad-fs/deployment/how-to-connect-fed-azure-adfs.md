---
title: Azure における Active Directory フェデレーション サービス | Microsoft Docs
description: このドキュメントでは、Azure に AD FS をデプロイして高可用性を確保する方法について説明します。
author: billmath
manager: mtillman
ms.assetid: 692a188c-badc-44aa-ba86-71c0e8074510
ms.topic: get-started-article
ms.date: 10/28/2018
ms.author: billmath
ms.openlocfilehash: a077a76814cc5ed99d4a1c0eb6c23584b22363e1
ms.sourcegitcommit: 5344adcf9c0462561a4f9d47d80afc1d095a5b13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2020
ms.locfileid: "90766755"
---
# <a name="deploying-active-directory-federation-services-in-azure"></a>Azure での Active Directory フェデレーション サービスのデプロイ
AD FS は、単純かつ安全な ID フェデレーションと Web シングル サインオン (SSO) 機能を実現します。 Azure AD または O365 とのフェデレーションによって、ユーザーはオンプレミスの資格情報を認証に使用し、クラウド内のあらゆるリソースにアクセスすることができます。 そのため、オンプレミスとクラウドの両方のリソースに確実にアクセスできるよう、AD FS インフラストラクチャには、高い可用性を確保することが重要となります。 AD FS を Azure にデプロイすると、必要な高可用性を最小限の手間で確保できます。
AD FS を Azure にデプロイする利点はいくつかありますが、その一部を以下に示します。

* **高可用性** - Azure の可用性セットを使用してインフラストラクチャに高い可用性を確保できます。
* **拡張が容易** - パフォーマンスを強化する必要がある場合、 Azure からの簡単なクリック操作で簡単に、より高性能なマシンに移行できます。
* **地域を越えた冗長性** - Azure Geo Redundancy によって地域を越えた世界規模での高可用性がインフラストラクチャに確保されます。
* **管理しやすい** - 高度に単純化された管理オプションが Azure ポータルに用意されているため、インフラストラクチャ管理の手間がかからず、ごく簡単に管理することができます。

## <a name="design-principles"></a>設計原則
![Deployment design](./media/how-to-connect-fed-azure-adfs/deployment.png)

上の図は、これから AD FS インフラストラクチャを Azure にデプロイしようとする場合に推奨される基本的なトポロジを示したものです。 このトポロジの各種コンポーネントの要点を以下に示します。

* **DC / ADFS サーバー**: ユーザー数が 1,000 人未満である場合、ドメイン コントローラーに AD FS ロールをインストールするだけでかまいません。 ドメイン コントローラーへのパフォーマンスの影響が懸念される場合や、ユーザー数が 1,000 人を超える場合は、単独のサーバーに AD FS をデプロイします。
* **WAP サーバー** : ユーザーが会社のネットワークに接続していないときでも AD FS に到達できるよう WAP (Web アプリケーション プロキシ) サーバーをデプロイする必要があります。
* **DMZ**: Web アプリケーション プロキシ サーバーは DMZ に配置し、DMZ と内部サブネットとの間の通信には TCP/443 アクセスのみを許可します。
* **ロード バランサー**: AD FS サーバーと Web アプリケーション プロキシ サーバーの高可用性を確保するために、AD FS サーバーには内部ロード バランサーの使用を、Web アプリケーション プロキシ サーバーには Azure Load Balancer の使用をそれぞれお勧めします。
* **可用性セット**: AD FS のデプロイに冗長性を確保するために、同様のワークロードを処理する複数の仮想マシンは、1 つの可用性セットとしてグループ化するようお勧めします。 このように構成されていれば、計画済みまたは計画外メンテナンスの間も、少なくとも 1 つの仮想マシンを使用できます。
* **ストレージ アカウント**: ストレージ アカウントは 2 つ用意することをお勧めします。 ストレージ アカウントが 1 つである場合、単一障害点が形成され、万一ストレージ アカウントがダウンした場合に、環境が利用できなくなる可能性があります。 ストレージ アカウントが 2 つあれば、障害系統ごとに 1 つのストレージ アカウントを関連付けることができます。
* **ネットワークの分離**: Web アプリケーション プロキシ サーバーは、単独の DMZ ネットワークにデプロイする必要があります。 1 つの仮想ネットワークを 2 つのサブネットに分割したうえで、分離したサブネットに Web アプリケーション プロキシ サーバーをデプロイすることができます。 単にネットワーク セキュリティ グループの設定をサブネットごとに構成し、その 2 つのサブネット間に必要な通信のみを許可してください。 以降、デプロイのシナリオに従って詳しく説明します。

## <a name="steps-to-deploy-ad-fs-in-azure"></a>AD FS を Azure にデプロイする手順
このセクションで取り上げる手順は、以下に示した AD FS インフラストラクチャを Azure にデプロイするうえでの指針を概説したものです。

### <a name="1-deploying-the-network"></a>1. ネットワークを展開する
既に述べたように、1 つの仮想ネットワークに 2 つのサブネットを作成するか、まったく異なる 2 つの仮想ネットワーク (VNet) を作成することができます。 この記事では、1 つの仮想ネットワークをデプロイして 2 つのサブネットに分割する方法について重点的に説明します。 現時点では、その方が簡単です。2 つの独立した VNet を使用した場合、通信に VNet 間ゲートウェイが必要となります。

**1.1 仮想ネットワークを作成する**

![Create virtual network](./media/how-to-connect-fed-azure-adfs/deploynetwork1.png)

Azure ポータルで仮想ネットワークを選択すると、その仮想ネットワークと 1 つのサブネットを 1 回のクリックですぐにデプロイできます。 INT サブネットも定義されて VM を追加する準備が整います。
次の手順でこのネットワークにもう 1 つのサブネット (DMZ サブネット) を追加します。 DMZ サブネットを作成するには、次の手順を実行するだけです。

* 新しく作成したネットワークを選択する
* プロパティからサブネットを選択する
* サブネット パネルで追加ボタンをクリックする
* サブネットの名前とアドレス空間情報を指定してサブネットを作成する

![Subnet](./media/how-to-connect-fed-azure-adfs/deploynetwork2.png)

![Subnet DMZ](./media/how-to-connect-fed-azure-adfs/deploynetwork3.png)

**1.2.ネットワーク セキュリティ グループを作成する**

ネットワーク セキュリティ グループ (NSG) には、仮想ネットワークの VM インスタンスに対するネットワーク トラフィックを許可または拒否する一連のアクセス制御リスト (ACL) 規則が含まれています。 NSG は、サブネットまたはそのサブネット内の個々の VM インスタンスと関連付けることができます。 NSG がサブネットに関連付けられている場合、ACL 規則はそのサブネット内のすべての VM インスタンスに適用されます。
このガイドでは、その目的上、内部ネットワーク用と DMZ 用の 2 つの NSG を作成します。 それぞれ NSG_INT と NSG_DMZ という名前を付けます。

![Create NSG](./media/how-to-connect-fed-azure-adfs/creatensg1.png)

NSG の作成直後に存在する受信規則と送信規則は、いずれも 0 個です。 それぞれのサーバー上にロールがインストールされ正しく動作する状態になってから、必要なセキュリティ レベルに従って受信規則と送信規則を作成することができます。

![Initialize NSG](./media/how-to-connect-fed-azure-adfs/nsgint1.png)

NSG の作成後、NSG_INT をサブネット INT に、NSG_DMZ をサブネット DMZ に関連付けます。 以下のスクリーンショットはその例です。

![NSG configure](./media/how-to-connect-fed-azure-adfs/nsgconfigure1.png)

* [サブネット] をクリックしてサブネットのパネルを開きます。
* NSG に関連付けるサブネットを選択します。

構成後の [サブネット] のパネルは次のように表示されている必要があります。

![Subnets after NSG](./media/how-to-connect-fed-azure-adfs/nsgconfigure2.png)

**1.3.オンプレミスへの接続を作成する**

Azure にドメイン コントローラー (DC) をデプロイするためには、オンプレミスとの接続が必要となります。 Azure には、オンプレミスのインフラストラクチャを Azure のインフラストラクチャに接続するためのさまざまな接続方法が用意されています。

* ポイント対サイト
* Virtual Network サイト間
* ExpressRoute

推奨されるのは、ExpressRoute を使用する方法です。 ExpressRoute を使用すると、Azure データセンターと、お客様のオンプレミスまたはコロケーション環境にあるインフラストラクチャとの間にプライベート接続を作成できます。 ExpressRoute 接続では、公共のインターネットを利用できません。 ExpressRoute 接続は一般的なインターネットでの接続よりも信頼性が高く、高速で、待ち時間が短く、セキュリティの高い接続を提供します。
ExpressRoute の使用をお勧めしますが、所属する組織に合った任意の接続方法を選ぶことができます。 ExpressRoute と ExpressRoute を使用した各種の接続方法の詳細については、「 [ExpressRoute の技術概要](/azure/expressroute/expressroute-introduction)」を参照してください。

### <a name="2-create-storage-accounts"></a>2. ストレージアカウントを作成する
高い可用性を維持し、1 つのストレージ アカウントへの依存を回避するために、ストレージ アカウントは 2 つ作成することができます。 可用性セットごとの 2 つのグループにマシンを分けたうえで、それぞれのグループに別個のストレージ アカウントを割り当てます。

![Create storage accounts](./media/how-to-connect-fed-azure-adfs/storageaccount1.png)

### <a name="3-create-availability-sets"></a>3. 可用性セットを作成する
それぞれのロール (DC/AD FS と WAP) について、最低 2 つのマシンを含んだ可用性セットを作成します。 そうすることで各ロールの可用性を高めることができます。
可用性セットを作成する際は、次の点についての意思決定が必須となります。

* **障害ドメイン**: 同じ障害ドメインの仮想マシンは、同じ電源と物理ネットワーク スイッチを共有します。 障害ドメインは 2 以上とすることをお勧めします。 ここでは既定値の 3 をそのまま使用します。
* **更新ドメイン**: 同じ更新ドメインに属しているマシンは、更新時に一緒に再起動されます。 更新ドメインは 2 以上とすることをお勧めします。 ここでは既定値の 5 をそのまま使用します。

![可用性セット](./media/how-to-connect-fed-azure-adfs/availabilityset1.png)

次の可用性セットを作成します。

| 可用性セット | ロール | 障害ドメイン | 更新ドメイン |
|:---:|:---:|:---:|:--- |
| contosodcset |DC/ADFS |3 |5 |
| contosowapset |WAP |3 |5 |

### <a name="4-deploy-virtual-machines"></a>4. 仮想マシンを展開する
次に、インフラストラクチャ内の各ロールのホストとなる仮想マシンをデプロイします。 それぞれの可用性セットには、最低でも 2 つのマシンをデプロイすることをお勧めします。 基本的なデプロイでは 4 つの仮想マシンを作成します。

| Machine | ロール | Subnet | 可用性セット | ストレージ アカウント | IP アドレス |
|:---:|:---:|:---:|:---:|:---:|:---:|
| contosodc1 |DC/ADFS |INT |contosodcset |contososac1 |Static |
| contosodc2 |DC/ADFS |INT |contosodcset |contososac2 |Static |
| contosowap1 |WAP |DMZ |contosowapset |contososac1 |Static |
| contosowap2 |WAP |DMZ |contosowapset |contososac2 |Static |

お気付きかもしれませんが、NSG が指定されていません。 これは NSG が、Azure ではサブネット レベルで使用できるためです。 マシンのネットワーク トラフィックは、サブネットまたは NIC オブジェクトに関連付けられている個々の NSG を使って制御できます。 詳しくは、「 [ネットワーク セキュリティ グループ (NSG) について](/azure/virtual-network/tutorial-filter-network-traffic)」をご覧ください。
DNS が管理下にある場合は、静的 IP アドレスをお勧めします。 Azure DNS を使用し、ドメインの DNS レコードの方から、対応する Azure FQDN で新しいマシンを参照することができます。
デプロイの完了後、[仮想マシン] ウィンドウは次のように表示されている必要があります。

![Virtual Machines deployed](./media/how-to-connect-fed-azure-adfs/virtualmachinesdeployed_noadfs.png)

### <a name="5-configuring-the-domain-controller--ad-fs-servers"></a>5. ドメインコントローラー/AD FS サーバーを構成する
 受信要求を認証するためには、AD FS がドメイン コントローラーに問い合わせを行う必要があります。 認証のたびに Azure がオンプレミスの DC とやり取りするのでは無駄が大きいため、ドメイン コントローラーのレプリカを Azure にデプロイすることをお勧めします。 高い可用性を確保するために、少なくとも 2 つのドメイン コントローラーから成る可用性セットを作成することをお勧めします。

| ドメイン コントローラー | ロール | ストレージ アカウント |
|:---:|:---:|:---:|
| contosodc1 |[レプリカ] |contososac1 |
| contosodc2 |[レプリカ] |contososac2 |

* 2 台のサーバーをレプリカ ドメイン コントローラー (DNS を含む) として昇格させます。
* サーバー マネージャーを使用して AD FS ロールをインストールし、AD FS サーバーを構成します。

### <a name="6-deploying-internal-load-balancer-ilb"></a>6. 内部 Load Balancer (ILB) を展開する
**6.1.ILB を作成する**

ILB をデプロイするには、Azure ポータルで [ロード バランサー] を選択し、[追加] \(+) をクリックします。

> [!NOTE]
> メニューに **[ロード バランサー]** が表示されない場合は、ポータルの左下にある **[参照]** をクリックし、**[ロード バランサー]** が表示されるまでスクロールします。  その後、黄色の星印をクリックするとメニューに追加されます。 この新しいロード バランサー アイコンを選択してパネルを開き、ロード バランサーの構成を開始してください。
>
>

![Browse load balancer](./media/how-to-connect-fed-azure-adfs/browseloadbalancer.png)

* **[名前]**: ロード バランサーに適切な名前を付けます。
* **スキーム**: このロードバランサーは AD FS サーバーの前に配置され、内部ネットワーク接続のみを目的としているため、[内部] を選択します。
* **[仮想ネットワーク]**: AD FS をデプロイする仮想ネットワークを選択します。
* **[サブネット]**: 内部サブネットを選択します。
* **IP アドレスの割り当て**: 静的

![内部ロード バランサー](./media/how-to-connect-fed-azure-adfs/ilbdeployment1.png)

[作成] をクリックして ILB をデプロイすると、その ILB がロード バランサーの一覧に表示されます。

![Load balancers after ILB](./media/how-to-connect-fed-azure-adfs/ilbdeployment2.png)

次の手順では、バックエンド プールとバックエンド プローブを構成します。

**6.2.ILB バックエンド プールを構成する**

新しく作成した ILB を [ロード バランサー] パネルで選択し、 設定パネルを開きます。

1. 設定パネルからバックエンド プールを選択します。
2. [バックエンド プールの追加] パネルで [仮想マシンの追加] をクリックします。
3. パネルが表示され、可用性セットを選択することができます。
4. AD FS の可用性セットを選択します。

![Configure ILB backend pool](./media/how-to-connect-fed-azure-adfs/ilbdeployment3.png)

**6.3.プローブを構成する**

[ILB 設定] パネルで [正常性プローブ] を選択します。

1. [追加] をクリックします。
2. プローブの詳細を入力します。a.  **[名前]**: プローブ名。b.  **[プロトコル]**: HTTP c.  **[ポート]**: 80 (HTTP) d.  **[パス]**: /adfs/probe e.  **[間隔]**: 5 (既定値) - この値は、ILB がバックエンド プール内の仮想マシンをプローブする間隔です。f.  **[Unhealthy threshold limit]\(異常しきい値\)**: 2 (既定値) - これはプローブ エラーの連続回数のしきい値です。この値を超えると、ILB はバックエンド プール内の仮想マシンが応答していないと判断し、トラフィックの送信を停止します。


完全な HTTPS パス チェックが実行できない AD FS 環境での正常性チェックには、明示的に作成された /adfs/probe エンドポイントを使用しています。  基本的なポート 443 チェックでは、最新の AD FS デプロイの状態が正確に反映されないため、この方が明らかに有利な方法といえます。  詳細については、https://blogs.technet.microsoft.com/applicationproxyblog/2014/10/17/hardware-load-balancer-health-checks-and-web-application-proxy-ad-fs-2012-r2/ を参照してください。

**6.4.負荷分散規則を作成する**

トラフィックのバランスを効果的に調整するためには、負荷分散規則を使って ILB を構成する必要があります。 負荷分散規則を作成するには、

1. ILB の設定パネルから負荷分散規則を選択します。
2. [負荷分散規則] パネルの [追加] をクリックします。
3. [負荷分散規則の追加] パネルで、a.  **[名前]**: 規則の名前を入力します。b.  **[プロトコル]**: [TCP] を選択します。c.  **[ポート]**: 443。d.  **[バックエンド ポート]**: 443。e.  **[バックエンド プール]**: AD FS クラスター用に作成しておいたプールを選択します。f.  **[プローブ]**: AD FS サーバー用に作成しておいたプローブを選択します。

![Configure ILB balancing rules](./media/how-to-connect-fed-azure-adfs/ilbdeployment5.png)

**6.5.DNS に ILB を反映する**

内部 DNS サーバーを使用して、ILB の A レコードを作成します。 A レコードは、IP アドレスが ILB の IP アドレスを指すフェデレーションサービス用である必要があります。 たとえば、ILB IP アドレスが10.3.0.8 で、インストールされているフェデレーションサービスが fs.contoso.com の場合、10.3.0.8 を指す fs.contoso.com の A レコードを作成します。
これにより、fs.contoso.com のすべてのデータ trasmitted が ILB で終了し、適切にルーティングされるようになります。

> [!WARNING]
> AD FS データベースに WID (Windows Internal Database) を使用している場合は、この値を一時的にプライマリ AD FS サーバーを指すように設定する必要があります。そうしないと、Web アプリケーションプロキシは enrollement に失敗します。 すべての Web Appplication プロキシサーバーを正常に登録したら、この DNS エントリをロードバランサーを指すように変更します。

> [!NOTE]
> デプロイでも IPv6 を使用している場合は、必ず対応する AAAA レコードを作成してください。
>

### <a name="7-configuring-the-web-application-proxy-server"></a>7. Web アプリケーションプロキシサーバーを構成する
**7.1.AD FS サーバーに到達するための構成を Web アプリケーション プロキシ サーバーに対して行う**

Web アプリケーション プロキシ サーバーが ILB の内側にある AD FS サーバーに到達するためには、%systemroot%\system32\drivers\etc\hosts にその ILB のレコードを作成する必要があります。 識別名 (DN) は、フェデレーション サービスの名前 (例: fs.contoso.com) となることに注意してください。 また、IP エントリは ILB の IP アドレス (例では 10.3.0.8) のものである必要があります。

> [!WARNING]
> AD FS データベースに WID (Windows Internal Database) を使用している場合は、この値を一時的にプライマリ AD FS サーバーをポイントするように設定する必要があります。そうしないと、Web アプリケーションプロキシは enrollement に失敗します。 すべての Web Appplication プロキシサーバーを正常に登録したら、この DNS エントリをロードバランサーを指すように変更します。


**7.2.Web アプリケーション プロキシ ロールをインストールする**

Web アプリケーション プロキシ サーバーから ILB の内側の AD FS サーバーに到達できる状態を確保したら、続けて Web アプリケーション プロキシ サーバーをインストールすることができます。
Web アプリケーション プロキシ サーバーは、ドメインに参加する必要はありません。 リモート アクセス ロールを選択して、2 つの Web アプリケーション プロキシ サーバーに Web アプリケーション プロキシ ロールをインストールします。 サーバー マネージャーの指示に従って、WAP のインストールを実行してください。
WAP のデプロイ方法について詳しくは、「 [Web アプリケーション プロキシ サーバーをインストールし、構成する](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383662(v=ws.11))」をご覧ください。

### <a name="8--deploying-the-internet-facing-public-load-balancer"></a>8. インターネットに接続する (パブリック) Load Balancer を展開する
**8.1. インターネットに接続された (パブリック) Load Balancer を作成する**

Azure ポータルで [ロード バランサー] を選択し、[追加] をクリックします。 [ロード バランサーの作成] パネルで次の情報を入力します。

1. **[名前]**: ロード バランサーの名前。
2. **[スキーム]**: [パブリック] - このオプションを選択することで、作成するロード バランサーにパブリック アドレスが必要であるという情報が Azure に提供されます。
3. **[IP アドレス]**: 新しい IP アドレス (動的) を作成します。

![インターネットに接続するロード バランサー](./media/how-to-connect-fed-azure-adfs/elbdeployment1.png)

デプロイしたロード バランサーは、[ロード バランサー] の一覧に表示されます。

![Load balancer list](./media/how-to-connect-fed-azure-adfs/elbdeployment2.png)

**8.2.パブリック IP に DNS ラベルを割り当てる**

新しく作成したロード バランサーのエントリを [ロード バランサー] パネルでクリックして、構成用のパネルを表示します。 次の手順に従ってパブリック IP の DNS ラベルを構成してください。

1. 対象のパブリック IP アドレスをクリックします。 パブリック IP とその設定に必要なパネルが開きます。
2. [構成] をクリックします。
3. DNS ラベルを指定します。 これが、任意の場所からアクセスできるパブリック DNS ラベルになります (例: contosofs.westus.cloudapp.azure.com)。 外部 DNS には、この外部ロード バランサーの DNS ラベル (contosofs.westus.cloudapp.azure.com) に解決されるフェデレーション サービスのエントリ (例: fs.contoso.com) を追加してください。

![Configure internet facing load balancer](./media/how-to-connect-fed-azure-adfs/elbdeployment3.png)

![Configure internet facing load balancer (DNS)](./media/how-to-connect-fed-azure-adfs/elbdeployment4.png)

**8.3.インターネット接続 (パブリック) ロード バランサーのバックエンド プールを構成する**

内部ロード バランサーの作成と同じ手順に従って、インターネット接続 (パブリック) ロード バランサーのバックエンド プールを WAP サーバーの可用性セットとして構成します。 たとえば「contosowapset」とします。

![Configure backend pool of Internet Facing Load Balancer](./media/how-to-connect-fed-azure-adfs/elbdeployment5.png)

**8.4.プローブを構成する**

内部ロード バランサーの構成と同じ手順に従って、WAP サーバーのバックエンド プールに使用するプローブを構成します。

![Configure probe of Internet Facing Load Balancer](./media/how-to-connect-fed-azure-adfs/elbdeployment6.png)

**8.5.負荷分散規則を作成する**

ILB と同じ手順に従って、TCP 443 の負荷分散規則を構成します。

![Configure balancing rules of Internet Facing Load Balancer](./media/how-to-connect-fed-azure-adfs/elbdeployment7.png)

### <a name="9-securing-the-network"></a>9. ネットワークをセキュリティで保護する
**9.1.内部サブネットを保護する**

内部サブネットを効率的に保護するには、一般に次の規則が (以下に記載された順序で) 必要となります。

| ルール | 説明 | Flow |
|:--- |:--- |:---:|
| AllowHTTPSFromDMZ |DMZ からの HTTPS 通信を許可します。 |着信 |
| DenyInternetOutbound |インターネットへのアクセスを禁止します。 |送信 |

![INT access rules (inbound)](./media/how-to-connect-fed-azure-adfs/nsg_int.png)

**9.2.DMZ サブネットを保護する**

| ルール | 説明 | Flow |
|:--- |:--- |:---:|
| AllowHTTPSFromInternet |インターネットから DMZ への HTTPS を許可します。 |着信 |
| DenyInternetOutbound |インターネットへの通信は HTTPS を除きすべてブロックします。 |送信 |

![EXT access rules (inbound)](./media/how-to-connect-fed-azure-adfs/nsg_dmz.png)

> [!NOTE]
> クライアントユーザー証明書認証 (x.509 ユーザー証明書を使用した clientTLS 認証) が必要な場合、AD FS は、受信アクセスに対して TCP ポート49443を有効にする必要があります。
>
>

### <a name="10-test-the-ad-fs-sign-in"></a>10. AD FS サインインをテストする
AD FS のテストは、IdpInitiatedSignon.aspx ページを使用して行うのが最も簡単です。 そのためには、AD FS のプロパティで IdpInitiatedSignOn を有効にする必要があります。 以下の手順に従って AD FS の設定を確認してください。

1. AD FS サーバーで PowerShell から以下のコマンドレットを実行し、このプロパティを有効にします。
   Set-AdfsProperties -EnableIdPInitiatedSignonPage $true
2. 外部のコンピューターから https:\//adfs-server.contoso.com/adfs/ls/IdpInitiatedSignon.aspx にアクセスします。
3. 以下の AD FS ページが表示されたら成功です。

![Test login page](./media/how-to-connect-fed-azure-adfs/test1.png)

サインインに成功すると、その旨のメッセージが表示されます (下図)。

![Test success](./media/how-to-connect-fed-azure-adfs/test2.png)

## <a name="template-for-deploying-ad-fs-in-azure"></a>Azure で AD FS をデプロイするためのテンプレート
このテンプレートでは、ドメイン コントローラー、AD FS、WAP にそれぞれ 2 つずつ使用する、6 つのマシンのセットアップをデプロイします。

[Azure での AD FS のデプロイ テンプレート](https://github.com/paulomarquesc/adfs-6vms-regular-template-based)

このテンプレートのデプロイ中、既存の仮想ネットワークを使用するか、新しい VNET を作成できます。 デプロイをカスタマイズするために使用できる各種のパラメーターについて、デプロイ プロセスにおけるパラメーターの使用方法の説明と共に次の一覧に記載します。

| パラメーター | 説明 |
|:--- |:--- |
| 場所 |リソースのデプロイ先となるリージョン (例: 米国東部) |
| StorageAccountType |作成するストレージ アカウントの種類 |
| VirtualNetworkUsage |新しい仮想ネットワークを作成するか既存のものを使用するかを示します |
| VirtualNetworkName |作成する仮想ネットワークの名前 (新しい仮想ネットワークを使用する場合と既存のものを使用する場合の両方で必須) |
| VirtualNetworkResourceGroupName |既存の仮想ネットワークが存在するリソース グループの名前を指定します。 これは、既存の仮想ネットワークを使用している場合、既存の仮想ネットワークの ID がデプロイによって検出されるようにするための必須のパラメーターになります |
| VirtualNetworkAddressRange |新しい VNET のアドレス範囲 (新しい仮想ネットワークを作成する場合は必須) |
| InternalSubnetName |内部サブネットの名前 (新しい仮想ネットワークと既存の仮想ネットワークの両方で必須) |
| InternalSubnetAddressRange |ドメイン コントローラーと ADFS サーバーが含まれる内部サブネットのアドレス範囲 (新しい仮想ネットワークを作成する場合は必須) |
| DMZSubnetAddressRange |Windows アプリケーション プロキシ サーバーが含まれる DMZ サブネットのアドレス範囲 (新しい仮想ネットワークを作成する場合は必須) |
| DMZSubnetName |内部サブネットの名前 (新しい仮想ネットワークと既存の仮想ネットワークの両方で必須) |
| ADDC01NICIPAddress |最初のドメイン コントローラーの内部 IP アドレス。DC に静的に割り当てられるこの IP アドレスは、内部サブネットで有効な IP アドレスである必要があります |
| ADDC02NICIPAddress |2 番目のドメイン コントローラーの内部 IP アドレス。DC に静的に割り当てられるこの IP アドレスは、内部サブネットで有効な IP アドレスである必要があります |
| ADFS01NICIPAddress |最初の ADFS サーバーの内部 IP アドレス。ADFS サーバーに静的に割り当てられるこの IP アドレスは、内部サブネットで有効な IP アドレスである必要があります |
| ADFS02NICIPAddress |2 番目の ADFS サーバーの内部 IP アドレス。ADFS サーバーに静的に割り当てられるこの IP アドレスは、内部サブネットで有効な IP アドレスである必要があります |
| WAP01NICIPAddress |最初の WAP サーバーの内部 IP アドレス。WAP サーバーに静的に割り当てられるこの IP アドレスは、DMZ サブネットで有効な IP アドレスである必要があります |
| WAP02NICIPAddress |2 番目の WAP サーバーの内部 IP アドレス。WAP サーバーに静的に割り当てられるこの IP アドレスは、DMZ サブネットで有効な IP アドレスである必要があります |
| ADFSLoadBalancerPrivateIPAddress |ADFS ロード バランサーの内部 IP アドレス。ロード バランサーに静的に割り当てられるこの IP アドレスは、内部サブネットで有効な IP アドレスである必要があります |
| ADDCVMNamePrefix |ドメイン コントローラーの仮想マシン名のプレフィックス |
| ADFSVMNamePrefix |ADFS サーバーの仮想マシン名のプレフィックス |
| WAPVMNamePrefix |WAP サーバーの仮想マシン名のプレフィックス |
| ADDCVMSize |ドメイン コントローラーの VM サイズ |
| ADFSVMSize |ADFS サーバーの VM サイズ |
| WAPVMSize |WAP サーバーの VM サイズ |
| AdminUserName |仮想マシンのローカル管理者の名前 |
| AdminPassword |仮想マシンのローカル管理者アカウントのパスワード |

## <a name="additional-resources"></a>その他の技術情報
* [可用性セット](https://aka.ms/Azure/Availability)
* [Azure Load Balancer](/azure/load-balancer/load-balancer-overview)
* [内部 Load Balancer](/azure/load-balancer/quickstart-load-balancer-standard-internal-powershell)
* [インターネットに接続する Load Balancer](/azure/load-balancer/quickstart-load-balancer-standard-public-powershell)
* [ストレージ アカウント](https://aka.ms/Azure/Storage)
* [Azure 仮想ネットワーク](/azure/virtual-network/virtual-networks-overview)
* [AD FS と Web アプリケーション プロキシについてのリンク](/archive/blogs/tangent_thoughts/qrg-quick-reference-guide-active-directory-federation-services)

## <a name="next-steps"></a>次のステップ
* [オンプレミス ID と Azure Active Directory の統合](/azure/active-directory/hybrid/whatis-hybrid-identity)
* [Azure AD Connect を使用した AD FS の構成と管理](/azure/active-directory/hybrid/how-to-connect-fed-whatis)
* [Azure Traffic Manager を使用した Azure への可用性に優れた地域間 AD FS デプロイ](active-directory-adfs-in-azure-with-azure-traffic-manager.md)