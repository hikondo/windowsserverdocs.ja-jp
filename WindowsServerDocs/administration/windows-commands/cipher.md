---
title: cipher
description: Cipher コマンドの参照記事。 NTFS ボリューム上のディレクトリとファイルの暗号化を表示または変更します。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 78ef795e-0f87-4acd-8d15-192c972c0f41
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f23e2855c4542cc359d458f6825dd9420581657f
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85929976"
---
# <a name="cipher"></a>cipher

NTFS ボリュームのディレクトリとファイルの暗号化を表示または変更します。 パラメーターを指定せずに使用した場合、現在のディレクトリとそれに含まれるすべてのファイルの暗号化の状態**が表示されます**。

## <a name="syntax"></a>構文

```
cipher [/e | /d | /c] [/s:<directory>] [/b] [/h] [pathname [...]]
cipher /k
cipher /r:<filename> [/smartcard]
cipher /u [/n]
cipher /w:<directory>
cipher /x[:efsfile] [filename]
cipher /y
cipher /adduser [/certhash:<hash> | /certfile:<filename>] [/s:directory] [/b] [/h] [pathname [...]]
cipher /removeuser /certhash:<hash> [/s:<directory>] [/b] [/h] [<pathname> [...]]
cipher /rekey [pathname [...]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ---------- | ----------- |
| /b | エラーが発生した場合は中止します。 既定では、エラーが発生しても、**暗号**は引き続き実行されます。 |
| /c | 暗号化されたファイルに関する情報を表示します。 |
| /d | 指定されたファイルまたはディレクトリの暗号化を解除します。 |
| /e | 指定されたファイルまたはディレクトリを暗号化します。 後で追加されるファイルが暗号化されるように、ディレクトリにマークが付けられます。 |
| /h | 隠し属性またはシステム属性を持つファイルを表示します。 既定では、これらのファイルは暗号化または暗号化解除されません。 |
| /k | 暗号化ファイルシステム (EFS) ファイルで使用する新しい証明書とキーを作成します。 **/K**パラメーターを指定した場合、他のすべてのパラメーターは無視されます。 |
| /r: `<filename>` [/smartcard] | EFS 回復エージェントのキーと証明書を生成し、証明書と秘密キーを含む .pfx ファイルと .cer ファイル (証明書のみを含む) に書き込みます。 **/Smartcard**を指定すると、回復キーと証明書がスマートカードに書き込まれ、.pfx ファイルは生成されません。 |
| /s`<directory>` | 指定された*ディレクトリ*内のすべてのサブディレクトリに対して、指定された操作を実行します。 |
| /u [/n] |  ローカルドライブ上のすべての暗号化されたファイルを検索します。 **/N**パラメーターと共に使用すると、更新は行われません。 **/N**を指定せずに使用した場合、 **/u**では、ユーザーのファイル暗号化キーまたは回復エージェントのキーが現在のキーと比較され、変更された場合に更新されます。 このパラメーターは、 **/n**でのみ機能します。 |
| /w`<directory>` | ボリューム全体で使用可能な未使用のディスク領域からデータを削除します。 **/W**パラメーターを使用すると、他のすべてのパラメーターは無視されます。 指定されたディレクトリは、ローカルボリューム内の任意の場所に配置できます。 マウントポイントである場合、または別のボリューム内のディレクトリを指している場合は、そのボリューム上のデータが削除されます。 |
| /x [: efsfile] [ `<FileName>` ] | EFS 証明書とキーを指定されたファイル名にバックアップします。 **: Efsfile**と共に使用すると、 **/x**は、ファイルの暗号化に使用されたユーザーの証明書をバックアップします。 それ以外の場合は、ユーザーの現在の EFS 証明書とキーがバックアップされます。 |
| /y | 現在の EFS 証明書サムネイルがローカルコンピューターに表示されます。 |
| /adduser [/certhash:`<hash>` | /certfile: `<filename>` ] |
| /キー更新 | 指定された暗号化ファイルを更新して、現在構成されている EFS キーを使用します。 |
| /removeuser/certhash:`<hash>` | 指定されたファイルからユーザーを削除します。 **/Certhash**に指定する*ハッシュ*は、削除する証明書の SHA1 ハッシュである必要があります。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

### <a name="remarks"></a>注釈

- 親ディレクトリが暗号化されていない場合、暗号化されたファイルは、変更されると復号化される可能性があります。 したがって、ファイルを暗号化する場合は、親ディレクトリも暗号化する必要があります。

- 管理者は .cer ファイルの内容を EFS 回復ポリシーに追加して、ユーザーの回復エージェントを作成し、.pfx ファイルをインポートして個々のファイルを回復することができます。

- 複数のディレクトリ名とワイルドカードを使用できます。

- 複数のパラメーターの間にスペースを入れる必要があります。

## <a name="examples"></a>例

現在のディレクトリにある各ファイルおよびサブディレクトリの暗号化状態を表示するには、次のように入力します。

```
cipher
```

暗号化されたファイルとディレクトリは、 **E**でマークされます。暗号化されていないファイルとディレクトリは、 **U**でマークされます。たとえば、次の出力は、現在のディレクトリとそのすべての内容が現在暗号化されていないことを示しています。

```
Listing C:\Users\MainUser\Documents\
New files added to this directory will not be encrypted.
U Private
U hello.doc
U hello.txt
```

前の例で使用したプライベートディレクトリで暗号化を有効にするには、次のように入力します。

```
cipher /e private
```

次の出力が表示されます。

```
Encrypting files in C:\Users\MainUser\Documents\
Private             [OK]
1 file(s) [or directorie(s)] within 1 directorie(s) were encrypted.
```

**Cipher**コマンドを実行すると、次の出力が表示されます。

```
Listing C:\Users\MainUser\Documents\
New files added to this directory will not be encrypted.
E Private
U hello.doc
U hello.txt
```

ここで、**プライベート**ディレクトリが暗号化済みとしてマークされます。

### <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
