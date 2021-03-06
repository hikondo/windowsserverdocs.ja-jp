---
title: NPS での NAS 通知の転送を無効にする
description: このトピックでは、Windows Server 2016 でネットワークポリシーサーバーの同時認証を構成する手順について説明します。
manager: brianlic
ms.topic: article
ms.assetid: a09bfb03-95fc-4534-bf3c-97078ef6b07e
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 72ac7d13005fef609df437ce3fcb4e12f617a400
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87946976"
---
# <a name="disable-nas-notification-forwarding-in-nps"></a>NPS での NAS 通知の転送を無効にする

>適用先:Windows Server (半期チャネル)、Windows Server 2016

ネットワークアクセスサーバー (Nas) から NPS に構成されているリモート RADIUS サーバーグループのメンバーへの開始および停止メッセージの転送を無効にするには、次の手順を実行します。

リモート RADIUS サーバーグループが構成されていて、NPS**接続要求ポリシー**で [**このリモート radius サーバーグループにアカウンティング要求を転送**する] チェックボックスをオフにした場合、これらのグループには引き続き NAS の開始および停止通知メッセージが送信されます。

そのため、ネットワーク トラフィックが不必要に増大することになります。 このトラフィックを排除するには、各リモート RADIUS サーバーグループ内の個々のサーバーに対する NAS 通知転送を無効にします。

この手順を完了するには、**Administrators** グループのメンバーである必要があります。

### <a name="to-disable-nas-notification-forwarding"></a>NAS の通知転送を無効にするには

1. サーバー マネージャーで **[ツール]** をクリックし、 **[ネットワーク ポリシー サーバー]** をクリックします。 NPS コンソールが開きます。

2. NPS コンソールで、[ **Radius クライアントとサーバー**] をダブルクリックし、[**リモート radius サーバーグループ**] をクリックして、構成するリモート radius サーバーグループをダブルクリックします。 [リモート RADIUS サーバーグループの**プロパティ**] ダイアログボックスが表示されます。

3. 構成するグループメンバーをダブルクリックし、[**認証/アカウンティング**] タブをクリックします。

4. [**アカウンティング**] で、[**ネットワークアクセスサーバーの開始と停止の通知をこのサーバーに転送する**] チェックボックスをオフにし、[ **OK]** をクリックします。

5. 構成するすべてのグループメンバーに対して、手順 3. と 4. を繰り返します。

NPS の管理の詳細については、「 [Manage Network Policy Server](nps-manage-top.md)」を参照してください。

NPS の詳細については、「[ネットワークポリシーサーバー (nps)](nps-top.md)」を参照してください。
