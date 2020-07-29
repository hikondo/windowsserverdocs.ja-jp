---
title: Windows Admin Center についてよく寄せられる質問
description: Windows Admin Center (Project Honolulu) に関する回答を確認できます
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: medium
ms.date: 12/02/2019
ms.prod: windows-server
ms.openlocfilehash: 4125a3f427bd19ae7461aaaef058a558722d1987
ms.sourcegitcommit: b35fbd2a67d7a3395b50b2a3acd0817ba4e36b26
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86891377"
---
# <a name="windows-admin-center-frequently-asked-questions"></a>Windows Admin Center についてよく寄せられる質問

> 適用先:Windows Admin Center、Windows Admin Center Preview

ここでは、Windows Admin Center についてよく寄せられる質問に対する回答を示します。

## <a name="what-is-windows-admin-center"></a>Windows Admin Center とは?

Windows Admin Center は、IT 管理者が Windows Server および Windows 10 を管理するための軽量のブラウザー ベース GUI プラットフォームおよびツールセットです。 サーバー マネージャーおよび Microsoft 管理コンソール (MMC) などの使い慣れたインボックスの管理ツールが、最先端の簡素化され統合された安全なエクスペリエンスに進化したものです。

## <a name="can-i-use-windows-admin-center-in-production-environments"></a>運用環境で Windows Admin Center を使用できますか。

はい。 Windows Admin Center は一般提供されており、広範な使用方法や運用環境での展開に対応しています。 現在のプラットフォーム機能と主要なツールは Microsoft の標準リリースの基準と、ユーザビリティ、信頼性、パフォーマンス、アクセシビリティ、セキュリティ、導入の品質基準を満たしています。

[!INCLUDE [support-policy](../includes/support-policy.md)]

## <a name="how-much-does-it-cost-to-use-windows-admin-center"></a>Windows Admin Center を使用するにはいくらかかりますか。

Windows Admin Center には、Windows 以外の追加コストはかかりません。 Windows Admin Center (別のダウンロードとして利用可能) は、Windows Supplemental EULA に基づいて使用許諾されているため、Windows Server または Windows 10 の有効なライセンスと共に追加コストなしで使用することができます。

## <a name="what-versions-of-windows-server-can-i-manage-with-windows-admin-center"></a>Windows Admin Center によって管理できるのは、どのバージョンの Windows Server ですか。

Windows Admin Center は Windows Server 2019 用に最適化され、Windows Server 2019 リリースで主なテーマが有効になります (特に、ハイブリッド クラウドのシナリオとハイパーコンバージド インフラストラクチャの管理)。 Windows Admin Center は Windows Server 2019 で最適に機能しますが、お客様が既に使用している、次のようなさまざまなバージョンの管理をサポートしています。Windows Server 2012 以降は完全にサポートされます。 Windows Server 2008 R2 を管理する機能も、制限付きで提供しています。

## <a name="is-windows-admin-center-a-complete-replacement-for-all-traditional-in-box-and-rsat-tools"></a>Windows Admin Center は、すべての従来のインボックス ツールや RSAT ツールに完全に置き換わるものですか。

いいえ。 Windows Admin Center は多くの一般的なシナリオを管理できますが、従来のすべての Microsoft 管理コンソール (MMC) ツールに完全に置き換わるわけではありません。 Windows Admin Center に含まれるツールの詳細は、Microsoft のドキュメントで[サーバー管理](../use/manage-servers.md)について参照してください。 Windows Admin Center は、サーバー マネージャー ソリューション内に次の主要な機能を備えています。

* リソースとリソース使用率の表示
* 証明書の管理
* デバイスの管理
* イベント ビューアー
* エクスプローラー
* ファイアウォール管理
* インストールされたアプリの管理
* ローカル ユーザーとグループの構成
* ネットワーク設定
* プロセスの表示/終了およびプロセス ダンプの作成
* レジストリの編集
* スケジュールされたタスクの管理
* Windows サービスの管理
* 役割と機能の有効化/無効化
* Hyper-V VM と仮想スイッチの管理
* 記憶域の管理
* 記憶域レプリカの管理
* Windows Updates の管理
* PowerShell コンソール
* リモート デスクトップ接続

Windows Admin Center では、次のソリューションも提供されます。

* コンピューターの管理 – Windows 10 クライアント PC を管理するためのサーバー マネージャー機能のサブセットを提供します。
* フェールオーバー クラスター マネージャー – フェールオーバー クラスターおよびクラスター リソースの継続的な管理のためのサポートを提供します。
* ハイパーコンバージド クラスター マネージャー – 記憶域スペース ダイレクトおよび Hyper-V に合わせてカスタマイズされたまったく新しいエクスペリエンスを提供します。 ダッシュボードを備え、監視のためのグラフとアラートが重視されています。

Active Directory、DHCP、DNS、IIS などの役割には、Windows Admin Center に表示される同等の管理機能がまだないため、Windows Admin Center はリモート サーバー管理ツール (RSAT) に代わるものではなく、補完するものです。

## <a name="can-windows-admin-center-be-used-to-manage-the-free-microsoft-hyper-v-server"></a>無料の Microsoft Hyper-V サーバーを管理するために Windows Admin Center を使用することはできますか。

はい。 Windows Admin Center を使用して、Microsoft Hyper-V Server 2016 および Microsoft Hyper-V Server 2012 R2 を管理できます。

## <a name="can-i-deploy-windows-admin-center-on-a-windows-10-computer"></a>Windows 10 のコンピューター上に Windows Admin Center を展開できますか。

はい、Windows Admin Center はデスクトップ モードで実行される Windows 10 (バージョン 1709 以降) にインストールできます。  Windows Admin Center は、ゲートウェイ モードで Windows Server 2016 以降を実行しているサーバーにもインストールして、Windows 10 のコンピューターから Web ブラウザーでアクセスすることができます。 [インストール オプションに関する詳細を確認してください](../plan/installation-options.md)。

## <a name="ive-heard-that-windows-admin-center-uses-powershell-under-the-hood-can-i-see-the-actual-scripts-that-it-uses"></a>Windows Admin Center は内部で PowerShell を使用していると聞きました。使用されている実際のスクリプトを確認できますか。

はい。 Windows Admin Center Preview 1806 では [Showscript 機能](../use/get-started.md#view-powershell-scripts-used-in-windows-admin-center)が追加され、現在は GA のチャネルに追加されています。

## <a name="are-there-any-plans-for-windows-admin-center-to-manage-windows-server-2008-r2-or-earlier"></a>Windows Admin Center が Windows Server 2008 R2 以前を管理できるようになる予定はありますか。

Windows Admin Center では、Windows Server 2008 R2 を管理するための機能は**サポートされなくなりました**。 Windows Admin Center は、Windows Server 2008 R2 以前には存在しない PowerShell 機能やプラットフォーム テクノロジを利用しているため、完全なサポートは実現不可能です。 まだお持ちでない場合は、[Azure に移行するか、最新バージョンの Windows Server にアップグレードする](https://www.microsoft.com/cloud-platform/windows-server-2008)ことをお勧めします。

## <a name="are-there-any-plans-for-windows-admin-center-to-manage-linux-connections"></a>Windows Admin Center が Linux 接続を管理できるようになる予定はありますか。

顧客のニーズのため調査中ですが、現在、確定している提供予定はありません。また、サポートは、SSH 経由のコンソール接続のみで構成される可能性があります。

## <a name="which-web-browsers-are-supported-by-windows-admin-center"></a>Windows Admin Center によってサポートされているのは、どの Web ブラウザーですか。

Microsoft Edge (Windows 10 バージョン 1709 以降)、Google Chrome、および [Microsoft Edge Insider](https://microsoftedgeinsider.com) の最新バージョンは、Windows 10 上でテストされ、サポートされています。 [ブラウザー固有の既知の問題をご覧ください](../support/known-issues.md#browser-specific-issues)。 他の最新の Web ブラウザーまたは他のプラットフォームは、現在、弊社のテスト マトリックスには含まれていないため、*正式には*サポートされていません。

## <a name="how-does-windows-admin-center-handle-security"></a>Windows Admin Center では、セキュリティをどのように処理していますか。

ブラウザーから Windows Admin Center ゲートウェイへのトラフィックでは、HTTPS を使用します。 ゲートウェイからマネージド サーバーへのトラフィックでは、標準の PowerShell および WMI over WinRM です。 Microsoft は、LAPS (Local Administrator Password Solution)、リソースベースの制約付き委任、AD または Azure AD を使用したゲートウェイ アクセス制御、および対象サーバーを管理するためのロールベースのアクセス制御をサポートしています。

## <a name="does-windows-admin-center-use-credssp"></a>Windows Admin Center は CredSSP を使用しますか。

はい、一部のケースでは Windows Admin Center で CredSSP が必要です。 これは、管理対象の特定のサーバー以外のマシンに、認証のために資格情報を渡すために必要になります。 たとえば、**サーバー B** 上の仮想マシンを管理しているが、仮想マシンの vhdx ファイルを**サーバー C** によってホストされているファイル共有上に保存したい場合、ファイル共有にアクセスできるように Windows Admin Center で CredSSP を使用して**サーバー C** を認証する必要があります。

Windows Admin Center は、ユーザーの同意を確認した後、自動的に CredSSP の構成を処理します。 Windows Admin Center は、CredSSP を構成する前に、システムに最近の CredSSP の[更新プログラム](https://support.microsoft.com/help/4093492/credssp-updates-for-cve-2018-0886-march-13-2018)が含まれているかどうかを確認します。 

CredSSP は現在、次の領域で使用されています。

- 仮想マシン ツールで細分類された SMB 記憶域の使用 (上記の例)
- [クラスター対応更新](https://docs.microsoft.com/windows-server/failover-clustering/cluster-aware-updating)を実行する、フェールオーバーまたはハイパーコンバージド クラスター管理のソリューションでの更新プログラム ツールの使用 

## <a name="are-there-any-cloud-dependencies"></a>クラウド依存関係はありますか。

Windows Admin Center ではインターネット アクセスを必要とせず、また、Microsoft Azure を必要としません。 Windows Admin Center では、物理システム上、任意のハイパーバイザーにある仮想マシン上、または、任意のクラウドでの実行など、任意の場所で Windows Server および Windows のインスタンスを管理します。 今後、さまざまな Azure サービスとの統合が追加されていく予定ですが、これらはオプションの付加価値機能であり、Windows Admin Center を使用するための要件ではありません。

## <a name="are-there-any-other-dependencies-or-prerequisites"></a>その他の依存関係や前提条件はありますか。

Windows Admin Center は、Windows 10 Fall Anniversary Update (1709) 以降、または Windows Server 2016 以降にインストールできます。 Windows Server 2008 R2、2012、または 2012 R2 を管理するには、それらのサーバー上に Windows Management Framework 5.1 をインストールすることが必要になります。 その他の依存関係はありません。 IIS、エージェント、SQL Server は必要ありません。

## <a name="what-about-extensibility-and-3rd-party-support"></a>機能拡張およびサード パーティのサポートはどうなりますか。

Windows Admin Center には使用可能な SDK が含まれているため、すべてのユーザーが独自の拡張機能を書き込むことができます。 プラットフォームとして、エコシステムを拡大し、パートナーの拡張性を有効にすることは、当初から最優先でした。 [Windows Admin Center SDK の詳細について確認してください](../extend/extensibility-overview.md)。

## <a name="can-i-manage-hyper-converged-infrastructure-with-windows-admin-center"></a>Windows Admin Center を使用して、ハイパーコンバージド インフラストラクチャを管理することはできますか。

はい。 Windows Admin Center は、Windows Server 2016 または Windows Server 2019 を実行しているハイパーコンバージド クラスターの管理をサポートしています。 Windows Admin Center のハイパーコンバージド クラスター マネージャー ソリューションは以前はプレビューでしたが現在は**一般公開**され、いくつかの新機能がプレビューになっています。 詳細については、[ハイパーコンバージド インフラストラクチャの管理について確認してください](../use/manage-hyper-converged.md)。

## <a name="does-windows-admin-center-require-system-center"></a>Windows Admin Center に System Center は必要ですか。

いいえ。 Windows Admin Center は、System Center を補完するものですが、System Center は必要ありません。 [Windows Admin Center と System Center についての詳細をご確認ください](related-management.md#system-center)。

## <a name="can-windows-admin-center-replace-system-center-virtual-machine-manager-scvmm"></a>System Center Virtual Machine Manager (SCVMM) を Windows Admin Center に置き換えることはできますか。

Windows Admin Center と SCVMM は補完し合う関係にあります。Windows Admin Center は従来の Microsoft 管理コンソール (MMC) スナップインとサーバー管理者のエクスペリエンスを置き換えることを目的としています。  Windows Admin Center は、SCVMM の監視の側面を置き換えることを目的としていません。 [Windows Admin Center と System Center についての詳細をご確認ください](related-management.md#system-center)。

## <a name="what-is-windows-admin-center-preview-which-version-is-right-for-me"></a>Windows Admin Center Preview とは何ですか。どちらのバージョンが適しているでしょうか。

次の 2 つのバージョンの Windows Admin Center をダウンロードできます。

### <a name="windows-admin-center"></a>Windows Admin Center

* 頻繁に更新できなかったり、運用環境で使用するリリースの検証にもっと時間をかけたい IT 管理者には、このバージョンが適しています。 現在一般提供 (GA) されているリリースは、Windows Admin Center 1910 です。
* [!INCLUDE [support-policy](../includes/support-policy.md)]
* 最新のリリースは、[こちらでダウンロード](https://aka.ms/WACDownload)してください。

### <a name="windows-admin-center-preview"></a>Windows Admin Center Preview

* 定期的に最新かつ最善の機能を入手したい IT 管理者には、このバージョンが最適です。 Microsoft は毎月後続の更新プログラムのリリースを提供する予定です。 コア プラットフォームは引き続き運用環境に対応しており、ライセンスによって運用環境での使用権が提供されます。 ただし、明確に PREVIEW としてマークされ、評価やテストに適している新しいツールおよび機能の導入もあることに、注意してください。
* 最新の Insider Preview リリースを入手する場合、登録済みの Insider は [Windows Server Insider Preview ダウンロード ページ](https://microsoft.com/en-us/software-download/windowsinsiderpreviewserver)の [Additional Downloads] (追加のダウンロード) ドロップダウンから直接 Windows Admin Center Preview をダウンロードできます。 まだ Insider として登録していない場合は、Windows Insiders for Business ポータル上の [Windows Server の概要](https://insider.windows.com/en-us/for-business-getting-started-server/)に関するページを参照してください。

## <a name="why-was-windows-admin-center-chosen-as-the-final-name-for-project-honolulu"></a>"Project Honolulu" の最終的な名前として "Windows Admin Center" が選択されたのはなぜですか。

Windows Admin Center は、"Project Honolulu" の正式な製品名であり、当社のビジョンである、幅広い主要な管理シナリオでの IT 管理者の統合エクスペリエンスを強化しています。 また、IT 管理ユーザーのニーズを投資や提供サービスの中心として、顧客への取り組みを強調しています。

## <a name="where-can-i-learn-more-about-windows-admin-center-or-get-more-details-on-the-topics-above"></a>Windows Admin Center の詳細や上のトピックの詳細を、どこで確認できますか。

Microsoft の[起動画面](https://aka.ms/WindowsAdminCenter)を出発点にするのが最適です。新たに分類されたドキュメント コンテンツ、ダウンロード場所、フィードバックの提供方法、リファレンス情報、その他のリソースへのリンクがあります。

## <a name="what-is-the-version-history-of-windows-admin-center"></a>Windows Admin Center のバージョン履歴とは何ですか。

[こちらでバージョン履歴をご覧ください。](../support/release-history.md)

## <a name="im-having-an-issue-with-windows-admin-center-where-can-i-get-help"></a>Windows Admin Center で問題が発生していますが、どこでサポート情報を入手できますか。

[トラブルシューティング ガイド](../use/troubleshooting.md)および[既知の問題](../use/known-issues.md)の一覧を参照してください。
