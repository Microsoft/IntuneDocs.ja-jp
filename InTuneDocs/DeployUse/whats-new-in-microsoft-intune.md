---
title: "新機能 | Microsoft Intune"
description: "Microsoft Intune の今月の新機能と過去のリリースの情報について説明します"
keywords: 
author: Lindavr
manager: angrobe
ms.date: 08/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d51ab5d486e7e23d2527f9cb95f105e7916cdb27
ms.openlocfilehash: 138d362618c9859a55988b7a2ada85e44b0e95c5


---

# Microsoft Intune の新機能
Microsoft Intune の今回のリリースの新機能について説明します。 また、過去のリリースに関する情報だけでなく、準備する必要がある今後の変更についても説明します。

これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx)を参照してください。
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

## 2016 年 8 月
## アプリ管理
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

### iOS 9.3 で表示されないアプリと表示されるアプリ
iOS 9.3 以降を実行するデバイスでは、iOS の一般構成ポリシーの表示されないアプリと表示されるアプリのリストを使用して次のことができます。
- ユーザーに対して表示されないアプリの一覧を指定します。 ユーザーはこのようなアプリを表示または起動できません。
- ユーザーが表示および起動できるアプリの一覧を指定します。 他のアプリは表示または起動できません。

ユーザー自身が展開したアプリと、Messages や Notes などの iOS 組み込みアプリの両方を指定できます。 詳細については、「[Microsoft Intune の iOS ポリシー設定]( https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)」を参照してください。
<!---TFS 1279009 checked--->
### Samsung KNOX デバイスでの許可するアプリとブロックするアプリのポリシー
Samsung KNOX デバイスでは、次のいずれかを作成できるカスタム ポリシーを構成できます。
- デバイスでの実行をブロックするアプリの一覧。 ブロック リストで定義されているアプリは、インストールされている場合でも、デバイスでアクティブにできません。
- デバイスのユーザーが Google Play ストアからインストールできるアプリの一覧。 他のアプリはストアからインストールできません。

これらの設定は、Samsung KNOX を実行するデバイスでのみ使用できます。
詳細については、「[カスタム ポリシーを使用して、Samsung KNOX デバイス用のアプリを許可またはブロックする]( custom-policy-to-allow-and-block-samsung-knox-apps.md)」を参照してください。
<!---TFS 1311629 checked --->
### モバイル アプリケーション管理 (MAM) ポリシーと互換性のある新しいアプリ
[iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) および [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) 向けの Yammer アプリは、デバイスが登録されていてもいなくても、[Intune モバイル アプリケーション管理 (MAM) ポリシー](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)と互換性があります。

MAM と互換性のある全アプリの一覧については、[Microsoft Intune アプリケーション パートナー](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)のサイトをご覧ください。
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

### Intune Viewer アプリ
新しい RMS 共有アプリのリリースに伴い、2016 年 8 月以降、次の Intune Viewer アプリを削除する予定です。
- Intune AV Viewer
- Intune PDF Viewer
- Google Play の Android 用 Intune Image Viewer

Intune Viewer アプリを使用する代わりに、[Android 用の新しい Rights Management アプリ (RMS 共有) ](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)を使用することをお勧めします。そうすることで、3 つのアプリを個別にではなく、1 つのアプリを展開して、Android デバイス上の企業ファイルを安全に表示することができます。 Intune Viewer アプリがサポートされなくなると、Google ストアから削除され、その後使用することができなくなります。

## デバイス管理
### Android 7.0 のサポート
Intune は近日公開予定のモバイル デバイス向け Android 7.0 オペレーティング システムの "Day 0" サポートを提供します。
<!---TFS 1262053--->
### Google による Android 7.0 デバイスでのリモート パスコード リセット機能の削除
Google は、IT 管理者やエンド ユーザーが Android 7.0 デバイスのパスコードをリモートでリセットする機能を削除しています。 これまでは、IT 管理者はユーザーのパスコードをリモートでリセットでき、エンド ユーザーはポータル サイトから自分のパスコードをリセットできました。



## ポータル サイトの更新
### ポータル Web サイト
- **ポータル サイトから Microsoft へのフィードバック リンク** <br/>
ポータル サイトの Web サイトでは、エンドユーザーはページの下部にある新しい [フィードバック] リンクをタップして、サイトの操作性に関するフィードバックを Microsoft に送信できるようになります。 収集されて匿名化されたフィードバックは、Microsoft がポータル サイトの Web サイトについてユーザーの操作性を向上させるのに役立ちます。
<!--- TFS 1313657 checked--->

### iOS
- **iOS Managed Browser の最小バージョンの 8.0 への更新**<br/>
iOS 用の Microsoft Intune Managed Browser アプリは、iOS 8.0 以降を実行するデバイスをサポートするように更新されました。 iOS 7.1 デバイスでは、既存の Managed Browser アプリを使用することができますが、新しい Managed Browser の機能にアクセスしてフル活用できるように、ユーザーに iOS 8.0 以降に更新することをお勧めしてください。  
<!---TFS 1313253 checked--->

## 今後の更新情報
### Intune グループから Azure Active Directory グループへの移行 (2016年 9 月以降)
Intune は、Intune でのユーザーとデバイスのグループとして Azure Active Directory (AAD) のセキュリティ グループを使用する、新しいグループ管理エクスペリエンスを作成しています。 これらのグループは、**新しい Azure ベースの Intune 管理ポータルの導入時**に、すべてのグループの管理、ポリシーの展開、およびプロファイルの展開に使用されます。

この新しいエクスペリエンスにより、サービス間でグループを複製する必要がなくなり、**新しい Azure Active Directory Premium (AADP) グループ機能の一部にアクセスすることができ** 、PowerShell および Graph を使用して拡張機能を提供します。 またこれにより、エンタープライズ モビリティ管理でのグループ管理エクスペリエンスも統合されます。

セキュリティ グループへの移行を有効にするため、**現在の管理コンソール**のエクスペリエンスにいくつかの変更が施されます。 **これらの変更と、AAD セキュリティ グループの使用については、Intune のドキュメントに記録されます**。

Intune の新規のお客様には、**現在のテナントに表示される前に、セキュリティ グループの変更の一部**が表示されます。

グループ管理の変更に加えて、**次の機能が廃止される予定です**。
- 新規グループ作成時のメンバーまたはグループの除外
- **グループ化を解除されたユーザー**と**グループ化を解除されたデバイス**のグループ
- サービス管理者の役割での**グループの管理**
- 通知ルールに対するカスタム グループベースの警告
- レポート内のグループのピボット
<!--- TFS 1295329--->

### Android 用ポータル サイトへの '通知' の追加
Microsoft は、Android 用ポータル サイトに対する更新を 9 月にリリースし、ホームページ上に新しい**通知**アイコンを導入します。 このアイコンをタップすると、**通知**ページにアクセスし、デバイスのコンプライアンス非対応、登録の更新、および登録のアクティブ化などのポータル サイト アプリで注意が必要なすべての項目をエンド ユーザーに表示します。 iOS 用ポータル サイト アプリも使用している場合は、通知エクスペリエンスがすでに表示されます。 **通知**ページの導入に伴い、デバイスがすでに登録されている限り、Android 用ポータル サイトを起動または再開するたびに**会社アクセスのセットアップ**ページが表示されることはなくなります。 Microsoft は、多くのお客様がエンドユーザー ガイダンスを作成していることを把握しており、ガイダンスとスクリーンショットの更新が必要になる場合に事前に通知くださることに感謝いたします。 ドキュメントに今後のエクスペリエンスの変更を反映し、更新してください。 最新のスクリーンショットは、 https://aka.ms/androidcpupdate でご確認いただけます。  


### クラウドのロードマップ
[クラウド プラットフォームのロードマップ](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)では、Intune の今後の開発に関する情報を入手できます。

### 廃止予定のサービス
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **iOS ポータル サイト アプリのサポートの変更**<br/>
9 月には、iOS 用 Microsoft Intune ポータル サイト アプリのすべてのユーザーが、アプリの最新バージョンを使用するように要求されます。 新しいユーザーは最新バージョンのみをダウンロードでき、現在のユーザーは最新バージョンへの更新を求められます。 最新バージョンを使用するには iOS 8.0 以降が必要であり、デバイスで以前の iOS バージョンを実行している場合は、デバイスを iOS 8.0 以降に更新したうえでポータル サイト アプリを最新バージョンに更新するまで、ポータル サイトを使用できず、登録することもできません。 iOS 8.0 以前のバージョンを実行している登録済みのデバイスは、引き続き管理対象であり、Intune 管理コンソールに表示されます。  

- **iOS Managed Browser の最小バージョンの 8.0 への更新**<br/>
8 月、Intune は iOS 8.0 以降を実行するデバイスのみをサポートする、iOS 用の最新の Microsoft Intune Managed Browser アプリをリリースします。 iOS 7.1 デバイスでは、既存の Managed Browser アプリを使用することができますが、新しい Managed Browser の機能にアクセスしてフル活用できるように、ユーザーに iOS 8.0 以降に更新することをお勧めしてください。  
<!---TFS 1313253--->

- **Windows 8 および Windows Phone 8 用のポータル サイト アプリは、2016 年 9 月以降非推奨になります** <br/>
Microsoft Intune は、2016 年 9 月以降、Windows Phone 8 および Windows 8 プラットフォーム用 Microsoft Intune ポータル サイト アプリのサポートを終了します。 デバイスを Windows 8.1 および Windows Phone 8.1 に更新し、対応する Windows 8.1 および Windows Phone 8.1 のポータル サイト アプリを使用して、更新したデバイスへのアプリの配布を続行します。
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->



## 以前の Intune のリリース
過去 6 か月間に公開された Intune のリリースについては、「[以前の Intune のリリース](previous-intune-releases.md)」の記事をご覧ください。

### 関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Aug16_HO3-->


