---
title: DFS 名前空間でフォルダーを作成する
description: この記事では、DFS 名前空間にフォルダーを作成する方法について説明します。
ms.date: 6/5/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 7389b825afe5ccae3059f50ffdedac72ecd5ac9a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402242"
---
# <a name="create-a-folder-in-a-dfs-namespace"></a>DFS 名前空間でフォルダーを作成する

> 適用対象:Windows Server 2019、Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2、Windows Server 2008

フォルダーを使って、名前空間に追加の階層レベルを作成できます。 フォルダー ターゲットを持つフォルダーを作成して、共有フォルダーを名前空間に追加することもできます。 フォルダー ターゲットを持つ DFS フォルダーには他の DFS フォルダーを含めることはできないため、名前空間に追加の階層レベルを追加する場合は、フォルダー ターゲットをフォルダーに追加しないでください。

DFS 管理を使って名前空間でフォルダーを作成するには、次の手順に従います。

## <a name="to-create-a-folder-in-a-dfs-namespace"></a>DFS 名前空間でフォルダーを作成するには

1.  **[スタート]** をクリックし、 **[管理ツール]** をポイントして、 **[DFS 管理]** をクリックします。

2.  コンソール ツリーの **[名前空間]** ノードで、名前空間または名前空間内のフォルダーを右クリックし、 **[新しいフォルダー]** をクリックします。

3.  **[名前]** ボックスに、新しいフォルダーの名前を入力します。

4.  1 つ以上のフォルダー ターゲットをフォルダーに追加するには、 **[追加]** をクリックしてフォルダー ターゲットの汎用名前付け規則 (UNC) パスを指定し、 **[OK]** をクリックします。


> [!TIP]
> Windows PowerShell を使って名前空間でフォルダーを作成するには、[New-DfsnFolder](https://docs.microsoft.com/powershell/module/dfsn/new-dfsnfolder) コマンドレットを使います。 DFSN Windows PowerShell モジュールは、Windows Server 2012 で導入されました。


## <a name="see-also"></a>関連項目

-   [DFS 名前空間を展開する](deploying-dfs-namespaces.md)
-   [DFS 名前空間の管理アクセス許可を委任する](delegate-management-permissions-for-dfs-namespaces.md)


