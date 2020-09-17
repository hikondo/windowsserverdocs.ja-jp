---
title: ライブマイグレーショントラフィックのすべてのネットワークは、少なくとも 1 Gbps のリンク速度を持つ必要があります。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 89411b63-bec8-463d-b486-107548ed440e
ms.date: 8/16/2016
ms.openlocfilehash: e73f17a790ac64942ea1ca608d4eeaa9b18402de
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746317"
---
# <a name="all-networks-for-live-migration-traffic-should-have-a-link-speed-of-at-least-1-gbps"></a>ライブマイグレーショントラフィックのすべてのネットワークは、少なくとも 1 Gbps のリンク速度を持つ必要があります。

> 適用先:Windows Server 2016

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題
*ライブマイグレーショントラフィックのネットワークには、少なくとも 1 Gbps のリンク速度がありません。*

## <a name="impact"></a>影響
*ライブマイグレーションが遅くなり、TCP 接続のタイムアウトによってネットワーク接続が中断される可能性があります。*

## <a name="resolution"></a>解決策
*1 Gbps 以上の速度でライブマイグレーションネットワークを少なくとも1つ構成してください。*

既存のネットワークアダプターが 1 Gbps 以上のリンク速度をサポートしているかどうかを確認するには、ネットワークハードウェアベンダーのドキュメントを参照してください。



