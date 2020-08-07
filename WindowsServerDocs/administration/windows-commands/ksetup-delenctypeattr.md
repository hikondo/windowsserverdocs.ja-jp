---
title: ksetup delenctypeattr
description: Ksetup delenctypeattr の参照記事。ドメインの暗号化の種類の属性が削除されます。
ms.topic: article
ms.assetid: 4fc25ef3-e271-4229-a712-72c507df55aa
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7901cdb53c051885e5e4040cbc28b7cae0ed2a4d
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2020
ms.locfileid: "87888038"
---
# <a name="ksetup-delenctypeattr"></a>ksetup delenctypeattr

ドメインの暗号化の種類の属性を削除します。 正常に完了したか、完了しなかったときに、ステータスメッセージが表示されます。

Kerberos チケット保証チケット (TGT) とセッションキーの暗号化の種類を表示するには、 **klist**コマンドを実行し、出力を表示します。 コマンドを実行して、に接続してを使用するようにドメインを設定でき `ksetup /domain <domainname>` ます。

## <a name="syntax"></a>構文

```
ksetup /delenctypeattr <domainname>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ----------| ----------- |
| `<domainname>` | 接続を確立するドメインの名前。 完全修飾ドメイン名または名前の単純な形式 (corp.contoso.com や contoso など) のいずれかを使用できます。 |

### <a name="examples"></a>例

このコンピューターに設定されている現在の暗号化の種類を確認するには、次のように入力します。

```
klist
```

ドメインを mit.contoso.com に設定するには、次のように入力します。

```
ksetup /domain mit.contoso.com
```

ドメインの暗号化の種類の属性を確認するには、次のように入力します。

```
ksetup /getenctypeattr mit.contoso.com
```

ドメイン mit.contoso.com の [暗号化の種類の設定] 属性を削除するには、次のように入力します。

```
ksetup /delenctypeattr mit.contoso.com
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [klist コマンド](klist.md)

- [ksetup コマンド](ksetup.md)

- [ksetup domain コマンド](ksetup-domain.md)

- [ksetup addenctypeattr コマンド](ksetup-addenctypeattr.md)

- [ksetup setenctypeattr コマンド](ksetup-setenctypeattr.md)
