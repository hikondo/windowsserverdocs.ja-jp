---
title: logman
description: Logman コマンドのリファレンス記事。イベントトレースセッションとパフォーマンスログを作成して管理し、コマンドラインからのパフォーマンスモニターの多くの機能をサポートします。
ms.topic: reference
ms.assetid: 574a5203-5b3b-4759-a678-f26d00dde447
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b155e3cca0b9f5e35c1c817cfee4e96ca79b6610
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030550"
---
# <a name="logman"></a>logman

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

コマンド ラインから、イベント トレース セッションとパフォーマンス ログを作成、管理します。パフォーマンス モニターの多くの関数をサポートしています。

## <a name="syntax"></a>構文

```
logman [create | query | start | stop | delete| update | import | export | /?] [options]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| [logman create](logman-create.md) | カウンター、トレース、構成データコレクター、または API を作成します。 |
| [logman query](logman-query.md) | データコレクターのプロパティを照会します。 |
| [logman start &#124; stop](logman-start-stop.md) | データコレクションを開始または停止します。 |
| [logman delete](logman-delete.md) | 既存のデータコレクターを削除します。 |
| [logman update](logman-update.md) | 既存のデータコレクターのプロパティを更新します。 |
| [logman import &#124; export](logman-import-export.md) | XML ファイルからデータコレクターセットをインポートするか、データコレクターセットを XML ファイルにエクスポートします。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)