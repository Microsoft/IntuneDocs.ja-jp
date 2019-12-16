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
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 11b93d41ac09f637d6c75a3f2f4b7f4213cecec7
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74819768"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Windows デバイスの Intune 登録方法別の機能
[!INCLUDE[azure_portal](../includes/azure_portal.md)]

従業員のデバイスを Intune に登録する方法は複数あります。 次の表に示すように、各方法には異なるベスト プラクティスと機能があります。

## <a name="best-practices-by-enrollment-method"></a>登録方法別のベスト プラクティス
| **ベスト プラクティス** | **[Azure AD 参加済み](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Autopilot を使用した Azure AD 参加済み (ユーザー駆動型モード)](enrollment-autopilot.md)** |**[Autopilot を使用した Azure AD 参加済み (自己展開モード)](enrollment-autopilot.md)** |**[一括](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[共同管理](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|EDU でよく使用されます|![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|
|デバイスは共有デバイスとして使用できます|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|
|個人のデバイスから会社のリソースにアクセスする必要があります|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|
|アプリのセルフサービス|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>登録方法別の機能

| **機能** | **[Azure AD 参加済み](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Autopilot を使用した Azure AD 参加済み (ユーザー駆動型モード)](enrollment-autopilot.md)** |**[Autopilot を使用した Azure AD 参加済み (自己展開モード)](enrollment-autopilot.md)** |**[一括](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[共同管理](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|条件付きアクセス                                      |![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)\*\*|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|
|ユーザーはデバイスに関連付けられます                    |![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|
|Azure AD Premium が必要です                               |![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|
|デバイスで CA によって保護されたリソースを評価できます             |![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|
|ユーザーは自分のデバイスの管理者になることはできません               |![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|
|デバイスのセットアップ エクスペリエンスを構成する機能        |![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|
|ユーザー操作なしでデバイスを登録する機能      |![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|
|PowerShell スクリプトを実行する機能                       |![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/checkmark.png)\*| 
|AD ドメインへの参加後の自動登録がサポートされます      |![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|
|Hybrid Azure AD への参加後の自動登録がサポートされます|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|
|Azure AD への参加後の自動登録がサポートされます       |![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![チェックマーク](./media/enrollment-method-capab/checkmark.png)|![○](./media/enrollment-method-capab/xmark.png)|![○](./media/enrollment-method-capab/xmark.png)|

\* Configuration Manager のクライアント アプリのワークロードを Intune Pilot または Intune に移行する必要があります。

\** [Windows 10 1803 以降を例外として、デバイスは条件付きアクセスに対してブロックされます。](device-enrollment-manager-enroll.md)

## <a name="next-steps"></a>次の手順

[Windows の登録をセットアップする](windows-enroll.md)

