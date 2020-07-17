---
title: Windows Server 2016 への移行に関する推奨事項
description: Windows Server 2016 への移行に関する推奨事項。
ms.prod: windows-server
ms.date: 10/18/2016
ms.technology: server-general
ms.topic: article
ms.assetid: 74aa1da3-7076-4a1f-ad5b-9e17bd46dba2
author: jaimeo
ms.author: jaimeo
manager: dongill
ms.localizationpriority: medium
ms.openlocfilehash: 6b02a3caa0db2a66307754ebd95865d8ba10ef4f
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "80826755"
---
# <a name="recommendations-for-moving-to-windows-server-2016"></a>Windows Server 2016 への移行に関する推奨事項

>適用先:Windows Server 2016


|使用している Windows オペレーティング システム|Windows Server 2012 R2 または Windows Server 2012|Windows Server 2008 R2 または Windows Server 2008|  
|-------------------|----------|--------------|--------------|---------------------------------------|  
|**Windows Server の役割のインフラストラクチャ**|[特定の役割のガイダンス](https://technet.microsoft.com/windowsserver/jj554790)に関するページに従って、更新または移行のいずれかを選択します。|- Windows Server 2016 の新機能を利用するには、新しいハードウェアを展開するか、または既存のホスト上の仮想マシンに Windows Server 2016 をインストールします。 一部の新機能は、Hyper-V を実行する Windows Server 2016 物理ホストで最適に動作します。 <br>- [特定の役割のガイダンス](https://technet.microsoft.com/windowsserver/jj554790)に関するページを参照してください。|
|**Microsoft サーバーの管理とアプリケーションのワークロード**|- アプリケーションのアップグレードには Windows Server 2016 への*移行*を含める必要があります。 [互換性リスト](Server-Application-Compatibility.md)を参照してください。 <br>- Windows Server 2016 へのアップグレードのみ (つまり、アプリケーションのアップグレードは行わない) 場合は、アプリケーションに固有のガイダンスを使用する必要があります。|- Windows Server 2016 の新機能を利用するには、新しいハードウェアを展開するか、または既存のホスト上の仮想マシンに Windows Server 2016 をインストールします。 一部の新機能は、Hyper-V を実行する Windows Server 2016 物理ホストで最適に動作します。 必要に応じて移行ガイドに従ってください。 <br>- または、現在の OS 上に残り、Windows Server 2016 ホスト上で動作する仮想マシン内、あるいは Microsoft Azure で実行します。 [ソフトウェア アシュアランス](https://www.microsoft.com/Licensing/licensing-programs/software-assurance-default.aspx)による拡張サポート オプションについては、EA 販売店、TAM、または Microsoft にお問い合わせください。|
|**ISV アプリケーションのワークロード**|- Windows Server 2016 へのアップグレードには、アプリケーションに固有のガイダンスを使用する必要があります。 <br>- Windows Server と Microsoft 製品以外のアプリケーションとの互換性については、[Windows Server Logo Certification (Windows Server ロゴ認証) ポータル](https://msdn.microsoft.com/enterprisecloudcertified)にアクセスしてください。|- Windows Server 2016 の新機能を利用するには、新しいハードウェアを展開するか、または既存のホスト上の仮想マシンに Windows Server 2016 をインストールします。 一部の新機能は、Hyper-V を実行する Windows Server 2016 物理ホストで最適に動作します。 必要に応じて移行ガイドに従ってください。 <br>- または、現在の OS 上に残り、Windows Server 2016 ホスト上で動作する仮想マシン内、あるいは Microsoft Azure で実行します。 [ソフトウェア アシュアランス](https://www.microsoft.com/Licensing/licensing-programs/software-assurance-default.aspx)による拡張サポート オプションについては、EA 販売店、TAM、または Microsoft にお問い合わせください。|
|**カスタム アプリケーションのワークロード**|- Windows Server 2016 との互換性およびアップグレード ガイダンスについては、アプリケーションの開発者に問い合わせてください。 <br>- 切り替えを行う前に、Microsoft Azure を活用して Windows Server 2016 上でアプリケーションをテストします。 <br>- 次のセクションに示したオプション一覧を参照してください。|- Windows Server 2016 との互換性およびアップグレード ガイダンスについては、アプリケーションの開発者に問い合わせてください。 <br>- 切り替えを行う前に、Microsoft Azure を活用して Windows Server 2016 上でアプリケーションをテストします。 <br>- Windows Server 2016 の新機能を利用するには、新しいハードウェアを展開するか、または既存のホスト上の仮想マシンに Windows Server 2016 をインストールします。 一部の新機能は、Hyper-V を実行する Windows Server 2016 物理ホストで最適に動作します。 <br>- 次のセクションに示したオプション一覧を参照してください。|

## <a name="complete-options-for-moving-servers-running-custom-or-in-house-applications-on-older-versions-of-windows-server-to-windows-server-2016"></a>Windows Server の古いバージョンでカスタム アプリケーションまたは社内アプリケーションを実行するサーバーを Windows Server 2016 に移行するためのオプション一覧

現在のサービスやワークロードに与える影響を最小限に抑えながら、お客様やその顧客の皆様に Windows Server 2016 の機能をご利用いただけるようにするためのオプションがこれまで以上に多く用意されています。

- [Windows Server](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016) の評価版をダウンロードしてオンプレミスでテストすることにより、最新のオペレーティング システムとアプリケーションの組み合わせを試してみることができます。 テストが完了し、品質が確認できたら、製品版のライセンス キーを使用して簡単なライセンス変換を実行することができます (再起動が必要)。

- [Microsoft Azure](https://azure.microsoft.com) を試験的に使用して、カスタム アプリケーションが最新のサーバー オペレーティング システムで確実に動作するかテストすることもできます。 テストが完了し、品質を確認できたら、オンプレミスで[最新の Windows Server バージョンへの移行](https://docs.microsoft.com/windows-server/get-started/installation-and-upgrade#upgrade)を行います。 

- または、テストが完了し、品質を確認できたら、お客様のカスタム アプリケーションまたはサービスの永続的な場所として [Microsoft Azure](https://azure.microsoft.com) を使用することができます。 これにより、Azure の新しいサーバーへの切り替え準備ができるまで、古いサーバーを引き続き使用することができます。

    - Windows Server 用のソフトウェア アシュアランスを既にお持ちである場合は、[Azure Hybrid Use Benefit](https://azure.microsoft.com/pricing/hybrid-use-benefit/) で展開してコストを削減できます。 

- ほとんどの場合、[Microsoft Azure](https://azure.microsoft.com) を使用すれば、現在実行している古いバージョンの Windows Server 上にあるアプリケーションと同じものをホストすることができます。 [Azure Marketplace](https://azure.microsoft.com/marketplace/) イメージを使用して、目的のオペレーティング システムを搭載した仮想マシンにアプリケーションとワークロードを移行します。

    - Windows Server 用のソフトウェア アシュアランスを既にお持ちである場合は、[Azure Hybrid Use Benefit](https://azure.microsoft.com/pricing/hybrid-use-benefit/) で展開してコストを削減できます。 

- Windows Server 用の[ソフトウェア アシュアランス](https://www.microsoft.com/Licensing/licensing-programs/software-assurance-default.aspx) プログラムは、新しいバージョン権利の特典を提供します。 その他の特典の一覧と共に、ソフトウェア アシュアランスを含むサーバーは、しかるべき時が来たら、新しいライセンスを購入しなくても、Window Server の最新バージョンにアップグレードすることができます。 

## <a name="additional-resources"></a>その他の資料

- [Windows Server 2016 で削除された機能または非推奨の機能](deprecated-features.md)
- 一般的なサーバーのアップグレードおよび移行のオプションについては、「[Upgrade and conversion options for Windows Server 2016](Supported-Upgrade-Paths.md)」 (Windows Server 2016 のアップグレードと変換オプション) を参照してください。
- 製品のライフ サイクルとサポート レベルの詳細については、「[サポート ライフ サイクル ポリシーに関する FAQ](https://support.microsoft.com/help/17140/support-lifecycle-policy-faq)」を参照してください。

