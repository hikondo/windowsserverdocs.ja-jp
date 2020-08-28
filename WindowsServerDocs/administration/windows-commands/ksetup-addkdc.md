---
title: ksetup addkdc
description: Ksetup addkdc コマンドの参照記事。指定された Kerberos 領域のキー配布センター (KDC) アドレスを広告します。
ms.topic: reference
ms.assetid: 98bfc23a-14c4-401c-bcb3-9903c5cdde64
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 79f279ddaa32c0b3411ca024b5d0b7f6d511d132
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89034050"
---
# <a name="ksetup-addkdc"></a>ksetup addkdc

指定された Kerberos 領域のキー配布センター (KDC) アドレスを追加します。

マッピングは **HKEY_LOCAL_MACHINE \system\currentcontrolset\control\lsa\kerberos\domains** の下のレジストリに格納され、新しい領域設定を使用する前にコンピューターを再起動する必要があります。

> [!NOTE]
> Kerberos 領域構成データを複数のコンピューターに展開するには、 **セキュリティ構成テンプレート** スナップインとポリシー配布を個々のコンピューターで明示的に使用する必要があります。 このコマンドを使用することはできません。

## <a name="syntax"></a>構文

```
ksetup /addkdc <realmname> [<KDCname>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<realmname>` | CORP など、大文字の DNS 名を指定します。CONTOSO.COM。 この値は、 **ksetup** の実行時に既定の領域としても表示され、他の KDC を追加する領域です。 |
| `<KDCname>` | 大文字と小文字を区別しない、完全修飾ドメイン名 (mitkdc.contoso.com など) を指定します。 KDC 名を省略した場合、DNS は Kdc を検索します。 |

### <a name="examples"></a>例

Windows 以外の KDC サーバーと、ワークステーションで使用する領域を構成するには、次のように入力します。

```
ksetup /addkdc CORP.CONTOSO.COM mitkdc.contoso.com
```

前の例と同じコンピューターでローカルコンピューターアカウントのパスワードを% に設定 p@sswrd1 し、コンピューターを再起動するには、次のように入力します。

```
ksetup /setcomputerpassword p@sswrd1%
```

コンピューターの既定の領域名を確認するには、次のように入力します。

```
ksetup
```
レジストリを調べて、マッピングが意図したとおりに発生したことを確認してください。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ksetup コマンド](ksetup.md)

- [ksetup setcomputerpassword コマンド](ksetup-setcomputerpassword.md)
