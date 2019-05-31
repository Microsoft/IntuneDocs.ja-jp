---
title: Intune から Apple に送られるデータ
titleSuffix: Microsoft Intune
description: Intune から Apple に送られるデータの一覧。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b204a956-18ec-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f1fbf8f37b989112025bd6d54328dd61246913f7
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57400213"
---
# <a name="data-intune-sends-to-apple"></a>Intune から Apple に送られるデータ

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

以下の Apple サービスのいずれかがデバイスで有効になっている場合、Microsoft Intune は Apple との接続を確立し、Apple とユーザーとデバイスの情報を共有します。 

- [Apple Device Enrollment Program (DEP)](device-enrollment-program-enroll-ios.md)
- [Apple MDM プッシュ通知証明書 (APNS)](apple-mdm-push-certificate-get.md)
- [Apple School Manager (ASM)](https://docs.microsoft.com/schooldatasync/apple-school-manager-integration-with-intune-for-education-and-school-data-sync)
- [Apple Volume Purchase Program (VPP)](vpp-apps-ios.md)

Microsoft Intune が接続を確立する前に、各 Apple サービスの Apple アカウントを作成する必要があります。

次の表は、Microsoft Intune がデバイスから有効な Apple サービスに送信するデータの一覧です。 

| サービス | Apple に送信されるデータ | 使用目的 |
|---|---| ---|
| [APNS](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | トークン、PushMagic | サーバーがデバイスを受け入れる場合、デバイスはプッシュ通知デバイス トークンをサーバーに提供します。 サーバーがプッシュ メッセージをデバイスに送信するには、このトークンを使用する必要があります。 このチェックイン メッセージには、PushMagic 文字列も含まれます。 サーバーはこの文字列を記憶し、それをデバイスに送信するすべてのプッシュ メッセージに含める必要があります。 |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | サーバー トークン | Apple サービスに対する認証に使用されるプッシュ通知デバイス トークン。 |
| ASM/DEP | server_name | MDM サーバーの識別可能な名前。 |
| ASM/DEP | server_uuid | システムで生成されるサーバー識別子。 |
| ASM/DEP | admin_id | 使用されている現在のトークンを生成した個人の Apple ID。 |
| ASM/DEP | org_name | 組織の名前。 |
| ASM/DEP | org_email | 組織の電子メール アドレス。 |
| ASM/DEP | org_phone | 組織の電話番号。 |
| ASM/DEP | org_address | 組織の住所。 |
| ASM/DEP | org_id | DEP の顧客 ID このキーは、プロトコル バージョン 3 以降でのみ使用できます。 |
| ASM/DEP | serial_number | デバイスのシリアル番号 (文字列)。 |
| ASM/DEP | 対象となるのは、モデル | モデル名 (文字列)。 |
| ASM/DEP | 説明 | デバイスの説明 (文字列)。 |
| ASM/DEP | asset_tag | デバイスの資産タグ (文字列)。 |
| ASM/DEP | profile_status | プロファイルのインストールの状態。 使用可能な値: **空**、**assigned**、**pushed**、または **removed** |
| ASM/DEP | profile_uuid | 割り当てられたプロファイルの一意の ID。 |
| ASM/DEP | device_assigned_by | デバイスを割り当てた個人の電子メール アドレス。 |
| ASM/DEP | os | デバイスのオペレーティング システム: iOS、OSX、または tvOS。 このキーは、X-Server-Protocol-Version 2 以降で有効です。 |
| ASM/DEP | device_family | デバイスの Apple 製品ファミリ: iPad、iPhone、iPod、Mac、または AppleTV。 このキーは、X-Server-Protocol-Version 2 以降で有効です。 |
| ASM/DEP | profile_name | 文字列。 人が判読できるプロファイル名。 |
| ASM/DEP | support_phone_number | 任意。 文字列。 組織のサポートの電話番号。 |
| ASM/DEP | support_email_address | 任意。 文字列。 組織のサポートの電子メール アドレス。 このキーは、X-Server-Protocol-Version 2 以降で有効です。 |
| ASM/DEP | department | 任意。 文字列。 ユーザーが定義した部門または場所の名前。 |
| ASM/DEP | デバイス | デバイスのシリアル番号を含む文字列の配列 (空にすることができます)。 |
| VPP | Intune UserId guid | Intune で生成された GUID |
| VPP | 管理対象 AppleId UPN | Apple との VPP トークン接続を構成するときに管理者が指定した Apple ID。 |
| VPP | シリアル番号 | マネージド デバイスのシリアル番号。 |

Microsoft Intune で Apple サービスの使用を停止してデータを削除するには、Microsoft Intune の Apple トークンを無効にして、Apple アカウントを削除する必要があります。 詳細については、Apple アカウントのアカウントの管理方法を参照してください。


