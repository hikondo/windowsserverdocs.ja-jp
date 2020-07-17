---
title: DNS クライアントでの DNS クライアント側のキャッシュを無効にする
description: この記事では、dns クライアントで DNS クライアント側のキャッシュを無効にする方法について説明します。
manager: dcscontentpm
ms.technology: networking-dns
ms.topic: article
ms.author: delhan
ms.date: 8/8/2019
author: Deland-Han
ms.openlocfilehash: 09af41a544cacb0fd0977847b7bc2e6b0d8a59f7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80860075"
---
# <a name="disable-dns-client-side-caching-on-dns-clients"></a>DNS クライアントでの DNS クライアント側のキャッシュを無効にする

Windows には、クライアント側の DNS キャッシュが含まれています。 クライアント側の DNS キャッシュ機能では、dns の "ラウンドロビン" 負荷分散が DNS サーバーから Windows クライアントコンピューターに対して行われていないという誤った印象を生成することがあります。 Ping コマンドを使用して同じ A レコードドメイン名を検索すると、クライアントは同じ IP アドレスを使用する場合があります。  

## <a name="how-to-disable-client-side-caching"></a>クライアント側のキャッシュを無効にする方法

DNS キャッシュを停止するには、次のコマンドのいずれかを実行します。

```cmd
net stop dnscache
```

```cmd
sc servername stop dnscache
```


Windows で DNS キャッシュを完全に無効にするには、サービスコントローラーツールまたはサービスツールを使用して、DNS クライアントサービスのスタートアップの種類を **[無効]** に設定します。 Windows DNS クライアントサービスの名前は、"Dnscache" として表示される場合もあることに注意してください。 

> [!NOTE]
> DNS リゾルバーのキャッシュが非アクティブになると、クライアントコンピューターの全体的なパフォーマンスが低下し、DNS クエリのネットワークトラフィックが増加します。 

DNS クライアントサービスは、以前に解決された名前をメモリに格納することによって、DNS 名前解決のパフォーマンスを最適化します。 DNS クライアントサービスが無効になっている場合でも、コンピューターはネットワークの DNS サーバーを使用して DNS 名を解決できます。 

Windows リゾルバーがクエリに対して肯定または否定のいずれかの応答を受信すると、その応答がキャッシュに追加され、その結果、DNS リソースレコードが作成されます。 リゾルバーは、DNS サーバーに対してクエリを実行する前に常にキャッシュをチェックします。 DNS リソースレコードがキャッシュ内にある場合、競合回避モジュールは、サーバーを照会する代わりにキャッシュのレコードを使用します。 この動作により、クエリが迅速化され、DNS クエリのネットワークトラフィックが減少します。 

Ipconfig ツールを使用して、DNS リゾルバーキャッシュを表示およびフラッシュできます。 DNS リゾルバーのキャッシュを表示するには、コマンドプロンプトで次のコマンドを実行します。

```cmd
ipconfig /displaydns 
```

このコマンドを実行すると、DNS リゾルバーキャッシュの内容が表示されます。これには、ホストファイルからプリロードされた DNS リソースレコードと、システムによって解決された最近のクエリ名が含まれます。 しばらくすると、リゾルバーはキャッシュからレコードを破棄します。 この期間は、DNS リソースレコードに関連付けられている**Time to Live (TTL)** の値によって指定されます。 キャッシュを手動でフラッシュすることもできます。 キャッシュをフラッシュした後、コンピューターは、以前にコンピューターによって解決されたすべての DNS リソースレコードについて、DNS サーバーに対してもう一度クエリを実行する必要があります。 DNS リゾルバーキャッシュのエントリを削除するには、コマンドプロンプトで `ipconfig /flushdns` を実行します。

## <a name="using-the-registry-to-control-the-caching-time"></a>レジストリを使用したキャッシュ時間の制御

> [!IMPORTANT]  
> 慎重にこのセクションの手順に従います。 レジストリの変更の方法を誤った場合、深刻な問題が発生することがあります。 変更する前に、問題が発生した場合に[復元するためにレジストリをバックアップ](https://support.microsoft.com/help/322756)します。

正または負の応答がキャッシュされる時間の長さは、次のレジストリキーのエントリの値によって異なります。

**HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\DNSCache\Parameters**

肯定応答の TTL は、次の値のいずれか小さい方になります。 

- リゾルバーが受信したクエリ応答に指定された秒数

- **MaxCacheTtl**レジストリ設定の値。

>[!Note]
>- 肯定応答の既定の TTL は86400秒 (1 日) です。
>- 否定応答の TTL は、MaxNegativeCacheTtl レジストリ設定で指定された秒数になります。
>- 否定応答の既定の TTL は900秒 (15 分) です。
否定応答をキャッシュしない場合は、MaxNegativeCacheTtl レジストリ設定を0に設定します。

クライアントコンピューターのキャッシュ時間を設定するには、次のようにします。

1. レジストリエディター (Regedit.exe) を起動します。

2. レジストリで、次のキーを見つけてクリックします。

   **HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\Dnscache\Parameters**

3. [編集] メニューの [新規作成] をポイントし、[DWORD 値] をクリックして、次のレジストリ値を追加します。

   - 値の名前: MaxCacheTtl

     データ型: REG_DWORD

     値のデータ: 既定値は86400秒です。 
     
     クライアントの DNS キャッシュの TTL の最大値を1秒に下げると、クライアント側の DNS キャッシュが無効になっているように見えます。    

   - 値の名前: MaxNegativeCacheTtl

     データ型: REG_DWORD

     値のデータ: 既定値は900秒です。 
     
     否定応答をキャッシュしない場合は、値を0に設定します。

4. 使用する値を入力し、[OK] をクリックします。

5. レジストリ エディターを終了します。