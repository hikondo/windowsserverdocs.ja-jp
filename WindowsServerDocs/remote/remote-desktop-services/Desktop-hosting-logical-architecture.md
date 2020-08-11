---
title: リモート デスクトップ サービスのアーキテクチャ
description: RDS のアーキテクチャ図
ms.author: elizapo
ms.date: 02/10/2017
ms.topic: article
ms.assetid: 7f73bb0a-ce98-48a4-9d9f-cf7438936ca1
author: lizap
manager: dongill
ms.openlocfilehash: 756696dc4014801caf74a415117c205d59481ced
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87955099"
---
# <a name="remote-desktop-services-architecture"></a>リモート デスクトップ サービスのアーキテクチャ

>適用先:Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016

エンド ユーザー向けの Windows のアプリとデスクトップをホストするようにリモート デスクトップ サービスを展開するためのさまざまな構成を以下に示します。

>[!NOTE]
> 以下のアーキテクチャ図は、Azure での RDS の使用を示しています。 ただし、リモート デスクトップ サービスは、オンプレミスでも他のクラウドでも展開できます。 これらの図は、主に、RDS のロールがどのように共存し、他のサービスを使用するかを示すことを目的としています。

## <a name="standard-rds-deployment-architectures"></a>標準の RDS 展開アーキテクチャ

リモート デスクトップ サービスには、次の 2 つの標準的アーキテクチャがあります。
-    基本的な展開 – これには、完全に有効な RDS 環境を作成するための最小数のサーバーが含まれます。
-    高可用性の展開 – これには、RDS 環境で保証される最も高い稼働時間を実現するために必要なすべてのコンポーネントが含まれます。

### <a name="basic-deployment"></a>基本的な展開

![基本的な RDS の展開](./media/basic-rds.png)

### <a name="highly-available-deployment"></a>高可用性の展開

![高可用性 RDS の展開](./media/ha-rds.png)

## <a name="rds-architectures-with-unique-azure-paas-roles"></a>固有の Azure PaaS ロールを持つ RDS アーキテクチャ

標準的な RDS 展開アーキテクチャはほとんどのシナリオに適合しますが、Azure では、顧客価値を高めるファースト パーティ PaaS ソリューションに引き続き投資します。 それらが RDS にどのように組み込まれているかを示すいくつかのアーキテクチャを以下に示します。

### <a name="rds-deployment-with-azure-ad-domain-services"></a>Azure AD Domain Services を使用する RDS の展開

上記の 2 つの標準的なアーキテクチャ図は、Windows Server VM に展開される従来型の Active Directory (AD) に基づいています。 ただし、従来の AD はなく、Office365 のようなサービスを介して Azure AD テナントだけがあるが、RDS を活用したいという場合は、[Azure AD Domain Services](/azure/active-directory-domain-services/active-directory-ds-overview) を使って、Azure AD テナントに存在するのと同じユーザーを使用する、完全に管理されたドメインを Azure IaaS 環境に作成することができます。 これにより、ユーザーを手動で同期し、より多くの仮想マシンを管理するという複雑さが解消されます。 Azure AD Domain Services は、基本的な展開と高可用性の展開のどちらでも機能します。

![Azure AD と RDS の展開](./media/aadds-rds.png)

### <a name="rds-deployment-with-azure-ad-application-proxy"></a>Azure AD アプリケーション プロキシを使用する RDS の展開

上記の 2 つの標準的アーキテクチャ図では、RDS システムへのインターネット接続エントリ ポイントとして RD Web サーバー/ゲートウェイ サーバーが使用されています。 環境によっては、管理者は、独自のサーバーを境界から削除して、代わりに、リバース プロキシ テクノロジを介して追加のセキュリティも提供するテクノロジを使用することを選択します。 [Azure AD アプリケーション プロキシ](/azure/active-directory/active-directory-application-proxy-get-started) PaaS ロールは、このシナリオにうまく適合します。

サポートされている構成およびこのセットアップの作成方法については、「[Azure AD アプリケーション プロキシを使用したリモート デスクトップの発行](/azure/active-directory/application-proxy-publish-remote-desktop)」をご覧ください。

![Azure AD アプリケーション プロキシを使用する RDS](./media/aadappproxy-rds.png)
