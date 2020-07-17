---
title: 手順 2-高度な DirectAccess 展開を計画する
description: このトピックは、「Windows Server 2016 の詳細設定を使用して単一の DirectAccess サーバーを展開する」の一部です。
manager: brianlic
ms.prod: windows-server
ms.technology: networking-da
ms.topic: article
ms.assetid: 3bba28d4-23e2-449f-8319-7d2190f68d56
ms.author: lizross
author: eross-msft
ms.openlocfilehash: cf17c7f1349d5b3ee5b3efe0a872dd433ecbfe8d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80819576"
---
# <a name="step-2-plan-advanced-directaccess-deployments"></a>手順 2-高度な DirectAccess 展開を計画する

>適用対象: Windows Server (半期チャネル)、Windows Server 2016

DirectAccess インフラストラクチャの計画後、IPv4 と IPv6 を使用した単一サーバーでの高度な DirectAccess 展開の次の手順は、リモート アクセスのセットアップ ウィザードの設定の計画です。  
  
|タスク|説明|  
|----|--------|  
|[2.1 クライアント展開の計画](#21-plan-for-client-deployment)|DirectAccess を使用して、クライアント コンピューターに接続を許可する方法を計画します。 DirectAccess クライアントとして構成する管理対象のコンピューターを決定し、クライアント コンピューターへの Network Connectivity Assistant または DirectAccess Connectivity Assistant の展開を計画します。|  
|[2.2 DirectAccess サーバーの展開計画](#22-plan-for-directaccess-server-deployment)|DirectAccess サーバーの展開方法を計画します。|  
|[2.3 インフラストラクチャサーバーを計画する](#23-plan-infrastructure-servers)|DirectAccess ネットワーク ロケーション サーバー、ドメイン ネーム システム (DNS) サーバー、DirectAccess 管理サーバーを含む、DirectAccess 展開向けのインフラストラクチャ サーバーを計画します。|  
|[2.4 アプリケーションサーバーを計画する](#24-plan-application-servers)|IPv4 および IPv6 アプリケーション サーバーを計画し、必要に応じて、DirectAccess クライアント コンピューターと内部アプリケーション サーバーの間にエンド ツー エンド認証が必要かどうかを検討します。|  
|[2.5 DirectAccess とサードパーティ VPN クライアントを計画する](#25-plan-directaccess-and-third-party-vpn-clients)|サードパーティ VPN クライアントで DirectAccess を展開する場合、レジストリ値を設定して、2 つのリモート アクセス ソリューションのシームレスな共存を有効にする必要がある場合があります。|  
  
## <a name="21-plan-for-client-deployment"></a>2.1 クライアント展開を計画する  
クライアント展開を計画しているときに、決定すべきことが 3 つあります。  
  
1.  DirectAccess をモバイル コンピューターのみから使用できるようにするか、すべてのコンピューターから使用できるようにするか  
  
    DirectAccess クライアントのセットアップ ウィザードで DirectAccessクライアントを構成すると、指定したセキュリティ グループのモバイル コンピューターのみに DirectAccess を使用した接続を許可する選択が可能です。 アクセスをモバイル コンピューターに制限する場合、リモート アクセスによって自動的に WMI フィルターが構成され、DirectAccess クライアント GPO が指定したセキュリティ グループのモバイル コンピューターにのみ適用されるようになります。 リモート アクセス管理者がこの設定を有効にするには、グループ ポリシー オブジェクト (GPO) WMI フィルターを作成または変更するために、作成、または変更のセキュリティのアクセス許可が必要です。  
  
2.  どのセキュリティ グループに DirectAccess クライアント コンピューターを含めるか  
  
    DirectAccess クライアント設定は、DirectAccess クライアント GPO に含まれています。 GPO は、DirectAccess クライアントのセットアップ ウィザードで指定したセキュリティ グループに含まれるコンピューターに適用されます。 セキュリティ グループは、サポートされるドメインに含まれるように指定できます。 詳細については、「 [1.7 Plan Active Directory Domain Services](da-adv-plan-s1-infrastructure.md#17-plan-active-directory-domain-services)」セクションを参照してください。  
  
    DirectAccess を構成する前に、セキュリティ グループを作成する必要があります。 DirectAccess 展開を完了した後で、コンピューターをセキュリティ グループに追加できますが、セキュリティ グループとは別のドメインにあるクライアント コンピューターを追加する場合、クライアント GPO はこれらのクライアントには適用されません。 たとえば、DirectAccess クライアントに対して、ドメイン A で SG 1 を作成し、ドメイン B からのクライアントを後でこのグループに追加した場合、クライアント GPO はドメイン B からのクライアントには適用されません。この問題を回避するには、DirectAccess クライアント コンピューターを含む各ドメイン向けに新しいクライアント セキュリティ グループを作成します。 または、新しいセキュリティ グループを作成しない場合は、Windows PowerShell コマンドレット **Add-DAClient** を新しいドメインの新しい GPO の名前で実行します。  
  
3.  Network Connectivity Assistant にどのような設定を構成するか  
  
    Network Connectivity Assistant はクライアント コンピューターで実行され、エンド ユーザーへの DirectAccess 接続に関する追加情報を提供します。 DirectAccess クライアントのセットアップ ウィザードで、次の構成が可能です。  
  
    -   **接続検証方法**  
  
        クライアントが内部ネットワークへの接続の検証に使用する既定の Web プローブが作成されます。 既定の名前は次のとおりです。  
  
        https://directaccess-WebProbeHost.<domain_name>  
  
        この名前は手動で DNS に登録する必要があります。 HTTP または **ping** で、その他の Web アドレスを使用して、その他の接続検証方法を作成できます。 接続検証方法ごとに、DNS エントリが存在している必要があります。  
  
    -   **ヘルプデスクの電子メールアドレス**  
  
        DirectAccess 接続の問題が発生した場合、エンド ユーザーは、DirectAccess 管理者による問題のトラブルシューティング用に診断情報が含まれた電子メールを送信できます。  
  
    -   **DirectAccess 接続名**  
  
        エンド ユーザーがコンピューターで DirectAccess 接続を識別できるように、DirectAccess 接続名を指定します。  
  
    -   **DirectAccess クライアントでローカルの名前解決を使用できるようにする**  
  
        クライアントには名前をローカルで解決する方法が必要です。 DirectAccess クライアントにローカルでの名前解決を許可すると、エンド ユーザーはローカル DNS サーバーを使用して名前を解決できます。 エンド ユーザーが名前解決にローカル DNS サーバーの使用を選択すると、DirectAccess は単一のラベル名に対する解決要求を企業内部 DNS サーバーに送信しません。 代わりに (リンク ローカル マルチキャスト名前解決 (LLMNR) と NetBIOS over TCP/IP プロトコルを使用して) ローカルの名前解決を使用します。  
  
## <a name="22-plan-for-directaccess-server-deployment"></a>2.2 DirectAccess サーバー展開を計画する  
DirectAccess サーバーの展開を計画している場合は、次の決定項目を考慮してください。  
  
-   **ネットワークトポロジ**  
  
    DirectAccess サーバーの展開に使用できるトポロジはいくつかあります。  
  
    -   **2 つのネットワーク アダプター**します。 2 つのネットワーク アダプターを使用して、DirectAccess はインターネットに直接接続するネットワーク アダプターと、内部ネットワークに接続するもう 1 つのネットワーク アダプターで構成できます。 または、サーバーはファイアウォールやルーターなどのエッジ デバイスの内側にインストールされます。 この構成では、1 つのネットワーク アダプターが境界ネットワークに接続され、もう 1 つのネットワーク アダプターが内部ネットワークに接続されます。  
  
    -   **1 つのネットワーク アダプター**: この構成では、DirectAccess サーバーはファイアウォールやルーターなどのエッジ デバイスの内側にインストールされます。 ネットワーク アダプターは内部ネットワークに接続します。  
  
    デプロイのトポロジの選択の詳細については、「 [1.1 ネットワークトポロジと設定を計画](da-adv-plan-s1-infrastructure.md#11-plan-network-topology-and-settings)する」を参照してください。  
  
-   **ConnectTo アドレス**  
  
    クライアント コンピューターは ConnectTo アドレスを使用して、DirectAccess サーバーに接続します。 選択したアドレスは、IP-HTTPS 接続に展開する IP-HTTPS 証明書のサブジェクト名と一致していて、パブリック DNS で使用できる必要があります。  
  
-   **ネットワーク アダプター**  
  
    リモート アクセス サーバーのセットアップ ウィザードは、DirectAccess サーバー上で構成されたネットワーク アダプターを自動的に検出します。 正しいアダプターが選択されていることを確認する必要があります。  
  
-   **Ip-https 証明書**  
  
    リモート アクセス サーバーのセットアップ ウィザードは、IP-HTTPS 接続に適した証明書を自動的に検出します。 選択した証明書のサブジェクト名は、ConnectTo アドレスと一致している必要があります。 自己署名証明書を使用している場合は、リモート アクセス サーバーで自動的に作成された証明書を使用するように選択できます。  
  
-   **IPv6 プレフィックス**  
  
    リモート アクセス サーバーのセットアップ ウィザードで、ネットワーク アダプターに IPv6 が展開されていることが検出された場合、内部ネットワーク向けの IPv6 プレフィックス、DirectAccess クライアント コンピューターに割り当てられる IPv6 プレフィックス、VPN クライアント コンピューターに割り当てられる IPv6 プレフィックスが自動的に設定されます。 自動的に生成されたプレフィックスがネイティブ IPv6 インフラストラクチャ向けに適切でない場合は、手動で変更する必要があります。 詳細については、「 [1.1 ネットワークトポロジと設定を計画](da-adv-plan-s1-infrastructure.md#11-plan-network-topology-and-settings)する」を参照してください。  
  
-   **[認証]**  
  
    DirectAccess クライアントが DirectAccess サーバーを認証する方法を決定します。  
  
    -   **[ユーザー認証]** : ユーザーが Active Directory 資格情報、または 2 要素認証を使用して認証できるようにします。 2要素認証を使用した認証の詳細については、「 [OTP 認証を使用したリモートアクセスの展開](https://technet.microsoft.com/library/hh831379.aspx)」を参照してください。  
  
    -   **コンピューター認証**: コンピューター認証を構成して証明書を使用、またはクライアントの代わりに、Kerberos プロキシとして DirectAccess サーバーを使用できます。 詳細については、「 [1.3 証明書の要件を計画](da-adv-plan-s1-infrastructure.md#13-plan-certificate-requirements)する」を参照してください。  
  
    -   **Windows 7 クライアント**。 既定では、windows 7 を実行しているクライアントコンピューターは、Windows Server 2012 R2 または Windows Server 2012 の DirectAccess 展開に接続できません。 組織内に Windows 7 を実行していて、内部リソースへのリモートアクセスを必要とするクライアントがある場合は、接続を許可することができます。 内部リソースへのアクセスを許可するクライアント コンピューターは、DirectAccess クライアントのセットアップ ウィザードで指定したセキュリティ グループのメンバーである必要があります。  
  
        > [!NOTE]  
        > Windows 7 を実行しているクライアントが DirectAccess を使用して接続できるようにするには、コンピューター証明書認証を使用する必要があります。  
  
-   **VPN の構成**  
  
    DirectAccess を構成する前に、VPN アクセスを DirectAccess 対応でないリモート クライアントに提供するかどうかを決定します。 組織に Direct Access 接続をサポートしていないクライアント コンピューターがある場合 (管理されていない。または DirectAccess がサポートされていないオペレーティング システムで実行されているため)、VPN アクセスを提供する必要があります。 リモート アクセス サーバーのセットアップ ウィザードでは、IP アドレスを (DHCP を使用して、または静的アドレス プールから) 割り当てる方法と、Active Directory またはリモート認証ダイヤルイン ユーザー サービス (RADIUS) サーバーを使用して VPN クライアントを認証する方法を構成できます。  
  
## <a name="23-plan-infrastructure-servers"></a>2.3 インフラストラクチャ サーバーを計画する  
DirectAccess には、次の 3 種類のインフラストラクチャ サーバーが必要です。  
  
-   **DNS サーバー**: 詳細については、「[1.4 DNS 要件を計画する](da-adv-plan-s1-infrastructure.md#14-plan-dns-requirements)」を参照してください。  
  
-   **ネットワーク ロケーション サーバー**: 詳細については、「[1.5 ネットワーク ロケーション サーバーを計画する](da-adv-plan-s1-infrastructure.md#15-plan-the-network-location-server)」を参照してください。  
  
-   **管理サーバー**: 詳細については、「[1.6 管理サーバーを計画する](da-adv-plan-s1-infrastructure.md#16-plan-management-servers)」を参照してください。  
  
## <a name="24-plan-application-servers"></a>2.4 アプリケーション サーバーを計画する  
アプリケーション サーバーとは、企業ネットワークに置かれ、DirectAccess 接続でクライアント コンピューターによってアクセス可能なサーバーです。 アプリケーション サーバーは、セキュリティ グループに追加して識別されます。 そして、アプリケーション サーバー GPO がそのグループのサーバーに適用されます。  
  
> [!NOTE]  
> アプリケーション サーバーをセキュリティ グループに追加する必要があるのは、エンド ツー エンド認証と暗号化が必要な場合だけです。  
  
DirectAccess クライアントと選択した内部アプリケーション サーバーとの間で、必要に応じてエンド ツー エンド認証と暗号化を使用できます。 エンド ツー エンド認証を構成すると、DirectAccess クライアントは、IPsec トランスポート ポリシーを使用します。 このポリシーでは、IPsec セッションの認証とトラフィック保護が指定したアプリケーション サーバーで終了している必要があります。 この場合、リモート アクセス サーバーは、認証され、保護された IPsec セッションをアプリケーション サーバーに転送します。  
  
既定では、認証をアプリケーション サーバーに拡張すると、DirectAccess クライアントとアプリケーション サーバーとの間のデータ ペイロードが暗号化されます。 トラフィックを暗号化せずに、認証のみを使用する選択も可能です。 ただし、これは認証と暗号化を使用するより安全性が低く、Windows Server 2008 R2 または Windows Server 2012 オペレーティングシステムを実行しているアプリケーションサーバーでのみサポートされています。  
  
## <a name="25-plan-directaccess-and-third-party-vpn-clients"></a>2.5 DirectAccess とサードパーティ VPN クライアントを計画する  
一部のサードパーティ VPN クライアントでは、ネットワーク接続フォルダーで接続が作成されません。 このため、VPN 接続が確立され、イントラネットへの接続が存在しても、DirectAccess はイントラネット接続がないと判断する可能性があります。 これは、サードパーティ VPN クライアントが Network Device Interface Specification (NDIS) エンドポイントの種類として定義して、インターフェイスを登録するときに発生します。 DirectAccess クライアントで次のレジストリ値を 1 に設定して、これらの種類の VPN クライアントとの共存を有効にできます。  
  
**HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\services\NlaSvc\Parameters\ShowDomainEndpointInterfaces (REG_DWORD)**  
  
一部のサードパーティ VPN クライアントは、分割トンネル構成を使用します。この構成は、VPN 接続からイントラネットへのトラフィックを送信する必要なく、VPN クライアント コンピューターにインターネットへの直接のアクセスを許可します。  
  
分割トンネル構成では、通常、VPN クライアントで既定のゲートウェイ設定が構成されないまま残るか、すべてゼロ (0.0.0.0) になります。 これは、イントラネットへの正常な VPN 接続を確立し、Ipconfig.exe コマンド ライン ツールを使用して、結果となる構成を表示することで確認できます。  
  
VPN 接続で、既定のゲートウェイが空、またはすべてゼロ (0.0.0.0) と表示されている場合は、VPN クライアントがこの方法で構成されています。 既定では、DirectAccess クライアントは分割トンネル構成を識別しません。 DirectAccess クライアントが、これらの種類の VPN クライアント構成を検出して共存するように構成するには、次のレジストリ値を 1 に設定します。  
  
**HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\services\NlaSvc\Parameters\Internet\ Enabl Gatewaylocationdetection (REG_DWORD)**  
  
## <a name="previous-step"></a>前のステップ  
  
-   [手順 1: DirectAccess インフラストラクチャを計画する](da-adv-plan-s1-infrastructure.md)  
  


