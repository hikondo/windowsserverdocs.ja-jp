---
title: ftp open
description: 指定された ftp サーバーに接続する、ftp open コマンドの参照記事です。
ms.topic: reference
ms.assetid: 4b61926a-dc60-4b4c-96d3-64e5c91c18ba
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a7599eb4728a46655b4c3274a9d7708061c3a9ee
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89032820"
---
# <a name="ftp-open"></a>ftp open

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定された ftp サーバーに接続します。

## <a name="syntax"></a>構文

```
open <computer> [<port>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<computer>` | 接続を試みているリモート コンピューターを指定します。 IP アドレスまたはコンピューター名を使用できます (この場合、DNS サーバーまたはホストファイルを使用できる必要があります)。 |
| `[<port>]` | Ftp サーバーへの接続に使用する TCP ポート番号を指定します。 既定では、TCP ポート 21 を使用します。 |

### <a name="examples"></a>例

*Ftp.microsoft.com*で ftp サーバーに接続するには、次のように入力します。

```
open ftp.microsoft.com
```

TCP ポート*755*でリッスンしている*ftp.microsoft.com*で ftp サーバーに接続するには、次のように入力します。

```
open ftp.microsoft.com 755
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
