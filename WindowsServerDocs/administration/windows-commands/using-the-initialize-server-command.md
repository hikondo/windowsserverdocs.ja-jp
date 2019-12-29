---
title: Initialize サーバー コマンドを使用してください。
description: 'Windows コマンドに関するトピック * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68a26ad9-5eb2-4490-b782-b7cd46b8000d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b9e95972838fc70ee1e617d1e299c9e35db5b979
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392098"
---
# <a name="using-the-initialize-server-command"></a>Initialize サーバー コマンドを使用してください。

>適用先:Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サーバーの役割をインストールした後は、初期使用のための Windows 展開サービス サーバーを構成します。 このコマンドを実行した後必要がありますを使用する、 [追加イメージのコマンドを使用して](using-the-add-image-command.md) コマンドをサーバーにイメージを追加します。
## <a name="syntax"></a>構文
```
wdsutil /Initialize-Server [/Server:<Server name>] /remInst:<Full path> [/Authorize]
```
## <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
|/remInst: "<Full path>"|RemoteInstall フォルダーの完全なパスと名前を指定します。 指定したフォルダーが既に存在しない場合、コマンドの実行時に、このオプションを作成します。 常に発生した場合でも、リモート コンピューターのローカル パスを入力する必要があります。 以下に例を示します。**D:\remoteInstall**。|
|[]、[承認]|動的ホスト制御プロトコル (DHCP) で、サーバーが認証されます。 このオプションは、DHCP 承認されていない検出が有効になっている場合にのみ意味を Windows 展開サービス PXE サーバーで承認する必要 DHCP クライアント コンピューターが処理される前に必要があります。 既定では DHCP 承認されていない検出が無効になっていることに注意してください。|
## <a name="BKMK_examples"></a>例
サーバーを初期化し、remoteInstall 共有フォルダーを F: ドライブに設定するには、「」と入力します。
```
wdsutil /Initialize-Server /remInst:"F:\remoteInstall"
```
サーバーを初期化し、remoteInstall 共有フォルダーを C: ドライブに設定するには、「」と入力します。
```
wdsutil /verbose /Progress /Initialize-Server /Server:MyWDSServer /remInst:"C:\remoteInstall"
```
#### <a name="additional-references"></a>その他の参照情報
[コマンドライン構文のポイント](command-line-syntax-key.md)
[、無効にするサーバーのコマンドを使用して](using-the-disable-server-command.md)
[、有効にするサーバーのコマンドを使用して](using-the-enable-server-command.md)
[get サーバー コマンドを使用して](using-the-get-server-command.md)
[サブコマンド: サーバーを設定する](subcommand-set-server.md)
[サブコマンド: サーバーを起動](subcommand-start-server.md)
[サブコマンド: サーバーの停止](subcommand-stop-server.md)
[非サーバー オプション](the-uninitialize-server-option.md)
