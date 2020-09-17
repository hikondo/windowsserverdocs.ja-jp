---
title: Hyper-v で標準チェックポイントまたは運用チェックポイントを選択する
description: 標準チェックポイントまたは運用チェックポイントを使用するように仮想マシンを構成する手順について説明します。
ms.topic: article
ms.assetid: 92bb573b-03b7-470e-b72e-e35edf52b349
ms.author: benarm
author: BenjaminArmstrong
ms.date: 10/04/2016
ms.openlocfilehash: 00a3c8d94fc18d180faa8927b33b90dc98854da0
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746477"
---
# <a name="choose-between-standard-or-production-checkpoints-in-hyper-v"></a>Hyper-v で標準チェックポイントまたは運用チェックポイントを選択する

>適用対象: Windows 10、Windows Server 2016、Microsoft Hyper-V Server 2016、Windows Server 2019、Microsoft Hyper-V Server 2019


Windows Server 2016 と Windows 10 以降では、各仮想マシンの標準チェックポイントと運用チェックポイントのどちらかを選択できます。 運用チェックポイントは、新しい仮想マシンの既定値です。

- 運用チェックポイントは、仮想マシンの "特定の時点" のイメージで、後ですべての運用環境のワークロードで完全にサポートされるように復元できます。 これは、保存された状態を利用する代わりに、ゲスト内のバックアップ技術を利用してチェックポイントを作成することで行います。

- 標準チェックポイントは、実行中の仮想マシンの状態、データ、およびハードウェアの構成をキャプチャします。これは、開発およびテストのシナリオでの使用を目的としています。 標準チェックポイントは、問題のトラブルシューティングを行うために、実行中の仮想マシンの特定の状態または条件を再作成する必要がある場合に便利です。

  ## <a name="change-checkpoints-to-production-or-standard-checkpoints"></a>チェックポイントを運用または標準チェックポイントに変更する

1.  **Hyper-v マネージャー**で、仮想マシンを右クリックし、[**設定**] をクリックします。

2.  [ **管理** ] セクションで、[ **チェックポイント**] を選択します。

3.  運用チェックポイントまたは標準チェックポイントのいずれかを選択します。

    運用チェックポイントを選択した場合は、運用チェックポイントを取得できない場合に、ホストが標準チェックポイントを取得するかどうかを指定することもできます。 このチェックボックスをオフにして、運用チェックポイントを取得できない場合、チェックポイントは作成されません。

4.  チェックポイントの構成ファイルを別の場所に保存する場合は、[ **チェックポイントファイルの場所** ] セクションで変更します。

5.  [ **適用** ] をクリックして変更を保存します。 完了したら、[ **OK** ] をクリックしてダイアログボックスを閉じます。

> [!NOTE]
> Active Directory Domain Services ロール (ドメインコントローラー) または Active Directory ライトウェイトディレクトリサービスロールを実行しているゲストでは、 **運用チェックポイント** のみがサポートされます。

## <a name="additional-references"></a>その他の参照情報

-   [実稼働のチェックポイント](../What-s-new-in-Hyper-V-on-Windows.md#production-checkpoints-new)

-   [チェックポイントを有効または無効にする](Enable-or-disable-checkpoints-in-Hyper-V.md)



