---
title: ntcmdprompt
description: Ntcmdprompt コマンドの参照記事。 **Command.com**ではなく、TERMINATE (tsr) を実行した後、または MS-DOS アプリケーション内からコマンドプロンプトを起動した後に、コマンド**Cmd.exe**インタープリターを実行します。
ms.topic: reference
ms.assetid: 0063bdbb-dc2b-41c4-99ee-b011603aaa86
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 02aac71aea099359c1aa661086ed2702a89d276b
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639156"
---
# <a name="ntcmdprompt"></a>ntcmdprompt

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Terminate (TSR) を実行した後、または MS-DOS アプリケーション内からコマンドプロンプトを起動した後に、 **Command.com**ではなく、コマンドインタープリター **Cmd.exe**を実行します。

## <a name="syntax"></a>構文

```
ntcmdprompt
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- **Command.com**が実行されている場合、コマンド履歴の**doskey**表示などの**Cmd.exe**の一部の機能は使用できません。 終了と常駐 (TSR) を開始した後、または MS-DOS に基づくアプリケーション内からコマンドプロンプトを起動した後に **Cmd.exe** コマンドインタープリターを実行する場合は、 **ntcmdprompt** コマンドを使用できます。 ただし、 **Cmd.exe**を実行している場合は、TSR を使用できない可能性があることに注意してください。 **Ntcmdprompt**コマンドは、アプリケーションのプログラム情報ファイル (Pif) にある**config.xml**ファイルまたはそれと同等のカスタムスタートアップファイルに含めることができます。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
