---
title: サーバー クリーンアップ ウィザード
description: Windows Server Update Service (WSUS) トピック-サーバークリーンアップウィザードを使用してディスク領域を管理する方法
ms.topic: article
ms.assetid: 7c351797-2716-4442-a668-60d5b4e77751
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 967df91afdf7bab1f6fd4d6c1daabcf04f104d23
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624405"
---
# <a name="the-server-cleanup-wizard"></a>サーバー クリーンアップ ウィザード

>適用先:Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サーバークリーンアップウィザードはユーザーインターフェイスに統合されており、ディスク領域の管理に使用できます。 このウィザードでは、次の操作を実行できます。

- 使用されていない更新プログラムを削除し、更新プログラムの改訂がすべての以前の更新プログラムおよび承認されていない更新プログラムの改訂を削除します。

- サーバーの削除に接続しないコンピューターの 30 日間以上で、サーバー通信していないすべてのクライアント コンピューターを削除します。

- 不要な更新プログラム ファイルの削除が更新またはダウン ストリーム サーバーによって、不要なファイルを更新すべてを削除します。

- 有効期限が切れた更新プログラムの拒否マイクロソフトが期限切れになったされているすべての更新プログラムの拒否します。

- 拒否は、次のすべての条件を満たすすべての更新プログラムを拒否します。

  -   置き換えられる更新プログラムが必須ではありません。

  -   置き換えられる更新プログラムはしたサーバーの 30 日以上

  -   置き換えられる更新プログラムは必要に応じて、任意のクライアントによって現在報告しません。

  -   置き換えられる更新プログラムが展開されていない明示的にコンピューター グループに 90 日以上

  -   コンピューター グループにインストールの優先する更新プログラムを承認する必要があります。

  > [!WARNING]
  >  WSUS 階層では、最下位のダウンストリーム/レプリカ WSUS サーバーでクリーンアッププロセスを実行してから、階層を上に移動することを強くお勧めします。 すべてのダウンストリームサーバーでクリーンアップを実行する前に、アップストリームサーバーでクリーンアップを正しく実行しないと、アップストリームデータベースとダウンストリームデータベースに存在するデータが一致しなくなる可能性があります。 データの不一致が原因で、アップストリームサーバーとダウンストリームサーバーの間で同期エラーが発生する可能性があります。
  >
  > [!IMPORTANT]
  >  サーバークリーンアップウィザードを使用して不要なコンテンツを削除すると、Microsoft Update カタログサイトからダウンロードしたすべてのプライベート更新ファイルも削除されます。 これらのファイルは、サーバークリーンアップウィザードの実行後に再インポートする必要があります。

自動承認規則を使用して更新プログラムが承認されている場合、更新プログラムは承認済みの状態である可能性があり、サーバークリーンアップウィザードによって削除されることはありません。 承認済みの状態にある自動承認された更新プログラムを削除するには、WSUS 管理者は、[優先される更新プログラムの承認ステータス] を [承認されていません] に手動で設定する必要があります。これにより、サーバークリーンアップウィザードによる拒否の対象となります。 サーバークリーンアップウィザードを実行すると、新しい更新プログラムが承認され、更新プログラムを拒否済みとしてマークする前に、必要に応じて更新するクライアントシステムがまだ報告されていないことが確認されます。




