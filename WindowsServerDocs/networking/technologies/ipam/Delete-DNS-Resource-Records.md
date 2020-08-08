---
title: DNS リソース レコードを削除する
description: このトピックは、Windows Server 2016 の IP アドレス管理 (IPAM) 管理ガイドに含まれています。
manager: brianlic
ms.topic: article
ms.assetid: 366e6fd5-d563-4de3-9551-5614cbb8f2cb
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 76a2847113536020bec6ea9724026c6e297cead2
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87952303"
---
# <a name="delete-dns-resource-records"></a>DNS リソース レコードを削除する

>適用先:Windows Server (半期チャネル)、Windows Server 2016

このトピックを使用して、IPAM クライアントコンソールを使用して1つまたは複数の DNS リソースレコードを削除できます。

この手順を実行するには、**Administrators** のメンバーシップ、またはそれと同等のメンバーシップが最低限必要です。

### <a name="to-delete-dns-resource-records"></a>DNS リソースレコードを削除するには

1.  サーバー マネージャーで、クリックして  **IPAM**します。 IPAM クライアントコンソールが表示されます。

2.  ナビゲーションウィンドウの [**監視と管理**] で、[ **DNS ゾーン数**] をクリックします。  上部のナビゲーション ウィンドウと下のナビゲーション ウィンドウのナビゲーション ウィンドウに分割します。

3.  [**前方参照**] をクリックして展開し、削除するゾーンとリソースレコードが配置されているドメインを展開します。 ゾーンをクリックし、表示ウィンドウで [**現在のビュー**] をクリックします。 [**リソースレコード**] をクリックします。

4.  表示ウィンドウで、削除するリソースレコードを見つけて選択します。

    ![削除するリソースレコードの選択](../../media/Delete-DNS-Resource-Records/ipam_DeleteRR_01.jpg)

5.  選択したレコードを右クリックし、[ **DNS リソースレコードの削除**] をクリックします。

    ![レコードを削除する](../../media/Delete-DNS-Resource-Records/ipam_DeleteRR_02.jpg)

6.  [ **DNS リソースレコードの削除**] ダイアログボックスが表示されます。 正しい DNS サーバーが選択されていることを確認します。 そうでない場合は、[ **DNS サーバー** ] をクリックし、リソースレコードを削除するサーバーを選択します。 **[OK]** をクリックします。 IPAM は、DNS サーバーからリソースレコードを削除します。

    ![正しい DNS サーバーが選択されていることを確認し、レコードを削除します。](../../media/Delete-DNS-Resource-Records/ipam_DeleteRR_03.jpg)

## <a name="see-also"></a>参照
[DNS リソースレコードの管理](DNS-Resource-Record-Management.md) 
[IPAM の管理](Manage-IPAM.md)



