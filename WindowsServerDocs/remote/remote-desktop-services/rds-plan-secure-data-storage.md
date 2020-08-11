---
title: リモート デスクトップ サービス - セキュリティで保護されたデータ ストレージ
description: RDS でユーザー プロファイル ディスク (UPD) を使用してデータを安全に格納するための計画情報。
ms.topic: article
ms.assetid: 37b7f68e-7c3a-4190-a52f-99ae96885fae
author: lizap
ms.author: elizapo
ms.date: 11/21/2016
manager: dongill
ms.openlocfilehash: 90bb870f5d26bcce7f0c96c8260b7c39ad40f327
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87936763"
---
# <a name="remote-desktop-services---secure-data-storage-with-upds"></a>リモート デスクトップ サービス - UPD を使用してセキュリティで保護されたデータ ストレージ

>適用先:Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016

ビジネス リソース、ユーザーの個人用設定データ、および設定をオンプレミスまたは Azure で安全に保管します。 RD セッション ホストは、AD 認証を使用して、カスタマイズした環境で必要になるリソースを、ユーザーに安全に付与します。

ユーザーが自身のリモート リソースにどのエンドポイントからアクセスするかに関わらず、一貫したエクスペリエンスを享受できるようにすることは、RDS 展開の管理の重要な要素です。 ユーザー プロファイル ディスク (UPD) は、ユーザー データ、カスタマイズ、およびアプリケーション設定が単一のコレクション内でユーザーに追従できるようにします。 UPD は、ユーザーがサインインしたときに、そのセッションにマウントされる中央の共有場所に保存されたユーザー別、コレクション別の VHD ファイルです。UPD は、そのセッションの有効期間中はローカル ドライブとして扱われます。

ユーザー側から見ると、UPD は慣れ親しんだエクスペリエンスをもたらします。ユーザーは (ローカル ドライブと思われるものの上にある) ドキュメント フォルダーにドキュメントを保存し、アプリ設定を通常どおり変更し、Windows 環境に対するカスタマイズを行います。 このレジストリ ハイブを含むこのすべてのデータは、UPD に格納され、中央のネットワーク共有場所で保持されます。 UDP は、ユーザーが実際にデスクトップまたは RemoteApp に接続しているときに、ユーザーだけが利用できます。 ユーザーの `C:\Users\<username\>` ディレクトリ全体 (AppData\Local を含む) が UPD に格納されるため、UPD はコレクション内でのみローミングできます。

[PowerShell コマンドレット](/archive/blogs/mniehaus/windows-10-1607-keeping-apps-from-coming-back-when-deploying-the-feature-update)を使用して、中央の共有場所へのパス、各 UPD のサイズ、および UPD に保存されるユーザー プロファイルに対して含めるフォルダーと除外するフォルダーを指定できます。 または、 **[リモート デスクトップ サービス]**  >  **[コレクション]**  >  **[Desktop Collection] (デスクトップ コレクション)**  >  **[Desktop Collection Properties] (デスクトップ コレクションのプロパティ)**  >  **[ユーザー プロファイル ディスク]** の順に移動し、サーバー マネージャーから UPD を有効にできます。 UPD は、コレクション内の特定のユーザーに対してではなく、そのコレクション全体のすべてのユーザーに対して有効または無効にすることに注意してください。 UPD は、コレクション内のサーバーがフル コントロール アクセス許可を持つ中央のファイル共有場所に格納する必要があります。

[記憶域スペース ダイレクト](rds-storage-spaces-direct-deployment.md)を使用して Azure に格納することにより、UPD の高可用性を実現できます。
