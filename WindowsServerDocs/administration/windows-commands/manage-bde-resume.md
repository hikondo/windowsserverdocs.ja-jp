---
title: manage-bde resume
description: 一時停止した後に BitLocker 暗号化または暗号化解除を再開する、manage-bde resume コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: ca3cd1ca-6f2c-4190-b68f-27816635facb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 57f12ad478e565fa8edbeed0818e83b62c2d17fb
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89027500"
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
