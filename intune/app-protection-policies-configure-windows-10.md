---
title: "Windows 10 用のアプリ保護ポリシーを構成する準備をする"
titlesuffix: Azure portal
description: "Azure AD でモバイル アプリケーション管理 (MAM) プロバイダーをセットアップします"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e36998236515f66f65817497522496874c92f5a2
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Windows 10 用のアプリ保護ポリシーを構成する準備をする

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Azure AD で MAM プロバイダーを設定して、Windows 10 用モバイル アプリケーション管理 (MAM) を有効にします。 Azure AD で MAM プロバイダーを設定することで、Intune で新しい Windows 情報保護 (WIP) ポリシーを作成するときに、登録状態を定義することができます。 登録状態には、MAM またはモバイル デバイス管理 (MDM) のいずれかを指定できます。

> [!NOTE]
> MAM の登録状態を持つデバイスは、Azure AD に参加している必要があります。

## <a name="to-configure-the-mam-provider"></a>MAM プロバイダーを構成するには

1. Azure Portal にサインインして、**[Azure Active Directory]** を選択します。

2. **[管理]** グループで **[モビリティ (MDM および MAM)]** を選択します。

3. **[Microsoft Intune]** をクリックします。

4. **[構成]** ブレードの **[既定の MAM URL を復元する]** グループで設定を構成します。

   **MAM ユーザー スコープ**  
   MAM の自動登録を使用して、従業員の Windows デバイス上のエンタープライズ データを管理します。 MAM 自動登録は、Bring Your Own Device シナリオ向けに構成されます。<ul><li>**なし**<br>MAM に登録できるユーザーがいない場合に選択します。</li><li>**一部**<br>MAM に登録するユーザーが含まれる Azure AD グループを選択します。</li><li>**すべて**<br>MAM にすべてのユーザーを登録する場合に選択します。</li></ul>

   **MAM 使用条件 URL**  
   MAM 使用条件 URL は、Microsoft Intune ではサポートされていません。 保護ポリシーを適用するには、この入力ボックスを空白のままにする必要があります。

   **MAM 探索 URL**  
   MAM サービスの登録エンドポイントの URL です。 登録エンドポイントを使用して、MAM サービスによる管理の対象となるデバイスを登録します。

   **MAM 準拠 URL**  
   MAM 準拠 URL は、Microsoft Intune ではサポートされていません。 保護ポリシーを適用するには、この入力ボックスを空白のままにする必要があります。 

5.  **[Save]**(保存) をクリックします。

## <a name="next-steps"></a>次の手順

[WIP アプリ保護ポリシーを作成する](windows-information-protection-policy-create.md)
