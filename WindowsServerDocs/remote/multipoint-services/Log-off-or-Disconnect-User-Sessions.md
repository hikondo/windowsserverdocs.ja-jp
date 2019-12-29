---
title: ユーザー セッションをログオフまたは切断する
description: ユーザーを手動でログオフする方法について説明します。
ms.custom: na
ms.prod: windows-server
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3e9bbcdc-e33b-481e-8b46-787a4f6d58bc
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/04/2016
ms.openlocfilehash: c636af35a78eab76d69c68b6f506b64dcb555f81
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71395269"
---
# <a name="log-off-or-disconnect-user-sessions"></a>ユーザー セッションをログオフまたは切断する
MultiPoint Services のユーザーは、Windows セッションの場合と同様に、デスクトップセッションにログオンしてログオフできます。 また、ユーザーは、MultiPoint Services ステーションが使用されないようにセッションを切断または中断することができますが、そのセッションは MultiPoint Services システムのコンピューターメモリ内でアクティブなままになります。  
  
さらに、ユーザーが MultiPoint Services セッションから移動した場合、またはシステムからログオフし忘れた場合、管理ユーザーはユーザーのセッションを終了できます。  
  
## <a name="logging-off-or-disconnecting-a-session"></a>セッションのログオフまたは切断  
次の表では、管理者またはユーザーがセッションのログオフ、中断、または終了に使用できるさまざまなオプションについて説明します。  
  
|||  
|-|-|  
|**操作**|**とき**|  
|**[スタート]** ボタンをクリックし、設定 をクリックして、ユーザー名 (右上隅) をクリックし、 **[サインアウト]** をクリックします。|セッションは終了し、ステーションは任意のユーザーによるログオンに使用できます。|  
|**[開始]** をクリックし、 **[設定]** をクリックし、[電源] をクリックして、 **[切断]** をクリックします。|セッションは切断されますが、コンピューターのメモリ内に保持されています。 ステーションは、同じユーザーまたは別のユーザーによるログオンに使用できるようになります。|  
|**[スタート]** ボタンをクリックし、設定 をクリックして、ユーザー名 (右上隅) をクリックし、 **[ロック]** をクリックします。|ステーションはロックされ、セッションはコンピューターのメモリ内に保持されています。|  
  
## <a name="suspending-or-ending-a-users-session"></a>ユーザーのセッションを中断または終了する  
次の表では、管理ユーザーがユーザーのセッションを切断または終了するために使用できるさまざまなオプションについて説明します。  
  
|||  
|-|-|  
|**操作**|**とき**|  
|**中断**MultiPoint マネージャーでは、 **[ステーション]** タブを使用して、ユーザーのセッションを中断します。 詳細については、「[ユーザー セッションを中断してアクティブな状態で保持する](Suspend-and-Leave-User-Session-Active.md)」トピックを参照してください。|ユーザーのセッションは終了し、コンピューターのメモリに保持されます。 ステーションは、同じユーザーまたは別のユーザーによるログオンに使用できるようになります。 ユーザーは、同じステーションまたは別のステーションにログオンし、仕事を続けることができます。|  
|**終わり：** MultiPoint マネージャーで、 **[ステーション]** タブを使用して、ユーザーのセッションを終了します。 **[ステーション]** タブではすべてのユーザー セッションを終了することもできます。詳細については、「[ユーザー セッションの終了](End-a-User-Session.md)」トピックを参照してください。|ユーザーのセッションが終了し、ステーションは任意のユーザーがログオンできるようになります。 ユーザーのセッションは **[ステーション]** タブに表示されなくなり、コンピューターのメモリには表示されません。|  
  
## <a name="see-also"></a>関連項目  
[ユーザーセッションを中断してアクティブのままにする](Suspend-and-Leave-User-Session-Active.md)  
[ユーザー セッションを終了する](End-a-User-Session.md)  
[ユーザーデスクトップの管理](manage-user-desktops-using-multipoint-dashboard.md)  
[ユーザー セッションをログオフする](Log-Off-User-Sessions.md)    