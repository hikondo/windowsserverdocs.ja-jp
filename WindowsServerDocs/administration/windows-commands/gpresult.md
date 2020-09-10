---
title: gpresult
description: リモートユーザーとコンピューターのポリシーの結果セット (RSoP) 情報を表示する、gpresult コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: dfaa3adf-2c83-486c-86d6-23f93c5c883c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a608f94a0239dd2e2d7eff2cc5aba5bfc7e918e8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634743"
---
# <a name="gpresult"></a>gpresult

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

リモートユーザーとコンピューターのポリシーの結果セット (RSoP) 情報を表示します。 ファイアウォール経由でリモートターゲットコンピューターの RSoP レポートを使用するには、ポートで受信ネットワークトラフィックを有効にするファイアウォール規則が必要です。

## <a name="syntax"></a>Syntax

```
gpresult [/s <system> [/u <username> [/p [<password>]]]] [/user [<targetdomain>\]<targetuser>] [/scope {user | computer}] {/r | /v | /z | [/x | /h] <filename> [/f] | /?}
```

> [!NOTE]
> **/?** を使用する場合を除き、出力オプション、 **/r**、 **/v**、 **/z**、 **/x**、または **/h**を含める必要があります。

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| /s `<system>` | 名前またはリモート コンピューターの IP アドレスを指定します。 バックスラッシュは使用しないでください。 既定値はローカル コンピューターです。 |
| /u `<username>` | 指定されたユーザーの資格情報を使用してコマンドを実行します。 既定のユーザーは、コマンドを発行するコンピューターにログオンしているユーザーです。 |
| /p `[<password>]` | **/U**パラメーターに指定されているユーザーアカウントのパスワードを指定します。 **/P**を省略した場合、 **gpresult**はパスワードの入力を求めます。 **/P**パラメーターは、 **/x**または **/h**と共に使用することはできません。 |
| /user `[<targetdomain>\]<targetuser>]` | RSoP データを表示するリモートユーザーを指定します。 |
| /scope `{user | computer}` | ユーザーまたはコンピューターの RSoP データを表示します。 **/Scope**を省略した場合、 **gpresult**はユーザーとコンピューターの両方の RSoP データを表示します。 |
| `[/x | /h] <filename>` | は、 *filename*パラメーターで指定されたファイル名を使用して、レポートを XML (**/x**) 形式または HTML 形式 (**/h**) 形式で保存します。 **/U**、 **/p**、 **/r**、 **/v**、または **/z**と共に使用することはできません。 |
| /f | **/X**または **/h**オプションで指定されたファイル名を強制的に**gpresult**に上書きします。 |
| /r | RSoP の概要データを表示します。 |
| /v | 詳細なポリシー情報を表示します。 これには、優先順位1で適用された詳細設定が含まれます。 |
| /z | グループポリシーに関する利用可能なすべての情報を表示します。 これには、1以上の優先順位で適用された詳細設定が含まれます。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- グループポリシーは、組織内のユーザーとコンピューターに対してプログラム、ネットワークリソース、およびオペレーティングシステムがどのように動作するかを定義および制御するための主要な管理ツールです。 Active directory 環境では、グループポリシーは、サイト、ドメイン、または組織単位のメンバーシップに基づいてユーザーまたはコンピューターに適用されます。

- 重複したポリシー設定を任意のコンピューターまたはユーザーに適用できるため、グループポリシー機能によって、ユーザーがログオンしたときに生成されるポリシー設定のセットが生成されます。 **Gpresult**コマンドを実行すると、ユーザーがログオンしたときに、指定したユーザーのコンピューターに適用されたポリシー設定の結果セットが表示されます。

- **/V**および **/z**では大量の情報が生成されるため、出力をテキストファイルにリダイレクトすると便利です (たとえば、 `gpresult/z >policy.txt` )。

### <a name="examples"></a>例

リモートユーザーのみの RSoP データを取得するには、 *maindom\hiropln* *p@ssW23* コンピューターの *srvmain*にあるパスワードを使用して、次のように入力します。

```
gpresult /s srvmain /u maindom\hiropln /p p@ssW23 /user targetusername /scope user /r
```

グループポリシーに関する利用可能なすべての情報をという*policy.txt*名前のファイルに保存する*maindom\hiropln*には、maindom\hiropln *p@ssW23* コンピューターの*srvmain*に、次のように入力します。

```
gpresult /s srvmain /u maindom\hiropln /p p@ssW23 /user targetusername /z > policy.txt
```

ログオンしているユーザーの RSoP データを表示するには、 *maindom\hiropln* *p@ssW23* コンピューターの *srvmain*に、次のように入力します。

```
gpresult /s srvmain /u maindom\hiropln /p p@ssW23 /r
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
