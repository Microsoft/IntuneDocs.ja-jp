---
title: "Lookout for Work アプリを展開する | Microsoft Intune"
description: "Android 用の Lookout for Work アプリを構成して展開します。"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c59707ba2967b069dc30aee71d2642e91d71b23b
ms.openlocfilehash: 720fe241e7f1205dbad4b64af5cf7f16a80db23e


---

# <a name="configure-and-deploy-lookout-for-work-apps"></a>Lookout for Work アプリを構成して展開する
この記事では、Android デバイスと iOS デバイス用に Lookout for Work アプリを構成し、展開する方法について説明します。

## <a name="android-google-play-store-app"></a>Android (Google Play ストア アプリ)

* **手順 1**:   [Microsoft Intune 管理者コンソール](https://manage.microsoft.com)で、**[アプリ]** に移動し、**[アプリの追加]** を選択します。   
* **手順 2**:   発行元の **[ソフトウェア セットアップ]** ページで、**[外部リンク]** を選択し、URL "https://play.google.com/store/apps/details?id=com.lookout.enterprise" を指定します。
>[!NOTE]
>Managed Browser を要求するボックスをオンにしないでください。

* **手順 3**:   **[ソフトウェアの説明]** ページで、次の情報を入力します。
  * **[発行元]:** Lookout Mobile Security
  * **[名前]:**   Lookout for Work
  * **[説明]:**  Lookout はモバイルの脅威に対する最適な保護を提供し、モバイル デバイスの安全を保ちます。 デバイスにインストールされた Lookout アプリは、デバイスを脅威から保護し、検出された脅威を管理者に通知します。
  * **[カテゴリ]:** コンピューターの管理
* **手順 4**: 正常に完了すると、**[Microsoft Intune にデータが正常にアップロードされました]** というメッセージが表示されます。

Intune コンソールで **[アプリ]** をクリックすると、Lookout for Work アプリが一覧に表示されます。![Intune 管理者コンソールのアプリ ページの一覧に表示された Lookout for Work アプリのスクリーンショット](../media/mtp/lookout-app-listed-intune-console.png)

* **手順 5**: アプリをユーザーに展開するには、Lookout for Work アプリを選択し、**[展開の管理]** を選択します。

  Lookout MTP コンソールの 「Enrollment Management」 (登録管理) オプションで追加したものと同じユーザーを選択する必要があります。  Lookout MTP へのユーザー グループの追加の詳細については、「[Lookout MTP でサブスクリプションを構成する](set-up-your-subscription-with-lookout-mtp.md#configure-your-subscription-with-lookout-device-threat-protection)」セクションの手順 3 をご覧ください。

  >[!IMPORTANT]
  > Intune アプリ展開ウィザードは Azure AD のユーザー グループを認識せず、代わりに Intune のユーザー グループを使用します。 したがって、Lookout MTP コンソールで登録されている Azure AD のユーザー グループに基づいて Intune のユーザー グループを作成する必要があります ([こちら](plan-your-user-and-device-groups.md)のトピックを参照)。

* **手順 6**: **[必須のインストール]** オプションを選択し、Lookout アプリがユーザーのデバイスに必ずインストールされるようにします。


## <a name="ios-enterprise-signed-version-of-lookout-app"></a>iOS (Enterprise 署名バージョンの Lookout アプリ)

* **手順 1:** **iOS 管理**がデバイスにセットアップされていることを確認します。 デバイスで iOS 管理をセットアップする手順については、「[iOS および Mac のデバイス管理をセットアップする](set-up-ios-and-mac-management-with-microsoft-intune.md)」を参照してください。

* **手順 2:** Lookout for Work iOS アプリに**再署名**します。 Lookout は、iOS App Store 以外の場所で Lookout for Work iOS アプリを配布しています。 **アプリを配布する前に**、iOS Enterprise Developer Certificate でアプリに再署名する必要があります。 Lookout for Work アプリに再署名する詳細な手順については、Lookout サイトの「[Lookout for Work iOS app re-signing process](https://personal.support.lookout.com/hc/en-us/articles/114094038714)」(Lookout for Work iOS アプリの再署名プロセス) を参照してください。


* **手順 3:** 次の手順を実行して、iOS ユーザーの Azure Active Directory 認証を有効にします。
  1.  [Azure Active Directory 管理ポータル](https://manage.windowsazure.com)にログインし、アプリケーション ページに移動します。
  2.  **ネイティブ クライアント アプリケーション**として **Lookout for Work iOS アプリ**を追加します。
  ![ネイティブ クライアント アプリ オプションが表示されたアプリの追加ダイアログのスクリーンショット](../media/mtp/aad-add-app.png)

  3. **com.lookout.enterprise.yourcompanyname** は、IPA に署名したときに選択したカスタマー バンドル ID で置き換えます。
  4.  リダイレクト URI を追加します。**&lt;companyportal://code/>** の後に、元のリダイレクト URI を URL エンコードしたバージョンを続けます。
  5.  アプリに**デリゲートされたアクセス許可**を追加します。

  詳細については、「[ネイティブ クライアント アプリケーションの構成](https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application)」を参照してください。


* **手順 4:** 「[Intune に登録されたデバイスのアプリを追加する](https://docs.microsoft.com/en-us/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)」トピックに従って、再署名した .ipa ファイルをアップロードします。 最小 OS バージョンを iOS 8.0 以降に設定します。

  ![アプリの一覧に Lookout for Work アプリが表示された Intune 管理コンソールのアプリ ページのスクリーンショット](../media/mtp/ios-app-uploaded-intune.png)

* **手順 5:** 「[Microsoft Intune でのモバイル アプリ構成ポリシーを使用した iOS アプリの構成](https://docs.microsoft.com/en-us/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)」の説明に従って、管理対象アプリの構成ポリシーを作成します。

  ![iOS 8.0 以降のアプリ構成ポリシーが強調表示された新しいポリシーの作成ウィザードのスクリーンショット](../media/mtp/ios-app-config.png)

* **手順 6:** **アプリをユーザーに展開する**には、Lookout for Work アプリを選択し、**[展開の管理]** を選択します。

  Lookout コンソールの 「Enrollment Management」 (登録管理) オプションで追加したのと同じユーザーを選択する必要があります。  Lookout MTP へのユーザー グループの追加の詳細については、「[Lookout デバイス脅威保護用にサブスクリプションを構成する](set-up-your-subscription-with-lookout-mtp.md#configure-your-subscription-with-lookout-device-threat-protection)」セクションの手順 3 をご覧ください。

>[!IMPORTANT]
> Intune アプリ展開ウィザードでは、Azure AD ユーザー グループは認識されず、代わりに Intune ユーザー グループが使用されます。このため、[こちら](plan-your-user-and-device-groups.md)のトピックの説明に従って Lookout コンソールで登録した Azure AD ユーザー グループに基づいて Intune ユーザー グループを作成する必要があります。

**[必須のインストール]** オプションを選択し、Lookout アプリがユーザーのデバイスに必ずインストールされるようにします。

## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>展開したアプリがデバイスで開かれている場合はどうなりますか




ユーザーがデバイスで Lookout for Work を開くと、アプリをアクティブ化し、「Sign in with Azure Active Directory」 (Azure Active Directory でサインインする) オプションを選択するように求められます。 エンド ユーザーの詳細な手順については、次のトピックをご覧ください。

* [Android デバイスで Lookout for Work のインストールを求められる](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Android デバイスで Lookout for Work が検出した脅威を解決する必要がある](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## <a name="next-steps"></a>次のステップ
* [コンプライアンス ポリシーでデバイスの脅威防御ルールを有効にする](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Dec16_HO2-->


