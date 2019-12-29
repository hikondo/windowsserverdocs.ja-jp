---
title: bitsadmin setclientcertificatebyid
description: '**Bitsadmin setclientcertificatebyid**の Windows コマンドトピック HTTPS (SSL) 要求でクライアント認証に使用するクライアント証明書の識別子を指定します。'
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8585a7a1-7472-437b-b04a-a11925782a3a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 53b6fa4c65397cf710d0497fbae889afd31ec136
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380731"
---
# <a name="bitsadmin-setclientcertificatebyid"></a>bitsadmin setclientcertificatebyid



HTTPS (SSL) 要求でクライアント認証に使用するクライアント証明書の識別子を指定します。

## <a name="syntax"></a>構文

```
bitsadmin /SetClientCertificateByID <Job> <store_location> <store_name> hexa-decimal_cert_id>
```

## <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|Job|ジョブの表示名または GUID|
|Store_location|証明書の検索に使用するシステムストアの場所を指定します。 有効な値は次のとおりです。</br>1 (CURRENT_USER)</br>2 (LOCAL_MACHINE)</br>3 (CURRENT_SERVICE)</br>4 (サービス)</br>5 (ユーザー)</br>6 (CURRENT_USER_GROUP_POLICY)</br>7 (LOCAL_MACHINE_GROUP_POLICY)</br>8 (LOCAL_MACHINE_ENTERPRISE)|
|Store_name|証明書ストアの名前。 有効な値は次のとおりです。</br>CA (証明機関の証明書)</br>MY (個人用証明書)</br>ルート (ルート証明書)</br>SPC (ソフトウェア発行元証明書)|
|Hexadecimal_cert_id|証明書のハッシュを表す16進数。|

## <a name="BKMK_examples"></a>例

次の例では、 *myjob*という名前のジョブに対する HTTPS (SSL) 要求でクライアント認証に使用するクライアント証明書の識別子を指定します。
```
C:\>bitsadmin Bitsadmin /SetClientCertificateByID myJob BG_CERT_STORE_LOCATION_CURRENT_USER MY A106B52356D3FBCD1853A41B619358BD 
```

#### <a name="additional-references"></a>その他の参照情報

[コマンド ライン構文の記号](command-line-syntax-key.md)