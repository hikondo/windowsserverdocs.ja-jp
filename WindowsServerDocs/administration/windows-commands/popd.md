---
title: popd
description: Pnputil コマンドの参照記事。現在のディレクトリを、pushd コマンドによって最後に格納されたディレクトリに変更します。
ms.topic: reference
ms.assetid: 8a4c52d5-9fd1-4eac-9c0c-5767b25728ed
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/11/2018
ms.openlocfilehash: 4884e294f878a55125a035d7113ce857e1964634
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633653"
---
# <a name="popd"></a>popd

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

**Popd**コマンドは、現在のディレクトリを、 **pushd**コマンドによって最後に格納されたディレクトリに変更します。

**Pushd**コマンドを使用するたびに、使用するために1つのディレクトリが格納されます。 ただし、 **pushd** コマンドを複数回使用して、複数のディレクトリを格納することができます。 ディレクトリは仮想スタックに連続して格納されるため、 **pushd** コマンドを1回使用すると、コマンドを使用するディレクトリがスタックの一番下に配置されます。 コマンドを再度使用すると、2つ目のディレクトリが最初のディレクトリの上に配置されます。 このプロセスは、 **pushd** コマンドを使用するたびに繰り返されます。

**Popd**コマンドを使用すると、スタックの一番上にあるディレクトリが削除され、現在のディレクトリがそのディレクトリに変更されます。 **Popd**コマンドを再度使用すると、スタック上の次のディレクトリが削除されます。 コマンド拡張機能が有効になっている場合は、 **pushd**コマンドによって作成されたドライブ文字の割り当てが削除**されます**。

## <a name="syntax"></a>構文

```
popd
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /? | コマンド プロンプトにヘルプを表示します。 |

### <a name="examples"></a>例

バッチプログラムが実行されたディレクトリから現在のディレクトリを変更し、それを元に戻すには、次のように入力します。

```
@echo off
rem This batch file deletes all .txt files in a specified directory
pushd %1
del *.txt
popd
cls
echo All text files deleted in the %1 directory
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [pushd](pushd.md)
