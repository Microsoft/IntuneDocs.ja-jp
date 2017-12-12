---
title: "Windows 10 用のアプリ保護ポリシーを構成する準備をする"
titlesuffix: Azure portal
description: "Azure AD でモバイル アプリケーション管理 (MAM) プロバイダーをセットアップします"
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 10/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 91e26256d220ba70e5ad6daa3910d34eea8bb5ed
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
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
      MAM の自動登録を使用して、従業員の Windows デバイス上のエンタープライズ データを管理します。 MAM 自動登録は、Bring Your Own Device シナリオ向けに構成されます。<ul><li>**なし**<br>MAM にすべてのユーザーを登録する場合に選択します。</li><li>**一部**<br>MAM に登録するユーザーが含まれる Azure AD グループを選択します。</li><li>**すべて**<br>MAM にすべてのユーザーを登録する場合に選択します。</li></ul>

    **MAM 使用条件 URL**  
     MAM サービスの使用条件エンドポイントの URL です。 使用条件エンドポイントを使用して、管理対象のデバイスを登録する前に、エンド ユーザーにサービス利用規約を表示できます。 使用条件のテキストは、モバイル デバイスに適用されるポリシーについてユーザーに案内します。

    **MAM 探索 URL**  
    MAM サービスの登録エンドポイントの URL です。 登録エンドポイントを使用して、MAM サービスによる管理の対象となるデバイスを登録します。

    **MAM 準拠 URL**  
      MAM サービスの準拠エンドポイントの URL です。 準拠していないデバイスからユーザーがリソースにアクセスしようとして拒否された場合は、準拠 URL へのリンクがユーザーに表示されます。 ユーザーは MAM サービスによってホストされるこの URL にアクセスすることで、デバイスが準拠していないと見なされる理由を知ることができます。 また、ユーザーはセルフサービス修復を開始してデバイスを準拠した状態にしてから、リソースへのアクセスを続行することもできます。

5.  **[Save]**(保存) をクリックします。

## <a name="next-steps"></a>次のステップ

[WIP アプリ保護ポリシーを作成する](windows-information-protection-policy-create.md)
