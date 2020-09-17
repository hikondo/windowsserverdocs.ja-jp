---
title: SR-IOV 用に構成された仮想マシンの実行の数は仮想マシンで使用できる仮想関数の数を超えることはできません。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 8bd4af5e-9e7d-4710-8950-39435a8bb373
ms.date: 8/16/2016
ms.openlocfilehash: 432bf4132e8c19a326fda646960b30315d3952b1
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745807"
---
# <a name="the-number-of-running-virtual-machines-configured-for-sr-iov-should-not-exceed-the-number-of-virtual-functions-available-to-the-virtual-machines"></a>SR-IOV 用に構成された仮想マシンの実行の数は仮想マシンで使用できる仮想関数の数を超えることはできません。

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題
*利用していない十分な仮想関数をシングル ルート I/O 仮想化 (SR-IOV) 用に構成された仮想マシンの実行の数。*

## <a name="impact"></a>影響
*ネットワークのパフォーマンスは、次の仮想マシンに最適でない可能性があります。*

\<list of virtual machines>

## <a name="resolution"></a>解決策
*SR-IOV 仮想機能を必要としない 1 つまたは複数の仮想マシンで SR-IOV を無効にすることを検討してください。*



