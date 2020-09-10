---
title: サーバーでの WinSAT スコアの設定
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 911dc494-0f8f-4723-93d6-2106f914b906
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 56769966cbfb6778c06abc4ba07d21f258e900a4
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89623341"
---
# <a name="set-the-winsat-score-on-the-server"></a>サーバーでの WinSAT スコアの設定

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

ビデオストリーミング解像度を最適化するには、Windows Server Essentials オペレーティングシステムを実行しているサーバーの WinSAT CPU スコアを設定する必要があります。 これには、WinSAT スコア情報を含む .xml ファイルを作成してインストールします。

## <a name="obtain-the-winsat-cpu-score"></a>WinSAT CPU スコアの取得
 OPK には WinServerSAT.exe という名前のプログラムが付属しており、WinSAT CPU スコアを検出して、その情報を WinServerSAT.xml ファイルに格納します。オペレーティング システムはこのファイルを読み取ります。

#### <a name="to-obtain-the-winsat-cpu-score"></a>WinSAT CPU スコアを取得するには

1. \\ADK メディアの resources* を参照コンピューターにコピーします。

2. 参照コンピューター上で、昇格した [コマンド プロンプト] ウィンドウを開きます。

3. %ProgramFiles%\Windows Server\Bin\OEM フォルダーがない場合は、次のコマンドを入力して Enter キーを押します。

    **mkdir "%ProgramFiles%\Windows Server\Bin\OEM"**

4. 次のコマンドを入力して Enter キーを押します。

    **WinServerSAT.exe "%ProgramFiles%\Windows Server\Bin\OEM\WinServerSAT.xml"**

   次の例では、作成される WinServerSAT.xml ファイルの XML コンテンツを示します。

```

<?xml version="1.0" encoding="UTF-16"?>
<WinSAT>
   <CpuScore description="WinSAT CPU score">WinSAT_Score</CpuScore>
</WinSAT>
```

 ここで *WinSAT_Score* は、サーバー上で検出された値に置き換えられます。

> [!IMPORTANT]
>  イメージをキャプチャする前に、WinServerSAT.exe、winsat.prx、winsat.wmv、および WinSATEncode.wmv ファイルを参照コンピューターから削除する必要があります。
