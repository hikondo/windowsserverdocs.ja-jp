---
title: 取得-ImageGroup
description: イメージグループとその中のイメージに関する情報を取得する、get ImageGroup の参照記事。
ms.topic: reference
ms.assetid: 0fc25aca-a529-44ee-bc8e-96bc8affb458
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c135072be3ff8ccf0993ed72ddf8f079f1d88c05
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638095"
---
# <a name="get-imagegroup"></a>取得-ImageGroup

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

イメージ グループおよびその中のイメージに関する情報を取得します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Get-ImageGroumediaGroup:<Image group name> [/Server:<Server name>] [/detailed]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
mediaGroup:<Image group name>|イメージグループの名前を指定します。|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
|詳細/|各イメージのイメージのメタデータを返します。 このパラメーターが使用でない場合は、既定の動作は、イメージの名前、説明、およびファイル名のみを返すには。|
## <a name="examples"></a>例
イメージ グループに関する情報を表示するには、次のように入力します。
```
wdsutil /Get-ImageGroumediaGroup:ImageGroup1
```
メタデータを含む情報を表示するには、次のように入力します。
```
wdsutil /verbose /Get-ImageGroumediaGroup:ImageGroup1 /Server:MyWDSServer /detailed
```
## <a name="additional-references"></a>その他の参照情報
- [コマンドライン構文のキー](command-line-syntax-key.md) 
[追加 ImageGroup コマンド](using-the-add-imagegroup-command.md) 
 を使用してください。[Get AllImageGroups コマンド](using-the-get-allimagegroups-command.md) 
 の使用[削除 ImageGroup コマンド](using-the-remove-imagegroup-command.md) 
 を使用してください。[サブコマンド: セット ImageGroup](subcommand-set-imagegroup.md)
