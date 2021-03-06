---
title: dcgpofix
description: ドメインの既定のグループポリシーオブジェクト (Gpo) を再作成する、dcgpofix コマンドの参照記事です。
ms.topic: reference
ms.assetid: 81d5fa65-2aea-49d3-b353-357441846c00
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 3ee90daa4e0bc6100c28f06c892694e015976f8a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89628945"
---
# <a name="dcgpofix"></a>dcgpofix

ドメインの既定のグループポリシーオブジェクト (Gpo) を再作成します。 グループポリシー管理コンソール (GPMC) にアクセスするには、サーバーマネージャーを通じてグループポリシー管理を機能としてインストールする必要があります。

>[!IMPORTANT]
> ベストプラクティスとして、既定のドメインポリシー GPO は、既定の **アカウントポリシー** 設定、パスワードポリシー、アカウントロックアウトポリシー、および Kerberos ポリシーを管理するためにのみ構成することをお勧めします。 また、[既定のドメインコントローラーポリシー] GPO は、ユーザー権利と監査ポリシーを設定するためにのみ構成する必要があります。

## <a name="syntax"></a>構文

```
dcgpofix [/ignoreschema] [/target: {domain | dc | both}] [/?]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| /ignoreschema | では、このコマンドを実行すると、Active Directory スキーマのバージョンは無視されます。 それ以外の場合、コマンドは、コマンドが配布された Windows バージョンと同じスキーマバージョンでのみ機能します。 |
| `/target {domain | dc | both` | 既定のドメインポリシー、既定のドメインコントローラーポリシー、または両方の種類のポリシーを対象にするかどうかを指定します。 |
| /? | コマンド プロンプトでヘルプを表示します。 |

## <a name="examples"></a>例

既定の **アカウントポリシー** 設定、パスワードポリシー、アカウントロックアウトポリシー、および Kerberos ポリシーを管理するには、Active Directory スキーマのバージョンを無視するには、次のように入力します。

```
dcgpofix /ignoreschema /target:domain
```

ユーザー権利と監査ポリシーを設定するためだけに既定のドメインコントローラーポリシー GPO を構成するには、Active Directory スキーマのバージョンを無視するには、次のように入力します。

```
dcgpofix /ignoreschema /target:dc
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)