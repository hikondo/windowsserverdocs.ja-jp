---
title: 記憶域レポートを構成する
description: この記事では、記憶域レポートの既定のパラメーターを構成する方法を説明します。
ms.date: 7/7/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 94d1b75bba4edac5ad8df80adb13d95a7b8dec39
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "85474159"
---
# <a name="configure-storage-reports"></a>記憶域レポートを構成する

> 適用対象: Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2

記憶域レポートの既定のパラメーターを構成することができます。 これらの既定のパラメーターは、クォータまたはファイル スクリーン処理イベント発生時に生成されるインシデント レポートに使用されます。 また、スケジュールされたレポートやオン デマンドのレポートにも使用され、これらのレポートの特定のプロパティを定義する際に既定のパラメーターを上書きできます。

> [!Important]
> 1 種類のレポートについて既定のパラメーターを変更すると、その既定の設定を使用するすべてのインシデント レポートおよび既存のスケジュールされたレポート タスクに変更が反映されます。

## <a name="to-configure-the-default-parameters-for-storage-reports"></a>記憶域レポートの既定のパラメーターを構成するには

1. コンソール ツリーで、**[ファイル サーバー リソース マネージャー]** を右クリックし、**[オプションの構成]** をクリックします。 [**ファイル サーバー リソース マネージャーのオプション**] ダイアログ ボックスが開きます。

2. **[記憶域レポート]** タブの **[既定のパラメーターを構成する]** で、変更するレポートの種類を選択します。

3. [**パラメーターの編集**] をクリックします。

4. 選択したレポートの種類に応じて、異なるレポート パラメーターが編集できるようになります。 必要なすべての変更を行ったら、**[OK]** をクリックし、そのレポートの種類の既定のパラメーターとしてそれらを保存します。

5.  編集対象の各レポートの種類に対し、手順 2 ～ 4 を繰り返します。

6. すべてのレポートについて、既定のパラメーターの一覧を表示するには、**[レポートの表示]** をクリックします。 次に、**[閉じる]** をクリックします。

7.  **[OK]** をクリックします。

## <a name="additional-references"></a>その他のリファレンス

-   [ファイル サーバー リソース マネージャーのオプションを設定する](setting-file-server-resource-manager-options.md)
-   [記憶域レポートの管理](storage-reports-management.md)