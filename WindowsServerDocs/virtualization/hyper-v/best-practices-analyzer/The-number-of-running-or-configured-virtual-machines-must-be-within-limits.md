---
title: 実行中の数や、構成された仮想マシンがサポートされている制限内になければなりません
description: このベスト プラクティス アナライザー ルールによって報告された問題を解決する方法を説明します。
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 9d3c4aa3-8416-46ec-a253-26dc98088d7b
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 8a971a48b2d8199a6c279f1bd3f1715039fa6e0d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59855353"
---
# <a name="the-number-of-running-or-configured-virtual-machines-must-be-within-supported-limits"></a>実行中の数や、構成された仮想マシンがサポートされている制限内になければなりません

>適用先:Windows Server 2016

ベスト プラクティスとスキャンの詳細については、次を参照してください。 [Run Best Practices Analyzer Scans and Manage Scan Results](https://go.microsoft.com/fwlink/p/?LinkID=223177)します。  
  
|プロパティ|詳細|  
|-|-|  
|**オペレーティング システム**|Windows Server 2016|  
|**製品/機能**|Hyper-V|  
|**重要度**|エラー  
|**カテゴリ**|構成|  
  
次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示されるテキストを示します。  
  
## <a name="issue"></a>問題  
*多くの仮想マシンには、実行中またはサポートされているよりも構成されているです。*  
  
## <a name="impact"></a>影響  
*Microsoft は、仮想マシンを実行しているか、このサーバーで構成の現在の数をサポートしていません。*  
  
## <a name="resolution"></a>解決方法  
*1 つまたは複数の仮想マシンを別のサーバーに移動します。*  
  
実行中の仮想マシンの数など、HYPER-V の最大のサポートされる構成の詳細については「 [Windows Server 2016 での HYPER-V のスケーラビリティの計画](../plan/Plan-for-Hyper-V-scalability-in-Windows-Server-2016.md)します。  
  
仮想マシンを別のサーバーに移動するには、次のことができます。  
  
- 現在のサーバーからバーチャル マシンをエクスポートしてインポートして、新しいサーバーに以下に示すよう。   
- ライブ マイグレーションの操作を行います。   
    - このサーバーがフェールオーバー クラスターに所属している場合は、フェールオーバー クラスタ リング機能で提供されるツールを使用します。 手順については、次を参照してください。 [ライブ マイグレーション、クイック移行、またはノードのノードから移動、バーチャル マシン](https://go.microsoft.com/fwlink/?LinkID=181519)します。  
    - これは、スタンドアロン サーバーでの手順を参照して [ライブ マイグレーションの構成およびフェールオーバー クラスタ リングのないバーチャル マシンの移行](https://technet.microsoft.com//library/jj134199(v=ws.11).aspx)  
  
### <a name="to-export-a-virtual-machine"></a>仮想マシンをエクスポートするには  
  
   > [!IMPORTANT]  
   > エクスポートする HYPER-V ホストをドメインに属している、リモートの場所にエクスポートされたファイルを格納する場合は、制約付き委任用 HYPER-V ホストを構成する必要があります。 リモートの場所は、共有ネットワーク フォルダーまたはにインポートしているホスト上のフォルダーにあります。 制約付き委任には、委任された資格情報でリモート コンピューターに共通インターネット ファイル システム (CIFS) サービスは、HYPER-V ホストのコンピューター アカウントことができます。 制約付き委任を構成する手順についてには、次のエクスポートを参照してくださいし、下手順についてをインポートします。  
  
1.  Hyper-V マネージャーを開きます。 **[スタート]** ボタンをクリックし、**[管理ツール]** をポイントして **[Hyper-V マネージャー]** をクリックします。  
  
2.  結果ウィンドウで  **仮想マシン**, 、仮想マシンを右クリックし、 **エクスポート**します。  
  
3.  **バーチャル マシンをエクスポート** ダイアログ ボックスで、型、またはバーチャル マシンのリソースのすべてを保存するための十分な空き容量がある場所を指定します。 仮想マシンをエクスポートする場合は、すべてのバーチャル ハード_ディスク (.vhd ファイルまたは .vhdx ファイル)、チェックポイント (.avhd ファイル)、および仮想マシンに関連付けられている保存された状態ファイルが、指定したフォルダーにコピーされます。  
  
4.  **[Export]** (エクスポート) をクリックします。  
  
仮想マシンをエクスポートした後は、他のサーバーに仮想マシンをインポートします。  
  
### <a name="to-import-a-virtual-machine-to-another-server"></a>仮想マシンを別のサーバーにインポートするには  
  
1.  HYPER-V を実行しているサーバーに接続し、HYPER-V マネージャーを開きます。  
  
2.  **アクション**  ウィンドウで、をクリックして **仮想マシンのインポート**します。  
  
3.  **仮想マシンのインポート**  ダイアログ ボックスで、仮想マシンをエクスポートした場所を指定します。 このバーチャル マシンを再インポートする場合を除きはそのままインポート設定します。  
  
4.  **[インポート]** をクリックします。  
  
### <a name="to-configure-constrained-delegation"></a>制約付き委任を構成するには  
  
メンバーシップ、 **Domain Administrators** グループは、この手順を実行するために必要なです。  
  
1.  Active Directory ドメイン サービス ツール機能がインストールになっているコンピューターで **管理ツール**, 、開かれている **Active Directory ユーザーとコンピューター**, 、し、HYPER-V を実行しているコンピューターのコンピューター アカウントに移動します。  
  
    > [!NOTE]  
    > 場合 **Active Directory ユーザーとコンピューター** が記載されていない Active Directory ドメイン サービス ツール機能をインストールします。 手順については、次を参照してください。 [AD DS 用にリモート サーバー管理ツールをインストールする](https://go.microsoft.com/fwlink/?LinkId=140463)(https://go.microsoft.com/fwlink/?LinkId=140463)します。  
  
2.  HYPER-V を実行しているコンピューターのコンピューター アカウントを右クリックし、をクリックし、 **プロパティ**します。  
  
3.  **[委任]** タブで、**[指定されたサービスへの委任でのみこのコンピューターを選択する]** を選択してから、**[認証プロトコルを使う]** を選択します。  
  
4.  HYPER-V コンピューター アカウントは、リモート コンピューターに委任された資格情報を表示するためには。  
  
    1.  **[追加]** をクリックします。  
  
    2.  **サービスの追加** ダイアログ ボックスで、をクリックして **ユーザーまたはコンピューター**, をリモート コンピューターを選択してクリックして **[ok]** します。  
  
    3.  **利用可能なサービス** ボックスの一覧で、 **cifs** プロトコル (サーバー メッセージ ブロック (SMB) プロトコルとも呼ばれます) をクリックして **追加**します。  
  
  
  

