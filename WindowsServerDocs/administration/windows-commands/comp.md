---
title: comp
description: Comp コマンドの参照記事。2つのファイルまたはファイルのセットの内容をバイト単位で比較します。
ms.topic: reference
ms.assetid: 40319d23-704d-4da1-be93-8259547275d0
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 15859b06ffb402feb05bf3dee3bad5462093a888
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89629438"
---
# <a name="comp"></a>comp

2つのファイルまたはファイルのセットの内容をバイト単位で比較します。 これらのファイルは、同じドライブまたは別のドライブに保存することも、同じディレクトリまたは別のディレクトリに格納することもできます。 このコマンドは、ファイルを比較するときに、その場所とファイル名を表示します。 パラメーターを指定せずに使用した場合、 **comp** で比較するファイルを入力するように求められます。

## <a name="syntax"></a>構文

```
comp [<data1>] [<data2>] [/d] [/a] [/l] [/n=<number>] [/c]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<data1>` | 比較する1つ目のファイルまたはファイルのセットの場所と名前を指定します。 ワイルドカード文字 (**&#42;** と **?**) を使用して、複数のファイルを指定できます。 |
| `<data2>` | 比較する2番目のファイルまたは一連のファイルの場所と名前を指定します。 ワイルドカード文字 (**&#42;** と **?**) を使用して、複数のファイルを指定できます。 |
| /d | 10進数形式での相違点を表示します。 (既定の形式は16進数です)。 |
| /a | 文字の違いを表示します。 |
| /l | バイトオフセットを表示するのではなく、相違が発生した行の番号を表示します。 |
| /n =`<number>` | ファイルのサイズが異なる場合でも、各ファイルに指定されている行数のみを比較します。 |
| /c | 大文字と小文字を区別しない比較を実行します。 |
| /off [行] | オフライン属性が設定されたファイルを処理します。 |
| /? | コマンド プロンプトでヘルプを表示します。 |

## <a name="remarks"></a>注釈

- 比較中、 **comp** では、ファイル間の異なる情報の場所を識別するメッセージが表示されます。 各メッセージは、等しくないバイトのオフセットメモリアドレスとバイトの内容 ( **/a** または **/d** コマンドラインパラメーターが指定されていない場合は16進表記) を示します。 メッセージは次の形式で表示されます。

    ```
    Compare error at OFFSET xxxxxxxx
    file1 = xx
    file2 = xx
    ```

    10個の等しくない比較を実行すると、 **comp** でファイルの比較が停止し、次のメッセージが表示されます。

    `10 Mismatches - ending compare`

- *Data1*または*data2*の必要なコンポーネントを省略した場合、または*data2*を完全に省略した場合、このコマンドは、不足している情報の入力を求めます。

- *Data1*にファイル名のないドライブ文字またはディレクトリ名のみが含まれている場合、このコマンドは、指定されたディレクトリ内のすべてのファイルを、 *data1*に指定されたファイルと比較します。

- *Data2*にドライブ文字またはディレクトリ名のみが含まれている場合、 *data2*の既定のファイル名は、 *data1*の場合と同じになります。

- **Comp**コマンドで指定されたファイルが見つからない場合は、他のファイルを比較するかどうかを確認するメッセージが表示されます。

- 異なるディレクトリまたは異なるドライブにある場合は、比較するファイルのファイル名を同じにすることができます。 ワイルドカード文字 (**&#42;** と **?**) を使用して、ファイル名を指定できます。

- さまざまなサイズのファイルを比較するには、 **/n** を指定する必要があります。 ファイルサイズが異なり、 **/n** が指定されていない場合は、次のメッセージが表示されます。

    ```
    Files are different sizes
    Compare more files (Y/N)?
    ```

    これらのファイルを比較するには、 **N** キーを押してコマンドを停止します。 次に、 **/n**オプションを使用して**comp**コマンドをもう一度実行し、各ファイルの最初の部分のみを比較します。

- ワイルドカード文字 (**&#42;** と **?**) を使用して複数のファイルを指定した場合、 **comp** は、 *data1* に一致する最初のファイルを検索し、それを *data2*内の対応するファイル (存在する場合) と比較します。 **Comp**コマンドは、 *data1*に一致する各ファイルの比較結果を報告します。 完了すると、 **カンプ** には次のメッセージが表示されます。

    `Compare more files (Y/N)?`

    他のファイルを比較するには、 **Y**キーを押します。 **Comp** コマンドを実行すると、新しいファイルの場所と名前を入力するように求められます。 比較を停止するには、 **N**キーを押します。 **Y**キーを押すと、使用するコマンドラインオプションを入力するように求められます。 コマンドラインオプションを指定しない場合、 **カンプ** では、前に指定したものが使用されます。

## <a name="examples"></a>例

ディレクトリ *c:\ レポート* の内容をバックアップディレクトリと比較するには `\\sales\backup\april` 、次のように入力します。

```
comp c:\reports \\sales\backup\april
```

*\ Invoice*ディレクトリ内のテキストファイルの最初の10行を比較し、結果を10進形式で表示するには、次のように入力します。

```
comp \invoice\*.txt \invoice\backup\*.txt /n=10 /d
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)