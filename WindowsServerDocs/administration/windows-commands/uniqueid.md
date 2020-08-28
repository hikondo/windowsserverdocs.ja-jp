---
title: uniqueid
description: フォーカスがあるディスクの GUID パーティションテーブル (GPT) 識別子またはマスターブートレコード (MBR) 署名を表示または設定する uniqueid の参照記事。
ms.topic: reference
ms.assetid: 64235a4a-b91c-46da-b9b0-68ee90571c2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 42b3bcc50ad5f13a941a0ff81a7c74f40b45b48d
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89032197"
---
# <a name="uniqueid"></a>uniqueid

フォーカスがあるディスクの GUID パーティションテーブル (GPT) 識別子またはマスターブートレコード (MBR) 署名を表示または設定します。

> [!IMPORTANT]
> この DiskPart コマンドは、Windows Vista のどのエディションでも使用できません。

## <a name="syntax"></a>構文

```
uniqueid disk [id={<dword> | <GUID>}] [noerr]
```

### <a name="parameters"></a>パラメーター

|  パラメーター   |                                                                                             説明                                                                                              |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id = {\<dword> |                                                                                               <GUID>}                                                                                                |
|    noerr     | スクリプト専用です。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

## <a name="remarks"></a>解説

-   このコマンドは、ベーシックディスクとダイナミックディスクで機能します。
-   このコマンドを成功させるには、ディスクを選択してください。 使用して、 **select ディスク** コマンド ディスクを選択し、それにフォーカスをします。

## <a name="examples"></a>例

フォーカスがある MBR ディスクの署名を表示するには、次のように入力します。
```
uniqueid disk
```
5f1b2c36 にフォーカスがある MBR ディスクの署名を設定するには、次のように入力します。
```
uniqueid disk id=5f1b2c36
```
Baf784e7-6bbd-4cfb-aaac-e86c96e166ee にフォーカスがある GPT ディスクの識別子を設定するには、次のように入力します。
```
uniqueid disk id=baf784e7-6bbd-4cfb-aaac-e86c96e166ee
```

## <a name="additional-references"></a>その他の参照情報

