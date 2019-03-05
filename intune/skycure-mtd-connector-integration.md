---
title: Symantec と Microsoft Intune の統合を設定する | Microsoft Intune
description: Microsoft Intune で Symantec Endpoint Protection Mobile ソリューションをセットアップし、モバイル デバイスから会社のリソースへのアクセスを制御する方法。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/21/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 676f34f8bc445109c2d4b86cf419f37cf291dfcc
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233374"
---
# <a name="set-up-symantec-endpoint-protection-mobile-integration-with-intune"></a>Symantec Endpoint Protection Mobile と Intune の統合を設定する

Symantec Endpoint Protection Mobile (SEP Mobile) ソリューションと Intune を統合するには、以下の手順のようにします。 シングル サインオン機能を有効にするには、SEP Mobile アプリを Azure AD に追加する必要があります。

## <a name="before-you-begin"></a>始める前に

### <a name="azure-ad-account-used-to-integrate-intune-and-sep-mobile"></a>Intune と SEP Mobile の統合に使用される Azure AD アカウント

-   SEP Mobile の基本セットアップ プロセスを始める前に、[Symantec Endpoint Protection Mobile Management コンソール](https://aad.skycure.com)で Azure AD アカウントを適切に構成する必要があります。
- Azure AD アカウントは、統合を実行する全体管理者アカウントである必要があります。
### <a name="network-setup"></a>ネットワークのセットアップ

SEP Mobile セットアップとの統合用にネットワークが正しく構成されていることを確認するには、Symantec の記事「[Setting up your network configuration](https://portal.skycure.com/articles/Documentation/Setting-up-your-network-configuration-26-8-2016)」(ネットワーク構成の設定) をご覧ください。

### <a name="full-integration-vs-read-only"></a>比較: 完全統合と読み取り専用

SEP Mobile では、Intune との統合に 2 つのモードがあります。

-   **読み取り専用統合 (基本セットアップ):** Azure Active Directory からのデバイスのインベントリのみを作成し、それらを Symantec Endpoint Protection Mobile Management コンソールに設定します。
<br>
    -   Symantec Endpoint Protection Mobile Management コンソールで **[Report the health and risk of devices to Intune]\(デバイスの健全性とリスクを Intune に報告する\)** ボックスと **[Also report security incidents to Intune]\(セキュリティ インシデントも Intune に報告する\)** ボックスがオンになっていない場合、統合は読み取り専用となり、Intune でデバイスの状態 (準拠または非準拠) が変化することはありません。
<br></br>
-   **完全統合:** リスクのあるデバイスとセキュリティ インシデントの詳細を Intune に報告することを SEP Mobile に許可します。両方のクラウド サービス間に双方向の通信が作成されます。

### <a name="how-are-the-sep-mobile-apps-used-with-azure-ad-and-intune"></a>Azure AD および Intune での SEP Mobile アプリの使用方法

-   **iOS アプリ:** エンドユーザーは iOS アプリを利用し、Azure AD にサインインできます。

-   **Android アプリ:** エンドユーザーは Android アプリを利用し、Azure AD にサインインできます。

-   **Management アプリ:** これは、Intune とのサービス間通信を可能にする SEP Mobile Azure AD マルチテナント アプリです。

## <a name="to-set-up-the-read-only-integration-between-intune-and-sep-mobile"></a>Intune と SEP Mobile の間に読み取り専用の統合を設定するには

> [!IMPORTANT]
> SEP Mobile 管理者の資格情報は、Azure Active Directory の有効なユーザーに属するメール アカウントで構成されている必要があります。そうでない場合、ログインは失敗します。 SEP Mobile は、シングル サインオン (SSO) を使った管理者の認証に、Azure Active Directory を使います。

1.  [Symantec Endpoint Protection Mobile Management コンソール](https://aad.skycure.com)に移動します。

2.  **[SEP Mobile admin credentials]\(SEP Mobile 管理者資格情報\)** を入力し、**[Continue]\(続行\)** を選びます。

3.  **[Settings]\(設定\)** に進み、**[Intune Integration]\(Intune との統合\)** で **[Basic Setup]\(基本セットアップ\)** を選びます。

4.  **[iOS App]\(iOS アプリ\)** の **[Add to Active Directory]\(Active Directory に追加\)** を選びます。

    ![Symantec Endpoint Protection Mobile Management コンソールの画像](./media/symantec-portal-basic-add.png)

5.  ログイン ページが開いたら、Intune の資格情報を入力し、**[Accept]\(同意する\)** を選びます。

    ![iOS アプリの Intune ログイン プロンプトの画像](./media/symantec-portal-basic-accept.png)

6.  アプリが Azure AD に追加された後、アプリが正常に追加されたことが示されます。

    ![iOS アプリの完了画面の画像](./media/symantec-portal-basic-added.png)

7. **SEP Mobile Android** アプリと **Management** アプリについて、同じ手順を繰り返します。

### <a name="add-an-azure-ad-security-group-into-sep-mobile"></a>SEP Mobile に Azure AD セキュリティ グループを追加する

SEP Mobile を実行しているすべてのデバイスを含む Azure AD セキュリティ グループを追加する必要があります。

-  SEP Mobile を実行しているデバイスのセキュリティ グループをすべて入力し、変更を保存します。

    ![SEP Mobile アプリのユーザー グループを示す画像](./media/symantec-portal-basic-groups.png)   

SEP Mobile は、Mobile Threat Defense サービスを実行しているデバイスと Azure AD セキュリティ グループを同期します。

![SEP Mobile 管理コンソールのセキュリティ グループの構成の画像](./media/symantec-portal-basic-status.png)

## <a name="to-set-up-the-full-integration-between-intune-and-sep-mobile"></a>Intune と SEP Mobile の間に完全統合を設定するには

### <a name="retrieve-the-directory-id-in-azure-ad"></a>Azure AD でディレクトリ ID を取得する

1. [Azure ポータル](https://portal.azure.com)にサインインします。

2. 検索ボックスに「Active Directory」と入力し、**Azure Active Directory** を選びます。

3. **[プロパティ]** を選択します。

4. **[ディレクトリ ID]** のコピー アイコンをクリックし、安全な場所に貼り付けます。 この ID は後の手順で必要になります。

    ![Azure Portal のディレクトリの ID を示す画像](./media/symantec-azure-portal-directory-ID.png)

### <a name="optional-create-a-dedicated-security-group-for-devices-that-need-to-run-the-sep-mobile-apps"></a>(省略可能) SEP Mobile アプリの実行に必要なデバイスに専用のセキュリティ グループを作成する
1. [Azure portal](https://portal.azure.com) の **[管理]** で **[ユーザーとグループ]** を選んでから、**[すべてのグループ]** を選びます。

2. **[追加]** ボタンを選びます。 グループの **[名前]** を入力します。 **[メンバーシップの種類]** で、**[割り当て済み]** を選びます。

3. **[メンバー]** ブレードでグループのメンバーを選んでから、**[選択]** ボタンを選びます。

4. **[グループ]** ブレードで、**[作成]** を選びます。

### <a name="set-up-the-integration-between-symantec-endpoint-protection-mobile-and-intune"></a>Symantec Endpoint Protection Mobile と Intune の統合を設定する

1.  [Symantec Endpoint Protection Mobile Management コンソール](https://aad.skycure.com)に移動します。

2.  **[SEP Mobile admin credentials]\(SEP Mobile 管理者資格情報\)** を入力し、**[Continue]\(続行\)** を選びます。

3.  **[Settings]\(設定\)** > **[Integrations]\(統合\)** > **[Intune]** > **[EMM Integration Selection]\(EMM 統合の選択\)** セクションの順に移動します。

4. **[Directory ID]\(ディレクトリ ID\)** ボックスに、前のセクションで Azure Active Directory からコピーしたディレクトリ ID を貼り付け、設定を保存します。

    ![SEP Mobile ポータルのディレクトリの ID を示す画像](./media/symantec-portal-directory-ID.png)     

5. **[Settings]\(設定\)** > **[Integrations]\(統合\)** > **[Intune]** > **[Basic Setup]\(基本セットアップ\)** セクションの順に移動します。

6. **[iOS App]\(iOS アプリ\)** の **[Add to Active Directory]\(Active Directory に追加\)** ボタンを選びます。

    ![Active Directory への iOS アプリの追加を示す画像](./media/symantec-portal-basic-add.png)   

7.  ディレクトリを管理する Office 365 アカウントの Azure Active Directory 資格情報を使ってサインインします。

8.  **[同意する]** ボタンを選んで、SEP Mobile iOS アプリを Azure Active Directory に追加します。

    ![[同意する] ボタンの画像](./media/symantec-portal-basic-accept.png)     

9.  **Android アプリ**と **Management アプリ**についても同じプロセスを繰り返します。

10. SEP Mobile アプリを実行する必要があるすべてのユーザー グループを選びます (前に作成したセキュリティ グループなど)。

    ![SEP Mobile アプリのユーザー グループを示す画像](./media/symantec-portal-basic-groups.png)   

11.  選択したグループのデバイスが SEP Mobile によって同期され、Intune への情報の報告が始まります。 このデータは、[Full Integration]\(完全統合\) セクションで見ることができます。 **[Settings]\(設定\)** > **[Integrations]\(統合\)** > **[Intune]** > **[Full Integration]\(完全統合\)** セクションの順に移動します。

     ![SEP Mobile の完全統合の完了を示す画像](media/symantec-portal-basic-status.PNG)
## <a name="next-steps"></a>次の手順

[SEP Mobile アプリを設定する](mtd-apps-ios-app-configuration-policy-add-assign.md)
