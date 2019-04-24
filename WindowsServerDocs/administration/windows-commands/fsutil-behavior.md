---
title: Fsutil の動作
ms.prod: windows-server-threshold
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.assetid: 84eaba2c-c0af-49e1-bbbd-2ed2928e5e4b
ms.openlocfilehash: 4593739f25c356e72ea39947c67f3e1301573137
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59838273"
---
# <a name="fsutil-behavior"></a>Fsutil の動作

>適用先:Windows Server (半期チャネル)、Windows Server 2016、Windows 10、Windows Server 2012 R2、Windows 8.1、Windows Server 2012、Windows 8、Windows Server 2008 R2、Windows 7

クエリまたはを含む NTFS ボリュームの動作を設定します。

-   8.3 形式の文字長のファイル名の作成

-   NTFS ボリュームでの 8.3 形式の文字の長さの短いファイル名で拡張文字の使用

-   ディレクトリは NTFS ボリュームに一覧表示された場合、最終アクセス時刻スタンプの更新

-   システム ログと NTFS どのクォータ イベントが書き込まれる頻度ページ プール メモリおよび NTFS の非ページ プール メモリ キャッシュ レベル

-   マスター ファイル テーブル ゾーン (MFT ゾーン) のサイズ

-   NTFS ボリューム上の破損が検出されたときにデータのサイレント削除します。

-   ファイル削除通知 (トリムまたは解除とも呼ばれます)

このコマンドを使用する方法の例については、[例](#BKMK_examples)を参照してください。

## <a name="syntax"></a>構文

```
fsutil behavior query {allowextchar | bugcheckoncorrupt | disable8dot3 [<VolumePath>] | disablecompression | disablecompressionlimit | disableencryption | disablefilemetadataoptimization | disablelastaccess | disablespotcorruptionhandling | disabletxf | disablewriteautotiering | encryptpagingfile | mftzone | memoryusage | quotanotify | symlinkevaluation | disabledeletenotify}

fsutil behavior set {allowextchar {1|0} | bugcheckoncorrupt {1|0} | disable8dot3 [ <Value> | [<VolumePath> {1|0}] ] | disablecompression {1|0} | disablecompressionlimit {1|0} | disableencryption {1|0} | disablefilemetadataoptimization {1|0} | disablelastaccess {1|0} | disablespotcorruptionhandling {1|0} | disabletxf {1|0} | disablewriteautotiering {1|0} | encryptpagingfile {1|0} | mftzone <Value> | memoryusage <Value> | quotanotify <Frequency> | symlinkevaluation <SymbolicLinkType> | disabledeletenotify {1|0}}
```

## <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-------------|---------------|
|クエリ (query)|ファイル システムの動作のパラメーターをクエリします。|
|セット (set)|ファイル システムの動作のパラメーターを変更します。|
|allowextchar {1&#124;0}|許可 (**1**) を許可または拒否 (**0**) 拡張文字の文字で (分音文字を含む) を設定する NTFS ボリューム上の 8.3 形式の文字の長さの短いファイル名に使用します。<br /><br />このパラメーターを有効にするには、コンピューターを再起動する必要があります。|
|Bugcheckoncorrupt {1&#124;0}|により、(**1**) を許可または拒否 (**0**) のバグ チェック、NTFS ボリューム上の破損がある場合に生成します。 この機能は、NTFS がサイレント モードで、NTFS の自己修復機能を使用すると、データを削除するを防ぐために使用できます。<br /><br />このパラメーターを有効にするには、コンピューターを再起動する必要があります。<br /><br />このパラメーターに適用されます。Windows Server 2008 R2 および Windows 7。|
|disable8dot3 [<VolumePath>] {1&#124;0}|無効にします (**1**) または有効 (**0**) FAT と NTFS でフォーマットされたボリューム上の 8.3 形式の文字長のファイル名を作成します。 必要に応じて、プレフィックスを追加、 *VolumePath*ドライブ名の後にコロンまたは GUID として指定します。|
|disablecompression {1&#124;0}|無効にします **(1)** または有効にする **(0)** NTFS 圧縮。<br /><br />このパラメーターを有効にするには、コンピューターを再起動する必要があります。|
|disablecompressionlimit {1&#124;0}| 無効にします **(1)** または有効にする **(0)** NTFS ボリュームで NTFS 圧縮の制限。 圧縮されたファイルには、特定のファイルを拡張に失敗するのではなく、断片化のレベルに達すると、NTFS は、ファイルの追加のエクステントの圧縮を停止します。 これは通常なるよりも大きく、圧縮されたファイルを許可します。 システム上のファイルを圧縮するこの機能のサイズを制限する場合は TRUE。 無効にするこの値を設定します。 この機能を無効化はお勧めしません。<br /><br />このパラメーターを有効にするには、コンピューターを再起動する必要があります。|
|disableencryption {1&#124;0}|無効にします **(1)** または有効にする **(0)** フォルダーとファイルを NTFS ボリュームの暗号化。<br /><br />このパラメーターを有効にするには、コンピューターを再起動する必要があります。|
|disablefilemetadataoptimization {1&#124;0}|無効にします **(1)** または有効にする **(0)** ファイルのメタデータの最適化。 NTFS では、指定されたファイル数のエクステントに対する制限があります。 圧縮され、スペア ファイルの断片化の著しいになることができます。 既定では、NTFS は、断片化されたファイルに使用できる場合は、その内部のメタデータ構造を定期的に圧縮します。 この値を無効にします。 TRUE に設定すると、この内部の最適化。 この機能を無効化はお勧めしません。<br /><br />このパラメーターを有効にするには、コンピューターを再起動する必要があります。|
|disablelastaccess {1&#124;0}|無効にします (**1**) または有効 (**0**) ディレクトリは NTFS ボリュームの一覧表示された場合、各ディレクトリのアクセス時刻スタンプで更新、最後にします。<br /><br />このパラメーターを有効にするには、コンピューターを再起動する必要があります。|
|disablespotcorruptionhandling {1&#124;0}|無効にします **(1)** または有効にする **(0)** スポット破損処理します。 Windows 8 および Windows Server 2012 で導入された新しい機能の 1 つは、CHKDSK の新しい高可用性形式です。 この機能は、オフラインにすることがなく、ボリュームの状態を分析する CHKDSK を実行するシステム管理者を使用できます。 この機能を無効化はお勧めしません。<br /><br />このパラメーターを有効にするには、コンピューターを再起動する必要があります。|
|disabletxf {1&#124;0}|無効にします **(1)** または有効にする **(0)** 指定された NTFS ボリュームで txf します。 TxF は、ファイル システム操作にセマンティクスのようなトランザクションを提供する NTFS 機能です。 TxF は現在 deprected 機能は引き続き使用できます。 C: ボリュームでこの機能を無効化はお勧めしません。<br /><br />このパラメーターを有効にするには、コンピューターを再起動する必要があります。|
|disablewriteautotiering {1&#124;0}|階層化ボリュームには、v2 自動階層化のロジックを ReFS を無効にします。<br /><br />このパラメーターを有効にするには、コンピューターを再起動する必要があります。|
|encryptpagingfile {1&#124;0}|暗号化 (**1**) を暗号化しませんまたは (**0**)、Windows オペレーティング システムでメモリのページング ファイル。<br /><br />このパラメーターを有効にするには、コンピューターを再起動する必要があります。|
|mftzone <Value>|MFT ゾーンのサイズを設定し、200 MB 単位の倍数として表されます。 設定*値*から数値に**1** (既定値は 200 MB) を**4** (最大値は 800 MB)。<br /><br />このパラメーターを有効にするには、コンピューターを再起動する必要があります。|
|memoryusage <Value>|NTFS のページ プール メモリおよび NTFS の非ページ プール メモリの内部キャッシュ レベルを構成します。 設定**1**または**2**します。 設定すると**1** (既定)、NTFS は、既定のページ プール メモリの量を使用します。 設定すると**2**NTFS のルック アサイド リストとメモリのしきい値のサイズを大きくします。 (ルック アサイド リストは、ファイル システム操作では、ファイルの読み取りなどのプライベート メモリ キャッシュ、カーネルとデバイス ドライバーを作成する固定サイズのメモリ バッファーのプールです)。<br /><br />このパラメーターを有効にするには、コンピューターを再起動する必要があります。|
|quotanotify <Frequency>|システム ログで NTFS クォータ違反の報告頻度を構成します。 有効な値は 0 ~ 4294967295 の範囲内では。 既定の頻度は、3600 秒 (1 時間) です。<br /><br />このパラメーターを有効にするには、コンピューターを再起動する必要があります。|
|symlinkevaluation <SymbolicLinkType>|コンピューター上に作成できるシンボリック リンクの種類を制御します。 有効な選択肢は次のとおりです。<br /><br />1. ローカルへのローカルのシンボリック リンク、L2L: {0&#124;1}<br />2. ローカルへのリモートのシンボリック リンク、L2R: {0&#124;1}<br />3.リモートへのローカルのシンボリック リンク、R2R: {0&#124;1}<br />4。リモートへのリモートのシンボリック リンク、R2L: {0&#124;1}|
|DisableDeleteNotify|無効にします\( **1** \)または有効にする\( **0** \)通知を削除します。 通知を削除\(とも呼ばれますトリミングまたは解除\)ファイルのために解放されているクラスターの基になるストレージ デバイスに通知する機能の削除操作だけです。 さらに:<br /><br />ReFS を使用してシステムの v2、trim は既定で無効になります。 Windows Server 2016 に適用されます。<br />ReFS を使用してシステムの v1、trim は既定で有効にします。 Windows Server 2012、Windows Server 2012 R2、および Windows Server 2016 に適用されます。<br />-の NTFS を使用して、システム管理者によって無効にしない限り、trim は既定で有効にします。<br />場合は、ハード ディスク ドライブまたは SAN を報告するトリム、サポートされていませんし、ハード ディスク ドライブと San でトリム通知を取得できません。<br />有効化または無効にするには、再起動は不要です。<br />-Trim は、次のコマンドを解除するときに効果的なが発行されます。<br />-既存の実行中の IO がレジストリの変更により影響ありません。<br />で有効またはトリミングを無効にした場合は、任意のサービスの再起動は不要です。<br /><br />このパラメーターは、Windows Server 2008 R2 および Windows 7 で導入されました。 | 

## <a name="remarks"></a>注釈

-   MFT ゾーンは、マスター ファイル テーブル (MFT) MFT の断片化を防ぐために、必要に応じて拡張できるようにする予約済みの領域です。 ボリュームの平均ファイル サイズは 2 KB も以下の場合、設定すると解消できる場合、 **mftzone** 2 の値。 ボリュームの平均ファイル サイズは 1 KB も以下の場合、設定すると解消できる場合、 **mftzone** 4 までの値。

-   ときに**disable8dot3**に設定されている**0**、毎回の長いファイル名を持つファイルを作成する、NTFS、8.3 形式の文字長のファイルの名前を持つ 2 つ目のファイルのエントリを作成します。 NTFS では、ディレクトリにファイルを作成するときは、長いファイル名に関連付けられている 8.3 形式の文字長のファイル名を確認する必要があります。 このパラメーターを更新、 **HKLM\SYSTEM\CurrentControlSet\Control\FileSystem\NtfsDisable8dot3NameCreation**レジストリ キー。

-   **Allowextchar**パラメーターの更新、 **HKLM\SYSTEM\CurrentControlSet\Control\FileSystem\NtfsAllowExtendedCharacterIn8dot3Name**レジストリ キー。

-   **Disablelastaccess**パラメーターは、ファイルとディレクトリの最終アクセス日時スタンプをログ記録の更新の影響を軽減します。 無効にすると、**最終アクセス時刻**機能ファイルとディレクトリのアクセスの速度が向上します。 このパラメーターを更新、 **HKLM\SYSTEM\CurrentControlSet\Control\FileSystem\NtfsDisableLastAccessUpdate**レジストリ キー。

    注:

    -   ファイル ベース**最終アクセス時刻**クエリは、ディスク上のすべての値が最新でない場合でも正確です。 NTFS は、正確な値がメモリに格納されているために、クエリの正しい値を返します。

    -   1 時間は、NTFS は、更新を延期する最大時間**最終アクセス時刻**ディスクにします。 NTFS などその他のファイル属性を更新する場合**最終変更時刻**、および**最終アクセス時刻**NTFS 更新保留中の更新プログラムが**最終アクセス時刻**せず、他の更新プログラム追加のパフォーマンスに影響します。

    -   **Disablelastaccess**パラメーターは、この機能に依存するバックアップとリモート記憶域などのプログラムに影響を与えます。

-   物理メモリを増やすことも、NTFS を使用可能なページ プール メモリの量は常に増加しません。 設定**memoryusage**に**2**ページ プール メモリの制限を発生させます。 これにより、システムを開くと、設定しはまだ使用していないシステム メモリの大量の他のアプリケーションやキャッシュ メモリの同じファイル内の多数のファイルを閉じる場合のパフォーマンスが向上する可能性があります。 スライドを他のアプリケーションやキャッシュ メモリのコンピューターに既に大量のシステム メモリが使用して、ページングされた NTFS の制限を増やすし、非ページ プールのメモリが他のプロセスの使用可能なプールのメモリを削減します。 これにより、全体的なシステム パフォーマンスが低下する可能性があります。 このパラメーターを更新、 **HKLM\SYSTEM\CurrentControlSet\Control\FileSystem\NtfsMemoryUsage**レジストリ キー。

-   指定された値、 **mftzone**パラメーターは、MFT と新しいボリュームで、MFT ゾーンの初期サイズの概算値と各ファイル システムのマウント時に設定されます。 ボリュームの領域が使用されるため、NTFS は、将来の MFT 拡張予約された領域を調整します。 MFT ゾーンが既に大規模な場合は、完全な MFT ゾーンのサイズはもう一度予約されていません。 MFT ゾーンは、連続する範囲 MFT の末尾に基づいているため、領域の使用を縮小します。

    現在の MFT ゾーンが完全に使用されるまで、ファイル システムは新しい MFT ゾーンの場所を特定できません。 一般的なシステムで実行することはありませんに注意してください。

-   一部のデバイスは、削除の通知機能がオンにすると、パフォーマンスの低下にすることがあります。 ここでは、使用して、 **disabledeletenotify**通知機能をオフにします。

### <a name="BKMK_examples"></a>例
{928842df-5a01-11de-a85c-806e6f6e6963}、GUID で指定されたディスク ボリュームの無効化 8dot3 名の動作を照会するには、次のように入力します。

```
fsutil behavior query disable8dot3 Volume{928842df-5a01-11de-a85c-806e6f6e6963}
```

使用して、8dot3 名の動作を照会することも、 **8dot3name**サブコマンドします。

TRIM が有効になっていない、またはシステムを照会するには、次のように入力します。

```
fsutil behavior query DisableDeleteNotify
```
これには、次のような出力が得られます。

    NTFS DisableDeleteNotify = 1
    ReFS DisableDeleteNotify is not currently set

トリミングの既定の動作をオーバーライドする\(disabledeletenotify\) ReFS v2 を入力します。

```
fsutil behavior set DisableDeleteNotify ReFS 0
```

トリミングの既定の動作をオーバーライドする\(disabledeletenotify\) NTFS や refs などの v1 では、入力します。
```
fsutil behavior set DisableDeleteNotify 1
```

#### <a name="additional-references"></a>その他の参照情報
[コマンドライン構文キー](Command-Line-Syntax-Key.md)

[Fsutil](Fsutil.md)

[fsutil 8dot3name](Fsutil-8dot3name.md)

