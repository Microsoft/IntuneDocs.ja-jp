---
title: Microsoft Intune の新機能 - Azure | Microsoft Docs
titlesuffix: ''
description: Intune Azure Portal の新機能を確認する
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/14/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: 41c5af504bb65a661e55d09d735a78df780deb84
ms.sourcegitcommit: 698af815f6de2c4f003f6da428bbfb0680daafa0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43092177"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune の新機能
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

週ごとにまとめた、Microsoft Intune の新機能をご覧ください。 [今後の変更](#whats-coming)、サービスに関する[重要なお知らせ](#notices)、[過去のリリース](whats-new-archive.md)に関する情報も確認できます。 いくつかの機能については、数週間にわたってロールアウトされ、一部のお客様は最初の週にご利用になれない可能性があります。

> [!Note]
> ハイブリッド モバイル デバイス管理 (MDM) での新機能については、[ハイブリッドの新機能に関するページ](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を確認してください。


<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->   


## <a name="week-of-august-27-2018"></a>2018 年 8 月 27 日の週

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>VPP デバイス ライセンスを使用して DEP 登録時にポータル サイトを事前プロビジョニングする <!-- 1608345 -->
Volume Purchase Program (VPP) デバイス ライセンスを使用して、Device Enrollment Program (DEP) 登録時にポータル サイトを事前プロビジョニングすることができます。 そのためには、[登録プロファイルを作成または編集する](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)ときに、ポータル サイトをインストールするために使用する VPP トークンを指定します。 トークンの期限が切れていないことと、ポータル サイト アプリの十分なライセンスがあることを確認してください。 トークンの期限が切れているか、ライセンスが不足している場合、Intune は代わりに App Store ポータル サイトをプッシュします (この場合、Apple ID の入力が求められます)。


## <a name="week-of-august-14-2018"></a>2018 年 8 月 14 日の週

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Apple Device Enrollment Program の macOS によるサポート <!-- 747651 -->
Intune は、Apple Device Enrollment Program (DEP) への macOS デバイスの登録をサポートするようになりました。 詳細については、「[Apple の Device Enrollment Program を使用して macOS デバイスを自動登録する](device-enrollment-program-enroll-macos.md)」を参照してください。

## <a name="week-of-july-23-2018"></a>2018 年 7 月 23 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>macOS の基幹業務 (LOB) アプリのサポート <!-- 1895847 -->
Microsoft Intune では、macOS LOB アプリを **[必須]** として、または **[Available with enrollment]\(登録して利用可能\)** として展開することができます。 エンド ユーザーは、macOS 用のポータル サイトまたは[ポータル サイト Web サイト](https://portal.manage.microsoft.com)を使用して、アプリを **[利用可能]** として展開してもらうことができます。

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>キオスク モードに対応する iOS 組み込みアプリのサポート <!-- 2051098 -->
ストア アプリおよび管理対象アプリに加えて、iOS デバイス上でキオスク モードで実行される組み込みアプリ (Safari など) を選択できるようになりました。

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Office 365 Pro Plus アプリの展開を編集する <!-- 2150145 -->
Microsoft Intune 管理者は、Office 365 Pro Plus アプリのデプロイを編集するための強化された機能を使用できます。 さらに、スイートのいずれかのプロパティを変更するのに、デプロイを削除しなくてもよくなりました。 Azure Portal で、**[Microsoft Intune]** > **[モバイル アプリ]** > **[アプリ]** の順に選びます。 アプリの一覧から、Office 365 Pro Plus スイートを選択します。  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>更新された Android 用 Intune アプリ SDK が使用可能 <!-- 2744271-->

Android P のリリースをサポートする Android 用 Intune アプリ SDK の更新バージョンが使用可能になりました。 Android 用 Intune SDK を使用しているアプリ開発者は、Intune アプリ SDK の更新バージョンをインストールして、Android P デバイス上でも Android アプリの Intune 機能が正常に動作するようにする必要があります。 このバージョンの Intune アプリ SDK には、SDK の更新を実行する組み込みのプラグインが用意されています。 統合されている既存のコードを書き直す必要はありません。 詳細については、[Android 用 Intune SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-android) に関するページをご覧ください。 Intune に対して古いバッジのスタイルを使用している場合は、ブリーフケース アイコンを使用することをお勧めします。 ブランド化について詳しくは、[この GitHub リポジトリ](https://github.com/msintuneappsdk/intune-app-partner-badge)をご覧ください。


### <a name="device-configuration"></a>デバイス構成

#### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>S/MIME を使用して暗号化し、ユーザーの複数のデバイスに署名する <!-- 1333642 -->
この更新プログラムには、新しくインポートされる証明書プロファイル (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]**、該当するプラットフォーム、**[PKCS のインポートされた証明書]** プロファイルの種類の順に選択) を使用する S/MIME メールの暗号化が含まれます。 Intune では、PFX 形式で証明書をインポートできます。 その後、Intune はその同じ証明書を、単一ユーザーによって登録された複数のデバイスに配信できます。 これには、次のものも含まれます。

- ネイティブ iOS メール プロファイルでは、PFX 形式でインポートされた証明書を使用する S/MIME 暗号化を有効にすることができます。
- Windows Phone 10 デバイス上のネイティブ メール アプリでは、自動的に S/MIME 証明書が使用されます。
- プライベート証明書は複数のプラットフォームに配信できます。 しかし、すべてのメール アプリで S/MIME がサポートされるわけではありません。
- 他のプラットフォームでは、S/MIME を有効にするようにメール アプリを手動で構成する必要がある場合があります。  
- S/MIME 暗号化をサポートするメール アプリでは、発行元の証明書ストアからの読み取りなど、MDM ではサポートできない方法で S/MIME メール暗号化のための証明書の検索を処理する場合があります。

サポート対象: Windows、Windows Phone 10、macOS、iOS、Android

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>macOS デバイスでファイアウォール設定を使ってデバイスのコンプライアンス ポリシーを作成する <!-- 1497640 -->
macOS の新しいコンプライアンス ポリシーを作成するとき (**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[プラットフォーム: macOS]** > **[システム セキュリティ]**)、**ファイアウォール**に関するいくつかの新しい設定を使用できます。 

- **[ファイアウォール]**: ご利用の環境における着信接続の処理方法を構成します。
- **[着信接続]**: DHCP、Bonjour、IPSec など、基本的なインターネット サービスに必要な接続を除き、すべての着信接続を **[ブロック]** します。 この設定は、すべての共有サービスもブロックします。
- **[ステルス モード]**: ステルス モードを **[有効]** にして、デバイスがプローブ要求に応答するのを防ぎます。 デバイスは引き続き、許可されているアプリに関する着信要求に応答します。

適用対象: macOS 10.12 以降

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Windows 10 以降用の新しい Wi-Fi デバイス構成プロファイル <!-- 1879077 -->
現時点では、XML ファイルを使用して、Wi-Fi プロファイルをインポートおよびエクスポートすることができます。 この更新プログラムを使用すると、他のプラットフォームの場合と同じように、Intune で直接 Wi-Fi デバイス構成プロファイルを作成できるようになります。

プロファイルを作成するには、**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[Windows 10 以降]** > **[Wi-Fi]** の順に開きます。 

Windows 10 以降に適用されます。

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998-eeready---"></a>[Kiosk - obsolete]\(キオスク - 古い) が灰色で表示され、変更できない <!-- 2149998 eeready -->
[キオスクの機能](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[Windows 10 以降]** > **[デバイスの制限]**) は使用されなくなり、[Windows 10 以降用のキオスク設定](kiosk-settings.md)に置き換えられます。 この更新プログラムを使用すると、**[Kiosk - Obsolete]\(キオスク - 古い)** 機能は灰色で表示され、ユーザー インターフェイスの変更や更新はできません。 

キオスク モードを有効にする場合は、[Windows 10 以降用のキオスクの設定](kiosk-settings.md)に関するページを参照してください。

Windows 10 以降、Windows Holographic for Business に適用されます

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>サード パーティ証明機関を使用する API <!-- 2184013 -->
この更新プログラムでは、Java API でサード パーティ証明機関を使用して、Intune と SCEP を統合できるようになります。 その後、ユーザーは SCEP 証明書をプロファイルに追加し、MDM を使用してデバイスに適用できます。

現時点では、Intune で [Active Directory 証明書サービスを使用する SCEP 要求](certificates-scep-configure.md)がサポートされています。

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>キオスク ブラウザーで [セッションの終了] ボタンの表示と非表示を切り替える <!-- 2455253 -->
キオスク ブラウザーに [セッションの終了] ボタンを表示するかどうかを構成できるようになりました。 コントロールは **[デバイス構成]** > **[キオスク (プレビュー)]** > **[キオスク Web ブラウザー]** で表示できます。 有効にした場合、ユーザーがボタンをクリックしたときに、アプリでセッションを終了するための構成が求められます。 確認すると、ブラウザーで閲覧データがすべてクリアされ、既定の URL に戻ります。

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>eSIM 携帯電話の構成プロファイルの作成 <!-- 2564077 -->
**[デバイス構成]** では、eSIM 携帯電話のプロファイルを作成することができます。 携帯電話会社によって提供される携帯電話のアクティブ化コードを含むファイルをインポートできます。 その後、これらのプロファイルを、Surface Pro LTE やその他の eSIM 対応デバイスなど、eSIM LTE を有効にした Windows 10 デバイスに展開することができます。

ご利用の[デバイスで eSIM プロファイルがサポートされている](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)かどうかを確認してください。

Windows 10 以降に適用されます。 




### <a name="device-enrollment"></a>デバイスの登録

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Samsung Knox Mobile Enrollment を使用して登録された Android デバイスを自動的に "企業" としてマークする。 <!-- 2404851 -->
既定で、Samsung Knox Mobile Enrollment を使用して登録された Android デバイスは、**[デバイスの所有権]** に**企業**としてマークされるようになりました。 Knox Mobile Enrollment を使用して登録する前に、IMEI やシリアル番号を使って企業のデバイスを手動で特定する必要はありません。

### <a name="device-management"></a>デバイス管理

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>デバイス ブレードでのデバイスの一括削除 <!-- 1793693 -->

[デバイス] ブレードでは、一度に複数のデバイスを削除できるようになりました。 **[デバイス]** > **[すべてのデバイス]**、削除するデバイス、**[削除]** の順に選択します。 削除できないデバイスについては、アラートが表示されます。

## <a name="week-of-july-16-2018"></a>2018 年 7 月 16 日の週  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Windows 用ポータル サイト アプリ内での同期の機会の増加  
Windows 用ポータル サイト アプリでは、Windows タスク バーと [スタート] メニューから直接同期を開始できるようになりました。 この機能は、唯一のタスクがデバイスを同期して、企業リソースへのアクセスを取得することで場合に特に便利です。 この新しい機能にアクセスするには、ご利用のタスク バーまたは [スタート] メニューに固定されているポータル サイト アイコンを右クリックします。 メニュー オプション (ジャンプ リストとも呼ばれる) で、**[Sync this device]\(このデバイスを同期\)** を選択します。 ポータル サイトが開いて、**[設定]** ページが表示され、同期が開始されます。新しい機能については、[UI の新機能](whats-new-app-ui.md)に関するページを参照してください。   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Windows 用ポータル サイト アプリでの新しい参照エクスペリエンス  

Windows 用ポータル サイト アプリでアプリを参照または検索するときに、既存の **[タイル]** ビューと新しく追加された **[詳細]** ビューを切り替えることができるようになりました。 新しいビューには、名前、発行元、発行日、インストール状態などのアプリケーションの詳細が一覧表示されます。  

**[アプリ]** ページの **[インストール済み]** ビューでは、完了済みと進行中のアプリのインストールに関する詳細を確認できます。 新しいビューの外観を確認するには、[UI の新機能](whats-new-app-ui.md)を参照してください。  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>デバイス登録マネージャー向けのポータル サイト アプリの操作性の改善  
デバイス登録マネージャー (DEM) が Windows 用ポータル サイト アプリにサインインすると、アプリには DEM の現在 (実行中のデバイス) のみが一覧表示されるようになります。 この改善により、DEM に登録されたデバイスをすべて表示しようとしたときに以前に発生していたタイムアウトが削減されます。  


## <a name="week-of-july-9-2018"></a>2018 年 7 月 9 日の週

### <a name="app-management"></a>アプリ管理

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>未承認のデバイス ベンダーとモデルに基づくアプリのアクセスのブロック <!-- 1425689 ! -->
Intune の IT 管理者は、Intune App Protection ポリシーによって、Android 製造元や iOS モデルの指定された一覧を適用できます。 IT 管理者は、Android ポリシーの製造元と iOS ポリシーのデバイス モデルのセミコロン区切り一覧を提供できます。 Intune App Protection ポリシーは、Android および iOS 専用です。 この指定されたリストでは 2 つの個別操作を実行できます。
- 指定されていないデバイスでのアプリ アクセスからブロック。
- または、指定されていないデバイスでの企業データの選択的ワイプ。 

ユーザーは、ポリシーによる要件が満たされない場合、対象となるアプリケーションにアクセスすることができません。 設定に基づいて、ユーザーは、ブロックされるか、アプリ内の企業データを選択的にワイプされます。 iOS デバイス上でこの機能を利用するには、対象のアプリケーションに適用するこの機能の Intune アプリ SDK を統合するアプリケーション (WXP、Outlook、Managed Browser、Yammer など) の参加が必要となります。 この統合は、ローリング方式で行われ、特定のアプリケーション チームによって異なります。 Android でこの機能を利用するには、最新の Intune ポータル サイトが必要です。 

エンド ユーザー デバイスの Intune クライアントは、アプリケーション保護ポリシーに対して Intune ブレードで指定されている文字列の単純一致に基づいてアクションを実行します。 これは、デバイスを報告する値に完全に依存します。 そのため、IT 管理者には、意図した動作が正確であることを確認することをお勧めします。 これは、小さなユーザー グループを対象に、さまざまなデバイス製造元とモデルに基づいてこの設定をテストすることによって実現できます。 Microsoft Intune でアプリ保護ポリシーを表示および追加するには、**[Mobile Apps]** > **[アプリ保護ポリシー]** を選びます。 アプリ保護ポリシーの詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」および「[Intune でアプリ保護ポリシーのアクセス アクションを利用し、データを選択的にワイプする](app-protection-policies-access-actions.md)」を参照してください。

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>macOS ポータル サイトのプレリリース ビルドへのアクセス <!-- 1734766 -->
Microsoft AutoUpdate を使用すれば、Insider Program に参加することにより、早期にビルドを受け取るためにサインアップできます。 サインアップすると、エンド ユーザーが使用できるようになる前に更新されたポータル サイトを使用できます。 詳細については、[Microsoft Intune に関するブログ](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/) を参照してください。

## <a name="week-of-july-2-2018"></a>2018 年 7 月 2 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>デバイスごとに iOS アプリ構成の状態を監視する <!-- 880037 -->
Microsoft Intune 管理者は、各マネージド デバイスの iOS アプリ構成状態を監視できます。 Azure Portal の **[Microsoft Intune]** から、**[デバイス]** > **[すべてのデバイス]** の順に選びます。 管理対象デバイスの一覧から、デバイスのブレードを表示する特定のデバイスを選びます。 デバイスのブレードで、**[アプリの構成]** を選びます。

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>アプリ保護ポリシーのアクションにアクセスする <!-- 1483510 -->
非準拠デバイスを明示的にワイプ、ブロック、または警告するようアプリ保護ポリシーを構成することができます。 "*ワイプ*" アクションによって、デバイスから会社の企業データが削除されます。 ワイプが発生した場合、デバイスのユーザーにはワイプの理由と修復手順の両方が通知されます。 最低 OS バージョンなどの一部の設定については、ブロックとワイプなど、複数のアクションを適用できます。 これらのアクションは、アプリが起動されるとトリガーされるので注意してください。

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>組織のアプリ データの選択的ワイプ <!-- 1507030 -->
管理者は、アプリケーション保護ポリシー (APP) アクセス設定の条件が満たされないときの新しいアクションとして、組織のデータの選択的ワイプを構成できるようになりました。  この機能を使うと、管理者は事前に構成した条件に基づいて、アプリケーションから組織の機密データを自動的に保護したり削除したりできます。

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>VPP を通じて購入した iOS アプリの取り消し <!-- 1777384 -->
Microsoft Intune 管理者は、ボリューム購入プログラム (VPP) で購入した iOS アプリのうち選択したもののライセンスをすべて取り消すことができます。 ユーザー ライセンスされたアプリがユーザーに割り当てられなくなった場合、該当するユーザーに通知することができます。 アプリのライセンスを取り消しても、関連する VPP アプリがデバイスからアンインストールされるわけではありません。 VPP アプリをアンインストールするには、割り当てアクションを **[アンインストール]** に変更する必要があります。 回収されたライセンスの数は、Intune の **[アプリ]** ワークロードの **[ライセンスされたアプリ]** ノードに反映されます。 iOS VPP アプリの詳細については、「[Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法](vpp-apps-ios.md)」をご覧ください。

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>ポータル サイト アプリの非準拠メッセージの更新 <!-- 1832222 -->
デバイスが準拠していない場合にそのデバイスのユーザーに表示されるメッセージが変更されました。 メッセージの元の意味は変わりませんが、専門用語を減らして、よりわかりやすくするために更新されました。 また、ドキュメントと修復手順へのリンクが最新の状態を保つために更新されました。
以下の更新前と後のテキストは、表示されるメッセージングの改善の一例です。
- **前**: *このデバイスは、IT 管理者によって要求された指定の期間に Intune サービスに接続していません。この問題を解決するためには、デバイスでポータル サイト アプリを開いて [コンプライアンスの確認] ボタンをクリックしてください。*
- **後**: *デバイスはしばらくの間、組織でチェックインされていません。接続を再確立するには、デバイスでポータル サイト アプリを開き、デバイスの [設定の確認] をタップします。*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>iOS VPP アプリのライセンスを取り消す <!-- 1863797 -->
管理者は、ユーザーまたはデバイスに割り当てられている iOS VPP アプリのライセンスを回収することができます。 iOS VPP アプリをアンインストールしても、アプリのライセンスを回収できます。 アプリをアンインストールする前に、アプリの対象となっているグループからユーザーまたはデバイスを削除する必要があります。 グループからユーザーまたはデバイスを削除することで、アプリの再インストールが回避されます。 これらの手順が完了したら、別のユーザーまたはデバイスにアプリ ライセンスを割り当てることができます。 iOS VPP アプリのライセンスの詳細については、「[Microsoft Intune での iOS のボリューム購入アプリの管理](vpp-apps-ios.md)」をご覧ください。

### <a name="device-configuration"></a>デバイス構成

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>[職場または学校にアクセスする] 設定を用いたデバイス カテゴリの選択<!-- 1058963 eenotready --> 
[デバイス グループ マッピング](https://docs.microsoft.com/en-us/intune/device-group-mapping)を有効にした場合、**[設定]** > **[アカウント]** > **[職場または学校にアクセスする]** の **[接続]** から登録後、または Windows 10 のユーザーはデバイス カテゴリの選択を求められるようになります。 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>電子メール プロファイルのアカウント ユーザー名として sAMAccountName を使用する <!-- 1500307 -->
Android、iOS、および Windows 10 用の電子メール プロファイルのアカウント ユーザー名として、オンプレミスの **sAMAccountName** を使うことができます。 また、Azure Active Directory (Azure AD) の `domain` または `ntdomain` 属性から、ドメインを取得できます。 または、カスタムの静的ドメインを入力します。

この機能を使うには、オンプレミスの Active Directory 環境から Azure AD に `sAMAccountName` 属性を同期する必要があります。

[Android](email-settings-android.md)、[iOS](email-settings-ios.md)、[Windows 10 以降](email-settings-windows-10.md)に適用される

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>競合しているデバイス構成プロファイルの確認 <!-- 1556983 -->
**[デバイス構成]** には、既存のプロファイルのリストが表示されます。 今回の更新プログラムでは、競合しているプロファイルに関する詳細を示す新しい列が追加されます。 競合する行を選択することで、競合しているプロファイルと設定を確認できます。 

詳細については、[構成プロファイルの管理](device-profile-monitor.md#view-conflicts)に関するページを参照してください。

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>デバイスのポリシー準拠でのデバイスの新しい状態 <!-- 2308882 -->
**[デバイスのポリシー準拠]** > **[ポリシー]**、該当するポリシー、**[概要]** の順に選択すると、次の新しい状態が追加されます。
- 成功
- エラー
- 競合
- 保留中
- 適用不可。異なるプラットフォームのデバイス数を示すイメージも表示されます。 たとえば、iOS プロファイルを見ている場合、新しいタイルでは、そのプロファイルに割り当てられている iOS 以外のデバイスの数も示されます。 [デバイス コンプライアンス ポリシー](compliance-policy-monitor.md#view-status-of-device-policies)に関するポリシーを参照してください。

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>デバイスのコンプライアンスはサード パーティのウイルス対策ソリューションをサポートする <!-- 2325484 -->
デバイス コンプライアンス ポリシーを作成するとき (**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[プラットフォーム: Windows 10 以降]** > **[設定]** > **[システム セキュリティ]**)、新しい **[[デバイスのセキュリティ]](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)** オプションがあります。 
- **[ウイルス対策]**: **[必要]** に設定すると、Windows Security Center に登録されている Symantec や Windows Defender などのウイルス対策ソリューションを使って、コンプライアンスを確認できます。 
- **[スパイウェア対策]**: **[必要]** に設定すると、Windows Security Center に登録されている Symantec や Windows Defender などのスパイウェア対策ソリューションを使って、コンプライアンスを確認できます。 

適用対象: Windows 10 以降 

### <a name="device-enrollment"></a>デバイスの登録

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>登録プログラム トークンのリスト内にあるプロファイルを持たないデバイスを示す列 <!-- 1853904 -->
登録プログラムのトークン リストには、プロファイルが割り当てられていないデバイスの数を示す新しい列があります。 この列は、管理者が、そのようなデバイスをユーザーに渡す前に、プロファイルを割り当てるのに役立ちます。 新しい列を参照するには、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** の順に選択します。

### <a name="device-management"></a>デバイス管理

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Android for Work および Play for Work の Google 名の変更 <!--842873 -->
Intune では、Google ブランドの変更を反映するように "Android for Work" の用語が更新されました。 "Android for Work" および "Play for Work" という用語は使われなくなりました。 コンテキストに応じて異なる用語が使われます。
- "Android エンタープライズ" は、最新の Android 管理スタック全体を指します。
- "Work profile" または "Profile Owner" は、作業プロファイルで管理されている BYOD デバイスを指します。
- "Managed Google Play" は、Google アプリ ストアを指します。

#### <a name="rules-for-removing-devices----1609459---"></a>デバイス削除のルール <!-- 1609459 -->
設定した日数の間チェックインしていないデバイスを自動的に削除する新しいルールを使用できます。 新しいルールを表示するには、**[Intune]** ウィンドウ、**[デバイス]**、**[デバイスのクリーンアップ ルール]** の順に選択します。

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>Android デバイスの会社所有、単一使用のサポート <!-- 1630973 -->

Intune は、高度に管理されてロック ダウンされた、キオスク スタイルの Android デバイスをサポートするようになりました。 これにより、管理者は、デバイスの使用を 1 つのアプリまたはアプリの小さなセットにさらにロックダウンし、ユーザーが他のアプリを有効にしたり、デバイスで他の操作を実行したりすることを禁止できます。 Android キオスクを設定するには、Intune > **[デバイスの登録]** > **[Android の登録]** > **[Kiosk and task device enrollments]\(キオスクおよびタスク デバイス登録\)** の順に進みます。 詳細については、[Android エンタープライズ キオスク デバイスの登録の設定](android-kiosk-enroll.md)に関するページを参照してください。

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>アップロードされた重複する業務用デバイス ID の行ごとのレビュー <!-- 2203794-->
業務用 ID をアップロードすると、重複の一覧が提供され、既存の情報を置き換えるか、保持することができるようになりました。 **[デバイスの登録]** > **[業務用デバイスの ID]** > **[ID の追加]** を選ぶと、重複がある場合はレポートが表示されます。 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>業務用デバイスの ID を手動で追加する <!-- 2203803 -->
業務用デバイスの ID を手動で追加できるようになりました。 **[デバイスの登録]** > **[業務用デバイスの ID]** > **[追加]** の順に選びます。 

## <a name="week-of-june-25-2018"></a>2018 年 6 月 25 日の週

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo - 新しい Mobile Threat Defense パートナー <!-- 1169249 -->

Microsoft Intune に統合されたモバイル脅威保護ソリューションである Pradeo によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

## <a name="week-of-june-18-2018"></a>2018 年 6 月 18 日の週

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Edge モバイルでの Intune アプリ保護ポリシーのサポート <!-- 1817882 -->

モバイル デバイス向けの Microsoft Edge ブラウザーで、Intune で定義されるアプリ保護ポリシーがサポートされるようになりました。

## <a name="week-of-june-11-2018"></a>2018 年 6 月 11 日の週

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>NDES 証明書コネクタで FIPS モードを使用する<!-- 1333688 -->
Federal Information Processing Standard (FIPS) モードが有効な NDES 証明書コネクタをコンピューターにインストールすると、証明書の発行や無効化が期待どおりに動作しません。 この更新プログラムでは、NDES 証明書コネクタに FIPS のサポートが含まれています。 

この更新プログラムには、次も含まれています。

- NDES 証明書コネクタには、Windows Server 2016 と Windows Server 2012 R2 に自動的に含まれる .NET 4.5 Framework が必要です。 これまでは、最小で .NET 3.5 Framework バージョンが必須でした。
- NDES 証明書コネクタには、TLS 1.2 のサポートが含まれています。 したがって、NDES 証明書コネクタがインストールされているサーバーが TLS 1.2 をサポートする場合、TLS 1.2 が使用されます。 サーバーが TLS 1.2 をサポートしない場合、TLS 1.1 が使用されます。 現在、デバイスとサーバー間の認証には、TLS 1.1 が使用されています。

詳細については、[SCEP 証明書の構成と使用](certificates-scep-configure.md)と、[PKCS 証明書の構成と使用](certficates-pfx-configure.md)に関するページを参照してください。

## <a name="week-of-june-4-2018"></a>2018 年 6 月 4 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>キオスク モードのビジネス向け Microsoft Store アプリの関連付けられたアプリ ユーザー モデル ID (AUMID) を取得する <!-- 1560077 ! -->
Intune で、ビジネス向け Microsoft Store (WSfB) アプリのアプリ ユーザー モデル ID (AUMID) を取得して、キオスク プロファイルの構成を改善できるようになりました。

ビジネス向け Microsoft Store アプリについて詳しくは、「[ビジネス向け Microsoft Store からのアプリの管理](windows-store-for-business.md)」をご覧ください。

#### <a name="new-company-portal-branding-page----1916370---"></a>新しいポータル サイトのブランド化ページ <!-- 1916370 -->
ポータル サイトのブランド化ページには、新しいレイアウト、メッセージ、ヒントがあります。


### <a name="device-configuration"></a>デバイス構成

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Palo Alto Networks GlobalProtect VPN プロファイルのサポート <!-- 1333680 eeready ! -->
今回の更新で、Intune での VPN プロファイルの VPN 接続の種類として、Palo Alto Networks GlobalProtect を選択できるようになりました (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[プロファイルの種類]** > **[VPN]**)。 このリリースでは、次のプラットフォームがサポートされます。 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>ローカル デバイス セキュリティ オプションの設定への追加 <!-- 1403702 -->
Windows 10 デバイスに対して追加のローカル デバイス セキュリティ オプションの設定を構成できるようになりました。 追加設定を利用できるのは、Microsoft ネットワーク クライアント、Microsoft ネットワーク サーバー、ネットワーク アクセスとセキュリティ、および対話型ログオンなどに関する部分です。 これらの設定は、Windows 10 デバイスの構成ポリシーを作成するときに、[Endpoint Protection] カテゴリに表示されます。

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Windows 10 デバイスでキオスク モードを有効にする <!-- 1560072 ! -->
Windows 10 デバイスでは、構成プロファイルを作成して、キオスク モードを有効にすることができます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[Windows 10]** > **[デバイスの制限]** > **[キオスク]**)。 この更新では、**[キオスク (プレビュー)]** の設定の名前が **[キオスク (古い)]** に変更されています。 **[キオスク (古い)]** は使用を推奨されませんが、7 月の更新までは機能し続けます。 **[キオスク (古い)]** は新しい **[キオスク]** プロファイルの種類に置き換えられ (**[プロファイルの作成]** > **[Windows 10]** > **[キオスク (プレビュー)]**)、Windows 10 RS4 以降でキオスクを構成する設定が含まれます。

Windows 10 以降に適用されます。

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>デバイス プロファイルのグラフィカル ユーザー グラフが戻った <!-- 2160133 -->
デバイス プロファイルのグラフィカルなグラフに表示される数値カウントの向上で (**[デバイス構成]** > **[プロファイル]** > 既存のプロファイルを選択 > **[概要]**)、グラフィカルなユーザー グラフが一時的に削除されました。

この更新では、グラフィカル ユーザー グラフが元に戻り、Azure portal に表示されます。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118-wnready---"></a>ユーザー認証なしの Windows Autopilot 登録のサポート <!-- 1165118 wnready -->
Intune では、ユーザー認証なしの Windows Autopilot 登録がサポートされるようになりました。 これは Windows Autopilot Deployment プロファイルの新しいオプションであり、"Autopilot Deployment モード" が "自己配置" に設定されます。  デバイスでは Windows 10 Insider プレビュー ビルド 17672 以降を実行しており、この種類の登録を正常に完了させるために TPM 2.0 チップがある必要があります。 ユーザー認証は不要であるため、このオプションを割り当てる必要があるのは、物理的に制御できるデバイスのみとなります。

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766-eeready---"></a>Autopilot の OOBE を構成するときの新しい言語/リージョンの設定 <!-- 1821766 eeready -->
Out of Box Experience (OOBE) の間に、Autopilot プロファイルの言語とリージョンを設定する、新しい構成設定を使用できます。 新しい設定を表示するには、**[デバイスの登録]** > **[Windows の登録]** > **[Deployment profiles]\(展開プロファイル\)** > **[プロファイルの作成]** > **[配置モード]** = **[Self-deploying]\(自己配置\)** > **[既定値が構成済み]** の順に選択します。

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>デバイス キーボードを構成するための新しい設定 <!-- 1821768 -->
Out of Box Experience (OOBE) の間に、Autopilot プロファイルのキーボードを構成する新しい設定を使用できます。 新しい設定を表示するには、**[デバイスの登録]** > **[Windows の登録]** > **[Deployment profiles]\(展開プロファイル\)** > **[プロファイルの作成]** > **[配置モード]** = **[Self-deploying]\(自己配置\)** > **[既定値が構成済み]** の順に選択します。

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Autopilot プロファイルの対象がグループに移動 <!-- 1877935 -->
AutoPilot 展開プロファイルは AutoPilot デバイスを含む Azure AD のグループに割り当てることができます。

### <a name="device-management"></a>デバイス管理

#### <a name="set-compliance-by-device-location----851881----"></a>デバイスの場所によるコンプライアンスの設定 <!-- 851881 ! -->
状況によっては、ネットワーク接続で定義される特定の場所に、企業リソースへのアクセスを制限することが必要な場合あります。 デバイスの IP アドレスに基づき、コンプライアンス ポリシーを作成できるようになりました (**[デバイスのポリシー準拠]** > **[場所]**)。 デバイスが IP 範囲外に移動した場合、デバイスは会社のリソースにアクセスできません。

適用対象: Android デバイス 6.0 以降 (ポータル サイト アプリ更新済み)

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Windows 10 Enterprise RS4 Autopilot デバイスでのコンシューマー アプリおよびエクスペリエンスの禁止<!-- 1621980 -->
Windows 10 Enterprise RS4 Autopilot デバイスへのコンシューマー アプリおよびエクスペリエンスのインストールを禁止することができます。 この機能を表示するには、**[Intune]** > **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[プラットフォーム]** = **[Windows 10 or later]\(Windows 10 以降\)** > **[プロファイルの種類]** = **[デバイスの制限]** > **[構成]** > **[Windows スポットライト]** > **[コンシューマー向けの機能]** の順に移動します。 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948-eeready---"></a>Windows 10 ソフトウェア更新プログラムの最新のものをアンインストールする <!-- 1732948 eeready -->
Windows 10 コンピューターで重大な問題が見つかった場合は、最新の機能更新プログラムまたは最新の品質更新プログラムをアンインストール (ロールバック) できます。 機能更新プログラムまたは品質更新プログラムをアンインストールできるのは、デバイスが存在するサービス チャネルの場合のみです。 アンインストールすると、Windows 10 コンピューター上の以前の更新プログラムを復元するためのポリシーがトリガーされます。 機能更新プログラムの場合、最新バージョンのアンインストールを適用できる期間を 2 日から 60 日間で制限できます。 ソフトウェア更新プログラムのアンインストール オプションを設定するには、Azure Portal 内の **[Microsoft Intune]** ブレードで **[ソフトウェア更新プログラム]** を選択します。 次に、**[ソフトウェア更新プログラム]** ブレードで **[Windows 10 更新プログラムのリング]** を選択します。 これで、**[概要]** セクションから **[アンインストール]** オプションを選択できます。

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>すべてのデバイスで IMEI およびシリアル番号を検索する <!-- 1793685 -->
[すべてのデバイス] ブレードで IMEI およびシリアル番号を検索できるようになりました (電子メール、UPN、デバイス名、管理名は引き続き使用できます)。 Intune で、**[デバイス]** > **[すべてのデバイス]** の順に選択し、検索ボックスに検索語句を入力します。

#### <a name="management-name-field-will-be-editable----1875989---"></a>管理名フィールドが編集可能になる <!-- 1875989 -->
デバイスの **[プロパティ]** ブレードで、管理名フィールドを編集できるようになりました。 このフィールドを編集するには、**[デバイス]** > **[すべてのデバイス]** > デバイスを選択 > **[プロパティ]** の順に選びます。 管理名フィールドを使って、デバイスを一意に識別できます。

#### <a name="new-all-devices-filter-device-category----1878520---"></a>新しいすべてのデバイス フィルター: デバイスのカテゴリ <!-- 1878520 -->
デバイスのカテゴリごとに **[すべてのデバイス]** リストをフィルター処理できるようになりました。 これを行うには、**[デバイス]** > **[すべてのデバイス]** > **[フィルター]** > **[デバイスのカテゴリ]** の順に選択します。

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>TeamViewer を使用して iOS デバイスと MacOS デバイスの画面を共有する <!-- 1985547 -->
管理者は [TeamViewer](device-profile-android-teamviewer.md) に接続し、iOS および macOS デバイスとの画面共有セッションを開始できるようになりました。 iPhone、iPad、macOS ユーザーは、他のデスクトップ デバイスまたはモバイル デバイスと画面をライブで共有できます。 

#### <a name="multiple-exchange-connector-support----2070451---"></a>複数の Exchange Connector のサポート <!-- 2070451 -->
テナントごとの Microsoft Intune Exchange Connector の数が 1 個だけという制限がなくなりました。 Intune で複数の Exchange Connector がサポートされ、複数のオンプレミス Exchange の組織で Intune の条件付きアクセスを設定できるようになりました。

Intune のオンプレミス Exchange Connector を使うと、デバイスが Intune に登録されているかどうか、およびデバイスが Intune のデバイス コンプライアンス ポリシーに準拠しているかどうかに基づいて、お使いのオンプレミスの Exchange メールボックスに対するデバイス アクセスを管理できます。 コネクタを設定するには、Azure Portal から Intune のオンプレミス Exchange Connector をダウンロードして、Exchange の組織内のサーバーにインストールします。 Microsoft Intune ダッシュ ボードで **[オンプレミス アクセス]** を選択し、**[セットアップ]** で **[Exchange ActiveSync のコネクタ]** を選択します。 Exchange のオンプレミス コネクタをダウンロードし、Exchange の組織内のサーバーにインストールします。 テナントごとに 1 個という Exchange Connector の制限がなくなったので、他に Exchange の組織がある場合は、他の各 Exchange の組織にも同じ手順でコネクタをダウンロードしてインストールできます。

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>新しいデバイス ハードウェアの詳細: CCID <!-- 2156657 -->
CCID (Chip Card Interface Device) 情報がデバイスごとに含まれるようになりました。 これを表示するには、**[デバイス]** > **[すべてのデバイス]** の順に選択します。次に、該当するデバイス、**[ハードウェア]** の順に選び、**[ネットワークの詳細]** の下を確認します。

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>スコープ グループとしてすべてのユーザーとすべてのデバイスを割り当てる <!-- 2196803 -->
スコープ グループ内のすべてのユーザー、すべてのデバイス、およびすべてのユーザーとすべてのデバイスを割り当てられるようになりました。 これを行うには、**[Intune の役割]** > **[すべてのロール]** > **[Policy and profile manager]\(ポリシーとプロファイル マネージャー\)** > **[割り当て]** の順に選び、割り当てを選んで、**[スコープ (グループ)]** を選びます。

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806-wnready--"></a>iOS および macOS デバイスの UDID 情報が含まれるようになりました <!-- 2219806 wnready-->
iOS および macOS デバイスの UDID (一意のデバイス識別子) を表示するには、**[デバイス]** > **[すべてのデバイス]** の順に選択します。次に、該当するデバイス、**[ハードウェア]** の順に選びます。 UDID は会社のデバイスでのみ利用できます (**[デバイス]** > **[すべてのデバイス]**、該当するデバイス、**[プロパティ]** > **[デバイスの所有権]** の順に選択して設定した場合)。

### <a name="intune-apps"></a>Intune アプリ

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>アプリのインストールのトラブルシューティングの向上 <!-- 928990 -->
Microsoft Intune の MDM で管理されたデバイスでは、アプリのインストールが失敗することがあります。 アプリのインストールが失敗した場合、失敗の理由を理解したり、問題をトラブルシューティングするのが難しい場合があります。 アプリ トラブルシューティング機能のパブリック プレビューが提供されています。 各デバイスの下に **[管理対象アプリ]** という新しいノードがあります。 これには、Intune MDM 経由で配布されたアプリが表示されます。 ノード内では、アプリのインストール状態が一覧表示されます。 個々のアプリを選ぶと、その特定のアプリのトラブルシューティング ビューが表示されます。 トラブルシューティング ビューでは、アプリが作成、変更、ターゲット指定、デバイス配布されたときなど、アプリのエンド ツー エンドのライフサイクルが表示されます。 さらに、アプリのインストールが成功しなかった場合は、エラー コードとエラーの原因に関する便利なメッセージが表示されます。 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Intune アプリ保護ポリシーと Microsoft Edge <!-- 1818968 -->
モバイル デバイス (iOS および Android) 向けの Microsoft Edge ブラウザーで、Microsoft Intune アプリ保護ポリシーがサポートされるようになりました。 Microsoft Edge アプリケーションで企業の Azure AD アカウントを使用してサインインした iOS および Android デバイスのユーザーは、Intune によって保護されます。 iOS デバイスでは、**Web コンテンツの管理対象ブラウザーを必要とする**ポリシーにより、ユーザーは Microsoft Edge が管理されている場合にその Microsoft Edge でリンクを開くことができます。

## <a name="week-of-may-14-2018"></a>2018 年 5 月 14 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>ポリシー、アプリ、証明書、およびネットワーク プロファイルのインストールを必要にする <!-- 1553555 -->

管理者は、AutoPilot デバイスのプロビジョニングの間、Intune がポリシー、アプリ、証明書、ネットワーク プロファイルをインストールするまで、エンド ユーザーによる Windows 10 RS4 デスクトップへのアクセスをブロックすることができます。 詳細については、「[登録ステータス ページを設定する](windows-enrollment-status.md)」を参照してください。

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>アプリ保護ポリシーの構成 <!-- 2144597 Part 2 -->

Azure portal では、Intune App Protection サービス ブレードに移動する代わりに、Intune に移動するようになりました。 Intune 内のアプリ保護ポリシーのための場所は 1 つだけになりました。 すべてのアプリ保護ポリシーが Intune の**アプリ保護ポリシー**の **[モバイル アプリ]** ブレードに置かれていることに注意してください。 この統合は、クラウド管理の簡素化に役立ちます。 ただし、すべてのアプリ保護ポリシーが既に Intune にあり、以前に構成した任意のポリシーを変更することができます。 Intune アプリ ポリシー保護 (APP) および条件付きアクセス (CA) ポリシーは現在、**[条件付きアクセス]** の下にあります。[条件付きアクセス] は、**[Microsoft Intune]** ブレードの **[管理]** セクション、または **[Azure Active Directory]** ブレードの **[セキュリティ]** セクションにあります。 条件付きアクセス ポリシーの変更の詳細については、「[Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)」を参照してください。 詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」を参照してください。

## <a name="week-of-may-7-2018"></a>2018 年 5 月 7 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Samsung Knox Mobile Enrollment のサポート <!--1112863-->

Knox Mobile Enrollment (KME) で Intune を使用すると、企業が所有する多数の Android デバイスを登録できます。 WiFi または移動体通信ネットワークのユーザーは、初めてデバイスをオンにしたときに、ほんの数タップで登録できます。 Knox Deployment App を使うと、Bluetooth または NFC を使ってデバイスを登録することもできます。 詳しくは、「[Samsung の Knox Mobile Enrollment を使用して Android デバイスを自動的に登録する](android-samsung-knox-mobile-enroll.md)」をご覧ください。

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Windows 10 用 Intune ポータル サイトでのヘルプの要求 <!-- 1874137 -->

ユーザーが問題に関するヘルプを入手するワークフローを開始すると、Windows 10 用 Intune ポータル サイトは Microsoft に直接アプリのログを送信するようになります。 これにより、Microsoft に問題を送ってすばやくトラブルシューティングして解決できます。

## <a name="week-of-april-23-2018"></a>2018 年 4 月 23 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Android での MAM PIN のパスコードのサポート<!-- 1438086 -->

Intune 管理者は、アプリケーション起動要件を設定して、数値の MAM PIN の代わりにパスコードを強制することができます。 構成した場合、ユーザーは、MAM 対応のアプリケーションにアクセスする前に、要求された時点で、パスコードを設定および使用する必要があります。 パスコードは、少なくとも 1 つの特殊文字または大文字/小文字アルファベットを含む数値 PIN と定義されます。 Intune によるパスコードのサポート方法は既存の数値 PIN と似ており、管理コンソールで最小の長さを設定したり、文字やシーケンスの繰り返しを許可したりできます。 この機能を利用するには、Android に最新バージョンの Intune ポータル サイトが必要です。 この機能は、iOS では既に利用できます。

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>macOS の基幹業務 (LOB) アプリのサポート <!-- 1473977 -->
Microsoft Intune では、Azure Portal から macOS LOB アプリをインストールできます。 GitHub で利用可能なツールを使って前処理した macOS LOB アプリを、Intune に追加できます。 Azure Portal で、**[Intune]** ブレードから **[Mobile Apps]** を選択します。 **[Mobile Apps]** ブレードで、**[アプリ]** > **[追加]** を選択します。 **[アプリの追加]** ブレードで、**[基幹業務アプリ]** を選択します。 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Android for Work (AFW) のアプリの割り当てに対する組み込みのすべてのユーザー グループとすべてのデバイス グループ <!-- 1813073 -->
組み込みの**すべてのユーザー** グループと**すべてのデバイス** グループを AFW アプリの割り当てに利用することができます。 詳細については、「[Microsoft Intune でのアプリ割り当ての組み込みと除外](apps-inc-exl-assignments.md)」を参照してください。

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>ユーザーがアンインストールした必要なアプリは Intune によって再インストールされる <!-- 1947010 -->
エンド ユーザーが必要なアプリをアンインストールした場合、Intune は 7 日間の再評価サイクルを待機するのではなく、24 時間以内に該当するアプリを自動的に再インストールします。

### <a name="device-configuration"></a>デバイス構成

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>デバイス プロファイル チャートと状態リストでグループ内のすべてのデバイスが表示されるようになる <!-- 1449153 eeready -->
デバイス プロファイルを構成するときは (**[デバイス構成]** > **[プロファイル]**)、iOS などのデバイス プロファイルを選択します。 このプロファイルを、iOS デバイスと iOS 以外のデバイスを含むグループに割り当てます。 グラフィカル チャートの数では、プロファイルが iOS デバイス "*および*" iOS 以外のデバイスに適用されているように示されます (**[デバイス構成]** > **[プロファイル]** > 既存のプロファイルを選択 > **[概要]**)。 **[概要]** タブでグラフィカル チャートを選択すると、**[デバイスの状態]** に、iOS デバイスだけではなく、グループ内のすべてのデバイスが一覧表示されます。 

この更新により、グラフィカル チャート (**[デバイス構成]** > **[プロファイル]** > 既存のプロファイルを選択 > **[概要]**) では、特定のデバイス プロファイルの数のみが表示されるようになります。 たとえば、構成デバイス プロファイルが iOS デバイスに適用される場合、チャートの一覧には iOS デバイスの数だけが表示されます。 グラフィカル チャートを選択すると開く **[デバイスの状態]** では、iOS デバイスだけが一覧表示されます。

この更新が行われている間、グラフィカル ユーザー チャートは一時的に削除されます。 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>Windows 10 の Always On VPN <!--1333666 -->

現在、[Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) は、OMA-URI を使って作成されたカスタム仮想プライベート ネットワーク (VPN) プロファイルを使うことで、Windows 10 デバイスで使用できます。

この更新では、管理者は Azure Portal の Intune で直接、Windows 10 VPN プロファイルに対する Always On を有効にできるようになります。 Always On VPN プロファイルは、次のときに自動的に接続します。

- ユーザーが自分のデバイスにサインインしたとき
- デバイスでネットワークが変更されたとき
- デバイスの画面がオフにされた後でオンに戻されたとき

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育プロファイル用の新しいプリンター設定 <!-- 1308900 -->

教育プロファイルの場合、**[プリンター]** カテゴリで新しい設定 **[プリンター]**、**[通常使うプリンター]**、**[新しいプリンターの追加]** を利用できます。

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>個人プロファイルでの発信者番号通知 - Android for Work <!--1098984 -->
デバイス上で個人プロファイルを使用する場合、勤務先の作業連絡先からの発信者番号の詳細がエンド ユーザーに表示されない場合があります。 

この更新プログラムでは、**[Android for Work]** > **[デバイスの制限]** > **[仕事用プロファイルの設定]** に、次の新しい設定が表示されます。
- 個人プロファイルに勤務先の連絡先の発信者番号を表示する

有効にすると (構成されていない場合)、勤務先の連絡先の発信者番号の詳細が個人プロファイルに表示されます。 ブロックすると、勤務先の連絡先の発信者番号は個人プロファイルに表示されません。 

適用対象: Android OS v6.0 以降の Android 仕事用プロファイル デバイス

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Endpoint Protection の設定に追加された新しい Windows Defender Credential Guard の設定 <!--1102252 --><!--from 1802 and 1804-->

この更新により、[Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**[デバイス構成]** > **[プロファイル]** > **[Endpoint Protection]**) に、次の設定が含まれます。 

- **Windows Defender Credential Guard**: 仮想化ベースのセキュリティによる Credential Guard が有効になります。 **[Platform Security Level with Secure Boot]\(セキュア ブートでのプラットフォーム セキュリティ レベル\)** と **[仮想化ベースのセキュリティ]** の両方が有効な場合にこの機能を有効にすると、次回の再起動時に資格情報を保護することができます。 次のオプションがあります。
  - **[無効]**: 以前に Credential Guard が **[ロックなしで有効化]** オプションで有効になっていた場合に、Credential Guard をリモートで無効にします。

  - **[UEFI ロックで有効化]**: レジストリ キーまたはグループ ポリシーを使って Credential Guard を無効にできないようにします。 この設定を使用した後に Credential Guard を無効にする場合は、グループ ポリシーを [無効] に設定する必要があります。 次に、実際に存在するユーザーの各コンピューターからセキュリティ機能を削除します。 この手順により、UEFI に存在した構成がクリアされます。 UEFI の構成が保持されている限り、Credential Guard は有効になっています。

  - **[ロックなしで有効化]**: グループ ポリシーを使ってリモートで Credential Guard を無効にできるようにします。 この設定を使うデバイスは、Windows 10 (バージョン 1511) 以降を実行している必要があります。

Credential Guard を構成すると、次の関連するテクノロジが自動的に有効になります。 

  - **[Enable Virtualization-based Security (VBS)]\(仮想化ベースのセキュリティ (VBS) を有効にする\)**: 次回の再起動で仮想化ベースのセキュリティ (VBS) が有効になります。 仮想化ベースのセキュリティは、Windows ハイパーバイザーを使用してセキュリティ サービスのサポートを提供し、セキュア ブートを要求します。
  - **[Secure Boot with Direct Memory Access (DMA)]\(直接メモリ アクセス (DMA) によるセキュア ブート\)**: セキュア ブートおよび直接メモリ アクセスによる VBS が有効になります。 DMA 保護は、ハードウェアのサポートを必要とし、正しく構成されたデバイスでのみ有効にされます。 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>SCEP 証明書でのカスタム サブジェクト名の使用 <!-- 2064190 -->
SCEP 証明書プロファイルでカスタム サブジェクトの共通名 **OnPremisesSamAccountName** を使うことができます。 たとえば、`CN={OnPremisesSamAccountName})` のように使用できます。

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Android for Work でカメラと画面キャプチャをブロックする <!-- 1098977 eeready-->
Android デバイスのデバイス制限を構成するときに、次の 2 つの新しいプロパティをブロックに利用できます。 
- カメラ: デバイスのすべてのカメラへのアクセスを禁止します
- 画面キャプチャ: 画面のキャプチャをブロックし、セキュリティで保護されたビデオ出力を持たないディスプレイ デバイスにコンテンツが表示されないようにします

Android for Work に適用されます。


### <a name="device-enrollment"></a>デバイスの登録

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>macOS High Sierra 10.13.2 以降のデバイスでのユーザーの新しい登録手順 <!--1734567 -->
macOS High Sierra 10.13.2 では、"ユーザー承認済み" MDM 登録の概念が導入されました。 承認済みの登録で、セキュリティ上重要な一部の設定の Intune による管理が許可されます。 詳細については、Apple のサポート ドキュメント https://support.apple.com/HT208019 をご覧ください。

macOS ポータル サイトを使って登録されたデバイスは、エンド ユーザーがシステム環境設定を開いて手動で承認しない限り、"ユーザー承認されていない" ものと見なされます。 そのため、macOS ポータル サイトでは、macOS 10.13.2 以降のユーザーは、登録プロセスの最後に、登録の手動承認に移動するようになりました。 Intune 管理コンソールでは、登録されているデバイスがユーザー承認済みかどうかが示されます。



### <a name="device-management"></a>デバイス管理

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----eeready-1629303---"></a>Advanced Threat Protection (ATP) と Intune は完全に統合されています <!-- EEready 1629303 -->

[Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) では、Windows 10 デバイスのリスク レベルが表示されます。 Windows Defender Security Center (ATP Portal) では、Microsoft Intune への接続を作成できます。 作成後、許容できる脅威レベルの決定に Intune コンプライアンス ポリシーが使用されます。 その脅威レベルを超えた場合、Azure Active Directory (AD) の条件付きアクセス ポリシーによって、組織内のさまざまなアプリへのアクセスを阻止できます。

この機能によって ATP はファイルをスキャンし、脅威を検出し、Windows 10 デバイス上のあらゆるリスクを報告できます。

[Intune で条件付きアクセスによる ATP を有効にする](advanced-threat-protection.md)方法に関するページを参照してください。

#### <a name="support-for-user-less-devices----1637553---"></a>ユーザーのいないデバイスのサポート <!-- 1637553 -->
Intune は、Microsoft Surface Hub など、ユーザーのいないデバイスでコンプライアンスを評価する機能をサポートします。 コンプライアンス ポリシーは、特定のデバイスを対象にすることができます。 したがって、ユーザーが関連付けられていないデバイスのコンプライアンス (および非コンプライアンス) を判断できます。

#### <a name="delete-autopilot-devices----1713650---"></a>Autopilot デバイスの削除 <!-- 1713650 -->
Intune 管理者は、[Autopilot デバイスを削除する](enrollment-autopilot.md#delete-autopilot-devices)ことができます。

#### <a name="improved-device-deletion-experience---1832333---"></a>デバイス削除エクスペリエンスの向上 <!--1832333 -->
[Intune からデバイスを削除する](devices-wipe.md#delete-devices-from-the-intune-portal)前に、会社のデータを削除したり、デバイスを工場出荷時の状態にリセットしたりする必要はなくなります。

新しいエクスペリエンスを表示するには、Intune にサインインし、**[デバイス]** > **[すべてのデバイス]** > デバイスの名前 > **[削除]** の順に選びます。

ワイプ/使用停止の確認が必要な場合は、**[削除]** の前に **[会社データを削除する]** と **[出荷時の設定にリセット]** を実行して、標準のデバイス ライフサイクル ルートを使うことができます。 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>紛失モードになったときに iOS で音を鳴らす <!-- 1947769 -->
監視対象の iOS デバイスがモバイル デバイス管理 (MDM) の[紛失モード](device-lost-mode.md)になったときに、[音を鳴らす](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device)ことができます (**[デバイス]** > **[すべてのデバイス]** > iOS デバイスを選択 > **[概要]** > **[詳細]**)。 音は、デバイスが紛失モードではなくなるまで、またはユーザーがデバイスで音を無効にするまで、鳴り続けます。 iOS デバイス 9.3 以降に適用されます。

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Intune デバイスで行った Web 検索の結果のブロックまたは許可 <!--1972804-->

管理者は、デバイスで行った Web 検索の結果をブロックできるようになりました。

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Apple MDM プッシュ通知証明書のアップロード失敗のエラー メッセージの改善 <!-- 2172331 -->

既存の MDM 証明書を更新するときは同じ Apple ID を使う必要があることが、エラー メッセージで説明されます。

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>仮想マシンでの macOS 用ポータル サイトのテスト <!-- 2216679 -->

Parallels Desktop と VMware Fusion の仮想マシンで IT 管理者が macOS 用ポータル サイト アプリをテストするために役立つガイドを公開しました。 詳しくは、「[テスト用に仮想 macOS マシンを登録する](macos-enroll.md#enroll-virtual-macos-machines-for-testing)」を参照してください。


### <a name="user-interface"></a>ユーザー インターフェイス

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Windows 10 ポータル サイトのデバイス タイルの改善 <!--2213364 -->

目の不自由なユーザーでもアクセスしやすく、画面読み上げツールでの動作が改善されるように、タイルが更新されました。

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>macOS のポータル サイト アプリでの診断レポートの送信 <!-- 2216677 -->
macOS デバイスのポータル サイト アプリが更新され、ユーザーが Intune 関連のエラーを報告しやすくなりました。 ポータル サイト アプリから、従業員は次の操作を行うことができます。

- Microsoft 開発者チームに直接診断レポートをアップロードする。
- 会社の IT サポート チームにインシデント ID をメールで送ります。

詳細については、[macOS のエラーの送信](/intune-user-help/send-errors-macos)に関するページを参照してください。

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune が Windows 10 ポータル サイト アプリの Fluent Design System に対応 <!-- 1195010 WNready -->
Windows 10 の Intune ポータル サイト アプリが [Fluent Design System のナビゲーション ビュー](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics)に合わせて更新されました。 アプリの側面だけでなく、すべてのトップ レベルのページに静的な縦方向リストが表示されます。 リンクをクリックすると、ページをすばやく表示したり、ページを切り替えたりできます。 これは現在作成中の更新の一部であり、今後さらにアダプティブで馴染みがあり、使いやすい Intune の機能を提供していきます。 更新された外観を確認するには、[アプリ UI の新機能](whats-new-app-ui.md)に関するページを参照してください。

## <a name="week-of-april-16-2018"></a>2018 年 4 月 16 日の週

#### <a name="use-cisco-anyconnect-client-for-ios----eeready-1333708---"></a>iOS 向け Cisco AnyConnect クライアントを使用する <!-- EEready 1333708 -->

iOS 用に新しい VPN プロファイルを作成するとき、**[Cisco AnyConnect]** と **[Cisco Legacy AnyConnect]** の 2 つの選択肢から選択できるようになりました。 Cisco AnyConnect プロファイルは、4.0.7x 以降のバージョンに対応しています。 既存の iOS Cisco AnyConnect VPN プロファイルは **[Cisco Legacy AnyConnect]** と表示されるようになり、現在と同じように Cisco AnyConnect 4.0.5x 以前のバージョンで引き続き動作します。

> [!NOTE]
> この変更は iOS にのみ適用されます。 Android、Android for Work、macOS プラットフォームの Cisco AnyConnect オプションは、これまでどおり 1 つだけです。

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Jamf 登録 macOS デバイスを Intune に登録できるようになりました <!-- 2370684 -->

macOS ポータル サイトのバージョン 1.3 と 1.4 では、Jamf デバイスが Intune に正常に登録されませんでした。 macOS ポータル サイトのバージョン 1.4.2 でこの問題が解決されました。


## <a name="week-of-april-9-2018"></a>2018 年 4 月 9 日の週  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Android 用ポータル サイト アプリでのヘルプ エクスペリエンスの更新 <!-- 1631531 -->

Android プラットフォームのベスト プラクティスに合うように、Android 用ポータル サイト アプリのヘルプ エクスペリエンスが更新されました。 ご使用のアプリで問題が発生した場合は、**[メニュー]** > **[ヘルプ]** の順にタップして、次のことが行えます。
- 診断ログを Microsoft にアップロードする。
- 問題とインシデント ID を記載した電子メールを社内のサポート担当者に送信する。  

更新されたヘルプ エクスペリエンスを確認するには、[[Send logs using email]\(メールでログを送信\)](/intune-user-help/send-logs-to-your-it-admin-by-email-android) および [[Send errors to Microsoft]\(エラーを Microsoft に送信\)](/intune-user-help/send-logs-to-microsoft-android) に進みます。


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>新しい登録エラー傾向グラフと失敗の理由テーブル <!-- 1471783 -->

[Enrollment Overview]\(登録の概要\) ページで、登録エラーの傾向と、上位 5 つのエラーの原因を表示することができます。 グラフやテーブルをクリックすると、トラブルシューティングのアドバイスや改善の提案の詳細にドリル ダウンすることができます。

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>アプリの保護ポリシーを構成する場所の更新 <!-- 2144597 -->

Azure Portal の Microsoft Intune サービスで、**[Intune アプリ保護]** サービス ブレードから **[モバイル アプリ]** ブレードに一時的にリダイレクトします。 すべてのアプリ保護ポリシーが Intune のアプリ構成の **[モバイル アプリ]** ブレードに既に置かれていることに注意してください。 Intune App Protection に移動する代わりに、Intune に移動します。 2018 年 4 月にリダイレクトを停止し、**[Intune App Protection]** サービス ブレードを完全に削除する予定です。したがって、Intune 内のアプリ保護ポリシーのための場所は 1 つだけになります。 

**ユーザーへの影響**
この変更は、Intune スタンドアロンのお客様とハイブリッド (Intune と Configuration Manager) のお客様の両方に影響します。 この統合は、クラウド管理の簡素化に役立ちます。

**この変更に対して必要な準備**
**[Intune アプリ保護]** サービス ブレードの代わりにお気に入りとして **Intune** に登録し、Intune の **[モバイル アプリ]** ブレードのアプリ保護ポリシーのワークフローを習熟してください。 リダイレクトを短期間行い、その後 **[アプリ保護]** ブレードを削除します。 ただし、すべてのアプリ保護ポリシーが既に Intune にあり、任意の条件付きアクセス ポリシーを変更することができます。 条件付きアクセス ポリシーの変更の詳細については、「[Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)」を参照してください。 詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」を参照してください。 


## <a name="week-of-april-2-2018"></a>2018 年 4 月 2 日の週

### <a name="intune-apps"></a>Intune アプリ

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>iOS 用ポータル サイト アプリに関するユーザー エクスペリエンスの更新プログラム <!--1412866 -->
iOS 用のポータル サイト アプリに対して、主要なユーザー エクスペリエンスの更新プログラムをリリースする予定です。 この更新プログラムでは、最新のルック アンド フィールを含む完全なビジュアル再設計が行われています。 アプリの機能を維持した上で、操作性とアクセシビリティが向上しています。  

また、次のような更新が行われています。
- iPhone X のサポート。
- アプリの起動および読み込み応答を速くして、ユーザー時間を節約。
- 最新の状態情報をユーザーに提供するための進行状況バーを追加。
- ログのアップロード方法を改善。これにより、問題が生じた場合に、その内容を簡単にレポートできる。  

更新された外観を確認するには、[アプリ UI の新機能](whats-new-app-ui.md)に関するページを参照してください。

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Intune APP および CA を使用したオンプレミス Exchange データの保護 <!-- 1056954 -->
Intune アプリ ポリシー保護 (APP) および条件付きアクセス (CA) を使用して、Outlook Mobile によるオンプレミスの Exchange データへのアクセスを保護できるようになりました。 Azure Portal 内でアプリの保護ポリシーの追加または変更を行うには、**[Microsoft Intune]** > **[モバイル アプリ]** > **[アプリ保護ポリシー]** を選択します。 この機能を使用する前に、[iOS および Android 用 Outlook の要件](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx)を満たしていることを確認します。

## <a name="week-of-march-26-2018"></a>2018 年 3 月 26 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Microsoft Intune 用の iOS 基幹業務 (LOB) アプリの有効期限切れを示すアラート <!-- 748789 -->

Azure Portal の Intune では、有効期限が近づいている iOS 基幹業務アプリが警告されます。 iOS 基幹業務アプリの新しいバージョンをアップロードすると、有効期限に関する通知が Intune によってアプリ一覧から削除されます。 この有効期限に関する通知は、iOS 基幹業務アプリが新たにアップロードされた場合にのみアクティブになります。 警告が表示されるのは、iOS LOB アプリのプロビジョニング プロファイルの有効期限が切れる 30 日前となります。 有効期限が切れると、アラート表示が "期限切れ" 表示に変わります。

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Intune ポータル サイトのテーマを 16 進コードでカスタマイズする <!--1049561 -->

Intune ポータル サイト アプリのテーマの色を、16 進コードを使ってカスタマイズできます。 16 進コードを入力すると、Intune はテキストの色と背景の色の間のコントラストが最高レベルになるようにテキストの色を決定します。 **[Mobile Apps]** > **[ポータル サイト]** で、テキストの色および色に対する会社のロゴの両方をプレビューできます。

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Android Enterprise に対するグループに基づくアプリ割り当ての追加と除外 <!-- 1813081 -->

Android エンタープライズ (旧称 Android for Work) では、グループの追加と除外をサポートしていますが、事前に作成された**すべてのユーザー**と**すべてのデバイス**の組み込みグループはサポートしていません。 詳細については、「[Microsoft Intune でのアプリ割り当ての組み込みと除外](apps-inc-exl-assignments.md)」を参照してください。


### <a name="device-management"></a>デバイス管理

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Intune サービスでの新たなセキュリティ強化  <!-- 1637539 -->   

Azure 上の Intune にトグルが導入されました。このスイッチを利用することにより、Intune スタンドアロンのお客様は、ポリシーが割り当てられていないデバイスを **[準拠]** として処理 (セキュリティ機能オフ) することも、そのようなデバイスを **[非準拠]** として処理 (セキュリティ機能オン) することもできます。 これにより、デバイスのポリシー準拠が評価された後でのみ、リソースへのアクセスが保証されます。

この機能がユーザーに及ぼす影響は、コンプライアンス ポリシーが割り当て済みかどうかによって異なります。

- 新しいアカウントまたは既存のアカウントがあるが、コンプライアンス ポリシーをデバイスに割り当てていない場合、トグルは自動的に **[準拠]** に設定されます。 コンソールの既定の設定では、この機能はオフになっています。 エンドユーザーに与える影響はありません。
- 既存のアカウントがあり、デバイスにはコンプライアンス ポリシーが割り当てられている場合、トグルは自動的に **[非準拠]** に設定されます。 この機能は、3 月の更新のロールアウト時に、既定の設定としてオンになっています。

コンプライアンス ポリシーを条件付きアクセス (CA) と共に使用し、この機能がオンになっている場合、少なくとも 1 つのコンプライアンス ポリシーが割り当てられているデバイスは、CA によってブロックされるようになりました。 これらのデバイスに関連付けられていて、以前は電子メールへのアクセスを許可されていたエンド ユーザーは、少なくとも 1 つのコンプライアンス ポリシーをすべてのデバイスに割り当てない限り、アクセスできなくなります。   

Intune サービスの 3 月の更新プログラムにより、既定のトグル状態は UI にすぐに表示されるようになりましたが、このトグル状態はすぐに適用されないので注意してください。 トグルに変更を加えても、アカウントがフライトされて準備が整うまで、デバイスのポリシー準拠に影響はありません。 アカウントのフライトが完了したら、メッセージ センターを介してお知らせします。 これには、3 月の Intune サービスの更新が行われてから、数日かかる場合があります。

**追加情報**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>脱獄の検出の機能強化 <!-- 846515 -->

強化された脱獄の検出の新しいコンプライアンス設定により、Intune による脱獄されたデバイスの評価方法が向上します。 この設定を使用すると、デバイスはこれまでより頻繁に Intune にチェックインされます。このときデバイスの場所サービスが使用されるため、バッテリの使用量に影響を与えます。

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Android O デバイスのパスワードをリセットする <!-- 1238299 -->
作業プロファイルで、登録済みの Android 8.0 デバイスのパスワードをリセットできるようになります。 Android 8.0 デバイスに "パスワード リセット" 要求を送信すると、新しいデバイス ロック解除パスワードまたはマネージド プロファイルのチャレンジが、現在のユーザーに設定されます。 パスワードまたはチャレンジが送信され、すぐには有効になります。

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>デバイス グループのデバイスへのコンプライアンス ポリシーのターゲット<!--1307012 -->

ユーザー グループ内のユーザーを、コンプライアンス ポリシーのターゲットにすることができます。 この更新プログラムを使用すると、デバイス グループ内のデバイスを、コンプライアンス ポリシーのターゲットにすることができます。 デバイス グループの一部としてターゲットにされたデバイスがコンプライアンス アクションを受け取ることはありません。

#### <a name="new-management-name-column----1333586---"></a>新しい [管理名] 列 <!-- 1333586 -->
 **[管理名]** という名前の新しい列がデバイス ブレードで使用できます。 これは、次の式に基づいてデバイスごとに割り当てられる、自動生成された編集不可能な名前です。
- すべてのデバイスの既定の名前: <username><em><devicetype></em><enrollmenttimestamp>
- 一括追加デバイスの場合: <PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

これは、デバイス ブレードの省略可能な列です。 既定では使用できず、列セレクターを使用してのみアクセスできます。 この新しい列によるデバイス名への影響はありません。

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>iOS デバイスで 15 分ごとに PIN の入力を求める <!--1550837 -->
iOS デバイスにコンプライアンスまたは構成ポリシーが適用されると、ユーザーは 15 分ごとに PIN を設定するように求められます。 PIN を設定するまで継続してユーザーは入力を求められます。

#### <a name="schedule-your-automatic-updates---1805514---"></a>自動更新スケジュールの設定 <!--1805514 -->
Intune では、[Windows Update リングの設定](windows-update-for-business-configure.md)を使用して、自動更新のインストールを制御することができます。 この更新プログラムでは、週、日、時刻などを指定して、繰り返し更新が発生するようスケジュールすることができます。

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>SCEP 証明書のサブジェクトとして完全な識別名を使用する <!--2221763 -->
SCEP 証明書プロファイルを作成するときには、サブジェクト名を入力します。 この更新プログラムでは、サブジェクト名として、完全な識別名を使用できるようになります。 **サブジェクト名**に対して **[カスタム]** を選択し、`CN={{OnPrem_Distinguished_Name}}` と入力します。 `{{OnPrem_Distinguished_Name}}` 変数を使用するには、[Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) を使用して、`onpremisesdistingishedname` ユーザー属性を Azure AD と同期させます。

### <a name="device-configuration"></a>デバイス構成

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Bluetooth での連絡先の共有の有効化 - Android for Work <!--1098983 -->
Android の既定では、仕事用プロファイルの連絡先が Bluetooth デバイスと同期することはできません。 その結果、Bluetooth デバイスに対して、仕事用プロファイルの連絡先が発信者 ID に表示されません。

この更新プログラムでは、**[Android for Work]** > **[デバイスの制限]** > **[仕事用プロファイルの設定]** に、次の新しい設定が表示されます。
- Bluetooth 経由での連絡先の共有

Intune の管理者は、これらの設定を構成して共有を有効にできます。 これは、デバイスを、ハンズフリー使用のために発信者 ID を表示する、車を拠点とする Bluetooth デバイスとペアリングする場合に便利です。 有効にすると、仕事用プロファイルの連絡先が表示されます。 無効にすると、仕事用プロファイルの連絡先は表示されません。

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>macOS アプリ ダウンロード ソースを制御するための Gatekeeper の構成 <!-- 1690459 -->

ダウンロードできるアプリの場所を制御することでアプリからデバイスを保護するように、Gatekeeper を構成することができます。 構成できるダウンロード ソースは、**[Mac App Store]**、**[Mac App Store と識別された開発者]**、または **[どこでも]** となります。 また、ユーザーが Ctrl キーを押しながらクリックしてアプリをインストールすることによりこれらの Gatekeeper 制御をオーバーライドできるかどうかも構成できます。

これらの設定は、**[デバイス構成]** -> **[プロファイルの作成]** -> **[macOS]** -> **[Endpoint Protection]** にあります。

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Mac アプリケーションのファイアウォールの構成 <!-- 1690461 -->

Mac アプリケーションのファイアウォールを構成できます。 これを使って、ポートごとではなく、アプリケーションごとに接続を制御できます。 これにより、ファイアウォールによる保護を簡単に利用できるようになり、正当なアプリ用に開かれているネットワーク ポートを望ましくないアプリが制御するのを防ぐのに役立ちます。

この設定は、**[デバイス構成]** -> **[プロファイルの作成]** -> **[macOS]** -> **[Endpoint Protection]** にあります。

ファイアウォールの設定を有効にすると、2 つの戦略を使ってファイアウォールを構成できます。

- すべての着信接続をブロックする

   対象デバイスに対するすべての着信接続をブロックすることができます。 この方法を選択した場合、すべてのアプリの着信接続がブロックされます。

- 特定のアプリを許可またはブロックする

   特定のアプリからの着信接続の受信を許可またはブロックできます。 ステルス モードを有効にして、プローブ要求への応答を防ぐこともできます。

####  <a name="detailed-error-codes-and-messages----1376342---"></a>詳しいエラー コードとメッセージ <!-- 1376342 -->

デバイス構成で、より詳しいエラー コードとエラー メッセージを確認できます。 この改善された報告機能には、設定、設定の状態、トラブルシューティングの詳細が表示されます。

##### <a name="more-information"></a>詳細情報

- すべての着信接続をブロックする

   すべての共有サービス (ファイル共有や画面共有など) が着信接続を受信するのをブロックします。 その場合でも、次のシステム サービスは着信接続を受信できます。
  - configd - DHCP および他のネットワーク構成サービスを実装します
  - mDNSResponder - Bonjour を実装します
  - racoon - IPSec を実装します

    共有サービスを使うには、**[着信接続]** を (**[ブロック]** ではなく) **[未構成]** に設定します。

- ステルス モード

   これを有効にすると、コンピューターはプローブ要求に応答しなくなります。 その場合でも、コンピューターは承認されたアプリの着信要求には応答します。 ICMP (ping) などの予期しない要求は無視されます。

#### <a name="disable-checks-on-device-restart---1805490---"></a>デバイス再起動時のチェックの無効化 <!--1805490 -->
Intune では[ソフトウェア更新プログラムを管理](windows-update-for-business-configure.md)することができる。 この更新プログラムでは、<strong>[再起動チェック]</strong> プロパティが提供され、既定では有効になります。 デバイスを再起動する際に発生する一般的なチェック (アクティブなユーザー、バッテリのレベルなど) をスキップするには、<strong>[スキップ]</strong> を選択します。

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>展開リングで利用できる新しい Windows 10 Insider Preview チャンネル <!-- 1746293 -->
Windows 10 展開リングを作成するときに、次の Windows 10 Insider Preview サービス チャンネルを選択するオプションが使用できるようになりました。
- Windows Insider ビルド - 高速
- Windows Insider ビルド - 低速
- Windows Insider ビルドのリリース 

これらのチャネルの詳細については、「[Insider Preview ビルドの管理](https://insider.windows.com/en-us/for-business-organization-admin/)」を参照してください。   
Intune での展開チャネルの作成の詳細については、「[ソフトウェア更新プログラムの管理](windows-update-for-business-configure.md)」を参照してください。

### <a name="intune-apps"></a>Intune アプリ

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>会社ポータルの登録の機能強化 <!-- 1874230 eeready-->
Windows 10 ビルド 1703 以降の Intune ポータル サイトを使ってデバイスを登録するユーザーは、アプリを離れることなく登録の最初の手順を完了できるようになりました。
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens と Surface Hub がデバイス リストに表示されるようになった <!--1725868 -->
Intune に登録された HoloLens および Surface Hub のデバイスを Android 用ポータル サイト アプリに表示するためのサポートが追加されました。

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>ボリューム購入プログラム (VPP) 電子ブックのカスタム ブック カテゴリ <!-- 1488911 -->
電子ブックのカスタム カテゴリを作成し、VPP の電子ブックをカスタム電子ブック カテゴリに割り当てることができます。 エンド ユーザーは、新しく作成された電子ブック カテゴリとそのカテゴリに割り当てられているブックを見ることができます。 詳細については、「[Microsoft Intune によるボリューム購入アプリとブックの管理](vpp-apps.md)」を参照してください。  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>Windows 用 Intune ポータル サイト アプリのフィードバック送信オプションのサポートの変更 <!-- 2070166 -->
2018 年 4 月 30 日以降、Windows 用 Intune ポータル サイト アプリの **[フィードバックの送信]** オプションは、Windows 10 Anniversary Update (1607) 以降を実行するデバイスでのみ動作します。 次の Windows で Intune ポータル サイト アプリを使用している場合、フィードバック送信オプションはサポートされません。  
- Windows 10、1507 リリース  
- Windows 10、1511 リリース  
- Windows Phone 8。1 

お使いのデバイスが Windows 10 RS1 以降を実行している場合は、Store から最新バージョンの Windows 用 Intune ポータル サイト アプリをダウンロードしてください。 サポートされないバージョンを実行している場合は、引き続き次のチャネルでフィードバックを送信してください。 
- Windows 10 のフィードバック ハブ アプリ
- WinCPfeedback@microsoft.com へのメール  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Windows Defender Application Guard の新しい設定 <!-- 1631890 -->

- **グラフィック アクセラレータを有効にする**: 管理者は、Windows Defender Application Guard に対して仮想グラフィック プロセッサを有効にすることができます。 この設定を使うと、CPU はグラフィックのレンダリングを vGPU にオフロードできます。 これにより、グラフィックが多用されている Web サイトを操作するとき、またはコンテナー内のビデオを見るときのパフォーマンスが向上します。

- **SaveFilestoHost**: 管理者は、コンテナーで実行されている Microsoft Edge からホスト ファイル システムへのファイルの受け渡しを有効にすることができます。 これをオンにすると、ユーザーはコンテナー内の Microsoft Edge からホスト ファイル システムにファイルをダウンロードできます。

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>管理の状態に基づいて対象とされる MAM 保護ポリシー <!-- 1665993 -->
デバイスの管理状態に基づいて、MAM ポリシーを対象とすることができます。
- **Android デバイス** - アンマネージド デバイス、Intune で管理されたデバイス、Intune で管理された Android Enterprise Profiles (旧称 Android for Work) を対象にできます。
- **iOS デバイス** - アンマネージド デバイス (MAM のみ) または Intune で管理されたデバイスを対象にできます。

    > [!NOTE]
    > - この機能用の iOS サポートは、2018 年 4 月を通してロールアウトされます。

詳細については、[デバイス管理状態に基づくターゲット アプリ保護ポリシー](app-protection-policies.md)に関するページを参照してください。

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Windows 用ポータル サイト アプリの言語を改善 <!-- 1683758 -->
ユーザーにわかりやすく、組織に特有の言語となるように、Windows 10 用ポータル サイトの言語に改善を加えました。 改善された内容を示すサンプル画像を確認するには、[アプリ UI の新機能](whats-new-app-ui.md)に関するページを参照してください。

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>ユーザー プライバシーに関する Microsoft ドキュメントへの新規追加 <!-- 1440709 -->
エンドユーザーが自身のデータとプライバシーをより厳密に制御できるようにするための Microsoft の取り組みの一環として、ポータル サイト アプリによってローカルに格納されたデータの表示および削除方法を説明した Microsoft ドキュメントに対する更新内容を公開しました。 これらの更新内容は以下で確認できます。

- **Android**: [Intune から Android デバイスを削除する方法](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **Android (ユーザーが使用条件を拒否した場合)**: ["使用条件" が拒否された場合にデバイス管理を削除する](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS**: [Intune から iOS デバイスを削除する](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows**: [Intune から Windows デバイスを削除する](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## <a name="week-of-march-19-2018"></a>2018 年 3 月 19 日の週

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>IE、Edge、または Chrome ですべてのデバイスを CSV ファイルにエクスポートする <!-- 2258071 -->
**[デバイス]** > **[すべてのデバイス]** で、デバイスを CSV 形式の一覧に**エクスポート**することができます。 10,000 を超えるデバイスを持つ Internet Explorer (IE) ユーザーは、デバイスを複数のファイルに正常にエクスポートできます。 各ファイルには、最大 10,000 のデバイスが含まれます。

30,000 を超えるデバイスを持つユーザーは、デバイスを複数のファイルに正常にエクスポートできます。 各ファイルには、最大 30,000 のデバイスが含まれます。

管理するデバイスに対して実行できる操作の詳細については、[デバイスの管理](device-management.md)に関するページを参照してください。

## <a name="week-of-march-12-2018"></a>2018 年 3 月 12 日の週

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory の Web サイトでは、Intune Managed Browser アプリを要求し、Managed Browser (パブリック プレビュー) に対するシングル サインオンをサポートすることができる <!-- 710595 -->

Azure Active Directory (Azure AD) を使用している場合、モバイル デバイスでの Web サイトへのアクセスを Intune Managed Browser アプリに制限できるようになりました。 Managed Browser では、Web サイトのデータは安全性が維持され、エンド ユーザーの個人データと分離されます。 さらに、Managed Browser は、Azure AD によって保護されているサイトに対するシングル サインオン機能をサポートします。 Managed Browser にサインインすると、または Intune によって管理されている別のアプリでデバイスの Managed Browser を使うと、ユーザーが資格情報を入力しなくても、Managed Browser は Azure AD によって保護されている会社サイトにアクセスできます。 この機能は、Outlook Web Access (OWA) や SharePoint Online などのサイトだけでなく、Azure App プロキシ経由でアクセスされるイントラネット リソースのような他の企業サイトにも適用されます。 詳細については、「[Azure Active Directory の条件付きアクセスのアクセス制御](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls)」を参照してください。

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Android 用ポータル サイト アプリのビジュアルの更新 <!--976944 -->

Android 用 Intune ポータル サイト アプリを、Android の[マテリアル デザイン](https://material.io/) ガイドラインに合わせて更新しています。 「[アプリ UI の新機能](whats-new-app-ui.md)」の記事で、新しいアイコンの画像を確認することができます。

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>Windows Defender Exploit Guard の新しい設定 <!-- 1631893 -->

<strong>[攻撃の回避]</strong> の 6 つの新しい設定と、拡張された <strong>[フォルダー アクセスの制御: フォルダーの保護]</strong> 機能が利用できるようになりました。 これらの設定は、[デバイス構成] > [プロファイル] > 
[プロファイルの作成] > [Endpoint Protection] > [Windows Defender Exploit Guard] にあります。

#### <a name="attack-surface-reduction"></a>攻撃の回避

|設定の名前  |設定オプション  |説明  |
|---------|---------|---------|
|Advanced ransomware protection (高度なランサムウェア防止)|有効、監査、未構成|積極的なランサムウェア防止を使います。|
|Flag credential stealing from the Windows local security authority subsystem (Windows ローカル セキュリティ機関サブシステムからの資格情報の盗難にフラグを設定する)|有効、監査、未構成|Windows ローカル セキュリティ機関サブシステム (lsass.exe) からの資格情報の盗難にフラグを設定します。|
|Process creation from PSExec and WMI commands (PSExec および WMI コマンドからのプロセス作成)|ブロック、監査、未構成|PSExec および WMI コマンドから開始されるプロセス作成をブロックします。|
|Untrusted and unsigned processes that run from USB (USB から実行された信頼されていない署名なしのプロセス)|ブロック、監査、未構成|USB から実行された信頼されていない署名なしのプロセスをブロックします。|
|Executables that don’t meet a prevalence, age, or trusted list criteria (普及、経過時間、または信頼されたリストの条件を満たしていない実行可能ファイル)|ブロック、監査、未構成|普及、経過時間、または信頼されたリストの条件を満たしていない実行可能ファイルの実行をブロックします。|

#### <a name="controlled-folder-access"></a>フォルダー アクセスの制御

|              設定の名前               |                                                              設定オプション                                                              | 説明 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| フォルダーの保護 (実装済み) | 未構成、有効、監査のみ (実装済み)<br><br> <strong>新規</strong><br>Block disk modification (ディスクの変更をブロックする)、Audit disk modification (ディスクの変更を監査する) |             |

ファイルおよびフォルダーを、悪意のあるアプリによる未承認の変更から保護します。<br><br>**有効**: 信頼されていないアプリによる、保護されたフォルダー内のファイルの変更または削除、およびディスク セクターへの書き込みを、禁止します。<br><br>
**Block disk modification only (ディスクの変更のみをブロック)**:<br>信頼されていないアプリによるディスク セクターへの書き込みをブロックします。 信頼されていないアプリは、保護されたフォルダー内のファイルを変更または削除することはできます。

## <a name="week-of-february-19-2018"></a>2018 年 2 月 19 日の週

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>複数の Apple DEP および Apple School Manager アカウントに対する Intune サポート<!-- 747685 -->

最大 100 個の異なる [Apple Device Enrollment Program (DEP)](device-enrollment-program-enroll-ios.md) または [Apple School Manager](apple-school-manager-set-up-ios.md) アカウントからのデバイス登録が、Intune でサポートされます。 アップロードされる各トークンは、登録プロファイルとデバイスで、別々に管理できます。 アップロードされる DEP および School Manager のトークンごとに、異なる登録プロファイルを自動で割り当てることができます。 複数の School Manager トークンがアップロードされた場合、Microsoft 学校データ同期と共有できるのは、一度に 1 つのみです。

移行後、Graph で Apple DEP および ASM を管理するベータ版の Graph API と公開されたスクリプトは、動作しなくなります。 現在、新しいベータ版の Graph API の開発が進行中で、移行後にリリースされる予定です。

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>ユーザーごとに登録の制限を表示する <!-- 1634444 eeready wnready -->
**[トラブルシューティング]** ブレードの **[割り当て]** 一覧から **[登録制限]** を選択すると、各ユーザーに対して有効な[登録制限](enrollment-restrictions-set.md)を参照することができます。

### <a name="device-management"></a>デバイス管理
#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Windows Defender の正常性状態レポートと脅威状態レポート<!--854704 -->

Windows Defender の正常性と状態を理解することは、Windows PC の管理において重要なことです。  この更新では、Intune に、Windows Defender エージェントの状態と正常性の新しいレポートやアクションが追加されています。 [デバイスのポリシー準拠ワークロード](compliance-policy-monitor.md)の状態ロールアップ レポートを使用すると、次のことが必要なデバイスを確認できます。
- 署名の更新
- 再起動
- 手動介入
- フル スキャン
- 介入を必要とする他のエージェント状態

各状態カテゴリのドリルイン レポートでは、注意の必要な PC または**クリーン**と報告されている PC が個別に一覧表示されます。

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>デバイス制限のための新しいプライバシー設定 <!--1308926 -->
[2 つの新しいプライバシー設定](device-restrictions-windows-10.md#privacy)をデバイスで利用できるようになりました。
- **ユーザー アクティビティの公開**: これを **[ブロック]** に設定すると、タスク スイッチャーでの共有エクスペリエンスおよび最近使われたリソースの検出が行われなくなります。
- **ローカル アクティビティの場合のみ**: これを **[ブロック]** に設定すると、ローカル アクティビティのみに基づいて、タスク スイッチャーでの共有エクスペリエンスおよび最近使われたリソースの検出が行われなくなります。

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Microsoft Edge ブラウザーの新しい設定 <!--1469166 -->
Microsoft Edge ブラウザーを備えたデバイスで、[2 つの新しい設定](device-restrictions-windows-10.md#edge-browser) **[Path to favorites file]\(お気に入りファイルへのパス\)** と **[Changes to Favorites]\(お気に入りへの変更\)** が利用できるようになりました。

### <a name="app-management"></a>アプリ管理
#### <a name="protocol-exceptions-for-applications---1035509---"></a>アプリケーションのプロトコル例外 <!--1035509 -->

Intune モバイル アプリケーション管理 (MAM) データ転送ポリシーの例外を作成し、特定の管理されていないアプリケーションを開くことができまるようになりました。 このようなアプリケーションは、IT 担当者によって信頼されている必要があります。 データ転送ポリシーを**管理対象アプリのみ**に設定すると、作成した例外以外については、やはりデータ転送が Intune で管理されているアプリケーションだけに制限されます。 プロトコル (iOS) またはパッケージ (Android) を使って制限を作成することができます。

たとえば、MAM データ転送ポリシーに対する例外として、Webex パッケージを追加できます。 これにより、管理された Outlook メール メッセージ内の Webex リンクを、Webex アプリケーションで直接開くことができます。 他の管理されていないアプリケーションでは、データ転送が制限されます。 詳細については、「[Data transfer policy exceptions for apps](app-protection-policies-exception.md)」(アプリのデータ転送ポリシーの例外) を参照してください。

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 検索結果の Windows 情報保護 (WIP) 暗号化データ<!-- 1469193 -->
Windows 情報保護 (WIP) ポリシーの設定により、WIP で暗号化されたデータを Windows の検索結果に含めるかどうかを制御できるようになりました。 このアプリ保護ポリシー オプションを設定するには、Windows 情報保護 (WIP) ポリシーの **[詳細設定]** で **[Allow Windows Search Indexer to search encrypted items]** \(暗号化されたアイテムの検索を Windows Search Indexer に許可する\) を選択します。 アプリの保護ポリシーは、*[Windows 10]* プラットフォームに設定し、アプリ ポリシーの **[登録状態]** は **[With enrollment]** \(登録あり\) に設定する必要があります。 詳細については、「[Allow Windows Search Indexer to search encrypted items](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items)」 (暗号化されたアイテムの検索を Windows Search Indexer に許可する) を参照してください。

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>自己更新モバイル MSI アプリの構成 <!-- 1740840 -->
バージョン チェック プロセスを無視するように、既知の自己更新モバイル MSI アプリを構成することができます。 この機能は、競合状態になるのを防ぐのに役立ちます。 たとえば、この種類の競合状態は、アプリ開発者によって自動更新されているアプリが、Intune によっても更新されると、発生する可能性があります。 両方が Windows クライアント上のアプリのバージョンを強制しようとして、競合が発生することがあります。 これらの自動更新される MSI アプリには、**[アプリ情報]** ブレードで **[Ignore app version]** \(アプリのバージョンを無視する\) を設定できます。 この設定を **[はい]** に切り替えると、Microsoft Intune で Windows クライアントにインストールされているアプリのバージョンは無視されます。

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Intune でサポートされるアプリ ライセンスの関連する設定 <!-- 1864117 -->
Azure Portal 内の Intune で、UI の単一アプリ項目として、アプリ ライセンスの関連する設定がサポートされるようになりました。 さらに、ビジネス向け Microsoft Store から同期されるすべてのオフライン ライセンス アプリは単一のアプリ エントリに統合され、個別のパッケージからの展開の詳細は 1 つのエントリに移行されます。 Azure Portal でアプリ ライセンスの関連する設定を表示するには、**[Mobile Apps]** ブレードから **[アプリ ライセンス]** を選びます。

### <a name="device-configuration"></a>デバイス構成
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Windows 情報保護 (WIP) ファイルの自動暗号化用拡張子<!-- 1463582 -->
会社の境界内のサーバー メッセージ ブロック (SMB) 共有からコピーする場合、WIP ポリシーの定義に従って、自動的に暗号化するファイル拡張子を、Windows 情報保護 (WIP) ポリシーで指定できるようになりました。

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Surface Hub のリソース アカウント設定を構成する

Surface Hub のリソース アカウント設定をリモートで構成することができるようになりました。

このリソース アカウントは、Skype または Exchange でミーティングに参加できるように認証する場合に Surface Hub で使用されます。
Surface Hub がミーティングで会議室として表示されるように、一意のリソース アカウントを作成できます。
たとえば、**会議室 B41/6233** のようなリソース アカウントです。

> [!NOTE]
> - フィールドを空白のままにすると、デバイスで以前に構成された属性がオーバーライドされます。
>
> - リソース アカウントのプロパティは、Surface Hub で動的に変更できます。 たとえば、パスワードのローテーションが有効かどうか、などです。 そのため、Azure コンソールの値が、デバイス上の現実に反映されるまでに時間がかかることがあります。
>
>   Surface Hub での現在の構成を理解するには、リソース アカウント情報をハードウェア インベントリ (既に 7 日間隔になっています) または読み取り専用プロパティに含めることができます。 リモート操作が行われた後の精度を向上させるには、操作実行直後にパラメーターの状態を取得し、Surface Hub のアカウント/パラメーターを更新できます。


##### <a name="attack-surface-reduction"></a>攻撃の回避


|設定の名前  |設定オプション  |説明  |
|---------|---------|---------|
|電子メールのパスワードで保護されている実行可能ファイルのコンテンツの実行|ブロック、監査、未構成|メールからのパスワードで保護されている実行可能ファイルのダウンロードを防止します。|
|Advanced ransomware protection (高度なランサムウェア防止)|有効、監査、未構成|積極的なランサムウェア防止を使います。|
|Flag credential stealing from the Windows local security authority subsystem (Windows ローカル セキュリティ機関サブシステムからの資格情報の盗難にフラグを設定する)|有効、監査、未構成|Windows ローカル セキュリティ機関サブシステム (lsass.exe) からの資格情報の盗難にフラグを設定します。|
|Process creation from PSExec and WMI commands (PSExec および WMI コマンドからのプロセス作成)|ブロック、監査、未構成|PSExec および WMI コマンドから開始されるプロセス作成をブロックします。|
|Untrusted and unsigned processes that run from USB (USB から実行された信頼されていない署名なしのプロセス)|ブロック、監査、未構成|USB から実行された信頼されていない署名なしのプロセスをブロックします。|
|Executables that don’t meet a prevalence, age, or trusted list criteria (普及、経過時間、または信頼されたリストの条件を満たしていない実行可能ファイル)|ブロック、監査、未構成|普及、経過時間、または信頼されたリストの条件を満たしていない実行可能ファイルの実行をブロックします。|

##### <a name="controlled-folder-access"></a>フォルダー アクセスの制御

|              設定の名前               |                                                              設定オプション                                                              | 説明 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| フォルダーの保護 (実装済み) | 未構成、有効、監査のみ (実装済み)<br><br> <strong>新規</strong><br>Block disk modification (ディスクの変更をブロックする)、Audit disk modification (ディスクの変更を監査する) |             |

ファイルおよびフォルダーを、悪意のあるアプリによる未承認の変更から保護します。<br><br>**有効**: 信頼されていないアプリによる、保護されたフォルダー内のファイルの変更または削除、およびディスク セクターへの書き込みを、禁止します。<br><br>
**Block disk modification only (ディスクの変更のみをブロック)**:<br>信頼されていないアプリによるディスク セクターへの書き込みをブロックします。 信頼されていないアプリは、保護されたフォルダー内のファイルを変更または削除することはできます。

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Windows 10 以降のコンプライアンス ポリシーのシステム セキュリティ設定への追加 <!--1704133-->

ファイアウォールと Windows Defender ウイルス対策の要求など、Windows 10 のコンプライアンス設定への追加機能が使用可能になりました。


### <a name="role-based-access-control"></a>ロールベースのアクセス制御
### <a name="intune-apps"></a>Intune アプリ
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>ビジネス向け Microsoft ストアから入手したオフライン アプリのサポート <!--1222672-->
ビジネス向け Microsoft ストアから購入したオフライン アプリが Azure Portal と同期されまるようになりました。 その後、これらのアプリをデバイス グループまたはユーザー グループに展開できます。 オフライン アプリは、ストアからではなく Intune でインストールします。

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>エンド ユーザーが作業プロファイルのアカウントを手動で追加または削除できないようにする <!-- 1728700 -->

Gmail アプリを Android for Work プロファイルに展開するとき、Android for Work デバイス制限プロファイルで **[Add and remove accounts]\(アカウントを追加および削除する\)** 設定を使うことで、エンド ユーザーが作業プロファイルのアカウントを手動で追加または削除できないようにすることができるようになりました。

## <a name="week-of-february-5-2018"></a>2018 年 2 月 5 日の週

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Apple の一括登録に対するユーザー認証の新しいオプション<!-- 747625 eeready -->

> [!NOTE]
> 新しいテナントでは、これは直ちに表示されます。 既存のテナントでは、この機能は 4 月にロールアウトされます。 このロールアウトが完了するまで、これらの新しい機能にアクセスできないことがあります。

Intune では現在、次の登録方法について、ポータル サイト アプリを使用してデバイスを認証できます。

- Apple Device Enrollment Program
- Apple School Manager
- Apple Configurator Enrollment

このポータル サイト オプションを使用すると、これらの登録方法をブロックすることなく、Azure Active Directory の多要素認証を強制できます。

このポータル サイト オプションを使用する場合、iOS 設定アシスタントでの、ユーザー アフィニティ登録用のユーザー認証がスキップされます。 つまり、このデバイスは、最初はユーザーのいないデバイスとして登録されるため、ユーザー グループの構成やポリシーは受信しません。 デバイス グループの構成とポリシーのみを受信します。 ただし、ポータル サイト アプリは自動的にデバイスにインストールされます。 ポータル サイト アプリを最初に起動してサインインするユーザーは、Intune でそのデバイスと関連付けられます。 この時点で、ユーザー グループの構成とポリシーが、このユーザーに送信されます。 ユーザーの関連付けを変更するには、再登録が必要です。

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>複数の Apple DEP および Apple School Manager アカウントに対する Intune サポート<!-- 747685 eeready -->

最大 100 個の異なる Apple Device Enrollment Program (DEP) または Apple School Manager アカウントからのデバイス登録が、Intune でサポートされます。 アップロードされる各トークンは、登録プロファイルとデバイスで、別々に管理できます。 アップロードされる DEP および School Manager のトークンごとに、異なる登録プロファイルを自動で割り当てることができます。 複数の School Manager トークンがアップロードされた場合、Microsoft 学校データ同期と共有できるのは、一度に 1 つのみです。

移行後、Graph で Apple DEP および ASM を管理するベータ版の Graph API と公開されたスクリプトは、動作しなくなります。 現在、新しいベータ版の Graph API の開発が進行中で、移行後にリリースされる予定です。

### <a name="remote-printing-over-a-secure-network----1709994----"></a>セキュリティで保護されたネットワークでのリモート印刷<!-- 1709994  -->
PrinterOn のワイヤレス モバイル印刷ソリューションは、時間や場所を問わない、セキュリティで保護されたネットワークでのリモート印刷を可能にします。 PrinterOn は、iOS 向けと Android 向けのどちらの Intune APP SDK とも統合します。 管理コンソールの Intune の **[アプリ保護ポリシー]** ブレードから、アプリ保護ポリシーのターゲットをこのアプリにすることもできます。 エンド ユーザーは、Play ストア、または iTunes から PrinterOn for Microsoft アプリをダウンロードして、Intune エコシステム内で使用できます。

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>デバイス登録マネージャーを使う登録の macOS ポータル サイトによるサポート <!-- 1352411 -->

ユーザーは、macOS ポータル サイトで登録するときに、デバイス登録マネージャーを使うことができるようになりました。

## <a name="week-of-january-29-2018"></a>2018 年 1 月 29 日の週

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>期限切れトークンと有効期限が近いトークンのアラート<!-- 1639263 -->
有効期限が切れているトークンと、有効期限が近づいているトークンのアラートが概要ページに表示されるようになりました。 1 つのトークンのアラートをクリックすると、そのトークンの詳細ページに移動します。  複数のトークンのアラートをクリックすると、トークンのステータスが表示された全トークンの一覧に移動します。 管理者は、有効期限が来る前にトークンを更新する必要があります。

### <a name="device-management"></a>デバイス管理

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>macOS デバイスのリモートの "消去" コマンド サポート <!-- 1438084 -->

管理者は、macOS デバイスの消去コマンドをリモートで発行できます。

> [!IMPORTANT]
> 消去コマンドは、元に戻すことができないため、使用する際は注意が必要です。

消去コマンドでは、オペレーティング システムを含むすべてのデータが、デバイスから削除されます。 また、そのデバイスも、Intune 管理から削除されます。 ユーザーに対して警告は表示されません。また、コマンドを発行すると、消去は即座に実行されます。

6 桁の回復用 PIN を構成する必要があります。 この PIN を使用すると、消去されたデバイスのロックが解除され、オペレーティング システムの再インストールが開始されます。 PIN は、消去が開始されると、Intune のデバイスの概要ブレードのステータス バーに表示されます。 消去が完了するまでの間、PIN はずっと表示されます。 消去が完了したら、デバイスは Intune 管理から完全に削除されます。 デバイスを復元する人が誰であっても、そのデバイスを使用できるように、回復用 PIN は必ず記録するようにしてください。

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>iOS Volume Purchasing Program トークンのライセンスの取り消し <!-- 820870 -->
特定の VPP トークンのすべての iOS Volume Purchasing Program (VPP) アプリのライセンスを取り消すことができます。

### <a name="app-management"></a>アプリ管理

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>iOS Volume-Purchase Program アプリの取り消し  <!-- 820863 -->
1 つ以上の iOS Volume-Purchase Program (VPP) アプリがインストールされた特定のデバイスでは、そのデバイスで関連付けられているデバイス ベース アプリのライセンスを取り消すことができます。 アプリのライセンスを取り消しても、関連する VPP アプリがデバイスからアンインストールされるわけではありません。 VPP アプリをアンインストールするには、割り当てアクションを **[アンインストール]** に変更する必要があります。 詳細については、「[Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法](vpp-apps-ios.md)」をご覧ください。

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>組み込み型のアプリを利用し、iOS デバイスまたは Android デバイスに Office 365 モバイル アプリを割り当てる <!-- 1332318 -->
**組み込み**型のアプリであれば、Office 365 アプリを作成し、管理している iOS または Android デバイスに割り当てることが簡単にできます。 これらのアプリには、Word、Excel、PowerPoint、OneDrive などの 0365 アプリがあります。 アプリの種類に特定のアプリを割り当て、アプリ情報構成を編集できます。

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>グループに基づくアプリ割り当ての追加と除外<!-- 1406920 -->

アプリの割り当て時、および割り当ての種類の選択後に、含めるグループと、除外するグループを選択できます。

### <a name="device-configuration"></a>デバイス構成

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>割り当てを含めたり除外したりしてグループにアプリケーション構成ポリシーを割り当てることができる <!-- 1480316 -->

含める割り当てと除外する割り当ての組み合わせを使って、ユーザーとデバイスのグループにアプリケーション構成ポリシーを割り当てることができます。 割り当ては、グループのカスタム選択または仮想グループとして選べます。 仮想グループは、**すべてのユーザー**、**すべてのデバイス**、または**すべてのユーザーとすべてのデバイス**を含むことができます。

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Windows 10 エディション アップグレード ポリシーのサポート <!-- 903672(archived), 1119689 -->  
Windows 10 デバイスを Windows 10 Education、Windows 10 Education N、Windows 10 Professional、Windows 10 Professional N、Windows 10 Professional Education、Windows 10 Professional Education N にアップグレードする Windows 10 エディション アップグレード ポリシーを作成できます。Windows 10 エディションのアップグレードについては、「[Windows 10 エディションのアップグレードを構成する方法](edition-upgrade-configure-windows-10.md)」をご覧ください。

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Intune の条件付きアクセス ポリシーの利用可能場所が Azure Portal のみに<!-- 1737088 1634311 -->

このリリース以降では、[Azure Portal](https://portal.azure.com) の **[Azure Active Directory]** > **[条件付きアクセス]** から条件付きアクセス ポリシーを構成および管理する必要があります。 便宜上、**[Intune]**  >  **[条件付きアクセス]** の、Azure Portal 内にある Intune からこのブレードにアクセスすることもできます。

#### <a name="updates-to-compliance-emails---1637547---"></a>コンプライアンスのメールに対する変更 <!--1637547 -->

コンプライアンス違反のデバイスを報告するメールが送信される際、そのコンプライアンス違反のデバイスの詳細が含まれるようになります。


## <a name="week-of-january-22-2018"></a>2018 年 1 月 22 日の週

### <a name="intune-apps"></a>Intune アプリ

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Android デバイスの "解決" アクションの新機能 <!--1583480-->

Android 用ポータル サイト アプリは、[デバイス暗号化の問題](/intune-user-help/encrypt-your-device-android)を解決するために、**[デバイス設定の更新]** の "解決" アクションを拡張しています。

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Windows 10 用の Intune ポータル サイトで利用できるリモート ロック <!--676506-->
エンドユーザーは、Windows 10 向けポータル サイト アプリから自分のデバイスをリモートでロックできるようになりました。 この機能はエンド ユーザーがアクティブに使用しているローカル デバイスには表示されません。

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Windows 10 でポータル サイト アプリのコンプライアンスの問題解決が簡単に<!--676546-->
Windows デバイスを持つエンド ユーザーは、ポータル サイト アプリのコンプライアンス非対応の理由をタップできます。 可能であれば、問題を解決するのに適切な、設定アプリ内の場所がエンド ユーザーに直接表示されます。

## <a name="week-of-december-11-2017"></a>2017 年 12 月 11 日の週

### <a name="device-configuration"></a>デバイス構成

#### <a name="new-automatic-redeployment-setting----1469168---"></a>新しい自動再配置設定 <!-- 1469168 -->
**自動再展開**設定では、管理権限を持つユーザーが、デバイス ロック画面で **CTRL + Win + R** を使用してすべてのユーザー データとユーザー設定を削除できます。 このデバイスは自動的に再構成され、管理対象に再登録されます。 この設定には、[Windows 10] -> [デバイスの制限] -> [全般] -> [自動再展開] でアクセスできます。 詳細については、[Intune での Windows 10 のデバイス制限設定](device-restrictions-windows-10.md#general)に関するページをご覧ください。

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Windows 10 エディションのアップグレード ポリシーにおける、その他のソース エディションのサポート<!-- 903672,  1119689 -->
Windows 10 エディションのアップグレード ポリシーを使用して、Windows 10 の他のエディション (Windows 10 Pro、Windows 10 Pro Education、Windows 10 Cloud など) からアップグレードできるようになりました。 以前のリリースでは、サポートされるエディションのアップグレードのパスは、今よりも限定されていました。 詳細については、[Windows 10 エディションのアップグレードを構成する方法](edition-upgrade-configure-windows-10.md)に関するページをご覧ください。

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>新しい Windows Defender セキュリティ センター (WDSC) デバイス構成プロファイルの設定 <!-- 1335507 -->

Intune の **Windows Defender セキュリティ センター**という名前の Endpoint Protection に、デバイス構成プロファイル設定の新しいセクションが追加されます。 IT 管理者は、Windows Defender セキュリティ センター アプリで、エンドユーザーがどの機能にアクセス可能かを構成できます。 IT 管理者が Windows Defender セキュリティ センター アプリで、ある機能を非表示にすると、ユーザーのデバイスで、その機能に関連するすべての通知が非表示になります。

管理者が Windows Defender セキュリティ センター デバイス構成プロファイル設定で非表示にできる機能は、以下のとおりです。
- ウイルスと脅威の防止
- デバイスのパフォーマンスと正常性
- ファイアウォールとネットワーク保護
- アプリとブラウザー コントロール
- ファミリー オプション

IT 管理者は、ユーザーが受け取る通知をカスタマイズすることもできます。 たとえば、ユーザーが WDSC に表示される機能で生成されたすべての通知を受け取るか、または重要な通知のみを受け取るかを構成できます。 重要度の低い通知には、Windows Defender Antivirus のアクティビティに関する定期的な概要や、スキャン完了時の通知があります。 その他のすべての通知は重要とみなされます。 さらに、通知の内容自体をカスタマイズすることもできます。たとえば、IT 担当の連絡先情報を、ユーザーのデバイスに表示される通知に組み込むなどです。

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>SCEP の複数コネクタ サポートと PFX 証明書処理 <!-- 1361755 -->

オンプレミス NDES コネクタを使用してデバイスに証明書を配信するお客様は、1 つのテナントに複数のコネクタを構成できるようになりました。

この新しい機能では、次のシナリオがサポートされています。

- **高可用性**

各 NDES コネクタは、Intune から証明書の要求を取得します。  1 つの NDES コネクタがオフラインになっても、その他のコネクタは要求の処理を続行できます。

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>カスタム サブジェクト名で AAD_DEVICE_ID 変数が使用可能に<!-- 1468599 -->

Intune で SCEP 証明書プロファイルを作成する際、カスタム サブジェクト名の作成時に AAD_DEVICE_ID 変数を使用できるようになりました。   この SCEP プロファイルを使用して証明書が要求されると、証明書の要求を行っているデバイスの AAD デバイス ID が、この変数に置き換わります。


### <a name="device-management"></a>デバイス管理

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Intune のデバイス コンプライアンス エンジンを使用した Jamf に登録された macOS デバイスの管理 <!-- 1592747 -->
Jamf を使って、macOS デバイスの状態情報を Intune に送信できるようになりました。情報はその後、Intune コンソールで定義されたポリシーに準拠しているかどうかが評価されます。 条件付きアクセスでは、デバイスのコンプライアンス対応状態や、その他の条件 (場所やユーザー リスクなど) に基づいて、Azure AD に接続されたクラウド アプリケーションやオンプレミス アプリケーション (Office 365 など) にアクセスする macOS デバイスにコンプライアンスを適用します。 [Jamf 統合の設定](conditional-access-integrate-jamf.md)と [Jamf で管理されたデバイスのコンプライアンスの強制](conditional-access-assign-jamf.md)について、詳細をご覧ください。

#### <a name="new-ios-device-action------1424701---"></a>新しい iOS デバイス アクション <!-- 1424701 -->

iOS 10.3 監視下のデバイスをシャット ダウンできるようになりました。 このアクションでは、エンド ユーザーへの警告なしにデバイスが即時シャットダウンされます。 **シャット ダウン (監視モードのみ)** アクションは、**デバイス** ワークロードでデバイスを選択した場合に、デバイス プロパティに表示されます。

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Samsung KNOX デバイスへの日付および時刻の変更禁止 <!-- 1468103 -->

Samsung KNOX デバイスでの日付と時刻の変更をブロックできる機能が新たに追加されました。 この機能は、**[デバイス構成プロファイル]** > **[デバイスの制限 (Android)]** > **[全般]** にあります。

#### <a name="surface-hub-resource-account-supported----1566442----"></a>サポートされる Surface Hub リソース アカウント <!-- 1566442  -->

Surface Hub に関連付けられたリソース アカウントを、管理者が定義、更新できる新しいデバイス アクションが追加されました。

このリソース アカウントは、Skype または Exchange でミーティングに参加できるように認証する場合に Surface Hub で使用されます。 Surface Hub がミーティングで会議室として表示されるように、一意のリソース アカウントを作成できます。 たとえば、リソース アカウントは*会議室 B41/6233* と表示されます。 Surface Hub のリソース アカウント (デバイス アカウントと呼ばれる) は通常、会議室の場所や、他のリソース アカウントのパラメーターをいつ変更するかを構成するのに必要となります。

管理者はデバイスでリソース アカウントを更新する場合、デバイスに関連付けられた現在の Active Directory または Azure Active Directory 資格情報を指定する必要があります。 デバイスでパスワードのローテーションがオンに設定されている場合には、管理者は Azure Active Directory に移動してパスワードを検索する必要があります。

> [!NOTE]
> すべてのフィールドがまとめて送信され、以前に構成されたすべてのフィールドを上書きします。 また、空のフィールドも既存のフィールドを上書きします。

管理者が行える構成は次のとおりです。

- **リソース アカウント**
   - **Active Directory ユーザー**

      Domainname\username、またはユーザー プリンシパル名: user@domainname.com

   - **パスワード**

- **オプションのリソース アカウント パラメーター** (指定されたリソース アカウントを使用して設定する必要があります)

   - **パスワードのローテーション期間**

     アカウントのパスワードは、セキュリティ上の理由から、毎週 Surface Hub によって自動的に更新されます。 これを有効にした後にパラメーターを構成するには、最初に Azure Active Directory のアカウントのパスワードをリセットする必要があります。

   - **SIP (セッション開始プロトコル) アドレス**

     自動検出が失敗した場合にのみ使用されます。

   - **電子メール**

     デバイス アカウントまたはリソース アカウントの電子メール アドレス。

   - **Exchange サーバー**

     自動検出が失敗した場合のみ必要です。

   - **予定表の同期**

     予定表の同期と他の Exchange サーバー サービスが有効かどうかを指定します。 たとえば、ミーティングの同期などです。

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>macOS デバイスでの Office アプリのインストール <!-- 1494311 -->
macOS デバイスで Office アプリをインストールできるようになりました。 この新しい種類のアプリでは、Word、Excel、PowerPoint、Outlook、OneNote をインストールできます。 これらのアプリには Microsoft AutoUpdate (MAU) も付属しており、アプリを安全かつ最新に保つことができます。

### <a name="app-management"></a>アプリ管理

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>iOS Volume Purchasing Program トークンのライセンスの削除 <!-- 820879 -->
コンソールを使用して、iOS Volume Purchasing Program (VPP) トークンを削除できます。 VPP トークンのインスタンスが重複している場合に、これが必要になることがあります。

### <a name="intune-apps"></a>Intune アプリ


### <a name="role-based-access-control"></a>ロールベースのアクセス制御

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>現在のユーザーという名前の新しいエンティティ コレクションは、現在アクティブなユーザー データに限られています <!-- 1667026 -->

**ユーザー** エンティティ コレクションには、社内のすべての Azure Active Directory (Azure AD) ユーザーと割り当てられているライセンスが表示されます。 たとえば、ユーザーが Intune に追加され、過去 1 か月の過程で削除されたとします。 このユーザーがレポートの時点では存在しない一方で、ユーザーと状態はデータに存在します。 データ内のユーザーの履歴における存在の期間を示すレポートを作成できます。

これに対し、新しい**現在のユーザー** エンティティ コレクションには、削除されていないユーザーのみが含まれています。 **現在のユーザー** エンティティ コレクションには、現在アクティブなユーザーのみが含まれています。 **現在のユーザー** エンティティ コレクションの詳細については、「[現在のユーザー エンティティのリファレンス](reports-ref-current-user.md)」をご覧ください。


### <a name="updated-graph-apis----1736360---"></a>Graph API の変更 <!-- 1736360 -->

このリリースでは、Intune のベータ版の Graph API にいくつか変更を加えました。 詳細については、[Graph API の変更ログ](https://developer.microsoft.com/graph/docs/concepts/changelog)のページ (毎月更新) をご覧ください。

## <a name="week-of-december-4-2017"></a>2017 年 12 月 4 日の週

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune では Windows Information Protection (WIP) で拒否されたアプリがサポートされる<!-- 1479103 -->
拒否されたアプリを Intune で指定することができます。 アプリが拒否された場合、企業の情報へのアクセスがブロックされます。これは事実上、許可されたアプリ リストの反対です。 詳しくは、[Windows 情報保護の推奨される拒否リスト](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection)を参照してください。



## <a name="notices"></a>通知

### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>アクションの実行: Intune でお使いの Android デバイスの制限またはコンプライアンス ポリシー パスワードの設定を更新してください。
Intune では、Android 4.4 以降のデバイスについて使用可能なパスワードの種類 "既定のデバイス" が削除されます。 Android プラットフォームと既定のデバイスの違いにより、そのポリシーはデバイスによってオプションとして扱われることがよくあります。 Android でこの設定が強制される場合についての混乱を解消するため、次回のリリースでこの設定を UI から削除します。 
#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
- デバイスでパスワードを要求することが望ましい場合は、"既定のデバイス" を使用する代わりに、Android プラットフォームのプロファイルを編集して、必要なパスワードの種類を明確に示すことをお勧めします。
- パスワードを作成するかどうかをエンド ユーザーに決定させることが望ましい場合は、[未構成] ボタンを選択します。 UI からこの設定が削除される時点で、設定がまだ有効になっていた場合は、次にプロファイルを編集するときに、[既定のデバイス] 以外の値を選択するよう求められます。
この変更に対して必要な準備
お使いの Android および Android エンタープライズ デバイスの制限とコンプライアンスのポリシーで、パスワードの設定を確認します。 これらの設定は、コンプライアンスのためのシステム セキュリティ ポリシー、およびデバイスの制限に関するデバイスのパスワードまたは作業プロファイルの設定にあります。 追加情報には、詳細情報およびこれらの設定の構成画面のスクリーンショットへのリンクがあります。
####<a name="additional-information"></a>追加情報
https://aka.ms/PasswordSettings 

### <a name="plan-for-change-change-password-at-next-auth-added-to-intune---1873216---"></a>変更の計画: [次回の認証でパスワードを変更する] 設定を Intune に追加する <!-- 1873216 -->
9 月のサービス リリースで、Intune では、macOS バージョン 10.13 以降を実行しているデバイスについて、Apple が新しく公開した **[次回の認証でパスワードを変更する]** 設定を統合する予定です。 この設定の導入前は、MDM プロバイダーは、デバイスのパスコードがポリシーに準拠するように変更されたことを確認できませんでした。 Intune の構成とコンプライアンスのポリシーでは、次回デバイスのパスワードが変更されること、それがポリシー準拠として見なされることのみを検証されます。 Apple のこの新しい機能が追加されると、macOS ユーザーには、パスワードがポリシーに準拠していても更新するように要求が届きます。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
Intune またはハイブリッド MDM を使用している macOS デバイス ポリシーの環境に影響が出ます。 今回、Apple が **[次回の認証でパスワードを変更する]** 設定を備えたことで、Intune では、パスワード ポリシーがプッシュされたときにパスワードを更新するようにユーザーに強制できます。 デバイスがポリシー準拠であると見なされるまで会社のリソースをブロックすると、エンド ユーザーは自分のパスワードをリセットするまで、電子メールや SharePoint サイトなど、会社のリソースにアクセスできなくなる可能性があります。 今後、構成とコンプライアンスのパスワード ポリシーが更新されるたびに、対象となるユーザーには自分のパスワードの更新が強制されます。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
ヘルプデスクにお知らせください。 この macOS デバイス ポリシーを強制しない場合、既存の macOS ポリシーの割り当てを解除すること、あるいは削除さすることをお勧めします。 顧客調査により、ほとんどの顧客がこの変更の影響を受けないことが示されています。 ほとんどのエンド ユーザーはパスワードの登録要求またはリセット要求が届くと自分のパスワードを更新し、ポリシー準拠の状態を維持します。


### <a name="plan-for-change-intune-moving-to-support-ios-10-and-later-in-september----2454656---"></a>変更の計画: Intune は 9 月に iOS 10 以降をサポートするようになります<!-- 2454656 -->
9 月に Apple は iOS 12 をリリースする予定です。 このリリース直後に、Microsoft では iOS 10 以降をサポートするように Intune の登録、ポータル サイト、および Managed Browser を移行します。  

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響  
Office 365 モバイル アプリは iOS 10 以降でサポートされているため、ご利用の OS またはデバイスは既にアップグレードされている可能性があります。 その場合、この移行の影響はありません。  

ただし、以下に一覧したデバイスのいずれかを所有している場合、または以下に一覧したデバイスのいずれかを登録する場合、それらのデバイスは iOS 9 以前しかサポートしていないので注意してください。  Intune ポータル サイトに引き続きアクセスするには、それらのデバイスを 9 月までに iOS 10 以降をサポートするデバイスにアップグレードする必要があります。  

* iPhone 4S  
* iPod Touch  
* iPad 2  
* iPad (第 3 世代)  
* iPad Mini (第 1 世代)  

7 月以降、iOS 9 とポータル サイトの両方が使用されている MDM 登録デバイスには、OS またはデバイスのアップグレードを求めるメッセージが表示されます。 アプリ保護ポリシーを使用する場合は、[iOS オペレーティング システムの最小要件 (警告のみ)] アクセス設定を設定することもできます。  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備   
組織内で影響を受けるデバイスまたはユーザーが存在しないか確認します。 Azure portal の Intune で、[デバイス]、[すべてのデバイス]、[OS でフィルター処理] の順に進みます。  [列] をクリックして、OS バージョンなどの詳細を表示します。 使用しているデバイスを 9 月までに、サポートされている OS バージョンにアップグレードするようにユーザーに依頼します。  

### <a name="plan-for-change-intune-moving-to-tls-12"></a>変更の計画: Intune の TLS 1.2 への移行
2018 年 10 月 31 日以降、Intune では、サービスが既定でより安全であることを保障するため、また Microsoft Office 365 などの他の Microsoft 製品と並んでクラス最高の暗号化を提供できるよう、トランスポート層セキュリティ (TLS) プロトコル バージョン 1.2 をサポートするようになりました。 Office では、この変更を MC128929 でご連絡しています。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
2018 年 10 月 31 日以降、Intune では TLS プロトコル バージョン 1.0 または 1.1 はサポートしなくなります。 問題なく Intune に接続できるようにするには、すべてのクライアントとサーバー、およびブラウザーとサーバーの組み合わせで、接続を確保するために TLS バージョン 1.2 を使用する必要があります。 これらの変更は Intune ではサポートされていないが、引き続き Intune からポリシーを受け取っていて TLS バージョン 1.2 を使用できないエンド ユーザー デバイスには影響することに注意してください。 これには、Android 4.3 以前を実行するデバイスも含まれます。 影響を受けるデバイスやブラウザーの一覧については、以下の「追加情報」を参照してください。

2018 年 10 月 31 日以降、古い TLS のバージョンの使用に関連した問題が発生する場合、解決策の一環として TLS 1.2 に更新するか、TLS 1.2 をサポートするデバイスに更新する必要があります。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
環境から TLS 1.0 と 1.1 の依存関係を積極的に削除し、可能な場合にはオペレーティング システム レベルで TLS 1.0 と 1.1 を無効にすることをお勧めします。 今日、TLS 1.2 への移行を計画しましょう。 現在 Intune ではサポートされていないが、ポリシーを依然受け取っていて、TLS バージョン 1.2 では通信できないデバイス一覧を以下のサポートのブログ投稿で確認してください。 会社のリソースにアクセスできなくなることを、エンド ユーザーに通知する必要がある場合があります。

**追加情報**: [Intune moving to TLS 1.2 for encryption](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/) (Intune の暗号化の TLS 1.2 への移行)


### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>変更計画: Microsoft Intune App SDK for Cordova プラグインのサポートでの変更
Intune による [Microsoft Intune App SDK Cordova プラグイン](app-sdk-cordova.md)のサポートは、2018 年 5 月 1 日で終了します。 代わりに Intune アプリ ラッピング ツールを使って、Cordova ベースのアプリの Intune での管理性と可用性の準備をすることをお勧めします。 この変更が有効になると、Microsoft Intune APP SDK for Cordova プラグインは保守されたり更新プログラムを受け取ったりしなくなります。 アプリ開発者はこのプラグインを使えなくなります。 Intune は、Cordova でのアプリ構築のサポートを続ける予定です。 ただし、Microsoft Intune APP SDK for Cordova プラグインを使って作成されたアプリは、Intune での機能が制限されるようになります。 Intune アプリ ラッピング ツールでラップした後は、通常どおりにアプリをエンド ユーザーに展開できます。 Google Play Store にリリースされた Cordova ベースの Android アプリの場合:
- エンド ユーザーは、初めて起動するときに Intune ポリシーを受け取るために資格情報を求められます。
- アプリは、Intune ユーザーが対象のアプリ ストアにリリースされる必要があります ("Contoso App for Intune" など)。

アプリ ラッピング ツールについては、[iOS 用アプリ ラッピング ツール](app-wrapper-prepare-ios.md)および [Android 用アプリ ラッピング ツール](app-wrapper-prepare-android.md)に関する説明をご覧ください。 問題または質問がある場合は、[msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com) にお問い合わせください。

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>変更の計画: MDM 管理に今すぐ Azure で Intune を使用する <!-- 1227338 -->
1 年以上前、[Azure の Intune のパブリック プレビュー](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/)を発表し、その後、6 か月前に Intune の[新しい管理者エクスペリエンスを一般公開](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/)しました。 Intune スタンドアロンをご利用の場合、2018 年 8 月 31 日以降、従来の Silverlight コンソールではモバイル デバイス管理 (MDM) を使用できなくなります。 MDM が必要な場合は、代わりに [Azure 上の Intune](https://aka.ms/Intune_on_Azure) を使用できます。 まだ MDM に従来のコンソールを使用している場合は、使用を止め、Azure 上の Intune に慣れてください。 この変更によるエンド ユーザーへの影響はない予定です。 従来の PC 管理は Silverlight に残ります。 この変更とその影響については、[こちら](https://aka.ms/Intune_on_Azure_mdm)を参照してください。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->
Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure Portal の Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューは Intune クラシック ポータルのリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントで Azure Portal にアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。

## <a name="whats-coming"></a>今後の更新情報

### <a name="local-device-security-option-settings----1251887---"></a>ローカル デバイス セキュリティ オプションの設定 <!-- 1251887 -->
新しいローカル デバイス セキュリティ オプションの設定を使って、Windows 10 デバイスのセキュリティ設定を有効にできます。 これらの設定は、Windows 10 デバイスの構成ポリシーを作成するときに、[Endpoint Protection] カテゴリに表示されます。

### <a name="new-user-experience-update-for-the-company-portal-website---2000968--"></a>ポータル Web サイトの新しいユーザー エクスペリエンスの更新<!--2000968-->

UI の更新、ワークフローの簡素化、ユーザー補助機能の改善を備えた新しいポータル Web サイトのエクスペリエンスを、8 月から導入します。 これには、アプリ共有などのお客様の要望に基づいた機能拡張や、よりユーザー フレンドリなエクスペリエンスを提供するための全体的なパフォーマンスの向上などが含まれます。
お客様からのフィードバックに基づいて、既存の機能と使いやすさを大幅に向上させる新しい機能もいくつか追加されています。

* Web サイト全体の UI の機能強化
* アプリへの直接リンクを共有する機能
* 大規模なアプリケーション カタログのパフォーマンスの向上

この変更の準備のために何かを行う必要はありません。 更新されたポータル Web サイトが利用可能になったら、お知らせいたします。 ただし、最終的には、更新されたスクリーンショットを使用して、エンド ユーザーのドキュメントを更新する必要があります。 また、Web サイトは iOS アプリの **[アプリ]** セクションに影響するため、iOS のポータル サイト アプリのドキュメントも更新する必要があることに注意してください。 このサンプル イメージは、[アプリ UI の新機能](whats-new-app-ui.md)のページでご覧になれます。

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->
Apple は、Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。 詳細については、[Intune サポート ブログ](https://aka.ms/compportalats)を参照してください。



## <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](https://www.microsoft.com/cloud-platform/roadmap)
* [ポータル Web サイトの UI の新機能](whats-new-app-ui.md)
* [以前の月の新機能](whats-new-archive.md)
