---
title: autochk
description: Autochk コマンドの参照記事。コンピューターを起動したとき、およびファイルシステムの論理的な整合性の検証を開始する前に、Windows Server の前に実行されます。
ms.topic: reference
ms.assetid: 8787e6a3-f023-4ea5-b2d1-61c6876d8aff
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: acdb9330ca1b99578c43c98e30c647171413ddd2
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028930"
---
# <a name="autochk"></a>autochk

コンピューターが起動したとき、および Windows Server の前に、ファイルシステムの論理的な整合性の検証を開始するときに実行されます。

**Autochk.exe** は、NTFS ディスクだけで実行され、Windows Server が起動する前にのみ実行される **chkdsk** のバージョンです。 コマンドラインから**autochk**を直接実行することはできません。 代わりに、次のような状況で **autochk** が実行されます。

- ブートボリュームで **chkdsk** を実行しようとした場合。

- **Chkdsk**でボリュームを排他的に使用できない場合。

- ボリュームにダーティのフラグが設定されている場合。

## <a name="remarks"></a>解説

> [!WARNING]
> **Autochk**コマンドラインツールは、コマンドラインから直接実行することはできません。 代わりに、 **chkntfs** コマンドラインツールを使用して、起動時に **autochk** を実行する方法を構成します。
>
> - **Chkntfs**を **/x**パラメーターと共に使用すると、 **autochk**が特定のボリュームまたは複数のボリュームで実行されないようにすることができます。
>
> - **chkntfs.exe**コマンドラインツールと **/t**パラメーターを使用して、autochk 遅延時間を0秒から最大3日 (259200 秒) に変更します。 ただし、長い遅延とは、時間が経過するまで、またはキーを押して **autochk**をキャンセルするまで、コンピューターが起動しないことを意味します。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [chkdsk コマンド](chkdsk.md)

- [chkntfs コマンド](chkntfs.md)
