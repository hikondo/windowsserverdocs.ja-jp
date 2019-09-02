---
title: リモート デスクトップ クライアントの URI スキーム
description: リモート デスクトップ クライアントの Uniform Resource Identifier スキームについて説明します
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c3f1eb6-835c-4522-99ff-56c6ee4bb911
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 06/11/2018
ms.localizationpriority: medium
ms.openlocfilehash: f2934fed43c8f4feec2f321d684cc3593933eb5d
ms.sourcegitcommit: 3743cf691a984e1d140a04d50924a3a0a19c3e5c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2019
ms.locfileid: "63743851"
---
# <a name="remote-desktop-client-universal-resource-identifier-uri-scheme-support"></a>リモート デスクトップ クライアント Universal Resource Identifier (URI) スキームのサポートします。

>適用対象:Windows Server バージョン 1803、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2

Uniform Resource Identifier (URI) スキームの対応により、以下が可能になるため、IT 担当者および開発者はプラットフォーム間でリモート デスクトップ クライアントの機能を統合し、ユーザー エクスペリエンスを向上させることができます。 

- サード パーティのアプリケーションで Microsoft リモート デスクトップを起動し、(URI 文字列の一部として指定する) 定義済みの設定を使ってリモート セッションを開始する。
- エンド ユーザーがあらかじめ構成された URL を使ってリモート接続を開始する。

>[!NOTE]
> Windows オペレーティング システムでは、URI を使用した RD クライアントへの接続はサポートされていません。URI は MacOS、iOS、および Android デバイスで使用してください。

Microsoft リモート デスクトップでは、URI スキーム rdp://query_string を使用して、クライアントを起動するときに使用される事前構成されている属性の設定を格納します。 クエリ文字列は、URL で指定する単一または一連の RDP 属性を表します。 

RDP 属性は、アンパサンド記号で区切ります (&)。 たとえば、PC に接続する場合、文字列は次のようになります。

```
rdp://full%20address=s:mypc:3389&audiomode=i:2&disable%20themes=i:1
```

次の表に、iOS、Mac、Android のリモート デスクトップ クライアントで使うことができる、サポートされている属性の完全な一覧を示します (プラットフォームの列の "x" は属性がサポートされていることを示します。 山かっこ (<>) 内の値は、リモート デスクトップ クライアントでサポートされている値を表します)。

| **RDP 属性**                                           | **Android** | **Mac** | **iOS** |
|---------------------------------------------------------|---------|-----|-----|
| allow desktop composition=i:&lt;0 または 1&gt;                    | ○       | ○   | ○   |
| allow font smoothing=i:<0 または 1&gt;                         | ○       | ○   | ○   |
| alternate shell=s:&lt;文字列&gt;                              | ○       | ○   | ○   |
| [audiomode=i:&lt;0、1、または 2&gt;](https://technet.microsoft.com/library/ff393707.aspx)                                | ○       | ○   | ○   |
| [authentication level=i:&lt;0 または 1&gt;](https://technet.microsoft.com/library/ff393709.aspx)                         | ○       | ○   | ○   |
| connect to console=i:&lt;0 または 1&gt;                           | ○       | ○   | ○   |
| disable cursor settings=i:&lt;0 または 1&gt;                      | ○       | ○   | ○   |
| disable full window drag=i:&lt;0 または 1&gt;                     | ○       | ○   | ○   |
| disable menu anims=i:&lt;0 または 1&gt;                           | ○       | ○   | ○   |
| disable themes=i:&lt;0 または 1&gt;                               | ○       | ○   | ○   |
| disable wallpaper=i:&lt;0 または 1&gt;                            | ○       | ○   | ○   |
| [drivestoredirect = s: *](https://technet.microsoft.com/library/ff393728(v=ws.10).aspx) (これは、唯一サポートされる値です) | ○       | ○   |     |
| [desktopheight=i:&lt;ピクセル単位の値&gt;](https://technet.microsoft.com/library/ff393702.aspx)                       |         | ○   |     |
| [desktopwidth=i:&lt;ピクセル単位の値&gt;](https://technet.microsoft.com/library/ff393697.aspx)                        |         | ○   |     |
| [domain=s:&lt;文字列&gt;](https://technet.microsoft.com/library/ff393673.aspx)                           | ○ | ○ | ○ |
| [full address=s:&lt;文字列&gt;](https://technet.microsoft.com/library/ff393661.aspx)                     | ○ | ○ | ○ |
| gatewayhostname=s:&lt;文字列&gt;                  | ○ | ○ | ○ |
| [gatewayusagemethod=i:&lt;1 または 2&gt;](https://msdn.microsoft.com/aa381329.aspx)               | ○ | ○ | ○ |
| [prompt for credentials on client=i:&lt;0 または 1&gt;](https://technet.microsoft.com/library/ff393660(v=ws.10).aspx) |   | ○ |   |
| [loadbalanceinfo=s:&lt;文字列&gt;](https://technet.microsoft.com/library/ff393684.aspx)                  | ○ | ○ | ○ |
| [redirectprinters=i:&lt;0 または 1&gt;](https://technet.microsoft.com/library/ff393671(v=ws.10).aspx)                 |   | ○ |   |
| remoteapplicationcmdline=s:&lt;文字列&gt;         | ○ | ○ | ○ |
| remoteapplicationmode=i:&lt;0 または 1&gt;            | ○ | ○ | ○ |
| remoteapplicationprogram=s:&lt;文字列&gt;         | ○ | ○ | ○ |
| shell working directory=s:&lt;文字列&gt;          | ○ | ○ | ○ |
| Use redirection server name=i:&lt;0 または 1&gt;      | ○ | ○ | ○ |
| [username=s:&lt;文字列&gt;](https://technet.microsoft.com/library/ff393678.aspx)                         | ○ | ○ | ○ |
| [screen mode id=i:&lt;1 または 2&gt;](https://technet.microsoft.com/library/ff393692.aspx)                   |   | ○ |   |
| [session bpp=i:&lt;8、15、16、24、または 32&gt;](https://technet.microsoft.com/library/ff393680.aspx)        |   | ○ |   |
| [use multimon=i:&lt;0 または 1&gt;](https://technet.microsoft.com/library/ff393695(v=ws.10).aspx)          |   | ○ |   |