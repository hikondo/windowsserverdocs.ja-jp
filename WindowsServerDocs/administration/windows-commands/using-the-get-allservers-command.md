---
title: 取得-AllServers
description: すべての Windows 展開サービスサーバーに関する情報を取得する get AllServers のリファレンス記事です。
ms.topic: reference
ms.assetid: fe2e3c69-8f2e-457d-af55-d249ebf70f53
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3cd70245754ff544524ed9511f1b6cc5c9574e2f
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89035890"
---
# <a name="get-allservers"></a>取得-AllServers

すべての Windows 展開サービス サーバーに関する情報を取得します。

> [!NOTE]
> このコマンドは、期間を延長環境内で多くの Windows 展開サービス サーバーがある場合、または、サーバーのリンクのネットワーク接続速度が遅い場合の所要時間をかかる場合があります。

## <a name="syntax"></a>構文

```
WDSUTIL [Options] /Get-AllServers /Show:{Config | Images | All} [/Detailed] [/Forest:{Yes | No}]
```

### <a name="parameters"></a>パラメーター

|   パラメーター   |                                                                                                                 説明                                                                                                                  |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /Show: {Config |                                                                                                                    イメージ                                                                                                                    |
|  [/詳細]  | 組み合わせて使用すると、 **/Show:Images** または **/Show:All**, 、すべてのイメージの各イメージからメタデータを返します。 場合、 **詳細/** オプションを指定しない場合、既定の動作は、イメージの名前、説明、およびファイル名を返す。 |
| [/Forest: {はい |                                                                                                                     いいえ}]                                                                                                                     |

## <a name="examples"></a>例

すべてのサーバーに関する情報を表示するには、次のように入力します。
```
WDSUTIL /Get-AllServers /Show:Config
```
すべてのサーバーに関する詳細情報を表示するには、次のように入力します。
```
WDSUTIL /Verbose /Get-AllServers /Show:All /Detailed /Forest:Yes
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)