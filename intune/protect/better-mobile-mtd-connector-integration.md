---
title: Better Mobile と Intune の統合を設定する
titleSuffix: Intune on Azure
description: Better Mobile コネクタと Intune の統合
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0528ec962165f358b35afce98f58c8b9b4efe93c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72810331"
---
# <a name="integrate-better-mobile-with-intune"></a>Better Mobile と Intune を統合する

Better Mobile Threat Defense ソリューションを Intune と統合するには、次の手順を行います。

## <a name="before-you-begin"></a>始める前に

[Better Mobile の管理コンソール](https://aad.bmobi.net)内で、以下の手順を実行します。これにより、Intune に登録されているデバイス (デバイス コンプライアンスを使用) および登録されていないデバイス (アプリ保護ポリシーを使用) の両方で Better Mobile のサービスに接続できるようになります。

Better Mobile と Intune の統合を始める前に、次のものがあることを確認します。

- Microsoft Intune サブスクリプション

- 次のアクセス許可を付与する Azure Active Directory 管理者資格情報:

  - サインインしてユーザー プロファイルを読み取る

  - サインインしたユーザーとしてディレクトリにアクセスする

  - ディレクトリ データの読み込み

  - Intune にデバイス情報を送信する

- Better Mobile 管理コンソールにアクセスするための管理者資格情報。

### <a name="better-mobile-app-authorization"></a>Better Mobile アプリの承認

Better Mobile アプリの承認プロセスは以下で構成されます。

- Better Mobile サービスがデバイスの正常性状態に関する情報を Intune に通知できるようにします。

- Better Mobile は、Azure AD 登録グループ メンバーシップと同期してデバイスのデータベースを設定します。

- Better Mobile 管理コンソールが Azure AD シングル サインオン (SSO) を使用できるようにします。

- Better Mobile アプリが Azure AD SSO を使用してサインインできるようにします。

## <a name="to-set-up-better-mobile-integration"></a>Better Mobile の統合を設定するには

1. [Better Mobile の管理コンソール](https://aad.bmobi.net)に移動し、資格情報を使用してサインインします。
2. **[統合]**  >  **[EMM/MDM]**  >  **[アカウントの追加]** の順に選択します。

     ![Better Mobile の管理コンソールの画像](./media/better-mobile-mtd-connector-integration/better_mobile_console.png)
 
3. **[Intune]** を選択します。
4. **[アカウント名]** の横に、記述子を入力します。 
5. **Microsoft のサインイン**のウィンドウに Intune の資格情報を入力します。
6. **[要求されているアクセス許可]** ウィンドウで、 **[Accept]\(同意\)** を選択します。
7. Better Mobile を同期するデバイスが属する Azure AD セキュリティ グループを検索し、一覧から選択します。 **[続行]** を選択します。
8. **[完了]** を選びます。
9. **[アカウントの追加]** ページが再表示されます。 ページを閉じます。 

## <a name="next-steps"></a>次の手順

- [登録されたデバイスに Better Mobile アプリを設定する](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [登録されていないデバイスに Better Mobile アプリを設定する](~/protect/mtd-add-apps-unenrolled-devices.md)
