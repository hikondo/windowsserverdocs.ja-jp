---
title: 拡張機能のインストールと管理
description: Windows Admin Center (Project Honolulu) での拡張機能のインストールと管理
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.localizationpriority: medium
ms.openlocfilehash: c2feaaff614d00afeaf5d132c446eebe5fdf0989
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87966779"
---
# <a name="install-and-manage-extensions"></a>拡張機能のインストールと管理

>適用先:Windows Admin Center、Windows Admin Center Preview

Windows Admin Center は拡張可能なプラットフォームとして構築されています。各接続の種類とツールは、個別にインストール、アンインストール、更新が可能な拡張機能です。 Microsoft や他の開発者から発行された新しい拡張機能を検索し、Windows Admin Center インストール全体を更新することなく、個別にインストールおよび更新できます。 また、個別の NuGet フィードまたはファイル共有を構成し、組織内で使用する拡張機能を配布することもできます。

## <a name="installing-an-extension"></a>拡張機能のインストール

Windows Admin Center には、指定された NuGet フィードから使用できる拡張機能が表示されます。 既定で、Windows Admin Center では、Microsoft や他の開発者から発行された拡張機能をホストする Microsoft の公式 NuGet フィードが示されます。

1. 右上の **[設定]** ボタンをクリックし、左ペインの **[拡張機能]** をクリックします。
2. **[使用可能な拡張機能]** タブには、インストールできる拡張機能がフィードに一覧表示されます。
3. 拡張機能をクリックすると、 **[詳細]** ペインに拡張機能の説明、バージョン、発行元、およびその他の情報が表示されます。
4. **[インストール]** をクリックして拡張機能をインストールします。 この変更を行うために、ゲートウェイを特権モードで実行する必要がある場合は、UAC の昇格プロンプトが表示されます。 インストールが完了すると、ブラウザーが自動的に更新され、Windows Admin Center に新しい拡張機能がインストールされ、再度読み込まれます。 インストール対象の拡張機能が以前にインストールされた拡張機能の更新プログラムである場合、 **[Update to latest]\(最新版への更新\)** ボタンをクリックして更新プログラムをインストールできます。 また、 **[インストール済みの拡張機能]** タブにアクセスしてインストールされている拡張機能を表示し、 **[状態]** 列で更新プログラムがあるかどうかを確認することもできます。

## <a name="installing-extensions-from-a-different-feed"></a>別のフィードからの拡張機能のインストール

Windows Admin Center は複数のフィードをサポートしており、一度に複数のフィードからパッケージを表示および管理できます。 NuGet V2 API またはファイル共有をサポートする NuGet フィードを Windows Admin Center に追加して、拡張機能をインストールできます。

1. 右上の **[設定]** ボタンをクリックし、左ペインの **[拡張機能]** をクリックします。
2. 右側のペインで **[フィード]** タブをクリックします。
3. 別のフィードを追加するには **[追加]** ボタンをクリックします。 NuGet フィードの場合は、NuGet V2 フィードの URL を入力します。 NuGet フィード プロバイダーまたは管理者は、URL 情報を指定できる必要があります。 ファイル共有の場合は、拡張機能パッケージ ファイル (.nupkg) が格納されているファイル共有の完全パスを入力します。
4. **[追加]** をクリックします。 この変更を行うために、ゲートウェイを特権モードで実行する必要がある場合は、UAC の昇格プロンプトが表示されます。 このプロンプトは、デスクトップ モードで Windows Admin Center を実行している場合にのみ表示されます。

**[使用可能な拡張機能]** 一覧には、すべての登録済みフィードの拡張機能が表示されます。 **[Package Feed]\(パッケージ フィード\)** 列を使用して、各拡張機能のフィード元を確認できます。

## <a name="uninstalling-an-extension"></a>拡張機能のアンインストール

以前にインストールした拡張機能をアンインストールできます。また、Windows Admin Center のインストールの一部として事前にインストールされていたツールをアンインストールすることもできます。

1. 右上の **[設定]** ボタンをクリックし、左ペインの **[拡張機能]** をクリックします。
2. インストールされているすべての拡張機能を表示するには **[インストール済みの拡張機能]** タブをクリックします。
3. アンインストールする拡張機能を選択し、 **[アンインストール]** をクリックします。

アンインストールが完了すると、ブラウザーは自動的に更新され、拡張機能が削除された状態で Windows Admin Center が再度読み込まれます。 Windows Admin Center の一部としてプレインストールされたツールをアンインストールした場合、 **[使用可能な拡張機能]** タブでそのツールを再インストールできます。

## <a name="installing-extensions-on-a-computer-without-internet-connectivity"></a>インターネットに接続されていないコンピューターへの拡張機能のインストール

インターネットに接続されていないコンピューターまたはプロキシの背後にあるコンピューターに Windows Admin Center がインストールされている場合、Windows Admin Center フィードから拡張機能にアクセスおよびインストールできない場合があります。 拡張機能パッケージを手動でまたは PowerShell スクリプトを使用してダウンロードし、ファイル共有またはローカル ドライブからパッケージを取得するように Windows Admin Center を構成できます。

### <a name="manually-downloading-extension-packages"></a>拡張機能パッケージを手動でダウンロードする

1. インターネットに接続できる別のコンピューターで Web ブラウザーを開き、[https://dev.azure.com/WindowsAdminCenter/Windows%20Admin%20Center%20Feed/_packaging?_a=feed&feed=WAC](https://dev.azure.com/WindowsAdminCenter/Windows%20Admin%20Center%20Feed/_packaging?_a=feed&feed=WAC) の URL に移動します。

   * 拡張機能パッケージを表示するには、Microsoft アカウントを作成してログインすることが必要な場合もあります。

2. インストールするパッケージの名前をクリックすると、パッケージの詳細ページが表示されます。
3. パッケージの詳細ページの上部ナビゲーション バーにある **[ダウンロード]** リンクをクリックし、拡張機能の .nupkg ファイルをダウンロードします。
4. ダウンロードするすべてのパッケージについて、手順 2 と 3 を繰り返します。
5. Windows Admin Center がインストールされているコンピューターからアクセスできる共有ファイル、またはコンピューターのローカル ディスクにパッケージ ファイルをコピーします。
6. [指示に従って別のフィードから拡張機能をインストールします](#installing-extensions-from-a-different-feed)。

### <a name="downloading-packages-with-a-powershell-script"></a>PowerShell スクリプトを使用したパッケージのダウンロード

NuGet フィードから NuGet パッケージをダウンロードするためにインターネット上で利用できるスクリプトは多数あります。 ここでは、Microsoft のシニア プログラム マネージャーである [Jon Galloway が提供しているスクリプト](https://weblogs.asp.net/jongalloway/downloading-a-local-nuget-repository-with-powershell)を使用します。

1. [ブログ投稿](https://weblogs.asp.net/jongalloway/downloading-a-local-nuget-repository-with-powershell)で説明されているように、このスクリプトを NuGet パッケージとしてインストールするか、スクリプトをコピーして PowerShell ISE に貼り付けます。
2. スクリプトの最初の行を NuGet フィードの v2 URL に変更します。 Windows Admin Center の公式フィードからパッケージをダウンロードする場合は、以下の URL を使用します。

```powershell
$feedUrlBase = "https://aka.ms/sme-extension-feed"
```

3. スクリプトを実行すると、フィードからローカル フォルダー %USERPROFILE%\Documents\NuGetLocal にすべての NuGet パッケージがダウンロードされます。
4. [指示に従って別のフィードから拡張機能をインストールします](#installing-extensions-from-a-different-feed)。

## <a name="manage-extensions-with-powershell"></a>PowerShell を使用して拡張機能を管理する

Windows Admin Center プレビューには、ゲートウェイ拡張機能を管理する PowerShell モジュールが含まれています。

[!INCLUDE [ps-extensions](../includes/ps-extensions.md)]

### <a name="learn-more-about-building-an-extension-with-the-windows-admin-center-sdk"></a>[Windows Admin Center SDK を使用した拡張機能の構築の詳細については、こちらを参照してください](../extend/extensibility-overview.md)。
