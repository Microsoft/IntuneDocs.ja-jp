---
title: Windows デバイスの Intune 登録方法別の機能
titleSuffix: Microsoft Intune
description: Windows デバイスの登録方法別の機能です。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: dd1dbb3280fbbb93423796b18f6dd85a50a41f11
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567544"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Windows デバイスの Intune 登録方法別の機能
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

従業員のデバイスを Intune に登録する方法は複数あります。 次の表に示すように、各方法には異なるベスト プラクティスと機能があります。

## <a name="best-practices-by-enrollment-method"></a>登録方法別のベスト プラクティス
| **ベスト プラクティス** | **[Azure AD 参加済み](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Autopilot を使用した Azure AD 参加済み (ユーザー駆動型モード)](enrollment-autopilot.md)** |**[Autopilot を使用した Azure AD 参加済み (自己展開モード)](enrollment-autopilot.md)** |**[一括](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[共同管理](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|EDU でよく使用されます|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|
|デバイスは共有デバイスとして使用できます|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|
|個人のデバイスから会社のリソースにアクセスする必要があります|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|
|アプリのセルフサービス|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>登録方法別の機能

| **機能** | **[Azure AD 参加済み](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Autopilot を使用した Azure AD 参加済み (ユーザー駆動型モード)](enrollment-autopilot.md)** |**[Autopilot を使用した Azure AD 参加済み (自己展開モード)](enrollment-autopilot.md)** |**[一括](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[共同管理](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|条件付きアクセス                                      |![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|
|ユーザーはデバイスに関連付けられます                    |![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|
|Azure AD Premium が必要です                               |![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|
|デバイスで CA によって保護されたリソースを評価できます             |![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|
|ユーザーは自分のデバイスの管理者になることはできません               |![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|
|デバイスのセットアップ エクスペリエンスを構成する機能        |![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|
|ユーザー操作なしでデバイスを登録する機能      |![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|
|PowerShell スクリプトを実行する機能                       |![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)| 
|AD ドメインへの参加後の自動登録がサポートされます      |![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|
|Hybrid Azure AD への参加後の自動登録がサポートされます|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|
|Azure AD への参加後の自動登録がサポートされます       |![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|

## <a name="next-steps"></a>次の手順

[Windows の登録をセットアップする](windows-enroll.md)

