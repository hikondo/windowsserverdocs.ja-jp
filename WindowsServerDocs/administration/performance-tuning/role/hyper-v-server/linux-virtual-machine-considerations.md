---
title: Linux 仮想マシンに関する考慮事項
description: Linux および BSD の仮想マシン
ms.topic: article
ms.author: asmahi
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: be9d2f0d758f6f59282c770ef1a48d71a947ba00
ms.sourcegitcommit: 7cacfc38982c6006bee4eb756bcda353c4d3dd75
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2020
ms.locfileid: "90078289"
---
# <a name="linux-virtual-machine-considerations"></a>Linux 仮想マシンに関する考慮事項

Linux および BSD の仮想マシンには、Hyper-v の Windows 仮想マシンと比較して、追加の考慮事項があります。

最初の考慮事項は、Integration Services が存在するか、または VM が、啓蒙されていないエミュレートされたハードウェア上でのみ実行されているかどうかです。 組み込みまたはダウンロード可能な Integration Services を持つ Linux および BSD リリースの表は、 [Windows 上の hyper-v のサポートされている linux および FreeBSD 仮想マシン](../../../../virtualization/hyper-v/supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows.md)で利用できます。 これらのページには、Linux ディストリビューションリリースで利用できる使用可能な Hyper-v 機能のグリッドと、該当する場合はそれらの機能に関する注意事項があります。

ゲストが Integration Services 実行されている場合でも、最適なパフォーマンスを発揮しないレガシハードウェアで構成できます。 たとえば、レガシネットワークアダプターを使用する代わりに、ゲストの仮想イーサネットアダプターを構成して使用します。 Windows Server 2016 では、sr-iov などの高度なネットワークも利用できます。

## <a name="linux-network-performance"></a>Linux ネットワークパフォーマンス

既定では、ハードウェアの高速化とオフロードが既定で有効になっています。 ホスト上の NIC のプロパティで vRSS が有効になっていて、Linux ゲストには vRSS を使用する機能がある場合は、機能が有効になります。 Powershell では、コマンドを使用して同じパラメーターを変更でき `EnableNetAdapterRSS` ます。

同様に、ゲスト**プロパティ**の [  >  **構成...**  >  ] で使用される物理 NIC で、VMMQ (仮想スイッチ RSS) 機能を有効にすることもできます。**[詳細**設定] タブで、次のものを使用して、**仮想スイッチ RSS**を**有効**に設定 > か、Powershell で VMMQ を有効にします。

```PowerShell
 Set-VMNetworkAdapter -VMName **$VMName** -VmmqEnabled $True
 ```

ゲストでは、追加の TCP チューニングを制限を増やすことによって実行できます。 仮想化されたワークロードは、複数の Cpu に対して最適なパフォーマンスを拡散し、仮想化されたワークロードは "ベアメタル" よりも待機時間が長くなるため、最適なスループットが得られます。

ネットワークベンチマークで有用なチューニングパラメーターの例を次に示します。

```PowerShell
net.core.netdev_max_backlog = 30000
net.core.rmem_max = 67108864
net.core.wmem_max = 67108864
net.ipv4.tcp_wmem = 4096 12582912 33554432
net.ipv4.tcp_rmem = 4096 12582912 33554432
net.ipv4.tcp_max_syn_backlog = 80960
net.ipv4.tcp_slow_start_after_idle = 0
net.ipv4.tcp_tw_reuse = 1
net.ipv4.ip_local_port_range = 10240 65535
net.ipv4.tcp_abort_on_overflow = 1
```

ネットワークマイクロベンチマークの便利なツールは ntttcp です。これは、Linux と Windows の両方で使用できます。 Linux バージョンはオープンソースであり、 [github.com の ntttcp-linux](https://github.com/Microsoft/ntttcp-for-linux)から入手できます。 Windows のバージョンについては、 [ダウンロードセンター](https://gallery.technet.microsoft.com/NTttcp-Version-528-Now-f8b12769)を参照してください。 ワークロードをチューニングする場合は、スループットを最大にするために必要な数のストリームを使用することをお勧めします。 Ntttcp を使用してトラフィックをモデル化すると、パラメーターによって、 `-P` 使用される並列接続の数が設定されます。

## <a name="linux-storage-performance"></a>Linux ストレージのパフォーマンス

次のようなベストプラクティスについては、「 [hyper-v で Linux を実行するためのベストプラクティス](../../../../virtualization/hyper-v/best-practices-for-running-linux-on-hyper-v.md)」に記載されています。 Linux カーネルには、さまざまなアルゴリズムで要求を並べ替えるための異なる i/o スケジューラがあります。 NOOP は、ハイパーバイザーによって実行されるスケジュールの決定を渡す先入れ先出しキューです。 Hyper-v で Linux 仮想マシンを実行する場合は、スケジューラとして NOOP を使用することをお勧めします。 特定のデバイスの scheduler を変更するには、ブートローダーの構成 (/etc/grub.conf など) で、を `elevator=noop` カーネルパラメーターに追加してから、を再起動します。

ネットワークの場合と同様に、Linux ゲストのパフォーマンスは、記憶域を使用すると、ホストのビジー状態を維持するのに十分な深さのキューから最大限に活用できます。 Microbaio エンジンを使用した fio ベンチマークツールでは、マイクロベンチマークストレージのパフォーマンスが最も高くなります。

## <a name="additional-references"></a>その他の参照情報

-   [Hyper-V の用語](terminology.md)

-   [Hyper-V のアーキテクチャ](architecture.md)

-   [Hyper-V サーバーの構成](configuration.md)

-   [Hyper-V プロセッサのパフォーマンス](processor-performance.md)

-   [Hyper-V メモリのパフォーマンス](memory-performance.md)

-   [Hyper-V 記憶域の I/O のパフォーマンス](storage-io-performance.md)

-   [Hyper-V ネットワークの I/O のパフォーマンス](network-io-performance.md)

-   [仮想化環境のボトルネックの検出](detecting-virtualized-environment-bottlenecks.md)