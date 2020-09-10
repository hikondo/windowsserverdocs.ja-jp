---
title: 編集
description: '[編集] コマンドの参照記事。これにより、MS-DOS エディターが起動され、ASCII テキストファイルを作成および変更できるようになります。'
ms.topic: reference
ms.assetid: 4e0ff2e8-3518-47c1-8c69-5e93f895fa0e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b3723c65456fd7e17395cd7a9bc931ddc56a09b3
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89636176"
---
# <a name="edit"></a>編集

ASCII テキストファイルを作成および変更する MS-DOS エディターを起動します。

## <a name="syntax"></a>構文

```
edit [/b] [/h] [/r] [/s] [/<nnn>] [[<drive>:][<path>]<filename> [<filename2> [...]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `[<drive>:][<path>]<filename> [<filename2> [...]]` | 1つ以上の ASCII テキストファイルの場所と名前を指定します。 ファイルが存在しない場合は、MS-DOS エディターによって作成されます。 ファイルが存在する場合は、MS-DOS エディターが開き、その内容が画面に表示されます。 *Filename*オプションには、ワイルドカード文字 (**&#42;** と **?**) を含めることができます。 複数のファイル名をスペースで区切ります。 |
| /b | 白黒モードで、MS-DOS エディターが白黒で表示されるようにします。 |
| /h | 現在のモニターで使用できる最大行数を表示します。 |
| /r | 読み取り専用モードでファイルを読み込みます。 |
| /s | 短いファイル名の使用を強制します。 |
| `<nnn>` | バイナリファイルを読み込み、行を *nnn* 文字幅に折り返します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- 追加のヘルプを表示するには、MS-DOS エディターを開き、F1 キーを押します。

- 一部のモニターでは、ショートカットキーの表示が既定でサポートされていません。 モニターにショートカットキーが表示されない場合は、 **/b**を使用します。

### <a name="examples"></a>例

MS-DOS エディターを開くには、次のように入力します。

```
edit
```

現在のディレクトリ内の *newtextfile.txt* という名前のファイルを作成して編集するには、次のように入力します。

```
edit newtextfile.txt
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
