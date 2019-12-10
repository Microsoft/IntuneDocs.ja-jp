---
title: Intune を使用して Android デバイス用 Google Chrome を構成する
titleSuffix: Microsoft Intune
description: Android デバイス用 Google Chrome で Intune 構成ポリシーを使用します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: c344a518890a2309a7805d61a5675e2646029bbb
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564042"
---
# <a name="configure-google-chrome-for-android-devices-using-intune"></a>Intune を使用して Android デバイス用 Google Chrome を構成する 

Intune アプリ構成ポリシーを使用して、Android デバイス用 Google Chrome を構成できます。 アプリの設定を自動的に適用できます。 たとえば、ブロックまたは許可するブックマークと URL を具体的に設定できます。

## <a name="prerequisites"></a>必要条件

- ユーザーの Android Enterprise デバイスは、Intune に登録されている必要があります。 詳細については、「[Android Enterprise 仕事用プロファイル デバイスの登録を設定する](~/enrollment/android-work-profile-enroll.md)」を参照してください。
- Google Chrome は managed Google Play アプリとして追加されます。 managed Google Play の詳細については、「[managed Google Play アカウントに Intune アカウントを接続する](~/enrollment/connect-intune-android-enterprise.md)」を参照してください。

## <a name="add-the-google-chrome-app-to-intune"></a>Google Chrome アプリを Intune に追加する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** を選択し、**マネージド Google Play** アプリを追加します。
3. managed Google Play に移動し、**Google Chrome** を検索して承認します。

    ![Google Chrome を検索して承認する](~/apps/media/apps-configure-chrome-android/search.png)

4. 必要なアプリの種類として Google Chrome をユーザー グループに割り当てます。 デバイスが Intune に登録されると、Google Chrome が自動的に展開されます。

managed Google Play アプリを Intune に追加する方法の詳細については、「[マネージド Google Play ストア アプリ](~/apps/apps-add-android-for-work.md#managed-google-play-store-apps)」を参照してください。

## <a name="add-app-configuration-for-managed-ae-devices"></a>マネージド AE デバイスのアプリ構成を追加する

1. [[Intune]](https://go.microsoft.com/fwlink/?linkid=2090973) ウィンドウで、 **[アプリ構成ポリシー]**  >  **[追加]** を選択します。
2. ポリシー名を追加し、[デバイス登録の種類] で **[マネージド デバイス]** を選択し、[プラットフォーム] で **[Android]** を選択します。

    ![Google Chrome 構成ポリシーを追加する](~/apps/media/apps-configure-chrome-android/add-policy.png)

3. **[関連アプリ]** をクリックして **[Google Chrome]** を選択します。

    ![[関連アプリ] で [Google Chrome] を選択する](~/apps/media/apps-configure-chrome-android/associated-app.png)

4. **[構成設定]** をクリックし、 **[構成デザイナーを使用する]** を選択し、 **[追加]** をクリックして構成キーを選択します。

    ![[構成デザイナーを使用する] の追加](~/apps/media/apps-configure-chrome-android/configuration.png)

    共通設定の例を次に示します。
    - **URL の一覧へのアクセスをブロックする**: `["*"]`
    - **URL の一覧へのアクセスを許可する**: `["baidu.com", "youtube.com", "chromium.org", "chrome://*"]`
    - **マネージド ブックマーク**: `[{"toplevel_name": "My managed bookmarks folder"  },  {"url": "baidu.com",   "name": "Baidu"},  {"url": "youtube.com", "name": "Youtube"},  {"name": "Chrome links",  "children": [{"url": "chromium.org", "name": "Chromium"},    {"url": "dev.chromium.org", "name": "Chromium Developers"}]}]`
    - **シークレット モードの可用性**: `Incognito mode disabled`

    構成デザイナーを使用して構成設定が追加されると、表に一覧表示されます。 

    ![共通設定](~/apps/media/apps-configure-chrome-android/common-settings.png)

    上記の設定によりブックマークが作成され、`baidu.com`、`yahoo.com`、`chromium.org`、`chrome://` を除くすべての URL へのアクセスがブロックされます。

5. **[OK]** と **[追加]** をクリックして、構成ポリシーを Intune に追加します。
6. この構成ポリシーをユーザー グループに割り当てます。 詳細については、「[Microsoft Intune を使用してアプリをグループに割り当てる方法](~/apps/apps-deploy.md)」を参照してください。 

## <a name="verify-the-device-settings"></a>デバイスの設定を確認する

Android デバイスが Android Enterprise に登録されると、ポートフォリオ アイコン付きのマネージド Google Chrome アプリが自動的に展開されます。
 
   <img alt="Managed Google Chrome with the portfolio icon" src="~/apps/media/apps-configure-chrome-android/chrome-icon.png" width="350">

Google Chrome を起動すると、設定が適用されていることがわかります。

   ブックマーク:<br>
   <img alt="Bookmarks" src="~/apps/media/apps-configure-chrome-android/bookmarks.png" width="350">

   ブロックされた URL:<br>
   <img alt="Blocked URL" src="~/apps/media/apps-configure-chrome-android/blocked-url.png" width="350">

   許可する URL:<br>
   <img alt="Allow URL" src="~/apps/media/apps-configure-chrome-android/allowed-url.png" width="350">

   シークレット タブ:<br>
   <img alt="Incognito tab" src="~/apps/media/apps-configure-chrome-android/incognito-tab.png" width="350">

## <a name="troubleshooting"></a>トラブルシューティング

1. Intune ポータルを確認してポリシーの展開状態を監視します。

    ![ポリシーの展開状態を監視する](~/apps/media/apps-configure-chrome-android/monitor-status.png)

2. Google Chrome を起動し、**chrome://policy** にアクセスします。 設定が正常に適用されたかどうかを確認できます。

    ![設定が正常に適用されたことを確認する](~/apps/media/apps-configure-chrome-android/confirm.png)

## <a name="additional-information"></a>追加情報

- [マネージド Android Enterprise デバイス用にアプリ構成ポリシーを追加する](~/app-configuration-policies-use-android.md)
- [Chrome Enterprise のポリシー リスト](https://cloud.google.com/docs/chrome-enterprise/policies/)

## <a name="next-steps"></a>次の手順

- Android Enterprise フル マネージド デバイスの詳細については、「[Android Enterprise フル マネージド デバイスの Intune 登録を設定する](~/enrollment/android-fully-managed-enroll.md)」を参照してください。
