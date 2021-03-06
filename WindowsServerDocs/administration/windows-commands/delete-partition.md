---
title: delete partition
description: '[パーティションの削除] コマンドの参照記事。フォーカスのあるパーティションを削除します。'
ms.topic: reference
ms.assetid: 65752312-cb16-46f6-870f-1b95c507b101
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2833039c9237a271910c43ff8acb7b8fb94828f1
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89628833"
---
# <a name="delete-partition"></a>delete partition

フォーカスがあるパーティションを削除します。 開始する前に、この操作を成功させるには、パーティションを選択する必要があります。 [[パーティションの選択](select-partition.md)] コマンドを使用してパーティションを選択し、それにフォーカスを移動します。

> [!WARNING]
> ダイナミックディスク上のパーティションを削除すると、ディスク上のすべてのダイナミックボリュームを削除し、データを破棄して、ディスクを破損した状態のままにすることができます。
>
> システムパーティション、ブートパーティション、またはアクティブなページングファイルやクラッシュダンプ情報が含まれているパーティションは削除できません。

## <a name="syntax"></a>構文

```
delete partition [noerr] [override]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| noerr | スクリプト専用です。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |
| override | パーティションの種類にかかわらず、DiskPart ですべてのパーティションを削除できるようにします。 通常、DiskPart では既知のデータパーティションのみを削除できます。 |

#### <a name="remarks"></a>注釈

- ダイナミックボリュームを削除するには、代わりに [ [ボリュームの削除](delete-volume.md) ] コマンドを常に使用します。

- パーティションはダイナミックディスクから削除できますが、作成することはできません。 たとえば、ダイナミック GPT ディスク上の認識されていない GUID パーティションテーブル (GPT) パーティションを削除することができます。 このようなパーティションを削除しても、結果として得られる空き領域が使用できなくなることはありません。 代わりに、このコマンドは、DiskPart の [clean](clean.md) コマンドを使用できない緊急の状況で、破損したオフラインダイナミックディスク上の領域を再利用できるようにするためのものです。

## <a name="examples"></a>例

フォーカスのあるパーティションを削除するには、次のように入力します。

```
delete partition
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [select partition](select-partition.md)

- [delete コマンド](delete.md)

- [ボリュームの削除コマンド](delete-volume.md)

- [clean コマンド](clean.md)
