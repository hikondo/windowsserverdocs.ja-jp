---
title: pause
description: 一時停止コマンドの参照記事。バッチプログラムの処理を中断します。
ms.topic: reference
ms.assetid: cab3afc3-d046-432f-a0bf-6282f0099032
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4611980b0f805843b1f93c20450163f01e362cf8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640660"
---
# <a name="pause"></a>pause

バッチプログラムの処理を中断し、プロンプトを表示します。 `Press any key to continue . . .`

## <a name="syntax"></a>構文

```
pause
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="remarks"></a>注釈

- CTRL + C キーを押してバッチプログラムを停止すると、次のメッセージが表示され `Terminate batch job (Y/N)?` ます。 このメッセージに応答して **Y** (yes の場合) を押すと、バッチプログラムが終了し、制御がオペレーティングシステムに戻ります。

- 挿入することができます、 **を一時停止** コマンドを処理したくないバッチ ファイルのセクションまでにします。 **一時停止**時に batch プログラムの処理が中断された場合は、CTRL + C キーを押してから**Y**キーを押してバッチプログラムを停止することができます。

## <a name="examples"></a>例

いずれのドライブでディスクを変更するユーザーの入力を要求するバッチ ファイルを作成するには、次のように入力します。

```
@echo off
:Begin
copy a:*.*
echo Put a new disk into Drive A
pause
goto begin
```

この例では、ドライブ A のディスクにあるすべてのファイルが現在のディレクトリにコピーされます。 新しいディスクをドライブ A に挿入するようにメッセージが表示された後、 **一時停止** コマンドを実行すると、ディスクを変更し、任意のキーを押して処理を再開できるように処理が中断されます。 このバッチ ファイルは、無限ループで実行される —、 **goto 開始** コマンドは、バッチ ファイルの先頭のラベルに、コマンド インタープリターを送信します。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)