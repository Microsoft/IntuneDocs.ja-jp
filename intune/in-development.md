---
title: 開発中 - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune の開発中の機能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 95eede7c62e728aa0dbade4478eb87f31c252558
ms.sourcegitcommit: a6775522df49d17a4125ccb31be395f2343bdae8
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2019
ms.locfileid: "68833555"
---
# <a name="in-development-for-microsoft-intune---august-2019"></a>Microsoft Intune 用に開発中 - 2019 年 8 月

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

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>アプリ管理

### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144---"></a>デバイス登録解除で iOS アプリのアンインストール動作を制御する <!-- 3504144 -->
管理者は、デバイスがユーザーまたはデバイスグループレベルで登録解除されたときに、デバイスでアプリを削除するか保持するかを管理できます。 

### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>ビジネス向け Microsoft Store アプリの分類 <!-- 3926922 -->
ビジネスアプリの Microsoft Store を分類できるようになります。 これを行うには **[Intune** > **クライアント**  > **アプリアプリ]を**選択し > [ビジネス向けアプリの Microsoft Store] > アプリを選択します。 **情報** > **カテゴリ。** ドロップダウンメニューで、カテゴリを割り当てます。
### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>組織アカウントのアプリ通知コンテンツを構成する <!-- 2576686 -->
Android および iOS デバイスの Intune アプリ保護ポリシー (アプリ) では、組織アカウントのアプリ通知コンテンツを制御できます。 この機能は、アプリケーションからのサポートを必要とし、すべてのアプリ対応アプリケーションで使用できるとは限りません。 アプリの詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」を参照してください。

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Android の仕事用プロファイルに使用できる Google Play アプリのレポート <!-- 3041956  -->
Android の仕事用プロファイル デバイスに使用できるアプリのインストールについては、アプリのインストール状態と managed Google Play アプリのインストール済みバージョンを確認できます。 詳細については、[アプリの保護ポリシーを監視する方法](app-protection-policies-monitor.md)、[Intune を使用した Android の仕事用プロファイル デバイスの管理](android-enterprise-overview.md)、および[マネージド Google Play アプリの種類](apps-add-android-for-work.md#managed-google-play-app-type)に関する記事を参照してください。

<!-- ***********************************************-->
## <a name="device-configuration"></a>デバイス構成

### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809----"></a>Ios 13.0 リリースでは、一部の教師なし iOS デバイスの制限が監視対象になります <!-- 4867809  -->
一部の設定は、iOS 13.0 リリース以降の監視対象デバイスに適用されます。 設定は次のとおりです。

- アプリ ストア、ドキュメント表示、ゲーム
  - アプリ ストア
  - ITunes、音楽、ポッドキャスト、またはニュースの明示的なコンテンツ
  - Game Center の友だちの追加
  - マルチプレイヤー ゲーム
- 組み込みアプリ
  - カメラ
    - FaceTime
  - Safari
    - オートフィル
- クラウドとストレージ
  - iCloud へのバックアップ
  - ICloud ドキュメントの同期をブロックする
  - iCloud キーチェーンの同期をブロックする

これらの設定が構成されていて、iOS 13.0 リリースより前の教師なしデバイスに割り当てられている場合、これらの教師なしデバイスには引き続き設定が適用されます。 また、デバイスが iOS 13.0 にアップグレードされた後も引き続き適用されます。 これらの制限は、バックアップおよび復元される教師なしデバイスでは削除されます。 

現在の設定を確認するには、「[Intune を使用して機能を許可または制限するように iOS デバイスを設定する](device-restrictions-ios.md)」を参照してください。

適用対象:  
- iOS 13.0 以降

### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709----"></a>IOS および macOS デバイスの機能を制限するための新しい設定と既存の設定の変更 <!-- 4867699 4867709  -->
IOS と macOS を実行しているデバイスの設定を制限するプロファイルを作成**できます**( >  **[デバイス構成**プロファイル >  **] [プロファイルの作成]**  > **iOS**または**macOS**for platform type >**デバイスの制限)** 。 次の機能が追加されます。

- **MacOS** >  **デバイスの** > 制限クラウド**およびストレージでは**、新しいハンドオフ**設定を使用して** ユーザーが1つの macOS デバイスで作業を開始できないようにし、別の macOS または iOS デバイスでの作業を続行します。
  現在の設定を確認するには、「[Intune を使用して機能を許可または制限するように macOS デバイスを設定する](device-restrictions-macos.md)」を参照してください。
- IOS **デバイスの** > **制限には、いくつかの変更があります。**
  - **[** 組み込みアプリ >  **で iPhone を検索する (監視モードのみ)]** : アプリの検索機能でこの機能をブロックする新しい設定です。 
  - **[** 自分の >  **友人を検索する (監視モードのみ)]** : アプリの検索機能でこの機能をブロックする新しい設定です。 
  - **Wi-fi**状態のワイヤレス > **変更 (監視モードのみ)** : ユーザーがデバイスで wi-fi をオンまたはオフにできないようにする新しい設定。
  - **キーボードと辞書** >  **のクイックパス (監視モードのみ)** : quickpath 機能をブロックする新しい設定。
  - **クラウドとストレージ**: **アクティビティの**継続は、 **ハンド**オフに名前が変更されました。

  現在の設定を確認するには、「[Intune を使用して機能を許可または制限するように iOS デバイスを設定する](device-restrictions-ios.md)」を参照してください。

適用対象:  
- macOS 10.15 以降
- iOS 13 以降

### <a name="control-the-apps-files-documents-and-folders-that-open-when-user-signs-in-to-macos-devices---3914202----"></a>ユーザーが macOS デバイスにサインインしたときに開くアプリ、ファイル、ドキュメント、およびフォルダーを制御する <!--3914202  -->
MacOS デバイスで機能を有効にして構成することが**できます**( >  **デバイス構成** >  **プロファイル**の [プロファイルの作成] > **macOS** for platform >**プロファイルの**種類のデバイス機能)。 

ユーザーが登録済みのデバイスにサインインしたときに開くアプリ、ファイル、ドキュメント、およびフォルダーを制御するための新しい [ログイン項目] 設定が追加されます。 

現在の設定を確認するには[、「Intune](macos-device-features-settings.md)の macOS デバイス機能設定」にアクセスしてください。

適用対象:  
- macOS

### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946----"></a>マルチアプリモードでの Android Enterprise 専用デバイスの新機能 <!-- 3755304 3041943 3041946  -->
Android エンタープライズ専用デバイスでは、キオスク形式のエクスペリエンスで機能と設定を制御することができます。 これを行うには **、[** デバイス > **構成** プロファイル >  **][プロファイル]**  >  **[AndroidEnterprise]** を選択します。プラットフォーム > **デバイス所有者のみの場合**、プロファイルの種類に関するデバイスの制限。

次の機能が追加されます。
- **専用デバイス** > **マルチアプリ**:仮想ホーム**ボタンを表示するには、デバイスにスワイプするか、画面上にフローティングして、ユーザーが移動できるようにします。**
- **専用デバイス** > **マルチアプリ**:**懐中電灯**アクセスを使用すると、ユーザーは懐中電灯を使用できます。 
- **専用デバイス** > :**マルチ**アプリ:**メディアボリューム**コントロールを使用すると、ユーザーはスライダーを使用してデバイスのメディアボリュームを制御できます。 
- **専用デバイス** > **マルチアプリ**: スクリーンセーバーを有効にし、カスタムイメージをアップロードし、スクリーンセーバーを表示するタイミングを制御します。

現在の設定を確認するには、[Intune を使用して Android エンタープライズ デバイスの機能を許可または制限する設定](device-restrictions-android-for-work.md#dedicated-device-settings)に関するページを参照してください。

適用対象:  
- Android Enterprise 専用デバイス

### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215----"></a>Android Enterprise の完全に管理されたデバイスの新しいアプリと構成プロファイル <!-- 3574215  -->
プロファイルを使用すると、Android Enterprise の完全に管理されたデバイスに VPN、電子メール、および Wi-fi 設定を適用する設定を構成できます。 次のことが可能になります。
- アプリプロファイルを使用して、Outlook、Gmail、および9の職場の電子メール設定を展開します。
- デバイス構成プロファイルを使用して、信頼されたルート証明書の設定を展開します。
- デバイス構成プロファイルを使用して、VPN と Wi-fi の設定を展開します。

ユーザーは、VPN、Wi-fi、および電子メールプロファイルのユーザー名とパスワードを使用して認証されます。 現在、証明書ベースの認証は使用できません。 

適用対象:  
- Android Enterprise のフル マネージド

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>iOS 用の IKEv2 VPN プロファイルのサポート <!-- 1943438 -->
IKEv2 プロトコルを使用して、iOS ネイティブ VPN クライアント用の VPN プロファイルを作成できるようになります。 IKEv2 は、 **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > **プラットフォームに [iOS]** > プラットフォームの種類に **[VPN]** > **[設定]** の新しい接続の種類です。

これらの VPN プロファイルではネイティブ VPN クライアントを構成します。 そのため、VPN クライアント アプリはマネージド デバイスにインストールまたはプッシュされません。 この機能を使用するには、デバイスを Intune に登録する必要があります (MDM 登録)。

現在構成できる VPN 設定については、「[Microsoft Intune で iOS デバイスに対する VPN 設定を構成する](vpn-settings-ios.md)」を参照してください。

適用対象: iOS

<!-- ***********************************************-->
## <a name="device-enrollment"></a>デバイスの登録

### <a name="skip-more-screens-in-setup-assistant---4877451---"></a>セットアップアシスタントで他の画面をスキップする <!--4877451 -->
Device Enrollment Program プロファイルを設定して、次のセットアップアシスタント画面をスキップできます。 
- 画面の表示時間
- タッチ ID の設定

これを行うには、 **[デバイス** >  **の登録** ** >  **] [Apple の登録]** [enrollment program トークン] **の順に選択し** > **トークンを選択し >**  >   **プロファイル>[** セットアップアシスタントのカスタマイズ]の**横にある [プロパティ] [編集] > プロファイルを選択します。**
セットアップアシスタントのカスタマイズの詳細について[は、「Apple の](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)登録プロファイルを作成する」を参照してください。

### <a name="android-enrollment-device-administrator-support----4869749----"></a>Android 登録デバイス管理者のサポート <!-- 4869749  -->
Android デバイス管理者の登録オプションは、android の**登録ページ (Intune** > **のデバイス登録** > **android) に追加されます。登録**)。 Android デバイス管理者は、すべてのテナントで既定で有効になります。  

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>IOS デバイスの場合は、ポータルサイトの [登録プロセスのプライバシー] 画面をカスタマイズします。 <!-- 4394993  -->
Markdown を使用すると、iOS の登録時にエンドユーザーに表示されるポータルサイトのプライバシー画面をカスタマイズできます。 具体的には、組織がデバイスで参照または実行できない項目の一覧をカスタマイズできます。

<!-- ***********************************************-->
## <a name="device-management"></a>デバイス管理

### <a name="build-number-included-on-android-device-hardware-page----4461910----"></a>Android デバイスハードウェアページに含まれるビルド番号 <!-- 4461910  -->
各 Android デバイスのハードウェアページに新しいエントリとして、デバイスのオペレーティングシステムのビルド番号が含まれます。

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>自動デバイスクリーンアップの時間制限を30日に設定する <!--4231059  -->
最後にサインインした後に、デバイスの自動クリーンアップ時間の制限を30日 (現在の制限である90日よりも短く) に設定することができます。 これを行うには、 **Intune** > **デバイス** >  **セットアップ** > **デバイスのクリーンアップルール**に関するページを参照してください。

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>ロールベースのアクセス制御

### <a name="default-scope-tag----3702875---"></a>既定のスコープタグ <!-- 3702875 -->
新しい組み込みの既定のスコープタグが使用できるようになります。 スコープタグをサポートするすべてのタグなし Intune オブジェクトが、既定のスコープタグに自動的に割り当てられます。 **既定**のスコープタグは、現在の管理エクスペリエンスと同等のものになるように、既存のすべてのロールの割り当てに追加されます。 管理者が既定のスコープタグを持つ Intune オブジェクトを表示しないようにするには、ロールの割り当てから既定のスコープタグを削除します。 この機能は、System Center Configuration Manager のセキュリティスコープ機能に似ています。

<!-- ***********************************************-->
## <a name="security"></a>セキュリティ

### <a name="import-and-export-security-baselines------3408610------------"></a>セキュリティベースラインのインポートとエクスポート    <!--3408610          -->  
ここでは、セキュリティベースラインをエクスポートおよびインポートする機能を追加しています。 この機能を使用すると、カスタマイズを行ったり、Intune 環境間で共有したりすることができます。

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。




