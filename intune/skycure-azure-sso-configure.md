---
title: "Intune で Azure AD シングル サインオンを使用するように Skycure を構成する"
titlesuffix: Azure portal
description: "Intune で Azure AD シングル サインオンを使用するように Skycure を構成する"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0466ac4-4942-4c4c-b8af-996b597c701d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 93e7f1a21c9badb3cc3ccdf02432267b271e6e94
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="configure-skycure-to-use-azure-active-directory-single-sign-on-sso"></a>Azure Active Directory シングル サインオン (SSO) を使用するように Skycure を構成する

Azure AD SSO は、Intune と Skycure の統合時に利用されます。 主な利点:

-   **管理者**は同じ資格情報を利用できます。Microsoft ポータル (Intune、Azure) と Skycure 管理コンソールでログイン/ログアウトするたびに資格情報を入力する必要がありません。

-   **エンドユーザー**は同じ Azure AD 資格情報を利用できます。Skycure アプリでログイン/ログアウトするたびに資格情報を入力する必要がありません。

Skycure と Azure Active Directory シングル サインオン (SSO) を統合する手順を以下に示します。

## <a name="to-retrieve-the-azure-active-directory-tenant-id"></a>Azure Active Directory テナント ID を取得するには

Azure AD テナント ID を取得する必要があります。

1.  [Azure Portal](https://portal.azure.com/) に移動し、資格情報でサインインします。

2.  **ダッシュボード**が表示されたら、**[Azure Active Directory]** を選択します。

    ![Azure AD ダッシュボード](./media/skycure-sso-1.png)

3.  **[Azure Active Directory]** ブレードが開いたら、**[プロパティ]** を選択します。

    ![Azure AD の [プロパティ] ブレード](./media/skycure-sso-2.png)

4.  Azure Active Directory の **[プロパティ]** ブレードの **[テナント ディレクトリ ID]** で **[コピー]** アイコンをクリックします。

5. 後で使用できるように、コピーしたディレクトリ ID 値をテキスト ファイルに貼り付けます。 ディレクトリ ID 値は、後で、Skycure と Intune の統合プロセスで必要になります。

    ![Azure AD ダッシュボード](./media/skycure-sso-3.png)

## <a name="allow-skycure-to-communicate-with-azure-active-directory"></a>Azure Active Directory との通信を Skycure に許可する

1.  ブラウザーに下の URL を入力します。 **DIRECTORY_ID** の代わりに、前にテキスト ファイルにコピーした Azure Active Directory テナント ID を入力します。

        https://login.microsoftonline.com/<DIRECTORY_ID>/oauth2/authorize?client_id=28fd67fdb1794629a8b0dad420b697c7&prompt=admin_consent&redirect_uri=https%3A%2F%2Fmc.skycure.com%2Fapi%2Fexternal%2Fmdm%2Faad_app_consent%2Fmanagement_callback&response_type=code

2.  Azure Active Directory の資格情報を使用してログインする必要があります。 **[同意する]** をクリックして続行します。

![Azure AD ログイン ページ](./media/skycure-sso-4.png)

## <a name="create-an-azure-ad-security-group-for-skycure-optional"></a>Skycure の Azure AD セキュリティ グループを作成する (省略可能)

Skycure を実行しているユーザーを含む専用ユーザー グループを作成すると便利です (Skycure ユーザーなど)。 レポートで Skycure アクティビティを分析するときに便利です。

-   詳細については、「[Azure Active Directory でグループを作成し、メンバーを追加する](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal)」を参照してください。

> [!NOTE] 
> また、既存の Azure AD セキュリティ グループを使用できます。

## <a name="configure-the-azure-ad-account-to-integrate-intune-with-skycure"></a>Intune と Skycure を統合するように Azure AD アカウントを構成する

1.  [Skycure 管理コンソール](https://aad.skycure.com/)から、前にテキスト ファイルに保存した Azure Active Directory テナント ID を入力します。

![Skycure 管理コンソールの Azure AD テナント ID フィールド](./media/skycure-sso-5.png)

> [!IMPORTANT] 
> Skycure は Azure AD に問い合わせ、Azure AD テナント ID が存在するかどうかを確認します。存在することがわかると、管理者は次の手順である基本セットアップに進むことができます。

## <a name="next-steps"></a>次のステップ

[Skycure iOS アプリ構成ポリシーをダウンロードする](skycure-ios-app-configuration-policy-download.md)
