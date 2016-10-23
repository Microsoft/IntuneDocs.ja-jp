---
title: "新機能 | Microsoft Intune"
description: "Microsoft Intune の今月の新機能と過去のリリースの情報について説明します"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 503719953031bf5079b2bf5bc84a0497d708f79a
ms.openlocfilehash: 730809e0841a248b90f5fe157f2c6338bfd32b2d


---
# Microsoft Intune の新機能 - 2016 年 10 月
Microsoft Intune の今回のリリースの新機能について説明します。 また、過去のリリースに関する情報だけでなく、準備する必要がある今後の変更についても説明します。

これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://technet.microsoft.com/library/mt718155.aspx)を参照してください。
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

## 新機能

### モバイル アプリケーションを管理するための条件付きアクセス
Exchange Online へのアクセスを制限して、Intune モバイル アプリケーション管理ポリシーをサポートするアプリ (Outlook など) からのアクセスのみを許可することができます。 [この新機能](/intune/deploy-use/allow-policy-managed-apps-access-to-o365)は組み込みのメール クライアントや Intune MAM ポリシーが構成されていない他のアプリへのアクセスをブロックできるため、Intune のモバイル アプリ管理 (MAM) ポリシーと組み合わせると効果的です。 これにより、ユーザーが組織のデータにアクセスする際に、Intune MAM を使用して保護できるアプリを使用するようになります。 Intune モバイル アプリ管理は、Azure ポータルから使用することができます。 [設定] ブレードの新しい [条件付きアクセス] セクションを探してください。

### Windows PC の条件付きアクセス
Intune 管理コンソールを通して条件付きアクセス ポリシーを作成することで、Windows PC が [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) および [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) にアクセスするのをブロックできるようになりました。 また、Office デスクトップおよびユニバーサル アプリケーションへのアクセスをブロックする条件付きアクセス ポリシーを作成することもできます。

### Android for Work のサポート
Intune は、現在、Android for Work プログラムの一部となっています。 Intune に対する Android for Work 機能のサポートのロールアウトを今月から開始します。
[Android for Work の Intune サポートに関する Microsoft からのお知らせをお読みください](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/)。

次の Intune トピックは、Android for Work に関する新しい情報と更新情報を扱っています。

IT プロフェッショナル向け:
- [Android for Work のセットアップ](/intune/deploy-use/set-up-android-for-work)
<!--- [Nathan Bigman's resource access topics]()-->
- [Intune で Exchange Online と新しい Exchange Online Dedicated への電子メール アクセスを制限する](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [Intune で Exchange On-premises と従来の Exchange Online Dedicated への電子メール アクセスを制限する](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Android for Work のコンプライアンス ポリシー設定](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [Android for Work アプリを展開する方法](/intune/deploy-use/android-for-work-apps)
- [モバイル アプリ構成ポリシーを使用した Android for Work アプリの構成](/intune/deploy-use/afw-app-configuration-policy)
- [Android for Work のポリシー設定](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

エンド ユーザー向け:
- [仕事用プロファイルを作成するとどうなりますか](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [Intune での仕事用プロファイルの作成とデバイスの登録](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### iOS デバイスを保護するため Lookout 統合
10 月、Microsoft は、デバイス上のマルウェアやリスクの高いアプリなどを検出して iOS モバイル デバイスを保護するため、Lookout のモバイル脅威保護ソリューションに統合します。 Lookout のソリューションにより、構成可能な脅威レベルを決定できます。 Intune に、Lookout によるリスク評価に基づいてデバイスのコンプライアンスを判断するためのコンプライアンス ポリシー ルールを作成できます。 条件付きアクセス ポリシーを使用すると、デバイスのコンプライアンス状態に基づいて、会社のリソースへのアクセスを許可したりブロックしたりできます。

非準拠 iOS デバイスのエンド ユーザーは登録が求められ、会社のデータへのアクセス権を得るにはデバイスへの Lookout for Work アプリケーションのインストール、アプリのアクティブ化、Lookout for Work アプリケーションで報告された驚異の修復が必要となります。 [Lookout for Work アプリを構成して展開する](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps)方法について説明します。
<!--TFS 1319493-->

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

### Android 用 Intune アプリ ラッピング ツール
Intune アプリ ラッピング ツールを使うと、アプリで Intune モバイル アプリケーション管理 (MAM) ポリシーを使用できるようになります。 デバイスの登録を必要としない Intune MAM ポリシーのサポートが開始されました。

### MAM ポリシーを使用して管理されたアプリケーションから印刷する
MAM ポリシーを使用しているアプリから会社データが印刷されるのを防ぐことができるようになりました。 この設定は、[Azure ポータル](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)で利用することができ、[iOS](/Intune/deploy-use/ios-mam-policy-settings) デバイスと [Android](/Intune/deploy-use/android-mam-policy-settings) デバイスの両方でサポートされています。
<!--TFS 1014328-->

## 通知

### Android Samsung KNOX と Intune の互換性
スマートフォン Samsung Galaxy Ace の特定のモデルは、Samsung KNOX デバイスとして Intune で管理することができません。 これらのデバイスは、Intune に登録すると、標準の Android デバイスとして管理されます。

該当するモデルの番号は次のとおりです。

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

お客様とエンドユーザーは、これ以上操作を行う必要はありません。 詳細については、[Samsung KNOX](https://www.samsungknox.com) の Web サイトをご覧ください。

### Windows 8 のポータル サイト アプリは廃止されています。Windows Phone 8 および Windows RT プラットフォームのサポートは廃止される予定です。
2016年 10 月以降、Microsoft Intune は Windows 8 ポータル サイトのサポートを廃止します。 Microsoft Intune は、Windows Phone 8 プラットフォームおよび Windows RT プラットフォームのサポートも廃止します。 その結果、Windows Phone 8 デバイスまたは Windows RT デバイスの登録または更新はできなくなります。

既に登録されている Windows Phone 8 デバイス、 Windows RT デバイス、Windows 8 デバイスは継続して管理できます。 デバイスへのアプリの配布を中断することなく続行するには、Windows Phone 8 および Windows 8 デバイスを Windows 8.1 および Windows Phone 8.1 に更新し、対応する Windows 8.1 および Windows Phone 8.1 のポータル サイト アプリを使用します。

2016 年 11 月以降、Windows Phone 8 ポータル サイトのサポートは廃止されます。
<!--TFS 1255391-->

## 今後の更新情報

### Windows 10 デバイスで使用可能な新しい Microsoft Intune ポータル サイト
Microsoft は、Windows 10 デバイス用に新しい Microsoft Intune ポータル サイトをリリースします。 このアプリでは新しい Windows 10 ユニバーサル形式を利用します。このアプリ内ではユーザーに対して更新されたユーザー エクスペリエンスが提供され、すべての Windows 10 デバイスで同じエクスペリエンスが提供されます。現在使用されている機能はすべて引き続き利用できます。

この新しいアプリでは、ユーザーは、Windows 10 デバイスでのシングル サインオン (SSO) や証明書ベースの認証など、追加のプラットフォーム機能も利用することができます。 アプリは、既存の Windows 8.1 ポータル サイトおよび Windows Phone 8.1 ポータル サイトのインストールのアップグレードとして Windows ストアから入手できるようになります。 詳細については、[aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp) を参照してください。
<!--TFS 1016502-->

### 関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [以前の Intune のリリース](previous-intune-releases.md)



<!--HONumber=Oct16_HO3-->


