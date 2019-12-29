---
title: 接続しているリモート クライアントの活動と状態を監視する
description: このトピックは、Windows Server 2016 のリモートアクセスの監視とアカウンティングに関するガイドの一部です。
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: beb94475-b21f-46a9-ac51-bf2bb28ca94e
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 03d87fb086a9f2797af8399be3d833b11bed79a5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71367261"
---
# <a name="monitor-connected-remote-clients-for-activity-and-status"></a>接続しているリモート クライアントの活動と状態を監視する

>適用対象: Windows Server (半期チャネル)、Windows Server 2016

**注:** Windows Server 2012 は DirectAccess とリモート アクセス サービス (RAS) は単一のリモート アクセス役割に結合します。  
  
リモート アクセス サーバーで、管理コンソールを使用すると、リモート クライアントの活動と状態を監視します。  
  
> [!NOTE]  
> このトピックで説明するタスクを完了には、Domain Admins グループのメンバーまたは各コンピューターの Administrators グループのメンバーとしてサインインする必要があります。 Administrators グループのメンバーであるアカウントでサインインしているときにタスクを完了できない場合は、Domain Admins グループのメンバーであるアカウントでサインインしているときにタスクを実行するみてください。  
  
#### <a name="to-monitor-remote-client-activity-and-status"></a>リモート クライアントの活動と状態を監視するには  
  
1.  **サーバー マネージャー**, をクリックして **ツール**, 、順にクリック **リモート アクセス管理**します。  
  
2.  クリックして **レポート** に移動する **リモート アクセス レポート** で、 **リモート アクセス管理コンソール**します。  
  
3.  クリックして **リモート クライアントの状態** でリモート クライアントの利用状況と状態のユーザー インターフェイスに移動する、 **リモート アクセス管理コンソール**します。  
  
4.  リモート アクセス サーバーに接続され、詳細なユーザーの一覧が表示されますに関する統計。 クライアントに対応するリストの最初の行をクリックします。 行を選択すると、リモート ユーザーの活動は、プレビュー ウィンドウに表示されます。  
  
windows PowerShell の ![](../../../media/Monitor-connected-remote-clients-for-activity-and-status/PowerShellLogoSmall.gif)***<em>windows powershell の同等のコマンド</em>***  
  
以下の Windows PowerShell コマンドレットは、前述の手順と同じ機能を実行します。 ここでは書式上の制約のために、折り返されて複数の行にわたって表示される場合もありますが、各コマンドレットは 1 行に入力します。  
  
```  
PS> Get-RemoteAccessConnectionStatistics  
```  
  
次の表にフィールドを使用して、条件の選択に基づいて、ユーザーの統計情報をフィルターできます。  
  
|フィールド名|Value|  
|-------|-----|  
|Username|リモート ユーザーのユーザー名またはエイリアス。 Contoso のようなユーザーのグループを選択するワイルドカード文字を使用できる\\* または \*\administrator します。|  
|ホスト名|リモート ユーザーのコンピューター アカウント名。 IPv4 または IPv6 アドレスも指定できます。|  
|種類|DirectAccess または VPN。 DirectAccess を選択すると、DirectAccess を使用して接続されているすべてのリモート ユーザーが一覧表示されます。 VPN を選択すると、VPN を使用して接続されているすべてのリモート ユーザーが一覧表示されます。|  
|ISP アドレス|リモート ユーザーの IPv4 アドレスまたは IPv6 アドレス。|  
|IPv4 アドレス|リモート ユーザーを企業ネットワークに接続しているトンネルの内部 IPv4 アドレス。|  
|IPv6 アドレス|リモート ユーザーを企業ネットワークに接続するトンネルの内部 IPv6 アドレス。|  
|プロトコル/トンネル|リモート クライアントで使用されて、移行テクノロジです。 DirectAccess ユーザーは、Teredo、6to4、または IP-HTTPS は、これとは PPTP、L2TP、SSTP、または IKEv2 VPN ユーザーです。|  
|アクセス先のリソース|特定の企業リソースまたはエンドポイントにアクセスしているすべてのユーザー。 このフィールドに対応する値は、サーバーのホスト名または IP アドレスです。|  
|Server|クライアントの接続先のリモート アクセス サーバー。 クラスター展開とマルチサイト展開にのみ関係します。|  
  
  
  


