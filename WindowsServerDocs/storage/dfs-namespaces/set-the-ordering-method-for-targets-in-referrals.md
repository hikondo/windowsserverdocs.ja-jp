---
title: 紹介におけるターゲットの順序指定方法を設定する
description: この記事では、紹介におけるターゲットの順序指定方法を設定する方法について説明します。
ms.date: 6/5/2017
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: e448a12659ca7aa9fbc4230dce51df4fbcd7bcf0
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87936105"
---
# <a name="set-the-ordering-method-for-targets-in-referrals"></a>紹介におけるターゲットの順序指定方法を設定する

> 適用対象: Windows Server 2019、Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2、Windows Server 2008

紹介とは、ユーザーが名前空間のルートにアクセスするか、ターゲットを持つフォルダーにアクセスしたときに、クライアント コンピューターがドメイン コントローラーまたは名前空間サーバーから受信する、順序付きのターゲット一覧です。 クライアントは、紹介を受信した後、一覧の先頭のターゲットにアクセスしようとします。 そのターゲットにアクセスできない場合は、次のターゲットにアクセスしようとします。
クライアント サイト上のターゲットは常に紹介の最初にリストされます。 クライアント サイト外のターゲットは、順序指定方法に従ってリストされます。

以降のセクションでは、ターゲットをクライアントに紹介する順序を指定し、ターゲット紹介の順序を指定するさまざまな方法について理解します。

## <a name="to-set-the-ordering-method-for-targets-in-namespace-root-referrals"></a>名前空間ルートの紹介におけるターゲットの順序指定方法を設定するには

名前空間ルートにおける順序指定方法を設定するには、次の手順を使用します。

1.  [**スタート**] をクリックし、[**管理ツール**] をポイントして、[**DFS 管理**] をクリックします。

2.  コンソール ツリーの **[名前空間]** ノードで、名前空間を右クリックし、**[プロパティ]** をクリックします。

3.  **[紹介]** タブで、順序指定方法を選択します。

> [!NOTE]
> Windows PowerShell を使って名前空間ルートの紹介におけるターゲットの順序指定方法を設定するには、次のいずれかのパラメーターを指定して [Set-DfsnRoot](/powershell/module/dfsr/update-dfsrconfigurationfromad?view=win10-ps) コマンドレットを使います。
>    -   **EnableSiteCosting** の場合、**"最低コストの順序指定"** の方法が指定されます。
>    -   **EnableInsiteReferrals** の場合、**"クライアント サイト外のターゲットを除外する"** 順序指定方法が指定されます。
>    -   いずれかのパラメーターを省略すると、**"ランダム順序"** の参照順序指定方法が指定されます。

DFSN Windows PowerShell モジュールは、Windows Server 2012 で導入されました。

## <a name="to-set-the-ordering-method-for-targets-in-folder-referrals"></a>フォルダー紹介におけるターゲットの順序指定方法を設定するには

ターゲットを持つフォルダーは、名前空間ルートからの順序指定方法を継承します。 順序指定方法は、次の手順を使用して上書きできます。

1.  [**スタート**] をクリックし、[**管理ツール**] をポイントして、[**DFS 管理**] をクリックします。

2.  コンソール ツリーの **[名前空間]** ノードで、ターゲットを持つフォルダーを右クリックし、**[プロパティ]** をクリックします。

3.  **[紹介]** タブで、**[クライアント サイト外のターゲットを除外する]** チェック ボックスをオンにします。

> [!NOTE]
> Windows PowerShell を使ってクライアント サイト外のフォルダー ターゲットを除外するには、[Set-DfsnFolder –EnableInsiteReferrals](/powershell/module/dfsr/update-dfsrconfigurationfromad?view=win10-ps) コマンドレットを使います。

## <a name="target-referral-ordering-methods"></a>ターゲット紹介の順序指定方法

3 つの順序指定方法は次のとおりです。

-   ランダム順序
-   最低コスト
-   クライアント サイト外のターゲットを除外する

## <a name="random-order"></a>ランダム順序

この方法では、ターゲットが次のように順序指定されます。

1.  クライアントと同じ Active Directory ディレクトリ サービス (AD DS) サイト内のターゲットは、紹介の一番上にランダムな順序でリストされます。
2.  クライアント サイト外部のターゲットは、ランダムな順序でリストされます。

同じサイトのターゲット サーバーがない場合、クライアント コンピューターは、接続のコストやターゲットとの距離に関係なくランダムなターゲット サーバーに紹介されます。

## <a name="lowest-cost"></a>最低コスト

この方法では、ターゲットが次のように順序指定されます。

1.  クライアントと同じサイト内のターゲットは、紹介の一番上にあるランダムな順序でリストされます。
2.  クライアント サイト外のターゲットは、コストが低い順にリストされます。 同じコストの紹介は一緒にグループ化され、ターゲットはグループごとにランダムな順序でリストします。

> [!NOTE]
> サイト リンクのコストは、DFS 管理スナップインに表示されません。 サイト リンクのコストを表示するには、Active Directory サイトとサービス スナップインを使います。

## <a name="exclude-targets-outside-of-the-clients-site"></a>クライアント サイト外のターゲットを除外する

この方法では、クライアントと同じサイト内のターゲットのみ紹介に含まれます。 これらの同じサイトのターゲットは、ランダムな順序でリストされます。 同じサイトのターゲットが存在しない場合、クライアントは紹介を受け取らず、名前空間の部分にアクセスできません。

> [!NOTE]
> 順序指定方法が **[クライアント サイト外のターゲットを除外する]** に設定されている場合でも、ターゲット優先順位が [すべてのターゲットのうち最初のターゲット] または [すべてのターゲットのうち最後のターゲット] に設定されたターゲットは紹介にリストされます。

## <a name="additional-references"></a>その他の参照情報

-   [DFS 名前空間を調整する](tuning-dfs-namespaces.md)
-   [DFS 名前空間の管理アクセス許可を委任する](delegate-management-permissions-for-dfs-namespaces.md)
