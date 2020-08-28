---
title: bitsadmin transfer
description: Bitsadmin transfer コマンドの参照記事。1つ以上のファイルを転送します。
ms.topic: reference
ms.assetid: fe302141-b33a-4a05-835e-dc4fc4db7d5a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 989c2ace5aa8cb0f123dec6f2ad490c1c8c778cd
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033350"
---
# <a name="bitsadmin-transfer"></a>bitsadmin transfer

1つ以上のファイルを転送します。 既定では、BITSAdmin サービスは、 **通常** の優先順位で実行されるダウンロードジョブを作成し、転送が完了するか重大なエラーが発生するまで、進行状況の情報を使用してコマンドウィンドウを更新します。

サービスは、すべてのファイルを正常に転送し、重大なエラーが発生した場合にジョブをキャンセルすると、ジョブを完了します。 ジョブにファイルを追加できない場合、または *種類* または *job_priority*に無効な値を指定した場合、サービスはジョブを作成しません。 複数のファイルを転送するには、複数のペアを指定し `<RemoteFileName>-<LocalFileName>` ます。 ペアはスペースで区切る必要があります。

> [!NOTE]
> 一時的なエラーが発生した場合、BITSAdmin コマンドは引き続き実行されます。 コマンドを終了するには、CTRL + C キーを押します。

## <a name="syntax"></a>構文

```
bitsadmin /transfer <name> [<type>] [/priority <job_priority>] [/ACLflags <flags>] [/DYNAMIC] <remotefilename> <localfilename>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| name | ジョブの名前。 このコマンドに GUID を指定することはできません。 |
| type | 省略可能。 ジョブの種類を設定します。次に例を示します。<ul><li>**ダウンロード.** 既定値。 ダウンロードジョブにこの種類を選択します。</li><li>**5d.** アップロードジョブの場合は、この種類を選択します。</li></ul> |
| priority | 省略可能。 ジョブの優先順位を設定します。次に例を示します。<ul><li>FOREGROUND</li><li>HIGH</li><li>NORMAL</li><li>LOW</li></ul> |
| ACLflags | 省略可能。 ファイルをダウンロードするときに所有者と ACL の情報を保持することを示します。 次のように、1つまたは複数の値を指定します。<ul><li>**o** -所有者の情報をファイルにコピーします。</li><li>**g** -グループ情報をファイルと共にコピーします。</li><li>**d** -随意アクセス制御リスト (DACL) の情報をファイルと共にコピーします。</li><li>**s** -システムアクセス制御リスト (SACL) の情報をファイルにコピーします。</li></ul> |
| /動的 | [**BITS_JOB_PROPERTY_DYNAMIC_CONTENT**](/windows/win32/api/bits5_0/ne-bits5_0-bits_job_property_id)を使用してジョブを構成します。これにより、サーバー側の要件が緩和されます。 |
| remotefilename | サーバーに転送された後のファイルの名前です。 |
| localfilename | ローカルに存在するファイルの名前。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前の転送ジョブを開始するには、次のようにします。

```
bitsadmin /transfer myDownloadJob http://prodserver/audio.wma c:\downloads\audio.wma
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
