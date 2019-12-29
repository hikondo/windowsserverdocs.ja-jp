---
ms.assetid: 7e804590-6d6c-4cca-ac14-02d4dff06cec
title: パスワードのカスタマイズの更新
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: e007d4449cb62e7888c30f5b5929e393d7b571ef
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407454"
---
# <a name="update-password-customization"></a>パスワードのカスタマイズの更新 


場合によっては、ユーザーがアカウント パスワードを変更するために企業ネットワークに接続できないことがあります。 これが問題となるのは、リモートで働く従業員が最寄りのオフィスから離れた場所に住んでいるような場合です。 このような特別な場合には、インターネット接続のみでパスワード更新ページを使用できます。  
  
パスワード更新ページは、独自の説明を追加してカスタマイズできます。  
  
> パスワード更新ページを有効化するには、[エンドポイント] の下にある [AD FS 管理] に移動します。 パスワード更新用のエンドポイントは、[その他] の下部にある /adfs/portal/updatepassword/ です。 このエンドポイントを有効化したら、AD FS サービスを再起動する必要があります。 この操作は手動で行う必要があります。 その後、ワークプレース ジョインが設定されたデバイスで https://<fqdn>/adfs/portal/updatepassword/ を開くと、パスワード更新ページが表示されます。  
  
![update](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom5.png)  
  
## <a name="customize-the-update-password-page-description"></a>パスワード更新ページの説明のカスタマイズ  
パスワード更新ページの説明をカスタマイズするには、次の Windows PowerShell コマンドレットと構文を使用します。  
  

    Set-AdfsGlobalWebContent -UpdatePasswordPageDescriptionText "This is the Contoso Update Password page."  

## <a name="additional-references"></a>その他の参照情報 
[AD FS ユーザーサインインのカスタマイズ](AD-FS-user-sign-in-customization.md)  
