---
title: ホスト型キャッシュを移動およびサイズ変更する (省略可能)
description: このガイドでは、Windows Server 2016 と Windows 10 を実行するコンピューターに、ホスト型キャッシュモードで BranchCache を展開する手順について説明します。
manager: brianlic
ms.topic: article
ms.assetid: bb0eb349-914d-4596-9140-d3aae7597d55
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 8eed5b91d0634a8409b6b6e26f823ffe86ea8a14
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87964268"
---
# <a name="move-and-resize-the-hosted-cache-optional"></a>ホスト型キャッシュの移動とサイズ変更 \( (オプション)\)

>適用対象: Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

この手順を使用すると、ホスト型キャッシュを目的のドライブとフォルダーに移動したり、ホスト型キャッシュサーバーがホスト型キャッシュに使用できるディスク領域の量を指定したりすることができます。

この手順は省略可能です。 既定のキャッシュの場所 \( % windir% \\ serviceprofiles \\ NetworkService \\ AppData \\ Local \\ peerdistpub \) と size (ハードディスクの合計容量の 5%) が、展開に適している場合は、それらを変更する必要はありません。

この手順を実行するには、Administrators グループのメンバーである必要があります。

### <a name="to-move-and-resize-the-hosted-cache"></a>ホスト型キャッシュの移動とサイズ変更を行うには

1. 管理者特権で Windows PowerShell を開きます。

2. 次のコマンドを入力して、ホスト型キャッシュをローカルコンピューター上の別の場所に移動し、enter キーを押します。

    > [!IMPORTANT]
    > 次のコマンドを実行する前に、– Path や– MoveTo などのパラメーター値を、配置に適した値に置き換えます。

    ```
    Set-BCCache -Path C:\datacache –MoveTo D:\datacache
    ```

3.  次のコマンドを入力して、ホスト型キャッシュのサイズを変更します (具体的には、 \- ローカルコンピューター上の datacache)。 Enter キーを押します。

    > [!IMPORTANT]
    > 次のコマンドを実行する前に、割合などのパラメーター値を、 \- デプロイに適した値に置き換えます。

    ```
    Set-BCCache -Percentage 20
    ```

4.  ホスト型キャッシュサーバーの構成を確認するには、次のコマンドを入力し、enter キーを押します。

    ```
    Get-BCStatus
    ```

    コマンドの結果は、BranchCache インストールのすべての側面の状態を表示します。 次に、BranchCache の設定のいくつかと、各項目の正しい値を示します。

    -   DataCache |CacheFileDirectoryPath: SetBCCache コマンドの– MoveTo パラメーターで指定した値と一致するハードディスクの場所が表示されます。 たとえば、値 D: datacache を指定した場合、 \\ その値はコマンドの出力に表示されます。

    -   DataCache |MaxCacheSizeAsPercentageOfDiskVolume: SetBCCache コマンドの–パーセントパラメーターで指定した値と一致する数値を表示します。 たとえば、値20を指定した場合、その値はコマンドの出力に表示されます。

このガイドを使用するには、「[ホスト型キャッシュサーバーでのコンテンツの事前ハッシュと事前読み込み &#40;オプションの&#41;](7-Bc-Prehash-Preload.md)」を参照してください。