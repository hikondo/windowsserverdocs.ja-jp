---
title: ftp literal
description: リモート ftp サーバーに逐語的引数を送信する ftp リテラルコマンドの参照記事です。
ms.topic: reference
ms.assetid: fb81aa2d-07fa-4e79-bf44-1fb5526fdf14
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ff0f322d3b2ff63705077165ad73f58830cee216
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89023866"
---
# <a name="ftp-literal"></a>ftp literal

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

は、逐語的引数をリモート ftp サーバーに送信します。 単一の ftp 応答コードが返されます。

> [!NOTE]
> このコマンドは、 [ftp 引用符コマンド](ftp-quote.md)と同じです。

## <a name="syntax"></a>構文

```
literal <argument> [ ]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<argument>` | Ftp サーバーに送信する引数を指定します。 |

### <a name="examples"></a>例

リモート ftp サーバーに **quit** コマンドを送信するには、次のように入力します。

```
literal quit
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ftp 引用符コマンド](ftp-quote.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
