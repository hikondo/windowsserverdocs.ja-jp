---
title: Web サーバー WEB1 をインストールする
description: このトピックでは、802.1 X ワイヤードおよびワイヤレス展開の証明書をサーバーのデプロイ ガイドの一部
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: f51c9e38-98bb-49c1-9d39-427d07021499
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 8871b2b82b30bca5b4efd62a31b52e8dbd7284a9
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80318284"
---
# <a name="install-the-web-server-web1"></a>Web サーバー WEB1 をインストールする

>適用対象: Windows Server (半期チャネル)、Windows Server 2016

Windows Server 2016 で Web サーバー (IIS) ロールは、信頼性の高い web サイト、サービス、およびアプリケーションをホストするため、セキュリティで保護された、管理が容易なモジュール化および拡張可能なプラットフォームを提供します。 IIS では、インターネット、イントラネットまたはエクストラネット上のユーザーと情報を共有できます。 IIS は、IIS、ASP.NET、FTP サービス、PHP、および Windows Communication Foundation (WCF) を一体化した統合 web プラットフォームです。  

サーバー証明書を展開するときに、Web サーバーは証明機関 (CA) の証明書失効リスト (CRL) を公開できる場所を提供します。 発行した後、CRL は、認証プロセス中にこの一覧を別のコンピュータで提示された証明書が取り消されていないことを確認に使用できるように、ネットワーク上のすべてのコンピューターにアクセスできます。   

失効と CRL に証明書がある場合は、認証作業は失敗し、コンピューターが保護を無効になっている証明書を持つエンティティを信頼します。  

Web サーバー (IIS) の役割をインストールする前に、サーバー名と IP アドレスを構成して、コンピューターをドメインに参加することを確認します。  

## <a name="to-install-the-web-server-iis-server-role"></a>Web サーバー (IIS) サーバーの役割をインストールするには  
この手順を完了するには、**Administrators** グループのメンバーである必要があります。  

>[!NOTE]  
>Windows PowerShell を使用してこの手順を実行するには、PowerShell と、次のコマンドを入力し、ENTER キーを押します。  
`Install-WindowsFeature Web-Server -IncludeManagementTools`  

1.  サーバー マネージャーで、 **[管理]** をクリックし、 **[役割と機能の追加]** をクリックします。 役割と機能の追加ウィザードが起動されます。  
2.  **[開始する前に]** で **[次へ]** をクリックします。  

**注**   
**開始する前に** 以前に実行した追加の役割と機能のウィザードと選択した場合に、役割の追加機能のウィザードのページが表示されない **既定ではこのページをスキップ** その時点でします。  

3. **[インストールの種類]** ページで、 **[次へ]** をクリックします。  
4. **サーバーの選択** ] ページで [ **次**します。  
5. **サーバーの役割**  ページで、 **Web サーバー (IIS)** , 、 をクリックし、 **次**します。  
6. 既定の Web サーバーの設定をすべて受け入れるまで **[次へ]** をクリックしてから、 **[インストール]** をクリックします。  
7. すべてのインストールに成功したことを確認し、 **[閉じる]** をクリックします。
