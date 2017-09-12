---
title: "Windows 10 用のアプリ保護ポリシーを構成する準備をする"
titlesuffix: Azure portal
description: "Azure AD でモバイル アプリケーション管理 (MAM) プロバイダーをセットアップします"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 52b273532935184918e65d25a37ca3d03e76680c
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Windows 10 用のアプリ保護ポリシーを構成する準備をする

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Windows 10 のアプリ保護ポリシーを作成する前に、Azure AD でモバイル アプリケーション管理 (MAM) プロバイダーを設定することにより、Windows 10 用に MAM を有効にする必要があります。 この構成を行うことで、Intune で新しい Windows 情報保護 (WIP) ポリシーを作成するときに、登録状態を定義することができます。

> [!NOTE]
> 登録状態には、MAM またはモバイル デバイス管理 (MDM) のいずれかを指定できます。

## <a name="to-configure-the-mam-provider"></a>MAM プロバイダーを構成するには

1.  [Azure Portal](https://portal.azure.com/) に移動し、Intune 資格情報でサインインします。

2.  左側のメニューで、**[Azure Active Directory]** を選択します。

    ![MAM プロバイダーの構成](./media/mam-provider-sc-1.png)

3.  **[Azure AD]** ブレードが開くので、**[モビリティ (MDM および MAM)]** を選択し、**[Microsoft Intune]** をクリックします。

    ![モビリティ MDM および MAM](./media/mam-provider-sc-1.png)

4.  構成ブレードが開くので、**[既定の MAM URL を復元する]** を最初に選んでから、以下を構成します。

    a.  [MAM ユーザー スコープ]: MAM を使って、Windows 10 デバイスを使う特定のユーザー グループまたはすべてのユーザーの企業データを保護できます。

    b.  [MAM 使用条件 URL]: MAM サービスの使用条件エンドポイントの URL です。 これは、MAM サービスの使用条件をエンドユーザーに表示するために使います。

    c.  [MAM 探索 URL]: アプリ保護ポリシーを適用する必要があるときにデバイスが探索する URL です。

    d.  [MAM 準拠 URL]:

5.  これらの設定を構成した後、**[保存]** を選びます。

## <a name="next-steps"></a>次のステップ

[WIP アプリ保護ポリシーを作成する](windows-information-protection-policy-create.md)
