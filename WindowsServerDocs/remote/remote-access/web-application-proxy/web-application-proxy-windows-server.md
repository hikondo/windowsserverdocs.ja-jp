---
ms.assetid: d8adcb68-18e0-41bf-a817-d57344bf2e7d
title: Windows Server 2016 における Web アプリケーション プロキシ
description: ''
author: kgremban
manager: femila
ms.date: 07/13/2016
ms.topic: article
ms.prod: windows-server
ms.technology: web-app-proxy
ms.openlocfilehash: 4f2827f02ec13d187cdf360637882c6c9d4b2441
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71387975"
---
# <a name="web-application-proxy-in-windows-server-2016"></a>Windows Server 2016 における Web アプリケーション プロキシ

>適用対象: Windows Server 2016

**このコンテンツは、オンプレミスバージョンの Web アプリケーションプロキシに関連しています。クラウド経由でオンプレミスアプリケーションへの安全なアクセスを実現するには、 [Azure AD アプリケーションプロキシのコンテンツ](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-get-started/)を参照してください。**  
  
このセクションの内容では、Windows Server 2016 用の Web アプリケーションプロキシの新機能と変更された機能について説明します。 ここに記載されている新機能と変更点は、プレビューを操作するときに最も大きな影響を与える可能性の高いものです。  
  
## <a name="web-application-proxy-new-features-in-windows-server-2016"></a>Windows Server 2016 の Web アプリケーションプロキシの新機能
  
- HTTP 基本アプリケーションの発行の事前認証  
  
  HTTP Basic は、多数のプロトコル (ActiveSync など) によって使用される認証プロトコルで、スマートフォンなどのリッチクライアントを Exchange メールボックスに接続します。 従来、Web アプリケーションプロキシは、ActiveSync クライアントでサポートされていないリダイレクトを使用して AD FS とやり取りします。 この新しいバージョンの Web アプリケーションプロキシでは、http アプリがアプリケーションの要求されていない証明書利用者信頼をフェデレーションサービスに受信できるようにすることで、HTTP basic を使用してアプリを発行するためのサポートを提供します。  
  
  HTTP 基本発行の詳細については、「 [AD FS 事前認証を使用してアプリケーションを公開する](Publishing-Applications-using-AD-FS-Preauthentication.md#publish-an-application-that-uses-http-basic)」を参照してください。  
  
- ワイルドカードによるアプリケーションのドメイン公開  
  
  SharePoint 2013 のようなシナリオをサポートするために、アプリケーションの外部 URL にワイルドカードを含めることができるようになりました。これにより、 https://*. sp-アプリなど、特定のドメイン内から複数のアプリケーションを発行できます。 これにより、SharePoint アプリの発行が簡単になります。  
  
- HTTP から HTTPS へのリダイレクト  
  
  URL に HTTPS を入力しない場合でも、ユーザーがアプリにアクセスできるようにするために、Web アプリケーションプロキシで HTTP から HTTPS へのリダイレクトがサポートされるようになりました。  
  
- HTTP 発行  
  
  パススルー事前認証を使用して HTTP アプリケーションを公開できるようになりました  
  
- リモートデスクトップゲートウェイアプリの発行  
  
  Web アプリケーションプロキシの RDG の詳細については、「 [SharePoint、Exchange、および RDG を使用したアプリケーションの発行](../web-application-proxy/Publishing-Applications-with-SharePoint,-Exchange-and-RDG.md)」を参照してください。  
  
- 詳細なトラブルシューティングと改善されたサービスログを記録し、完全な監査証跡を作成し、エラー処理を改善します。  
  
  トラブルシューティングの詳細については、「 [Web アプリケーションプロキシのトラブルシューティング](https://technet.microsoft.com/library/dn770156.aspx)」を参照してください。  
  
- 管理コンソール UI の機能強化  
  
- バックエンドアプリケーションへのクライアント IP アドレスの伝達  
  
## <a name="see-also"></a>参照  
  
-   [Windows Server 2016 の新機能](https://technet.microsoft.com/library/dn765472.aspx)  
  
-   [AD FS 事前認証を使用してアプリケーションを公開する](../web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication.md)  
  
-   [Web アプリケーション プロキシのトラブルシューティング](https://technet.microsoft.com/library/dn770156.aspx)  
  


