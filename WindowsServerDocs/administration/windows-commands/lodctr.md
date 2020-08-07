---
title: lodctr
description: Lodctr コマンドのリファレンス記事。これにより、パフォーマンスカウンターの名前とレジストリ設定をファイルに登録または保存し、信頼されたサービスを指定することができます。
ms.topic: article
ms.assetid: 5a849abd-6b31-4833-bc8a-306c05eca29a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 428830b06796914e66434c90f7624cc7c64eec5b
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2020
ms.locfileid: "87887474"
---
# <a name="lodctr"></a>lodctr

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

を使用すると、パフォーマンスカウンターの名前とレジストリ設定をファイルに登録または保存し、信頼されたサービスを指定できます。

## <a name="syntax"></a>構文

```
lodctr <filename> [/s:<filename>] [/r:<filename>] [/t:<servicename>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<filename>` | パフォーマンスカウンターの名前設定と説明文を登録する初期化ファイルの名前を指定します。 |
| /s`<filename>` | パフォーマンスカウンターのレジストリ設定と説明テキストを保存するファイルの名前を指定します。 |
| /r | 現在のレジストリ設定およびレジストリに関連するキャッシュされたパフォーマンスファイルから、カウンターのレジストリ設定と説明文を復元します。 |
| r`<filename>` | パフォーマンスカウンターのレジストリ設定と説明文を復元するファイルの名前を指定します。<p>**警告:** このコマンドを使用すると、すべてのパフォーマンスカウンターのレジストリ設定と説明文が上書きされ、指定したファイルで定義されている構成に置き換えられます。 |
| /t: `<servicename>` | サービスが信頼されていることを示し `<servicename>` ます。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>Remarks

- 入力した情報にスペースが含まれている場合は、テキストを引用符で囲みます ("ファイル名 1" など)。

### <a name="examples"></a>例

現在のパフォーマンスレジストリ設定と説明テキストをファイル *"perf backup1.txt"* に保存するには、次のように入力します。

```
lodctr /s:"perf backup1.txt"
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
