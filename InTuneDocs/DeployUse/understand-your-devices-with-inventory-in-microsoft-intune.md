---
title: "インベントリを使用してデバイスを把握する | Microsoft Intune"
description: "Intune を使用して、管理するデバイスのハードウェアに関する情報を表示します。"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/17/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: df4e0bc8a818f22d6f7327f9f1348f67882e0c49
ms.openlocfilehash: 80b157c021099513854b8ffc1fe09cd2922ee0c2


---

# Microsoft Intune でインベントリを使用してデバイスを把握する
Microsoft Intune では、Intune クライアント ソフトウェアを実行している、登録済みデバイスと Windows PC のインベントリを表示できます。

## 登録済みデバイスから収集される情報
モバイル デバイスで収集されたインベントリを表示するには、[モバイル デバイスのインベントリ レポート](understand-microsoft-intune-operations-by-using-reports.md)を実行します。 Intune では、登録済みデバイスから次のインベントリを収集します。

|プロパティ|デバイスの種類|
|------------|-----------------------|
|**名前**|All のいずれかのデバイス|
|**オペレーティング システム**|All のいずれかのデバイス|
|**製造元**|All のいずれかのデバイス|
|**モデル**|All のいずれかのデバイス|
|**管理チャネル**|All のいずれかのデバイス|
|**AAD に登録済み**|Mac OS X を除くすべてのデバイス|
|**準拠**|All のいずれかのデバイス|
|**EAS アクティブ化**|Mac OS X を除くすべてのデバイス|
|**EAS アクティブ化 ID**|Mac OS X を除くすべてのデバイス|
|**EAS アクティブ化時刻**|Mac OS X を除くすべてのデバイス|
|**管理状態**|All のいずれかのデバイス|
|**Email Address**|All のいずれかのデバイス|
|**Exchange ActiveSync ID**|All のいずれかのデバイス|
|**脱獄またはルート化**|iOS デバイスと Android デバイスのみ|
|**一意のデバイス ID**|Exchange ActiveSync を除くすべてのデバイス|
|**シリアル番号**|iOS、Mac OS X、Android、Windows 8.1、Windows 10 の各デバイス|
|**記憶域の合計容量**|iOS、Mac OS X、Windows 8.1、Windows 10 の各デバイス|
|**記憶域の空き容量**|iOS、Mac OS X、Windows 8.1、Windows 10 の各デバイス|
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

## Windows PC から収集される情報
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

-   **プロセッサ名**

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



<!--HONumber=Aug16_HO3-->


