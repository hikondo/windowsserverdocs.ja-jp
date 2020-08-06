---
title: Windows Server Essentials のシステム要件
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/31/2013
ms.topic: article
ms.assetid: 0951a67d-492f-41ad-9ae5-8e4cd25e3041
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: b82435dc9d0018d3ac3fa5c6855b18bcddbd2797
ms.sourcegitcommit: 04637054de2bfbac66b9c78bad7bf3e7bae5ffb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2020
ms.locfileid: "87838101"
---
# <a name="system-requirements-for-windows-server-essentials"></a>Windows Server Essentials のシステム要件

>適用対象: Windows Server 2019 Essentials、Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

  Windows Server Essentials サーバーソフトウェアは、64ビットのみのオペレーティングシステムです。 表1は、Windows Server Essentials で推奨される最小ハードウェア要件を定義します。 表 2 に、サーバーの追加のハードウェアおよびソフトウェア要件を定義します。


## <a name="table-1-system-requirements-for-windows-server-essentials"></a>表 1 Windows Server Essentials のシステム要件

|コンポーネント|最小値|推奨*|最大値|
|---------------|-------------|-------------------|-------------|
|CPU ソケット|1.4 GHz (64 ビット プロセッサ) 以上、シングル コア用<br /><br /> 1.3 GHz (64 ビット プロセッサ) 以上、マルチコア用|3.1 GHz (64 ビット プロセッサ) 以上、マルチコア用|2 つのソケット|
|メモリ (RAM)|2 GB<br /><br /> Windows Server Essentials を仮想マシンとして展開する場合は 4 GB|16 GB|64 GB|
|ハード ディスクと利用可能な記憶域|160 GB ハード ディスク、60 GB のシステム パーティション||制限なし|

 *推奨されるハードウェア要件では、ユーザーおよびデバイスの最大の制限をサポートします。

## <a name="table-2-additional-hardware-and-software-requirements-for-windows-server-essentials"></a>表 2 Windows Server Essentials の追加のハードウェアおよびソフトウェア要件

|コンポーネント|説明|
|---------------|-----------------|
|ネットワーク アダプター|Gigabit Ethernet アダプター (10/100/1000BaseT PHY/MAC)|
|インターネット|機能によっては、インターネット アクセス (有料の可能性があります) または Microsoft アカウントが必要となる場合があります|
|サポートされるクライアント オペレーティング システム|Windows 8.1、Windows 8、Windows 7、Macintosh OS X バージョン 10.5 ～ 10.8<br /><br /> **注:** 一部の機能には、professional またはそれ以降のエディションが必要です。<br /><br /> 1 GB の利用可能なハード ドライブの容量 (このディスクの一部はインストール後に解放されます)|
|ルーター|IPv4 または IPv6 ネットワーク アドレス変換 (NAT) をサポートするルーターまたはファイアウォール|
|その他の要件|DVD-ROM ドライブ|

 実際の要件は、システム構成やインストールするアプリケーションおよび機能によって異なります。 プロセッサのパフォーマンスは、プロセッサのクロック周波数だけでなく、コアの数やプロセッサ キャッシュのサイズの影響も受けます。 システム パーティションに必要な記憶域の要件はおおよそのものです。 ネットワーク経由でインストールしている場合、追加の利用可能な記憶域が必要になる可能性があります。

 ハードウェア要件の詳細については、「 [Windows Server カタログ](https://www.windowsservercatalog.com/)」を参照してください。

 すべてのサーバーハードウェアは、システム用の Windows Server 2012 R2 ロゴプログラム用に設定された要件を満たしている必要があります。 詳細については、「 [Windows ロゴ プログラム](/previous-versions/windows/hardware/hck/dn641155(v=vs.85))」を参照してください。

> [!IMPORTANT]
> ダイナミックディスクは、Windows Server Essentials ではサポートされていません。

## <a name="additional-references"></a>その他の参照情報

-   [Windows Server Essentials のインストール](../install/Install-Windows-Server-Essentials.md)

-   [Windows Server Essentials のシステム要件](system-requirements.md)