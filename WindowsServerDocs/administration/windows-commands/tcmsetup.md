---
title: tcmsetup
description: TAPI クライアントを設定および無効にする方法について説明します。
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 15e0c10f-996f-4301-92e5-943f7ee8212d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0c646acef51f06c57f16ec7e5310e3319a11383f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370684"
---
# <a name="tcmsetup"></a>tcmsetup



設定または、TAPI クライアントを無効にします。

## <a name="syntax"></a>構文

```
tcmsetup [/q] [/x] /c <Server1> [<Server2> …] 
tcmsetup  [/q] /c /d
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|/q|メッセージ ボックスが表示されないようにします。|
|/x|接続指向のコールバックを使用することに大量のトラフィックのネットワーク パケット損失が多いを指定します。 このパラメーターを省略すると、コネクションレス型コールバックが使用されます。|
|/c|必須。 クライアントのセットアップを指定します。|
|\<Server1 >|必須。 クライアントで使用される TAPI サービス プロバイダーのあるリモート サーバーの名前を指定します。 クライアントはサービス プロバイダーの回線や電話を使用します。 クライアントは、サーバーと同じドメインまたはサーバーを含むドメインと双方向の信頼関係があるドメインにする必要があります。|
|\<Server2 >...|その他のサーバーまたはこのクライアントに利用可能なサーバーを指定します。 サーバーの一覧を指定する場合は、スペースを使用して、サーバー名を区切ります。|
|/d|リモート サーバーの一覧をクリアします。 リモート サーバー上にある TAPI サービス プロバイダーを使用できなくなり、TAPI クライアントを無効にします。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>コメント

-   ここで示す手順を実行するには、ローカル コンピューターの Administrators グループに属しているか、適切な権限を委任されている必要があります。 コンピューターがドメインに参加している場合は、Domain Admins グループのメンバーがここで示す手順を実行できます。 セキュリティの点から、 **[別のユーザーとして実行]** を使用してこの手順を実行することを検討してください。
-   TAPI が正しく機能するためには、実行する必要があります **tcmsetup** TAPI クライアントによって使用されるリモート サーバーを指定します。
-   クライアント ユーザーは、TAPI サーバー上、電話または回線を使用できるように、テレフォニー サーバーの管理者は、電話または回線にユーザーを割り当てる必要があります。
-   このコマンドによって作成されるテレフォニー サーバーの一覧には、クライアントで利用できるテレフォニー サーバーの既存の一覧が置き換えられます。 このコマンドを使用、既存のリストに追加することはできません。

#### <a name="additional-references"></a>その他の参照情報

[コマンド ライン構文の記号](command-line-syntax-key.md)

[コマンドシェルの概要](https://technet.microsoft.com/library/cc737438(v=ws.10).aspx)

[クライアントコンピューターのテレフォニーサーバーを指定する](https://technet.microsoft.com/library/cc759226(v=ws.10).aspx)

[回線または電話にテレフォニーユーザーを割り当てる](https://technet.microsoft.com/library/cc736875(v=ws.10).aspx)

