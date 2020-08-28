---
title: change logon
description: '[ログオンの変更] コマンドの参照記事。クライアントセッションからのログオンを有効または無効にしたり、現在のログオンステータスを表示したりします。'
ms.topic: reference
ms.assetid: 41466260-aee9-4333-bcb6-178112c22afd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 67f6a5b93fbe5ec16c4cece1c5c8429de06ce494
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89031170"
---
# <a name="change-logon"></a>change logon

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

クライアントセッションからのログオンを有効または無効にします。または、現在のログオンステータスを表示します。 このユーティリティは、システムのメンテナンスに役立ちます。 このコマンドを実行するには、管理者である必要があります。

> [!NOTE]
> 最新バージョンの新機能については、「 [Windows Server でのリモートデスクトップサービスの新](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))機能」を参照してください。

## <a name="syntax"></a>構文

```
change logon {/query | /enable | /disable | /drain | /drainuntilrestart}
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| /query | 有効または無効になっているかどうかについて、現在のログオン状態を表示します。 |
| /enable | コンソールからではなく、クライアントセッションからのログオンを有効にします。 |
| /disable | コンソールからではなく、クライアントセッションからの以降のログオンを無効にします。 現在ログオンしているユーザーには影響しません。 |
| /ドレイン | 新しいクライアントセッションからのログオンを無効にしますが、既存のセッションへの再使用を許可します。 |
| 再起動する (& a) | コンピューターが再起動されるまで新しいクライアントセッションからのログオンを無効にしますが、既存のセッションへの再実行を許可します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- システムを再起動すると、ログオンが再度有効になります。

- クライアントセッションからリモートデスクトップセッションホストサーバーに接続している場合、ログオンを再度有効にする前にログオンを無効にしてログオフすると、セッションに再接続できなくなります。 クライアントセッションからのログオンを再び有効にするには、コンソールでログオンします。

### <a name="examples"></a>例

- 現在のログオン状態を表示するには、次のように入力します。

  ```
  change logon /query
  ```

- クライアントセッションからのログオンを有効にするには、次のように入力します。

  ```
  change logon /enable
  ```

- クライアントログオンを無効にするには、次のように入力します。

  ```
  change logon /disable
  ```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [コマンドの変更](change.md)

- [リモート デスクトップ サービス (ターミナル サービス) のコマンド リファレンス](remote-desktop-services-terminal-services-command-reference.md)
