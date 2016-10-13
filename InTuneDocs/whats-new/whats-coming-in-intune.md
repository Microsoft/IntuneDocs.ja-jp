---
title: "初期エディション | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5c4b0f15456a9f24c95954d669a17c63f96a459
ms.openlocfilehash: 273016d4fe114bbe60e9cebc06e89584c8f91f0b


---

# Microsoft Intune に今後予定されている機能 - 10 月
**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能を一覧します。 ここに記載されている情報は、秘密保持契約書のもとごく限られた範囲について開示されたものであり、また今後変更される可能性があります。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Intune の開発チームまたは PM にお問い合わせください。

このページは定期的に更新されます。 定期的にこちらのページをご覧のうえ最新の機能をチェックしてください。

Intune に関して以下の機能が現在開発されています。 これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx)を参照してください。

### MAM ポリシーを使用して管理されたアプリケーションから印刷する
MAM ポリシーを使用しているアプリから会社データが印刷されるのを防ぐことができるようになりました。 この設定は、[Azure ポータル](..deployuse/create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)で利用することができ、[iOS](..deployuse/ios-mam-policy-settings) デバイスと [Android](..deployuse/android-mam-policy-settings) デバイスの両方でサポートされています。
<!--TFS 1014328-->

### Windows 10 デバイスで使用可能な新しい Microsoft Intune ポータル サイト
Microsoft は、Windows 10 デバイス用に新しい Microsoft Intune ポータル サイトをリリースします。 このアプリでは新しい Windows 10 ユニバーサル形式を利用します。このアプリ内ではユーザーに対して更新されたユーザー エクスペリエンスが提供され、すべての Windows 10 デバイスで同じエクスペリエンスが提供されます。現在使用されている機能はすべて引き続き利用できます。

この新しいアプリでは、ユーザーは、Windows 10 デバイスでのシングル サインオン (SSO) や証明書ベースの認証など、追加のプラットフォーム機能も利用することができます。 アプリは、既存の Windows 8.1 ポータル サイトおよび Windows Phone 8.1 ポータル サイトのインストールのアップグレードとして Windows ストアから入手できるようになります。
<!--TFS 1016502-->

### Android for Work のサポート

Intune は、現在、[Android for Work プログラム](https://enterprise.google.com/android/partners/)の一部となっています。 Intune に対する Android for Work 機能のサポートのロールアウトを今月から開始します。

[Android for Work の Intune サポートに関する Microsoft からのお知らせをお読みください](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/)。

<!---This month, some newly provisioned Intune tenants will start seeing the Android for Work features. We will announce later when existing tenants will begin to see this feature.--->
<!--TFS 1043303-->

### Android Samsung KNOX と Intune の互換性

スマートフォン Samsung Galaxy Ace の特定のモデルは、Samsung KNOX デバイスとして Intune で管理することができません。 これらのデバイスは、Intune に登録すると、標準の Android デバイスとして管理されます。
該当するモデルの番号は次のとおりです。

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

お客様とエンドユーザーは、これ以上操作を行う必要はありません。
詳細については、[Samsung KNOX](https://www.samsungknox.com) の Web サイトをご覧ください。

<!--TFS 1173566 iX blurb provided by Barry; requires PM signoff

### Multi-factor authentication for Android and iOS enrollment

In addition to Windows 8.1 and later, administrators can now enable multi-factor authentication for Android and iOS devices in the Microsoft Intune Enrollment application. -->    

### Windows 8 のポータル サイト アプリは廃止されています。Windows Phone 8 および Windows RT プラットフォームのサポートは廃止される予定です。
2016年 10 月以降、Microsoft Intune は Windows 8 ポータル サイトのサポートを廃止します。 Microsoft Intune は、Windows Phone 8 プラットフォームおよび Windows RT プラットフォームのサポートも廃止します。 その結果、Windows Phone 8 デバイスまたは Windows RT デバイスの登録または更新はできなくなります。

既に登録されている Windows Phone 8 デバイス、 Windows RT デバイス、Windows 8 デバイスは継続して管理できます。 デバイスへのアプリの配布を中断することなく続行するには、Windows Phone 8 および Windows 8 デバイスを Windows 8.1 および Windows Phone 8.1 に更新し、対応する Windows 8.1 および Windows Phone 8.1 のポータル サイト アプリを使用します。

2016 年 11 月以降、Windows Phone 8 ポータル サイトのサポートは廃止されます。
<!--TFS 1255391-->

### モバイル アプリケーションを管理するための条件付きアクセス
管理されていないモバイル アプリが [Exchange Online](..deployuse/restrict-access-to-exchange-online-with-microsoft-intune.md) および [SharePoint Online](..deployuse/restrict-access-to-sharepoint-online-with-microsoft-intune.md) にアクセスするのをブロックするための条件付きアクセス ポリシーを作成できるようになりました。 Intune アプリ SDK を使用すれば、MAM に対応していない組み込みのメール クライアントおよびアプリをブロックすることができます。  そのためには、Azure ポータルを使用して条件付きアクセス ポリシーを作成し、Exchange Online と SharePoint Online へのアクセスを許可するアプリケーションを指定します。
<!--TFS 1317673-->

<!--TFS 1318014; awaiting approval in notes as to whether to proceed

### "Default" policy is deprecated

To minimize unintentionally assigned profiles, Intune is removing support for the "default" Corporate Device Enrollment profile for Apple Device Enrollment Program (DEP) device serial numbers in the new Azure console. Serial numbers synchronized from an Apple DEP account will initially have no Corporate Device Enrollment profile assigned.  A profile must be assigned manually after synchronization. This change will apply to the new console only. Until the existing Admin console is retired, no change will take place.
-->

<!--TFS 1318023; awaiting approval in notes as to whether to proceed

### Deprecation of row-by-row iOS Details review for iOS device CSV uploads

In order to streamline uploading IMEI numbers for Corporate devices and Apple serial numbers for Configurator enrollment, Intune is removing the row by row review of hardware identifiers already found in the system. This review allows the IT Pro to accept associated Details from the CSV to overwrite the existing details for a hardware identifier already in the system. The review will be replaced by a single option to automatically overwrite Details for all hardware identifiers or ignore new details for existing identifiers. This change will apply to the new console only. Until the existing Admin console is retired, no change will take place.
-->

### iOS デバイスを保護するため Lookout 統合
10 月、Microsoft は、デバイス上のマルウェアやリスクの高いアプリなどを検出して iOS モバイル デバイスを保護するため、Lookout のモバイル脅威保護ソリューションに統合します。 Lookout のソリューションにより、構成可能な脅威レベルを決定できます。 Intune に、Lookout によるリスク評価に基づいてデバイスのコンプライアンスを判断するためのコンプライアンス ポリシー ルールを作成できます。 条件付きアクセス ポリシーを使用すると、デバイスのコンプライアンス状態に基づいて、会社のリソースへのアクセスを許可したりブロックしたりできます。

非準拠 iOS デバイスのエンド ユーザーは登録が求められ、会社のデータへのアクセス権を得るにはデバイスへの Lookout for Work アプリケーションのインストール、アプリのアクティブ化、Lookout for Work アプリケーションで報告された驚異の修復が必要となります。
<!--TFS 1319493-->

### Android 用の Intune アプリ SDK とアプリ ラッピング ツール
Intune アプリ ラッピング ツールまたは Intune アプリ SDK のいずれかを使うと、アプリで Intune モバイル アプリケーション管理 (MAM) ポリシーを使用することが可能です。 アプリ ラッピング ツールと SDK の新しい更新プログラムには、次のサポートが含められます。

* Android N のサポート
* デバイスの登録を必要としない Intune MAM ポリシーのサポート
* Xamarin ベースの Android アプリのサポート

Android アプリ ラッピング ツールのパブリック プレビュー ([https://github.com/msintuneappsdk/intune-app-wrapper-android-preview](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview)) では、デバイスの登録や Xamarin サポートなしで MAM をテストすることができます。
<!--TFS 1319511; please create new TFS entry for WN text associated with this TFS item-->

<!--TFS 1319613; no iX review on PM text blurb

### Private preview customers using MAM Conditional Access will have their policies reset

Due to changes in the policy structure for Conditional Access for Mobile App Management, any existing policies that were set by customers through the private preview will be removed. Customers will need to set new policies once the change is made. The timing will coincide with the October service update.
-->

### 関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new-in-microsoft-intune.md)」をご覧ください。



<!--HONumber=Oct16_HO1-->


