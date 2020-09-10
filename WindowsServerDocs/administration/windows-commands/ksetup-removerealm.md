---
title: ksetup removerealm
description: Ksetup removerealm コマンドの参照記事。指定された領域のすべての情報をレジストリから削除します。
ms.topic: reference
ms.assetid: 39f0c6f0-4c50-4781-941e-0893495405e8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 324eb79fee80e53da4dd1bc331e5af49c64c1574
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622759"
---
# <a name="ksetup-removerealm"></a>ksetup removerealm

指定された領域のすべての情報をレジストリから削除します。

領域名は、およびの下のレジストリに格納され `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001` `\CurrentControlSet\Control\Lsa\Kerberos` ます。 既定では、このエントリはレジストリに存在しません。 [Ksetup addrealmflags](ksetup-addrealmflags.md)コマンドを使用して、レジストリにデータを設定できます。

> [!IMPORTANT]
> ドメインコントローラーから既定の領域名を削除することはできません。これは、DNS 情報がリセットされ、削除されるとドメインコントローラーが使用できなくなる可能性があるためです。

## <a name="syntax"></a>構文

```
ksetup /removerealm <realmname>
```
### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| `<realmname>` | CORP など、大文字の DNS 名を指定します。CONTOSO.COM は、 **ksetup**の実行時に既定の領域または**領域 =** として表示されます。 |

### <a name="examples"></a>例

間違った領域名 () を削除するには.COM ではなく CON) ローカルコンピューターから次のように入力します。
```
ksetup /removerealm CORP.CONTOSO.CON
```

削除を確認するには、 **ksetup** コマンドを実行し、出力を確認します。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ksetup コマンド](ksetup.md)

- [ksetup setrealm コマンド](ksetup-setrealm.md)
