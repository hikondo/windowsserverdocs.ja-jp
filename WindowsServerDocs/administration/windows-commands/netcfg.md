---
title: netcfg
description: 'Windows コマンドに関するトピック * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2daaab7-12db-4e36-b70c-db8906d084f7 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8f8368aaff16592a55cc9def84d593cf323f28ee
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373292"
---
# <a name="netcfg"></a>netcfg

>適用先:Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows プレインストール環境 (WinPE) で、ワークステーションを展開するために使用する Windows の軽量バージョンをインストールします。   
## <a name="syntax"></a>構文  
```  
netcfg [/v] [/e] [/winpe] [/l ] /c /i  
```  
### <a name="parameters"></a>パラメーター  
|パラメーター|説明|  
|-------|--------|  
|/v|詳細 (詳細) モードで実行します。|  
|/e|インストール中にサービスの環境変数を使用し、アンインストール|  
|/winpe|Windows プレインストール環境用の TCP/IP、NetBIOS、および Microsoft のクライアントをインストールします。|  
|/l|INF の場所を指定します。|  
|/c|インストールするコンポーネントのクラスを提供します。プロトコル、サービス、またはクライアント|  
|/i|コンポーネント ID を提供します。|  
|/s|型を表示するにはコンポーネントを提供します。<br /><br />\ta アダプター、n = = net コンポーネント|  
|/?|コマンド プロンプトにヘルプを表示します。|  
## <a name="BKMK_Examples"></a>例  
プロトコルをインストールする *例* c:\oemdir\example.inf を使用します。  
```  
netcfg /l c:\oemdir\example.inf /c p /i example  
```  
インストールする、 *MS_Server* サービス。  
```  
netcfg /c s /i MS_Server  
```  
Windows プレインストール環境の TCP/IP、NetBIOS、および Microsoft のクライアントをインストールするには  
```  
netcfg /v /winpe  
```  
コンポーネントを表示する *MS_IPX* がインストールされています。  
```  
netcfg /q MS_IPX  
```  
コンポーネントをアンインストールする *MS_IPX*:  
```  
netcfg /u MS_IPX  
```  
すべてを表示するには、net のコンポーネントをインストールします。  
```  
netcfg /s n  
```  
バインドを含むパスに *MS_TCPIP*:  
```  
netcfg /b ms_tcpip  
```  
## <a name="additional-references"></a>その他の参照情報  
-   [コマンド ライン構文の記号](command-line-syntax-key.md)  
