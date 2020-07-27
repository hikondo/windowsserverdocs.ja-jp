---
title: リリース ノート - Windows Server バージョン 1803 に関する重要な問題
description: Windows Server バージョン 1803 をインストールする前に必要な既知の情報、制限時刻、その他の情報について説明する
ms.prod: windows-server
ms.date: 05/07/2018
ms.technology: server-general
ms.topic: article
author: lizap
ms.author: elizapo
manager: dougkim
ms.localizationpriority: medium
ms.openlocfilehash: 7dc63afba827e2a58ba28d2c4398f1ba80d7e7b5
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86962494"
---
# <a name="release-notes-important-issues-in-windows-server-version-1803"></a>リリース ノート:Windows Server バージョン 1803 に関する重要な問題

>適用先:Windows Server 半期チャネル

これらのリリース ノートは、Windows Server オペレーティング システムの最も重大な問題と既知の問題の回避策についてまとめます。 このリリースの最新機能については、「[Windows Server バージョン 1803 の新機能](whats-new-in-windows-server-1803.md)」を参照してください。 Windows Server バージョン 1803 のコンテナーの実行に関心がある場合は、「[Windows コンテナーについて](/virtualization/windowscontainers/about/)」を確認してください。 

特に指定がない限り、レポートされる問題はそれぞれ、Windows Server バージョン 1803 のすべてのエディションおよびインストール オプションに適用されます。  

この記事は継続的に更新していきます。 既知の問題が特定されると、ここでそれを文書化します。 


## <a name="software-defined-datacenter"></a>ソフトウェア定義データセンター

記憶域スペース ダイレクトなどのソフトウェア定義のデータセンター機能、ソフトウェア定義のネットワーク、およびシールドされた仮想マシンは、Windows Server バージョン 1803 に含まれません。 「[Windows Server 半期チャネルの更新プログラム](https://cloudblogs.microsoft.com/windowsserver/2018/03/29/windows-server-semi-annual-channel-update/)」に記されているように、Windows Server の半期チャネルは、迅速な革新から利益が得られるコンテナーとアプリケーション シナリオに重点を置いています。 

インフラストラクチャ ロールが必要な場合は、長期的なサービス チャネル リリースを使用してください。Windows Server 2016 (現在の利用可能) または[Windows Server 2019](https://cloudblogs.microsoft.com/windowsserver/2018/03/20/introducing-windows-server-2019-now-available-in-preview) (今年の後半に登場)。

ハイパーコンバージド インフラストラクチャの最適なプラットフォームの構築に取り組んでおり、新しい機能の開発や、お客様のフィードバックに基づいた既存の機能の改善を継続しています。 [記憶域スペース ダイレクトのクラスターが 10,000 を超え](https://techcommunity.microsoft.com/t5/storage-at-microsoft/storage-spaces-direct-10-000-clusters-and-counting/ba-p/428185)、ご協力いただきありがとうございます。 今年の後半ではさらに多くを共有できることを楽しみにしています。
