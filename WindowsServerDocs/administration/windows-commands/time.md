---
title: time
description: システム時刻を設定および表示する方法について説明します。
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1276a257-7283-41da-ae80-fb4cfb311f9d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 484653ed65d5e5c16d74b2cb45b2c9da71aa62aa
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71369951"
---
# <a name="time"></a>time



表示またはシステム時刻を設定します。 パラメーターを指定せずに使用する場合 **時間** 現在のシステム時刻が表示され、新しい時間を入力するように求められます。

このコマンドを使用する方法の例については、[例](#BKMK_examples)を参照してください。

## <a name="syntax"></a>構文

```
time [/t | [<HH>[:<MM>[:<SS>]] [am|pm]]]
```

## <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|\<HH > [:\<MM > [:\<SS > [.\<NN >]]] [am\|pm]|システム時刻を指定された、新しい時間に設定 *HH* (必要)、時間単位で *MM* 分単位で、 *SS* の秒数。 *NN* の秒を指定するために使用できます。 場合 **いる** または **pm** が指定されていない **時間** 既定で 24 時間制を使用します。|
|/t|ときに、新しいメッセージを表示せずには、現在の時刻を表示します。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>注釈

-   現在の時刻を変更するには、管理者の資格情報が必要です。
-   値を区切る必要があります *HH*, 、*MM*, 、および *SS* コロン (::)。 *SS* と *NN* ピリオド (.) で区切る必要があります。
-   有効な *HH* 値は 0 ~ 24 です。
-   有効な *MM* と *SS* 値は 0 ~ 59 です。

## <a name="BKMK_examples"></a>例

コマンド拡張機能が有効になっている場合は、現在のシステム時刻を表示するを入力します。
```
time /t
```
現在のシステム時刻を午後 5 時 30 分に変更するには、次のいずれかを入力します。
```
time 17:30:00
time 5:30 pm
```
新しい時間を入力するプロンプトが後に現在のシステム時刻を表示するには、次のように入力します。
```
The current time is: 17:33:31.35
Enter the new time:
```
現在の時刻を保持し、コマンド プロンプトに戻り、ENTER キーを押します。 現在の時刻を変更するには、新しい時間を入力し、ENTER キーを押します。

#### <a name="additional-references"></a>その他の参照情報

[コマンド ライン構文の記号](command-line-syntax-key.md)