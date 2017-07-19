---
title: "MTD アプリを追加して Intune に割り当てる"
titleSuffix: Intune on Azure
description: "MTD アプリ、Microsoft Authenticator アプリ、iOS 構成ポリシーを Azure での Intune に追加する"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7b3fb86648a86b161eadfc071bdacbfd4ea0222f
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Intune で Mobile Threat Defense (MTD) アプリを追加して割り当てる

脅威がモバイル デバイスで特定されたときにエンドユーザーが通知を受け取れるように、また、脅威を除去するための手引きが受けられるように、Intune を利用して MTD アプリを追加して展開することができます。

iOS デバイスでは、Azure AD によってチェックされた ID がユーザーに与えられるように、[Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) が必要です。 さらに、Intune で使用するには MTD の iOS アプリが通知される iOS アプリ構成ポリシーも必要です。

> [!TIP]
> Intune ポータル サイトは Android デバイスでブローカーとして機能するため、ユーザーに Azure AD によってチェックされた ID が与えられます。

## <a name="before-you-begin"></a>始める前に

-   [Azure Portal](https://portal.azure.com/) で以下の手順を完了しておく必要があります。

-   次のプロセスをよく理解している必要があります。

    -   [Intune にアプリを追加する](apps-add.md)。

    -   [iOS アプリ構成ポリシーを Intune に追加する](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

    -   [Intune でアプリを割り当てる](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune)。

    -   [iOS アプリ構成ポリシーを追加する](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

## <a name="to-add-apps"></a>アプリを追加するには

### <a name="skycure-app-for-android"></a>Android 向け Skycure アプリ

- Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-android.md)をご覧ください。 **手順 7**には、この [Skycure アプリ ストア URL](https://play.google.com/store/apps/details?id=com.skycure.skycure) を使用してください。

### <a name="skycure-app-for-ios"></a>iOS 向け Skycure アプリ

- iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-ios.md)をご覧ください。 「**アプリ情報を構成する**」セクションの**手順 5** には、この [Skycure アプリ ストア URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) を使用してください。

### <a name="microsoft-authenticator-app-for-ios"></a>iOS 向け Microsoft Authenticator アプリ

- iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-ios.md)をご覧ください。 「**アプリ情報を構成する**」セクションの**手順 5** には、この [Microsoft Authenticator アプリ ストア URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) を使用してください。

### <a name="lookout-for-work-android-app"></a>Lookout for Work Android アプリ

- Android ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-android.md)をご覧ください。 **手順 7** には、この [Lookout for work の Google アプリ ストア URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise) を使用してください。

### <a name="lookout-for-work-ios-app"></a>Lookout for Work iOS アプリ

- iOS ストア アプリを Microsoft Intune に追加する方法については、[こちら](store-apps-ios.md)をご覧ください。 「**アプリ情報を構成する**」セクションの**手順 5** には、この [Lookout for Work iOS アプリ ストア URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) を使用してください。

### <a name="lookout-for-work-app-outside-the-apple-store"></a>Apple ストア以外の Lookout for Work アプリ

Lookout for Work iOS アプリに再署名する必要があります。 Lookout は、iOS App Store 以外の場所で Lookout for Work iOS アプリを配布しています。 アプリを配布する前に、iOS Enterprise Developer Certificate でアプリに再署名する必要があります。

Lookout for Work iOS アプリに再署名する詳細な手順については、Lookout の Web サイトの「[Lookout for Work iOS app re-signing process](https://personal.support.lookout.com/hc/articles/114094038714)」(Lookout for Work iOS アプリの再署名プロセス) を参照してください。

#### <a name="enable-azure-ad-authentication-for-lookout-for-work-ios-app"></a>Lookout for Work iOS アプリで Azure AD 認証を有効にする

次の手順を実行して、iOS ユーザーの Azure Active Directory 認証を有効にします。

1. [Azure Portal](https://portal.sazure.com) に移動し、資格情報でサインインして、アプリケーションのページに移動します。
  
2. **ネイティブ クライアント アプリケーション**として **Lookout for Work iOS アプリ**を追加します。

3. **com.lookout.enterprise.yourcompanyname** は、IPA に署名したときに選択したカスタマー バンドル ID で置き換えます。

4.  リダイレクト URI を追加します。**&lt;companyportal://code/>** の後に、元のリダイレクト URI を URL エンコードしたバージョンを続けます。

5.  アプリに**デリゲートされたアクセス許可**を追加します。

    > [!NOTE] 
    > 詳細については、「[ネイティブ クライアント アプリケーションの構成](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application)」を参照してください。

#### <a name="add-the-lookout-for-work-ipa-file"></a>Lookout for Work の ipa ファイルを追加する

- [Intune での iOS LOB アプリの追加](lob-apps-ios.md)に関するトピックの説明に従って、再署名した .ipa ファイルをアップロードします。 また、最小 OS バージョンを iOS 8.0 以降に設定する必要があります。

## <a name="to-associate-the-mtd-app-with-an-ios-app-configuration-policy"></a>MTD アプリを iOS アプリ構成ポリシーと関連付けるには

### <a name="for-skycure"></a>Skycure の場合

-   Skycure 管理コンソールで以前に構成したものと同じ Azure AD アカウントを使用します。これは、Intune クラシック コンソールにログインするためのものと同じアカウントにする必要があります。

-   Skycure 統合ファイルを利用できる状態にしておく必要があります。 これは以前、Skycure 管理コンソールからダウンロードしておいた .zip ファイルです。**skycure\_configuration.plist** というファイルと iOS アプリ構成ポリシー パラメーターが含まれています。

- [iOS 用 Microsoft Intune アプリ構成ポリシーを使用する](app-configuration-policies-use-ios.md)手順に従って、Skycure iOS アプリ構成ポリシーを追加します。
    - 手順 8 で、**[XML データを入力する]** オプションを使用して内容を **skycure_configuration.plist** ファイルからコピーして、構成ポリシーの本文に貼り付けます。

**skycure_configuration.plist** の内容は以下からコピーすることもできます。

```
<dict>
    <key>MdmType</key>
    <string>Intune</string>
    <key>UserEmail</key>
    <string>{{userprincipalname}}</string>
</dict>

```
### <a name="for-lookout"></a>Lookout の場合

- [iOS アプリ構成ポリシーの使用](app-configuration-policies-use-ios.md)に関するトピックの説明に従って、iOS アプリ構成ポリシーを作成します。

## <a name="to-assign-mtd-apps"></a>MTD アプリを割り当てるには

- [Intune でアプリをグループに割り当てる](apps-deploy.md)手順を参照してください。

## <a name="next-steps"></a>次のステップ

[Skycure と Intune の統合をセットアップする](skycure-mtd-connector-integration.md)
[Lookout と Intune の統合をセットアップする](lookout-mtd-connector-integration.md)
