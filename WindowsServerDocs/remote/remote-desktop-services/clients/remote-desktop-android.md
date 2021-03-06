---
title: Android クライアントの概要
description: Android クライアントに関する一般的な情報。
ms.topic: article
ms.assetid: 64f038e1-40ec-4c67-938b-72edea49e5d8
author: heidilohr
manager: lizross
ms.author: helohr
ms.date: 09/17/2020
ms.localizationpriority: medium
ms.openlocfilehash: 1f59c00e375ab142c4e3dadc480c648cdd8e2396
ms.sourcegitcommit: 877d6db73d9520e3a23738d6528016235493cff3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2020
ms.locfileid: "90779246"
---
# <a name="get-started-with-the-android-client"></a>Android クライアントの概要

>適用先:Android 4.1 以降

Android 用リモート デスクトップ クライアントを使用して、Google Play ストアをサポートする Android デバイスまたは Chromebook から直接 Windows のアプリおよびデスクトップを使用することができます。

この記事では、クライアントの使用を開始する方法について説明します。 その他の質問がある場合は、[FAQ](remote-desktop-client-faq.md) を確認してください。

> [!NOTE]
> - Android クライアントの新しいリリースについて興味がありますか。 「[Android クライアントの新機能](android-whatsnew.md)」を確認してください。
> - Android クライアントでは、Android 4.1 以降が実行されているデバイスおよび ChromeOS 53 以降が搭載された Chromebook が、サポートされています。 Chrome の Android アプリケーションの詳細については、「[Android アプリをサポートする Chrome OS システム](https://sites.google.com/a/chromium.org/dev/chromium-os/chrome-os-systems-supporting-android-apps)」を参照してください。

## <a name="download-the-remote-desktop-client"></a>リモート デスクトップ クライアントをダウンロードする

Android デバイスでリモート デスクトップ クライアントを設定する方法を次に示します。

1. Google Play から Microsoft [リモート デスクトップ クライアントをダウンロード](https://play.google.com/store/apps/details?id=com.microsoft.rdc.androidx)します。
2. アプリの一覧から **RD クライアント**を起動します。
3. [リモート デスクトップ接続](#add-a-remote-desktop-connection)または[リモート リソース](#add-remote-resources)を追加します。 リモート デスクトップ接続を使用すると、Windows PC およびリモート リソースに直接接続して、管理者によって公開されたアプリやデスクトップにアクセスすることができます。

## <a name="add-a-remote-desktop-connection"></a>リモート デスクトップ接続を追加する

これで、デバイスにクライアントがインストールされたので、リモート デスクトップ接続を追加してリモート リソースにアクセスできます。

まだ行っていない場合は、接続を追加する前に、[リモート接続を受け入れるように PC を設定](remote-desktop-allow-access.md)します。

リモート デスクトップ接続を追加するには:

1. 接続センターで、 **[+]** をタップしてから、 **[Desktop]\(デスクトップ\)** をタップします。
2. **[PC name]\(PC 名\)** にリモート PC の名前を入力します。 この名前には、Windows コンピューター名、インターネット ドメイン名、または IP アドレスを指定できます。 PC 名にポート情報を追加することもできます (例: MyDesktop:3389、10.0.0.1:3389)。 必須フィールドはこのフィールドのみです。
3. リモート PC へのアクセスに使用する **[User name]\(ユーザー名\)** を選択します。

   - リモート PC に接続するたびにクライアントで資格情報が要求されるようにするには、 **[毎回入力する]** を選択します。
   - 頻繁に使用するアカウントを保存するには、 **[Add user account]\(ユーザー アカウントの追加\)** を選択します。これにより、サインインするたびに資格情報を入力する必要がなくなります。 ユーザー アカウントの詳細については、「[ユーザー アカウントの管理 ](#manage-your-user-accounts)」を参照してください。

4. **[Show additional options]\(追加オプションの表示\)** をタップして、次のオプション パラメーターを設定することもできます。

   - **[Friendly name]\(フレンドリ名\)** には、接続する PC の覚えやすい名前を入力できます。 フレンドリ名を指定しないと、PC の名前が代わりに表示されます。
   - **[Gateway]** \(ゲートウェイ\) は、外部ネットワークからコンピューターに接続するために使用するリモート デスクトップ ゲートウェイです。 詳細については、システム管理者に問い合わせてください。
   - **[Sound]** \(サウンド\) では、リモート セッションでオーディオに使用するデバイスを選択します。 ローカル デバイスまたはリモート デバイスでサウンドを再生するか、またはまったく再生しないことを選択できます。
   - **[Customize display resolution]\(ディスプレイの解像度をカスタマイズする\)** では、リモート セッションの解像度を設定します。 オフにすると、グローバル設定で指定されている解像度が使用されます。
   - **[マウス ボタンの入れ替え]** では、右と左のマウス ジェスチャで送信されるコマンドを入れ替えます。 左ききのユーザーに最適です。
   - **[管理者セッションに接続]** では、リモート PC の管理者セッションに接続できます。
   - **[Redirect local storage]\(ローカル ストレージのリダイレクト\)** では、ローカル ストレージのリダイレクトを有効にします。 この設定は既定では無効になっています。

5. 完了したら、 **[保存]** をタップします。

これらの設定を編集する必要がありますか。 デスクトップの名前の横にある **[その他のオプション]** メニュー ( **[...]** ) タップし、 **[編集]** をタップします。

接続を削除しますか。 ここでも **[その他のオプション]** メニュー ( **[...]** ) をタップし、 **[削除]** をタップします。

>[!TIP]
> "We couldn't connect to the remote PC because the password associated with the user account has expired" (ユーザー アカウントに関連付けられたパスワードの有効期限が切れたので、リモート PC に接続できませんでした) のようなエラー名 "0xf07" が表示された場合は、新しいパスワードを使用してもう一度やり直してください。

## <a name="add-remote-resources"></a>リモート リソースを追加する

リモート リソースとは、管理者が公開した RemoteApp プログラム、セッション ベースのデスクトップ、および仮想デスクトップです。Android クライアントでは、**リモート デスクトップ サービス**および **Windows 仮想デスクトップ**の展開から公開されたリソースがサポートされています。

リモート リソースを追加します。

1. 接続センターで **[+]** をタップした後、 **[Remote Resource Feed]\(リモート リソースのフィード\)** をタップします。
2. **[Feed URL]** \(フィード URL\) を入力します。 この URL には、URL またはメール アドレスを指定できます。
   - **[URL]** は、管理者によって提供されている RD Web アクセス サーバーです。Windows Virtual Desktop からリソースにアクセスする場合は、使用しているバージョンに応じて次の URL のいずれかを使用できます。
     - Windows Virtual Desktop (クラシック) を使用している場合は、`https://rdweb.wvd.microsoft.com/api/feeddiscovery/webfeeddiscovery.aspx` を使用します。
     - Windows Virtual Desktop を使用している場合は、`https://rdweb.wvd.microsoft.com/api/arm/feeddiscovery` を使用します。
   - **[Email]** \(電子メール\) を使用する予定の場合は、このフィールドにメール アドレスを入力してください。 このフィールドに入力すると、管理者によって構成されている場合、メール アドレスに関連付けられている RD Web アクセス サーバーを検索するようにクライアントが指示されます。
3. **[Next]** \(次へ\) をタップします。
4. 入力を求められたら、サインイン情報を入力します。 使用する資格情報は、展開によって異なる場合があり、次のものを含めることができます。
   - リソースへのアクセス許可を持っている **[ユーザー名]** 。
   - ユーザー名に関連付けられている **[パスワード]** 。
   - **[Additional factor]\(追加要素\)** 。管理者によってその認証方法が構成されている場合、要求されることがあります。
5. 完了したら、 **[保存]** をタップします。

リモート リソースが、接続センターで表示されます。

## <a name="remove-remote-resources"></a>リモート リソースを削除する

リモート リソースを削除するには:

1. 接続センターで、オーバーフロー メニューをタップ ( **...** )、リモート リソースの横にあります。
2. タップ **削除**します。
3. リソースが削除されたことを確認します。

## <a name="pin-a-connection-to-your-home-screen"></a>ホーム画面に接続をピン留めする

リモート デスクトップ クライアントでは、Android のウィジェットの機能を使用した、ホーム画面への接続のピン留めがサポートされています。 ウィジェットの追加プロセスは、使用している Android デバイスの種類と Android OS のバージョンによって異なります。

ウィジェットを追加するには:

1. **[Apps]\(アプリ\)** をタップして、アプリ メニューを起動します。
2. **[Widgets]\(ウィジェット\)** をタップします。
3. ウィジェットをスワイプし、次の説明が表示されるリモート デスクトップ アイコンを探します。"Pin Remote Desktop" (リモート デスクトップをピン留めする)。
4. そのリモート デスクトップ ウィジェット キーを押しながら、ホーム画面に移動します。
5. アイコンを離すと、保存されているリモート デスクトップが表示されます。 ホーム画面を保存する接続を選択します。

これで、ホーム画面から直接タップすることにより、リモート デスクトップ接続を開始できます。

> [!NOTE]
> リモート デスクトップ クライアントでデスクトップ接続の名前を変更した場合、ピン留めされたラベルは更新されません。

## <a name="manage-general-app-settings"></a>アプリの全般設定を管理する

アプリの全般設定を変更するには、接続センターにアクセスし、 **[Settings]\(設定\)** をタップしてから、 **[General]\(全般\)** をタップします。

次の全般設定を設定できます。

- **[Show desktop previews]\(デスクトップ プレビューを表示する\)** では、接続する前に、接続センターでデスクトップのプレビューを表示できます。 既定では、この設定は有効になっています。
- **[Pinch to zoom remote session]\(ピンチでリモート セッションをズームする\)** では、ピンチ操作によるズーム ジェスチャを使用することができます。 リモート デスクトップから使用しているアプリでマルチタッチ (Windows 8 で導入) がサポートされている場合は、この機能を無効にします。
- スキャンコードとして送信されたキーボード入力にリモート アプリが正しく応答しない場合は、 **[Use scancode input when available]\(使用可能な場合はスキャンコード入力を使用する\)** を有効にします。 無効にすると、入力は Unicode として送信されます。
- **[リモート デスクトップの改善にご協力ください]** を選択すると、Android 用リモート デスクトップの使用方法に関する匿名データが Microsoft に送信されます。 このデータを使用してクライアントを改善します。 プライバシー ポリシーと収集するデータの種類の詳細については、[Microsoft のプライバシーに関する声明](https://privacy.microsoft.com/privacystatement)を参照してください。 既定では、この設定は有効になっています。

## <a name="manage-display-settings"></a>ディスプレイの設定を管理する

ディスプレイの設定を変更するには、接続センターで **[Settings]\(設定\)** をタップしてから、 **[Display]\(ディスプレイ\)** をタップします。

次のディスプレイ設定を設定できます。

- **[Orientation]\(方向\)** では、セッションの優先する方向 (横または縦) を設定します。

  >[!NOTE]
  > Windows 8 以前を実行している PC に接続した場合、デバイスの向きが変更されてもセッションが適切にスケールされません。 クライアントを適切にスケールするには、PC から切断し、使用する方向で再接続します。 また、Windows 10 を使用している PC を使用して、適切にスケールすることもできます。

- **[Resolution]\(解像度\)** では、デスクトップ接続でグローバルに使用する解像度を設定します。 個々の接続に対してカスタム解像度を既に設定している場合は、この設定ではそれは変更されません。

  >[!NOTE]
  >表示設定を変更した場合、設定を変更した後に作成した新しい接続にのみ変更が適用されます。 現在接続しているセッションに変更を適用するには、切断し、再接続することでセッションを更新します。

## <a name="manage-your-rd-gateways"></a>RD ゲートウェイを管理する

リモート デスクトップ ゲートウェイ (RD ゲートウェイ) を使用すると、インターネットのどこからでもプライベート ネットワーク上のリモート コンピューターに接続できます。 作成および、リモート デスクトップ クライアントを使用して、ゲートウェイを管理できます。

新しい RD ゲートウェイを設定するには:

1. 接続センターで、 **[Settings]\(設定\)** をタップしてから、 **[Gateways]\(ゲートウェイ\)** をタップします。
2. タップ **+** を新しいゲートウェイを追加します。
3. 次の情報を入力します。
   - ゲートウェイとして使用するコンピューターの名前を **[Server name]\(サーバー名\)** に入力します。 この名前には、Windows コンピューター名、インターネット ドメイン名、または IP アドレスを指定できます。 サーバー名に、ポート情報を追加することもできます (例:RDGateway:443、10.0.0.1:443)。
   - RD ゲートウェイへのアクセスに使用する **[User account]\(ユーザー アカウント\)** を選択します。
     - リモート PC に指定したものと同じ資格情報を使用する場合は、 **[Use desktop user account]\(デスクトップ ユーザー アカウントを使用する\)** を選択します。
     - 頻繁に使用するアカウントを保存するには、 **[Add user account]\(ユーザー アカウントの追加\)** を選択します。これにより、サインインするたびに資格情報を入力する必要がなくなります。 詳細については、「[ユーザー アカウントを管理する](#manage-your-user-accounts)」を参照してください。

RD ゲートウェイを削除するには:

1. 接続センターで、 **[Settings]\(設定\)** をタップしてから、 **[Gateways]\(ゲートウェイ\)** をタップします。
2. タップして、それを選択するには、一覧内のゲートウェイを保持します。 複数のゲートウェイを一度に選択することができます。
3. ごみ箱に選択したゲートウェイを削除する をタップします。

## <a name="manage-your-user-accounts"></a>ユーザー アカウントを管理する

リモート デスクトップまたはリモート リソースに接続するたびに使用するユーザー アカウントを保存できます。

ユーザー アカウントを保存するには:

1. タップして、接続センターで **設定**, 、順にタップ **ユーザー アカウント**します。
2. タップ **+** 新しいユーザー アカウントを追加します。
3. 次の情報を入力します。
   - リモート接続で使用するために保存する **[User Name]\(ユーザー名\)** 。 ユーザー名は、user_name、domain\user_name、user_name@domain.com のいずれかの形式で入力できます。
   - 指定したユーザーの **[Password]\(パスワード\)** 。 リモート接続に使用する保存するすべてのユーザー アカウントは、関連付けられているパスワードが必要です。
4. 完了したら、 **[保存]** をタップします。

保存したユーザー アカウントを削除するには:

1. タップして、接続センターで **設定**, 、順にタップ **ユーザー アカウント**します。
2. タップして、それを選択するには、一覧内のユーザー アカウントを保持します。 複数のユーザーを同時に選択することができます。
3. ごみ箱に、選択したユーザーを削除する をタップします。

## <a name="start-a-remote-desktop-connection"></a>リモート デスクトップ接続を開始する

これで、Android 用のリモート デスクトップ クライアントがセットアップされたので、リモート デスクトップ セッションを開始する方法について説明します。

セッションを開始するには:

1. **リモート デスクトップ接続の名前**をタップしてセッションを開始します。
2. リモート デスクトップ用の証明書の確認を求められた場合は、 **[Connect]\(接続\)** をタップします。 **[このコンピューターへの接続について今後確認しない]** を選択して、既定で常に証明書を受け入れることもできます。

## <a name="use-the-connection-bar"></a>接続バーを使用する

接続バーは、追加のナビゲーション コントロールへのアクセスを提供します。 既定では、接続バーは、画面の上部中央に配置されます。 バーを移動するには、左または右にドラッグします。

- **パン コントロール**:パン コントロールを使用すると、画面を拡大し、移動させることができます。 パン コントロールは、直接タッチにのみ使用できます。
  - パン コントロールを表示するには、接続バーのパン アイコンをタップしてパン コントロールを表示し、画面をズームします。 コントロールを非表示にして画面を元のサイズに戻すには、パン アイコンをもう一度タップします。
  - パン コントロールを使用するには、長押ししてから、目的の方向にドラッグして画面を動かします。
  - パン コントロールを移動するには、ダブルタップから長押しし、画面上でコントロールを移動します。
- **追加オプション**:追加オプション アイコンをタップすると、セッション選択バーおよびコマンド バーが表示されます。
- **キーボード**:キーボード アイコンをタップして、キーボードを表示したり非表示にします。 キーボードが表示されたら、パン コントロールが自動的に表示されます。

## <a name="use-the-session-selection-bar"></a>セッションの選択バーを使用する

複数の接続を同時に別の Pc を開くことができます。 画面の左側にあるセッションの選択バーを表示する接続バーをタップします。 セッション選択バーを使用すると、開いている接続を表示し、切り替えることができます。

リモート リソースに接続しているときは、展開メニュー ( **[>]** ) をタップし、使用可能な項目の一覧から選択することにより、そのセッション内でアプリを切り替えることができます。

現在の接続内で新しいセッションを開始するには、 **[Start New]\(新しく開始\)** をタップした後、利用可能な項目の一覧から選択します。

セッションを切断するには、セッション タイルの左側にある **[X]** をタップします。

## <a name="use-the-command-bar"></a>コマンド バーを使用する

接続バーをタップして、画面の右側にコマンドバーを表示します。 コマンド バーでは、マウス モード (直接タッチとマウス ポインター) を切り替えたり、[ホーム] ボタンをタップして接続センターに戻ったりすることができます。 [戻る] ボタンをタップして、接続センターに戻ることもできます。 接続センターに戻っても、アクティブなセッションが切断されることはありません。

## <a name="touch-gestures-and-mouse-modes"></a>タッチ ジェスチャとマウス モード

Android 用のリモート デスクトップ クライアントでは、標準的なタッチ ジェスチャが使用されます。 リモート デスクトップ上でマウス アクションをレプリケートするのにタッチ ジェスチャを使用することもできます。 次の表では、各マウス モードでどのジェスチャがどのマウス操作と一致するかを説明します。

> [!NOTE]
> ネイティブのタッチ ジェスチャは、Windows 8 以降の直接タッチ モードでサポートされています。

| [マウス モード]    | マウス操作         | ジェスチャ                                                                 |
|---------------|----------------------|-------------------------------------------------------------------------|
| 直接タッチ  | 左クリック           | 1 本の指でタップする                                                     |
| 直接タッチ  | 右ボタンのクリック          | 1 本の指で長押ししてから離す                              |
| マウス ポインター | ズーム                 | 2 本の指を使って、ピンチで縮小または指を開いて拡大する。 |
| マウス ポインター | 左クリック           | 1 本の指でタップする                                                     |
| マウス ポインター | 左クリックしてドラッグ  | 1 本の指でダブルタップから長押しして、ドラッグする                          |
| マウス ポインター | 右ボタンのクリック          | 2 本の指でタップする                                                    |
| マウス ポインター | 右クリックしてドラッグ | 2 本の指でダブルタップから長押しして、ドラッグする                         |
| マウス ポインター | マウス ホイール          | 2 本の指で長押しして、上または下にドラッグする                     |

## <a name="join-the-beta-channel"></a>Beta チャネルに参加する

リリース前に新しいビルドをテストしたり、今後のバージョンの更新で問題を見つけたりするには、ベータ チャネルに参加してください。 エンタープライズ管理者は、ベータ チャネルを使用して、ユーザーの新しいバージョンの Android クライアントを検証することができます。

ベータに参加するには、[ベータ クライアントをダウンロード](https://play.google.com/apps/testing/com.microsoft.rdc.androidx)し、プレビュー バージョンへのアクセスとクライアントのダウンロードに同意します。 Google Play ストアを通じて、プレビュー バージョンを直接受け取ることができます。
