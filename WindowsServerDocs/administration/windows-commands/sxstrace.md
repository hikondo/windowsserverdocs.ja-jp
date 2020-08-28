---
title: sxstrace
description: サイドバイサイドの問題を診断する方法について説明します。
ms.topic: reference
ms.assetid: fcd26eeb-fbd9-4a86-b6a9-dfa5e9c6e4fc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4a5398a9dcab96719de998a86bfa74df67a3f39b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024596"
---
# <a name="sxstrace"></a>sxstrace

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サイド バイ サイドの問題を診断します。

## <a name="syntax"></a>構文
```
sxstrace [{[trace -logfile:<FileName> [-nostop]|[parse -logfile:<FileName> -outfile:<ParsedFile>  [-filter:<AppName>]}]
```

#### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|trace|Sxs (サイド バイ サイド) のトレースを有効に|
|-logfile|未処理のログ ファイルを指定します。|
|\<FileName>|トレース ログが保存 *FileName*します。|
|-nostop|トレースを停止するように求めるメッセージは指定されません。|
|parse|生のトレース ファイルに変換します。|
|-出力|出力ファイル名を指定します。|
|\<ParsedFile>|解析されたファイルのファイル名を指定します。|
|-filter|フィルター選択される出力を使用します。|
|\<AppName>|アプリケーション名を示します。|
|stoptrace|前に停止していない場合は、トレースを停止します。|
|-?|コマンド プロンプトにヘルプを表示します。|

## <a name="examples"></a>例
トレースを有効にして、トレース ファイルを保存して **sxstrace.etl**:
```
sxstrace trace -logfile:sxstrace.etl
```
生のトレース ファイルを人間が読める形式に変換し、結果を保存 **sxstrace.txt**:
```
sxstrace parse -logfile:sxstrace.etl -outfile:sxstrace.txt
```

## <a name="additional-references"></a>その他の参照情報
- [コマンド ライン構文の記号](command-line-syntax-key.md)

