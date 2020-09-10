---
title: アドインのインストール
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.topic: article
ms.assetid: e62e4f07-c2ba-4c5e-b30c-bdc287cd654e
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 32bb6be1ff24823d628e23945849b5030d6e0723
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626323"
---
# <a name="install-add-ins"></a>アドインのインストール

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

イメージを作成する前にアドインをインストールすることで、すべてのサーバーまたはクライアント コンピューターにアドインを含めることができます。 これらのアドインは、そのイメージを使用してレプリケートされたすべてのコンピューターに自動的に含まれます。 1 個のアドインをインストールするには .wssx ファイルを実行します。または、アドインの種類ごとに [SDK ドキュメント](https://go.microsoft.com/fwlink/?LinkID=248648)のガイダンスに従って、個別のアドイン ファイルをインストールします。 .wssx ファイルを使用してインストールすると、アドイン マネージャーを通じてアドインをアンインストールできます。 個別のファイルをインストールする場合、アドインはアドイン マネージャーから管理されません。

> [!NOTE]
>  サーバーにインストールまたはダウンロードされたソフトウェア (ダッシュボードのタブや正常性通知など) のインターフェイスは、サーバーにインストールされているオペレーティング システムと同じ言語にローカライズされている必要があります。

#### <a name="to-install-an-add-in"></a>アドインをインストールするには

1.  (省略可能) .wssx ファイルを使用してアドインをインストールしている場合、次の手順を完了します。

    1.  <AddinName \> . wssx ファイルを参照コンピューターに保存します。

    2.  .wssx ファイルをダブルクリックして、アドインのインストール ウィザードを開きます。

    3.  ウィザードの指示に従って、インストールを完了させます。

2.  (省略可能) 個別のアドイン ファイルを、アドインの種類ごとに SDK で定義されたように適切な場所にインストールします。

## <a name="see-also"></a>参照
 [イメージの作成とカスタマイズ追加の](Creating-and-Customizing-the-Image.md)[カスタマイズ](Additional-Customizations.md)[展開のイメージの準備](Preparing-the-Image-for-Deployment.md)[カスタマーエクスペリエンスのテスト](Testing-the-Customer-Experience.md)