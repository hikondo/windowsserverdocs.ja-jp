---
title: ksetup delkdc
description: Ksetup delkdc コマンドのリファレンス記事。 Kerberos 領域のキー配布センター (KDC) 名のインスタンスを削除します。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7d6ec389-094c-4a7b-a78b-605497ddc289
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2d0477fd7317b0b9424fd6199cfde268c00dd1d6
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926129"
---
# <a name="ksetup-delkdc"></a>ksetup delkdc

Kerberos 領域のキー配布センター (KDC) 名のインスタンスを削除します。

マッピングは、レジストリのの下に格納され `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\LSA\Kerberos\Domains` ます。 このコマンドを実行した後、KDC が削除され、一覧に表示されなくなったことを確認することをお勧めします。

> [!NOTE]
> 複数のコンピューターから領域構成データを削除するには、個々のコンピューターで**ksetup**コマンドを明示的に使用するのではなく、ポリシー配布による**セキュリティ構成テンプレート**スナップインを使用します。

## <a name="syntax"></a>構文

```
ksetup /delkdc <realmname> <KDCname>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<realmname>` | CORP など、大文字の DNS 名を指定します。CONTOSO.COM。 これは、 **ksetup**コマンドを実行したときに表示される既定の領域であり、KDC を削除する領域です。 |
| `<KDCname>` | 大文字と小文字が区別される完全修飾ドメイン名 (mitkdc.contoso.com など) を指定します。 |

### <a name="examples"></a>例

Windows 領域と Windows 以外の領域間のすべての関連付けを表示するには、次のように入力します。

```
ksetup
```

関連付けを削除するには、次のように入力します。

```
ksetup /delkdc CORP.CONTOSO.COM mitkdc.contoso.com
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ksetup コマンド](ksetup.md)

- [ksetup addkdc コマンド](ksetup-addkdc.md)