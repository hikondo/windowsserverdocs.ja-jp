---
title: automount
description: Automount コマンドの参照記事。自動マウント機能を有効または無効にします。
ms.topic: reference
ms.assetid: 4635fc91-a477-4f17-8dcc-aa08854bfe45
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 0f4be54f7610929627e0cc0332a7f5d65eafc8b2
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632998"
---
# <a name="automount"></a>automount

適用先:Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

- [コマンド ライン構文の記号](command-line-syntax-key.md)

> [!IMPORTANT]
> 記憶域ネットワーク (SAN) 構成では、自動マウントを無効にすると、システムに表示される新しいベーシックボリュームに、ドライブ文字を自動的にマウントしたり、割り当てたりすることができなくなります。

## <a name="syntax"></a>Syntax

自動マウント [{enable | disable | スクラブ}] [noerr]

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| 有効化 (enable) | システムに追加された新しいベーシックおよびダイナミックボリュームを Windows で自動的にマウントし、ドライブ文字を割り当てることができるようにします。 |
| 無効化 (disable) | システムに追加された新しいベーシックボリュームおよびダイナミックボリュームが Windows によって自動的にマウントされないようにします。<p>**注**: 自動マウントを無効にすると、フェールオーバークラスターが構成の検証ウィザードの記憶域部分に障害を起こす可能性があります。 |
| scrub | システムに存在しなくなったボリュームのマウント ポイントのディレクトリとレジストリ設定を削除します。 これにより、以前に存在したボリュームが再びシステムに追加されたときに、自動的にマウントされて以前のボリュームのマウント ポイントが割り当てられることを回避できます。 |
| noerr | スクリプト専用です。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

## <a name="examples"></a>例

自動マウント機能が有効になっているかどうかを確認するには、diskpart コマンド内から次のコマンドを入力します。

```
automount
```

自動マウント機能を有効にするには、次のように入力します。

```
automount enable
```

自動マウント機能を無効にするには、次のように入力します。

```
automount disable
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [diskpart コマンド](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc770877(v%3dws.11))
