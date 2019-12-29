---
ms.assetid: a8558c9d-0606-4881-93b2-f2d2716b18e7
title: Windows Server 2012 R2 での AD FS 設計ガイド
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 614bc2b4571dd8a1b35c075ae1dec6934e77e148
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408166"
---
# <a name="ad-fs-design-guide-in-windows-server"></a>Windows Server の AD FS 設計ガイド 

Active Directory フェデレーションサービス (AD FS) \(AD FS\) を使用すると、セキュリティで保護されたエンタープライズ、フェデレーションパートナー組織、またはクラウド内のアプリケーションへのアクセスを必要とするエンドユーザー向けに、シンプルで安全な id フェデレーションと Web シングルサイン\-を \(SSO\) 機能に提供できます。\-  
  
Windows Server® 2012 R2 では、AD FS に、id プロバイダーとして機能するフェデレーションサービス役割サービスが含まれています。これは、ユーザーを認証して AD FS\) を信頼するアプリケーションにセキュリティトークンを提供し \(フェデレーションプロバイダーとして使用して、他の id プロバイダーからのトークンを使用し、\(を信頼するアプリケーションにセキュリティトークンを提供\)  
  
Windows Server 2012 R2 の AD FS によって保護されたアプリケーションやサービスへのエクストラネット アクセスを提供する機能は、Web アプリケーション プロキシと呼ばれる新しいリモート アクセス役割サービスによて実行されるようになりました。 以前のバージョンの Windows Server では、この機能は AD FS フェデレーション サーバー プロキシによって処理されていました。 Web アプリケーションプロキシは、関連するエクストラネットシナリオやその他のエクストラネットシナリオに AD FS\-アクセスできるように設計されたサーバーの役割です。 Web アプリケーションプロキシの詳細については、 [Web アプリケーションプロキシのチュートリアルガイド](https://technet.microsoft.com/library/dn280944.aspx)を参照してください。  
  
## <a name="about-this-guide"></a>このガイドについて  
このガイドでは、組織の要件に基づいて、AD FS の新しい展開を計画する際に役立つ推奨事項について説明します。 このガイドの対象読者は、インフラストラクチャ専門家またはシステム アーキテクトです。 AD FS の展開を計画する際に、主な意思決定点に焦点を当てます。 このガイドを読む前に、AD FS が機能レベルでどのように機能するかについて十分に理解しておく必要があります。 詳細については、「 [Understanding Key AD FS Concepts](../../ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md)」を参照してください。  
  
## <a name="in-this-guide"></a>このガイドについて  
  
-   [AD FS 展開目標の特定](Identify-Your-AD-FS-Deployment-Goals.md)  
  
-   [AD FS 展開トポロジの計画](Plan-Your-AD-FS-Deployment-Topology.md)  
  
-   [AD FS の要件](AD-FS-Requirements.md)  
  
  
## <a name="see-also"></a>参照  
[AD FS の設計](../../ad-fs/AD-FS-Design.md)  
  

