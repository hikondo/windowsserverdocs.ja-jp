---
title: MultiPoint Services のユーザー アカウント
description: MultiPoint Services のユーザーアカウント、特にさまざまなシナリオで使用するユーザーアカウントについて説明します。
ms.topic: article
ms.assetid: 7f3c6ce5-9b7c-45a0-83c5-3f9b9f5f48d4
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/04/2016
ms.openlocfilehash: a14d7da2d633c659be9ea949e913857534e244a2
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87992753"
---
# <a name="example-scenarios-multipoint-services-user-accounts"></a>シナリオ例: MultiPoint Services のユーザー アカウント
MultiPoint Services 環境用に選択したユーザーアカウントシナリオを実装するには、どうすればよいですか。 次の表では、ユーザーアカウントを構成し、スタンドアロンの MultiPoint コンピューター、またはワークグループまたは Active Directory ドメイン内のネットワークサーバー上の共有ユーザーアカウントまたは個人ユーザーアカウントのステーションを準備するために実行する各タスクについて説明します。 環境に当てはまるシナリオを選択します。 次に、表のリンクに従って、必要な各構成タスクを完了します。

> [!NOTE]
> ユーザーアカウントの設定方法をまだ決定していない場合は、各選択肢がユーザーに与える影響の詳細について、「 [MultiPoint Services 環境のユーザーアカウントを計画](Plan-user-accounts-for-your-MultiPoint-services-environment.md)する」を参照してください。

## <a name="single-multipoint-services-computer-in-a-stand-alone-environment-no-network"></a>スタンドアロン環境における単一の MultiPoint Services コンピューター (ネットワークなし)

|||
|-|-|
|**ユーザーはログオンする必要がありません。** これらのステーションは、それらについて説明するすべてのユーザーが利用できます。 データまたは個人用のデスクトップを格納するためのプライベートフォルダーを含む個別の Windows デスクトップエクスペリエンスは必要ありません。|1. ローカルユーザーアカウントを1つ作成します (手順については、「[ローカルユーザーアカウントの作成](Create-local-user-accounts.md)」を参照してください)。<br />2. [1 つのアカウントに複数のセッションを許可する](Allow-one-account-to-have-multiple-sessions.md)<br />3.[自動ログオン用にステーションを構成する](Configure-stations-for-automatic-logon.md)|
|**すべてのユーザーが同じユーザーログオンを共有できます。** データまたは個人用のデスクトップを格納するためのプライベートフォルダーを含む個別の Windows デスクトップエクスペリエンスは必要ありません。|1. ローカルユーザーアカウントを1つ作成します (手順については、「[ローカルユーザーアカウントの作成](Create-local-user-accounts.md)」を参照してください)。<br />2. [1 つのアカウントに複数のセッションを許可する](Allow-one-account-to-have-multiple-sessions.md)|
|**ユーザーは、個別の Windows デスクトップエクスペリエンスを持っている必要があります。**|各ユーザーのローカルユーザーアカウントを作成します (手順については、「[ローカルユーザーアカウントの作成](Create-local-user-accounts.md)」を参照してください)。|

## <a name="multiple-multipoint-services-computers-on-a-network-but-with-no-domain"></a>ネットワーク上の複数の MultiPoint Services コンピューター (ドメインなし)

|||
|-|-|
|**ユーザーはログオンする必要がありません。** これらのステーションは、それらについて説明するすべてのユーザーが利用できます。 データまたは個人用のデスクトップを格納するためのプライベートフォルダーを含む個別の Windows デスクトップエクスペリエンスは必要ありません。|1. 各サーバーに1つのローカルユーザーアカウントを作成します。 (手順については、「[ローカルユーザーアカウントの作成](Create-local-user-accounts.md)」を参照してください)。<br />2. 各サーバーで[1 つのアカウントに複数のセッションを許可する](Allow-one-account-to-have-multiple-sessions.md)<br />3. 各サーバーで[自動的にログオンするようにステーションを構成する](Configure-stations-for-automatic-logon.md)|
|**すべてのユーザーが同じユーザーログオンを共有できます。** データまたは個人用のデスクトップを格納するためのプライベートフォルダーを含む個別の Windows デスクトップエクスペリエンスは必要ありません。|1. 各サーバーに1つのローカルユーザーアカウントを作成します。 (手順については、「[ローカルユーザーアカウントの作成](Create-local-user-accounts.md)」を参照してください)。<br />2. [1 つのアカウントに](Allow-one-account-to-have-multiple-sessions.md)各サーバー上の複数のセッションを許可します。|
|**ユーザーは、個別の Windows デスクトップエクスペリエンスを持っている必要があります。**<p>-   **オプション A** -マイユーザーは、常に同じ MultiPoint Services コンピューターに接続されているローカルステーションを使用します。<br />-   **オプション B** -マイユーザーは、複数の MultiPoint Services コンピューターでローカルステーションを使用します。<br />-   **オプション C** -マイユーザーは、LAN 上のリモートクライアントを使用します。|-   **オプション A** -サーバーのユーザーのために、各サーバーに1つのローカルユーザーアカウントを作成します。 (手順については、「[ローカルユーザーアカウントの作成](Create-local-user-accounts.md)」を参照してください)。<br />-   **オプション B** -すべてのサーバー上のすべてのユーザーに対してローカルユーザーアカウントを作成します。 **注:** これは、各ユーザーに各サーバーのプロファイルがあることを意味します。 つまり、サーバー A のステーションにログオンしているときに、ファイルがマイドキュメントに保存された場合、サーバー B のステーションにログオンしてもファイルは表示されません。 (手順については、「[ローカルユーザーアカウントの作成](Create-local-user-accounts.md)」を参照してください)。<br />-   **オプション C** -各ユーザーを特定の MultiPoint Services コンピューターに割り当てます。 各サーバーで、割り当てられたユーザーのローカルユーザーアカウントを作成します。 (手順については、「[ローカルユーザーアカウントの作成](Create-local-user-accounts.md)」を参照してください)。|

## <a name="one-or-more-multipoint-services-computers-in-a-domain-network-environment"></a>ドメインネットワーク環境内の1つまたは複数の MultiPoint Services コンピューター

|||
|-|-|
|**ユーザーはログオンする必要がありません。** これらのステーションは、それらについて説明するすべてのユーザーが利用できます。 データまたは個人用のデスクトップを格納するためのプライベートフォルダーを含む個別の Windows デスクトップエクスペリエンスは必要ありません。|1. サーバーにログオンするためのドメインアカウントを作成します。<br />2. [1 つのアカウントに](Allow-one-account-to-have-multiple-sessions.md)各サーバー上の複数のセッションを許可します。<br />3. 各サーバーで[自動的にログオンするようにステーションを構成](Configure-stations-for-automatic-logon.md)します。|
|**すべてのユーザーが同じユーザーログオンを共有できます。** データまたは個人用のデスクトップを格納するためのプライベートフォルダーを含む個別の Windows デスクトップエクスペリエンスは必要ありません。|1. グループまたはユーザーごとにドメインアカウントを作成します。<br />2. [1 つのアカウントに](Allow-one-account-to-have-multiple-sessions.md)各サーバー上の複数のセッションを許可します。|
|**ユーザーは、個別の Windows デスクトップエクスペリエンスを持っている必要があります。**<p>-   **オプション A** -ドメインアカウントを持つすべてのユーザーは、MultiPoint Services コンピューターを使用できます。<br />-   **オプション B** -サーバーにアクセスできるドメインアカウントを制限する。|-   **オプション A** -セットアップは必要ありません。 既定では、すべてのドメインユーザーが、ネットワーク上の任意の MultiPoint Services コンピューターにアクセスできます。<br />-   **オプション B** -MultiPoint Services コンピューターへのドメインユーザーアカウントのアクセスを制限します。 手順については、「[ユーザーにサーバーへのアクセスを制限する](./limit-user-access-to-multipoint.md)」を参照してください。|
|**ローカルユーザーアカウントを使用して、ドメインアカウントとは別に管理する必要があります。** たとえば、あるユーザーが MultiPoint Services を管理し、ドメインを管理しないようにする場合、またはすべての MultiPoint Services ユーザーにドメインアカウントを付与しないようにする場合などです。|各サーバーに1つ以上のローカルユーザーアカウントを作成します。 (手順については、「[ローカルユーザーアカウントの作成](Create-local-user-accounts.md)」を参照してください)。<p>**注:** これは、各ユーザーアカウントに各サーバーのプロファイルがあることを意味します。 つまり、サーバー A のステーションにログオンしているときに、ファイルがマイドキュメントに保存された場合、サーバー B のステーションにログオンしてもファイルは表示されません。|