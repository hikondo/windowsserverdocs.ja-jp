---
title: logman
description: Logman コマンドのリファレンス記事。イベントトレースセッションとパフォーマンスログを作成して管理し、コマンドラインからのパフォーマンスモニターの多くの機能をサポートします。
ms.topic: reference
ms.assetid: 574a5203-5b3b-4759-a678-f26d00dde447
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ac3e541436ca6f3b0e9d7c0dc03154ffefdfda0d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639514"
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