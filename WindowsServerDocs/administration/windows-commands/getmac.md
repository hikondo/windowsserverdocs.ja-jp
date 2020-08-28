---
title: getmac
description: Getmac コマンドのリファレンス記事。このコマンドは、メディアアクセスコントロール (MAC) アドレスと、各ネットワークに関連付けられているネットワークプロトコルの一覧をローカルまたはネットワーク経由で返します。
ms.topic: reference
ms.assetid: a749a348-7cd1-4336-9f33-bb42dd0e31e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 901777744b98095e4e19ff39d9965d144ee1f1c8
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89034080"
---
# <a name="getmac"></a>getmac

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ローカルまたはネットワーク経由で、各コンピューターのすべてのネットワークカードの各アドレスに関連付けられている、メディアアクセス制御 (MAC) アドレスとネットワークプロトコルの一覧を返します。 このコマンドは、MAC アドレスをネットワークアナライザーに入力する場合や、コンピューターの各ネットワークアダプターで現在使用されているプロトコルを知る必要がある場合に特に便利です。

## <a name="syntax"></a>構文

```
getmac[.exe][/s <computer> [/u <domain\<user> [/p <password>]]][/fo {table | list | csv}][/nh][/v]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- |------------ |
| /s `<computer>` | 名前またはリモート コンピューターの IP アドレスを指定します (円記号を使用しない)。 既定値はローカル コンピューターです。 |
| /u `<domain>\<user>` | *User*または*domain\user*によって指定されたユーザーのアカウントアクセス許可を使用してコマンドを実行します。 既定値は、コマンドを実行しているコンピューターの現在のログオンユーザーのアクセス許可です。 |
| /p `<password>` | 指定されているユーザー アカウントのパスワードを指定します、 **/u** パラメーター。 |
| /fo {テーブル | list | 市区 | クエリ出力に使用する形式を指定します。 有効な値は **テーブル**, 、**リスト**, 、および **csv**します。 出力の既定の形式は **table**です。 |
| /nh | 出力に列ヘッダーを表示しません。 **/Fo**パラメーターが**table**または**csv**に設定されている場合に有効です。 |
| /v | 出力に詳細情報を表示するように指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

### <a name="examples"></a>例

次の例は、 **getmac** コマンドを使用する方法を示しています。

```
getmac /fo table /nh /v
```

```
getmac /s srvmain
```

```
getmac /s srvmain /u maindom\hiropln
```

```
getmac /s srvmain /u maindom\hiropln /p p@ssW23
```

```
getmac /s srvmain /u maindom\hiropln /p p@ssW23 /fo list /v
```

```
getmac /s srvmain /u maindom\hiropln /p p@ssW23 /fo table /nh
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
