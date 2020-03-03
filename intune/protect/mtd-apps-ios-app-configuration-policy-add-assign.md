---
title: MTD アプリを追加し、Microsoft Intune に割り当てる
titleSuffix: Microsoft Intune
description: Intune を使用し、Mobile Threat Defense (MTD) アプリ、Microsoft Authenticator アプリ、iOS 構成ポリシーを Azure Portal で追加します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: efdb1912fdbb2f28c6859fae4407116173daa99d
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576293"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Intune で Mobile Threat Defense (MTD) アプリを追加して割り当てる

脅威がモバイル デバイスで特定されたときにエンドユーザーが通知を受け取れるように、また、脅威を除去するための手引きが受けられるように、Intune を利用して Mobile Threat Defense (MTD) アプリを追加して展開することができます。

> [!NOTE]
> この記事は、すべての Mobile Threat Defense パートナーに適用されます。

## <a name="before-you-begin"></a>始める前に

Intune で次の手順を実行します。 次のプロセスをよく理解している必要があります。

- [Intune にアプリを追加する](../apps/apps-add.md)。
- [iOS アプリ構成ポリシーを Intune に追加する](../apps/app-configuration-policies-use-ios.md)。
- [Intune でアプリを割り当てる](../apps/apps-deploy.md)。

> [!TIP]
> Intune ポータル サイトは Android デバイスでブローカーとして機能するため、ユーザーに Azure AD によってチェックされた ID が与えられます。

## <a name="configure-microsoft-authenticator-for-ios"></a>iOS 向け Microsoft Authenticator を構成する

iOS デバイスでは、Azure AD によってチェックされた ID がユーザーに与えられるように、[Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) が必要です。 さらに、Intune で使用する MTD の iOS アプリを設定する iOS アプリ構成ポリシーも必要です。

iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-ios.md)をご覧ください。 **[アプリ情報]** を構成するときに、こちらの [Microsoft Authenticator のアプリ ストア URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) を使用してください。

## <a name="configure-mtd-applications"></a>MTD アプリケーションの構成

MTD プロバイダーに対応するセクションを選択します。

- [Lookout for Work](#configure-lookout-for-work-apps)
- [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
- [Check Point SandBlast Mobile](#configure-check-point-sandblast-mobile-apps)
- [Zimperium](#configure-zimperium-apps)
- [Pradeo](#configure-pradeo-apps)
- [Better Mobile](#configure-better-mobile-apps)
- [Sophos Mobile](#configure-sophos-apps)
- [Wandera](#configure-wandera-apps)

### <a name="configure-lookout-for-work-apps"></a>Lookout for Work アプリを構成する

- **Android**
  - Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-android.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [Lookout for work の Google アプリ ストア URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise) を使用してください。

- **Android**
  - iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-ios.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [Lookout for Work の iOS アプリ ストア URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) を使用してください。

- **Apple ストア以外の Lookout for Work アプリ**
  - Lookout for Work iOS アプリに再署名する必要があります。 Lookout により、その Lookout for Work iOS アプリが the iOS App Store の外部で配布されます。 アプリを配布する前に、iOS Enterprise Developer Certificate でアプリに再署名する必要があります。  
  - Lookout for Work iOS アプリに再署名する詳細な手順については、Lookout の Web サイトの「[Lookout for Work iOS app re-signing process](https://personal.support.lookout.com/hc/articles/114094038714)」(Lookout for Work iOS アプリの再署名プロセス) を参照してください。

  - **Lookout for Work iOS アプリ ユーザーに対して Azure AD Authentication を有効にします。**

    1. [Azure Portal](https://portal.azure.com) に移動し、資格情報でサインインして、アプリケーションのページに移動します。

    2. **Lookout for Work iOS アプリ**を**ネイティブ クライアント アプリケーション**として追加します。

    3. **com.lookout.enterprise.yourcompanyname** を、IPA に署名したときに選択したカスタマー バンドル ID に置換します。

    4. リダイレクト URI を追加します。 **&lt;companyportal://code/>** の後に、元のリダイレクト URI を URL エンコードしたバージョンを続けます。

    5. アプリに**デリゲートされたアクセス許可**を追加します。

    > [!NOTE]
    > 詳細については、「[ネイティブ クライアント アプリケーションの構成](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application)」を参照してください。

  - **Lookout for Work の ipa ファイルを追加します。**

    - [Intune での iOS LOB アプリの追加](../apps/lob-apps-ios.md)に関する記事の説明に従って、再署名した .ipa ファイルをアップロードします。 また、最小 OS バージョンを iOS 8.0 以降に設定する必要があります。

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>Symantec Endpoint Protection Mobile アプリを構成する

- **Android**
  - Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-android.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [SEP Mobile の アプリ ストア URL](https://play.google.com/store/apps/details?id=com.skycure.skycure) を使用してください。  **[Minimum operating system]\(最小オペレーティング システム\)** では、**Android 4.0 (Ice Cream Sandwich)** を選びます。

- **Android**
  - iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-ios.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [SEP Mobile の アプリ ストア URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) を使用してください。

### <a name="configure-check-point-sandblast-mobile-apps"></a>Check Point SandBlast Mobile アプリを構成する

- **Android**  
  - Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-android.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [Check Point SandBlast Mobile の アプリ ストア URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) を使用してください。

- **Android**
  - iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-ios.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [Check Point SandBlast Mobile の アプリ ストア URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) を使用してください。  

### <a name="configure-zimperium-apps"></a>Zimperium アプリを構成する

- **Android**
  - Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-android.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [Zimperium の アプリ ストア URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) を使用してください。

- **Android**
  - iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-ios.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [Zimperium の アプリ ストア URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) を使用してください。  
 
### <a name="configure-pradeo-apps"></a>Pradeo アプリを構成する

- **Android**
  - Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-android.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [Pradeo の アプリ ストア URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) を使用してください。

- **Android**
  - iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-ios.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [Pradeo の アプリ ストア URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) を使用してください。

### <a name="configure-better-mobile-apps"></a>Better Mobile アプリを構成する

- **Android**
  - Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-android.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [Active Shield の アプリ ストア URL](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) を使用してください。

- **Android**
  - iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-ios.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [ActiveShield の アプリ ストア URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) を使用してください。

### <a name="configure-sophos-apps"></a>Sophos アプリを構成する

- **Android**
  - Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-android.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [Sophos の アプリ ストア URL](https://play.google.com/store/apps/details?id=com.sophos.smsec) を使用してください。

- **Android**
  - iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-ios.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [ActiveShield の アプリ ストア URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) を使用してください。

### <a name="configure-wandera-apps"></a>Wandera アプリを構成する

- **Android**
  - Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-android.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [Wandera Mobile の アプリ ストア URL](https://play.google.com/store/apps/details?id=com.wandera.android) を使用してください。 **[Minimum operating system]\(最小オペレーティング システム\)** では、 **[Android 5.0]** を選びます。

- **Android**
  - iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](../apps/store-apps-ios.md)をご覧ください。 **[アプリ ストアの URL]** には、こちらの [Wandera Mobile の アプリ ストア URL](https://itunes.apple.com/app/wandera/id605469330) を使用してください。

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>MTD アプリに iOS アプリ構成ポリシーを構成する

### <a name="lookout-for-work-app-configuration-policy"></a>Lookout for Work アプリ構成ポリシー

[iOS アプリ構成ポリシーの使用](../apps/app-configuration-policies-use-ios.md)に関する記事の説明に従って、iOS アプリ構成ポリシーを作成します。

### <a name="sep-mobile-app-configuration-policy"></a>SEP モバイル アプリ構成ポリシー

[Symantec Endpoint Protection Management コンソール](https://aad.skycure.com)で以前に構成したものと同じ Azure AD アカウントを使います。これは、Intune へのサインインに使用するアカウントと同じものである必要があります。

- iOS アプリ構成ポリシー ファイルを**ダウンロード**します。
  - [Symantec Endpoint Protection Management コンソール](https://aad.skycure.com)に移動し、管理者資格情報でサインインします。

  - **[Settings]\(設定\)** に移動し、 **[Integrations]\(統合\)** で **[Intune]** を選びます。 **[EMM Integration Selection]\(EMM 統合の選択\)** を選びます。 **[Microsoft]** を選び、選択内容を保存します。

  - **[Integration setup files]\(統合セットアップ ファイル\)** リンクをクリックし、生成された \*.zip ファイルを保存します。 この .zip ファイルには * **.plist** ファイルが含まれます。このファイルを利用し、Intune で iOS アプリ構成ポリシーが作成されます。

  - [iOS 用 Microsoft Intune アプリ構成ポリシーを使用する](../apps/app-configuration-policies-use-ios.md)手順に従って、SEP Mobile iOS アプリ構成ポリシーを追加します。

    - **[構成設定の形式]** に対して、 **[XML データを入力する]** を選択し、* **.plist** ファイルから内容をコピーして、その内容を構成ポリシーの本文に貼り付けます。

> [!NOTE]
> ファイルを取得できない場合は、[Symantec Endpoint Protection Mobile エンタープライズ サポート](https://support.symantec.com/en_US/contact-support.html)にお問い合わせください。

### <a name="check-point-sandblast-mobile-app-configuration-policy"></a>Check Point SandBlast Mobile アプリ構成ポリシー

[iOS 用 Microsoft Intune アプリ構成ポリシーを使用する](../apps/app-configuration-policies-use-ios.md)手順に従って、Check Point SandBlast Mobile iOS アプリ構成ポリシーを追加します。

- **[構成設定の形式]** に対して、 **[XML データを入力する]** を選択し、次の内容をコピーして、構成ポリシーの本文に貼り付けます。

  `<dict><key>MDM</key><string>INTUNE</string></dict>`


### <a name="zimperium-app-configuration-policy"></a>Zimperium アプリ構成ポリシー

[iOS 用 Microsoft Intune アプリ構成ポリシーを使用する](../apps/app-configuration-policies-use-ios.md)手順に従って、Zimperium iOS アプリ構成ポリシーを追加します。

- **[構成設定の形式]** に対して、 **[XML データを入力する]** を選択し、次の内容をコピーして、構成ポリシーの本文に貼り付けます。

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

### <a name="pradeo-app-configuration-policy"></a>Pradeo アプリ構成ポリシー

Pradeo では、iOS/iPadOS でのアプリケーション構成ポリシーをサポートしていません。  アプリを構成するには、代わりに、Pradeo を使用して目的の設定であらかじめ構成されたカスタム IPA または APK ファイルを実装します。

### <a name="better-mobile-app-configuration-policy"></a>Better Mobile モバイル アプリ構成ポリシー

[iOS 用 Microsoft Intune アプリ構成ポリシーを使用する](../apps/app-configuration-policies-use-ios.md)手順に従って、Better Mobile iOS アプリ構成ポリシーを追加します。

- **[構成設定の形式]** に対して、 **[XML データを入力する]** を選択し、次の内容をコピーして、構成ポリシーの本文に貼り付けます。 `https://client.bmobi.net` の URL を適切なコンソールの URL に置き換えます。

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

### <a name="sophos-mobile-app-configuration-policy"></a>Sophos Mobile アプリ構成ポリシー

[iOS アプリ構成ポリシーの使用](../apps/app-configuration-policies-use-ios.md)に関する記事の説明に従って、iOS アプリ構成ポリシーを作成します。

### <a name="wandera-app-configuration-policy"></a>Wandera アプリ構成ポリシー

[iOS 用 Microsoft Intune アプリ構成ポリシーを使用する](../apps/app-configuration-policies-use-ios.md)手順に従って、Wandera iOS アプリ構成ポリシーを追加します。

- **[構成設定の形式]** に対して、 **[XML データを入力する]** を選択します。

RADAR Wandera ポータルにサインインして、 **[設定]**  >  **[EMM Integration]\(EMM 統合\)**  >  **[App Push]\(アプリのプッシュ\)** の順に移動します。 **[Intune]** を選択して使用して以下の内容をコピーし、構成ポリシーの本文に貼り付けます。  

  ```
  <dict><key>secretKey</key>
  <string>SeeRADAR</string>
  <key>apiKey</key>
  <string> SeeRADAR </string>
  <key>customerId</key>
  <string> SeeRADAR </string>
  <key>email</key>
  <string>{{mail}}</string>
  <key>firstName</key>
  <string>{{username}}</string>
  <key>lastName</key>
  <string></string>
  <key>activationType</key>
  <string>PROVISION_THEN_AWP</string></dict>
  ```

## <a name="assign-apps-to-groups"></a>アプリをグループに割り当てる

この手順は、すべての MTD パートナーに該当します。 [Intune でアプリをグループに割り当てる](../apps/apps-deploy.md)手順を参照してください。

## <a name="next-steps"></a>次のステップ

- [MTD のデバイス コンプライアンス ポリシーを構成する](mtd-device-compliance-policy-create.md)
