---
title: wbadmin stop job
description: 現在実行中のバックアップまたは回復操作をキャンセルする wbadmin stop ジョブの参照記事。 取り消された操作は再開できません。最初から取り消されたバックアップまたは回復操作を再実行する必要があります。
ms.topic: reference
ms.assetid: 3b83b398-39c7-4410-bf17-5c1fb1a4f46d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7060fcac4c7a712695800534a23eddbcd043a4f8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633639"
---
# <a name="wbadmin-stop-job"></a>wbadmin stop job



現在実行中のバックアップまたは回復操作をキャンセルします。 取り消された操作は再開できません。最初から取り消されたバックアップまたは回復操作を再実行する必要があります。

このサブコマンドを使用してバックアップまたは回復操作を停止するには、 **Backup Operators** グループまたは **Administrators** グループのメンバーであるか、適切な権限が委任されている必要があります。 さらに、実行する必要があります **wbadmin** 管理者特権でコマンド プロンプトからです。 (管理者特権でのコマンドプロンプトを開くには、[ **コマンドプロンプト** ] を右クリックし、[ **管理者として実行**] をクリックします)。

## <a name="syntax"></a>構文

```
wbadmin stop job
[-quiet]
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|-quiet|ユーザーにプロンプトを表示せずにサブコマンドを実行します。|

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)