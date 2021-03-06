---
title: 管理ユーザー アカウントの作成
description: MultiPoint Services で管理者特権を持つアカウントを作成する
ms.topic: article
ms.assetid: 8ce4c5a9-3dec-412f-910b-54a252f8f209
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/04/2016
ms.openlocfilehash: 451f090bb56d0fc9c4c801d128bdb5ae1df885ff
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87971759"
---
# <a name="create-an-administrative-user-account"></a>管理ユーザー アカウントの作成
MultiPoint Services システムを管理するユーザーには、*管理ユーザー アカウント*を作成します。 管理者アクセス権を持つユーザーを表示するには、MultiPoint マネージャーで [**ユーザー** ] タブをクリックします。管理ユーザーアカウントは、[**アカウントの種類**] 列に**管理者**として表示されます。 *管理ユーザー*は、デスクトップとシステムの設定を変更するすべての MultiPoint Manager タスクにアクセスできます。次に例を示します。

-   アカウントの作成

-   プログラムの追加と削除

-   *デスクトップ*とハードウェアの管理

-   他のユーザーの*セッション*の終了

管理ユーザーは、ソフトウェアのインストールやセキュリティ設定の変更など、MultiPoint Services システムの他のすべてのユーザーに影響を与えるタスクを実行できます。 そのような理由から、管理ユーザーには一意の名前と管理ユーザーだけが知るパスワードを与えます。

管理ユーザーがユーザー アカウントを作成および管理するときに考慮する必要のある問題の詳細については、「[ユーザー アカウントに関する考慮事項](User-Account-Considerations.md)」トピックを参照してください。

> [!NOTE]
> 管理ユーザーは、MultiPoint Services システムの管理に関係のないタスクを MultiPoint Services システムで実行するときに使用する、*標準ユーザー アカウント*を作成できます。 システム管理タスクを実行する必要がある場合にのみ、管理ユーザー アカウントにログオンします。

#### <a name="to-create-an-administrative-user-account"></a>管理ユーザー アカウントを作成するには

1.  MultiPoint マネージャーで、[**ユーザー** ] タブをクリックします。

2.  **[ユーザーのタスク]** で、**[ユーザー アカウントの追加]** をクリックします。 **[ユーザー アカウントの追加]** ウィザードが表示されます。

3.  **[ユーザー アカウント]** フィールドに、ユーザーのログオン名を入力します。 通常、ログオン ユーザー名は、名と姓をスペースで区切らずに入力するか、または名のイニシャルのみと姓をスペースで区切らずに入力します。

4.  [**フルネーム**] フィールドに、指定した名前、氏名、ニックネームなど、任意の形式でユーザー名を入力します。

5.  **[パスワード]** フィールドには、ユーザーのパスワードを入力します。 パスワードは管理者とユーザーのみが知っている必要があり、安全な場所にこの情報を保管する必要があります。 パスワードは、管理ユーザーのみが変更できます。

6.  **[パスワードの確認]** フィールドにパスワードを再度入力して、**[次へ]** をクリックします。

7.  [アクセス レベル] ページで、**[管理ユーザー]** を選択して、**[次へ]** をクリックします。

8.  MultiPoint Services によってすべての情報が確認され、アカウントがセットアップされるとメッセージが表示されます。 **[新しいユーザー アカウントが正常に作成されました]** と表示されたら、**[完了]** をクリックします。
