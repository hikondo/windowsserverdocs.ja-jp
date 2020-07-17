---
title: bitsadmin setpriority
description: 指定されたジョブの優先度を設定する bitsadmin setpriority コマンドの参照記事です。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 90788363-01a2-4d7c-a560-a3eba45b5e9e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 07afd9c636a5dbcd4e70de71b3a6f515e7e02bae
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927594"
---
# <a name="bitsadmin-setpriority"></a>bitsadmin setpriority

指定されたジョブの優先順位を設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setpriority <job> <priority>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| priority | ジョブの優先順位を設定します。次に例を示します。<ul><li>FOREGROUND</li><li>HIGH</li><li>NORMAL</li><li>LOW</li></ul> |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの優先順位を normal に設定するには、次のようにします。

```
bitsadmin /setpriority myDownloadJob NORMAL
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
