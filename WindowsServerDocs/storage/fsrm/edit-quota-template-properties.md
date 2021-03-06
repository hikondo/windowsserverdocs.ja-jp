---
title: クォータ テンプレートのプロパティを編集する
description: この記事では、クォータ テンプレートのプロパティを編集して、元のクォータ テンプレートから作成されたクォータにも変更を適用する方法を説明します。
ms.date: 7/7/2017
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 4e8a112f26f2b0ffdf8047063411dbb5539f4eb1
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87961416"
---
# <a name="edit-quota-template-properties"></a>クォータ テンプレートのプロパティを編集する

> 適用対象: Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2

クォータ テンプレートを変更したときに、過去に元のファイル スクリーン テンプレートから作成されたクォータにもその変更を適用することができます。 元のテンプレートと現在も一致しているクォータのみを変更するか、クォータが作成後に変更されているかどうかにかかわらず、元のテンプレートから取得したすべてのクォータを変更するかを選択できます。 この機能では、すべての更新を 1 か所で集中的に実行できるため、クォータのプロパティの更新処理が簡略化されます。

> [!Note]
> 元のテンプレートから取得したすべてのクォータに変更を適用すると、それまでに作成されたカスタム クォータ プロパティがすべて上書きされます。

## <a name="to-edit-quota-template-properties"></a>クォータ テンプレートのプロパティを編集するには

1.  **[クォータのテンプレート]** で、変更するテンプレートを選択します。

2.  クォータのテンプレートを右クリックして **[テンプレートのプロパティの編集]** をクリックするか、**[操作]** ウィンドウで **[指定したクォータのテンプレート]** の **[テンプレートのプロパティの編集]** をクリックします。 **[クォータ テンプレートのプロパティ]** ダイアログ ボックスが表示されます。

3.  必要なすべての変更を行います。 設定と通知のオプションは、クォータのテンプレートの作成時に利用できるオプションと同じです。 必要に応じて、別のテンプレートのプロパティをコピーして、このテンプレート用にプロパティを変更することもできます。

4.  テンプレートのプロパティの編集が完了したら、**[OK]** をクリックします。 **[テンプレートから取得したクォータの更新]** ダイアログ ボックスが表示されます。

5.  適用する更新の種類を選択します。

    -   元のテンプレートから作成された後に変更されたクォータを変更しない場合は、**[元のテンプレートに一致する取得したクォータのみにテンプレートを適用する]** をクリックします。 このオプションでは、元のテンプレートを使用して作成されてから編集されていないクォータのみが更新されます。
    -   元のテンプレートを使用して作成された既存のすべてのクォータを変更する場合は、**[取得したクォータすべてにテンプレートを適用する]** を選択します。
    -   既存のクォータをすべて変更しない場合は、**[取得したクォータにテンプレートを適用しない]** を選択します。

6.  **[OK]** をクリックします。

## <a name="additional-references"></a>その他の参照情報

-   [クォータの管理](quota-management.md)
-   [クォータテンプレートを作成する](create-quota-template.md)


