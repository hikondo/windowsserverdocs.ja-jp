---
title: telnet unset
description: 以前に設定したオプションをオフにする telnet 設定の参照記事。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: da9a0d99-1930-4858-93c7-0e9c3797ee09
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3efbf7d4f2507d16dbe0beb704ab0c80467a56d3
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85935290"
---
# <a name="telnet-unset"></a>telnet: 未設定

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

以前の set オプションをオフにします。

## <a name="syntax"></a>構文
```
u[nset] {bsasdel | crlf | delasbs | escape | localecho | logging | ntlm} [?]
```
#### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|bsasdel|送信 **Backspace** として、 **Backspace**します。|
|crlf|送信、 **Enter** CR としてキー。 呼ばれるモードを改行します。|
|delasbs|Delete**を** **delete**として送信します。|
|エスケープ|エスケープ文字の設定を削除します。|
|localecho|Localecho オフにします。|
|logging|ログ記録をオフにします。|
|ntlm|NTLM 認証をオフにします。|
|?|このコマンドのヘルプを表示します。|
## <a name="examples"></a>例
ログをオフにします。
```
u logging
```
## <a name="additional-references"></a>その他の参照情報
- [コマンド ライン構文の記号](command-line-syntax-key.md)
