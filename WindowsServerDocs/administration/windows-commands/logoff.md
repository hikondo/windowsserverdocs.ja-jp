---
title: ログオフ
description: ログオフコマンドの参照記事。リモートデスクトップセッションホストサーバー上のセッションからユーザーをログオフし、セッションを削除します。
ms.topic: reference
ms.assetid: 939f09cc-de8c-436c-a05d-aca5f2a06371
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 249b63e5b98d17b67c6d00fe6d2f8a634d67de6f
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030530"
---
# <a name="logoff"></a>ログオフ

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

リモートデスクトップセッションホストサーバー上のセッションからユーザーをログオフし、セッションを削除します。

## <a name="syntax"></a>構文
```
logoff [<sessionname> | <sessionID>] [/server:<servername>] [/v]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<sessionname>` | セッションの名前を指定します。 これはアクティブなセッションである必要があります。|
| `<sessionID>` | サーバーに対するセッションを識別する数値 ID を指定します。 |
| /server:`<servername>` | ユーザーがログオフするセッションを含むリモートデスクトップセッションホストサーバーを指定します。 指定しない場合は、現在アクティブになっているサーバーが使用されます。 |
| /v | 実行されているアクションに関する情報を表示します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- 現在ログオンしているセッションから、いつでも自分でログオフできます。 ただし、他のセッションからユーザーをログオフするには、 **フルコントロール** アクセス許可を持っている必要があります。

- 警告なしでセッションからユーザーをログオフすると、ユーザーのセッションでデータが失われる可能性があります。 この操作を実行する前に、 **msg** コマンドを使用してユーザーに警告するメッセージをユーザーに送信する必要があります。

- `<sessionID>`またはが `<sessionname>` 指定されていない場合、**ログオフ**は、現在のセッションからユーザーをログオフします。

- ユーザーをログオフすると、すべてのプロセスが終了し、セッションがサーバーから削除されます。

- コンソールセッションからユーザーをログオフすることはできません。

### <a name="examples"></a>例

現在のセッションからユーザーをログオフするには、次のように入力します。

```
logoff
```

セッションの ID (例: *セッション 12*) を使用してセッションからユーザーをログオフするには、次のように入力します。

```
logoff 12
```

セッションとサーバーの名前を使用してセッションからユーザーをログオフするには (たとえば、 *Server1*の session *TERM04* )、次のように入力します。

```
logoff TERM04 /server:Server1
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [リモート デスクトップ サービス (ターミナル サービス) のコマンド リファレンス](remote-desktop-services-terminal-services-command-reference.md)
