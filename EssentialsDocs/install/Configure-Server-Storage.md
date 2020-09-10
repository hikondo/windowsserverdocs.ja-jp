---
title: サーバー記憶域の構成
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.topic: article
ms.assetid: ef7ddcdd-3a74-40ca-9487-c3a6fc5155a5
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: be4bf42f2fe287ad6bd96b9ea5735147ec253e0d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89621833"
---
# <a name="configure-server-storage"></a>サーバー記憶域の構成

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

## <a name="sample-hard-disk-configurations"></a>ハード ディスク構成例
 次の表では、ハード ディスク構成例を示します。 見積もりは、標準的な使用量と機能をベースにしていますが、最適なパフォーマンスに影響を与える問題については記載していません。 顧客の好みとニーズに合わせて、構成でサポートされているどのような種類のハード ディスク (SATA、SCSI など) でも使用できます。

> [!IMPORTANT]
>   Windows Server Essentials は、C: ボリュームとしてインストールする必要があり、ボリュームサイズは 60 GB 以上にする必要があります。 オペレーティング システム ディスクに 2 つのパーティションを作成し、ビジネス データの格納には C: (システム パーティション) を使用しないことをお勧めします。

|サーバーのレベル|ディスク構成|
|------------------|------------------------|
|入力|-2 台の物理ディスク<br /><br /> -次のものを含む RAID 1 ミラーセットとして構成されます。<br /><br /> -C: ボリューム? 60 GB<br /><br /> -D: ボリューム? 1000 GB|
|中間|-3 台の物理ディスク<br /><br /> -次のものを含む RAID 5 セットとして構成されます。<br /><br /> -C: ボリューム? 60 GB<br /><br /> -D: ボリューム? 1500 GB|
|高|-5 台以上の物理ディスク<br /><br /> -C: ボリュームを含む RAID 1 ミラーセット内の2つのディスク 100 GB<br /><br /> -次のものを含む RAID 5 セット内の残りのすべてのディスク。<br /><br /> -D: ボリューム? 1500 GB<br /><br /> -E: ボリューム? 1500 GB|

 これらの推奨値は、インストールされたオペレーティング システムのサイズ、サーバーが使用するデータ記憶域の標準的なサイズ、およびサーバーの稼働期間を通して予想されるデータ記憶域の増分を考慮に入れています。 ボリュームは、1 台の物理ディスク上のパーティションでも、または個別の物理ディスク上に作られたものでもかまいません。 サーバーには顧客の重要なデータが格納されるため、複数の物理ディスクを使用し、ハードウェア RAID または記憶域スペースを使用して顧客のデータを保護することをお勧めします。

## <a name="configuring-your-server-backup"></a>サーバー バックアップの構成
 サーバーの内部ハード ディスクに加えて、顧客は外部 USB ハード ディスクをバックアップに使用することを考慮する必要があります。 顧客は、少なくとも 2 台の十分な容量の外部ハード ディスクで、サーバーのすべてのデータをバックアップすることが理想です。 外部ハード ディスクを使用すると、顧客は毎晩 1 台を離れた場所に置くことで、よりいっそうのデータ保護がはかれます。

## <a name="partition-configuration"></a>パーティション構成
 サーバーの初期構成中に、共有フォルダーとクライアント コンピューターのバックアップ フォルダーを含む一連の既定のサーバー フォルダーが、ディスク 0 の最大のデータ パーティションに作成されます。

## <a name="see-also"></a>参照

 [Windows Server ESSENTIALS ADK を使用したはじめに](Getting-Started-with-the-Windows-Server-Essentials-ADK.md)[イメージの作成とカスタマイズ追加の](Creating-and-Customizing-the-Image.md)[カスタマイズカスタマイズ](Additional-Customizations.md)[のイメージの準備カスタマーエクスペリエンスをテストするためのイメージの準備](Preparing-the-Image-for-Deployment.md) [Testing the Customer Experience](Testing-the-Customer-Experience.md)

