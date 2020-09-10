---
title: diskperf
description: Windows を実行しているコンピューターで物理ディスクまたは論理ディスクのパフォーマンスカウンターをリモートで有効または無効にするために使用できる、diskperf コマンドの参照記事。
ms.topic: reference
ms.assetid: f06916e8-069b-4ec8-a6eb-59f1d9f77111
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: f0e7700b3fbe1cec79aa9cf2b5c93eab9bd8372d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624812"
---
# <a name="diskperf"></a>diskperf

**Diskperf**コマンドは、Windows を実行しているコンピューターの物理ディスクまたは論理ディスクのパフォーマンスカウンターをリモートで有効または無効にします。

## <a name="syntax"></a>構文

```
diskperf [-y[d|v] | -n[d|v]] [\\computername]
```

## <a name="options"></a>Options

| オプション | 説明 |
| ------ | ----------- |
| -y | コンピューターの再起動時に、すべてのディスクパフォーマンスカウンターを開始します。 |
| -yd | コンピューターの再起動時に、物理ドライブのディスクパフォーマンスカウンターを有効にします。 |
| -yv | コンピューターの再起動時に、論理ドライブまたは記憶域ボリュームのディスクパフォーマンスカウンターを有効にします。 |
| -n | コンピューターの再起動時に、すべてのディスクパフォーマンスカウンターを無効にします。 |
| -nd | コンピューターの再起動時に、物理ドライブのディスクパフォーマンスカウンターを無効にします。 |
| -nv | コンピューターの再起動時に、論理ドライブまたは記憶域ボリュームのディスクパフォーマンスカウンターを無効にします。 |
| `\\<computername>` | ディスクパフォーマンスカウンターを有効または無効にするコンピューターの名前を指定します。 |
| -? | 状況依存のヘルプを表示します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
