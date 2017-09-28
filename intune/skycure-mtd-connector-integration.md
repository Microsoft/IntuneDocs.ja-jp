---
title: "Skycure と Intune の統合をセットアップする"
titlesuffix: Azure portal
description: "Skycure と Microsoft Intune の統合をセットアップします。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d495046a990817e73fcee385b3a1482229aac721
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2017
---
# <a name="set-up-the-skycure-integration-with-intune"></a>Skycure と Intune の統合をセットアップする

シングル サインオン機能を与えるには、Skycure アプリを Azure AD に追加する必要があります。

## <a name="before-you-begin"></a>始める前に

### <a name="azure-ad-account-used-to-integrate-intune-and-skycure"></a>Intune と Skycure を統合するために使用する Azure AD アカウント

-   Skycure の基本セットアップ プロセスを開始する前に、[Skycure 管理コンソール](https://aad.skycure.com)で Azure AD アカウントを適切に構成する必要があります。

### <a name="full-integration-vs-read-only"></a>比較: 完全統合と読み取り専用

Skycure では、Intune との統合に 2 つのモードがあります。

-   **読み取り専用統合 (基本セットアップ):** Azure Active Directory からのデバイスのみが目録を作成し、それらを Skycure コンソールに入力します。
<br>
    -   Skycure 管理コンソールで [**Report the health and risk of devices to Intune (デバイスの健全性とリスクを Intune に報告する)**] ボックスと [**Also report security incidents to Intune (セキュリティ インシデントも Intune に報告する)**] ボックスが選択されていない場合、統合は読み取り専用となり、Intune でデバイスの状態 (準拠または非準拠) が変化することはありません。
<br></br>
-   **完全統合:** デバイスのリスクとセキュリティ インシデントの詳細を Intune に報告することを Skycure に許可します。Intune は両方のクラウド サービス間で双方向通信を構築します。

### <a name="how-the-skycure-apps-are-used-with-azure-ad-and-intune"></a>Azure AD と Intune で Skycure アプリはどのような方法で使用されますか?

-   **iOS アプリ:** エンドユーザーは iOS アプリを利用し、Azure AD にサインインできます。

-   **Android アプリ:** エンドユーザーは Android アプリを利用し、Azure AD にサインインできます。

-   **管理アプリ:** これは、Intune とのサービス間通信を可能にする Skycure Azure AD マルチテナント アプリです。

## <a name="to-set-up-the-read-only-integration-between-intune-and-skycure"></a>Intune と Skycure の間に読み取り専用の統合を設定するには

> [!IMPORTANT]
> Skycure 管理者の資格情報は電子メールですが、そのメールは Azure Active Directory の有効なユーザーに属している必要があります。属していない場合、ログインは失敗します。 Skycure は、シングル サインオン (SSO) を使用して、管理者の認証に Azure Active Directory を使用します。

1.  [Skycure 管理コンソール](https://aad.skycure.com)に進みます。

2.  自分の **Skycure 管理者資格情報**を入力し、**[続行]** をクリックします。

3.  **[設定]** に進み、**[Intune との統合]** で **[基本セットアップ]** を選択します。

4.  **[iOS アプリ]** ラベルで、**[Add to Active Directory (Active Directory に追加)]** をクリックします。

    ![Skycure 管理コンソールの iOS アプリ](./media/skycure-setup-1.png)

5.  ログイン ページが開いたら、Intune 資格情報を入力し、**[同意する]** をクリックします。

    ![iOS アプリの Intune ログイン プロンプト](./media/skycure-setup-2.png)

6.  アプリが Azure AD に追加されると、Skycure 管理コンソールでアプリが Azure AD に追加されたというメッセージが表示されます。

    ![iOS アプリの完了画面](./media/skycure-setup-3.png)

> [!NOTE]
> **Skycure Android** アプリと**管理**アプリで同じプロセスを繰り返します。

### <a name="add-an-azure-ad-security-group-into-skycure"></a>Skycure に Azure AD セキュリティ グループを追加する

Skycure を実行しているすべてのデバイスを含む Azure AD セキュリティ グループを追加する必要があります。

1.  Skycure を実行しているデバイスのセキュリティ グループをすべて入力し、選択し、**[変更の適用]** をクリックします。

    ![セキュリティ グループ Skycure 管理コンソールを構成する](./media/skycure-setup-4.png)

Skycure は、Mobile Threat Defense サービスを実行しているデバイスと Azure AD セキュリティ グループを同期します。

![Skycure 管理コンソールで完了したセキュリティ グループの構成](./media/skycure-setup-5.png)

## <a name="set-up-the-full-integration-between-intune-and-skycure"></a>Intune と Skycure の間に完全統合を設定する

1.  [Skycure 管理コンソール](https://aad.skycure.com)に進みます。

2.  自分の **Skycure 管理者資格情報**を入力し、**[続行]** をクリックします。

3.  **[設定]** に進み、**[Intune との統合]** で **[完全統合]** を選択します。

4.  次の設定を確認してください。

    a.  デバイスの健全性とリスクを Intune に報告する

    b.  セキュリティ インシデントも Intune に報告する

5.  **[変更の適用]** をクリックします。

    ![Skycure の完全統合の完了](./media/skycure-setup-6.png)

## <a name="next-steps"></a>次のステップ

[Skycure アプリを設定する](mtd-apps-ios-app-configuration-policy-add-assign.md)
