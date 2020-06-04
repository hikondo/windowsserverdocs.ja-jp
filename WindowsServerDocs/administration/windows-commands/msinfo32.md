---
title: msinfo32
description: Msinfo32 コマンドのリファレンストピック。システム情報ツールを開き、ローカルコンピューター上のハードウェア、システムコンポーネント、およびソフトウェア環境の包括的なビューを表示します。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a38f31d7-1766-4103-becc-9d0b87c2826d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d6a97902d9988260a840d236e197d7361bcd3882
ms.sourcegitcommit: 5e313a004663adb54c90962cfdad9ae889246151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84354434"
---
# <a name="msinfo32"></a>msinfo32

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

システム情報ツールを開き、ローカルコンピューター上のハードウェア、システムコンポーネント、およびソフトウェア環境の包括的なビューを表示します。

システム情報のカテゴリによっては、大量のデータが含まれている場合があります。 **Start/wait**コマンドを使用すると、これらのカテゴリのレポートパフォーマンスを最適化できます。 詳細については、「[システム情報](https://technet.microsoft.com/library/cc783305(v=ws.10).aspx)」を参照してください。

## <a name="syntax"></a>構文

```
msinfo32 [/pch] [/nfo <path>] [/report <path>] [/computer <computername>] [/showcategories] [/category <categoryID>] [/categories {+<categoryID>(+<categoryID>)|+all(-<categoryID>)}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<path>` | *C:\Folder1\File1.xxx*の形式で開くファイルを指定します。 *C*はドライブ文字、 *Folder1*はフォルダー、 *File1*はファイル名、 *xxx*はファイル名拡張子です。<p>このファイルには、 **.nfo**、 **.xml**、 **.txt**、または **.cab**ファイルを指定できます。 |
| `<computername>` | ターゲットコンピューターまたはローカルコンピューターの名前を指定します。 UNC 名、IP アドレス、または完全なコンピューター名を指定できます。 |
| `<categoryID>` | カテゴリ項目の ID を指定します。 **/Showcategories**を使用して、カテゴリ ID を取得できます。 |
| /pch | システム情報ツールのシステム履歴ビューを表示します。 |
| /nfo | エクスポートされたファイルを **.nfo**ファイルとして保存します。 *Path*に指定されているファイル名の末尾が **.nfo**でない場合、 **.nfo**拡張子はファイル名に自動的に追加されます。 |
| /report」 | ファイルを*パス*にテキストファイルとして保存します。 ファイル名は*パス*に表示されているとおりに保存されます。 .Txt 拡張子は、path に指定されていない限り、ファイルに追加されません。 |
| /コンピューター | 指定されたリモートコンピューターのシステム情報ツールを起動します。 リモートコンピューターにアクセスするには、適切なアクセス許可が必要です。 |
| /showcategories | 表示またはローカライズされた名前を表示するのではなく、使用可能なすべてのカテゴリ Id を使用してシステム情報ツールを起動します。 たとえば、[ソフトウェア環境] カテゴリが [ **Swenv** ] カテゴリとして表示されます。 |
| /category | 指定されたカテゴリでシステム情報を開始します。 使用可能なカテゴリ Id の一覧を表示するには、 **/showcategories**を使用します。 |
| /カテゴリ | 指定されたカテゴリまたはカテゴリのみを含むシステム情報を開始します。 また、選択したカテゴリに出力を制限します。 使用可能なカテゴリ Id の一覧を表示するには、 **/showcategories**を使用します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

### <a name="examples"></a>例

使用可能なカテゴリ Id の一覧を表示するには、次のように入力します。

```
msinfo32 /showcategories
```

読み込まれたモジュールを除く、利用可能なすべての情報を含むシステム情報ツールを起動するには、次のように入力します。

```
msinfo32 /categories +all -loadedmodules
```

システムの**概要**情報を表示し、[**システムの概要**] カテゴリに情報が含まれている .nfo ファイルを作成するには、次のように入力し*ます。*

```
msinfo32 /nfo syssum.nfo /categories +systemsummary
```

リソースの競合情報を表示し、*リソースの競合*に関する情報が含まれている .nfo ファイルを作成するには、次のように入力します。

```
msinfo32 /nfo conflicts.nfo /categories +componentsproblemdevices+resourcesconflicts+resourcesforcedhardware
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
