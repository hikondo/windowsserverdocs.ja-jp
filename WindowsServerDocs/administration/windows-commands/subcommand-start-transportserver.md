---
title: サブコマンドの開始 TransportServer
description: サブコマンドの参照記事、トランスポートサーバーのすべてのサービスを開始する、サブコマンドの開始 TransportServer です。
ms.topic: reference
ms.assetid: 0e93bc84-5b9e-4f9d-8cf0-1634417da0f6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 635013a5f45d1014c24074728c5ecb951d5dccb2
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633870"
---
# <a name="subcommand-start-transportserver"></a>サブコマンド: 開始 TransportServer

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

トランスポート サーバーのすべてのサービスを開始します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /start-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|トランスポート サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
## <a name="examples"></a>例
サーバーを起動するには、次のいずれかを入力します。
```
wdsutil /start-TransportServer
wdsutil /verbose /start-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>その他の参照情報
- [コマンドライン構文のキー](command-line-syntax-key.md) 
[無効化-TransportServer コマンド](using-the-disable-transportserver-command.md) 
 の使用[Enable TransportServer コマンド](using-the-enable-transportserver-command.md) 
 の使用[Get TransportServer コマンド](using-the-get-transportserver-command.md) 
 を使用する[サブコマンド: Set TransportServer](subcommand-set-transportserver.md) 
[サブコマンド: 停止 TransportServer](subcommand-stop-transportserver.md)
