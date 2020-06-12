---
title: Windows Server のトラブルシューティング
description: Windows Server の問題に関するトラブルシューティング記事へのリンクを取得する
ms.prod: windows-server
ms.technology: server-general
ms.date: 1/24/2020
author: kaushika-msft
ms.author: kaushika
ms.openlocfilehash: f3012f499e67f73ec9e8ab20b24df122492ea0ea
ms.sourcegitcommit: fa9a8badf4eb366aeeca7d2905e2cad711ee8dae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2020
ms.locfileid: "84714904"
---
# <a name="troubleshooting-windows-server-components"></a>Windows Server コンポーネントのトラブルシューティング

> [!TIP]
> 以前のバージョンの Windows Server に関する情報をお探しの場合は、 docs.microsoft.com の他の [Windows Server ライブラリ](/previous-versions/windows/)を参照してください。  
>   
> また、[このサイトで検索して](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions)、具体的な情報を確認することもできます。

Microsoft は、Windows Server の両方の更新プログラムを定期的にリリースします。 お客様のサーバーでセキュリティ更新プログラムなどの今後の更新プログラムを受信できることを確認するには、サーバーを最新の状態に維持する必要があります。 リリースされた更新プログラムの完全なリストについては、「[Windows 10 および Windows Server 2016 の更新履歴](https://support.microsoft.com/help/4000825/windows-10-windows-server-2016-update-history)」をご覧ください。

このセクションには、Windows Server の問題を解決するのに役立つ高度なトラブルシューティングのトピックとリンクが含まれています。 追加のトピックが利用可能になると追加されます。

## <a name="troubleshoot-activation"></a>アクティブ化のトラブルシューティング

- [Windows ボリューム ライセンス認証のトラブルシューティング](https://docs.microsoft.com/windows-server/get-started/activation-troubleshooting-guide)
- [KMS のトラブルシューティングに関するガイドライン](https://docs.microsoft.com/windows-server/get-started/activation-troubleshoot-kms-general)
- [ボリューム ライセンス認証情報を取得するための Slmgr.vbs オプション](https://docs.microsoft.com/windows-server/get-started/activation-slmgr-vbs-options)
- [Windows ライセンス認証のエラー コードの解決](https://docs.microsoft.com/windows-server/get-started/activation-error-codes)
- [KMS ライセンス認証の既知の問題](https://docs.microsoft.com/windows-server/get-started/activation-troubleshoot-kms-issues)
- [MAK ライセンス認証の既知の問題](https://docs.microsoft.com/windows-server/get-started/activation-troubleshoot-mak-issues)
- [DNS に関連するライセンス認証の問題のトラブルシューティングに関するガイドライン](https://docs.microsoft.com/windows-server/get-started/common-troubleshooting-procedures-kms-dns)
- [Tokens.dat ファイルの再構築](https://docs.microsoft.com/windows-server/get-started/activation-rebuild-tokens-dat-file)
- [ADBA クライアントのトラブルシューティング](https://docs.microsoft.com/windows-server/get-started/activation-troubleshoot-adba-clients)

## <a name="troubleshoot-startup-and-restart"></a>スタートアップと再起動のトラブルシューティング

- [Windows のスタートアップの高度なトラブルシューティング](https://docs.microsoft.com/windows/client-management/troubleshoot-windows-startup)
- [64 ビット版 Windows 用の適切なページ ファイルのサイズを確認する方法](https://docs.microsoft.com/windows/client-management/determine-appropriate-page-file-size)
- [カーネルまたは完全なクラッシュダンプを生成する](https://docs.microsoft.com/windows/client-management/generate-kernel-or-complete-crash-dump)
- [ページファイルの概要](https://docs.microsoft.com/windows/client-management/introduction-page-file)
- [Windows でのシステムエラーと回復オプションの構成](https://docs.microsoft.com/windows/client-management/system-failure-recovery-options)
- [Windows の起動の問題の高度なトラブルシューティング](https://docs.microsoft.com/windows/client-management/advanced-troubleshooting-boot-problems)
- [Windows ベースのコンピューターのフリーズの高度なトラブルシューティング](https://docs.microsoft.com/windows/client-management/troubleshoot-windows-freeze)
- [Stop エラーまたはブルー スクリーン エラーの高度なトラブルシューティング](https://docs.microsoft.com/windows/client-management/troubleshoot-stop-errors)
- [Stop エラー 7B または Inaccessible_Boot_Device の高度なトラブルシューティング](https://docs.microsoft.com/windows/client-management/troubleshoot-inaccessible-boot-device)
- [イベント ID 41 の高度なトラブルシューティング "システムは最初に正常にシャットダウンされずに再起動されました"](https://docs.microsoft.com/windows/client-management/troubleshoot-event-id-41-restart)
- [Box の Broadcom ネットワークアダプタードライバーを更新すると停止エラーが発生する](https://docs.microsoft.com/windows/client-management/troubleshoot-stop-error-on-broadcom-driver-update)

## <a name="troubleshoot-ad-forest-recovery"></a>AD フォレストの回復に関するトラブルシューティング

- [AD フォレストの回復 - FAQ](https://docs.microsoft.com/windows-server/identity/ad-ds/manage/ad-forest-recovery-faq)

## <a name="troubleshoot-ad-replication"></a>AD レプリケーションのトラブルシューティング

- [Active Directory レプリケーションの問題のトラブルシューティングに関するページ](https://docs.microsoft.com/windows-server/identity/ad-ds/manage/troubleshoot/troubleshooting-active-directory-replication-problems)
- [仮想化ドメイン コントローラーのトラブルシューティング](https://docs.microsoft.com/windows-server/identity/ad-ds/manage/virtual-dc/virtualized-domain-controller-troubleshooting)
- [ドメイン コントローラーの展開のトラブルシューティング](https://docs.microsoft.com/windows-server/identity/ad-ds/deploy/troubleshooting-domain-controller-deployment)
- [トラブルシューティング用にコンピューターを構成する](https://docs.microsoft.com/windows-server/identity/ad-ds/manage/troubleshoot/configuring-a-computer-for-troubleshooting)

## <a name="troubleshoot-ad-fs"></a>AD FS のトラブルシューティング

- [AD FS のトラブルシューティング](https://docs.microsoft.com/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-overview)
- [AD FS のトラブルシューティング-イベントとログの監査](https://docs.microsoft.com/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-logging)
- [AD FS のトラブルシューティング-SQL 接続](https://docs.microsoft.com/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-sql)
- [AD FS のトラブルシューティング-要求の発行](https://docs.microsoft.com/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-claims-issuance)
- [AD FS トラブルシューティング-ループ検出](https://docs.microsoft.com/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-loop)
- [AD FS のトラブルシューティング-証明書](https://docs.microsoft.com/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-certs)
- [AD FS のトラブルシューティング-Fiddler](https://docs.microsoft.com/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-fiddler)
- [AD FS のトラブルシューティング-Fiddler](https://docs.microsoft.com/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-fiddler-ws-fed)
- [AD FS のトラブルシューティング-要求規則](https://docs.microsoft.com/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-claims-rules)
- [AD FS トラブルシューティング-統合 Windows 認証](https://docs.microsoft.com/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-iwa)
- [AD FS のトラブルシューティング-Azure AD](https://docs.microsoft.com/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-azure)
- [AD FS の FAQ](https://docs.microsoft.com/windows-server/identity/ad-fs/overview/ad-fs-faq)
- [AD FS ヘルプ診断アナライザー](https://docs.microsoft.com/windows-server/identity/ad-fs/troubleshooting/ad-fs-diagnostics-analyzer)

## <a name="troubleshoot-aovpn"></a>Vpn のトラブルシューティング

- [Always On VPN のトラブルシューティング](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy-troubleshooting)

## <a name="troubleshoot-converged-nic"></a>収束 NIC のトラブルシューティング

- [収束 NIC 構成のトラブルシューティング](https://docs.microsoft.com/windows-server/networking/technologies/conv-nic/cnic-app-troubleshoot)

## <a name="troubleshoot-dfsr"></a>DFSR のトラブルシューティング

- [DFS レプリケーション:よく寄せられる質問 (FAQ)](https://docs.microsoft.com/windows-server/storage/dfs-replication/dfsr-faq)

## <a name="troubleshoot-directaccess"></a>DirectAccess のトラブルシューティング

- [DirectAccess のトラブルシューティング](https://docs.microsoft.com/windows-server/remote/remote-access/directaccess/troubleshooting-directaccess)

## <a name="troubleshoot-disk-management"></a>ディスク管理のトラブルシューティング

- [ディスクの管理のトラブルシューティング](https://docs.microsoft.com/windows-server/storage/disk-management/troubleshooting-disk-management)

## <a name="troubleshoot-dns"></a>DNS のトラブルシューティング

- [ドメインネームシステム (DNS) に関する問題のトラブルシューティング](https://docs.microsoft.com/windows-server/networking/dns/troubleshoot/troubleshoot-dns-data-collection)
- [DNS クライアントのトラブルシューティング](https://docs.microsoft.com/windows-server/networking/dns/troubleshoot/troubleshoot-dns-client)
- [DNS クライアントでの DNS クライアント側キャッシュの無効化](https://docs.microsoft.com/windows-server/networking/dns/troubleshoot/disable-dns-client-side-caching)
- [DNS サーバーのトラブルシューティング](https://docs.microsoft.com/windows-server/networking/dns/troubleshoot/troubleshoot-dns-server)

## <a name="troubleshoot-failover-cluster"></a>フェールオーバークラスターのトラブルシューティング

- [Windows エラー報告を使用したフェールオーバー クラスターのトラブルシューティング](https://docs.microsoft.com/windows-server/failover-clustering/troubleshooting-using-wer-reports)
- [クラスター対応更新についてよく寄せられる質問](https://docs.microsoft.com/windows-server/failover-clustering/cluster-aware-updating-faq)
- [イベント ID 1135 のクラスターの問題のトラブルシューティング](https://docs.microsoft.com/windows-server/troubleshoot/troubleshooting-cluster-event-id-1135)
- [アクティブなフェールオーバークラスターのメンバーシップからノードが削除されるという問題が発生する](https://docs.microsoft.com/windows-server/troubleshoot/problem-nodes-failover-cluster)
- [VMWare ESX のフェールオーバークラスターメンバーシップから削除されているノード](https://docs.microsoft.com/windows-server/troubleshoot/nodes-failover-cluster-vmware)
- [IaaS と SQL AlwaysOn - フェールオーバー クラスター ネットワークのしきい値の調整](https://docs.microsoft.com/windows-server/troubleshoot/iaas-sql-failover-cluster)

## <a name="troubleshoot-dhcp"></a>DHCP のトラブルシューティング

- [動的ホスト構成プロトコル (DHCP) のトラブルシューティングガイド](https://docs.microsoft.com/windows-server/troubleshoot/troubleshoot-dhcp-issue)
- [DHCP (動的ホスト構成プロトコル) の基本](https://docs.microsoft.com/windows-server/troubleshoot/dynamic-host-configuration-protocol-basics)
- [DHCP のトラブルシューティングに関する一般的なガイダンス](https://docs.microsoft.com/windows-server/troubleshoot/general-guidance-to-troubleshoot-dhcp)
- [DHCP サーバーなしで TCP/IP 自動アドレス指定を使用する方法](https://docs.microsoft.com/windows-server/troubleshoot/how-to-use-automatic-tcpip-addressing-without-a-dh)
- [DHCP クライアントでの問題のトラブルシューティング](https://docs.microsoft.com/windows-server/troubleshoot/troubleshoot-problems-on-dhcp-client)
- [DHCP サーバーでの問題のトラブルシューティング](https://docs.microsoft.com/windows-server/troubleshoot/troubleshoot-problems-on-dhcp-server)

## <a name="troubleshoot-fsrm"></a>FSRM のトラブルシューティング

- [ファイル サーバー リソース マネージャーのトラブルシューティング](https://docs.microsoft.com/windows-server/storage/fsrm/troubleshooting-file-server-resource-manager)

## <a name="troubleshoot-guarded-fabric"></a>保護されたファブリックのトラブルシューティング

- [保護されたファブリック診断ツールを使用したトラブルシューティング](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-troubleshoot-diagnostics)
- [ホストガーディアンサービスのトラブルシューティング](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-troubleshoot-hgs)
- [ホストガーディアンサービスのトラブルシューティング](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-troubleshoot-hosts)

## <a name="troubleshoot-multi-site-ras"></a>マルチサイト RAS のトラブルシューティング

- [マルチサイト有効化のトラブルシューティング](https://docs.microsoft.com/windows-server/remote/remote-access/ras/multisite/troubleshoot/troubleshooting-enabling-multisite)
- [エントリポイント追加のトラブルシューティング](https://docs.microsoft.com/windows-server/remote/remote-access/ras/multisite/troubleshoot/troubleshooting-adding-entry-points)
- [エントリ ポイント ドメイン コントローラー設定のトラブルシューティング](https://docs.microsoft.com/windows-server/remote/remote-access/ras/multisite/troubleshoot/troubleshooting-setting-the-entry-point-domain-controller)
- [Web プローブ URL のトラブルシューティング](https://docs.microsoft.com/windows-server/remote/remote-access/ras/multisite/troubleshoot/troubleshooting-web-probe-urls)

## <a name="troubleshoot-nano-server"></a>Nano Server のトラブルシューティング

- [Nano Server のトラブルシューティング](https://docs.microsoft.com/windows-server/get-started/troubleshooting-nano-server)

## <a name="troubleshoot-nic-teaming"></a>NIC チーミングのトラブルシューティング

- [NIC チーミングのトラブルシューティング](https://docs.microsoft.com/windows-server/networking/technologies/nic-teaming/troubleshooting-nic-teaming)

## <a name="troubleshoot-otp-authentication"></a>OTP 認証のトラブルシューティング

- [認証の問題のトラブルシューティング](https://docs.microsoft.com/windows-server/remote/remote-access/ras/otp/troubleshoot/troubleshooting-authentication-issues)
- [OTP の有効化のトラブルシューティング](https://docs.microsoft.com/windows-server/remote/remote-access/ras/otp/troubleshoot/troubleshooting-enabling-otp)

## <a name="troubleshoot-qos"></a>QoS のトラブルシューティング

- [QoS に関してよく寄せられる質問](https://docs.microsoft.com/windows-server/networking/technologies/qos/qos-policy-faq)

## <a name="troubleshoot-s2d"></a>S2D のトラブルシューティング

- [記憶域スペースダイレクトのトラブルシューティング](https://docs.microsoft.com/windows-server/storage/storage-spaces/troubleshooting-storage-spaces)
- [記憶域スペースダイレクトに関してよく寄せられる質問](https://docs.microsoft.com/windows-server/storage/storage-spaces/storage-spaces-direct-faq)
- [正常性と動作状態の記憶域スペースダイレクト](https://docs.microsoft.com/windows-server/storage/storage-spaces/storage-spaces-states)
- [記憶域スペースダイレクトを使用した診断データの収集](https://docs.microsoft.com/windows-server/storage/storage-spaces/data-collection)
- [Windows での記憶域クラス メモリ (NVDIMM-N) の正常性管理](https://docs.microsoft.com/windows-server/storage/storage-spaces/storage-class-memory-health)

## <a name="troubleshoot-sdn"></a>SDN のトラブルシューティング

- [SDN のトラブルシューティング](https://docs.microsoft.com/windows-server/networking/sdn/troubleshoot/troubleshoot-software-defined-networking)
- [Windows Server ソフトウェア定義ネットワーク スタックのトラブルシューティング](https://docs.microsoft.com/windows-server/networking/sdn/troubleshoot/troubleshoot-windows-server-software-defined-networking-stack)

## <a name="troubleshoot-rds-session-connectivity"></a>RDS セッション接続のトラブルシューティング

- [リモート デスクトップ接続の一般的なトラブルシューティング](https://docs.microsoft.com/windows-server/remote/remote-desktop-services/troubleshoot/rdp-error-general-troubleshooting)
- [クライアントが接続できず、クラスが登録されていないというエラーが発生する](https://docs.microsoft.com/windows-server/remote/remote-desktop-services/troubleshoot/rdp-error-class-not-registered)
- [クライアントが接続できず、利用可能なライセンスがないというエラーが表示される](https://docs.microsoft.com/windows-server/remote/remote-desktop-services/troubleshoot/rdp-error-no-licenses-available)
- [ユーザーが認証できない、または 2 回認証する必要がある](https://docs.microsoft.com/windows-server/remote/remote-desktop-services/troubleshoot/cannot-authenticate-or-must-authenticate-twice)
- [接続時に、ユーザーがリモートデスクトップサービスを受信しています。現在ビジー状態です](https://docs.microsoft.com/windows-server/remote/remote-desktop-services/troubleshoot/remote-desktop-service-currently-busy)
- [リモート デスクトップ クライアントが切断され、同じセッションに再接続できない](https://docs.microsoft.com/windows-server/remote/remote-desktop-services/troubleshoot/rdp-client-disconnects-cannot-reconnect-same-session)
- [リモート ラップトップがワイヤレス ネットワークから切断される](https://docs.microsoft.com/windows-server/remote/remote-desktop-services/troubleshoot/remote-laptop-disconnects-wireless-network)
- [リモート デスクトップ接続時のパフォーマンスの低下またはアプリケーションの問題](https://docs.microsoft.com/windows-server/remote/remote-desktop-services/troubleshoot/poor-performance-or-application-problems)

## <a name="troubleshoot-shielded-vm"></a>シールドされた VM のトラブルシューティング

- [シールドされた Vm のトラブルシューティング](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-troubleshoot-shielded-vms)

## <a name="troubleshoot-software-restriction-policies"></a>ソフトウェアの制限のポリシーのトラブルシューティング

- [ソフトウェア制限ポリシーのトラブルシューティング](https://docs.microsoft.com/windows-server/identity/software-restriction-policies/troubleshoot-software-restriction-policies)

## <a name="troubleshoot-storage-migration"></a>記憶域の移行のトラブルシューティング

- [記憶域移行サービスの既知の問題](https://docs.microsoft.com/windows-server/storage/storage-migration-service/known-issues)
- [記憶域移行サービスに関してよく寄せられる質問 (FAQ)](https://docs.microsoft.com/windows-server/storage/storage-migration-service/faq)

## <a name="troubleshoot-storage-replica"></a>記憶域レプリカのトラブルシューティング

- [記憶域レプリカに関する既知の問題](https://docs.microsoft.com/windows-server/storage/storage-replica/storage-replica-known-issues)
- [記憶域レプリカについてよく寄せられる質問](https://docs.microsoft.com/windows-server/storage/storage-replica/storage-replica-frequently-asked-questions)

## <a name="troubleshoot-user-profiles"></a>ユーザー プロファイルのトラブルシューティング

- [イベントを使用したユーザー プロファイルのトラブルシューティング](https://docs.microsoft.com/windows-server/storage/folder-redirection/troubleshoot-user-profiles-events)

## <a name="troubleshoot-vrss"></a>VRSS のトラブルシューティング

- [vRSS に関してよく寄せられる質問](https://docs.microsoft.com/windows-server/networking/technologies/vrss/vrss-faq)

## <a name="troubleshoot-webproxy"></a>WebProxy のトラブルシューティング

- [Web アプリケーション プロキシのトラブルシューティング](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/troubleshooting-web-application-proxy)

## <a name="troubleshoot-windows-admin-center"></a>Windows Admin Center のトラブルシューティング

- [Windows Admin Center の一般的なトラブルシューティングの手順](https://docs.microsoft.com/windows-server/manage/windows-admin-center/support/troubleshooting)
- [Windows Admin Center の既知の問題](https://docs.microsoft.com/windows-server/manage/windows-admin-center/support/known-issues)
- [Windows Admin Center についてよく寄せられる質問](https://docs.microsoft.com/windows-server/manage/windows-admin-center/understand/faq)
