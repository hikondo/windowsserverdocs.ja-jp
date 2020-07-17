---
title: 通知の制限を構成する
description: この記事では、さまざまな通知の種類ごとに時間制限を設定する方法を説明します。
ms.date: 7/7/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 32728fc9b19fca458b7ac4b86f3b550d9ff29490
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "85474169"
---
# <a name="configure-notification-limits"></a>通知の制限を構成する

> 適用対象: Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2

クォータのしきい値の超過や承認されていないファイルの保存などに関する通知は、繰り返し何度も発生することがあります。このような通知が頻繁に発生することを抑えるため、ファイル サーバー リソース マネージャーでは、次の種類の通知について時間の制限が適用されています。

-   電子メール
-   イベント ログ
-   コマンド
-   レポート

これらの各制限により、構成対象の種類の通知は、最初の通知が生成された後、指定した時間が経過するまで同一の問題についての 2 回目の通知は生成されません。

既定では、それぞれの通知の種類ごとに 60 分の制限が設定されていますが、この値は変更することができます。 制限は、クォータのしきい値に関する通知であるか、ファイルのスクリーン処理イベントに関する通知であるかを問わず、同じ種類のすべての通知に適用されます。

## <a name="to-specify-a-standard-notification-limit-for-each-notification-type"></a>通知の種類ごとに標準の通知の制限を指定するには

1.  コンソール ツリーで、**[ファイル サーバー リソース マネージャー]** を右クリックし、**[オプションの構成]** をクリックします。 [**ファイル サーバー リソース マネージャーのオプション**] ダイアログ ボックスが開きます。

2.  **[通知の制限]** タブで、表示されているそれぞれの通知の種類に対して、分単位で値を入力します。

3.  **[OK]** をクリックします。

> [!Note]
> 特定のクォータまたはファイル スクリーンの通知に関連付けられている時間制限をカスタマイズするには、[ファイル サーバー リソース マネージャー](https://technet.microsoft.com/itpro/powershell/windows/fileserverresourcemanager/fileserverresourcemanager)のコマンド ライン ツールである **Dirquota.exe** と **Filescrn.exe** を使用できます。

## <a name="additional-references"></a>その他のリファレンス

-   [ファイル サーバー リソース マネージャーのオプションを設定する](setting-file-server-resource-manager-options.md)
-   [コマンドライン ツール](command-line-tools.md)