---
title: Windows Server Essentials でのファイアウォールのトラブルシューティング
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 51d94b67-8b9b-4159-80dd-f652d73a43cb
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: d1a36ecbd62e658c6361c004cf0166a295641b35
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89625042"
---
# <a name="troubleshoot-your-firewall-in-windows-server-essentials"></a>Windows Server Essentials でのファイアウォールのトラブルシューティング

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

 リモート アクセスで問題が発生した場合は、Anywhere Access の修復ウィザードを実行します。

### <a name="to-run-the-repair-anywhere-access-wizard"></a>Anywhere Access の修復ウィザードを実行するには

1. ダッシュボードを開きます。

2. **[設定]** をクリックし、**[Anywhere Access]** タブをクリックし、**[修復]** をクリックします。

3. Anywhere Access の修復ウィザードの指示に従います。

   高度なネットワーク設定または Microsoft 以外のファイアウォールを使用している場合は、ファイアウォールで追加のポートを開く必要が生じる場合があります。 Internet Assigned Numbers Authority (IANA) では次の表のポートが登録されています。

|ポート番号|Description|
|-----------------|-----------------|
|65500|証明書の Web サービス|
|65510 と 65515|クライアント コンピューターの展開 Web サイト|
|65520|Mac クライアント コンピューターの Web サービス|
|65532|サーバー ループバック通信のプロバイダー フレームワーク|
|6602|サーバー コンピューターとクライアント コンピューター間の通信のプロバイダー フレームワーク|

## <a name="see-also"></a>こちらもご覧ください

-   [リモート Web アクセスの使用](../use/Use-Remote-Web-Access-in-Windows-Server-Essentials.md)

-   [リモート Web アクセスの管理](../manage/Manage-Remote-Web-Access-in-Windows-Server-Essentials.md)

-   [Anywhere Access の管理](../manage/Manage-Anywhere-Access-in-Windows-Server-Essentials.md)

-   [Windows Server Essentials の管理](../manage/Manage-Windows-Server-Essentials.md)

-   [Windows Server Essentials のサポート](../support/Support-Windows-Server-Essentials.md)

