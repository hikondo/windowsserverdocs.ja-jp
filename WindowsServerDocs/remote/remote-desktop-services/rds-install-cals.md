---
title: RDS クライアント アクセス ライセンスをインストールする
description: RD クライアントの CAL をインストールする方法について説明します。
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.topic: article
author: lizap
ms.author: elizapo
ms.date: 09/20/2016
manager: dongill
ms.openlocfilehash: 3a9f73418bd4da67c97db30a3272588afc287b95
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "80860445"
---
# <a name="install-rds-client-access-licenses-on-the-remote-desktop-license-server"></a>リモート デスクトップ ライセンス サーバーに RDS クライアント アクセス ライセンスをインストールする

>適用先:Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016

ライセンス サーバーにリモート デスクトップ サービス クライアント アクセス ライセンス (CAL) をインストールするには、次の情報を使用します。 CAL がインストールされると、ライセンス サーバーは必要に応じてそれらをユーザーに発行します。

インターネット接続は、リモート デスクトップ ライセンス マネージャーを実行しているコンピューターでは必要ですが、ライセンス サーバーを実行しているコンピューターでは必要ありません。

1. ライセンス サーバー (通常は 1 番目の RD 接続ブローカー) で、リモート デスクトップ ライセンス マネージャーを開きます。
2. ライセンス サーバーを右クリックして、 **[ライセンスのインストール]** をクリックします。
3. ウェルカム ページで、 **[次へ]** をクリックします。
4. RDS CAL を購入したときのプログラムを選択し、 **[次へ]** をクリックします。 サービス プロバイダーである場合は、 **[Service Provider License Agreement]** (サービス プロバイダー ライセンス契約) を選択します。
5. ライセンス プログラムの情報を入力します。 ほとんどの場合、これは、ライセンス コードか契約番号になりますが、使用しているライセンス プログラムによって異なります。
6. **[次へ]** をクリックします。
7. お使いの環境に合わせて製品バージョン、ライセンスの種類、およびライセンスの数を選択し、 **[次へ]** をクリックします。 ライセンス マネージャーは、Microsoft クリアリングハウスに問い合わせて、ライセンスの検証および取得を行います。
8.  **[完了]** をクリックして、注文プロセスを完了します。