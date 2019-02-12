---
title: デバイス登録マネージャー アカウントを使用してデバイスを登録する
titlesuffix: Microsoft Intune
description: デバイス登録マネージャー アカウントを使用してデバイスを Intune に登録します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 20f21789be7635c19a51de8ac4dbc07b9288766c
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55837292"
---
# <a name="enroll-devices-in-intune-by-using-a-device-enrollment-manager-account"></a>デバイス登録マネージャー アカウントを使用してデバイスを Intune に登録する

デバイス登録マネージャー (DEM) アカウントを使用することで、1 つの Azure Active Directory アカウントで最大 1,000 台のモバイル デバイスを登録できます。 DEM は AAD ユーザー アカウントに適用できる Intune アクセス許可であり、ユーザーは最大 1,000 台のデバイスを登録できます。 DEM アカウントは、デバイスのユーザーに渡される前にデバイスの登録と準備を行うシナリオで役立ちます。

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>DEM アカウントで登録されるデバイスの制限事項

DEM ユーザー アカウントと DEM ユーザー アカウントを使用して登録されているデバイスには、次の制限があります。

  - ポータル サイトからはワイプできません。 DEM ユーザー アカウントで登録されたデバイスは、Azure portal で Intune からワイプできます。
  - ポータル サイト アプリまたは Web サイトには、ローカルのデバイスのみが表示されます。
  - アプリ管理のための Apple ID 要件がユーザー単位になるため、DEM ユーザー アカウントは Apple ID ユーザー ライセンスで Apple Volume Purchase Program (VPP) アプリを利用することはできません。
  - デバイスでは、Apple ID デバイス ライセンスがある場合に VPP アプリをインストールすることができます。
  - Windows 10 1803+ 以降の例外と共にデバイスが条件付きアクセスをブロックされます
  - DEM アカウントに登録されている各デバイスには、それぞれ独自の Intune デバイスのライセンスが必要です。


## <a name="add-a-device-enrollment-manager"></a>デバイス登録マネージャーの追加

1.  [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[デバイス登録マネージャー]** の順に選択します。

2.  **[追加]** を選択します。

3.  **[ユーザーの追加]** ブレードで、DEM ユーザーのユーザー プリンシパル名を入力し、**[追加]** を選択します。 DEM ユーザーが DEM ユーザーの一覧に追加されます。

## <a name="permissions-for-dem"></a>DEM のアクセス許可

次のために、グローバル管理者または Intune サービス管理者の Azure AD ロールが必要です。
- Azure AD ユーザー アカウントに DEM アクセス許可を割り当てる
- すべての DEM ユーザーを表示する

ユーザーにグローバル管理者または Intune サービス管理者のロールが割り当てられていないが、デバイス登録マネージャー ロールが割り当てられていてその読み取りアクセス許可を持っているという場合は、そのユーザー自身が作成した DEM ユーザーのみを表示できます。


## <a name="remove-device-enrollment-manager-permissions"></a>デバイス登録マネージャーのアクセス許可の削除

デバイス登録マネージャーを削除しても、登録済みのデバイスに影響はありません。

**デバイス登録マネージャーを削除するには**

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]**、**[デバイス登録マネージャー]** の順に選びます。
2. **[デバイス登録マネージャー]** ブレードで、DEM ユーザーを選択し、**[削除]** を選択します。

