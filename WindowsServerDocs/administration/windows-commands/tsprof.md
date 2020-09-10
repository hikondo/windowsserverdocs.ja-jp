---
title: tsprof
description: リモートデスクトップサービスユーザーの構成情報をあるユーザーから別のユーザーにコピーする tsprof のリファレンス記事です。
ms.topic: reference
ms.assetid: 27047868-b706-4208-b7e0-1437a2325dd3
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: de1acc0c99f91f3ebf01d09d39d9fb0685d7f8f6
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626689"
---
# <a name="tsprof"></a>tsprof

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

1 人のユーザーから別のリモート デスクトップ サービス ユーザーの構成情報をコピーします。
リモートデスクトップサービスユーザーの構成情報は、[ローカルユーザーとグループ]、[active directory ユーザーとコンピューター] のリモートデスクトップサービスの拡張機能に表示されます。

**tsprof** では、ユーザーのプロファイルパスを設定することもできます。

> [!NOTE]
> 最新バージョンの新機能については、Windows Server TechNet ライブラリの「 [Windows server 2012 のリモートデスクトップサービスの新機能](/previous-versions/orphan-topics/ws.11/hh831527(v=ws.11)) 」を参照してください。

## <a name="syntax"></a>構文
```
tsprof /update {/domain:<DomainName> | /local} /profile:<path> <UserName>
tsprof /copy {/domain:<DomainName> | /local} [/profile:<path>] <Src_usr> <Dest_usr>
tsprof /q {/domain:<DomainName> | /local} <UserName>
```

### <a name="parameters"></a>パラメーター
|パラメーター|Description|
|-------|--------|
|/update|ドメイン <*DomainName*> 内の <*ユーザー名*> のプロファイルパス情報を <*Profilepath*> に更新します。|
|/domain\<DomainName>|操作が適用されるドメインの名前を指定します。|
|/local|ローカルユーザーアカウントにのみ操作を適用します。|
|/profile\<path>|[ローカルユーザーとグループ]、[active directory ユーザーとコンピューター] のリモートデスクトップサービス拡張機能に表示されるプロファイルパスを指定します。|
|\<UserName>|サーバープロファイルパスを更新または照会するユーザーの名前を指定します。|
|/copy|からにユーザー構成情報をコピー \<*SourceUser*> \<*DestinationUser*> し、のプロファイルパス情報をに更新し \<*DestinationUser*> \<*Profilepath*> ます。 とはどちらもローカルであるか、 \<*SourceUser*> \<*DestinationUser*> またはドメイン内に存在する必要があり \<*DomainName*> ます。|
|\<Src_usr>|ユーザー構成情報をコピーするユーザーの名前を指定します。|
|\<Dest_usr>|ユーザー構成情報をコピーするユーザーの名前を指定します。|
|/q|サーバープロファイルパスに対してクエリを実行するユーザーの現在のプロファイルパスを表示します。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>注釈
-   **Tsprof**コマンドを使用できるのは、windows server 2008 を実行しているコンピューターにターミナルサーバーの役割サービスをインストールした場合、または windows Server 2008 R2 を実行しているコンピューターに RD セッションホスト役割サービスをインストールした場合のみです。

## <a name="examples"></a>例
-   ユーザー構成情報を LocalUser1 から LocalUser2 にコピーするには、次のように入力します。
    ```
    tsprof /copy /local LocalUser1 LocalUser2
    ```
-   LocalUser1 のリモートデスクトップサービスプロファイルパスを c:\ プロファイルという名前のディレクトリに設定するには、次のように入力します。
    ```
    tsprof /update /local /profile:c:\profiles LocalUser1
    ```

## <a name="additional-references"></a>その他の参照情報
- [コマンドライン構文のキー](command-line-syntax-key.md) 
[リモートデスクトップサービス (ターミナルサービス) のコマンドリファレンス](remote-desktop-services-terminal-services-command-reference.md)
