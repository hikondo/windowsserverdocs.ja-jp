---
title: 正常性アラートの追加
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 270e0aac-dc42-46f3-a20b-a68ffbded06d
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 3a3c04a48e06ef0040943b866eaf1ddb0be8fa89
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624076"
---
# <a name="add-health-alerts"></a>正常性アラートの追加

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

正常性アドインは、アラートの定義、正常性チェック、ネットワークの問題の修復を提供します。 正常性アドインは、特定の機能の正常性情報を評価するために使用されるコードまたはデータをコメントする xml ファイルから構成されます。 正常性アドインは、開発者によって作成され、管理者によってサーバーとクライアント コンピューターにインストールされます。

 正常性アドインの作成の詳細については、 [Windows Server Solutions SDK](https://go.microsoft.com/fwlink/?LinkID=248648) を参照してください。

## <a name="installing-health-add-in-files"></a>正常性アドインのファイルをインストールする
 開発者による xml ファイルの作成後、ファイルのコピーをサーバーとクライアント コンピューター上の適切な場所に配置する必要があります。

#### <a name="to-install-the-xml-files-on-the-server"></a>XML ファイルをサーバーにインストールするには

1. **%ProgramFiles%\Windows Server\Bin\Feature Definitions** フォルダーで、 **MyHealthAddIn**という名前の新しいフォルダーを作成します。 このフォルダーには任意の名前を付けることができます。 フォルダーの名前は、機能名と同じにすることを推奨します。

2. Definition.xml ファイルと Definition.xml.config ファイルを新しいフォルダーにコピーします。

3. 条件または操作用にバイナリ ファイルを作成した場合、これらのファイルも **%ProgramFiles%\Windows Server\Bin** にコピーする必要があります。

   クライアント コンピューターが、XML ファイルを適切な場所に抽出するスケジュールされたタスクを 6 時間ごとに実行します。 クライアント コンピューターとサーバーを強制的に同期させるには、このタスクを手動で実行します。

#### <a name="to-install-the-xml-files-on-the-client-computer"></a>XML ファイルをクライアント コンピューターにインストールするには

1.  タスク スケジューラを開きます。

2.  タスク スケジューラで **HealthDefintionUpdateTask** を実行します。

    > [!NOTE]
    >  このタスクでは、バイナリ ファイルはインストールされません。 バイナリ ファイルは、クライアント コンピューターの **%ProgramFiles%\Windows Server\Bin** フォルダーに手動でコピーする必要があります。

## <a name="see-also"></a>参照
 [イメージの作成とカスタマイズ追加の](Creating-and-Customizing-the-Image.md)[カスタマイズ](Additional-Customizations.md)[展開のイメージの準備](Preparing-the-Image-for-Deployment.md)[カスタマーエクスペリエンスのテスト](Testing-the-Customer-Experience.md)