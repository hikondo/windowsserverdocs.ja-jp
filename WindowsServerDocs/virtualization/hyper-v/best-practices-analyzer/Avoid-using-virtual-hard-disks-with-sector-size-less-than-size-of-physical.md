---
title: バーチャルハードディスクファイルが保管されている物理記憶域のセクターサイズよりも小さいセクターサイズのバーチャルハードディスクは使用しないでください。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: b7cf994e-bf4b-4b1b-bad6-ecf7d46d105e
ms.date: 8/16/2016
ms.openlocfilehash: 946168aa200ec80e5d2c9a69e0ecfad2477dcb6e
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745887"
---
# <a name="avoid-using-virtual-hard-disks-with-a-sector-size-less-than-the-sector-size-of-the-physical-storage-that-stores-the-virtual-hard-disk-file"></a>バーチャルハードディスクファイルが保管されている物理記憶域のセクターサイズよりも小さいセクターサイズのバーチャルハードディスクは使用しないでください。

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**運転中** <br />**システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>**問題点**
*1つまたは複数のバーチャルハードディスクの物理セクターサイズが、バーチャルハードディスクファイルが配置されている記憶域の物理セクターサイズよりも小さくなっています。*

## <a name="impact"></a>**影響**
*バーチャルハードディスクを使用するバーチャルマシンまたはアプリケーションでパフォーマンスの問題が発生する可能性があります。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>**解決方法**
*次のいずれかの操作を行います。*

-   *記憶域の移行を実行して、仮想ハードディスクを新しい物理システムに移動する*

-   *Windows PowerShell または WMI を使用して、VHDX 形式の仮想ハードディスクが特定のセクターサイズを報告できるようにする*

-   *レジストリ設定を使用して、VHD 形式のバーチャルハードディスクが4k の物理セクターサイズを報告できるようにします。*



