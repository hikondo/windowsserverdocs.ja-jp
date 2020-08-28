---
title: query termserver
description: Query termserver コマンドのリファレンス記事。ネットワーク上のすべてのリモートデスクトップセッションホストサーバーの一覧を表示します。
ms.topic: reference
ms.assetid: 3b89d3b4-236f-4376-90b6-939a0ec4b288
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 103e1c888f20e368e014eba762b739e099d9e491
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038400"
---
# <a name="query-termserver"></a>query termserver

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ネットワーク上のすべてのリモートデスクトップセッションホストサーバーの一覧を表示します。 このコマンドは、ネットワークで接続されているすべてのリモートデスクトップセッションホストサーバーを検索し、次の情報を返します。

- サーバーの名前

- Network (/address オプションが使用されている場合はノードアドレス)

> [!NOTE]
> 最新バージョンの新機能については、「 [Windows Server でのリモートデスクトップサービスの新](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))機能」を参照してください。

## <a name="syntax"></a>構文

```
query termserver [<servername>] [/domain:<domain>] [/address] [/continue]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<servername>` | リモートデスクトップセッションホストサーバーを識別する名前を指定します。 |
| /domain`<domain>` | ターミナル サーバーを照会するドメインを指定します。 現在作業しているドメインに対してクエリを実行する場合は、ドメインを指定する必要はありません。 |
| /address | 各サーバーのネットワークとノードのアドレスを表示します。 |
| 続行/ | 情報の各画面が表示された後の一時停止できないようにします。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

### <a name="examples"></a>例

ネットワーク上のすべてのリモートデスクトップセッションホストサーバーに関する情報を表示するには、次のように入力します。

```
query termserver
```

*Server3*という名前のリモートデスクトップセッションホストサーバーに関する情報を表示するには、次のように入力します。

```
query termserver Server3
```

ドメイン *CONTOSO*内のすべてのリモートデスクトップセッションホストサーバーに関する情報を表示するには、次のように入力します。

```
query termserver /domain:CONTOSO
```

*Server3*という名前のリモートデスクトップセッションホストサーバーのネットワークとノードのアドレスを表示するには、次のように入力します。

```
query termserver Server3 /address
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [クエリコマンド](query.md)

- [リモート デスクトップ サービス (ターミナル サービス) のコマンド リファレンス](remote-desktop-services-terminal-services-command-reference.md)
