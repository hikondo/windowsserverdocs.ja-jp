---
title: ツール拡張機能に iFrame を追加する
description: ツール拡張機能の開発 Windows 管理センター SDK (Project ホノルル)-ツール拡張に iFrame を追加する
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: da145d4ef3a58af51846d395081fb643af7c78ac
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87945109"
---
# <a name="add-an-iframe-to-a-tool-extension"></a>ツール拡張機能に iFrame を追加する

>適用先:Windows Admin Center、Windows Admin Center Preview

この記事では、Windows 管理センター CLI で作成した新しい空のツール拡張機能に iFrame を追加します。

## <a name="prepare-your-environment"></a>環境を準備する ##

まだ行っていない場合は、「[ツール拡張機能の開発](../develop-tool.md)」の指示に従って、環境を準備し、新しい空のツール拡張を作成します。

## <a name="add-a-module-to-your-project"></a>モジュールをプロジェクトに追加する ##

新しい空の[モジュール](add-module.md)をプロジェクトに追加します。ここでは、次の手順で iFrame を追加します。

## <a name="add-an-iframe-to-your-module"></a>モジュールに iFrame を追加する ##

ここで、作成した新しい空のモジュールに iFrame を追加します。

アプリケーションで、 \, モジュールフォルダーを参照し、 ```{!module-name}.component.html``` 次の名前付け規則に従ってファイルを開きます。

| 値 | 説明 | ファイル名の例 |
| ----- | ----------- | ------- |
| ```{!module-name}``` | モジュール名 (小文字、スペースをダッシュに置換) | ```manage-foo-works-portal.component.html``` |

次の内容を html ファイルに追加します。

``` html
<div>
  <iframe  style="height: 850px;" src="https://www.bing.com"></iframe>
</div>
```

これで、拡張機能に iFrame が追加されました。  次に、Windows 管理センターで拡張機能を[ビルドしてサイドロード](../develop-tool.md#build-and-side-load-your-extension)し、結果を確認することができます。

> [!Note]
> コンテンツセキュリティポリシー (CSP) の設定により、一部のサイトが Windows 管理センター内の iFrame で表示されない可能性があります。 詳細については、[こちら](https://content-security-policy.com/)を参照してください。
