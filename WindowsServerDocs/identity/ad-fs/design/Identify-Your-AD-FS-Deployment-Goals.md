---
ms.assetid: c81b8291-fba5-4b30-a43d-7feb2f4b66be
title: AD FS の展開目標の dentify
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 3705d9c1e5675c233e91df9b5f1e73f68ce4b34c
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87945304"
---
# <a name="identify-your-ad-fs-deployment-goals"></a>AD FS 展開目標の特定

\( \) AD FS design プロジェクトを成功させるには、Active Directory フェデレーションサービス (AD FS) AD FS の配置目標を正しく特定することが不可欠です。 反復的なアプローチを使用して AD FS を設計および展開できるように、展開の目標を優先順位付けし、場合によっては組み合わせることができます。 AD FS 設計に関連する既存の、文書化された、定義済みの AD FS の展開の目標を活用して、状況に応じた実用的なソリューションを開発できます。

以前のバージョンの AD FS は、次のことを実現するために最も一般的に展開されていました。

-   \-企業内の要求ベースのアプリケーションにアクセスするときに、従業員や顧客に web ベースの SSO エクスペリエンスを提供し \- ます。

-   従業員または顧客が、web ベースの SSO エクスペリエンスを提供して \- 、フェデレーションパートナー組織のリソースにアクセスできるようにします。

-   \-内部でホストされている web サイトまたはサービスにリモートアクセスするときに、従業員や顧客に web ベースの SSO エクスペリエンスを提供します。

-   \-クラウド内のリソースまたはサービスにアクセスするときに、従業員や顧客に web ベースの SSO エクスペリエンスを提供します。

これらに加えて、Windows Server 2012 R2 の AD FS には、 &reg; 次の機能を実現するのに役立つ機能が追加されています。

-   SSO およびシームレスな 2 要素認証のためのデバイス社内参加。 これにより、組織はユーザーの個人のデバイスからのアクセスを許可し、このアクセスを提供する際のリスクを管理できます。

-   多要素アクセス制御によるリスク管理 \- 。 AD FS では、だれがどのアプリケーションにアクセスするかを制御する承認レベルが充実しています。 これは、ユーザー属性 \( UPN、電子メール、セキュリティグループメンバーシップ、認証強度などに基づいて作成されます。デバイス属性は、 \) \( デバイスが社内参加しているか、 \) 要求属性の \( ネットワークの場所、IP アドレス、またはユーザーエージェントか \) によって決まります。

-   追加 \- の多要素認証による機密アプリケーションのリスク管理。 AD FS を使用すると \- 、グローバルに、またはアプリケーションごとに多要素認証を必要とする可能性のあるポリシーを制御できます。 さらに、AD FS は、多要素のベンダーが拡張ポイントを提供して緊密に統合し、 \- エンドユーザーが安全かつシームレスに多要素エクスペリエンスを実現できるようにし \- ます。

-   Web アプリケーションプロキシによって保護されているエクストラネットから web リソースにアクセスするための認証と承認の機能を提供します。

要約すると、Windows Server 2012 R2 の AD FS を展開して、組織で次の目標を達成できます。

### <a name="enable-your-users-to-access-resources-on-their-personal-devices-from-anywhere"></a>ユーザーがどこからでも自分の個人用デバイス上のリソースにアクセスできるようにする

-   社内参加: ユーザー個人のデバイスが企業の Active Directory に参加できるため、そのデバイスから企業のリソースにシームレスにアクセスできます。

-   \-Web アプリケーションプロキシによって保護され、インターネットからアクセスされる企業ネットワーク内のリソースを事前に認証します。

-   社内参加デバイスからのパスワード変更: パスワードの有効期限が切れたときに、ユーザーが引き続きリソースにアクセスできるように、任意の社内参加デバイスからパスワードを変更できます。

### <a name="enhance-your-access-control-risk-management-tools"></a>アクセス制御リスク管理ツールを強化する
リスク管理は、どの IT 組織にとってもガバナンスおよびコンプライアンスの面で重要です。 Windows Server 2012 R2 の AD FS には、次のようなアクセス制御リスク管理の強化が数多くあり &reg; ます。

-   セキュリティで保護されたアプリケーション AD FS にアクセスするためにユーザーが認証する方法を、ネットワークの場所に基づいて制御する柔軟な制御 \- 。

-   ユーザーが \- ユーザーのデータ、デバイスデータ、およびネットワークの場所に基づいて multi-factor authentication を実行する必要があるかどうかを判断するための柔軟なポリシー。

-   \-アプリケーションごとの制御。 SSO を無視し、機密性の高いアプリケーションにアクセスするたびにユーザーに資格情報の入力を強制します。

-   \-ユーザーデータ、デバイスデータ、またはネットワークの場所に基づいて、アプリケーションごとのアクセスポリシーを柔軟に構成できます。

-   AD FS のエクストラネット ロックアウト。管理者がインターネットのブルート フォース攻撃から Active Directory アカウントを保護できます。

-   Active Directory で無効化されているか削除されている、社内参加対応デバイスに対するアクセスの失効。

### <a name="use-ad-fs-to-enhance-the-sign-in-experience"></a>AD FS を使用してサインインエクスペリエンスを強化する \-
Windows Server 2012 R2 の新しい AD FS 機能を次に示し &reg; ます。これにより、管理者はサインインエクスペリエンスをカスタマイズおよび強化することができ \- ます。

-   AD FS サービスの統合カスタマイズ。一度行った変更は、指定されたファームの残りの AD FS フェデレーション サーバーに自動的に反映されます。

-   \-さまざまなフォームファクターを自動的に表示する最新のサインインページが更新されました。

-   \-企業ドメインに参加していないが、引き続き企業ネットワークイントラネット内からアクセス要求を生成するデバイスに対して、フォームベース認証への自動フォールバックがサポートされるようになりました \( \) 。

-   シンプルなコントロールで、会社のロゴ、画像、IT サポートへの標準リンク、ホーム ページ、プライバシーなどをカスタマイズ。

-   サインインページでの説明メッセージのカスタマイズ \- 。

-   Web テーマのカスタマイズ。

-   \( \) 会社のパートナーのプライバシーを強化するために、ユーザーの組織サフィックスに基づくホーム領域検出 hrd。

-   アプリケーションごとに HRD フィルター処理 \- を行い、アプリケーションに基づいて領域を自動的に選択します。

-   \-IT のトラブルシューティングを容易にするワンクリックエラー報告。

-   カスタマイズ可能なエラー メッセージ。

-   ユーザー認証の選択 (複数の認証プロバイダーが使用可能な場合)。

## <a name="see-also"></a>参照
[Windows Server 2012 R2 での AD FS 設計ガイド](../../ad-fs/design/AD-FS-Design-Guide-in-Windows-Server-2012-R2.md)


