---
title: 開発中 - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune の開発中の機能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1c8a7be6646c0035eaefed6d61d749c8469c8a4e
ms.sourcegitcommit: 119962948045079022aa48f968dde3e961d7cd0c
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031655"
---
# <a name="in-development-for-microsoft-intune---june-2019"></a>Microsoft Intune 用に開発中 - 2019 年 6 月

お客様による準備と計画を支援するため、このページには Intune の UI の更新と、開発中でまだリリースされていない機能がリストされています。 さらに

- お客様による変更前の対処が必要であると予測される場合は、補足の Office メッセージ センター投稿を公開します。
- 機能が運用環境でプレビューまたは一般公開としてリリースされると、機能の説明はこのページから[新機能ページ](whats-new.md)に移されます。
- このページと[新機能ページ](whats-new.md)は定期的に更新されます。 適宜確認してください。
- 戦略的成果物とタイムラインについては、[Microsoft 365 のロードマップ](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)を参照してください。

> [!Note]
> これらの項目には、将来のリリースで導入される Intune の機能に関する Microsoft の現在の予測が反映されています。 日付と個々の機能は変更されることがあります。 すべての開発中の項目について、このページに機能の説明があるわけではりません。

**RSS フィード**: ご自身のフィード リーダーに次の URL をコピーして貼り付けることで、このページの更新時に通知を受け取ることができます。`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune

<!-- ***********************************************-->
### <a name="app-management"></a>アプリ管理

#### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>デバイスのユーザーは、インストール済みまたはインストールしようとしたすべての管理対象アプリを表示できる <!-- 2352913 -->
Windows 用ポータル サイトに、ユーザーのデバイスにインストールされているすべてのマネージド アプリ (必須および使用可能の両方) が一覧表示されます。 ユーザーは、試行した、および保留中のアプリのインストールと、それらの現在の状態を表示することができるようになります。 組織でアプリが必須または使用可能とされていない場合、会社のアプリは全くインストールされていないというメッセージがユーザーに表示されます。 ユーザーはまた、インストールの状態でアプリを並べ替えまたはフィルタリングすることができます。

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>組織データへのリンクを許可するブラウザーを構成する <!-- 3145939 -->
Android および iOS デバイス上の Intune App Protection ポリシー (APP) を使用すると、組織の Web リンクを Intune Managed Browser または Microsoft Edge 以外の特定のブラウザーに転送できます。  アプリの詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」を参照してください。

#### <a name="installed-apps-page-on-the-company-portal-website-----4224326---"></a>ポータル サイト Web サイト上のインストール済みアプリ ページ  <!-- 4224326 -->
[ポータル サイト Web サイト](https://portal.manage.microsoft.com/)には、デバイスにインストールされているすべてのアプリをユーザーに表示する新しいページが含まれます。 この一覧には、その組織で使用できるアプリと必要なアプリの両方が含まれています。 このページから、ユーザーは自分のデバイス上のアプリのインストールと要件の状態を確認することができます。 ポータル サイト Web サイトの詳細については、「[Intune ポータル サイト Web サイトの使用](/intune-user-help/using-the-intune-company-portal-website)」と「[Microsoft Intune ポータル サイト アプリを構成する方法](company-portal-app.md)」を参照してください。

#### <a name="call-graph-api-read-operations-from-an-application-without-user-credentials----4655885---"></a>ユーザーの資格情報なしでアプリケーションから Graph API の読み取り操作を呼び出す <!-- 4655885 -->
アプリケーションから、ユーザー資格情報を使用せず、アプリ ID を使用して Intune Graph API 読み取り操作を呼び出すことができるようになります。 詳細については、「[ユーザーなしでアクセスを取得](https://docs.microsoft.com/graph/auth-v2-service)」を参照してください。

<!-- ***********************************************-->
### <a name="device-configuration"></a>デバイス構成


#### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>iOS 用の IKEv2 VPN プロファイルのサポート <!-- 1943438 -->
IKEv2 プロトコルを使用して、iOS ネイティブ VPN クライアント用の VPN プロファイルを作成できるようになります。 IKEv2 は、 **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > **プラットフォームに [iOS]** > プラットフォームの種類に **[VPN]** > **[設定]** の新しい接続の種類です。

これらの VPN プロファイルではネイティブ VPN クライアントを構成します。 そのため、VPN クライアント アプリはマネージド デバイスにインストールまたはプッシュされません。 この機能を使用するには、デバイスを Intune に登録する必要があります (MDM 登録)。

現在構成できる VPN 設定については、「[Microsoft Intune で iOS デバイスに対する VPN 設定を構成する](vpn-settings-ios.md)」を参照してください。

適用対象: iOS

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----20430240---"></a>macOS デバイスのカーネル拡張機能の設定を構成する <!-- 20430240 -->
macOS デバイスで、デバイス構成プロファイルを作成できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > プラットフォームに **[macOS]** を選択します)。 今後の更新プログラムには、デバイスのカーネル拡張機能を構成して使用することができる新しい設定のグループが追加される予定です。

適用対象: macOS 10.13.2 以降

#### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>キーワード検索のベースライン サポート  <!-- 3082036         -->
まもなく、セキュリティのベースライン プロファイルを作成または編集中、コンソールに表示される設定をフィルター処理するために "*検索*" を使用できるようになります。   

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Windows 10 デバイス構成プロファイルを作成するときは "適用規則" を使用する <!-- 2549910 -->
Windows 10 デバイス構成プロファイルを作成します ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Windows 10]** (プラットフォーム))。 **適用規則**を作成し、プロファイルが特定のエディションまたは特定のバージョンにのみ適用されるようにすることができます。 たとえば、いくつかの BitLocker 設定を有効にするプロファイルを作成します。 プロファイルを追加したら、適用規則を使用して Windows 10 Enterprise を実行しているデバイスにのみプロファイルを適用します。

適用対象: 
- Windows 10 以降

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002----"></a>Windows 10 デバイスのストアのアプリのみ設定に含まれるその他の構成オプション <!-- 2697002  -->

ユーザーが Windows アプリ ストアからのみアプリをインストールするように、Windows デバイス用のデバイス制限プロファイルを作成するときに **[Apps from the store only]\(ストアのアプリのみ\)** 設定を使用することがでます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > **プラットフォームに [Windows 10 以降]** > プロファイルの種類に **[デバイスの制限]** )。 今後の更新プログラムでは、この設定はより多くのオプションをサポートするように拡張される予定です。 

現在の設定を確認するには、「[Intune を使用して機能を許可または制限するように Windows 10 (以降) のデバイスを設定する](device-restrictions-windows-10.md#app-store)」を参照してください。

適用対象: Windows 10 以降

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>複数の Zebra モビリティ拡張機能デバイス プロファイルを 1 つのデバイス、同じユーザー グループ、または同じデバイス グループに展開する <!-- 4089955 -->
Intune では、デバイス構成プロファイルで Zebra モビリティ拡張機能 (MX) を使用して設定をカスタマイズすることや、Intune に組み込まれていない設定を追加することができます。 現在、1 つのデバイスに 1 つのプロファイルを展開できます。 今後の更新プログラムでは、複数のプロファイルを以下に展開できるようになります。

- 同じユーザー グループ
- 同じデバイス グループ
- 1 つのデバイス

「[Microsoft Intune で Zebra モビリティ拡張機能を備えた Zebra デバイスを使用および管理する](android-zebra-mx-overview.md)」には、Intune で MX を使用する方法が説明されています。

適用対象: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>iOS デバイス上の一部のキオスク設定は、[許可] の代わりに [ブロック] を使用して設定されています。 <!-- 4404075  -->
iOS デバイス上にデバイス制限プロファイルを作成した場合は ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > **プラットフォームに [iOS]** > プロファイルの種類に **[デバイスの制限]** > **[キオスク]** )、 **[自動ロック]** 、 **[着信音スイッチ]** 、 **[画面の回転]** 、 **[画面スリープ ボタン]** 、および **[音量ボタン]** を設定します。 

現在、これらの設定は **[許可]** (機能をブロックする) または **[未構成]** (機能を許可する) を使用して構成されています。 今後の更新プログラムでは、値は **[ブロック]** (機能をブロックする) または **[未構成]** (機能を許可する) になる予定です。

現在の設定を確認するには、[機能を許可または制限する iOS デバイスの設定](device-restrictions-ios.md)に関するページを参照してください。 

適用対象: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704----"></a>iOS デバイスのパスワード認証に Face ID を使用する <!-- 4490704  -->
iOS デバイス用のデバイス制限プロファイルを作成するときは、パスワードに指紋を使用できます。 今後の更新プログラムでは、指紋のパスワード設定でも顔認識が可能になる予定です ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > **プラットフォームに [iOS]** > **プロファイルの種類に [デバイスの制限]** > **[パスワード]** )。 その結果、次の設定が変更されています。

- **[指紋によるロック解除]** は **[Touch ID と Face ID のロック解除]** になりました。
- **[指紋の変更 (管理モードのみ)]** は **[Touch ID と Face ID の変更 (監視モードのみ)]** になりました。

Face ID は iOS 11.0 以降で使用できます。 現在の設定を確認するには、「[Intune を使用して機能を許可または制限するように iOS デバイスを設定する](device-restrictions-ios.md#password)」を参照してください。

適用対象: iOS

#### <a name="apps-feature-is-dependent-on-ratings-region-when-restricting-gaming-and-app-store-features-on-ios-devices----4593948----"></a>iOS デバイスでゲームやアプリ ストアの機能を制限している場合、アプリの機能は年齢区分の地域によって異なります <!-- 4593948  -->
iOS デバイスでは、ゲーム、アプリ ストア、およびドキュメントの表示に関連する機能を許可または制限できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > **プラットフォームに [iOS]** > プロファイルの種類に **[デバイスの制限]** > **[アプリ ストア、ドキュメント表示、ゲーム]** )。 米国などの年齢区分の地域を選択することもできます。 今後の更新プログラムでは、 **[アプリ]** 機能が **[年齢区分の地域]** の子に移動され、 **[年齢区分の地域]** に依存するようになります。

現在の設定を確認するには、「[Intune を使用して機能を許可または制限するように iOS デバイスを設定する](device-restrictions-ios.md#app-store-doc-viewing-gaming)」を参照してください。

適用対象: iOS

#### <a name="administrative-templates-for-group-policy---------3510695---"></a>グループ ポリシーの管理用テンプレート     <!--  3510695 -->
クラウド内のデバイスのセキュリティを向上するために、Intune を使用して Windows PC 用に選択したグループ ポリシー設定を構成することができる管理用テンプレートをリリースする予定です。  これらのテンプレートでは、Office、Windows、および OneDrive の最大 2,500 個の追加設定を提供するためにポリシー構成サービス プロバイダー (CSP) を使用します。

####  <a name="new-settings-for-the-windows-security-baseline-----3534649-4217151------------"></a>Windows セキュリティ ベースラインの新しい設定  <!-- 3534649, 4217151          -->
Windows セキュリティ ベースラインに新しい設定を追加しています。 最初の設定は、セキュア ブートが必要な仮想化ベースのセキュリティです。 2 つ目の設定では、画面がロックされているときに Windows アプリの音声によるアクティブ化を管理できます。

#### <a name="security-baselines-will-be-generally-available------3785395---------"></a>セキュリティ ベースラインは一般提供される予定  <!--  3785395       -->
セキュリティ ベースライン機能は間もなくプレビュー段階ではなくなり、一般提供される予定です。 

#### <a name="the-windows-security-baseline-template-will-be-generally-available-------3794072---------"></a>Windows セキュリティ ベースライン テンプレートは一般提供される予定   <!--  3794072       -->
Windows セキュリティ ベースライン テンプレートは間もなくプレビュー段階ではなくなり、一般提供される予定です。 プレビュー バージョンのテンプレートは廃止され、新しいテンプレートがリリースされる予定です。

<!-- ***********************************************-->
### <a name="device-management"></a>デバイス管理

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>セキュリティ グループ内のすべてのマネージド デバイスにスコープ タグを割り当てる <!-- 3173810 -->
現時点では、個々のデバイスの **[プロパティ]** ページに移動し、スコープ タグを選択することで、デバイスにスコープ タグを割り当てることができます。 今後の更新プログラムでは、スコープ タグをセキュリティ グループに割り当てられるようになります。また、セキュリティ グループ内のすべてのデバイスもそれらのスコープ タグに関連付けられるようになります。 これを行うには、 **[Intune]**  >  **[ロール]**  >  **[スコープ (タグ)]**  >  **[作成]**  >  **[スコープ (タグ)]** を選択し、スコープ タグを割り当てるグループを選択します。 これらのグループ内のすべてのデバイスにもスコープ タグが割り当てられます。 この機能で設定されたスコープ タグによって、現在のデバイス スコープ タグ フローで設定されたスコープ タグは上書きされる予定です (今後の更新プログラムでは、スコープ タグをデバイスに割り当てる現在のフローは読み取り専用になる予定です)。

#### <a name="see-the-security-patch-level-for-android-devices----4461911----"></a>Android デバイス用のセキュリティ パッチ レベルを確認する <!-- 4461911  -->
Android デバイス用のセキュリティ パッチ レベルを確認できるようになる予定です。 これを行うには、 **[Intune]**  >  **[デバイス]**  >  **[すべてのデバイス]** > デバイスを選択 > **[監視]**  >  **[ハードウェア]** を選択します。


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。


