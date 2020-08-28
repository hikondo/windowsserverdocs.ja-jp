---
title: logman import および logman export
description: Logman インポートおよび logman エクスポートに関するリファレンス記事。 XML ファイルからデータコレクターセットをインポートしたり、データコレクターセットを XML ファイルにエクスポートしたりします。
ms.topic: reference
ms.assetid: c258daba-fb93-47c0-a53b-2fe83ed2c743
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5fb750b2ba514c28b05b7b7817994aef3b83eb62
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89023796"
---
# <a name="logman-import-and-logman-export"></a>logman import および logman export

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

XML ファイルからデータコレクターセットをインポートするか、データコレクターセットを XML ファイルにエクスポートします。

## <a name="syntax"></a>構文

```
logman import <[-n] <name> <-xml <name> [options]
logman export <[-n] <name> <-xml <name> [options]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| -s `<computer name>` | 指定したリモートコンピューターでコマンドを実行します。 |
| -config `<value>` | コマンドオプションを含む設定ファイルを指定します。 |
| [-n] `<name>` | 対象オブジェクトの名前。 |
| -xml `<name>` | インポートまたはエクスポートする XML ファイルの名前。 |
| -/ | イベントトレースセッションに直接コマンドを送信します。保存もスケジュールもされません。 |
| -[-] u `<user [password]>` | として実行するユーザーを指定します。 パスワードのを入力すると、パスワードの入力を `*` 求めるメッセージが表示されます。 パスワードは、パスワード用プロンプトで入力した場合は表示されません。 |
| -y | プロンプトを表示せずにすべての質問に対する回答を表示します。 |
| /? | 状況依存のヘルプを表示します。 |

### <a name="examples"></a>例

XML ファイル *c:\windows\perf_log.xml* をコンピューター *server_1* から *perf_log*というデータコレクターセットとしてインポートするには、次のように入力します。

```
logman import perf_log -s server_1 -xml c:\windows\perf_log.xml
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [logman コマンド](logman.md)
