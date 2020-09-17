---
title: 仮想マシンでの専用の 1 つまたは複数の外部仮想ネットワークを予約します。
description: このベストプラクティスアナライザー規則によって報告された問題を解決するための手順を示します。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: f7732258-93f1-44e8-835b-5ad2d1c45cd9
ms.date: 8/16/2016
ms.openlocfilehash: 8039f5ef94f1ca762a994607d5a1faf8eac0d98e
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746507"
---
# <a name="reserve-one-or-more-external-virtual-networks-for-exclusive-use-by-virtual-machines"></a>仮想マシンでの専用の 1 つまたは複数の外部仮想ネットワークを予約します。

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

*すべての外部仮想ネットワークは、管理オペレーティング システムと仮想マシンの両方で使用するために構成されます。*

## <a name="impact"></a>影響

*管理オペレーティング システムのネットワークのパフォーマンスが低下する可能性があります。*

## <a name="resolution"></a>解決策

*管理オペレーティング システムとの外部仮想ネットワークの共有を停止するのにには、仮想スイッチ マネージャーを使用します。*

#### <a name="to-stop-sharing-the-external-virtual-network-with-the-management-operating-system"></a>管理オペレーティング システムとの外部仮想ネットワークの共有を停止するには

1.  Hyper-V マネージャーを開きます。 **[スタート]** ボタンをクリックし、**[管理ツール]** をポイントして **[Hyper-V マネージャー]** をクリックします。

2.  **[操作]** メニューの **[仮想スイッチ マネージャー]** をクリックします。

3.  **仮想スイッチ**, 、外部仮想スイッチの名前をクリックします。

4.  **接続の種類** 物理ネットワーク アダプターの名前の下の領域をオフに、 **管理オペレーティング システムでこのネットワーク アダプタを共有できるように** チェック ボックスをオンします。

5.  **[OK]** をクリックします。



