---
title: manage-bde pause
description: BitLocker の暗号化または暗号化解除を一時停止する manage-bde pause コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: efda0e08-b9ff-4e71-83d8-bb666b3032bd
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ca15aa1b48e0b06a036eaf8906c7d5b7d43b881b
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639646"
---
# <a name="manage-bde-pause"></a>manage-bde pause

一時停止します。 BitLocker の暗号化または復号化します。

## <a name="syntax"></a>構文

```
manage-bde -pause [<volume>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<volume>` | ドライブ文字の後にコロン、ボリューム GUID パス、またはマウントされたボリュームを指定します。 |
| -computername | manage-bde.exe が別のコンピューターの BitLocker 保護を変更するために使用されることを指定します。 また、このコマンドの省略版として **-cn** を使用することもできます。 |
| `<name>` | BitLocker による保護を変更するコンピューターの名前を表します。 指定できる値には、コンピューターの NetBIOS 名とコンピューターの IP アドレスが含まれます。 |
| -? または /? | コマンドプロンプトで簡単なヘルプを表示します。 |
| -help または-h | 表示は、コマンド プロンプトでヘルプを完了します。 |

### <a name="examples"></a>例

ドライブ C で BitLocker 暗号化を一時停止するには、次のように入力します。

```
manage-bde pause C:
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [コマンドの manage-bde を管理する](manage-bde-on.md)

- [manage-bde コマンドの管理](manage-bde-off.md)

- [manage-bde resume コマンド](manage-bde-resume.md)

- [manage-bde コマンド](manage-bde.md)
