---
title: Fsutil fsinfo
description: すべてのドライブを一覧表示する、ドライブの種類を照会する、ボリューム情報を照会する、NTFS 固有のボリューム情報を照会する、ファイルシステムの統計情報を照会する、fsutil fsinfo コマンドの参照記事。
manager: dmoss
ms.author: toklima
author: toklima
ms.assetid: 7787a72e-a26b-415f-b700-a32806803478
ms.topic: reference
ms.date: 10/16/2017
ms.openlocfilehash: e921b8572b7d1d87a1baf40cfdbc955adce3ec01
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037370"
---
# <a name="fsutil-fsinfo"></a>fsutil fsinfo

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows 10、Windows Server 2012 R2、Windows 8.1、Windows Server 2012、Windows 8

すべてのドライブの一覧表示、ドライブの種類の照会、ボリューム情報の照会、NTFS 固有のボリューム情報の照会、またはファイルシステムの統計情報の照会を行います。

## <a name="syntax"></a>構文

```
fsutil fsinfo [drives]
fsutil fsinfo [drivetype] <volumepath>
fsutil fsinfo [ntfsinfo] <rootpath>
fsutil fsinfo [statistics] <volumepath>
fsutil fsinfo [volumeinfo] <rootpath>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- |------------ |
| ドライブ | コンピューター内のすべてのドライブを一覧表示します。 |
| drivetype が | ドライブに対してクエリを行い、その種類を一覧表示します (例: CD-ROM ドライブ)。 |
| ntfsinfo | 指定されたボリュームの NTFS 固有のボリューム情報を一覧表示、セクターの数、クラスターの総数、空きクラスター、および MFT ゾーンの開始と終了。 |
| sectorinfo | ハードウェアのセクターサイズとアラインメントに関する情報を一覧表示します。 |
| statistics | メタデータ、ログファイル、MFT の読み取りと書き込みなど、指定されたボリュームのファイルシステム統計情報を一覧表示します。 |
| volumeinfo | ファイルシステムなど、指定されたボリュームの情報を一覧表示します。ボリュームが大文字と小文字を区別するファイル名、ファイル名の unicode、ディスククォータ、または DirectAccess (DAX) ボリュームをサポートするかどうかを指定します。 |
| `<volumepath>:` | ドライブ文字を指定します (その後にコロンが続きます)。 |
| `<rootpath>:` | ルートドライブのドライブ文字 (後ろにコロンを付ける) を指定します。 |

### <a name="examples"></a>例

コンピューターのすべてのドライブを一覧表示するには、次のように入力します。

```
fsutil fsinfo drives
```

次のような出力が表示されます。

```
Drives: A:\ C:\ D:\ E:\
```

ドライブ C のドライブの種類に対してクエリを実行するには、次のように入力します。

```
fsutil fsinfo drivetype c:
```

クエリには次のような結果があります。

```
Unknown Drive
No such Root Directory
Removable Drive, for example floppy
Fixed Drive
Remote/Network Drive
CD-ROM Drive
Ram Disk
```

ボリューム E のボリューム情報を照会するには、次のように入力します。

```
fsinfo volumeinfo e:\
```

次のような出力が表示されます。

```
Volume Name : Volume
Serial Number : 0xd0b634d9
Max Component Length : 255
File System Name : NTFS
Supports Named Streams
Is DAX Volume
```

NTFS 固有のボリューム情報をドライブ F に照会するには、次のように入力します。

```
fsutil fsinfo ntfsinfo f:
```

次のような出力が表示されます。

```
NTFS Volume Serial Number : 0xe660d46a60d442cb
Number Sectors : 0x00000000010ea04f
Total Clusters : 0x000000000021d409
Mft Zone End : 0x0000000000004700
```

ファイルシステムの基になるハードウェアでセクター情報を照会するには、次のように入力します。

```
fsinfo sectorinfo d:
```

次のような出力が表示されます。

```
D:\>fsutil fsinfo sectorinfo d:
LogicalBytesPerSector : 4096
PhysicalBytesPerSectorForAtomicity : 4096
Trim Not Supported
DAX capable
```

ドライブ E のファイルシステム統計情報を照会するには、次のように入力します。

```
fsinfo statistics e:
```

次のような出力が表示されます。

```
File System Type : NTFS
Version : 1
UserFileReads : 75021
UserFileReadBytes : 1305244512
LogFileWriteBytes : 180936704
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [fsutil](fsutil.md)
