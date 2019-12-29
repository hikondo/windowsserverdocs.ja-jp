---
title: 手順 9 EDGE1 を構成する
description: このトピックは、「Windows Server 2016 用の DirectAccess マルチサイト展開のテストラボガイド」の一部です。
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f6e8d85b-de65-43b3-bf3e-ec84471a1fcc
ms.author: pashort
author: shortpatti
ms.openlocfilehash: ce86a75ac5b8d53874d2fc5c6743979506591680
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71388231"
---
# <a name="step-9-configure-edge1"></a>手順 9 EDGE1 を構成する

>適用先:Windows Server (半期チャネル)、Windows Server 2016

EDGE1 サーバーでは、次の手順が実行されます。  
  
1. EDGE1 で DNS サーバーを構成します。 EDGE1 の corp2.corp.contoso.com ドメインから DNS サーバーを構成する必要があります。  
  
2. サブネット間のルーティングを構成します。 EDGE1 でルーティングを構成して、企業ネットワークと2ネットワークのサブネット間の通信を有効にします。  
  
## <a name="IPv6"></a>EDGE1 で DNS サーバーを構成する  
  
1.  サーバーマネージャーコンソールで **[ローカルサーバー]** をクリックし、 **[プロパティ]** 領域の [企業**ネットワーク] の横にある**リンクをクリックします。  
  
2.  [ネットワーク接続] ウィンドウで、[企業ネットワーク **] を右クリックし**、 **[プロパティ]** をクリックします。  
  
3.  **[インターネット プロトコル バージョン 4 (TCP/IPv4)]** をクリックし、 **[プロパティ]** をクリックします。  
  
4.  **[代替 DNS サーバー]** に、「 **10.2.0.1**」と入力します。 **[OK]** をクリックします。  
  
5.  **[インターネット プロトコル バージョン 6 (TCP/IPv6)]** をクリックし、 **[プロパティ]** をクリックします。  
  
6.  **[代替 DNS サーバー]** に「 **2001: db8: 2:: 1** 」と入力し、[ **OK]** をクリックします。  
  
7.  企業ネットワークの **[プロパティ]** ダイアログボックスで、 **[閉じる]** をクリックします。  
  
8.  **[ネットワーク接続]** ウィンドウを閉じます。  
  
## <a name="ConfigRouting"></a>サブネット間のルーティングを構成する  
  
1.  **スタート**画面で、「**cmd.exe**」と入力し、 **[cmd]** を右クリックして、 **[詳細設定]** をクリックし、 **[管理者として実行]** をクリックします。 **[ユーザー アカウント制御]** ダイアログ ボックスが表示されたら、表示された操作が正しいことを確認し、 **[はい]** をクリックします。  
  
2.  コマンドプロンプトウィンドウで、次のコマンドを入力します。 各コマンドを入力したら、enter キーを押します。  
  
    ```  
    netsh interface IPv4 add route 10.2.0.0/24 Corpnet 10.0.0.254  
    netsh interface IPv6 add route 2001:db8:2::/64 Corpnet 2001:db8:1::fe  
    ```  
  
3.  コマンド プロンプト ウィンドウを閉じます。  
  


