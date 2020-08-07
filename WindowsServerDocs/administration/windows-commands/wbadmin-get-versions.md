---
title: wbadmin get versions
description: Wbadmin get バージョンの参照記事。ローカルコンピューターまたは別のコンピューターに格納されている利用可能なバックアップの詳細が表示されます。
ms.topic: article
ms.assetid: b986acc4-d083-4d32-9434-862314ed5e97
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 209244f18758a13838a27ffd2f44e871cf5971c1
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2020
ms.locfileid: "87891727"
---
# <a name="wbadmin-get-versions"></a>wbadmin get versions



ローカルコンピューターまたは別のコンピューターに格納されている利用可能なバックアップの詳細を一覧表示します。 パラメーターを指定せずにこのサブコマンドを使用すると、それらのバックアップが使用できない場合でも、ローカルコンピューターのすべてのバックアップが一覧表示されます。 バックアップに関して提供される詳細には、バックアップ時刻、バックアップの保存場所、バージョン識別子 ( **wbadmin get items**サブコマンドに必要なものと回復を実行するために必要)、および実行できる回復の種類が含まれます。

このサブコマンドを使用して利用可能なバックアップの詳細を取得するには、 **Backup Operators**グループまたは**Administrators**グループのメンバーであるか、適切な権限が委任されている必要があります。 さらに、実行する必要があります **wbadmin** 管理者特権でコマンド プロンプトからです。 (管理者特権でのコマンドプロンプト**コマンドプロンプト**を開き、[**管理者として実行**] をクリックします)。

## <a name="syntax"></a>構文

```
wbadmin get versions
[-backupTarget:{<BackupTargetLocation> | <NetworkSharePath>}]
[-machine:BackupMachineName]
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|-backuptarget|詳細を表示するバックアップが格納されている場所を指定します。 対象の場所に格納されているバックアップを一覧表示するには、を使用します。 バックアップターゲットの場所は、ローカルに接続されたディスクドライブ、ボリューム、リモート共有フォルダー、リムーバブルメディア (DVD ドライブなど)、またはその他の光学メディアにすることができます。 **Wbadmin get バージョン**が、バックアップが作成された同じコンピューターで実行されている場合、このパラメーターは必要ありません。 ただし、別のコンピューターから作成されたバックアップに関する情報を取得するには、このパラメーターが必要です。|
|-コンピューター|バックアップの詳細を表示するコンピューターを指定します。 複数のコンピューターのバックアップが同じ場所に格納されている場合に使用します。 **-BackupTarget**が指定されている場合は、を使用する必要があります。|

## <a name="remarks"></a>Remarks

特定のバックアップからの回復に使用できる項目を一覧表示するには、 **wbadmin get items**を使用します。

## <a name="examples"></a>例

ボリューム h に格納されている利用可能なバックアップの一覧を表示するには、次のように入力します。
```
wbadmin get versions -backupTarget:h:
```
リモート共有フォルダー servername\share に格納されている利用可能なバックアップの一覧を表示するには、次のように \\ \\ 入力します。
```
wbadmin get versions -backupTarget:\\servername\share -machine:server01
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)
-   [WBBackupTarget](/powershell/module/windowserverbackup/?view=winserver2012r2-ps)コマンドレット
