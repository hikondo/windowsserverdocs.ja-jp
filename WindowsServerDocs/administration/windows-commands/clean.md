---
title: clean
description: Diskpart の clean コマンドの参照記事。フォーカスがあるディスクからすべてのパーティションまたはボリュームのフォーマットを削除します。
ms.topic: reference
ms.assetid: 9bbe6fd3-e07e-487b-9035-910957a1d326
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 82026520c456c76823993d34a4fb09bcd4b79808
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89629650"
---
# <a name="clean"></a>clean

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

フォーカスがあるディスクからすべてのパーティションまたはボリュームのフォーマットを削除します。

>[!NOTE]
> このコマンドの PowerShell バージョンについては、「 [clear-disk コマンド](/powershell/module/storage/clear-disk)」を参照してください。

## <a name="syntax"></a>構文

```
clean [all]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| all | ディスク上のすべてのセクターをゼロに設定し、ディスクに含まれるすべてのデータを完全に削除することを指定します。 |

#### <a name="remarks"></a>注釈

- マスターブートレコード (MBR) ディスクでは、MBR パーティション情報と隠しセクター情報のみが上書きされます。

- GUID パーティションテーブル (gpt) ディスクでは、gpt パーティション情報 (保護 MBR を含む) が上書きされます。 隠しセクター情報はありません。

- この操作を成功させるには、ディスクを選択する必要があります。 使用して、 **select ディスク** コマンド ディスクを選択し、それにフォーカスをします。

## <a name="examples"></a>例

選択したディスクからすべてのフォーマットを削除するには、次のように入力します。

```
clean
```

## <a name="additional-references"></a>その他の参照情報

- [ディスクの消去コマンド](/powershell/module/storage/clear-disk)

- [コマンド ライン構文の記号](command-line-syntax-key.md)
