---
title: Windows Server Update Services を展開する
description: Windows Server Update Service (WSUS) のトピック - 展開プロセスの概要とそれを実現するための 4 つの手順へのリンク
ms.topic: get-started-article
ms.assetid: 2708f6b2-4252-4b8f-9b7e-84c9b4222075
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 78df9b93205e07e58310ad2077571b29b9ff5360
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624548"
---
# <a name="deploy-windows-server-update-services"></a>Windows Server Update Services を展開する

>適用先:Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows Server Update Services (WSUS) を使用すると、IT 管理者は Microsoft 製品の最新の更新プログラムを展開できます。 WSUS は Windows Server のサーバーの役割の 1 つで、更新プログラムを管理および配布するためにインストールできます。 1 台の WSUS サーバーを、組織内にある他の WSUS サーバー用の更新プログラムの供給元として運用できます。 更新プログラムの供給元として機能する WSUS サーバーは、"アップストリーム サーバー" と呼ばれます。

WSUS 実装では、利用可能な更新プログラムの情報を入手するために、ネットワーク内にある WSUS サーバーのうち少なくとも 1 台を Microsoft Update に接続する必要があります。 ユーザーは、ネットワークのセキュリティと構成に基づいて、Microsoft Update に直接接続するサーバーの台数を決めることができます。

Windows Server Update Services を計画して展開するための概念について説明します。

-   [WSUS 展開を計画する](../plan/plan-your-wsus-deployment.md)

-   [手順 1: WSUS サーバーの役割をインストールする](1-install-the-wsus-server-role.md)

-   [手順 2:WSUS を構成する](2-configure-wsus.md)

-   [手順 3:WSUS で更新プログラムを承認および展開する](3-approve-and-deploy-updates-in-wsus.md)

-   [手順 4:自動更新のグループ ポリシー設定を構成する](4-configure-group-policy-settings-for-automatic-updates.md)
