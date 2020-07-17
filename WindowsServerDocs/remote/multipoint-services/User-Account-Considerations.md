---
title: ユーザー アカウントに関する考慮事項
description: MultiPoint Services のユーザーアカウント、ユーザー名、およびパスワードに関する考慮事項を提供します。
ms.prod: windows-server
ms.technology: multipoint-services
ms.topic: article
ms.assetid: e225900b-cee9-48c9-b21c-394dc5e72b78
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/04/2016
ms.openlocfilehash: 732100a79adbdd7d9fbe4ade742c43084d6b54f6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80820575"
---
# <a name="user-account-considerations"></a>ユーザー アカウントに関する考慮事項
このトピックでは、管理ユーザーがユーザー アカウントを作成し、管理するときに考慮するべき問題について説明します。 MultiPoint マネージャーの [Users] タブ内のユーザー アカウントを管理します。 詳細については、「[ユーザー アカウントの管理](Manage-User-Accounts.md)」トピックを参照してください。  
  
## <a name="user-account-types"></a>ユーザー アカウントの種類  
ユーザーアカウントは、ユーザーがアクセスできるファイルとフォルダー、MultiPoint Services システムに対してどのような変更を加えることができるか、およびデスクトップの背景などの各ユーザーの設定を MultiPoint Services に伝えるための情報のコレクションです。 各ユーザーが一意のユーザー名とパスワードを使用して自分のユーザー アカウントにアクセスします。 MultiPoint サービスには、次の 3 つの種類のユーザー アカウントがサポートされています。  
  
-   **管理者のユーザー アカウント** は MultiPoint マネージャーを使用してを使用して、MultiPoint サービス システムを管理する個人用です。 詳細については、「[管理ユーザー アカウントの作成](Create-an-Administrative-User-Account.md)」を参照してください。  
  
-   **標準ユーザー アカウント**は、定期的にステーションにアクセスするが、システムを管理しない個人のためのアカウントです。 通常は、MultiPoint Services システムのほとんどのユーザーに標準ユーザー アカウントを作成します。 詳細については、「[標準ユーザー アカウントの作成](Create-a-Standard-User-Account.md)」を参照してください。  
  
-   **MultiPoint ダッシュボード ユーザー アカウント**は、MultiPoint ダッシュボードを使用して標準ユーザー セッションを管理し、あらゆるステーションからのログオンが許可される個人のためのアカウントです。 詳細については、「[MultiPoint ダッシュボード ユーザー アカウントを作成する](Create-a-MultiPoint-Dashboard-User-Account.md)」を参照してください。  
  
## <a name="user-name-and-password-considerations"></a>ユーザー名とパスワードに関する考慮事項  
管理ユーザーは、ソフトウェアのインストールやセキュリティ設定の変更など、MultiPoint Services システムの他のすべてのユーザーに影響を与えるタスクを実行できます。 そのような理由から、管理ユーザーには一意の名前と管理ユーザーだけが知るパスワードを与えます。  
  
ユーザー アカウントの重要な考慮事項の 1 つが、ユーザー アカウントごとにエクスプローラーに一意の**ドキュメント** ライブラリを割り与えることです。このライブラリに **My Documents** フォルダーが含まれます。 MultiPoint Services システムの標準ユーザーがエクスプローラーの自分の**ドキュメント** ライブラリにプライベートな文書を保存する場合、標準ユーザーも一意のユーザー名と自分だけが知るパスワードで MultiPoint Services システムにログオンする必要があります。 エクスプローラーに文書を保管する方法については、「[ユーザー ファイルの管理](Manage-User-Files.md)」トピックを参照してください。  
  
> [!TIP]  
> システムセキュリティを強化するには、すべてのユーザーのパスワードを強力なパスワードにする必要があります。 強力なパスワードとは、簡単に推測または解読できない、8文字以上の長さで、ユーザーのアカウント名の全部または一部を含まない、およびキーボードで見つかった大文字、小文字、数字、および記号 (!、@、# など) の4種類の文字のうち少なくとも3つが含まれます。  
  
## <a name="see-also"></a>参照  
[管理ユーザー アカウントを作成する](Create-an-Administrative-User-Account.md)  
[標準ユーザー アカウントを作成する](Create-a-Standard-User-Account.md)  
[ユーザー ファイルを管理する](Manage-User-Files.md)
[ユーザー アカウントの管理](Manage-User-Accounts.md)