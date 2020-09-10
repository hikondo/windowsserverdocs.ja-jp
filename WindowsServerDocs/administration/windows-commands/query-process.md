---
title: query process
description: クエリ処理コマンドの参照記事。リモートデスクトップセッションホストサーバーで実行されているプロセスに関する情報を表示します。
ms.topic: reference
ms.assetid: 36ce3ffc-0092-4eb1-a374-28e6616ca946
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: eb2deaeac012eba4dad06ae6084474942536adfd
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639891"
---
# <a name="query-process"></a>query process

適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

リモートデスクトップセッションホストサーバーで実行されているプロセスに関する情報を表示します。 このコマンドを使用すると、特定のユーザーが実行しているプログラム、および特定のプログラムを実行しているユーザーを調べることができます。 このコマンドは、次の情報を返します。

- プロセスを所有しているユーザー

- プロセスを所有するセッション

- セッションの ID

- プロセスの名前

- プロセスの ID

> [!NOTE]
> 最新バージョンの新機能については、「 [Windows Server でのリモートデスクトップサービスの新](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))機能」を参照してください。

## <a name="syntax"></a>構文

```
query process [*|<processID>|<username>|<sessionname>|/id:<nn>|<programname>] [/server:<servername>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| * | すべてのセッションのプロセスを一覧表示します。 |
| `<processID>` | クエリするプロセスを識別する数値 ID を指定します。 |
| `<username>` | プロセスを一覧表示するユーザーの名前を指定します。 |
| `<sessionname>` | プロセスを一覧表示するアクティブセッションの名前を指定します。 |
| /id`<nn>` | 一覧表示するプロセスを含むセッションの ID を指定します。 |
| `<programname>` | クエリするプロセスのプログラムの名前を指定します。 .Exe 拡張子が必要です。 |
| /server:`<servername>` | プロセスを一覧表示するリモートデスクトップセッションホストサーバーを指定します。 指定しない場合は、現在ログオンしているサーバーが使用されます。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- 管理者は、すべての **クエリ処理** 機能にフルアクセスできます。

- <*username*>、<の*セッション*名>、 */id `<nn>` :*、<*programname*>、または *&#42;* パラメーターを指定しない場合、このクエリでは現在のユーザーに属しているプロセスのみが表示されます。

- **クエリ処理**で情報が返されると、 `(>)` 現在のセッションに属する各プロセスの前に、より大きい記号が表示されます。

## <a name="examples"></a>例

すべてのセッションで使用されているプロセスに関する情報を表示するには、次のように入力します。

```
query process *
```

*セッション ID 2*によって使用されているプロセスに関する情報を表示するには、次のように入力します。

```
query process /ID:2
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [クエリコマンド](query.md)

- [リモート デスクトップ サービス (ターミナル サービス) のコマンド リファレンス](remote-desktop-services-terminal-services-command-reference.md)
