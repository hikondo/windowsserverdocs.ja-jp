---
title: prompt
description: プロンプトコマンドの参照記事。 Cmd.exe コマンドプロンプトをカスタマイズします。
ms.topic: reference
ms.assetid: 3d98e965-02eb-46ad-9d0a-5dc44830373e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/11/2018
ms.openlocfilehash: 8cf91a2a2e78191f035545bc897eceae4c897457
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640321"
---
# <a name="prompt"></a>prompt

現在のディレクトリの名前、時刻と日付、Microsoft Windows のバージョン番号など、必要なテキストを表示するなど、Cmd.exe のコマンドプロンプトを変更します。 パラメーターを指定せずに使用すると、コマンドプロンプトが既定の設定にリセットされます。これは、現在のドライブ文字とディレクトリの後に不等号 () が続き **>** ます。

## <a name="syntax"></a>構文

```
prompt [<text>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<text>` | テキストと、コマンド プロンプトに追加する情報を指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- *Text*パラメーター内の1つ以上の文字列の代わりに、またはその他に含めることができる文字の組み合わせ。

    | 文字 | 説明 |
    |--|--|
    | $q | = (等号) |
    | $$ | $ (ドル記号) |
    | $t | 現在の時刻 |
    | $d | 現在の日付 |
    | $p | 現在のドライブおよびパス |
    | $v | Windows のバージョン番号 |
    | $n | 現在のドライブ |
    | $g | > (符号より大きい) |
    | $l | < (符号未満) |
    | $b | `|` (パイプ記号) |
    | $_ | 改行を入力してください。 |
    | $e | ANSI エスケープ コード (コード 27) |
    | $h | バック スペース (がコマンドラインに書き込まれた文字を削除) する |
    | $、 | & (アンパサンド) |
    | $c | ((左かっこ) |
    | $f | ) (右かっこ) |
    | $s | Space |

- コマンド拡張機能が有効になっている場合、 **prompt** コマンドでは次の書式設定文字がサポートされます。

    | 文字 | 説明 |
    |--|--|
    | $+ | **+** **Pushd**ディレクトリスタックの深さ (プッシュされた各レベルの1文字) に応じて、0個以上の正符号 () 文字。 |
    | $m | 現在のドライブがネットワーク ドライブではない場合は、現在のドライブ文字または空の文字列に関連付けられているリモートの名前。 |

- 含める場合、 **$p** 文字 (現在のドライブとパスを決定) するには、各コマンドを入力した後に、ディスクを読み取るテキスト パラメーターにします。 これにより、特にフロッピー ディスク ドライブの場合の余分な時間がかかります。

### <a name="examples"></a>例

を最初の行と、大なり記号、次の行に現在の時刻と日付で 2 行のコマンド プロンプトを設定するには、次のように入力します。

```
prompt $d$s$s$t$_$g
```

プロンプトに、日付と時刻が現在、次のように変更します。

```
Fri 06/01/2007  13:53:28.91
```

矢印として表示するコマンド プロンプトを設定する (`-->`)、型。

```
prompt --$g
```

既定の設定 (現在のドライブとパスの後に不等号) をコマンド プロンプトを手動で変更するには、次のように入力します。

```
prompt $p$g
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
