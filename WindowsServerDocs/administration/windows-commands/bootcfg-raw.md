---
title: bootcfg raw
description: Bootcfg raw コマンドのリファレンス記事。文字列として指定されたオペレーティングシステムの読み込みオプションを、Boot.ini ファイルのオペレーティングシステムセクションのオペレーティングシステムエントリに追加します。
ms.topic: reference
ms.assetid: e3458749-b0a0-460f-a022-3ff199a71f27
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b86945a126c73742982ea01442101c6d1250226d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630144"
---
# <a name="bootcfg-raw"></a>bootcfg raw

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

文字列として指定されたオペレーティングシステムの読み込みオプションを、Boot.ini ファイルの [オペレーティングシステム] セクションのオペレーティングシステムエントリに追加します。 このコマンドは、既存のオペレーティングシステムのエントリオプションを上書きします。

## <a name="syntax"></a>構文

```
bootcfg /raw [/s <computer> [/u <domain>\<user> /p <password>]] <osloadoptionsstring> [/id <osentrylinenum>] [/a]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| `/s <computer>` | リモートコンピューターの名前または IP アドレスを指定します (円記号は使用しないでください)。 既定値はローカル コンピューターです。 |
| `/u <domain>\<user>`  | またはによって指定されたユーザーのアカウントアクセス許可を使用してコマンドを実行し `<user>` `<domain>\<user>` ます。 既定値は、コマンドを実行しているコンピューターの現在のログオンユーザーのアクセス許可です。 |
| `/p <password>` | 指定されているユーザー アカウントのパスワードを指定します、 **/u** パラメーター。 |
| `<osloadoptionsstring>` | オペレーティングシステムエントリに追加するオペレーティングシステムの読み込みオプションを指定します。 これらの読み込みオプションは、オペレーティングシステムエントリに関連付けられている既存の読み込みオプションを置き換えます。 パラメーターに対する検証は行われません `<osloadoptions>` 。
| `/id <osentrylinenum>` | オペレーティングシステムの読み込みオプションが追加される Boot.ini ファイルの [オペレーティングシステム] セクションのオペレーティングシステムエントリの行番号を指定します。 [オペレーティングシステム] セクションヘッダーの後の最初の行は1です。 |
| /a | 既存のオペレーティングシステムオプションに追加するオペレーティングシステムオプションを指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

このテキストに**は、有効**な OS 読み込みオプション ( **/debug**、 **/fastdetect**、 **/nodebug**、 **/crashdebug**、 **/sos**など) が含まれている必要があります。

最初のオペレーティングシステムエントリの末尾に **/debug/fastdetect** を追加するには、以前のオペレーティングシステムエントリのオプションを置き換えます。

```
bootcfg /raw /debug /fastdetect /id 1
```

**Bootcfg/raw**コマンドを使用するには、次のようにします。

```
bootcfg /raw /debug /sos /id 2
bootcfg /raw /s srvmain /u maindom\hiropln /p p@ssW23 /crashdebug  /id 2
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bootcfg コマンド](bootcfg.md)
