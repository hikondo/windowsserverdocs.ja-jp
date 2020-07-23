---
title: DFS 名前空間の管理アクセス許可を委任する
description: この記事では、DFS 名前空間の管理アクセス許可を委任する方法と、名前空間タスクを既定で実行できるグループについて説明します。
ms.date: 6/5/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 838b8c716618bf10b900c12b118e940e318b56a2
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86965874"
---
# <a name="delegate-management-permissions-for-dfs-namespaces"></a>DFS 名前空間の管理アクセス許可を委任する

> 適用対象: Windows Server 2019、Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2、Windows Server 2008

次の表では、基本的な名前空間タスクを既定で実行できるグループと、それらのタスクを実行する権限を委任する方法について説明します。

|タスク | このタスクを既定で実行できるグループ | 委任方法 |
|---|---|---|
|ドメイン ベースの名前空間を作成する|名前空間が構成されているドメインの Domain Admins グループ|コンソール ツリーで **[名前空間]** ノードを右クリックし、**[管理アクセス許可の委任]** をクリックします。 または、[Set-DfsnRoot GrantAdminAccounts](/powershell/module/dfsn/set-dfsnroot?view=win10-ps) および [Set-DfsnRoot RevokeAdminAccounts](/powershell/module/dfsn/set-dfsnroot?view=win10-ps) を使います。 Windows PowerShell コマンドレット (Windows Server 2012 で導入)。 名前空間サーバー上のローカル Administrators グループにもユーザーを追加する必要があります。|
|ドメインベースの名前空間に名前空間サーバーを追加する|名前空間が構成されているドメインの Domain Admins グループ| コンソール ツリーでドメイン ベースの名前空間を右クリックし、**[管理アクセス許可の委任]** をクリックします。 または、[Set-DfsnRoot GrantAdminAccounts](/powershell/module/dfsn/set-dfsnroot?view=win10-ps) および [Set-DfsnRoot RevokeAdminAccounts](/powershell/module/dfsn/set-dfsnroot?view=win10-ps) を使います。 Windows PowerShell コマンドレット (Windows Server 2012 で導入)。 追加する名前空間サーバー上のローカル Administrators グループにもユーザーを追加する必要があります。|
|ドメイン ベースの名前空間を管理する|各名前空間サーバー上のローカル Administrators グループ| コンソール ツリーでドメイン ベースの名前空間を右クリックし、**[管理アクセス許可の委任]** をクリックします。 |
|スタンドアロン名前空間を作成する|名前空間サーバー上のローカル Administrators グループ| 名前空間サーバー上のローカル Administrators グループにもユーザーを追加します。 |
|スタンドアロン名前空間を管理する*|名前空間サーバー上のローカル Administrators グループ| コンソール ツリーでスタンドアロン名前空間を右クリックし、**[管理アクセス許可の委任]** をクリックします。 または、[Set-DfsnRoot GrantAdminAccounts](/powershell/module/dfsn/set-dfsnroot?view=win10-ps) および [Set-DfsnRoot RevokeAdminAccounts](/powershell/module/dfsn/set-dfsnroot?view=win10-ps) を使います。 Windows PowerShell コマンドレット (Windows Server 2012 で導入)。|
|レプリケーション グループを作成するか、フォルダーで DFS レプリケーションを有効にする|名前空間が構成されているドメインの Domain Admins グループ| コンソール ツリーでレプリケーション ノードを右クリックし、**[管理アクセス許可の委任]** をクリックします。 |

<br />

\*スタンドアロンの名前空間を管理するために管理アクセス許可を委任しても、ユーザーが名前空間サーバーのローカルの Administrators グループのメンバーでない限り、[**委任**] タブを使用してセキュリティを表示および管理する権限をユーザーに付与することはできません。 この問題は、DFS 管理スナップインがスタンドアロン名前空間の随意アクセス制御リスト (DACL) をレジストリから取得できないために発生します。 スナップインに委任情報を表示できるようにするには、Microsoft<sup>®</sup> サポート技術情報「[KB314837: レジストリへのリモート アクセスを管理する方法](https://go.microsoft.com/fwlink?linkid=46803)」の手順に従う必要があります。
