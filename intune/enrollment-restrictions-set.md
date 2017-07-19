---
title: "Intune で登録制限を設定する"
titleSuffix: Intune on Azure
description: "Intune でプラットフォームごとに登録を制限し、デバイス登録の上限数を設定します。 \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2dfcba8c788f262ce816dcd23dc2921fd57f331b
ms.sourcegitcommit: d1ad84edf4f03cb4c11fe55131556b43fc3a4500
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/05/2017
---
# <a name="set-enrollment-restrictions"></a>登録制限を設定する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 管理者は、Intune による管理に登録できるデバイスを決定できます。 Intune ポータルを使って、デバイスの登録に次の制限を設定します。

- 登録されるデバイスの最大数
- 登録できるデバイスのプラットフォーム:
  - Android
  - iOS
  - macOS
  - Windows
- 個人所有デバイスの制限 (iOS および Android のみ)

>[!NOTE]
>登録の制限はセキュリティ機能ではありません。 侵害されたデバイスでは特徴が正しく示されない可能性があります。 これらの制限は、悪意のないユーザーにとって最善の防御策となります。

## <a name="set-device-type-restrictions"></a>デバイスの種類の制限を設定する
既定の登録制限は、それより高い優先度の登録制限が割り当てられていないすべてのユーザーに適用されます。  
1. Intune ポータルで **[デバイスの登録]** を選択し、**[登録の制限]** を選択します。
![既定のデバイス種類制限とデバイス数制限が表示されたバイス制限ワークスペースのスクリーンショット。](media/device-restrictions-set-default.png)
2. **[登録の制限]** > **[デバイスの種類の制限]** で、**[既定]** を選びます。
3. **[すべてのユーザー]** で、**[プラットフォーム]** を選びます。 プラットフォームごとに、**[許可]** または **[ブロック]** を選びます。
  - **Android**
  - **iOS**
  - **macOS**
  - **Windows**

  **[保存]**をクリックします。
4. **[すべてのユーザー]** で **[プラットフォーム構成]** を選び、次の構成を選びます。
  - **[個人所有]** - Android および iOS デバイスの **[許可]** または **[ブロック]** を指定します。
  ![個人所有設定の構成を示す既定デバイス プラットフォーム構成のデバイス制限ワークスペースのスクリーンショット。](media/device-restrictions-platform-configurations.png)
  **[保存]**をクリックします。

>[!NOTE]
>個人所有 Android デバイスの登録をブロックした場合でも、Android for Work デバイスは登録できます。

## <a name="set-device-limit-restrictions"></a>デバイス数の制限を設定する
既定の登録制限は、それより高い優先度の登録制限が割り当てられていないすべてのユーザーに適用されます。  
1. Intune ポータルで **[デバイスの登録]** を選択し、**[登録の制限]** を選択します。
2. **[登録制限]** > **[デバイス数の制限]** を選びます。
3. **[すべてのユーザー]** で、**[デバイスの上限数]** を選びます。 ユーザーごとに、登録可能なデバイスの最大数を指定します。  
![[デバイス数の制限] ブレードのスクリーンショット。](./media/device-restrictions-limit.png)

  **[保存]**をクリックします。
