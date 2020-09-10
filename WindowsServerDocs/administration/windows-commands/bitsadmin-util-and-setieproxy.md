---
title: bitsadmin util および setieproxy
description: Bitsadmin util と setieproxy コマンドの参照記事。サービスアカウントを使用してファイルを転送するときに使用するプロキシ設定を設定します。
ms.topic: reference
ms.assetid: 0e9f31ba-3070-4ffd-a94c-388c8d78f688
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7c341a3fffad0951b800c618605c15b47d4d9308
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630425"
---
# <a name="bitsadmin-util-and-setieproxy"></a>bitsadmin util および setieproxy

サービスアカウントを使用してファイルを転送するときに使用するプロキシ設定を設定します。 このコマンドを正常に完了するには、管理者特権のコマンドプロンプトから実行する必要があります。

> [!NOTE]
> このコマンドは、BITS 1.5 以前ではサポートされていません。

## <a name="syntax"></a>構文

```
bitsadmin /util /setieproxy <account> <usage> [/conn <connectionname>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ---------- |
| account | プロキシ設定を定義するサービスアカウントを指定します。 次の値を指定できます。<ul><li>LOCALSYSTEM</li><li>   NETWORKSERVICE</li><li>LOCALSERVICE.</li></ul> |
| usage | 使用するプロキシ検出の形式を指定します。 次の値を指定できます。<ul><li>**NO_PROXY。** プロキシサーバーは使用しないでください。</li><li>**認識.** プロキシ設定を自動的に検出します。</li><li>**MANUAL_PROXY。** 指定されたプロキシリストとバイパスリストを使用します。 使用状況タグの直後にリストを指定する必要があります。 たとえば、「 `MANUAL_PROXY proxy1,proxy2 NULL` 」のように入力します。<ul><li>**プロキシの一覧。** 使用するプロキシサーバーのコンマ区切りの一覧。</li><li>**バイパスリスト。** 転送がプロキシ経由でルーティングされない、ホスト名または IP アドレス、またはその両方のスペース区切りのリスト。 これは \<local> 、同じ LAN 上のすべてのサーバーを参照することができます。 NULL またはの値は、空のプロキシバイパスリストに使用できます。</li></ul><li>**AUTOSCRIPT。** **自動検出**と同じです。ただし、スクリプトも実行されます。 使用状況タグの直後にスクリプト URL を指定する必要があります。 たとえば、「 `AUTOSCRIPT http://server/proxy.js` 」のように入力します。</li><li>**解除.** **NO_PROXY**と同じですが、手動プロキシ url (指定されている場合) および自動検出を使用して検出されたすべての url が削除される点が異なります。</li></ul> |
| connectionname | 省略可能。 **/Conn**パラメーターと共に使用して、使用するモデム接続を指定します。 **/Conn**パラメーターを指定しない場合、BITS は LAN 接続を使用します。 |

### <a name="remarks"></a>注釈

このスイッチを使用する後続の各呼び出しは、以前に指定された使用量を置き換えますが、以前に定義された使用法のパラメーターは置き換えられません。 たとえば、個別の呼び出しで **NO_PROXY**、 **自動検出**、および **MANUAL_PROXY** を指定した場合、BITS は最後に指定された使用量を使用しますが、以前に定義した使用法のパラメーターを保持します。

## <a name="examples"></a>例

LOCALSYSTEM アカウントのプロキシの使用を設定するには、次のようにします。

```
bitsadmin /util /setieproxy localsystem AUTODETECT
```

```
bitsadmin /util /setieproxy localsystem MANUAL_PROXY proxy1,proxy2,proxy3 NULL
```

```
bitsadmin /util /setieproxy localsystem MANUAL_PROXY proxy1:80
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin util コマンド](bitsadmin-util.md)

- [bitsadmin コマンド](bitsadmin.md)
