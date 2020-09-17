---
title: 仮想スイッチにバインドされているチーム インターフェイスが既定のモードである必要があります。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 8c118e1e-865f-4cff-acdc-7c35e45d5da9
ms.date: 8/16/2016
ms.openlocfilehash: 1e3d701ccc0ac7a6a3765df08f6b039fbb4ca3eb
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746137"
---
# <a name="the-team-interface-bound-to-a-virtual-switch-should-be-in-default-mode"></a>仮想スイッチにバインドされているチーム インターフェイスが既定のモードである必要があります。

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>**問題点**
*一部の仮想スイッチがチーム インターフェイスにバインドされますが、チーム インターフェイスは、すべての Vlan でトラフィックを仮想スイッチに渡されない。*

## <a name="impact"></a>**影響**
*次の仮想スイッチは、すべての Vlan にアクセスすることはできません: \n{0}*

## <a name="resolution"></a>**解決方法**
*サーバー マネージャーを使用してまたは Windows PowerShell コマンドレット セット NetLbfoTeamNic チーム インターフェイスの既定のモードにリセットします。*



