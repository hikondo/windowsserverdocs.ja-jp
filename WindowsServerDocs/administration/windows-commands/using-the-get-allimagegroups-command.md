---
title: get-AllImageGroups
description: Get AllImageGroups のリファレンス記事。サーバー上のすべてのイメージグループとそれらのイメージグループ内のすべてのイメージに関する情報を取得します。
ms.topic: reference
ms.assetid: 2ca06533-bcf5-4590-ac8e-263d6c9874f8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b69375cff867d317c3ac6c83ec1c75358455ac03
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626423"
---
# <a name="get-allimagegroups"></a>get-AllImageGroups

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サーバーおよびそれらのイメージ グループのすべてのイメージ上のすべてのイメージ グループに関する情報を取得します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Get-AllImageGroups [/Server:<Server name>] [/detailed]
```
### <a name="parameters"></a>パラメーター
|パラメーター|Description|
|-------|--------|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
|詳細/|各イメージからイメージのメタデータを返します。 このパラメーターを使用しない場合、既定の動作は、イメージの名前、説明、および各イメージのファイル名のみを返すには。|
## <a name="examples"></a>例
イメージ グループに関する情報を表示するには、次のいずれかを入力します。
```
wdsutil /Get-AllImageGroups
wdsutil /verbose /Get-AllImageGroups /Server:MyWDSServer /detailed
```
## <a name="additional-references"></a>その他の参照情報
- [コマンドライン構文のキー](command-line-syntax-key.md) 
[追加 ImageGroup コマンド](using-the-add-imagegroup-command.md) 
 を使用してください。[Get ImageGroup コマンド](using-the-get-imagegroup-command.md) 
 の使用[削除 ImageGroup コマンド](using-the-remove-imagegroup-command.md) 
 を使用してください。[サブコマンド: セット ImageGroup](subcommand-set-imagegroup.md)
