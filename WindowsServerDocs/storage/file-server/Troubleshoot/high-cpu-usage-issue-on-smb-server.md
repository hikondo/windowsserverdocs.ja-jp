---
title: SMB サーバーでの CPU 使用率の高い問題
description: SMB サーバーでの CPU 使用率の高い問題をトラブルシューティングする方法について説明します。
author: Deland-Han
manager: dcscontentpm
ms.topic: article
ms.author: delhan
ms.date: 12/25/2019
ms.openlocfilehash: 9634ca5b0eb07beff8d8213f88e771d76734e6fc
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80815436"
---
# <a name="high-cpu-usage-issue-on-the-smb-server"></a>SMB サーバーでの CPU 使用率の高い問題

この記事では、SMB サーバーでの CPU 使用率の高い問題をトラブルシューティングする方法について説明します。

## <a name="high-cpu-usage-because-of-storage-performance-issues"></a>記憶域のパフォーマンスに問題があるため、CPU 使用率が高くなっています

記憶域のパフォーマンスの問題により、SMB サーバーの CPU 使用率が高くなる可能性があります。 トラブルシューティングを行う前に、srv2 の既知の問題を排除するために、最新の更新プログラムのロールアップが SMB サーバーにインストールされていることを確認してください。

ほとんどの場合、システムプロセスで CPU 使用率が高くなるという問題が発生していることがわかります。 続行する前に、プロセスエクスプローラーを使用して、srv2 または ntfs.sys が過剰な CPU リソースを消費していることを確認してください。

### <a name="storage-area-network-san-scenario"></a>記憶域ネットワーク (SAN) のシナリオ

集計レベルでは、SAN 全体のパフォーマンスが問題なく表示されることがあります。 ただし、SMB の問題を処理する場合は、個々の要求の応答時間が最も重要になります。

通常、この問題は、SAN 内の何らかの形式のコマンドキューによって発生することがあります。 **Perfmon**を使用して、 **Microsoft Windows-StorPort**トレースをキャプチャし、それを分析してストレージの応答性を正確に判断できます。

### <a name="disk-io-latency"></a>ディスク IO 待機時間

ディスク IO 待機時間は、ディスク IO 要求が作成されて完了するまでの遅延時間の尺度です。

Perfmon で測定される IO 待機時間には、ハードウェアレイヤーで費やされた時間に加えて、Microsoft ポートドライバーキュー (SCSI の場合は Storport) で費やされた時間も含まれます。 実行中のプロセスが大きな StorPort キューを生成する場合、測定される待機時間が増加します。 これは、IO がハードウェアレイヤーにディスパッチされる前に待機する必要があるためです。

Perfmon では、次のカウンターは物理ディスクの待機時間を示します。

- "物理ディスクパフォーマンスオブジェクト"-\> "Avg. Disk sec/Read カウンタ" –これは、読み取りの平均待機時間を示します。

- "物理ディスクパフォーマンスオブジェクト"-\> "Avg. Disk sec/Write カウンタ" –これは、書き込みの平均待機時間を示します。

- "物理ディスクのパフォーマンスオブジェクト"-\> "Avg. Disk sec/Transfer カウンタ" –読み取りと書き込みの両方の合計の平均が表示されます。

"\_Total" インスタンスは、コンピューター内のすべての物理ディスクの待機時間の平均値です。 他の各インスタンスは、個々の物理ディスクを表します。

> [!NOTE]
> これらのカウンターは、1秒あたりの平均ディスク転送数と混同しないようにしてください。これらはまったく異なるカウンターです。

### <a name="windows-storage-stack-follows"></a>Windows の記憶域スタックは次のとおりです

このセクションでは、Windows の記憶域スタックに関する簡単な説明を示します。

アプリケーションが IO 要求を作成すると、スタックの一番上にある Windows IO サブシステムに要求が送信されます。 その後、IO はスタックのすべての方向をハードウェアの "ディスク" サブシステムに転送します。 その後、応答はすべてのバックアップ方法をたどります。 このプロセスでは、各レイヤーがその機能を実行し、次のレイヤーに IO を渡します。

![スタックフロー](media/high-cpu-usage-issue-on-smb-server-1.png)

Perfmon では、1秒あたりのパフォーマンスデータは作成されません。 代わりに、Windows 内の他のサブシステムによって提供されるデータを使用します。

"物理ディスクパフォーマンスオブジェクト" の場合、データは記憶域スタックの "Partition manager" レベルでキャプチャされます。

前のセクションで説明したカウンターを測定する際には、要求によって "Partition manager" レベル以下で費やされたすべての時間を測定します。 IO 要求がパーティションマネージャーによってスタックに送信されると、その要求にタイムスタンプがかかります。 返されたときに、もう一度スタンプし、時間の差を計算します。 時差は待ち時間です。

これにより、次のコンポーネントで費やされる時間について会計が行われます。

- クラスドライバー-ディスクやテープなどのデバイスの種類を管理します。

- ポートドライバー-SCSI、FC、SATA などのトランスポートプロトコルを管理します。

- デバイスミニポートドライバー-これは、記憶域アダプターのデバイスドライバーです。 これは、Raid コントローラーや FC HBA など、デバイスの製造元によって提供されます。

- ディスクサブシステム-デバイスミニポートドライバーの下にあるすべてのものが含まれます。 これは、単一の物理ハードディスクに接続されているケーブル、または記憶域ネットワークとして複雑なケーブルとして簡単に行うことができます。 問題の原因がこのコンポーネントであると判断された場合、トラブルシューティングの詳細については、ハードウェアベンダーに問い合わせてください。

### <a name="disk-queuing"></a>ディスクキュー

ディスクサブシステムが特定の時間に受け入れることができる IO の量は限られています。 余分な IO は、ディスクが IO を再び受け入れることができるようになるまで、キューに入れられます。 I/O が "Partition manager" レベルより下のキューで使用される時間は、Perfmon の物理ディスク待機時間の測定値で考慮されます。 キューのサイズが大きくなり、IO の待機時間が長くなると、測定される待機時間も長くなります。

次のように、"Partition manager" レベルの下に複数のキューがあります。

- Microsoft ポートドライバーキュー-SCSIport または Storport キュー

- 製造元が提供するデバイスドライバキュー-OEM デバイスドライバ

- ハードウェアキュー (ディスクコントローラーキュー、SAN スイッチキュー、配列コントローラーキュー、ハードディスクキューなど)

また、ハードディスクが IO のアクティブな処理に費やした時間と、要求が "Partition manager" レベルに戻って完了とマークされるまでの移動時間についても考慮します。

最後に、ポートドライバーキュー (SCSI Storport 用) に特に注意を払う必要があります。 ポートドライバーは、製造元が提供するデバイスミニポートドライバーに渡す前に、IO に触れる最後の Microsoft コンポーネントです。

デバイスのミニポートドライバーが、そのキューまたはその下にあるハードウェアキューが飽和状態になっているため、それ以上 IO を受け入れることができない場合は、ポートドライバーキューで IO の累積を開始します。 Microsoft ポートドライバーキューのサイズは、使用可能なシステムメモリ (RAM) によってのみ制限され、非常に大きくなる可能性があります。 これにより、測定される待機時間が長くなります。

## <a name="high-cpu-caused-by-enumerating-folders"></a>フォルダーの列挙によって発生する CPU の増加 

この問題のトラブルシューティングを行うには、アクセスベースの列挙 (ABE) 機能を無効にします。

ABE が有効になっている SMB 共有を特定するには、次の PowerShell コマンドを実行します。

```PowerShell
Get-SmbShare | Select Name, FolderEnumerationMode
```

無制限 = ABE は無効です。 <br />
AccessBase = ABE enabled。


**サーバーマネージャー**で ABE を有効にすることができます。 Navigatie は、**ファイルサービスと記憶域サービス**を**共有 > 共有**を右クリックし、 **[プロパティ]** 、 **[設定]** の順に選択し、 **[アクセスベースの列挙を有効に]** する を選択します。

![UI オプション](media/high-cpu-usage-issue-on-smb-server-2.png)

また、パフォーマンスを向上させるために、 **ABELevel**を低いレベル (1 または 2) に減らすこともできます。

コンソールまたは RDP セッションを使用してローカルでフォルダーを開くと、列挙が遅い場合にディスクのパフォーマンスを確認できます。
