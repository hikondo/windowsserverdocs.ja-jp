---
title: wbadmin get items
description: 特定のバックアップに含まれる項目を一覧表示する wbadmin get 項目の参照記事。
ms.topic: reference
ms.assetid: 27d08ce3-6e06-4260-b264-fc1bde132d09
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 95c3c81534c3ccce87e6404409081c47121f3c2d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640725"
---
# <a name="wbadmin-get-items"></a>wbadmin get items



特定のバックアップに含まれるアイテムを一覧表示します。

このサブコマンドを使用するには、 **Backup Operators** グループまたは **Administrators** グループのメンバであるか、適切な権限が委任されている必要があります。 さらに、実行する必要があります **wbadmin** 管理者特権でコマンド プロンプトからです。 (管理者特権でのコマンドプロンプトを開くには、[ **コマンドプロンプト** ] を右クリックし、[ **管理者として実行**] をクリックします)。

## <a name="syntax"></a>構文

```
wbadmin get items
-version:<VersionIdentifier>
[-backupTarget:{<BackupDestinationVolume> | <NetworkSharePath>}]
[-machine:<BackupMachineName>]
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|-version|バックアップのバージョンを MM/DD/YYYY-HH: MM 形式で指定します。 バージョン情報がわからない場合は、「 **wbadmin get versions**」と入力します。|
|-backuptarget|詳細を表示するバックアップが格納されている場所を指定します。 対象の場所に格納されているバックアップを一覧表示するには、を使用します。 バックアップターゲットの場所には、ローカルに接続されたディスクドライブまたはリモート共有フォルダーを指定できます。 **Wbadmin get items**がバックアップが作成されたのと同じコンピューター上で実行されている場合、このパラメーターは必要ありません。 ただし、別のコンピューターから作成されたバックアップに関する情報を取得するには、このパラメーターが必要です。|
|-コンピューター|バックアップの詳細を表示するコンピューターの名前を指定します。 複数のコンピューターが同じ場所にバックアップされている場合に利用できます。 **-BackupTarget**が指定されている場合は、を使用する必要があります。|

## <a name="examples"></a>例

2013年3月31日の午前9:00 に実行されたバックアップの項目を一覧表示するには、次のように入力します。
```
wbadmin get items -version:03/31/2013-09:00
```
2013年4月30日に実行された server01 のバックアップからの項目を一覧表示するには、午前9:00 に servername\share に格納されている \\ \\ 場合は、次のように入力します。
```
wbadmin get items -version:04/30/2013-09:00 -backupTarget:\\servername\share -machine:server01
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)
-   [WBBackupSet](/powershell/module/windowserverbackup/?view=winserver2012r2-ps) コマンドレット
