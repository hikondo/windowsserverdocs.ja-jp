---
title: Windows Server Essentials でのバックアップと復元の管理
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 41000915-f6ff-4dbb-b7be-629ef36386d4
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 2f42cd78bb5cc3198421edccd32c05e2eada7be0
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87181038"
---
# <a name="manage-backup-and-restore-in-windows-server-essentials"></a>Windows Server Essentials でのバックアップと復元の管理

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

 Windows Server Essentials を導入すれば、信頼できる方法でサーバーの通常バックアップとネットワーク コンピューターのバックアップを実行できます。 データが失われた場合、コンピューター全体を復元しなくても、サーバーのバックアップからデータを復元できます。 必要であれば、システム全体をネットワークにあるサーバーまたはクライアント コンピューターに復元できます。 次の表は、利用できるさまざまなバックアップ オプションとその長所をまとめたものです。

|バックアップ機能|説明|長所|
|--------------------|-----------------|----------------|
|サーバー バックアップ|Windows Server Essentials を実行しているサーバーをバックアップします。 データは外部 USB ドライブにバックアップされます。<br /><br /> 詳細については、「サーバー[バックアップの管理](Manage-Server-Backup-in-Windows-Server-Essentials.md)」および「[サーバーの復元または修復](Restore-or-repair-your-server-running-Windows-Server-Essentials.md)」を参照してください。|-サーバー上のファイルとフォルダーを復元できます。<br /><br /> -サーバーのシステムの完全復元を実行できます。|
|クライアント コンピューター バックアップ|ネットワークのクライアント コンピューターをバックアップします。 データは Windows Server Essentials を実行しているサーバーにバックアップされます。<br /><br /> 詳細については、「[クライアントのバックアップを管理](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md)する」および「既存の[クライアントコンピューターのバックアップから完全なシステムを復元する](Restore-a-full-system-from-an-existing-client-computer-backup.md)」を参照してください。|-サーバーからファイルとフォルダーを復元できます。<br /><br /> -クライアントコンピューターのシステムの完全復元を実行できます。|
| Microsoft Azure Backup|サーバーのファイルまたはフォルダーのオンライン バックアップを実行します。 Azure Backup を使用してサーバーデータをバックアップする場合、インターネット上のセキュリティで保護されたデータセンターにアップロードされる前に、パスフレーズを使用して情報が暗号化されます。<br /><br /> 詳細については、「[オンラインバックアップの管理](Manage-Online-Backup-in-Windows-Server-Essentials.md)」を参照してください。|-サーバーからファイルとフォルダーを復元できます。<br /><br /> -増分バックアップでは、ファイルに対する変更のみがクラウドに転送されます。<br /><br /> -バックアップは Microsoft Azure に格納され、オフサイトであるため、オンサイトのバックアップメディアをセキュリティで保護する必要が少なくなります。|

## <a name="additional-references"></a>その他のリファレンス

-   [Windows Server Essentials の管理](Manage-Windows-Server-Essentials.md)

-   [Windows Server Essentials の使用](../use/Use-Windows-Server-Essentials.md)
