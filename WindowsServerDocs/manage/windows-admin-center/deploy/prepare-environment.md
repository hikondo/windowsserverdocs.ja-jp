---
title: Windows Admin Center のための環境の準備
description: Windows Admin Center (Project Honolulu) のための環境の準備
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 06/07/2019
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 72e71ce2d1427f392aa02d32597f92d031f9a5c9
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407009"
---
# <a name="prepare-your-environment-for-windows-admin-center"></a>Windows Admin Center のための環境の準備

> 適用対象:Windows Admin Center、Windows Admin Center Preview

Windows Admin Center で管理する準備が完了する前に、追加の準備が必要ないくつかの Server バージョンがあります。

- [Windows Server 2012 および 2012 R2](#prepare-windows-server-2012-and-2012-r2)
- [Windows Server 2008 R2](#prepare-windows-server-2008-r2)
- [Microsoft Hyper-V Server 2016](#prepare-microsoft-hyper-v-server-2016)
- [Microsoft Hyper-V Server 2012 R2](#prepare-microsoft-hyper-v-server-2012-r2)

また、Windows 管理センターで管理する前に[、ターゲットサーバーのポート構成](#port-configuration-on-the-target-server)を変更しなければならない場合もあります。

## <a name="prepare-windows-server-2012-and-2012-r2"></a>Prepare Windows Server 2012 および 2012 R2

### <a name="install-wmf-version-51-or-higher"></a>WMF バージョン 5.1 以上のインストール

Windows Admin Center には、既定で Windows Server 2012 および 2012 R2 に含まれていない PowerShell 機能が必要です。 Windows Admin Center で Windows Server 2012 または 2012 R2 を管理するには、それらのサーバーに WMF バージョン 5.1 以上をインストールする必要があります。

PowerShell で `$PSVersiontable` を入力して、WMF がインストールされていること、またバージョンが 5.1 以上であることを確認します。

インストールされていない場合は、[WMF 5.1 をダウンロードしてインストール](https://docs.microsoft.com/powershell/wmf/setup/install-configure)できます。

## <a name="prepare-windows-server-2008-r2"></a>Windows Server 2008 R2 の準備

### <a name="install-wmf-version-51-or-higher"></a>WMF バージョン 5.1 以上のインストール

Windows Admin Center では、既定で Windows Server 2008 R2 に含まれていない PowerShell 機能が必要です。 Windows Admin Center で Windows Server 2008 R22 を管理するには、それらのサーバーに WMF バージョン 5.1 以上をインストールする必要があります。 

[.NET Framework 4.5.2](https://docs.microsoft.com/dotnet/framework/install/on-windows-7)以降が既にコンピューターにインストールされていることを確認してください。

PowerShell で `$PSVersiontable` を入力して、WMF がインストールされていること、またバージョンが 5.1 以上であることを確認します。

インストールされていない場合は、[WMF 5.1 をダウンロードしてインストール](https://docs.microsoft.com/powershell/wmf/setup/install-configure)できます。

PowerShell コンソールで `Enable-PSRemoting –force` を実行して Powershell リモート接続を有効にします。 

### <a name="enable-remote-desktop"></a>リモート デスクトップの有効化

Windows Admin Center 内でリモート デスクトップを使用するには、Windows Server 2008 R2 サーバーでリモート デスクトップを有効にする必要があります。

**サーバー マネージャー**で、 **[リモート デスクトップの構成]** に移動します。 リモート デスクトップを有効にし、リモート デスクトップを実行しているコンピューターからの接続を許可します。

## <a name="prepare-microsoft-hyper-v-server-2016"></a>Microsoft Hyper-V Server 2016 の準備

Windows Admin Center で Microsoft Hyper-V Server 2016 を管理するには、事前に有効にする必要のあるサーバーの役割がいくつかあります。

### <a name="to-manage-microsoft-hyper-v-server-2016-with-windows-admin-center"></a>Windows Admin Center で Microsoft Hyper-V Server 2016 を管理するには:

1. リモート管理を有効にします。
2. ファイル サーバーの役割を有効にします。
3. PowerShell 用 Hyper-V モジュールを有効にします。

### <a name="step-1-enable-remote-management"></a>**手順 1:** リモート管理の有効化

Hyper-V Server でリモート管理を有効にするには:

1. Hyper-V Server にログインします。
2. **サーバー構成** (SCONFIG) ツールで、**4** を入力してリモート管理を構成します。
3. **1** を入力してリモート管理を有効にします。
4. **4** を入力してメイン メニューに戻ります。

### <a name="step-2-enable-file-server-role"></a>**手順 2:** ファイル サーバーの役割の有効化

基本的なファイル共有とリモート管理のためにファイル サーバー ロールを有効にするには:

1. **[ツール]** メニューで **[役割と機能]** をクリックします。
2. **[役割と機能]** で、 **[ファイルおよび記憶域サービス]** を見つけて、 **[ファイルおよび iSCSI サービス]** と **[ファイル サーバー]** をオンにします。

![ファイルと iSCSI サービスの役割が選択されている役割と機能のスクリーンショット](../media/prepare-environment/c6c30b812d96afcc1edcdb6f52f0e13c.png)

### <a name="step-3-enable-hyper-v-module-for-powershell"></a>**手順 3:** PowerShell の Hyper-V モジュールの有効化

PowerShell 機能の Hyper-V モジュールを有効にするには:

1. **[ツール]** メニューで **[役割と機能]** をクリックします。
2. **[役割と機能]** で、 **[リモート サーバー管理ツール]** を見つけて **[役割管理ツール]** と **[PowerShell 用 Hyper-V モジュール]** をオンにします。

![選択された Hyper-v の役割を示す役割と機能のスクリーンショット](../media/prepare-environment/7ab0999602b7083733525bd0c1ba2747.png)

これで、Microsoft Hyper-V Server 2016 は、Windows Admin Center で管理するための準備が整いました。

## <a name="prepare-microsoft-hyper-v-server-2012-r2"></a>Microsoft Hyper-V Server 2012 R2 の準備

Windows Admin Center で Microsoft Hyper-V Server 2012 R2 を管理するには、事前に有効にする必要があるサーバーの役割がいくつかあります。  また、WMF バージョン 5.1 以上をインストールする必要があります。

### <a name="to-manage-microsoft-hyper-v-server-2012-r2-with-windows-admin-center"></a>Windows Admin Center で Microsoft Hyper-V Server 2012 R2 を管理するには:

1. Windows Management Framework (WMF) バージョン 5.1 以上のインストール
2. リモート管理の有効化
3. ファイル サーバーの役割の有効化
4. PowerShell の Hyper-V モジュールの有効化

### <a name="step-1-install-windows-management-framework-51"></a>手順 1:Windows Management Framework 5.1 をインストールします。

Windows Admin Center では、既定で Microsoft Hyper-V Server 2012 R2 に含まれていない PowerShell 機能が必要です。 Windows Admin Center で Microsoft Hyper-V Server 2012 R2 を管理するには、WMF バージョン 5.1 以上をインストールする必要があります。

PowerShell で `$PSVersiontable` を入力して、WMF がインストールされていること、またバージョンが 5.1 以上であることを確認します。 

インストールされていない場合は、[WMF 5.1 をダウンロード](https://docs.microsoft.com/powershell/wmf/setup/install-configure)することができます。

### <a name="step-2-enable-remote-management"></a>手順 2:リモート管理の有効化

Hyper-V Server のリモート管理を有効にするには:

1. Hyper-V Server にログインします。
2. **サーバー構成** (SCONFIG) ツールで、**4** を入力してリモート管理を構成します。
3. **1** を入力してリモート管理を有効にします。
4. **4** を入力してメイン メニューに戻ります。

### <a name="step-3-enable-file-server-role"></a>手順 3:ファイル サーバーの役割の有効化

基本的なファイル共有とリモート管理のためにファイル サーバー ロールを有効にするには:

1. **[ツール]** メニューで **[役割と機能]** をクリックします。
2. **[役割と機能]** で、 **[ファイルおよび記憶域サービス]** を見つけて、 **[ファイルおよび iSCSI サービス]** と **[ファイル サーバー]** をオンにします。

![ファイルと iSCSI サービスの役割が選択されている役割と機能のスクリーンショット](../media/prepare-environment/c6c30b812d96afcc1edcdb6f52f0e13c.png)

### <a name="step-4-enable-hyper-v-module-for-powershell"></a>手順 4:PowerShell の Hyper-V モジュールの有効化

PowerShell 機能の Hyper-V モジュールを有効にするには:

1. **[ツール]** メニューで **[役割と機能]** をクリックします。
2. **[役割と機能]** で、 **[リモート サーバー管理ツール]** を見つけて **[役割管理ツール]** と **[PowerShell 用 Hyper-V モジュール]** をオンにします。

![Hyper-v リモートサーバー管理ツールが選択されている役割と機能のスクリーンショット](../media/prepare-environment/7ab0999602b7083733525bd0c1ba2747.png)

これで、Microsoft Hyper-V Server 2012 R2 は、Windows Admin Center で管理するための準備が整いました。

## <a name="port-configuration-on-the-target-server"></a>ターゲットサーバーのポート構成

Windows 管理センターでは、リモートサーバーに証明書をインポートする場合など、一部のファイルコピータスクに SMB ファイル共有プロトコルを使用します。 これらのファイルコピー操作を成功させるには、リモートサーバーのファイアウォールでポート445での受信接続を許可する必要があります。  Windows 管理センターのファイアウォールツールを使用して、[ファイルサーバーのリモート管理 (SMB 受信)] がこのポートでのアクセスを許可するように設定されていることを確認できます。

> [!Tip]
> Windows Admin Center をインストールする準備はできましたか。 [今すぐダウンロード](https://docs.microsoft.com/windows-server/manage/windows-admin-center/understand/windows-admin-center#download-now)
