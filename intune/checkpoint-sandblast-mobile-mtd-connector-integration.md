---
title: Check Point SandBlast MTD の統合
titleSuffix: Microsoft Intune
description: Intune で CheckPoint SandBlast Mobile Threat Defense (MTD) をセットアップし、モバイル デバイスから会社のリソースへのアクセスを制御する方法。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1e9b1576-b239-48cc-a672-da6b5fb7be0a
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 49a6e8e625a08c9ad039d3106ff5d5c7001c2cab
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2019
ms.locfileid: "67547107"
---
# <a name="integrate-check-point-sandblast-mobile-with-intune"></a>Check Point SandBlast Mobile と Intune を統合します

## <a name="before-you-begin"></a>始める前に

> [!NOTE] 
> 以下の手順は、[Check Point SandBlast Mobile MTD コンソール](https://intune-4.eu1.locsec.net/)で行う必要があります。

Check Point SandBlast Mobile と Intune の統合を始める前に、次のものがあることを確認します。

- Microsoft Intune サブスクリプション

- 次のアクセス許可を付与する Azure Active Directory 管理者資格情報:

    - サインインしてユーザー プロファイルを読み取る

    - サインインしたユーザーとしてディレクトリにアクセスする

    - ディレクトリ データの読み込み

    - Intune にデバイス情報を送信する

- Check Point SandBlast Mobile MTD コンソールにアクセスするための管理者資格情報

### <a name="check-point-sandblast-app-authorization"></a>Check Point SandBlast アプリの承認

Check Point SandBlast アプリ承認プロセスは以下で構成されます。

- Check Point SandBlast Mobile サービスがデバイスの正常性状態に関する情報を Intune に通知できるようにします。

- Check Point SandBlast Mobile は、Azure AD 登録グループ メンバーシップと同期してデバイスのデータベースを設定します。

- Check Point SandBlast 管理者コンソールが Azure AD シングル サインオン (SSO) を使用できるようにします。

- Check Point SandBlast Mobile アプリが Azure AD SSO を使ってサインインできるようにします。

## <a name="to-set-up-check-point-sandblast-mobile-integration"></a>Check Point SandBlast Mobile の統合をセットアップするには

1. [Check Point SandBlast Mobile MTD コンソール](https://intune-4.eu1.locsec.net/)に移動し、資格情報でサインインします。

2. **[設定]** タブをクリックします。

3. **[Device management\(デバイス管理\)]** 、 **[設定]** の順に選択します。

4. **[MDM Service\(MDM サービス\)]** ドロップダウン リストから **[Microsoft Intune]** を選択します。

5. Microsoft Intune を MDM サービスとして設定するとポップアップする **[Microsoft Intune Configuration\(Microsoft Intune の構成\)]** ウィンドウで、各デバイス プラットフォーム (iOS、Android、Windows) の **[Add to my organization\(組織に追加する\)]** を選択して、Check Point SandBlast Mobile が Intune および Azure AD と通信することを承認します。

    ![Check Point MTD Intune の構成を示す画像](./media/checkpoint-MTD-1.PNG)

    > [!IMPORTANT]
    > 次の手順に進むには、すべてのデバイス プラットフォームを追加する必要があります。

6. **[Accept\(承認\)]** を選択して、Check Point SandBlast Mobile アプリが Intune および Azure Active Directory と通信することを承認します。

7. すべてのデバイス プラットフォームを有効にした後、Azure AD セキュリティ グループを入力する必要があります。

8. **[Verify\(確認\)]** を選択し、Azure AD セキュリティ グループが正常に検証された後、 **[保存]** を選択します。

## <a name="next-steps"></a>次の手順

- [Check Point SandBlast Mobile アプリをセットアップする](mtd-apps-ios-app-configuration-policy-add-assign.md)
