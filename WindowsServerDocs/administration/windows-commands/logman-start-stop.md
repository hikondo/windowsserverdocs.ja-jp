---
title: logman start および logman stop
description: Logman start および logman stop コマンドのリファレンス記事。データコレクターを起動し、開始時刻を手動に設定します。または、データコレクターセットを停止し、終了時刻を手動に設定します。
ms.topic: reference
ms.assetid: a40006a1-876e-474b-aaf1-f365c730deea
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5b573ecd78ad9f062162d2c1ad16d59aebe740ee
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038863"
---
# <a name="logman-start-and-logman-stop"></a>logman start および logman stop

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

**Logman start**コマンドは、データコレクターを起動し、開始時刻を手動に設定します。 **Logman stop**コマンドは、データコレクターセットを停止し、終了時刻を手動に設定します。

## <a name="syntax"></a>構文

```
logman start <[-n] <name>> [options]
logman stop <[-n] <name>> [options]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| -s `<computer name>` | 指定したリモートコンピューターでコマンドを実行します。 |
| -config `<value>` | コマンドオプションを含む設定ファイルを指定します。 |
| [-n] `<name>` | ターゲットオブジェクトの名前を指定します。 |
| -/ | イベントトレースセッションに直接コマンドを送信します。保存もスケジュールもされません。 |
| -as | 要求された操作を非同期的に実行します。 |
| -? | 状況依存のヘルプを表示します。 |

### <a name="examples"></a>例

データコレクター *perf_log*を開始するには、[リモートコンピューター *server_1*で次のように入力します。

```
logman start perf_log -s server_1
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [logman コマンド](logman.md)
