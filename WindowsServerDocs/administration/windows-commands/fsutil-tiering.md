---
title: fsutil tiering
description: Fsutil tiering コマンドの参照記事。これにより、フラグの設定や無効化、層の一覧表示など、記憶域階層の機能の管理が可能になります。
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: e5f55f3e-8d2a-4526-8d67-36a539126c22
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 1463a6c50d2f735456e0675bdeef235cb5484b3e
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932092"
---
# <a name="fsutil-tiering"></a>fsutil tiering

> 適用先:Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows 10

フラグの設定や無効化、層の一覧表示など、記憶域階層の機能の管理を有効にします。

## <a name="syntax"></a>構文

```
fsutil tiering [clearflags] <volume> <flags>
fsutil tiering [queryflags] <volume>
fsutil tiering [regionlist] <volume>
fsutil tiering [setflags] <volume> <flags>
fsutil tiering [tierlist] <volume>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| clearflags | ボリュームの階層化動作フラグを無効にします。 |
| `<volume>` | ボリュームを指定します。 |
| /trnh | 階層化された記憶域を持つボリュームでは、熱収集が無効になります。<p>NTFS および ReFS のみに適用されます。 |
| queryflags | ボリュームの階層化動作フラグを照会します。 |
| regionlist | ボリュームの階層化された領域とそれぞれの記憶域階層を一覧表示します。 |
| setflags | ボリュームの階層化動作フラグを有効にします。 |
| tierlist | ボリュームに関連付けられている記憶域階層を一覧表示します。 |

### <a name="examples"></a>例

ボリューム C のフラグを照会するには、次のように入力します。

```
fsutil tiering queryflags C:
```

ボリューム C でフラグを設定するには、次のように入力します。

```
fsutil tiering setflags C: /trnh
```

ボリューム C のフラグをクリアするには、次のように入力します。

```
fsutil tiering clearflags C: /trnh
```

ボリューム C の領域とそれぞれの記憶域階層を一覧表示するには、次のように入力します。

```
fsutil tiering regionlist C:
```

ボリューム C の階層を一覧表示するには、次のように入力します。

```
fsutil tiering tierlist C:
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [fsutil](fsutil.md)
