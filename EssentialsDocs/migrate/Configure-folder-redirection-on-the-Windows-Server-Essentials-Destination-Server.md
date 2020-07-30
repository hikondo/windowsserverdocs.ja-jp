---
title: Windows Server Essentials の移行先サーバーでフォルダー リダイレクトを構成する
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.topic: article
ms.assetid: fe77ba67-128c-4fc3-9361-30fa6af42516
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: b76246e24f17538741c278d432fa1ec275e891eb
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87180798"
---
# <a name="configure-folder-redirection-on-the-windows-server-essentials-destination-server"></a>Windows Server Essentials の移行先サーバーでフォルダー リダイレクトを構成する

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

移行元サーバーでフォルダー リダイレクトが有効になっている場合、このタスクを実行します。

 最初に、古いフォルダー リダイレクト グループ ポリシーの設定を削除します。 次に、Windows Server Essentials ダッシュボードを使用して、移行先サーバーでフォルダーリダイレクトを有効にします。

### <a name="to-delete-the-old-folder-redirection-group-policy-setting"></a>古いフォルダー リダイレクト グループ ポリシーの設定を削除するには

1. 移行先サーバーで、[**グループ ポリシーの管理**] 管理ツールを開きます。

2. **グループポリシー管理**] で、 **[フォレスト:**<em>ネットワークドメイン名</em>]、[**ドメイン**]、[*ネットワークドメイン名*] の順に展開し、[**グループポリシーオブジェクト**] を展開します。

3. [**SBS グループ ポリシー フォルダー リダイレクト**] を右クリックし、[**削除**] をクリックします。

4. [**SBS グループ ポリシー セキュリティ テンプレート**] を右クリックして、[**削除**] をクリックします。

5. 警告を読み、[**はい**] をクリックします。

6. **[グループ ポリシー管理]** を閉じます。

### <a name="to-enable-folder-redirection-on-the-destination-server"></a>移行先サーバーでフォルダー リダイレクトを有効にするには

1. 移行先サーバーで、Windows Server Essentials ダッシュボードを開きます。

2. ナビゲーション バーで、[**デバイス**] をクリックします。

3. [**デバイスのタスク**] ウィンドウで、[**グループ ポリシーの実装**] をクリックします。

4. [**フォルダー リダイレクト グループ ポリシーを有効にする**] ページで、リダイレクトするフォルダーを選択し、[**次へ**] をクリックします。

5. [**セキュリティ ポリシー設定を有効にする**] ページで、[**完了**] をクリックします。

   フォルダー リダイレクトの変更を適用するには、ネットワーク ユーザーはコンピューターからログオフした後、ログオンし直す必要があります。 これにより、リダイレクトされるすべてのフォルダーが移行先サーバーに転送されます。
