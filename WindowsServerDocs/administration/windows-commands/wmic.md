---
title: wmic
description: 'Windows コマンドに関するトピック * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76397c72-d06f-4cea-88cf-c7603315a983
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f5096ab82ebbd01cb4f3a7dc0cf0b15e4b9fae8e
ms.sourcegitcommit: effbc183bf4b370905d95c975626c1ccde057401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74781329"
---
# <a name="wmic"></a>wmic



対話型コマンドシェル内に WMI 情報を表示します。

このコマンドを使用する方法の例については、[例](#BKMK_examples)を参照してください。

## <a name="syntax"></a>構文

```
wmic </parameter>
```

## <a name="sub-commands"></a>サブコマンド

次のサブコマンドは常に使用できます。

|サブコマンド|説明|
|-----------|-----------|
|クラス|WMIC の既定のエイリアスモードをエスケープして、WMI スキーマ内のクラスに直接アクセスします。|
|パス|WMIC の既定のエイリアスモードをエスケープして、WMI スキーマ内のインスタンスに直接アクセスできるようにします。|
|コンテキスト|すべてのグローバルスイッチの現在の値を表示します。|
|[終了 \| 終了]|WMIC コマンドシェルを終了します。|

## <a name="BKMK_examples"></a>例

すべてのグローバルスイッチの現在の値を表示するには、次のように入力します。
```
wmic context
```
次のような出力が表示されます。
```
NAMESPACE    : root\cimv2
ROLE         : root\cli
NODE(S)      : BOBENTERPRISE
IMPLEVEL     : IMPERSONATE
[AUTHORITY   : N/A]
AUTHLEVEL    : PKTPRIVACY
LOCALE       : ms_409
PRIVILEGES   : ENABLE
TRACE        : OFF
RECORD       : N/A
INTERACTIVE  : OFF
FAILFAST     : OFF
OUTPUT       : STDOUT
APPEND       : STDOUT
USER         : N/A
AGGREGATE    : ON
```
コマンドラインで使用される言語 ID を英語 (ロケール ID 409) に変更するには、次のように入力します。
```
wmic /locale:ms_409
```

#### <a name="additional-references"></a>その他の参照情報

[コマンド ライン構文の記号](command-line-syntax-key.md)
