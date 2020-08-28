---
title: bitsadmin gettemporaryname
description: Bitsadmin gettemporary name コマンドの参照記事。ジョブ内の指定されたファイルの一時ファイル名を報告します。
ms.topic: reference
ms.assetid: 68925edc-a801-4292-a812-7471c4f60fdd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d9e03b00fa1885b89f25dab2781ce988aa0c5df8
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89034810"
---
# <a name="bitsadmin-gettemporaryname"></a>bitsadmin gettemporaryname

ジョブ内の指定されたファイルの一時ファイル名を報告します。

## <a name="syntax"></a>構文

```
bitsadmin /gettemporaryname <job> <file_index>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| file_index | 0から開始します。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのファイル2の一時ファイル名を報告するには、次のようにします。

```
bitsadmin /gettemporaryname myDownloadJob 1
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
