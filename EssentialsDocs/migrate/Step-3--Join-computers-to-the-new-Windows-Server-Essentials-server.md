---
title: '手順 3: 新しい Windows Server Essentials サーバーにコンピューターを参加させる'
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.topic: article
ms.assetid: a0e07d1a-8409-429b-87d7-0f4a7e14d668
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 7495831c6f593b65261fda8f50d4ef9d1000d9b4
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89625488"
---
# <a name="step-3-join-computers-to-the-new-windows-server-essentials-server"></a>手順 3: 新しい Windows Server Essentials サーバーにコンピューターを参加させる

>適用対象: Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials

移行プロセスの次の手順では、Windows Server Essentials を実行している新しいサーバーにクライアントコンピューターを接続します。

> [!NOTE]
>  Windows XP または Windows Vista オペレーティング システムを搭載しているコンピューターの場合は、この手順をスキップできます。 Windows Server コネクタ ソフトウェアは、Windows XP または Windows Vista を実行しているコンピューターはサポートしていません。

 クライアントコンピューターを新しい Windows Server Essentials サーバーに参加させる前に、クライアントコンピューターで Windows Server コネクタソフトウェアをアンインストールして、移行元サーバーからクライアントコンピューターを切断する必要があります。

### <a name="to-uninstall-windows-server-connector-on-a-client-computer"></a>クライアント コンピューターで Windows Server コネクタをアンインストールするには

1.  クライアント コンピューターでコントロール パネルを開き、[**プログラムと機能**] を開きます。

2.  プログラムのリストで、コンピューターで実行しているコネクタ アプリケーションを右クリックします。

    > [!NOTE]
    >  コネクタアプリケーションは、クライアントコンピューターが接続されていた Windows Server Essentials のバージョンに応じて、 **Windows Small Business Server 2011 Essentials connector**または **Windows server essentials connector**にすることができます。

3.  **[アンインストール]** をクリックします。

### <a name="to-reconnect-a-client-computer-to-the-server"></a>クライアント コンピューターをサーバーに再接続するには

1.  サーバーに接続するコンピューターにサインインします。

    > [!NOTE]
    >  このコンピューターに複数のユーザー アカウントがある場合は、コンピューターをサーバーに接続した後も残しておくドキュメント、ピクチャ、個人設定を持つユーザー アカウントを使用してサインインします。

2.  Internet Explorer などのインターネット ブラウザーを開きます。

3.  アドレスバーに「 **http://<servername \> /Connect**」と入力し、enter キーを押します。

4.  画面の指示に従って、新しい Windows Server Essentials サーバーにクライアントコンピューターを参加させます。

## <a name="next-steps"></a>次の手順
 Windows Server Essentials を実行している新しいサーバーにクライアントコンピューターを参加させました。 [次に、「手順 4: Windows Server Essentials への移行のために設定とデータを移行先サーバーに移動](Step-4--Move-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md)する」に進みます。


すべての手順を表示するには、「 [Windows Server Essentials への移行](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md)」を参照してください。

