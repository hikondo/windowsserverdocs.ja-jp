---
title: ftp get
description: Ftp get コマンドの参照記事。現在のファイル転送の種類を使用してリモートファイルをローカルコンピューターにコピーします。
ms.topic: reference
ms.assetid: d70355c4-58ef-43e0-916b-c7ecf77e6ee4
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 749c32160c58e2d59563b2355fa0b4c6e6a4c82a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89621769"
---
# <a name="ftp-get"></a>ftp get

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

現在のファイル転送の種類を使用して、リモートファイルをローカルコンピューターにコピーします。

> [!NOTE]
> このコマンドは、 [ftp の recv コマンド](ftp-recv.md)と同じです。

## <a name="syntax"></a>構文

```
get <remotefile> [<localfile>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| `<remotefile>` | コピーするリモートファイルを指定します。 |
| `[<localfile>]` | ローカルコンピューターで使用するファイルの名前を指定します。 *Localfile*が指定されていない場合、ファイルには*remotefile*の名前が付けられます。 |

### <a name="examples"></a>例

現在のファイル転送を使用して *test.txt* をローカルコンピューターにコピーするには、次のように入力します。

```
get test.txt
```

現在のファイル転送を使用して*test1.txt*としてローカルコンピューターに*test.txt*をコピーするには、次のように入力します。

```
get test.txt test1.txt
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ftp の recv コマンド](ftp-recv.md)

- [ftp ascii コマンド](ftp-ascii.md)

- [ftp バイナリコマンド](ftp-binary.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
