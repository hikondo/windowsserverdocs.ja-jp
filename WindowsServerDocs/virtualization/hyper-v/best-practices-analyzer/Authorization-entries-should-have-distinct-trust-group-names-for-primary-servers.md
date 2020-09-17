---
title: 承認エントリには、同じ信頼グループに属していない仮想マシンを持つプライマリサーバーに対して、異なる信頼グループ名を付ける必要があります。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 8827a3a7-9f3c-4f51-826a-8e2ec43e01df
ms.date: 8/16/2016
ms.openlocfilehash: 984fa9233a433384cddae34af9a62bcf1e0204ca
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90747107"
---
# <a name="authorization-entries-should-have-distinct-trust-group-names-for-primary-servers-with-virtual-machines-that-are-not-part-of-the-same-trust-group"></a>承認エントリには、同じ信頼グループに属していない仮想マシンを持つプライマリサーバーに対して、異なる信頼グループ名を付ける必要があります。

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
*サーバーは、仮想マシンと同じレプリケーションタグに関連付けられている承認リスト内の任意のサーバーから、レプリカ仮想マシンへのレプリケーション要求を受け入れます。*

## <a name="impact"></a>**影響**
*異なる承認エントリに属するプライマリサーバーからレプリケーションを受け入れる仮想マシンでは、プライバシーとセキュリティの問題が発生する可能性があります。これは、次の承認エントリに影響します。 \<list of authorization entries>*

## <a name="resolution"></a>**解決方法**
*同じセキュリティグループに属していない仮想マシンを使用して、プライマリサーバーの承認エントリで異なるタグを使用します。Hyper-v の設定を変更して、レプリケーションタグを構成します。*



