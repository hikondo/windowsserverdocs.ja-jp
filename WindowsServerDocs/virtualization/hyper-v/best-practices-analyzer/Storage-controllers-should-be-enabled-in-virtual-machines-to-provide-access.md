---
title: 接続された記憶域にアクセスできるようにするには、記憶域コントローラーを仮想マシンで有効にする必要があります
description: このベストプラクティスアナライザー規則によって報告された問題を解決するための手順を示します。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 532548a1-8ffe-4b5b-902e-ed2f0819012b
ms.date: 8/16/2016
ms.openlocfilehash: 5eb1767fd51253ed26c0a169be1043b633dbcbcd
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746197"
---
# <a name="storage-controllers-should-be-enabled-in-virtual-machines-to-provide-access-to-attached-storage"></a>接続された記憶域にアクセスできるようにするには、記憶域コントローラーを仮想マシンで有効にする必要があります

>適用先:Windows Server 2016

ベスト プラクティスとスキャンの詳細については、「 [ベスト プラクティス アナライザー](https://go.microsoft.com/fwlink/?LinkId=122786)」をご覧ください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題

*1つまたは複数の記憶域コントローラーが仮想マシンで無効になっている可能性があります。*

## <a name="impact"></a>影響

*バーチャルマシンは、無効な記憶域コントローラーに接続されている記憶域を使用できません。これは、次の仮想マシンに影響します。*

\<list of virtual machine names>

## <a name="resolution"></a>解決策

*ゲストオペレーティングシステムのデバイスマネージャーを使用して、すべての記憶域コントローラーを有効にします。記憶域コントローラーが不要な場合は、Hyper-v マネージャーを使用して仮想マシンから削除します。*

デバイスマネージャーの使用方法については、ゲストオペレーティングシステムのヘルプを参照してください。 記憶域コントローラーを削除する方法については、次の手順を参照してください。

#### <a name="to-remove-a-scsi-storage-controller-from-the-virtual-machine"></a>SCSI 記憶装置をバーチャルマシンから削除するには

1.  Hyper-V マネージャーを開きます。 **[スタート]** ボタンをクリックし、**[管理ツール]** をポイントして **[Hyper-V マネージャー]** をクリックします。

2.  結果ウィンドウで [ **仮想マシン**, 、構成する仮想マシンを選択します。

3.  仮想マシンが実行されている場合は、仮想マシンをシャットダウンします。 仮想マシンを右クリックし、[ **シャットダウン**] をクリックします。

4.  **[操作]** ウィンドウで、仮想マシン名の下の **[設定]** をクリックします。

5.  [ **設定** ] ダイアログボックスの左側のウィンドウで、[ **ハードウェア**] の下の [ **SCSI コントローラー**] をクリックします。

6.  右側のウィンドウで、[ **削除**] をクリックします。



