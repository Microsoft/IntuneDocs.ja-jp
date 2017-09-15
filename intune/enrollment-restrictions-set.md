---
title: "Intune で登録制限を設定する"
titlesuffix: Azure portal
description: "Intune でプラットフォームごとに登録を制限し、デバイス登録の上限数を設定します。 \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 06c0c58992a2119aff7fd5be54ae90be886d2a53
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="set-enrollment-restrictions"></a>登録制限を設定する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 管理者は、Intune による管理に登録できるデバイスを決定できます。 Azure Portal を使って、デバイスの登録に次の制限を設定します。

- 登録されるデバイスの最大数
- 登録できるデバイスのプラットフォーム:
  - Android
  - iOS
  - macOS
  - Windows
- プラットフォームのオペレーティング システム バージョン (iOS および Android のみ)
  - 最小バージョン
  - 最大バージョン
- 個人所有デバイスの制限 (iOS、Android、macOS のみ)

>[!NOTE]
>登録の制限はセキュリティ機能ではありません。 侵害されたデバイスでは特徴が正しく示されない可能性があります。 これらの制限は、悪意のないユーザーにとって最善の防御策となります。

## <a name="set-device-type-restrictions"></a>デバイスの種類の制限を設定する
既定の登録の制限は、すべてのユーザーとユーザーなし登録に適用されます。
1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[デバイスの登録]** > **[登録の制限]** を選択します。
4. **[登録の制限]** > **[デバイスの種類の制限]** で、**[既定]** を選びます。
5. **[すべてのユーザー]** で、**[プラットフォーム]** を選びます。 プラットフォームごとに、**[許可]** または **[ブロック]** を選びます。
  - **Android**
  - **iOS**
  - **macOS**
  - **Windows**

  **[Save]**(保存) をクリックします。
6. **[すべてのユーザー]** で **[プラットフォーム構成]** を選び、次の構成を選びます。 許可されているプラットフォームごとに、次のオプションを構成できます。
  - **[バージョン]** - Android および iOS デバイスの **[最小]** と **[最大]** のプラットフォーム オペレーティング システム バージョンを指定します。 オペレーティング システムのバージョンは、Device Enrollment Program、Apple School Manager、または Apple Configurator アプリを使用して登録するデバイスには適用されません。
  - **[個人所有]** - Android、iOS、および macOS デバイスの **[許可]** または **[ブロック]** を指定します。
  ![個人所有設定の構成を示す既定デバイス プラットフォーム構成のデバイス制限ワークスペースのスクリーンショット。](media/device-restrictions-platform-configurations.png)
  **[Save]**(保存) をクリックします。

>[!NOTE]
>個人所有の Android デバイスの登録をブロックした場合でも、個人所有の Android for Work デバイスは登録できます。

## <a name="set-device-limit-restrictions"></a>デバイス数の制限を設定する
既定の登録の制限は、すべてのユーザーに適用されます。
1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[デバイスの登録]** > **[登録の制限]** を選択します。
4. Azure Portal で **[デバイスの登録]** を選択し、**[登録の制限]** を選択します。
5. **[登録制限]** > **[デバイス数の制限]** を選びます。
6. **[すべてのユーザー]** で、**[デバイスの上限数]** を選びます。 ユーザーごとに、登録可能なデバイスの最大数を指定します。  
![[デバイス数の制限] ブレードのスクリーンショット。](./media/device-restrictions-limit.png)

  **[保存]**をクリックします。
