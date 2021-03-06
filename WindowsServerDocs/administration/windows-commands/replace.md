---
title: replace
description: Replace コマンドの参照記事。既存のファイルを置き換えることも、新しいファイルをディレクトリに追加することもできます。
ms.topic: reference
ms.assetid: 6143661e-d90f-4812-b265-6669b567dd1f
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/11/2018
ms.openlocfilehash: 44ece657b87b61bc9be6333644d05b8201061014
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626986"
---
# <a name="replace"></a>replace

ディレクトリ内の既存のファイルを置き換えます。 **/A**オプションと共に使用する場合、このコマンドは既存のファイルを置き換えるのではなく、ディレクトリに新しいファイルを追加します。

## <a name="syntax"></a>構文

```
replace [<drive1>:][<path1>]<filename> [<drive2>:][<path2>] [/a] [/p] [/r] [/w]
replace [<drive1>:][<path1>]<filename> [<drive2>:][<path2>] [/p] [/r] [/s] [/w] [/u]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
|--|--|
| `[<drive1>:][<path1>]<filename>` | ソースファイルまたはファイルのセットの場所と名前を指定します。 *Filename*オプションは必須であり、ワイルドカード文字 (**&#42;** と **?**) を含めることができます。 |
| `[<drive2>:][<path2>]` | コピー先ファイルの場所を指定します。 置換するファイルのファイル名を指定することはできません。 ドライブまたはパスを指定しない場合、このコマンドは現在のドライブとディレクトリをコピー先として使用します。 |
| /a | 既存のファイルを置き換える代わりに、新しいファイルをコピー先のディレクトリに追加します。 このコマンドラインオプションは、 **/s** または **/u** コマンドラインオプションと共に使用することはできません。 |
| /p | コピー先ファイルを置き換える前、またはソースファイルを追加する前に、確認を求めるメッセージが表示されます。 |
| /r | 読み取り専用ファイルと保護されていないファイルを置き換えます。 読み取り専用ファイルを置換しようとしても、 **/r**を指定しなかった場合は、エラーが発生して置換操作が停止されます。 |
| /w | は、ソースファイルの検索を開始する前に、ディスクの挿入を待機します。 **/W**を指定しない場合、このコマンドは enter キーを押すとすぐにファイルの置換または追加を開始します。 |
| /s | コピー先ディレクトリ内のすべてのサブディレクトリを検索し、一致するファイルを置き換えます。 **/S**を **/a**コマンドラインオプションと共に使用することはできません。 このコマンドでは、 *Path1*で指定されているサブディレクトリは検索されません。 |
| /U | コピー先ディレクトリのファイルのうち、ソースディレクトリ内のファイルよりも古いファイルのみを置き換えます。 **/U**を **/a**コマンドラインオプションと共に使用することはできません。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- このコマンドによってファイルが追加または置換されると、ファイル名が画面に表示されます。 このコマンドの実行後、概要行は次のいずれかの形式で表示されます。

  ```
  nnn files added
  nnn files replaced
  no file added
  no file replaced
  ```

- フロッピーディスクを使用していて、このコマンドの実行中にディスクを切り替える必要がある場合は、 **/w** コマンドラインオプションを指定して、このコマンドがディスクの切り替えを待機するようにすることができます。

- このコマンドを使用して、隠しファイルやシステムファイルを更新することはできません。

- 次の表に、各終了コードとその意味の簡単な説明を示します。

  | 終了コード | 説明 |
  |--|--|
  | 0 | このコマンドにより、ファイルが正常に置換または追加されました。 |
  | 1 | このコマンドでは、正しくないバージョンの MS-DOS が検出されました。 |
  | 2 | このコマンドは、ソースファイルを見つけることができませんでした。 |
  | 3 | このコマンドは、転送元または転送先のパスを見つけることができませんでした。 |
  | 5 | 置換するファイルへのアクセス権がユーザーにありません。 |
  | 8 | コマンドを実行するには、システムメモリが不足しています。 |
  | 11 | ユーザーはコマンドラインで間違った構文を使用しています。 |

> [!NOTE]
> バッチプログラムの **if** コマンドラインで ERRORLEVEL パラメーターを使用すると、このコマンドによって返される終了コードを処理できます。

## <a name="examples"></a>例

*Phone. cli*という名前のファイルのすべてのバージョンを更新するには (ドライブ C の複数のディレクトリに表示されます)、次のように入力し*ます。*

```
replace a:\phones.cli c:\ /s
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
