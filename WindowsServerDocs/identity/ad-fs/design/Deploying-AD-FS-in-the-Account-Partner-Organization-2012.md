---
ms.assetid: 9aaca9c5-ce44-495c-aad6-61aede87a83f
title: アカウント パートナー組織での AD FS の展開
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: db72dd69a44d90a89a255b7d974f0cf1816bd722
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87954328"
---
# <a name="deploying-ad-fs-in-the-account-partner-organization"></a>アカウント パートナー組織での AD FS の展開

Active Directory フェデレーションサービス (AD FS) AD FS のアカウントパートナーは、 \( \) サポートされている属性ストアにユーザーアカウントを物理的に格納する、フェデレーションの信頼関係にある組織を表します。 サポートされている属性ストアの詳細については、「[属性ストアの役割](../../ad-fs/technical-reference/The-Role-of-Attribute-Stores.md)」を参照してください。

アカウントパートナー組織のフェデレーションサーバーは、ローカルユーザーを認証し、リソースパートナーが承認の決定を行うときに使用するセキュリティトークンを作成します。 これにより、Web サイトや Web サービスなどの証明書利用者は、自身をフェデレーションサーバーに簡単に登録し、発行されたトークンを使用して認証とアクセス制御を行うことができます。

複数のフェデレーションアプリケーションまたはサービスへのアクセスをユーザーに提供する必要があるシナリオでは、各アプリケーションまたはサービスが別の組織によってホストされている場合は、複数の証明書利用者を展開できるようにアカウントパートナーのフェデレーションサーバーを構成できます。

アカウント パートナー組織のセットアップ方法と構成方法の詳細については、「 [Checklist: Configuring the Account Partner Organization](../../ad-fs/deployment/Checklist--Configuring-the-Account-Partner-Organization.md)」を参照してください。

## <a name="in-this-section"></a>このセクションの内容

-   [アカウント パートナー内のフェデレーション サーバーの役割を確認する](Review-the-Role-of-the-Federation-Server-in-the-Account-Partner.md)

-   [アカウント パートナー内のフェデレーション サーバー プロキシの役割を確認する](Review-the-Role-of-the-Federation-Server-Proxy-in-the-Account-Partner.md)

-   [アカウントパートナーでクライアントコンピューターを準備する](Prepare-Client-Computers-in-the-Account-Partner.md)

## <a name="see-also"></a>参照
[Windows Server 2012 での AD FS 設計ガイド](AD-FS-Design-Guide-in-Windows-Server-2012.md)
