---
title: "インベントリでデバイスを把握する"
description: "Intune を使用して、管理するデバイスのハードウェアに関する情報を表示します。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e50a7329512e6b57eb5486792669b7cd102eebdb
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="understand-your-devices-with-inventory-in-microsoft-intune"></a>Microsoft Intune でインベントリを使用してデバイスを把握する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune では、Intune クライアント ソフトウェアを実行している、登録済みデバイスと Windows PC のインベントリを表示できます。
Intune は通常、7 日ごとに管理対象デバイスからインベントリを収集します。 このため、デバイス名の変更など、デバイスに対する最近の変更結果や記憶域の空き容量をレポートが表示する際に、遅延が発生する可能性があります。

## <a name="whats-collected-from-enrolled-devices"></a>登録済みデバイスから収集される情報
モバイル デバイスで収集されたインベントリを表示するには、[モバイル デバイスのインベントリ レポート](understand-microsoft-intune-operations-by-using-reports.md)を実行します。 Intune では、登録済みデバイスから次のインベントリを収集します。

|プロパティ|デバイスの種類|
|------------|-----------------------|
|**名前**|All のいずれかのデバイス|
|**オペレーティング システム**|All のいずれかのデバイス|
|**製造元**|All のいずれかのデバイス|
|**モデル**|All のいずれかのデバイス|
|**管理チャネル**|All のいずれかのデバイス|
|**AAD に登録済み**|Mac OS X を除くすべてのデバイス|
|**対応**|All のいずれかのデバイス|
|**EAS アクティブ化**|Mac OS X を除くすべてのデバイス|
|**EAS アクティブ化 ID**|Mac OS X を除くすべてのデバイス|
|**EAS アクティブ化時刻**|Mac OS X を除くすべてのデバイス|
|**管理状態**|All のいずれかのデバイス|
|**電子メール アドレス**|All のいずれかのデバイス|
|**Exchange ActiveSync ID**|All のいずれかのデバイス|
|**脱獄またはルート化**|iOS デバイスと Android デバイスのみ|
|**一意のデバイス ID**|Exchange ActiveSync を除くすべてのデバイス|
|**シリアル番号**|iOS、Mac OS X、Android、Windows 8.1、Windows 10 デスクトップ デバイス|
|**記憶域の合計容量**|iOS、Mac OS X、Windows 8.1、および Windows 10 デスクトップおよびモバイル デバイス|
|**記憶域の空き容量**|iOS、Mac OS X、Windows 8.1、および Windows 10 デスクトップ デバイス|
|**電話番号**<br>会社の所有として分類される電話は、完全な電話番号で識別されます (モバイル デバイスのインベントリ レポートを実行するときなど)。 BYOD デバイスの電話番号は &#42; でマスクされ、表示されるのは最後の 4 桁のみとなります。|iOS、Android、Windows Phone の各デバイス|
|**IMEI**|Exchange ActiveSync、iOS、Android、Windows Phone の各デバイス|
|**MEID**<br>Mobile Equipment Identifier|iOS デバイスのみ|
|**Wi-Fi MAC**|Exchange ActiveSync を除くすべてのデバイス|
|**通信事業者**|iOS デバイスと Android デバイスのみ|
|**通信方式**|iOS デバイスと Android デバイスのみ|
|**監督下**|iOS デバイスのみ|
|**アクティブ化ロック状態**|iOS デバイスのみ|
|**登録日**|All のいずれかのデバイス|
|**最終更新日時**|All のいずれかのデバイス|
|**イーサネット MAC**|Mac OS X デバイスのみ|
|**アクティブ化ロック有効**|iOS デバイスのみ|
|**暗号化有効**|All のいずれかのデバイス|

>[!NOTE]
>上記項目の一部は、デバイスで利用している通信事業者によっては収集されない場合があります。

## <a name="whats-collected-from-windows-pcs"></a>Windows PC から収集される情報
> [!IMPORTANT]
> このセクションの情報は、Intune の Windows PC クライアント ソフトウェアを実行する Windows PC にのみ適用されます。

Windows PC で収集されたインベントリを表示するには、[コンピューター インベントリ レポート](understand-microsoft-intune-operations-by-using-reports.md)を実行します。 Intune では、Windows PC から次のインベントリを収集します。

-   **名前**

-   **シャーシの種類**

-   **製造元**

-   **モデル**

-   **オペレーティング システム**

-   **TPM バージョン**

-   **ディスク領域の合計**

-   **使用済みディスク領域**

-   **ディスクの空き領域**

-   **OS ディスク名**

-   **OS ディスク領域**

-   **OS ディスクの空き領域**

-   **物理メモリ**

-   **プロセッサー名**

-   **プロセッサーのアーキテクチャ**

-   **CPU 速度**

-   **IP アドレス**

-   **シリアル番号**

-   **最終ログオン ユーザー**

-   **割り当てられたユーザー**

-   **最終更新日時**

<!-- this section below belongs in the planning journey
### See Also
[Monitoring and reports with Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
-->
