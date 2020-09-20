---
title: Windows 10 デバイスに OMA-DM ベースの VPNv2 プロファイルを作成する
description: '2つの方法のいずれかを使用して、OMA-URI ベースの VPNv2 プロファイルを作成できます。 '
ms.topic: article
ms.date: 07/13/2018
ms.author: v-tea
author: Teresa-MOTIV
ms.localizationpriority: medium
ms.reviewer: deverette
ms.openlocfilehash: c5619baa5123d0cd611cb9371cd3944fdd91fb3c
ms.sourcegitcommit: 877d6db73d9520e3a23738d6528016235493cff3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2020
ms.locfileid: "90779266"
---
# <a name="step-75-create-oma-dm-based-vpnv2-profiles-to-windows-10-devices"></a>手順 7.5.  Windows 10 デバイスに OMA-URI ベースの VPNv2 プロファイルを作成する

>適用対象: Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows 10

- [**前へ:** 手順 7.4.条件付きアクセスルート証明書をオンプレミスの AD にデプロイする](vpn-deploy-cond-access-root-cert-to-on-premise-ad.md)
- [**次のようになります。** VPN の条件付きアクセスのしくみについて説明します。](/windows/access-protection/vpn/vpn-conditional-access)

この手順では、Intune を使用して OMA-URI ベースの VPNv2 プロファイルを作成し、VPN デバイス構成ポリシーを展開することができます。 VPNv2 プロファイルを作成するために Microsoft エンドポイント Configuration Manager または PowerShell スクリプトを使用する場合は、 [VPNV2 CSP の設定](/windows/client-management/mdm/vpnv2-csp) に関する詳細を参照してください。

## <a name="managed-deployment-using-intune"></a>Intune を使用した管理された展開

このセクションで説明するすべてのものは、VPN を条件付きアクセスで動作させるために最低限必要です。 WIP を使用した分割トンネリングについては説明しません。また、カスタムの Intune デバイス構成プロファイルを作成して AutoVPN の機能を取得します。 以下の設定を、前の手順5で作成した VPN プロファイルに統合し [ます。Windows 10 クライアント Always On VPN 接続を構成](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md)します。この例では、 [Intune ポリシーを使用して VPN クライアントを構成](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md#configure-the-vpn-client-by-using-intune) します。

**要件**

Windows 10 クライアントコンピューターは、Intune を使用して VPN 接続を使用して既に構成されています。


**作業**

1. [Azure portal で、[ **intune**  >  **デバイス構成**プロファイル] を選択し、「  >  **Profiles** [intune を使用して vpn クライアントを構成](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md#configure-the-vpn-client-by-using-intune)する」の手順で作成した vpn プロファイルを選択します。

2. ポリシーエディターで、[**プロパティ**] [設定] [  >  **Settings**  >  **Base VPN**] を選択します。 既存の **EAP Xml** を拡張して、検出された最初の証明書を使用できるようにするのではなく、ユーザーの証明書ストアから AAD 条件付きアクセス証明書を取得するために必要なロジックを VPN クライアントに付与するフィルターを含めるようにします。

    >[!NOTE]
    >これを行わない場合、VPN クライアントは、オンプレミスの証明機関から発行されたユーザー証明書を取得することができ、その結果、VPN 接続が失敗します。

    ![Intune ポータル](../../media/Always-On-Vpn/intune-eap-xml.png)

3. で終わるセクションを見つけ、 **\</AcceptServerName>\</EapType>** これらの2つの値の間に次の文字列を挿入して、VPN クライアントに AAD 条件付きアクセス証明書を選択するためのロジックを提供します。

    ```XML
    <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"><FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3"><EKUMapping><EKUMap><EKUName>AAD Conditional Access</EKUName><EKUOID>1.3.6.1.4.1.311.87</EKUOID></EKUMap></EKUMapping><ClientAuthEKUList Enabled="true"><EKUMapInList><EKUName>AAD Conditional Access</EKUName></EKUMapInList></ClientAuthEKUList></FilteringInfo></TLSExtensions>
    ```

4. [ **条件付きアクセス** ] ブレードを選択し、[ **この VPN 接続の条件付きアクセス** を **有効**にする] をオンにします。

   この設定を有効にすると、VPNv2 Profile XML の** \<DeviceCompliance> \<Enabled> 真 \</Enabled> **の設定が変更されます。

    ![Always On VPN の条件付きアクセス-プロパティ](../../media/Always-On-Vpn/vpn-conditional-access-azure-ad.png)

5. **[OK]** を選択します。

6. [ **割り当て**] を選択し、[含める] で [ **含めるグループ**を選択] を選択します。

7. このポリシーを受信する **VPN ユーザー** グループを選択し、[ **保存**] を選択します。

    ![自動 VPN ユーザーの上限-割り当て](../../media/Always-On-Vpn/cap-for-auto-vpn-users-assignments.png)

## <a name="force-mdm-policy-sync-on-the-client"></a>クライアントで MDM ポリシーの同期を強制する

VPN プロファイルがクライアントデバイスに表示されない場合は、[設定] [ネットワーク &] [インターネット VPN] の下で、 \\ \\ MDM ポリシーを強制的に同期することができます。

1. ドメインに参加しているクライアントコンピューターに、 **VPN ユーザー** グループのメンバーとしてサインインします。

2. [スタート] メニューで、「 **account**」と入力し、enter キーを押します。

3. 左側のナビゲーションウィンドウで、[ **職場または学校にアクセス**する] を選択します。

4. [職場または学校にアクセスする] で、[接続先] を選択し **< \domain> MDM**に選択し、[ **情報**] を選択します。

5. [ **同期** ] を選択し、[ \\ ネットワーク & インターネット vpn の設定] の下に vpn プロファイルが表示されていることを確認し \\ ます。


## <a name="next-steps"></a>次のステップ

Azure AD 条件付きアクセスを使用するように VPN プロファイルを構成しました。

|目的  |参照先  |
|---------|---------|
|Vpn での条件付きアクセスのしくみについての詳細情報  |[Vpn と条件付きアクセス](/windows/access-protection/vpn/vpn-conditional-access): このページでは、vpn での条件付きアクセスのしくみについて詳しく説明します。      |
|高度な VPN 機能についての詳細情報  |[高度な Vpn 機能](always-on-vpn/deploy/always-on-vpn-adv-options.md#advanced-vpn-features): このページでは、Vpn トラフィックフィルターを有効にする方法、アプリトリガーを使用して自動 VPN 接続を構成する方法、Azure AD によって発行された証明書を使用するクライアントからの vpn 接続のみを許可するように NPS を構成する方法に関するガイダンスを提供します。        |


## <a name="related-topics"></a>関連トピック

- [VPNV2 csp](/windows/client-management/mdm/vpnv2-csp): このトピックでは、VPNv2 csp の概要について説明します。 VPNv2 構成サービスプロバイダーを使用すると、モバイルデバイス管理 (MDM) サーバーでデバイスの VPN プロファイルを構成できます。

- [Windows 10 クライアント ALWAYS ON VPN 接続を構成](./always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md)する: このトピックでは、ProfileXML のオプションとスキーマ、および ProfileXML VPN の作成方法について説明します。 サーバーインフラストラクチャを設定したら、VPN 接続を使用して、そのインフラストラクチャと通信するように Windows 10 クライアントコンピューターを構成する必要があります。

- [Intune を使用して vpn クライアントを構成](./always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md#configure-the-vpn-client-by-using-intune)する: このトピックでは、Windows 10 リモートアクセス Always On vpn プロファイルに展開する方法について説明します。 Intune で Azure AD グループが使用されるようになりました。 VPN ユーザーグループをオンプレミスから Azure AD に同期 Azure AD Connect 場合、Intune を使用して VPN クライアントを構成する必要はありません。
