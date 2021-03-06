---
title: ftp type
description: ファイル転送の種類を設定または表示する ftp type コマンドの参照記事です。
ms.topic: reference
ms.assetid: 6e96dcd4-08f8-4e7b-90b7-1e1761fea4c7
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 943ac3ca85c1e99118ea772338ea427d758927cb
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639392"
---
# <a name="ftp-type"></a>ftp type

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

設定またはファイル転送の種類を表示します。 **Ftp**コマンドでは、ASCII (既定) とバイナリイメージファイル転送の両方の種類がサポートされています。

- テキストファイルを転送するときは、ASCII を使用することをお勧めします。 ASCII モードでは、ネットワークの標準の文字セットとの間の文字変換が実行されます。 たとえば、行末の文字は、対象のオペレーティングシステムに基づいて必要に応じて変換されます。

- 実行可能ファイルを転送するときは、バイナリを使用することをお勧めします。 バイナリモードでは、ファイルは1バイト単位で転送されます。

## <a name="syntax"></a>構文

```
type [<typename>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `[<typename>]` | ファイル転送の種類を指定します。 このパラメーターを指定しない場合は、現在の型が表示されます。|

### <a name="examples"></a>例

ファイル転送の種類を ASCII に設定するには、次のように入力します。

```
type ascii
```

転送ファイルの種類を binary に設定するには、次のように入力します。

```
type binary
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
