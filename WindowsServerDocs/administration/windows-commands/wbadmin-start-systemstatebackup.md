---
title: wbadmin start systemstatebackup
description: Wbadmin start systemstatebackup のリファレンス記事。ローカルコンピューターのシステム状態のバックアップを作成し、指定された場所に保存します。
ms.topic: reference
ms.assetid: 998366c1-0a64-45e6-9ed3-4c3f5b8406f0
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7bd0df6e0cbfd7e34439e858865420002f5fb364
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89621485"
---
# <a name="wbadmin-start-systemstatebackup"></a>wbadmin start systemstatebackup



ローカルコンピューターのシステム状態のバックアップを作成し、指定した場所に保存します。

> [!NOTE]
> Windows Server バックアップはバックアップまたはシステム状態のバックアップまたはシステム状態の回復の一部としてユーザーのレジストリ ハイブ (HKEY_CURRENT_USER) を回復します。

このサブコマンドを使用してシステム状態のバックアップを実行するには、 **Backup Operators** グループまたは **Administrators** グループのメンバであるか、適切な権限が委任されている必要があります。 さらに、実行する必要があります **wbadmin** 管理者特権でコマンド プロンプトからです。 (管理者特権でのコマンドプロンプトを開くには、[ **コマンドプロンプト**] を右クリックし、[ **管理者として実行**] をクリックします)。

## <a name="syntax"></a>構文

```
wbadmin start systemstatebackup
-backupTarget:<VolumeName>
[-quiet]
```

### <a name="parameters"></a>パラメーター

|   パラメーター   |                                                                                                                                                                                                                      Description                                                                                                                                                                                                                      |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| -backuptarget | バックアップを保存する場所を指定します。 記憶域の場所には、次の形式のドライブ文字または GUID ベースのボリュームが必要です: \\ \\ ? \ volume{*guid*}。</br>Windows Server 2008 を実行しているコンピューターでは、共有ネットワークフォルダーへのシステム状態のバックアップはサポートされていません。 サーバーで Windows Server 2008 R2 以降が実行されている場合は、 **backuptarget: \\ \\ \\ servername\sharedFolder**コマンドを使用してシステム状態のバックアップを保存できます。 |
|    -quiet     |                                                                                                                                                                                                   ユーザーにプロンプトを表示せずにサブコマンドを実行します。                                                                                                                                                                                                    |

## <a name="remarks"></a>注釈

システム状態のバックアップをボリュームに保存する方法の詳細については、Microsoft サポート技術情報の記事 944530 () を参照してください [https://go.microsoft.com/fwlink/?LinkId=110439](https://go.microsoft.com/fwlink/?LinkId=110439) 。

## <a name="examples"></a>例

システム状態のバックアップを作成し、ボリューム f に保存するには、次のように入力します。
```
wbadmin start systemstatebackup -backupTarget:f:
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)
-   [WBBackup](/previous-versions/windows/it-pro/windows-8.1-and-8/hh825173(v=win.10)) コマンドレット
