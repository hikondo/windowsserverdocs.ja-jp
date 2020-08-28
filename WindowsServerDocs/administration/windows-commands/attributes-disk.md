---
title: attributes disk
description: ディスクの属性を表示、設定、または消去する disk コマンドの属性に関するリファレンス記事です。
ms.topic: reference
ms.assetid: eed57071-c1c6-4394-9542-62b52a878c92
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 72b4a99c36085062441a7a8751a065dad1dd0c51
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89029200"
---
# <a name="attributes-disk"></a>attributes disk

ディスクの属性を表示、設定、またはクリアします。 このコマンドを使用してディスクの現在の属性を表示する場合、スタートアップディスク属性は、コンピューターを起動するために使用されるディスクを表します。 ダイナミックミラーの場合は、ブートボリュームのブートプレックスを含むディスクが表示されます。

> [!IMPORTANT]
> [ **ディスクの属性** ] コマンドを正常に実行するには、ディスクを選択する必要があります。 使用して、 **select ディスク** コマンド ディスクを選択し、それにフォーカスをします。

## <a name="syntax"></a>構文

```
attributes disk [{set | clear}] [readonly] [noerr]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| set | フォーカスがあるディスクの指定された属性を設定します。 |
| オフ | フォーカスがあるディスクの指定された属性をクリアします。 |
| readonly | ディスクが読み取り専用であることを指定します。 |
| noerr | スクリプト専用です。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

## <a name="examples"></a>例

選択したディスクの属性を表示するには、次のように入力します。

```
attributes disk
```

選択したディスクを読み取り専用に設定するには、次のように入力します。

```
attributes disk set readonly
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ディスクの選択コマンド](select-disk.md)
