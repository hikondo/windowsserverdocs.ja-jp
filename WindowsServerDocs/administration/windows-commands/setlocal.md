---
title: setlocal
description: 'Windows コマンドに関するトピック * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4e4b6d3-3f1a-4851-a782-25ee2470e16e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 997c996854f488bb1776f135e3288e3b094e683c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71384093"
---
# <a name="setlocal"></a>setlocal



バッチ ファイルで環境変数のローカライズを開始します。 ローカライズが一致するまで **endlocal** コマンドが見つかるまたはバッチ ファイルの末尾に到達します。

このコマンドを使用する方法の例については、[例](#BKMK_examples)を参照してください。

## <a name="syntax"></a>構文

```
setlocal [enableextensions | disableextensions] [enabledelayedexpansion | disabledelayedexpansion]
```

## <a name="arguments"></a>引数

|引数|説明|
|--------|-----------|
|enableextensions|一致するまでコマンド拡張機能を有効 **endlocal** する前に設定に関係なく、コマンドが発生しました、 **setlocal** コマンドが実行されました。|
|disableextensions|一致するまでコマンド拡張機能を無効に **endlocal** する前に設定に関係なく、コマンドが発生しました、 **setlocal** コマンドが実行されました。|
|enabledelayedexpansion|により、一致するまで遅延環境変数の拡張 **endlocal** する前に設定に関係なく、コマンドが発生しました、 **setlocal** コマンドが実行されました。|
|disabledelayedexpansion|一致するまで遅延環境変数の拡張を無効に **endlocal** する前に設定に関係なく、コマンドが発生しました、 **setlocal** コマンドが実行されました。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>コメント

-   使用して **setlocal**

    使用すると **setlocal** スクリプトまたはバッチ ファイルの外部で影響を与えません。
-   環境変数を変更します。

    使用 **setlocal** バッチ ファイルを実行すると、環境変数を変更します。 実行した後で変更した環境 **setlocal** バッチ ファイルに対してローカルです。 Cmd.exe プログラムが検出した場合に、以前の設定を復元する **endlocal** コマンドまたはバッチ ファイルの末尾に到達します。
-   入れ子のコマンド

    1 つ以上を持つことができます **setlocal** または **endlocal** コマンド バッチ プログラム (つまり、入れ子になったコマンド) を実行します。
-   バッチ ファイルでコマンド拡張機能のためのテスト

    **Setlocal** ERRORLEVEL 変数を設定します。 渡した場合 {**enableextensions** | **disableextensions**} または {**enabledelayedexpansion** | **disabledelayedexpansion**}、ERRORLEVEL 変数に設定されている **0** (ゼロ)。 設定されている場合は、 **1**します。 バッチ スクリプトでこの情報を使用すると、次の例で示すように拡張機能は、使用できるかどうかを決定します。  
    ```
    setlocal enableextensions
    verify other 2>nul
    if errorlevel 1 echo Unable to enable extensions
    ```  
    **Cmd** コマンド拡張機能を無効にすると、ERRORLEVEL 変数を設定しない、 **verify** に無効な引数を使用する場合、コマンドを 0 以外の値を ERRORLEVEL 変数を初期化します。 またを使用する場合、 **setlocal** コマンドの引数に {**enableextensions** | **disableextensions**} または {**enabledelayedexpansion** | **disabledelayedexpansion**} と、ERRORLEVEL 変数を設定しません **1**, 、コマンド拡張機能は使用できません。

## <a name="BKMK_examples"></a>例

次のサンプル スクリプトで示すようにバッチ ファイルで環境変数をローカライズすることができます。
```
rem *******Begin Comment**************
rem This program starts the superapp batch program on the network,
rem directs the output to a file, and displays the file
rem in Notepad.
rem *******End Comment**************
@echo off
setlocal
path=g:\programs\superapp;%path%
call superapp>c:\superapp.out
endlocal
start notepad c:\superapp.out
```

#### <a name="additional-references"></a>その他の参照情報

[コマンド ライン構文の記号](command-line-syntax-key.md)