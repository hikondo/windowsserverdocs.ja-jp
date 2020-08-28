---
title: bitsadmin setaclflag
description: Bitsadmin setaclflag コマンドの参照記事。アクセス制御リスト (ACL) の伝達フラグを設定します。
ms.topic: reference
ms.assetid: 6e3bcda0-827d-4dfd-8384-d1da018f3e10
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 89b605e94505610a2b355de9e4bcbc485a2bb7bf
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89026300"
---
# <a name="bitsadmin-setaclflag"></a>bitsadmin setaclflag

ジョブのアクセス制御リスト (ACL) の伝達フラグを設定します。 フラグは、ファイルをダウンロードするときに所有者と ACL の情報を保持することを示します。 たとえば、ファイルで所有者とグループを管理するには、 **flags** パラメーターをに設定し `og` ます。

## <a name="syntax"></a>構文

```
bitsadmin /setaclflag <job> <flags>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| flags | 次のように、1つまたは複数の値を指定します。<ul><li>**o** -所有者の情報をファイルにコピーします。</li><li>**g** -グループ情報をファイルと共にコピーします。</li><li>**d** -随意アクセス制御リスト (DACL) の情報をファイルと共にコピーします。</li><li>**s** -システムアクセス制御リスト (SACL) の情報をファイルにコピーします。</li></ul> |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのアクセス制御リストの伝達フラグを設定するには、ダウンロードされたファイルと共に所有者とグループの情報を保持します。

```
bitsadmin /setaclflags myDownloadJob og
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
