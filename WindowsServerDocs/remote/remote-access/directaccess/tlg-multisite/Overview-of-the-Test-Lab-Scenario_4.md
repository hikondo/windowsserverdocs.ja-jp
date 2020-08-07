---
title: テスト ラボのシナリオの概要
description: このトピックは、「Windows Server 2016 用の DirectAccess マルチサイト展開のテストラボガイド」の一部です。
manager: brianlic
ms.topic: article
ms.assetid: 9afeced4-1a9b-4cb3-9fc4-d7e44c675755
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 5f442608fc21069a400acf0ded8d955e51791111
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87950947"
---
# <a name="overview-of-the-test-lab-scenario"></a>テスト ラボのシナリオの概要

>適用先:Windows Server (半期チャネル)、Windows Server 2016

このテスト ラボのシナリオでは、DirectAccess に展開されます。

-   **DC1**- ドメイン コント ローラーとして構成されているサーバー、DNS サーバーおよび DHCP サーバーを corp.contoso.com ドメイン。

-   **2 DC1**- ドメイン コント ローラーと corp2.corp.contoso.com ドメインの DNS サーバーとして構成されているサーバーです。

-   **EDGE1 と 2 EDGE1**-リモート アクセス サーバーとして構成されている内部ネットワーク上の 2 つのサーバーです。 各サーバーには 2 つのネットワーク アダプターです。内部ネットワークに接続されているいずれかと、外部ネットワークに接続されている他のです。

-   **APP1 および 2 APP1**-web サービスとファイル サーバーとして構成されている内部ネットワーク上の 2 つのサーバーです。

-   **APP2**- IPv4 のみ web サービスとファイル サーバーとして構成されている内部ネットワーク上のコンピューターです。 このコンピューターは、nat64/dns64 機能を強調表示に使用されます。

-   **ROUTER1**2 つの企業内部ネットワーク間のルーティングを提供するように構成するには、サーバーです。

-   **INET1**- インターネット DNS と DHCP サーバーとして構成されているサーバーです。

-   **NAT1**のインターネット接続の共有を使用して、ネットワーク アドレス変換器 (NAT) デバイスとして構成されているクライアント コンピューター。

-   **CLIENT1 および CLIENT2**-内部のネットワーク、シミュレートされたインターネットやホーム ネットワーク間を移動するときに、DirectAccess の接続をテストするために使用する DirectAccess クライアントとして構成されている 2 台のクライアント コンピューター。 **CLIENT2** Windows 7 は、&reg;  クライアントです。

テスト ラボは、次をシミュレートする 4 つのサブネットで構成されます。

-   NAT でインターネットに接続されているホームネット (192.168.137.0/24) という名前のホーム ネットワーク

-   インターネット サブネット (131.107.0.0/24) によって表される外部ネットワークです。

-   Corpnet という名前の内部ネットワーク (10.0.0.0/24; 2001:db8:1::/64) EDGE1 のリモート アクセス サーバーによって、インターネットから分離します。

-   内部ネットワークという 2 Corpnet1 (10.2.0.0/24; 2001:db8:2::/64) 2 EDGE1 リモート アクセス サーバーによって、インターネットから分離します。

各サブネット上のコンピューターは、次の図に示すように、物理または仮想ハブまたはスイッチを使用して接続します。

![テスト ラボの概要](../../../media/Overview-of-the-Test-Lab-Scenario_4/TLG_DA_Multisite.png)



