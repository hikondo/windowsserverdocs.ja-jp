---
title: 移動
description: Move コマンドの参照記事。1つ以上のファイルを1つのディレクトリから別のディレクトリに移動します。
ms.topic: reference
ms.assetid: fde290a8-d385-450f-8987-ee837fed667d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: cd68c7bcfa1f33eeb977a46a1687bbbab678420f
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640562"
---
# <a name="move"></a>移動

1つ以上のファイルを1つのディレクトリから別のディレクトリに移動します。

> [!IMPORTANT]
> 暗号化されたファイルを暗号化ファイルシステム (EFS) の結果をサポートしていないボリュームに移動すると、エラーが発生します。 まず、ファイルの暗号化を解除するか、EFS をサポートするボリュームにファイルを移動する必要があります。

## <a name="syntax"></a>構文

```
move [{/y|-y}] [<source>] [<target>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| /y | 既存の対象ファイルを上書きするかどうかを確認するメッセージが表示されなくなります。 このパラメーターは、COPYCMD 環境変数で事前に設定されている場合があります。 このプリセットは、 **-y** パラメーターを使用してオーバーライドできます。 既定では、コマンドがバッチスクリプト内から実行される場合を除き、ファイルを上書きする前にプロンプトが表示されます。 |
| -y | 既存の対象ファイルを上書きするかどうかを確認するメッセージが表示されます。 |
| `<source>` | 移動するファイルのパスと名前を指定します。 ディレクトリの移動または名前変更を行うには、 *ソース* が現在のディレクトリのパスと名前である必要があります。 |
| `<target>` | ファイルの移動先のパスと名前を指定します。 ディレクトリの移動または名前変更を行うには、 *ターゲット* が目的のディレクトリパスと名前である必要があります。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

### <a name="examples"></a>例

.Xls 拡張子を持つすべてのファイルを *\Data* ディレクトリから *\ Second_Q \reports* ディレクトリに移動するには、次のように入力します。

```
move \data\*.xls \second_q\reports\
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
