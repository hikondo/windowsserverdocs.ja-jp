---
title: Windows Server Essentials でのデバイスの管理
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.topic: article
ms.assetid: f5fe1088-ebe7-4799-a47d-075b0048dea1
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 96d99bb41a528a3a2f86be2d876df6e777e4b790
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89623144"
---
# <a name="manage-devices-in-windows-server-essentials"></a>Windows Server Essentials でのデバイスの管理

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

 以下のセクションでは、サーバーのデバイス管理機能について説明し、さらに、ネットワーク上のデバイスを設定して使用する方法について説明します。

-   [ダッシュボードを使用したデバイスの管理](Manage-Devices-in-Windows-Server-Essentials.md#BKMK_1)

-   [特定のネットワーク コンピューターにログオンするためのアクセス許可をユーザー アカウントに割り当てる](Manage-Devices-in-Windows-Server-Essentials.md#BKMK_2)

-   [サーバーからのコンピューターの削除](Manage-Devices-in-Windows-Server-Essentials.md#BKMK_3)

-   [フォルダー リダイレクトとセキュリティ用のグループ ポリシー設定を構成する](Manage-Devices-in-Windows-Server-Essentials.md#BKMK_5)

-   [リモート デスクトップ セッションを使用してネットワーク コンピューターに接続する](Manage-Devices-in-Windows-Server-Essentials.md#BKMK_7)

-   [コンピューターのプロパティを表示する](Manage-Devices-in-Windows-Server-Essentials.md#BKMK_8)

##  <a name="manage-devices-by-using-the-dashboard"></a><a name="BKMK_1"></a> ダッシュボードを使用してデバイスを管理する
 Windows Server Essentials では、Windows Server Essentials ダッシュボードを使用して、一般的な管理タスクを実行することができます。 ダッシュボードの **[デバイス]** ページには、次の項目が表示されます。

-   次の情報を含む、ネットワーク コンピューターの一覧

    -   コンピューターの名前

    -   コンピューターの状態 (**[オンライン]** または **[オフライン]** のいずれか)

    -   コンピューターの説明

    -   コンピューターのバックアップの状態

    -   コンピューターの更新の状態

    -   コンピューターのセキュリティの状態

    -   コンピューターのアラートの状態

    -   コンピューターのグループ ポリシー情報

-   選択したコンピューターについての追加情報が表示される詳細ウィンドウ

-   一連のデバイス管理タスク (コンピューターのプロパティとアラートの表示、コンピューターのバックアップのセットアップ、バックアップからのファイルとフォルダーの復元など) が含まれる作業ウィンドウ

#### <a name="to-view-the-status-of-network-computers"></a>ネットワーク コンピューターの状態を表示するには

1. Windows Server Essentials ダッシュボードを開きます。

2. ナビゲーション バーで、**[デバイス]** をクリックします。

3. 一覧ウィンドウに、ネットワーク内のすべてのコンピューターの状態が表示されます。

   次の表で、Windows Server Essentials ダッシュボードで利用できる、コンピューターとバックアップに関するさまざまなタスクについて説明します。 一部のタスクはコンピューターに固有であり、一覧からコンピューターを選択した場合にのみ表示されます。

### <a name="computer-tasks-in-the-dashboard"></a>ダッシュボードでのコンピューターに関するタスク

|タスク名|Description|
|---------------|-----------------|
|コンピューターのプロパティの表示|選択したコンピューターの一般的な情報が表示されます。さらに、コンピューターのバックアップの詳細を確認することができます。|
|このコンピューターのバックアップの設定|バックアップの設定ウィザードを実行します。|
|コンピューターのバックアップのカスタマイズ|バックアップのプロパティが表示されます。選択したコンピューターのバックアップの設定を変更することができます。|
|コンピューターのバックアップの開始|選択したコンピューターのバックアップを開始します。|
|コンピューターのバックアップの停止|選択したコンピューターのバックアップを停止します。|
|コンピューターのファイルまたはフォルダーの復元|ファイルとフォルダーの復元ウィザードを実行して、特定のファイル、フォルダー、またはドライブを復元できます。|
|コンピューターのアラートの表示|重要なアラートやその他の情報アラートが表示されます。可能であれば、修正操作を実行できます。|
|コンピューターへのリモート デスクトップ|選択したコンピューターへのリモート デスクトップ接続を開きます。|
|コンピューターの削除|コンピューターの削除ウィザードを実行し、Windows Server Essentials ダッシュボードからコンピューターを接続解除します。|
|コンピューターのバックアップ設定とファイル履歴の設定のカスタマイズ|バックアップ設定ページが開き、クライアント コンピューターのバックアップ スケジュールとファイル履歴の設定を変更できます。|
|コンピューターをサーバーに接続する方法|コンピューターをネットワークに参加させるために実行する手順が説明されているヘルプ トピックが開きます。|
|グループ ポリシーの実装|ドメインに参加している Windows 8 および Windows 7 コンピューターにポリシー設定を適用します。|

##  <a name="assign-user-accounts-permission-to-log-on-to-specific-network-computers"></a><a name="BKMK_2"></a> 特定のネットワークコンピューターにログオンするためのアクセス許可をユーザーアカウントに割り当てる
 リモートの場所から Windows Server Essentials ネットワークにアクセスする場合、ユーザーが特定のネットワーク コンピューターのみにログオンできるように、ユーザー アカウントにアクセス許可を割り当てることができます。

#### <a name="to-change-the-computer-access-for-a-user-account"></a>ユーザー アカウントのコンピューター アクセスを変更するには

1.  Windows Server Essentials ダッシュボードを開きます。

2.  ナビゲーション バーで **[ユーザー]** をクリックします。

3.  ユーザー アカウント一覧で、変更するユーザー アカウントを選択します。

4.  [ ** ユーザーアカウント \> タスクの<** ] ウィンドウで、[ **アカウントのプロパティの表示**] をクリックします。 ユーザー アカウントの **[プロパティ]** ページが表示されます。

5.  **[コンピューター アクセス]** タブで、このユーザーがリモートでアクセスできるコンピューターを選択し、**[OK]** をクリックします。

##  <a name="remove-a-computer-from-the-server"></a><a name="BKMK_3"></a> サーバーからコンピューターを削除する
 ダッシュボードを使用して Windows Server Essentials を実行しているサーバーから削除されたコンピューターは、サーバーによって管理されなくなります。 その結果、サーバーは、ネットワークから削除されたコンピューターのバックアップの作成や状態の監視を停止します。

> [!NOTE]
>  サーバーからコンピューターを削除しても、そのコンピューターがネットワークから切断されることはありません。 コンピューターは引き続き、サーバーに接続される前と同じ方法でネットワーク上のリソースにアクセスできます。 コンピューターのサーバー リソースへのアクセスを禁止して、サーバーから切断するには、そのコンピューターをドメインから削除する必要があります。 さらに、サーバーからコンピューターを削除しても、コネクタ ソフトウェアまたはスタート パッドはそのコンピューターから自動的にアンインストールされません。 コンピューターからコネクタ ソフトウェアを手動で削除する必要があります。 詳細については、「 [Get Connected](../use/Get-Connected-in-Windows-Server-Essentials.md)」の「コネクタソフトウェアのアンインストール」を参照してください。

#### <a name="to-remove-a-computer-from-the-network-by-using-the-dashboard"></a>ダッシュボードを使用してネットワークからコンピューターを削除するには

1.  Windows Server Essentials ダッシュボードを開きます。

2.  ナビゲーション バーで、**[デバイス]** タブをクリックします。

3.  コンピューターの一覧で、ネットワークから削除するコンピューターを右クリックし、**[コンピューターの削除]** をクリックします。

##  <a name="configure-group-policy-settings-for-folder-redirection-and-security"></a><a name="BKMK_5"></a> フォルダーリダイレクトとセキュリティのグループポリシー設定を構成する
 Windows Server Essentials ダッシュボードを使用して、グループ ポリシーを構成し、Windows Server Essentials ネットワーク内のコンピューターにそのポリシーを展開できます。 Windows Server Essentials のグループ ポリシーには、Windows Update、Windows Defender、およびネットワーク ファイアウォールに影響を与えるフォルダー リダイレクトとセキュリティの設定が含まれます。

#### <a name="to-configure-group-policy-in-windows-server-essentials"></a>Windows Server Essentials のグループ ポリシーを構成するには

1.  Windows Server Essentials ダッシュボードを開きます。

2.  ナビゲーション バーで、**[デバイス]** をクリックします。

3.  Windows Server Essentials の場合: [グローバル **ユーザーのタスク** ] ウィンドウで、[ **グループポリシーの実装**] をクリックします。

     Windows Server Essentials の場合: [グローバル **デバイスタスク** ] ウィンドウで、[ **グループポリシーの実装**] をクリックします。

4.  グループ ポリシーの実装ウィザードが開きます。

5.  ウィザードの **[フォルダー リダイレクト グループ ポリシーを有効にする]** ページで、リダイレクトするユーザー フォルダーを選択できます。

6.  ウィザードの **[セキュリティ ポリシー設定を有効にする]** ページで、**[Windows Update]**、**[Windows Defender]**、および **[ネットワーク ファイアウォール]** のグループ ポリシー設定を有効にすることができます。

7.  **[完了]** をクリックして、グループ ポリシー設定を実装します。

##  <a name="connect-to-a-network-computer-by-using-a-remote-desktop-session"></a><a name="BKMK_7"></a> リモートデスクトップセッションを使用してネットワークコンピューターに接続する
 オフィスから離れた場所にいるときに Windows Server Essentials ネットワークコンピューターにリモートアクセスするには、Web ブラウザーを使用して組織のリモート Web アクセス web サイトにログオンし、[ **コンピューター** ] タブでコンピューターの名前をクリックします。

 **[状態]** 列に次の値が表示され、ネットワーク上のコンピューターに接続できるかどうかを示します。

-   **利用可能**

     コンピューターの電源が入っており、離れた場所から接続できる状態にあります。 この状態が表示されていても、サードパーティのファイアウォールが接続を拒む場合、このコンピューターには接続できません。

-   **オフラインまたはスリープ状態**

     コンピューターの電源が入っていないか、スリープまたは休止状態に入っています。 コンピューターがオフラインかスリープ状態の場合、コンピューターが利用可能状態になったことがわかるように、状態はリアルタイムで更新されます。

-   **サポートされないオペレーティング システム**

     コンピューターのオペレーティング システムは、リモート デスクトップをサポートしていません。 変更があった場合、この状態の更新に最大 6 時間かかることがあります。

-   **接続が無効です**

     コンピューターの接続がファイアウォールにより拒まれています。あるいは、リモート デスクトップがそのコンピューターで、またはグループ ポリシーにより無効になっています。 変更があった場合、この状態の更新に最大 6 時間かかることがあります。

##  <a name="view-computer-properties"></a><a name="BKMK_8"></a> コンピューターのプロパティの表示
 Windows Server Essentials ダッシュボードの **[デバイス]** セクションには、ネットワーク コンピューターの一覧が表示されます。 また、各コンピューターに関する追加情報も提供されます。

#### <a name="to-view-a-list-of-computers"></a>コンピューターの一覧を表示するには

1.  Windows Server Essentials ダッシュボードを開きます。

2.  メイン ナビゲーション バーで、**[デバイス]** をクリックします。

3.  ダッシュボードには、現在のコンピューターの一覧が表示されます。

#### <a name="to-view-or-change-properties-for-a-computer"></a>コンピューターのプロパティを表示または変更するには

1.  コンピューターの一覧で、プロパティを表示または変更するアカウントを選択します。

2.  [ **<Computername \> タスク** ] ウィンドウで、[ **コンピューターのプロパティの表示**] をクリックします。 コンピューターの **[プロパティ]** ページが表示されます。

3.  タブをクリックすると、そのコンピューターのプロパティが表示されます。

4.  コンピューターのプロパティに対して行った変更を保存するには、**[適用]** をクリックします。

## <a name="additional-references"></a>その他の参照情報

-   [リモート Web アクセスの管理](Manage-Remote-Web-Access-in-Windows-Server-Essentials.md)

-   [リモート Web アクセスの使用](../use/Use-Remote-Web-Access-in-Windows-Server-Essentials.md)

-   [ダッシュボードを使用したユーザー アカウントの管理](Manage-User-Accounts-in-Windows-Server-Essentials.md#BKMK_Manage8)

-   [Windows Server Essentials の管理](Manage-Windows-Server-Essentials.md)

-   [Windows Server Essentials の使用](../use/Use-Windows-Server-Essentials.md)
