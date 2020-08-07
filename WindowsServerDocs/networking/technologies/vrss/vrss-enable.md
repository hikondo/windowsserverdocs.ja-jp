---
title: Virtual Network アダプターでの vRSS の有効化
description: このトピックでは、デバイスマネージャーまたは Windows PowerShell のいずれかを使用して、Windows Server で vRSS を有効にする方法について説明します。
ms.topic: article
ms.assetid: cb48315c-0204-4927-aa24-64f6789c2e20
manager: dougkim
ms.localizationpriority: medium
ms.date: 09/05/2018
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 1bc5756bde740e367df44701f6cc0db1284b5e2c
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87953838"
---
# <a name="enable-vrss-on-a-virtual-network-adapter"></a>Virtual Network アダプターでの vRSS の有効化

>適用先:Windows Server (半期チャネル)、Windows Server 2016

仮想 RSS \( vRSS \) \( \) では、物理アダプターからの VMQ サポートを仮想マシンキュー必要があります。 VMQ が無効になっている場合、またはサポートされていない場合、仮想受信側のスケーリングは無効になります。

詳細については、「 [vRSS の使用を計画する](vrss-plan.md)」を参照してください。

## <a name="enable-vrss-on-a-vm"></a>VM での vRSS の有効化

Windows PowerShell またはデバイスマネージャーを使用して、vRSS を有効にするには、次の手順に従います。

-   デバイス マネージャ
-   Windows PowerShell

### <a name="device-manager"></a>デバイス マネージャ

次の手順を使用して、デバイスマネージャーを使用して vRSS を有効にすることができます。

>[!NOTE]
>この手順の最初の手順は、Windows 10 または Windows Server 2016 を実行している Vm に固有です。 VM で別のオペレーティングシステムが実行されている場合は、最初にコントロールパネルを開き、デバイスマネージャーを検索して開くことで、デバイスマネージャーを開くことができます。

1.  VM タスクバーの [**検索するテキストを入力**してください] に「**デバイス**」と入力します。

2.  検索結果で、[**デバイスマネージャー**] をクリックします。

3.  デバイスマネージャーで、[**ネットワークアダプター**] をクリックして展開します。

4.  構成するネットワークアダプターを右クリックし、[**プロパティ**] をクリックします。<p>[ネットワークアダプターの**プロパティ**] ダイアログボックスが表示されます。

5.  [ネットワークアダプターの**プロパティ**] で、[**詳細設定**] タブをクリックします。

6.  [**プロパティ**] で、下へスクロールして [ **Receive side scaling**] をクリックします。

7.  [**値**] の選択が**有効になっ**ていることを確認します。

8.  **[OK]** をクリックします。

> [!NOTE]
> [**詳細設定**] タブには、アダプターでサポートされている RSS キューの数も表示されます。

---

### <a name="windows-powershell"></a>Windows PowerShell

Windows PowerShell を使用して vRSS を有効にするには、次の手順に従います。

1. 仮想マシンで、 **Windows PowerShell**を開きます。

2. 次のコマンドを入力します。 **-Name**パラメーターの*adaptername*の値を、構成するネットワークアダプターの名前に置き換えて、enter キーを押します。

   ```PowerShell
   Enable-NetAdapterRSS -Name "AdapterName"
   ```

   >[!TIP]
   >または、次のコマンドを使用して、vRSS を有効にすることもできます。
   >```PowerShell
   >Set-NetAdapterRSS -Name "AdapterName" -Enabled $True
   >```

詳細については、「 [RSS および vRSS 用の Windows PowerShell コマンド](vrss-wps.md)」を参照してください。

---