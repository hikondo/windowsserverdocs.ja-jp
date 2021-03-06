---
title: Windows Server 上の Hyper-v でサポートされている Windows ゲストオペレーティングシステム
description: 仮想マシンでゲストとして使用できるようにサポートされている Windows オペレーティングシステムの一覧を示します。 また、以前のバージョンの Hyper-v に関する同様の記事へのリンクも示します。
ms.topic: article
ms.assetid: 06b35897-2192-48b7-8c2d-125c520b0786
ms.author: benarm
author: BenjaminArmstrong
ms.date: 01/08/2019
ms.openlocfilehash: 2e5cf6c94d0127a283c640a48aaa2fced5472e9d
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746727"
---
# <a name="supported-windows-guest-operating-systems-for-hyper-v-on-windows-server"></a>Windows Server 上の Hyper-v でサポートされている Windows ゲストオペレーティングシステム

>適用先:Windows Server 2019、Windows Server 2016

Hyper-v では、ゲストオペレーティングシステムとして仮想マシンで実行するために、Windows Server、Windows、および Linux のディストリビューションの複数のバージョンをサポートしています。 この記事では、サポートされている Windows Server と Windows ゲスト オペレーティング システムについて説明します。 Linux および FreeBSD のディストリビューションでは、次を参照してください。 [Windows にインストールされた Hyper-v の仮想マシンをサポートされている Linux および FreeBSD](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md)します。

一部のオペレーティング システムでは、組み込みの統合サービスがあります。 他のユーザーは、インストールか、仮想マシンのオペレーティング システムを設定した後に、別のステップとして integration services をアップグレードすることが必要です。 詳細については、以下のセクションを参照してくださいと  [Integration Services](/virtualization/hyper-v-on-windows/reference/integration-services)します。

## <a name="supported-windows-server-guest-operating-systems"></a>サポートされている Windows Server のゲスト オペレーティング システム

Windows server 2016 および Windows Server 2019 で Hyper-v のゲストオペレーティングシステムとしてサポートされている Windows Server のバージョンを次に示します。

|ゲスト オペレーティング システム (サーバー)|仮想プロセッサの最大数|Integration Services|メモ|
|-------------------------------------|----------------------------------------|------------------------|---------|
|Windows Server バージョン 1909 |ジェネレーション 2 の 240<br>64 (第1世代)|組み込み|240より大きい仮想プロセッサのサポートには、Windows Server、バージョン1903、またはそれ以降のゲストオペレーティングシステムが必要です。|
|Windows Server バージョン 1903 |ジェネレーション 2 の 240<br>64 (第1世代)|組み込み||
|Windows Server、バージョン 1809 |ジェネレーション 2 の 240<br>64 (第1世代)|組み込み||
|Windows Server 2019 |ジェネレーション 2 の 240<br>64 (第1世代)|組み込み||
|Windows Server、バージョン 1803 |ジェネレーション 2 の 240<br>64 (第1世代)|組み込み||
|Windows Server 2016 |ジェネレーション 2 の 240<br>64 (第1世代)|組み込み||
|Windows Server 2012 R2 |64|組み込み||
|Windows Server 2012 |64|組み込み||
|Windows Server 2008 R2 Service Pack 1 (SP 1)|64|ゲストオペレーティングシステムをセットアップした後、すべての重要な Windows 更新プログラムをインストールします。|Datacenter、Enterprise、Standard、および Web Edition。|
|Windows Server 2008 Service Pack 2 (SP2)|8|ゲストオペレーティングシステムをセットアップした後、すべての重要な Windows 更新プログラムをインストールします。|Datacenter、Enterprise、Standard、および Web Edition (32 ビットおよび 64 ビット)。|

## <a name="supported-windows-client-guest-operating-systems"></a>サポートされている Windows クライアントのゲスト オペレーティング システム

Windows Server 2016 および Windows Server 2019 で Hyper-v のゲストオペレーティングシステムとしてサポートされている Windows クライアントのバージョンを次に示します。

|ゲスト オペレーティング システム (クライアント)|仮想プロセッサの最大数|Integration Services|メモ|
|-------------------------------------|----------------------------------------|------------------------|---------|
|Windows 10|32|組み込み||
|Windows 8.1|32|組み込み||
|Windows 7 Service Pack 1 (SP 1)|4|ゲストオペレーティングシステムをセットアップした後で、統合サービスをアップグレードします。|Ultimate、Enterprise、および Professional Edition (32 ビットおよび 64 ビット)。|

## <a name="guest-operating-system-support-on-other-versions-of-windows"></a>その他のバージョンの Windows でのゲスト オペレーティング システムのサポート

次の表は、他のバージョンの Windows 上の Hyper-v でサポートされているゲストオペレーティングシステムに関する情報へのリンクを示しています。

|ホストのオペレーティング システム|トピック|
|-------------------------|---------|
|Windows 10|[クライアント HYPER-V で Windows 10 でサポートされるゲスト オペレーティング システム](/virtualization/hyper-v-on-windows/about/supported-guest-os)|
|Windows Server 2012 R2 および Windows 8.1|-   [Windows Server 2012 R2 および Windows 8.1 の Hyper-v でサポートされている Windows ゲストオペレーティングシステム](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn792027(v=ws.11))<br />-   [Hyper-v 上の Linux および FreeBSD Virtual Machines](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md)|
|Windows Server 2012 および Windows 8|[Windows Server 2012 と Windows 8 の Hyper-V でサポートされている Windows ゲスト オペレーティング システム](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn792028(v=ws.11))|
|Windows Server 2008 および Windows Server 2008 R2|[仮想マシンとゲスト オペレーティング システムについて](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794868(v=ws.10))|

## <a name="how-microsoft-provides-support-for-guest-operating-systems"></a>マイクロソフトがゲスト オペレーティング システムのサポートを提供する方法

以下の表に示されているゲスト オペレーティング システムは、Microsoft でサポートされます。

-   Microsoft のオペレーティング システムと統合サービスの問題は、Microsoft サポートによってサポートされます。

-   オペレーティング システム ベンダーによって Hyper-V の実行が認定されている、他のオペレーティング システムで検出された問題については、ベンダーによってサポートが提供されます。

-   他のオペレーティング システムで見つかった問題は、Microsoft は、マルチ ベンダー サポート コミュニティに問題を送信する [TSANet](https://www.tsanet.org/)します。

## <a name="additional-references"></a>その他の参照情報

-   [Hyper-V での Linux および FreeBSD の仮想マシン](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md)

-   [クライアント HYPER-V で Windows 10 でサポートされるゲスト オペレーティング システム](/virtualization/hyper-v-on-windows/about/supported-guest-os)