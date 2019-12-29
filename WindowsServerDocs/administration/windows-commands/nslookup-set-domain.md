---
title: nslookup set domain
description: 'Windows コマンドに関するトピック * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9d4d28e8-6e88-42cc-801f-94e9d8e051f4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f140a371a6374baa7921ca823df469156593423c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372928"
---
# <a name="nslookup-set-domain"></a>nslookup set domain

>適用先:Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

既定のドメインネームシステム (DNS) のドメイン名を、指定された名前に変更します。
## <a name="syntax"></a>構文
```
set domain=<DomainName>
```
## <a name="parameters"></a>パラメーター

|    パラメーター    |                                           説明                                           |
|-----------------|-------------------------------------------------------------------------------------------------|
|  <DomainName>   | 既定の DNS ドメイン名の新しい名前を指定します。 既定のドメイン名は、ホスト名です。 |
| {ヘルプ&#124; ?} |                      **Nslookup**サブコマンドの簡単な概要を表示します。                      |

## <a name="remarks"></a>コメント
- 既定の DNS ドメイン名は、 **defname**と**検索**オプションの状態に応じて、参照要求に追加されます。 DNS ドメインの検索一覧には、その名前に少なくとも2つのコンポーネントがある場合の既定の DNS ドメインの親が含まれます。 たとえば、既定の DNS ドメインが mfg.widgets.com の場合、検索リストには mfg.widgets.com と widgets.com の両方の名前が付けられます。 **Set srchlist**コマンドを使用して別のリストを指定し、 **set all**コマンドを使用して一覧を表示します。
  ## <a name="additional-references"></a>その他の参照情報
  [コマンドライン構文キー](command-line-syntax-key.md)
  [nslookup set srchlist](nslookup-set-srchlist.md)
  [nslookup set all](nslookup-set-all.md)
