---
title: "Windows 10 用のアプリ保護ポリシーを構成する準備をする | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Azure AD でモバイル アプリケーション管理 (MAM) プロバイダーをセットアップします"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 9490951b2953f8b8c6fe3d38824053bbe75f9af1
ms.contentlocale: ja-jp
ms.lasthandoff: 05/10/2017


---

# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Windows 10 用のアプリ保護ポリシーを構成する準備をする

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Windows 10 のアプリ保護ポリシーを作成する前に、Azure AD でモバイル アプリケーション管理 (MAM) プロバイダーを設定することにより、Windows 10 用に MAM を有効にする必要があります。 この構成を行うことで、Intune で新しい Windows 情報保護 (WIP) ポリシーを作成するときに、登録状態を定義することができます。

> [!NOTE]
> 登録状態には、MAM またはモバイル デバイス管理 (MDM) のいずれかを指定できます。

## <a name="to-configure-the-mam-provider"></a>MAM プロバイダーを構成するには

1.  [Azure Portal](https://portal.azure.com/) に移動し、Intune 資格情報でサインインします。

2.  左側のメニューで、**[Azure Active Directory]** を選択します。

    ![MAM プロバイダーの構成](../media/AppManagement/mam-provider-sc-1.png)

3.  **[Azure AD]** ブレードが開くので、**[モビリティ (MDM および MAM)]** を選択し、**[Microsoft Intune]** をクリックします。

    ![モビリティ MDM および MAM](../media/AppManagement/mam-provider-sc-1.png)

4.  構成ブレードが開くので、**[既定の MAM URL を復元する]** を最初に選んでから、以下を構成します。

    a.  [MAM ユーザー スコープ]: MAM を使って、Windows 10 デバイスを使う特定のユーザー グループまたはすべてのユーザーの企業データを保護できます。

    b.  [MAM 使用条件 URL]: MAM サービスの使用条件エンドポイントの URL です。 これは、MAM サービスの使用条件をエンドユーザーに表示するために使います。

    c.  [MAM 探索 URL]: アプリ保護ポリシーを適用する必要があるときにデバイスが探索する URL です。

    d.  [MAM 準拠 URL]:

5.  これらの設定を構成した後、**[保存]** を選びます。

## <a name="next-steps"></a>次のステップ

[WIP アプリ保護ポリシーを作成する](https://docs.microsoft.comcreate-windows-information-protection-policy-with-intune.md)

