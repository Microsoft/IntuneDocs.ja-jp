---
title: Intune との Pradeo 統合を設定する
titleSuffix: Intune on Azure
description: Intune と Pradeo コネクタを統合する
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 82872ba6-80f8-4cc9-adf4-0ccd8ff26dd2
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: cbe996565291d2aaf280de0612480b879b3e5d29
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61511429"
---
# <a name="integrate-pradeo-with-intune"></a>Pradeo と Intune を統合する

Pradeo Mobile Threat Defense ソリューションを Intune と統合するには、次の手順を実行します。

## <a name="before-you-begin"></a>始める前に

> [!NOTE]
> 次の手順は、[Pradeo のセキュリティ コンソール](https://www.apps-security.com)で完了する必要があります。

Pradeo と Intune の統合を始める前に、次のものがあることを確認します。

-   Microsoft Intune サブスクリプション

-   次のアクセス許可を付与する Azure Active Directory 管理者資格情報:

    -   サインインしてユーザー プロファイルを読み取る

    -   サインインしたユーザーとしてディレクトリにアクセスする

    -   ディレクトリ データの読み込み

    -   Intune にデバイス情報を送信する

-   Pradeo のセキュリティ コンソールにアクセスするための管理者資格情報。

### <a name="pradeo-app-authorization"></a>Pradeo アプリの承認

Pradeo アプリ承認プロセスは以下で構成されます。

-   Pradeo サービスがデバイスの正常性状態に関する情報を Intune に通知できるようにします。

-   Pradeo は、Azure AD 登録グループ メンバーシップと同期してデバイスのデータベースを設定します。

-   Pradeo 管理者コンソールが Azure AD シングル サインオン (SSO) を使用できるようにします。

-   Pradeo アプリが Azure AD SSO を使用してサインインできるようにします。

## <a name="to-set-up-pradeo-integration"></a>Pradeo の統合を設定するには

1.  [Pradeo のセキュリティ コンソール](https://www.apps-security.com)に移動し、資格情報を使用してサインインします。

2.  メニューから **[Administration - Enterprise Mobility Management]** (管理 - Enterprise Mobility Management) を選択します。

3.  **Intune のロゴ**を選択します。

4.  **[EMM (Enterprise Mobility Management - Intune)]** (EMM (Enterprise Mobility Management - Intune)) ウィンドウの **[手順 1]** で、**[Pradeo Connector]** (Pradeo コネクタ) ボタンを選択します。 

    ![Pradeo EMM Intune ウィンドウのスクリーンショット](./media/pradeo_setup.png)

5. Microsoft Intune の接続ウィンドウに Intune の資格情報を入力します。

5.  Pradeo の Web ページが再度開きます。 **[手順 2]** の **[Pradeo Device Health]** (Pradeo デバイスの正常性) ボタンを選択します。

7. Pradeo-Intune Connector] \(Pradeo-Intune コネクタ) ウィンドウで **[Accept]** \(同意する) を選択します。 

8. Pradeo device API connector] \(Pradeo デバイス API コネクタ) ウィンドウで **[Accept]** \(同意する) を選択します。

9. Pradeo の Web ページが再度開きます。 **[手順 3]** の **[Connect to Microsoft]** (Microsoft に接続) ボタンを選択します。 

10. Microsoft Intune の認証ウィンドウで、Intune の資格情報を入力します。

11. **[Successful Integration]** (統合に成功しました) というメッセージが表示されると統合は完了です。

## <a name="next-steps"></a>次の手順

-   [Pradeo アプリを設定する](mtd-apps-ios-app-configuration-policy-add-assign.md)
