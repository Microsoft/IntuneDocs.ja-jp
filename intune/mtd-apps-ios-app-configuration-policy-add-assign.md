---
title: MTD アプリを追加し、Microsoft Intune に割り当てる | Microsoft Intune
description: Intune を使用し、Mobile Threat Defense (MTD) アプリ、Microsoft Authenticator アプリ、iOS 構成ポリシーを Azure Portal で追加します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 44faac275eb19c9c73c935a6c7d6c950b9ac653e
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55847133"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Intune で Mobile Threat Defense (MTD) アプリを追加して割り当てる

> [!NOTE] 
> このトピックは、すべての Mobile Threat Defense パートナーに適用されます。

脅威がモバイル デバイスで特定されたときにエンドユーザーが通知を受け取れるように、また、脅威を除去するための手引きが受けられるように、Intune を利用して Mobile Threat Defense (MTD) アプリを追加して展開することができます。


## <a name="before-you-begin"></a>始める前に

[Azure Portal](https://portal.azure.com/) で以下の手順を完了しておく必要があります。 次のプロセスをよく理解している必要があります。

  -   [Intune にアプリを追加する](apps-add.md)。
  -   [iOS アプリ構成ポリシーを Intune に追加する](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。
  -   [Intune でアプリを割り当てる](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune)。

> [!TIP]
> Intune ポータル サイトは Android デバイスでブローカーとして機能するため、ユーザーに Azure AD によってチェックされた ID が与えられます。

## <a name="configure-microsoft-authenticator-for-ios"></a>iOS 向け Microsoft Authenticator を構成する
iOS デバイスでは、Azure AD によってチェックされた ID がユーザーに与えられるように、[Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) が必要です。 さらに、Intune で使用する MTD の iOS アプリを設定する iOS アプリ構成ポリシーも必要です。

iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-ios.md)をご覧ください。 「**アプリ情報を構成する**」セクションの**手順 12** では、この [Microsoft Authenticator アプリ ストア URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) を使います。

## <a name="configure-mtd-applications"></a>MTD アプリケーションの構成

MTD プロバイダーに対応するセクションを選択します。

  - [Lookout for Work](#configure-lookout-for-work-apps)
  - [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
  - [Check Point SandBlast Mobile](#configure-check-point-sandblast-mobile-apps)
  - [Zimperium](#configure-zimperium-apps)
  - [Pradeo](#configure-pradeo-apps)
  - [Better Mobile](#configure-better-mobile-apps)

### <a name="configure-lookout-for-work-apps"></a>Lookout for Work アプリを構成する

- **Android**
  - Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-android.md)をご覧ください。 **手順 7** には、この [Lookout for work の Google アプリ ストア URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise) を使用してください。

- **Android**

  - iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-ios.md)をご覧ください。 「**アプリ情報を構成する**」セクションの**手順 12** では、この [Lookout for Work iOS アプリ ストア URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) を使います。

-   **Apple ストア以外の Lookout for Work アプリ**
    - Lookout for Work iOS アプリに再署名する必要があります。 Lookout は、iOS App Store 以外の場所で Lookout for Work iOS アプリを配布しています。 アプリを配布する前に、iOS Enterprise Developer Certificate でアプリに再署名する必要があります。
    - Lookout for Work iOS アプリに再署名する詳細な手順については、Lookout の Web サイトの「[Lookout for Work iOS app re-signing process](https://personal.support.lookout.com/hc/articles/114094038714)」(Lookout for Work iOS アプリの再署名プロセス) を参照してください。

    - **Lookout for Work iOS アプリ ユーザーに対して Azure AD Authentication を有効にします。**

        1. [Azure Portal](https://portal.azure.com) に移動し、資格情報でサインインして、アプリケーションのページに移動します。

        2. **ネイティブ クライアント アプリケーション**として **Lookout for Work iOS アプリ**を追加します。

        3. **com.lookout.enterprise.yourcompanyname** は、IPA に署名したときに選択したカスタマー バンドル ID で置き換えます。

        4.  リダイレクト URI を追加します。**&lt;companyportal://code/>** の後に、元のリダイレクト URI を URL エンコードしたバージョンを続けます。

        5.  アプリに**デリゲートされたアクセス許可**を追加します。

        > [!NOTE] 
        > 詳細については、「[ネイティブ クライアント アプリケーションの構成](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application)」を参照してください。

     - **Lookout for Work の ipa ファイルを追加します。**

        - [Intune での iOS LOB アプリの追加](lob-apps-ios.md)に関するトピックの説明に従って、再署名した .ipa ファイルをアップロードします。 また、最小 OS バージョンを iOS 8.0 以降に設定する必要があります。

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>Symantec Endpoint Protection Mobile アプリを構成する

 - **Android**

    - Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-android.md)をご覧ください。 **手順 7** では、この [SEP Mobile アプリ ストア URL](https://play.google.com/store/apps/details?id=com.skycure.skycure) を使います。  **[Minimum operating system]\(最小オペレーティング システム\)** では、**Android 4.0 (Ice Cream Sandwich)** を選びます。

 - **Android**

    - iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-ios.md)をご覧ください。 「**アプリ情報を構成する**」セクションの**手順 12** では、この [SEP Mobile アプリ ストア URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) を使います。

### <a name="configure-check-point-sandblast-mobile-apps"></a>Check Point SandBlast Mobile アプリを構成する

 - **Android**

    - Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-android.md)をご覧ください。 **手順 7** には、この [Check Point SandBlast Mobile のアプリ ストア URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) を使用してください。

 - **Android**

    - [Check Point SandBlast Mobile](https://www.checkpoint.com/products/sandblast-mobile/) に連絡して iOS アプリを取得してください。 [iOS ストア アプリを Microsoft Intune に追加する](store-apps-ios.md)手順を確認し、「**アプリ情報を構成する**」セクションの**手順 12** では、Apple ストアの URL を使います。

### <a name="configure-zimperium-apps"></a>Zimperium アプリを構成する

 - **Android**

    - Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-android.md)をご覧ください。 **手順 7** には、この [Zimperium アプリ ストア URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) を使用してください。

 - **Android**

    - iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-ios.md)をご覧ください。 「**アプリ情報を構成する**」セクションの**手順 12** では、この [Zimperium アプリ ストア URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) を使います。

### <a name="configure-pradeo-apps"></a>Pradeo アプリを構成する

 - **Android**

    - Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-android.md)をご覧ください。 **手順 7** の [Pradeo アプリ ストア URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) を使用してください。

 - **Android**

    - iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-ios.md)をご覧ください。 「**アプリ情報を構成する**」セクションの**手順 12** の [Pradeo アプリ ストア URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) を使用してください。

### <a name="configure-better-mobile-apps"></a>Better Mobile アプリを構成する

 - **Android**

    - Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-android.md)をご覧ください。 **手順 7** では、この [Active Shield アプリ ストアの URL](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) を使用してください。

 - **Android**

    - iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-ios.md)をご覧ください。 **手順 12** の**アプリ情報を構成する**セクションでは、この [ActiveShield アプリ ストアの URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) を使用してください。

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>MTD アプリに iOS アプリ構成ポリシーを構成する

### <a name="lookout-for-work-app-configuration-policy"></a>Lookout for Work アプリ構成ポリシー

- [iOS アプリ構成ポリシーの使用](app-configuration-policies-use-ios.md)に関する記事の説明に従って、iOS アプリ構成ポリシーを作成します。

### <a name="sep-mobile-app-configuration-policy"></a>SEP モバイル アプリ構成ポリシー

-   [Symantec Endpoint Protection Management コンソール](https://aad.skycure.com)で以前に構成したものと同じ Azure AD アカウントを使います。これは、Intune クラシック ポータルにサインインするためのものと同じアカウントにする必要があります。

-   iOS アプリ構成ポリシーのファイルは次のようにして**ダウンロードする**必要があります。 
    -   [Symantec Endpoint Protection Management コンソール](https://aad.skycure.com)に移動し、管理者資格情報でサインインします。

    -   **[Settings]\(設定\)** に移動し、**[Integrations]\(統合\)** で **[Intune]** を選びます。 **[EMM Integration Selection]\(EMM 統合の選択\)** を選びます。 **[Microsoft]** を選び、選択内容を保存します。

    -   **[Integration setup files]\(統合セットアップ ファイル\)** リンクをクリックし、生成された \*.zip ファイルを保存します。 この .zip ファイルには ***.plist** ファイルが含まれます。このファイルを利用し、Intune で iOS アプリ構成ポリシーが作成されます。

    -   [iOS 用 Microsoft Intune アプリ構成ポリシーを使用する](app-configuration-policies-use-ios.md)手順に従って、SEP Mobile iOS アプリ構成ポリシーを追加します。

    - **手順 8** で、**[XML データを入力する]** オプションを使用して内容を ***.plist** ファイルからコピーして、構成ポリシーの本文に貼り付けます。

> [!NOTE]
> ファイルを取得できない場合は、[Symantec Endpoint Protection Mobile エンタープライズ サポート](https://support.symantec.com/en_US/contact-support.html)にお問い合わせください。

### <a name="check-point-sandblast-mobile-app-configuration-policy"></a>Check Point SandBlast Mobile アプリ構成ポリシー

- [iOS 用 Microsoft Intune アプリ構成ポリシーを使用する](app-configuration-policies-use-ios.md)手順に従って、Check Point SandBlast Mobile iOS アプリ構成ポリシーを追加します。
    - **手順 8** で、**[XML データを入力する]** オプションを使用して以下の内容をコピーし、構成ポリシーの本文に貼り付けます。

```
<dict><key>MDM</key><string>INTUNE</string></dict>
```

### <a name="zimperium-app-configuration-policy"></a>Zimperium アプリ構成ポリシー

- [iOS 用 Microsoft Intune アプリ構成ポリシーを使用する](app-configuration-policies-use-ios.md)手順に従って、Zimperium iOS アプリ構成ポリシーを追加します。
    - **手順 8** で、**[XML データを入力する]** オプションを使用して以下の内容をコピーし、構成ポリシーの本文に貼り付けます。

```
<dict>
<key>provider</key><string>Intune</string>
<key>userprincipalname</key><string>{{userprincipalname}}</string>
<key>deviceid</key>
<string>{{deviceid}}</string>
<key>serialnumber</key>
<string>{{serialnumber}}</string>
<key>udidlast4digits</key>
<string>{{udidlast4digits}}</string>
</dict>
```

### <a name="better-mobile-app-configuration-policy"></a>Better Mobile モバイル アプリ構成ポリシー

- [iOS 用 Microsoft Intune アプリ構成ポリシーを使用する](app-configuration-policies-use-ios.md)手順に従って、Better Mobile iOS アプリ構成ポリシーを追加します。
    - **手順 8** で、**[XML データを入力する]** オプションを使用して以下の内容をコピーし、構成ポリシーの本文に貼り付けます。 `https://client.bmobi.net` の URL を適切なコンソールの URL に置き換えます。

```
<dict>
<key>better_server_url</key>
<string>https://client.bmobi.net</string>
<key>better_udid</key>
<string>{{aaddeviceid}}</string>
<key>better_user</key>
<string>{{userprincipalname}}</string>
</dict>
```

## <a name="assign-apps-to-groups"></a>アプリをグループに割り当てる

- この手順は、すべての MTD パートナーに該当します。 [Intune でアプリをグループに割り当てる](apps-deploy.md)手順を参照してください。

## <a name="next-steps"></a>次の手順

- [MTD のデバイス コンプライアンス ポリシーを構成する](mtd-device-compliance-policy-create.md)
