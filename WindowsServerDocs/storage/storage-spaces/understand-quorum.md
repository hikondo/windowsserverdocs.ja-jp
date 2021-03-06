---
title: クラスターとプール クォーラムの概要
description: クラスターとプールのクォーラムについて理解する」を参照してください。
ms.author: adagashe
manager: eldenc
ms.topic: article
author: adagashe
ms.date: 01/18/2019
ms.localizationpriority: medium
ms.openlocfilehash: ffd1afdc76ddefbf53ff8f78d15666f343654022
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87970139"
---
# <a name="understanding-cluster-and-pool-quorum"></a>クラスターとプール クォーラムの概要

>適用先:Windows Server 2019、Windows Server 2016

[Windows Server フェールオーバー クラスタリング](../../failover-clustering/failover-clustering-overview.md)では、ワークロードの高可用性を実現します。 これらのリソースは、リソースをホストするノードが稼働していると可用性が高いと見なされます。ただし、クラスターでは通常、半分を越えるノードが実行されている必要があり、その場合に "*クォーラム*" を持つとされます。

クォーラムは、*スプリット ブレイン* シナリオを避けるように設計されています。これは、ネットワークにパーティションがあり、ノードのサブセットが相互に通信できない場合に発生します。 これにより、ノードの両方のサブセットがワークロードを所有し、同じディスクへ書き込もうとするため、さまざまな問題につながる可能性があります。 ただし、フェールオーバー クラスタリングのクォーラムの概念によってこれは回避されます。この概念では、これらのノードのグループのうち 1 つだけが実行を継続するよう強制され、これらのグループの 1 つのみがオンラインのままになります。

クォーラムでは、クラスターがオンライン状態を維持しながら耐えることができる障害数が決定されます。 クォーラムは、クラスター ノードのサブセット間の通信に問題がある場合のシナリオに対処するように設計されています。これにより、複数のサーバーが同時にリソース グループをホストし、同じディスクに同時に書き込むことはありません。 こうしたクォーラムの概念を持つことにより、クラスターは、ノードのいずれかのサブセットでクラスター サービスを強制的に停止し、特定のリソース グループの真の所有者が 1 つのみになるようにします。 停止されたノードが主要なノード グループと再度通信できるようになると、これらは、クラスターに再度参加し、そのクラスター サービスを開始します。

Windows Server 2019 と Windows Server 2016 には、独自のクォーラムメカニズムを持つシステムのコンポーネントが2つあります。

- **クラスター クォーラム**:これはクラスター レベルで動作します (つまり、ノードが停止した場合、クラスターは稼働状態を維持できます)
- **プール クォーラム**:これは記憶域スペース ダイレクトが有効な場合にプール レベルで動作します (つまり、ノードとドライブが停止した場合、プールは稼働状態を維持できます)。 記憶域プールは、クラスター化と非クラスター化の両方のシナリオで使用するように設計されているため、異なるクォーラム メカニズムを持ちます。

## <a name="cluster-quorum-overview"></a>クラスター クォーラムの概要

次の表に、シナリオごとのクラスター クォーラムの結果の概要を示します。

| サーバー ノード | 1 つのサーバー ノード障害に耐えることができる | 1 つのサーバー ノード障害に耐えた後、別の障害にも耐えることができる | 同時に発生する 2 つのサーバー ノード障害に耐えることができる |
|--------------|-------------------------------------|---------------------------------------------------|----------------------------------------------------|
| 2            | 50/50                               | いいえ                                                | いいえ                                                 |
| 2 + 監視  | はい                                 | いいえ                                                | いいえ                                                 |
| 3            | はい                                 | 50/50                                             | いいえ                                                 |
| 3 + 監視  | はい                                 | はい                                               | いいえ                                                 |
| 4            | はい                                 | はい                                               | 50/50                                              |
| 4 + 監視  | はい                                 | はい                                               | はい                                                |
| 5 以上  | はい                                 | はい                                               | はい                                                |

### <a name="cluster-quorum-recommendations"></a>クラスター クォーラムでの推奨事項

- 2 つのノードがある場合、監視は**必須**です。
- 3 つまたは 4 つのノードがある場合は、監視を**強く推奨**します。
- インターネットに接続している場合は、 **[クラウド監視](../../failover-clustering/deploy-cloud-witness.md)** を使用します。
- 他のマシンおよびファイル共有のある IT 環境の場合は、ファイル共有監視を使用します。

## <a name="how-cluster-quorum-works"></a>クラスター クォーラムのしくみ

ノードで障害が発生した場合、またはノードのサブセットが別のサブセットとの接続を失った場合、オンライン状態を維持するには、残りのノードがクラスターの "*過半数*" を占めることを確認する必要があります。 これを確認できない場合、これらはオフラインになります。

ただし、"*過半数*" の概念は、ノードの合計数が奇数 (たとえば、5 つのノードのうち 3 つのノード) である場合にのみ正常に機能します。 それでは、ノード数が偶数であるクラスター (たとえば、4 つのノードを持つクラスター) の場合はどうなるでしょうか。

クラスターで "*投票の合計数*" を奇数にできる方法は 2 つあります。

1. まず、追加の投票として "*監視*" を追加することにより、1 つ "*増やす*" ことができます。 これには、ユーザーによる設定が必要です。
2.    または、1 つのノードの投票をゼロにすることで、1 つ "*減らす*" ことができます (必要に応じて、自動的に実行されます)。

残りのノードが "*過半数*" であることが正常に確認されたら、"*過半数*" の定義が残りのノード間でのみ更新されます。 これにより、クラスターでは、1 つのノードが停止し、その後別のクラスターが順次停止することを許容できます。 連続する障害の発生後に適用される、この "*投票の合計数*" の概念は "***動的クォーラム***" と呼ばれます。

### <a name="dynamic-witness"></a>動的監視

動的監視では、"*投票の合計数*" が奇数になるように監視の投票が切り替えられます。 投票数が奇数の場合、監視は投票を持ちません。 投票数が偶数の場合、監視は投票を持ちます。 動的監視を使用すると、監視の障害が原因でクラスターが停止するリスクが大幅に減少します。 クラスターでは、クラスター内で使用可能な投票ノード数に基づいて、監視の投票を使用するかどうかが決定されます。

動的クォーラムは、以下で説明する方法で動的監視と連携します。

### <a name="dynamic-quorum-behavior"></a>動的クォーラムの動作

- ノード数が**偶数**であり、監視がない場合、"*1 つのノードの投票がゼロに設定されます*"。 たとえば、4 つのノードのうち 3 つだけが投票を取得して "*投票の合計数*" が 3 である場合、投票を持つ 2 つのノードが残ると過半数と見なされます。
- ノード数が**奇数**であり、監視がない場合、*すべてが投票を持ちます*。
- ノード数が**偶数**であり、監視がある場合、"*監視が投票する*" ため、合計は奇数になります。
- ノード数が**奇数**であり、監視がある場合、"*監視は投票しません*"。

動的クォーラムにより、ノードに動的に投票を割り当て、投票の過半数を失うことを回避できます。また、クラスターを 1 つのノード (最後に残ったもの) で実行できます。 例として、4 つのノードのクラスターを見ていきましょう。 クォーラムでは、3 票が必要であるとします。

この場合、クラスターは 2 つのノードが停止するとダウンします。

![それぞれが投票を持つ、クラスターの 4 つのノードを示す図](media/understand-quorum/dynamic-quorum-base.png)

ただし、動的クォーラムではこれが発生するのを回避します。 クォーラムで必要とされる "*投票の合計数*" は、使用可能なノードの数に基づいて決定されるようになりました。 このため、動的クォーラムでは、3 つのノードが停止してもクラスターは稼働状態を維持します。

![クラスターの 4 つのノードを示す図。一度に 1 つのノードに障害が発生し、それぞれの障害後に必要な投票数が調整される。](media/understand-quorum/dynamic-quorum-step-through.png)

上記のシナリオは、記憶域スペース ダイレクトが有効になっていない一般的なクラスターに適用されます。 ただし、記憶域スペース ダイレクトが有効になっている場合、クラスターは 2 つのノードの障害のみをサポートできます。 これについては、[プール クォーラムに関するセクション](#pool-quorum-overview)で詳しく説明します。

### <a name="examples"></a>例

#### <a name="two-nodes-without-a-witness"></a>監視なしの 2 つのノード。
**1 票**の合計から投票の "*過半数*" が決定されるように、1 つのノードの投票がゼロに設定されます。 投票しないノードが予期せず停止した場合、残りのノードは 1/1 となり、クラスターは存続します。 投票するノードが予期せず停止した場合、残りのノードは 0/1 となり、クラスターは停止します。 投票するノードの電源が正常に切断されると、投票はもう一方のノードに譲渡され、クラスターは存続します。 ***監視を構成することが重要であるのは、このためです。***

![監視なしの 2 つのノードの例で説明したクォーラム](media/understand-quorum/2-node-no-witness.png)

- 1 つのサーバー障害に耐えることができる:**50% の確率**。
- 1 つのサーバー障害に耐えた後、別の障害にも耐えることができる:**いいえ**。
- 同時に発生する 2 つのサーバー障害に耐えることができる:**いいえ**。

#### <a name="two-nodes-with-a-witness"></a>監視ありの 2 つのノード。
両方のノードが投票し、さらに監視も投票します。これにより、**3 票**の合計から "*過半数*" が決定されます。 いずれかのノードが停止した場合、残りのノードは 2/3 となり、クラスターは存続します。

![監視ありの 2 つのノードの例で説明したクォーラム](media/understand-quorum/2-node-witness.png)

- 1 つのサーバー障害に耐えることができる:**はい**。
- 1 つのサーバー障害に耐えた後、別の障害にも耐えることができる:**いいえ**。
- 同時に発生する 2 つのサーバー障害に耐えることができる:**いいえ**。

#### <a name="three-nodes-without-a-witness"></a>監視なしの 3 つのノード。
すべてのノードが投票するため、"*過半数*" は **3 票**の合計から決定されます。 いずれかのノードが停止した場合、残りのノードは 2/3 となり、クラスターは存続します。 この時点で、クラスターは監視なしの 2 つのノードとなり、シナリオ 1 になります。

![監視なしの 3 つのノードの例で説明したクォーラム](media/understand-quorum/3-node-no-witness.png)

- 1 つのサーバー障害に耐えることができる:**はい**。
- 1 つのサーバー障害に耐えた後、別の障害にも耐えることができる:**50% の確率**。
- 同時に発生する 2 つのサーバー障害に耐えることができる:**いいえ**。

#### <a name="three-nodes-with-a-witness"></a>監視ありの 3 つのノード。
すべてのノードが投票するため、監視は最初は投票しません。 "*過半数*" は **3 票**の合計から決定されます。 1 つの障害が発生した後に、クラスターには監視ありの 2 つのノードが残ります。これで、シナリオ 2 に戻ります。 これで、2 つのノードとなり、監視が投票します。

![監視ありの 3 つのノードの例で説明したクォーラム](media/understand-quorum/3-node-witness.png)

- 1 つのサーバー障害に耐えることができる:**はい**。
- 1 つのサーバー障害に耐えた後、別の障害にも耐えることができる:**はい**。
- 同時に発生する 2 つのサーバー障害に耐えることができる:**いいえ**。

#### <a name="four-nodes-without-a-witness"></a>監視なしの 4 つのノード
1 つのノードの投票がゼロに設定され、"*過半数*" は **3 票**の合計から決定されます。 1 つの障害が発生した後に、クラスターは 3 つのノードになり、シナリオ 3 になります。

![監視なしの 4 つのノードの例で説明したクォーラム](media/understand-quorum/4-node-no-witness.png)

- 1 つのサーバー障害に耐えることができる:**はい**。
- 1 つのサーバー障害に耐えた後、別の障害にも耐えることができる:**はい**。
- 同時に発生する 2 つのサーバー障害に耐えることができる:**50% の確率**。

#### <a name="four-nodes-with-a-witness"></a>監視ありの 4 つのノード。
すべてのノードと監視が投票し、**5 票**の合計から "*過半数*" が決定されます。 1 つの障害が発生した後、シナリオ 4 になります。 2 つの障害が同時に発生すると、シナリオ 2 になります。

![監視ありの 4 つのノードの例で説明したクォーラム](media/understand-quorum/4-node-witness.png)

- 1 つのサーバー障害に耐えることができる:**はい**。
- 1 つのサーバー障害に耐えた後、別の障害にも耐えることができる:**はい**。
- 同時に発生する 2 つのサーバー障害に耐えることができる:**はい**。

#### <a name="five-nodes-and-beyond"></a>5 つ以上のノード。
すべてのノードが投票するか、1 つを除いてすべてが投票し、合計が奇数になるようにします。 記憶域スペース ダイレクトでは 2 つを越えるノードの停止を処理できないため、この時点で監視は不要であり、役に立ちません。

![5 つ以上のノードの例で説明したクォーラム](media/understand-quorum/5-nodes.png)

- 1 つのサーバー障害に耐えることができる:**はい**。
- 1 つのサーバー障害に耐えた後、別の障害にも耐えることができる:**はい**。
- 同時に発生する 2 つのサーバー障害に耐えることができる:**はい**。

クォーラムのしくみを理解したところで、クォーラム監視の種類を見てみましょう。

### <a name="quorum-witness-types"></a>クォーラム監視の種類

フェールオーバー クラスタリングでは、次の 3 種類のクォーラム監視がサポートされています。

- **[クラウド監視](../../failover-clustering/deploy-cloud-witness.md)** - クラスターのすべてのノードからアクセス可能な Azure の Blob Storage。 クラスタリング情報は witness.log ファイルに保持されますが、クラスター データベースのコピーは保存されません。
- **ファイル共有監視** - Windows Server を実行しているファイル サーバー上で構成される SMB ファイル共有。 クラスタリング情報は witness.log ファイルに保持されますが、クラスター データベースのコピーは格納されません。
- **ディスク監視** - クラスターの使用可能記憶域グループ内にある小さいクラスター ディスク。 このディスクは可用性が高く、ノード間でフェールオーバーできます。 クラスター データベースのコピーが格納されます。  "***記憶域スペース ダイレクトでは、ディスク監視はサポートされていません***"。

## <a name="pool-quorum-overview"></a>プール クォーラムの概要

ここまでは、クラスター レベルで動作するクラスター クォーラムについて説明しました。 次に、プール レベルで動作する (つまり、ノードとドライブが停止した場合、プールが稼働状態を維持できる) プール クォーラムについて詳しく見ていきましょう。 記憶域プールは、クラスター化と非クラスター化の両方のシナリオで使用するように設計されているため、異なるクォーラム メカニズムを持ちます。

次の表に、シナリオごとのプール クォーラムの結果の概要を示します。

| サーバー ノード | 1 つのサーバー ノード障害に耐えることができる | 1 つのサーバー ノード障害に耐えた後、別の障害にも耐えることができる | 同時に発生する 2 つのサーバー ノード障害に耐えることができる |
|--------------|-------------------------------------|---------------------------------------------------|----------------------------------------------------|
| 2            | いいえ                                  | いいえ                                                | いいえ                                                 |
| 2 + 監視  | はい                                 | いいえ                                                | いいえ                                                 |
| 3            | はい                                 | いいえ                                                | いいえ                                                 |
| 3 + 監視  | はい                                 | いいえ                                                | いいえ                                                 |
| 4            | はい                                 | いいえ                                                | いいえ                                                 |
| 4 + 監視  | はい                                 | はい                                               | はい                                                |
| 5 以上  | はい                                 | はい                                               | はい                                                |

## <a name="how-pool-quorum-works"></a>プール クォーラムのしくみ

ドライブで障害が発生した場合、またはドライブのサブセットが別のサブセットとの接続を失った場合、オンライン状態を維持するには、残りのドライブがプールの "*過半数*" を占めることを確認する必要があります。 これを確認できない場合、これらはオフラインになります。 プールは、クォーラム用に十分なディスク (50% + 1) があるかどうかに基づいて、オフラインになるか、またはオンライン状態を維持するエンティティです。 プール リソースの所有者 (アクティブなクラスター ノード) をこの +1 にすることができます。

ただし、プール クォーラムのしくみはクラスター クォーラムとは次の点で異なります。

- プールでは、クラスター内の 1 つのノードを監視として、つまり半分のドライブが停止した場合に稼働状態を維持できるかどうかの判断基準として使用します (このノードがプール リソースの所有者です)
- プールには、動的クォーラムはありません
- プールには、投票を削除する独自の機能は実装されません

### <a name="examples"></a>例

#### <a name="four-nodes-with-a-symmetrical-layout"></a>対称レイアウトの 4 つのノード。
16 個のドライブはそれぞれ 1 つの投票を持ち、ノード 2 にも 1 つの投票があります (これがプール リソースの所有者であるため)。 "*過半数*" は **16 票**の合計から決定されます。 ノード 3 と 4 が停止した場合、残りのサブセットには 8 個のドライブとプール リソースの所有者があるため、9/16 票になります。 そのため、プールは存続します。

![プール クォーラム 1](media/understand-quorum/pool-1.png)

- 1 つのサーバー障害に耐えることができる:**はい**。
- 1 つのサーバー障害に耐えた後、別の障害にも耐えることができる:**はい**。
- 同時に発生する 2 つのサーバー障害に耐えることができる:**はい**。

#### <a name="four-nodes-with-a-symmetrical-layout-and-drive-failure"></a>対称レイアウトでドライブに障害が発生している 4 つのノード。
16 個のドライブはそれぞれ 1 つの投票を持ち、ノード 2 にも 1 つの投票があります (これがプール リソースの所有者であるため)。 "*過半数*" は **16 票**の合計から決定されます。 最初に、ドライブ 7 が停止します。 ノード 3 と 4 が停止した場合、残りのサブセットには 7 個のドライブとプール リソースの所有者があるため、8/16 票になります。 ここで、プールには過半数がないため停止します。

![プール クォーラム 2](media/understand-quorum/pool-2.png)

- 1 つのサーバー障害に耐えることができる:**はい**。
- 1 つのサーバー障害に耐えた後、別の障害にも耐えることができる:**いいえ**。
- 同時に発生する 2 つのサーバー障害に耐えることができる:**いいえ**。

#### <a name="four-nodes-with-a-non-symmetrical-layout"></a>非対称レイアウトの 4 つのノード。
24 個のドライブはそれぞれ 1 つの投票を持ち、ノード 2 にも 1 つの投票があります (これがプール リソースの所有者であるため)。 "*過半数*" は **24 票**の合計から決定されます。 ノード 3 と 4 が停止した場合、残りのサブセットには 8 個のドライブとプール リソースの所有者があるため、9/24 票になります。 ここで、プールには過半数がないため停止します。

![プール クォーラム 3](media/understand-quorum/pool-3.png)

- 1 つのサーバー障害に耐えることができる:**はい**。
- 1 つのサーバー障害に耐えた後、別の障害にも耐えることができる: **場合による** (ノード 3 と 4 が両方とも停止した場合は存続できないが、他のすべてのシナリオでは存続できる)。
- 同時に発生する 2 つのサーバー障害に耐えることができる: **場合による** (ノード 3 と 4 が両方とも停止した場合は存続できないが、他のすべてのシナリオでは存続できる)。

### <a name="pool-quorum-recommendations"></a>プール クォーラムでの推奨事項

- クラスター内の各ノードを必ず対称 (各ノードに同じ数のドライブがある) にします。
- ノード障害に耐性を持ち、仮想ディスクがオンライン状態を維持できるように、3 方向ミラーまたはデュアル パリティを有効にします。 詳細については、[ボリュームのガイダンスページ](plan-volumes.md)を参照してください。
- 2 つを越えるノードが停止したか、または 2 つのノードと別のノードの 1 つのディスクが停止した場合、ボリュームはそのデータの 3 つのコピーすべてにアクセスできなくなるため、オフラインになり、使用できなくなります。 ボリューム内のすべてのデータの回復性を最大限に高めるには、迅速にサーバーを復旧するかディスクを交換することをお勧めします。

## <a name="more-information"></a>詳細情報

- [クォーラムを構成して管理する](../../failover-clustering/manage-cluster-quorum.md)
- [クラウド監視を展開する](../../failover-clustering/deploy-cloud-witness.md)
