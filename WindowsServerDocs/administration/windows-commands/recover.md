---
title: 復元 (recover)
description: 'Windows コマンドに関するトピック * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf9be2e3-90c8-4773-a201-dc503b91948e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 415efe2d1e60ca70d68059b5702108440da735f3
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371770"
---
# <a name="recover"></a>復元 (recover)



正しくないか欠陥があるディスクから読み取り可能な情報を復元します。

このコマンドを使用する方法の例については、[例](#BKMK_examples)を参照してください。

## <a name="syntax"></a>構文

```
recover [<Drive>:][<Path>]<FileName>
```

## <a name="parameters"></a>パラメーター

|           パラメーター           |                                          説明                                          |
|-------------------------------|-----------------------------------------------------------------------------------------------|
| [\<Drive >:][<Path>] <FileName> | 回復するファイルの名前と場所を指定します。 *ファイル名* が必要です。 |
|              /?               |                             コマンド プロンプトにヘルプを表示します。                              |

## <a name="remarks"></a>コメント

-   **回復** コマンドは、ファイル、セクターごとを読み取り、データを正常なセクターから回復します。 不良セクターのデータは失われます。
-   によって報告された不良セクター **chkdsk** 操作用にディスクに作成されたときに"bad"が設定されました。 これらに問題ありません、および **回復** 影響しません。
-   ファイルを回復するときに不良セクターのすべてのデータが失われたために、一度に 1 つのファイルを回復する必要があります。
-   [回復] コマンドでは **&#42;** 、ワイルドカード文字 (および **?** ) は使用できません。 ファイル (および現在のディレクトリになっていない場合は、ファイルの場所) を指定する必要があります。

## <a name="BKMK_examples"></a>例

D ドライブに \Fiction ディレクトリに Story.txt ファイルを復元するには、次のように入力します。
```
recover d:\fiction\story.txt 
```

#### <a name="additional-references"></a>その他の参照情報

[コマンド ライン構文の記号](command-line-syntax-key.md)