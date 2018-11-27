---
title: Windows デバイスの登録方法別の Intune 機能
titlesuffix: Microsoft Intune
description: Windows デバイスの各登録方法でサポートされる機能を確認します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 38bb88015261aa50d6c27aec026614f1205aebe8
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189811"
---
# <a name="capabilities-by-enrollment-method-for-windows-devices"></a>Windows デバイスの登録方法別の機能
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune では、従業員のデバイスやアプリ、従業員が会社のデータにアクセスする手段を管理できます。 まず、デバイスを Intune サービスに登録する必要があります。 従業員のデバイスを登録する方法は複数あります。 次の表に示すように、各方法には異なるベスト プラクティスと機能があります。

## <a name="best-practices-by-enrollment-method"></a>登録方法別のベスト プラクティス
| **ベスト プラクティス** | **[Azure AD 参加済み](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD 参加済み (Autopilot を使用)](enrollment-autopilot.md)** |**[一括](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|EDU でよく使用されます|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|
|デバイスは共有デバイスとして使用できます|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|
|個人のデバイスから会社のリソースにアクセスする必要があります|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|
|アプリのセルフサービス|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>登録方法別の機能

| **機能** | **[Azure AD 参加済み](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD 参加済み (Autopilot を使用)](enrollment-autopilot.md)** |**[一括](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|条件付きアクセス                                      |![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|
|ユーザーはデバイスに関連付けられます                    |![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|
|Azure AD Premium が必要です                               |![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|
|デバイスで CA によって保護されたリソースを評価できます             |![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|
|ユーザーは自分のデバイスの管理者になることはできません               |![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|
|デバイスのセットアップ エクスペリエンスを構成する機能        |![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|
|ユーザー操作なしでデバイスを登録する機能      |![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|
|PowerShell スクリプトを実行する機能                       |![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|![○](media/xmark.png)| 
|AD ドメインへの参加後の自動登録がサポートされます      |![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|
|Hybrid Azure AD への参加後の自動登録がサポートされます|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![○](media/xmark.png)|![チェックマーク](media/checkmark.png)|
|Azure AD への参加後の自動登録がサポートされます       |![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![チェックマーク](media/checkmark.png)|![○](media/xmark.png)|

## <a name="next-steps"></a>次の手順

[Windows の登録をセットアップする](windows-enroll.md)

