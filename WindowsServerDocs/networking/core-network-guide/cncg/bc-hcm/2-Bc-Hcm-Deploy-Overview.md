---
title: BranchCache ホスト型キャッシュ モードの展開の概要
description: このガイドでは、Windows Server 2016 と Windows 10 を実行するコンピューターに、ホスト型キャッシュモードで BranchCache を展開する手順について説明します。
manager: brianlic
ms.topic: article
ms.assetid: 55686a9c-60dd-47f4-9f1f-fe72c2873a44
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 011c0e2f30dad914cc9fde4b2f81fdea2899bf11
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87956039"
---
# <a name="branchcache-hosted-cache-mode-deployment-overview"></a>BranchCache ホスト型キャッシュ モードの展開の概要

>適用対象: Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

このガイドを使用して、コンピューターがドメインに参加しているブランチオフィスに BranchCache ホスト型キャッシュサーバーを展開することができます。 このトピックでは、BranchCache ホスト型キャッシュモードの展開プロセスの概要について説明します。

この概要には、必要な BranchCache インフラストラクチャに加えて、展開の簡単なステップバイステップの概要が含まれています。

## <a name="hosted-cache-server-deployment-infrastructure"></a><a name="bkmk_components"></a>ホスト型キャッシュサーバーの配置インフラストラクチャ

この展開では、ホスト型キャッシュサーバーは Active Directory Domain Services AD DS のサービス接続ポイントを使用して展開されます。 \( \) また、windows server 2016、windows Server 2012 R2、および windows server 2012 の BranchCache を使用して、Web およびファイルベースのコンテンツサーバー上の共有コンテンツを事前にハッシュし、ホスト型キャッシュサーバーにコンテンツを事前に読み込むことができます。

次の図は、BranchCache ホスト型キャッシュサーバーを展開するために必要なインフラストラクチャを示しています。

![BranchCache ホスト型キャッシュモードの概要](../../../media/BranchCache-Hcm-Overview/Bc-Hcm-Overview.jpg)

> [!IMPORTANT]
> この展開はクラウドデータセンター内のコンテンツサーバーを示していますが、このガイドを使用して、コンテンツサーバーを展開する場所に関係なく、BranchCache ホスト型キャッシュサーバーを展開することができます (メインオフィスまたはクラウドの場所にあります)。

### <a name="hcs1-in-the-branch-office"></a>ブランチオフィスの HCS1

このコンピューターは、ホスト型キャッシュサーバーとして構成する必要があります。 コンテンツサーバーデータを事前にハッシュして、ホスト型キャッシュサーバーにコンテンツを事前に読み込むことを選択した場合は、Web サーバーとファイルサーバーからコンテンツを含むデータパッケージをインポートできます。

### <a name="web1-in-the-cloud-data-center"></a>クラウドデータセンターの WEB1

WEB1 は、BranchCache が \- 有効なコンテンツサーバーです。 コンテンツサーバーのデータを事前にハッシュして、ホスト型キャッシュサーバーにコンテンツを事前に読み込むことを選択した場合は、WEB1 で共有コンテンツを事前にハッシュし、HCS1 にコピーするデータパッケージを作成することができます。

### <a name="file1-in-the-cloud-data-center"></a>クラウドデータセンターの FILE1

FILE1 は、BranchCache が \- 有効なコンテンツサーバーです。 コンテンツサーバーのデータを事前にハッシュして、ホスト型キャッシュサーバーにコンテンツを事前に読み込むことを選択した場合は、共有コンテンツを FILE1 に事前にハッシュし、HCS1 にコピーするデータパッケージを作成することができます。

### <a name="dc1-in-the-main-office"></a>メインオフィスの DC1

DC1 はドメインコントローラーであり、既定のドメインポリシーを構成するか、展開に適した別のポリシーを構成する必要があります。また、サービス接続ポイントによるホスト型キャッシュの自動検出を有効にするための BranchCache グループポリシー設定を構成する必要があります。

ブランチ内のクライアントコンピュータがグループポリシーに更新され、このポリシー設定が適用されると、ブランチオフィスのホスト型キャッシュサーバーを自動的に検索して使用し始めます。

### <a name="client-computers-in-the-branch-office"></a>ブランチオフィスのクライアントコンピューター

新しい BranchCache グループポリシー設定を適用し、クライアントがホスト型キャッシュサーバーを検索して使用できるようにするには、クライアントコンピューターのグループポリシーを更新する必要があります。

## <a name="hosted-cache-server-deployment-process-overview"></a><a name="bkmk_overview"></a>ホスト型キャッシュサーバーの展開プロセスの概要

>[!NOTE]
>これらの手順の実行方法の詳細については、「 [BranchCache ホスト型キャッシュモードの展開](4-Bc-Hcm-Deployment.md)」を参照してください。

BranchCache ホスト型キャッシュサーバーを展開するプロセスは、次の段階で行われます。

>[!NOTE]
>次の手順の一部は省略可能です。たとえば、ホスト型キャッシュサーバーでコンテンツを事前にハッシュおよびプリロードする方法を説明する手順などです。 ホスト型キャッシュモードで BranchCache を展開する場合、Web およびファイルコンテンツサーバー上のコンテンツを事前にハッシュし、データパッケージを作成し、コンテンツを使用してホスト型キャッシュサーバーをプリロードするためにデータパッケージをインポートする必要はありません。 手順は、このセクションでは省略可能であり、必要に応じてスキップできるように「 [BranchCache ホスト型キャッシュモードの展開](4-Bc-Hcm-Deployment.md)」セクションで説明します。

1. HCS1 では、Windows PowerShell コマンドを使用して、コンピューターをホスト型キャッシュサーバーとして構成し、Active Directory にサービス接続ポイントを登録します。

2. \(HCS1 では省略可能 \) 。 BranchCache の既定値がサーバーおよびホスト型キャッシュの展開目標に一致しない場合は、ホスト型キャッシュに割り当てるディスク領域の量を構成します。 また、ホスト型キャッシュに使用するディスクの場所も構成します。

3. \(\)コンテンツサーバーの事前ハッシュコンテンツ (オプション)、データパッケージの作成、およびホスト型キャッシュサーバーへのコンテンツの事前読み込み。

    > [!NOTE]
    > ホスト型キャッシュサーバーでのコンテンツの事前ハッシュと事前読み込みは省略可能ですが、ハッシュとプリロードを事前に選択した場合は、展開に適用できる以下のすべての手順を実行する必要があります。 \(たとえば、Web サーバーを所有していない場合は、Web サーバーコンテンツのプリハッシュおよびプリロードに関連する手順を実行する必要はありません。\)

    1. WEB1 で、Web サーバーのコンテンツを事前ハッシュし、データパッケージを作成します。

    2. FILE1 で、ファイルサーバーのコンテンツを事前ハッシュし、データパッケージを作成します。

    3. WEB1 および FILE1 から、データパッケージをホスト型キャッシュサーバー HCS1 にコピーします。

    4. HCS1 で、データパッケージをインポートしてデータキャッシュをプリロードします。

4. DC1 で、BranchCache ポリシー設定を使用してグループポリシーを構成することによって、ホスト型キャッシュモード用にドメイン参加ブランチオフィスクライアントコンピューターを構成します。

5. クライアントコンピューターでグループポリシーを更新します。

このガイドを続行するには、「 [BranchCache ホスト型キャッシュモードの展開計画](3-Bc-Hcm-Plan.md)」を参照してください。