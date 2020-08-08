---
title: 記憶域移行サービスの概要
description: Storage Migration Service を使用すると、Windows Server または Azure にストレージを簡単に移行できます。 Windows と Linux のサーバー上のデータをインベントリし、そのデータを新しいサーバーまたは Azure virtual machines に転送するグラフィカルツールを提供します。 また、記憶域移行サービスでは、サーバーの id を移行先サーバーに転送するオプションも用意されています。これにより、アプリとユーザーがリンクまたはパスを変更することなくデータにアクセスできるようになります。
author: jasongerend
ms.author: jgerend
manager: elizapo
ms.date: 03/26/2020
ms.topic: article
ms.openlocfilehash: 18c9bb2bf22f107b988942706850907c67b5ec9a
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87939330"
---
# <a name="storage-migration-service-overview"></a>記憶域移行サービスの概要

>適用対象: Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server (半期チャネル)

Storage Migration Service を使用すると、Windows Server または Azure にストレージを簡単に移行できます。 Windows と Linux のサーバー上のデータをインベントリし、そのデータを新しいサーバーまたは Azure virtual machines に転送するグラフィカルツールを提供します。 また、記憶域移行サービスでは、サーバーの id を移行先サーバーに転送するオプションも用意されています。これにより、アプリとユーザーがリンクまたはパスを変更することなくデータにアクセスできるようになります。

このトピックでは、記憶域移行サービスを使用する理由、移行プロセスのしくみ、移行元サーバーと移行先サーバーの要件、および[記憶域移行サービスの新機能](#whats-new-in-storage-migration-service)について説明します。

## <a name="why-use-storage-migration-service"></a>記憶域移行サービスを使用する理由

新しいハードウェアまたは仮想マシンに移行するサーバー (または多数のサーバー) があるため、記憶域移行サービスを使用してください。 記憶域移行サービスは、次の操作を行うことによって役立つように設計されています。

- 複数のサーバーとそのデータのインベントリ
- 移行元サーバーからファイル、ファイル共有、およびセキュリティ構成を迅速に転送する
- 必要に応じて、ユーザーとアプリが既存のデータにアクセスするために変更する必要がないように、移行元サーバーの id を引き継ぎます。
- Windows 管理センターのユーザーインターフェイスからの1つまたは複数の移行の管理

![移行元サーバーから移行先サーバー、Azure Vm、または Azure File Sync にファイル & 構成を移行するストレージ移行サービスを示す図](media/overview/storage-migration-service-diagram.png)

**図 1: 記憶域移行サービスのソースと変換先**

## <a name="how-the-migration-process-works"></a>移行プロセスのしくみ

移行は、3つの手順からなるプロセスです。

1. ファイルと構成に関する情報を収集する**インベントリサーバー** (図2を参照)。
2. 移行元サーバーから移行先サーバーに**データを転送 (コピー)** します。
3. **新しいサーバーにカットオーバー**します (省略可能)。<br>移行先サーバーは、アプリとユーザーが何も変更する必要がないように、移行元サーバーの以前の id を想定しています。 <br>移行元サーバーは、常に同じファイル (移行元サーバーからファイルを削除することはありません) が含まれていても、ユーザーとアプリは使用できないというメンテナンス状態になります。 これにより、サーバーを使いやすくすることができます。

![スキャンの準備ができているサーバーを示すスクリーンショット ](media/migrate/inventory.png)
 **図 2: 記憶域移行サービスのサーバーのインベントリ**

ここでは、Storage Migration Service を使用して、現在サポートされていない Windows Server 2008 R2 サーバーなどのサーバーを作成し、記憶域を新しいサーバーに移動する方法を示すビデオを紹介します。

> [!VIDEO https://www.youtube.com/embed/h-Xc9j1w144]

## <a name="requirements"></a>要件

Storage Migration Service を使用するには、次のものが必要です。

- ファイルとデータを移行する**ソースサーバー**または**フェールオーバークラスター**
- に移行する Windows Server 2019 (クラスター化またはスタンドアロン) を実行している**移行先サーバー** 。 Windows Server 2016 と Windows Server 2012 R2 も同様に動作しますが、約50% 低速です。
- 移行を管理するために Windows Server 2019 を実行する**orchestrator サーバー**  <br>少数のサーバーのみを移行していて、いずれかのサーバーで Windows Server 2019 を実行している場合は、そのサーバーを orchestrator として使用できます。 より多くのサーバーを移行する場合は、別の orchestrator サーバーを使用することをお勧めします。
- 記憶域移行サービスのユーザーインターフェイスを実行する**PC またはサーバー [Windows Admin Center](../../manage/windows-admin-center/overview.md) ** 。 PowerShell を使用して移行を管理する場合を除きます。 Windows 管理センターと Windows Server 2019 のバージョンの両方が、バージョン1809以降である必要があります。

Orchestrator とセットアップ先のコンピューターには、少なくとも2つのコアまたは2つの vCPUs と、少なくとも 2 GB のメモリがあることを強くお勧めします。 プロセッサとメモリが増えると、インベントリおよび転送操作の速度が大幅に向上します。

### <a name="security-requirements-the-storage-migration-service-proxy-service-and-firewall-ports"></a>セキュリティ要件、記憶域移行サービスプロキシサービス、およびファイアウォールポート

- 移行元コンピューターと orchestrator コンピューターの管理者である移行アカウント。
- 移行先コンピューターと orchestrator コンピューターの管理者である移行アカウント。
- Orchestrator コンピューターでは、[ファイルとプリンターの共有 (SMB*受信*)] ファイアウォール規則が有効になっている必要があります。
- 移行元と移行先のコンピューターでは、次のファイアウォール規則の*受信*が有効になっている必要があります (ただし、既に有効になっている可能性があります)。
  - ファイルとプリンターの共有 (SMB 受信)
  - Netlogon サービス (NP 受信)
  - DCOM-In (Windows Management Instrumentation)
  - WMI-In (Windows Management Instrumentation)

  > [!TIP]
  > Windows Server 2019 コンピューターに Storage Migration Service プロキシサービスをインストールすると、そのコンピューターで必要なファイアウォールポートが自動的に開きます。 これを行うには、Windows 管理センターで移行先サーバーに接続し、[**サーバーマネージャー** (Windows 管理センター)] > [**役割と機能**] の順に選択し、[**記憶域移行サービスプロキシ**] を選択して [**インストール**] を選択します。


- コンピューターが Active Directory Domain Services ドメインに属している場合は、すべてが同じフォレストに属している必要があります。 移行元のドメイン名を移行先に転送する場合は、移行先サーバーが移行元サーバーと同じドメインにある必要もあります。 ドメイン間での移行は技術的には可能ですが、移行先の完全修飾ドメイン名はソースとは異なります...

### <a name="requirements-for-source-servers"></a>移行元サーバーの要件

移行元サーバーでは、次のいずれかのオペレーティングシステムを実行する必要があります。

- Windows Server 半期チャネル
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2
- Windows Server 2008
- Windows Server 2003 R2
- Windows Server 2003
- Windows Small Business Server 2003 R2
- Windows Small Business Server 2008
- Windows Small Business Server 2011
- Windows Server 2012 Essentials
- Windows Server 2012 R2 Essentials
- Windows Server 2016 Essentials
- Windows Server 2019 Essentials
- Windows Storage Server 2008
- Windows Storage Server 2008 R2
- Windows Storage Server 2012
- Windows Storage Server 2012 R2
- Windows Storage Server 2016

注: Windows Small Business Server と Windows Server Essentials はドメインコントローラーです。 記憶域移行サービスは、ドメインコントローラーからはまだ切り取れませんが、それらのファイルからファイルをインベントリして転送することはできます。

Orchestrator が Windows Server バージョン1903以降を実行している場合、または orchestrator で[KB4512534](https://support.microsoft.com/help/4512534/windows-10-update-kb4512534)がインストールされている以前のバージョンの windows server が実行されている場合は、次の追加のソースの種類を移行できます。

- Windows Server 2012、Windows Server 2012 R2、windows Server 2016、Windows Server 2019 を実行するフェールオーバークラスター
- Samba を使用する Linux サーバー。 次のことをテストしました。
    - CentOS 7
    - Debian GNU/Linux 8
    - RedHat Enterprise Linux 7.6
    - SUSE Linux Enterprise Server (SLES) 11 SP4
    - Ubuntu 16.04 LTS と 12.04.5 LTS
    - Samba 4.8、4.7、4.3、4.2、および3.6

### <a name="requirements-for-destination-servers"></a>移行先サーバーの要件

移行先サーバーでは、次のいずれかのオペレーティングシステムを実行する必要があります。

- Windows Server 半期チャネル
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2

> [!TIP]
> Windows Server 2019 または Windows Server を実行している移行先サーバー、半期チャネル以降では、以前のバージョンの Windows Server の転送パフォーマンスが2倍になっています。 このパフォーマンスの向上は、組み込みの Storage Migration Service プロキシサービスが含まれていることによるものであり、まだ開いていない場合は、必要なファイアウォールポートも開きます。

## <a name="azure-vm-migration"></a>Azure VM の移行

Windows 管理センターバージョン1910では、Azure 仮想マシンをデプロイできます。 これにより、VM のデプロイが記憶域移行サービスに統合されます。 ワークロードをデプロイする前に手動で Azure Portal で新しいサーバーと Vm を構築するのではなく、必要な手順と構成がない場合もあります。 Windows 管理センターでは、Azure VM のデプロイ、ストレージの構成、ドメインへの参加、ロールのインストール、および分散システムのセットアップを行うことができます。

   Storage Migration Service を使用して Azure Vm に移行する方法を示すビデオを次に示します。
   > [!VIDEO https://www.youtube-nocookie.com/embed/k8Z9LuVL0xQ]

新しいオペレーティングシステムに移行せずに仮想マシンを Azure にリフトアンドシフトする場合は、Azure Migrate の使用を検討してください。 詳細については、「 [Azure Migrate の概要](https://go.microsoft.com/fwlink/?linkid=2056064)」を参照してください。

## <a name="whats-new-in-storage-migration-service"></a>Storage Migration Service の新機能

Windows 管理センターバージョン1910では、Azure 仮想マシンをデプロイする機能が追加されています。 これにより、Azure VM のデプロイがストレージ移行サービスに統合されます。 詳細については、「 [AZURE VM の移行](#azure-vm-migration)」を参照してください。

Windows Server バージョン1903以降、または[KB4512534](https://support.microsoft.com/help/4512534/windows-10-update-kb4512534)がインストールされている以前のバージョンの windows Server で Storage Migration Server orchestrator を実行する場合は、次の新機能を使用できます。

- 新しいサーバーへのローカル ユーザーとローカル グループの移行
- フェールオーバークラスターから記憶域を移行し、フェールオーバークラスターに移行して、スタンドアロンサーバーとフェールオーバークラスター間で移行する
- Samba を使用する Linux サーバーからの記憶域の移行
- Azure File Sync を使用した Azure へ移行された共有のより簡単な同期
- Azure などの新しいネットワークへの移行

## <a name="additional-references"></a>その他の参照情報

- [記憶域移行サービスを使用してファイルサーバーを移行する](migrate-data.md)
- [記憶域移行サービスに関してよく寄せられる質問 (FAQ)](faq.md)
- [記憶域移行サービスの既知の問題](known-issues.md)
