---
title: Windows Server 2008 R2 は、少なくとも最小メモリ容量で構成する必要があります
description: このベストプラクティスアナライザー規則によって報告された問題を解決するための手順を示します。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 12418668-52d3-4e70-b56f-85dcb144a8c0
ms.date: 8/16/2016
ms.openlocfilehash: df8e54471ac4832baa095f26197ebe1d76c6dfa9
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746757"
---
# <a name="windows-server-2008-r2-should-be-configured-with-at-least-the-minimum-amount-of-memory"></a>Windows Server 2008 R2 は、少なくとも最小メモリ容量で構成する必要があります

>適用先:Windows Server 2016

ベスト プラクティスとスキャンの詳細については、「 [ベスト プラクティス アナライザー](https://go.microsoft.com/fwlink/?LinkId=122786)」をご覧ください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|エラー|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題

*Windows Server 2008 R2 を実行している仮想マシンは、最小 RAM 容量 (512 MB) 未満で構成されています。*

## <a name="impact"></a>影響

*次の仮想マシン上のゲストオペレーティングシステムが実行されていないか、または信頼性の高い動作をしていない可能性があります。*


\<list of virtual machine names>

## <a name="resolution"></a>解決策

*Hyper-v マネージャーを使用して、この仮想マシンに割り当てられているメモリを少なくとも 512 MB に増やします。*

### <a name="to-increase-the-memory-using-hyper-v"></a>Hyper-v を使用してメモリを増やすには

1.  Hyper-V マネージャーを開きます。 **[スタート]** ボタンをクリックし、**[管理ツール]** をポイントして **[Hyper-V マネージャー]** をクリックします。

2.  結果ウィンドウで [ **仮想マシン**, 、構成する仮想マシンを選択します。 バーチャルマシンの状態は [ **オフ (オフ**)」と表示されます。 そうでない場合は、バーチャルマシンを右クリックし、[ **シャットダウン**] をクリックします。

3.  **[操作]** ウィンドウで、仮想マシン名の下の **[設定]** をクリックします。

4.  ナビゲーションウィンドウで、[ **メモリ**] をクリックします。

5.  [ **メモリ** ] ページで、 **スタートアップ RAM** を 512 MB 以上に設定し、[ **OK]** をクリックします。

### <a name="increase-the-memory-using-windows-powershell"></a>Windows PowerShell を使用してメモリを増やす

1.  Windows PowerShell を開きます。 (デスクトップから [ **スタート** ] をクリックし、「 **Windows PowerShell**」と入力を開始します)。

2.  右クリック **Windows PowerShell** ] をクリック **管理者として実行**します。

3.  交換した後にこのコマンドを実行 \<MyVM> 、仮想マシンの名前に置き換えます。

```
Set-VMMemory <MyVM> -StartupBytes 512MB
```

## <a name="see-also"></a>関連項目
[設定-VMMemory](/powershell/module/hyper-v/set-vmmemory?view=win10-ps)