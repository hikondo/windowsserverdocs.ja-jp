---
title: manage-bde resume
description: 一時停止した後に BitLocker 暗号化または暗号化解除を再開する、manage-bde resume コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: ca3cd1ca-6f2c-4190-b68f-27816635facb
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ebae22e60a8110bc2ba5e4649fc6cf143431b359
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639296"
---
# <a name="manage-bde-resume"></a>manage-bde resume

一時停止された後は、BitLocker 暗号化または復号化を再開します。

## <a name="syntax"></a>構文

```
manage-bde -resume [<drive>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<drive>` | コロンの後にドライブ文字を表します。 |
| -computername | manage-bde.exe が別のコンピューターの BitLocker 保護を変更するために使用されることを指定します。 また、このコマンドの省略版として **-cn** を使用することもできます。 |
| `<name>` | BitLocker による保護を変更するコンピューターの名前を表します。 指定できる値には、コンピューターの NetBIOS 名とコンピューターの IP アドレスが含まれます。 |
| -? または /? | コマンドプロンプトで簡単なヘルプを表示します。 |
| -help または-h | 表示は、コマンド プロンプトでヘルプを完了します。 |

### <a name="examples"></a>例

ドライブ C で BitLocker 暗号化を再開するには、次のように入力します。

```
manage-bde –resume C:
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [コマンドの manage-bde を管理する](manage-bde-on.md)

- [manage-bde コマンドの管理](manage-bde-off.md)

- [manage-bde pause コマンド](manage-bde-pause.md)

- [manage-bde コマンド](manage-bde.md)
