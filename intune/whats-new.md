---
title: "Microsoft Intune の新機能"
titleSuffix: Intune on Azure
description: "Intune Azure Portal の新機能を確認する"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 06/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 73b43084c28436cb8a7e866dcee2d52694c60f5c
ms.openlocfilehash: 1a3069e128e25f4f0f5df7cc90392055729134fa
ms.contentlocale: ja-jp
ms.lasthandoff: 06/16/2017

---

# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune の新機能

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

週ごとにまとめた、Microsoft Intune の新機能をご覧ください。 [今後の変更](#whats-coming)、サービスに関する[重要なお知らせ](#notices)、[過去のリリース](whats-new-archive.md)に関する情報も確認できます。

> [!Note]
> これらの機能の多くは、最終的に Configuration Manager とのハイブリッド環境でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。

## <a name="week-of-june-12-2017"></a>2017 年 6 月 12 日の週

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>ポータル サイトを簡単に削除できるアクション メニューの追加<!--1164569-->
Android 用ポータル サイト アプリでは、ユーザーからのフィードバックに基づき、デバイスからポータル サイトの削除を開始できる新しいアクション メニューが追加されました。 この操作では Intune の管理対象からデバイスが削除されるため、ユーザーはデバイスからアプリを削除できるようになります。 これらの変更については、[Android エンド ユーザー向けドキュメント](/intune-user-help/unenroll-your-device-from-intune-android)の[アプリ UI の新機能](whats-new-app-ui.md)に関するページで確認できます。

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Windows 10 Creators Update とアプリを同期する機能の強化 <!--676505-->

Windows 10 用ポータル サイト アプリでは、Windows 10 Creators Update (バージョン 1703) がインストールされているデバイスのアプリ インストール要求の同期が自動的に開始されるようになりました。 "同期保留中" 状態中、アプリ インストールが止まる問題を減らします。 また、ユーザーはアプリ内から同期を手動で開始できます。 

## <a name="week-of-june-5-2017"></a>2017 年 6 月 5 日の週

### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Microsoft Intune 管理コンソールと条件付きアクセス管理コンソールの一般提供開始

Azure の新しい Intune 管理コンソールと、条件付きアクセス管理コンソールの一般提供開始が発表されました。 Azure から Intune を利用することで、Intune MAM および MDM のすべての機能を統合された 1 つの管理者エクスペリエンスで管理し、Azure AD のグループとターゲットを利用できるようになりました。 Azure の条件付きアクセスにより、Azure AD と Intune の豊富な機能が一元化されたコンソールに統合されます。 また管理者エクスペリエンスから Azure プラットフォームに移動して、最新のブラウザーを使用できます。

Intune は、**[プレビュー]** ラベルが外されて Azure コンソール (portal.azure.com) に表示されるようになりました。

メッセージ センターの一連のメッセージのうち、グループを移行できるようにお客様の対応をお願いするメッセージを受信された場合を除き、現時点で既存のお客様にしていただくことはありません。 こちらのバグにより、移行に時間がかかることをお知らせする通知がメッセージ センターから送信されている場合もあります。 Microsoft では、影響を受けたユーザーを移行する作業に引き続き取り組んでまいります。

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>iOS 用ポータル サイト アプリのアプリ タイルを改善
ポータル サイトに設定したブランド カラーが反映されるよう、ホーム ページのアプリ タイルのデザインを一新しました。 詳細については、[アプリ UI の新機能](whats-new-app-ui.md)に関するページをご覧ください。

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>iOS 用ポータル サイト アプリでアカウント選択の提供を開始
iOS デバイスのユーザーが、職場または学校アカウントを使用して別の Microsoft アプリにサインインしているときに、ポータル サイトにサインインしようとすると、新しいアカウントの選択が表示される場合があります。 詳細については、[アプリ UI の新機能](whats-new-app-ui.md)に関するページをご覧ください。

## <a name="week-of-may-29-2017"></a>2017 年 5 月 29 日の週

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>管理対象デバイスの登録を解除せず、MDM 機関を変更する <!--1103950-->

Microsoft サポートに問い合わせずに、また、既存の管理されたデバイスの登録解除と再登録を行わずに MDM 機関を変更できるようになりました。 Configuration Manager コンソールで、[Configuration Manager に設定]\(ハイブリッド\) から [Microsoft Intune]\(スタンドアロン\) に、またはその逆に [MDM 機関を変更](/sccm/mdm/deploy-use/change-mdm-authority)できます。 


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Samsung KNOX 起動 PIN の通知機能強化 <!--1087143-->
暗号化に対応する目的でエンド ユーザーが Samsung KNOX デバイスに起動 PIN を設定する必要があるとき、エンド ユーザーに表示される通知をタップすると、設定アプリ内の設定場所に移動します。  以前は、エンド ユーザーは通知からパスワード変更画面に進むことができました。


### <a name="device-enrollment"></a>デバイスの登録

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>共有 iPad での Apple School Manager (ASM) のサポート <!-- 748864, 770395-->

Intune では、Apple Device Enrollment Program の代わりに Apple School Manager (ASM) を使用できるようになりました。すぐに iOS デバイスを登録できます。 共有 iPad で Classroom アプリを使用するには ASM オンボードが必要です。これは、Microsoft School Data Sync (SDS) 経由で ASM から Azure Active Directory へのデータ同期を有効にする際にも必要です。 詳細については、「[Enable iOS device enrollment with Apple School Manager (Apple School Manager での iOS デバイス登録の有効化)](apple-school-manager-set-up-ios.md)」をご覧ください。

> [!NOTE]
> 共有 iPad で Classroom アプリを使用できるように構成するには、Azure に iOS 向けの Education の構成が必要ですが、現時点では提供されていません。  この機能は、近日中に追加される予定です。

### <a name="device-management"></a>デバイス管理

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>TeamViewer を利用して Android デバイスに リモート アシスタンスを提供<!-- 675418 -->

Intune では、別売りの [TeamViewer](https://www.teamviewer.com) ソフトウェアを利用して、Android デバイスを使用するユーザーにリモート アシスタンスを提供できるようになりました。 詳細については、「[Provide remote assistance for Intune managed Android devices (Intune 管理対象の Android デバイスにリモート アシスタンスを提供)](device-profile-android-teamviewer.md)」をご覧ください。

### <a name="app-management"></a>アプリ管理

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>MAM の新しいアプリ保護ポリシー条件 <!-- 679864 -->

登録ユーザーなしで、次のポリシーを強制する MAM の要件を設定できるようになりました。

- アプリケーションの最小バージョン
- オペレーティング システムの最小バージョン
- 対象アプリケーションの最小 Intune APP SDK バージョン (iOS のみ)

この機能は、Android と iOS の両方で使うことができます。 Intune は、OS プラットフォーム バージョン、アプリケーション バージョン、Intune APP SDK の最小バージョン強制に対応しています。 iOS の場合、SDK が統合されているアプリケーションでも SDK レベルで最小バージョン強制を設定できます。 アプリ保護ポリシーの最小要件が上述の 3 つの異なるレベルで満たされていない場合、ユーザーは対象アプリケーションにアクセスできません。 この時点で、ユーザーはアカウントを削除するか (複数 ID アプリケーションの場合)、アプリケーションを閉じるか、OS またはアプリケーションのバージョンを更新できます。

また、OS またはアプリケーションのアップグレードを推奨するブロック不可の通知を表示するように追加設定することもできます。 この通知は閉じて、アプリケーションを普段どおり使用できます。

詳細については、「[iOS アプリ保護ポリシー設定](app-protection-policy-settings-ios.md)」と「[Android アプリ保護ポリシー設定](app-protection-policy-settings-android.md)」をご覧ください。

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Android for Work 用のアプリ構成の設定<!-- 621621 -->
ストアの一部の Android アプリは管理対象の構成オプションをサポートしているため、IT 管理者は作業プロファイルでアプリの実行方法を制御できます。 Intune では、Intune ポータルからアプリがサポートする構成を表示し、構成デザイナーまたは JSON エディターを使用してこれらの構成を設定できるようになりました。 詳細については、[Android for Work 用のアプリ構成の使用](app-configuration-policies-use-android.md)に関するページをご覧ください。

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>登録なしで利用できる MAM の新しいアプリ構成機能<!-- 677969 -->

登録チャネルがなくても MAM からアプリ構成ポリシーを作成できるようになりました。 これは、モバイル デバイス管理 (MDM) のアプリ構成で使用できるアプリ構成ポリシーと同等の機能です。 登録せずに MAM を使用してアプリを構成する例については、「[Manage Internet access using Managed browser policies with Microsoft Intune (Microsoft Intune と Managed Browser のポリシーを使用したインターネット アクセスの管理)](app-configuration-managed-browser.md)」をご覧ください。

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Managed Browser で許可される URL とブロックされる URL 一覧の構成<!-- 682960 -->

Azure Portal のアプリ構成設定を使用して、Intune Managed Browser で許可またはブロックされるドメインおよび URL の一覧を構成できるようになりました。 これらの設定は、管理されたデバイスで使用されているか、管理されていないデバイスで使用されているかに関係なく構成できます。 詳細については、「[Manage Internet access using Managed browser policies with Microsoft Intune (Microsoft Intune と Managed Browser のポリシーを使用したインターネット アクセスの管理)](app-configuration-managed-browser.md)」をご覧ください。

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>アプリ保護ポリシー ヘルプデスクのビュー<!-- 1069473 -->

IT ヘルプデスクのユーザーは、[トラブルシューティング] ブレードで、ユーザー ライセンスの状態と、ユーザーに割り当てられているアプリのアプリ保護ポリシーの状態を確認できるようになりました。 詳細については、[トラブルシューティング](./help-desk-operators.md)に関するページをご覧ください。

### <a name="device-configuration"></a>デバイス構成

#### <a name="control-website-visits-on-ios-devices----723832---"></a>iOS デバイスの Web サイト アクセスの制御<!-- 723832 -->

iOS デバイスのユーザーがアクセスできる Web サイトを次の 2 つの方法を使って制御できるようになりました。

- Apple の組み込み Web コンテンツ フィルターを使って、許可される URL またはブロックされる URL を追加します。

- Safari ブラウザーによるアクセスを許可する Web サイトを指定します。 指定した各サイトについて、Safari にブックマークが作成されます。

詳細については、「[Web content filter settings for iOS devices (iOS デバイス用の Web コンテンツ フィルター設定)](web-content-filter-settings-ios.md)」をご覧ください。

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Android for Work アプリのデバイス アクセス許可の事前構成 <!-- 621614 -->

Android for Work デバイスの作業プロファイルに展開したアプリの場合、個々のアプリのアクセス許可状態を構成できるようになりました。  既定では、場所やデバイス カメラへのアクセスなど、デバイスのアクセス許可を必要とする Android アプリはアクセス許可の承諾または拒否をユーザーに求めます。  たとえば、アプリでデバイスのマイクが使用される場合、そのマイクを使用するアクセス許可をアプリに与えるようにエンド ユーザーに求められます。 この機能を利用すると、エンド ユーザーの代わりにアクセス許可を定義できます。  アクセス許可は、a) ユーザーに通知することなく自動的に拒否する、b) ユーザーに通知することなく自動的に承諾する、c) 承諾または拒否をユーザーに求めるのいずれかに構成できます。 詳細については、「[Microsoft Intune での Android for Work デバイスの制限設定](device-restrictions-android-for-work.md)」をご覧ください。

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Android for Work デバイスのアプリ固有 PIN を定義する <!-- 728976, 1102534 -->

管理者は、Android for Work デバイスとして管理されている Android 7.0 以上のデバイスの作業プロファイルで、作業プロファイルのアプリにのみ適用されるパスコード ポリシーを定義できます。  次のオプションがあります。

- デバイス全体のパスコード ポリシーだけを定義する - これは、デバイス全体のロックを解除するためにユーザーが使用しなければならないパスコードです。
 作業プロファイルのパスコード ポリシーだけを定義する - 作業プロファイルのアプリを起動するたびに、ユーザーにパスコードの入力が求められます。
- デバイスと作業プロファイル ポリシーの両方を定義する - IT 管理者はデバイスのパスコード ポリシーと作業プロファイルのパスコード ポリシーをいずれも異なる強度で定義できます。たとえば、デバイスのロック解除に 4 桁の PIN を要求し、作業アプリの起動に 6 桁の PIN を要求します。

詳細については、「[Microsoft Intune での Android for Work デバイスの制限設定](device-restrictions-android-for-work.md)」をご覧ください。

> [!NOTE]
> この機能は Android 7.0 以降でのみ利用できます。  既定では、エンド ユーザーは別々に定義された 2 つの PIN を利用できます。あるいは、定義された 2 つの PIN のうちの強いほうを選択できます。

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Windows 10 デバイスの新しい設定<!-- 978585 -->

Microsoft は、無線ディスプレイ、デバイス検出、タスク切り替え、SIM カード エラー メッセージなどの機能を制御する新しい [Windows デバイス制限設定](device-restrictions-windows-10.md)を追加しています。

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>証明書の構成の更新<!-- 918991 and 823198 -->

SCEP 証明書プロファイルを作成するときに、**[サブジェクト名の形式]**で、**[カスタム]** オプションを iOS、Android、および Windows デバイスでご利用いただけます。 今回の更新までは、**[カスタム]** フィールドを使用できるのは iOS デバイスだけでした。 詳細については、「SCEP 証明書プロファイルを作成する方法」(certificates-scep-configure.md#how-to-create-a-scep-certificate-profile) をご覧ください。

PKCS 証明書プロファイルを作成するときに、**[サブジェクトの別名]** で、**[Custom Azure AD attribute]\(Azure AD のカスタム属性\)** をご使用いただけます。 **[Custom Azure AD attribute]\(Azure AD のカスタム属性\)** を選択すると、**[部門]** オプションが使用できます。 詳細については、「PKCS 証明書プロファイルを作成する方法」(certficates-pfx-configure.md#how-to-create-a-pkcs-certificate-profile) をご覧ください。

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Android デバイスがキオスク モードのときに実行できる複数アプリの構成<!-- 662059 -->

これまでは、Android デバイスがキオスク モードのときに実行できるアプリは 1 つしか設定できませんでした。 アプリ ID やストアの URL を使用するか、すでに管理している Android アプリを選択して、複数のアプリを設定できるようになりました。 詳細については、[キオスク モードの設定](device-restrictions-android.md#kiosk)に関するページをご覧ください。


## <a name="notices"></a>通知

### <a name="ip-addresses-for-intune-updated----1175274---"></a>Intune の IP アドレスの更新<!-- 1175274 -->

[DNS 名と IP アドレスの更新された一覧](/intune/network-bandwidth-use)を、ファイアウォールのプロキシ設定に使用できます。

### <a name="use-azure-active-directory-for-conditional-access----967947---"></a>Azure Active Directory で条件付きアクセスを使用<!-- 967947 -->

Azure コンソールの Azure Active Directory セクションで条件付きアクセスが使用できるようになりました。Office 365 Exchange Online や SharePoint Online などのクラウド アプリのポリシー設定のための、強力かつ柔軟なフレームワークをご利用いただけます。  クラシックの Intune コンソールの代わりに **[Conditional access in Azure Active Directory]\(Azure Active Directory の条件付きアクセス\)** ブレードを使用して、ポリシーを構成します。 クラシックの Intune コンソールで作成した既存のポリシーは、Azure コンソールで再作成する必要があります。 詳細については、「[Create Azure AD conditional access policies (Azure AD の条件付きアクセス ポリシーを作成する)](/intune/conditional-access-exchange-create.md#create-azure-ad-conditional-access-policies-in-intune-azure-preview)」をご覧ください。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->

Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure Portal の Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューはクラシックの Intune ポータルのリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントで Azure Portal にアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Azure Portal で置き換えられる管理ロール

Intune クラシック ポータル (Silverlight) で使用される既存のモバイル アプリケーション管理 (MAM) の管理ロール (共同作成者、所有者、および読み取り専用) は、Intune Azure Portal の新しいロール ベースの管理制御 (RBAC) の完全なセットで置き換えられます。 Azure Portal に移行すると、管理者をこれらの新しい管理ロールに割り当て直す必要があります。 RBAC と新しいロールの詳細については、[Microsoft Intune のロール ベースのアクセス制御](/intune/role-based-access-control)に関する記事を参照してください。

## <a name="whats-coming"></a>今後の更新情報

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>すべてのプラットフォームでのポータル サイト アプリのサインイン操作の改善<!--User Story 1132123-->

Android、iOS、Windows 用の Intune ポータル サイト アプリのサインイン エクスペリエンス向上のために、今後数か月間に予定されている変更についてお知らせします。 Azure AD でこの変更が行われ次第、自動的にすべてのプラットフォームでポータル サイト アプリのユーザー エクスペリエンスが一新される予定です。 また、自動生成される一時使用コードを使用して、別のデバイスからポータル サイトにサインインできるようになりました。 これは、資格情報を使用せずにサインインする必要がある場合には特に便利です。

以前のサインイン エクスペリエンス、資格情報を使用した新たなエクスペリエンス、別のデバイスからのエクスペリエンスのスクリーンショットを確認するには、[アプリ UI の新機能](/intune/whats-new-app-ui)に関するページをご覧ください。

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>変更の計画: Intune で Intune パートナー ポータル エクスペリエンスが変更されます<!-- 1050016 -->

2017 年 5 月中旬のサービス更新で、Intune パートナーのページが manage.microsoft.com から削除されます。  

お客様がパートナーの管理者である場合は、Intune パートナーのページで顧客に代わって閲覧したり、操作したりすることができなくなります。代わりに、Microsoft の他の 2 つのパートナー ポータルのいずれかでサインインする必要があります。

[Microsoft パートナー センター](https://partnercenter.microsoft.com/)と [Microsoft Office 365 パートナー管理センター](https://portal.office.com/)の両方で、管理している顧客アカウントにサインインできます。 パートナーとして前進するために、これらのサイトのいずれかを使用して顧客の管理を行いましょう。


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->

Apple は、Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。

Microsoft では、新しい ATS 要件を適用する Apple TestFlight プログラムから、iOS 用ポータル サイト アプリのバージョンを入手できるようにしています。 ATS コンプライアンスをテストできるように、このバージョンを試す場合は、お客様の姓名、電子メール アドレス、および会社名を <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> に電子メールで送信してください。 詳細については、[Intune サポートのブログ](https://aka.ms/compportalats)をご覧ください。

### <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [ポータル Web サイトの UI の新機能](whats-new-app-ui.md)
* [以前の月の新機能](whats-new-archive.md)

