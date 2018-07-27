---
title: 初期エディション
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3aed8fcefd640e5b7df46fe1ef8cd1c973a68044
ms.sourcegitcommit: 5251a630fb2c7a2e6f86abd84ab887f8eabc1481
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2018
ms.locfileid: "39212139"
---
# <a name="the-early-edition-for-microsoft-intune---july-2018"></a>Microsoft Intune の初期エディション - 2018 年 7 月

> [!Note]
> NDA 通知: Intune に関して、以下の機能が現在開発されています。 この情報は、NDA に基づき、非常に限られた範囲で共有されます。 Twitter、UserVoice、Reddit などの、ソーシャル メディアやパブリック Web サイトには、この情報を投稿しないでください。 

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている、NDA に基づいて共有される新機能のリストを提供します。 ここに記載されている情報は、限られた範囲について開示されたものであり、また今後変更される可能性があります。 ツイート、UserVoice への投稿、またそれ以外の方法で、社外でこの情報を共有したりしないでください。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Microsoft 製品グループにお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune

<!-- 1807 start -->

### <a name="more-sync-opportunities-in-the-company-portal-app-for-windows----2683177---"></a>Windows 用ポータル サイト アプリ内の同期の機会の増加 <!-- 2683177 -->
Windows 用ポータル サイト アプリでは、Windows タスク バーと [スタート] メニューのジャンプ リストにデバイスの同期アクションを追加しています。 いずれの場所からクリックしても、デバイスをすばやく同期して企業リソースにアクセスすることができます。  

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Windows 10 用ポータル サイト アプリからデバイスのパスコードをリセットする <!-- 2101282 --> 
従業員の方々は、すぐに Windows 10 用ポータル サイト アプリから直接デバイスの PIN またはパスコードをリセットできるようになります。 この機能は、パスコードのリセットをサポートする、リモートとローカルの Intune で管理されている両方のデバイスで使用できます。 デバイスの種類に応じて、リモート デバイスに対して行われた要求では、デバイスの現在のパスコードが削除されるか、一時的なパスコードが作成されます。 ローカル デバイスのリセットを要求するユーザーは、デバイスの設定アプリにリダイレクトされます。  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>Windows 用ポータル サイト アプリでの新しい参照エクスペリエンス <!-- 2317227 -->  
Windows 用ポータル サイト アプリでアプリを参照または検索するときに、既存の **[タイル]** ビューと新しく追加された **[詳細]** ビューを切り替えることができます。 新しいビューには、名前、発行元、発行日、インストール状態などのアプリケーションの詳細が一覧表示されます。  

**[アプリ]** ページは、**[インストール済み]** ビューに追加されます。ここでは、完了済みと進行中のアプリのインストールに関する詳細を確認できます。 新しい変更についてフィードバックまたはご意見を共有してください ポータル サイト アプリからフィードバックをお寄せください。

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>デバイス登録マネージャ ユーザー向けのポータル サイト アプリの操作性の改善<!-- 675800 -->
デバイス登録マネージャ (DEM) が Windows 用ポータル サイト アプリにサインインすると、アプリには DEM の現在 (実行中のデバイス) のみが一覧表示されます。 この改善により、DEM に登録されたデバイスをすべて読み込もうとしたときに以前に発生していたタイムアウトが削減されます。  

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>S/MIME を使用して暗号化し、ユーザーの複数のデバイスに署名する <!-- 1333642 -->
今後の更新には、新しくインポートされる証明書プロファイル (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]**、該当するプラットフォーム、**[PKCS のインポートされた証明書]** プロファイルの種類の順に選択) を使用する S/MIME メールの暗号化が含まれます。 Intune では、PFX 形式で証明書をインポートできます。 その後、Intune はその同じ証明書を、単一ユーザーによって登録された複数のデバイスに配信できます。 これには、次のものも含まれます。

- ネイティブ iOS メール プロファイルでは、PFX 形式でインポートされた証明書を使用する S/MIME 暗号化を有効にすることができます。
- Windows Phone 10 デバイス上のネイティブ メール アプリでは、自動的に S/MIME 証明書が使用されます。
- プライベート証明書は複数のプラットフォームに配信できます。 しかし、すべてのメール アプリで S/MIME がサポートされるわけではありません。
- 他のプラットフォームでは、S/MIME を有効にするようにメール アプリを手動で構成する必要がある場合があります。  
- S/MIME 暗号化をサポートするメール アプリでは、発行元の証明書ストアからの読み取りなど、MDM ではサポートできない方法で S/MIME メール暗号化のための証明書の検索を処理する場合があります。

サポート対象: Windows、Windows Phone 10、macOS、iOS、Android

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>VPP デバイス ライセンスを使用して DEP 登録時にポータル サイトを事前プロビジョニングする <!-- 1608345 -->
Volume Purchase Program (VPP) デバイス ライセンスを使用して、Device Enrollment Program (DEP) 登録時にポータル サイトを事前プロビジョニングすることができます。 そのためには、登録プロファイルの作成または編集時に、ポータル サイトをインストールするために使用する VPP トークンを指定します。 トークンの期限が切れていないことと、ポータル サイト アプリの十分なライセンスがあることを確認してください。 トークンの期限が切れているか、ライセンスが不足している場合、Intune は代わりに App Store ポータル サイトをプッシュします (この場合、Apple ID の入力が求められます)。

### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>デバイス ブレードでのデバイスの一括削除 <!-- 1793693 -->
[デバイス] ブレードでは、一度に複数のデバイスを削除することができます。 **[デバイス]** > **[すべてのデバイス]**、削除するデバイス、**[削除]** の順に選択します。 削除できないデバイスについては、アラートが表示されます。

### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Windows 10 以降用の新しい Wi-Fi デバイス構成プロファイル <!-- 1879077 -->
現時点では、XML ファイルを使用して、Wi-Fi プロファイルをインポートおよびエクスポートすることができます。 他のプラットフォームの場合と同じように、Intune で直接 Wi-Fi デバイス構成プロファイルを作成できるようになります。

プロファイルを作成するには、**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[Windows 10 以降]** > **[Wi-Fi]** の順に開きます。 

Windows 10 以降に適用されます。

###  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Windows 基幹業務 (LOB) アプリのファイル拡張子 <!-- 1884873 -->
Windows LOB アプリのファイル拡張子に、*.msi*、*.appx*、*.appxbundle*、*.msix* および *.msixbundle* が含まれるようになりました。 Microsoft Intune にアプリを追加するには、**[モバイル アプリ]** > **[アプリ]** > **[追加]** の順に選択します。 **[アプリの追加]** ウィンドウが表示され、そこで **[アプリの種類]** を選択できます。 Windows LOB アプリの場合は、アプリの種類として **[基幹業務]** アプリを選び、**[アプリのパッケージ ファイル]** を選択して、適切な拡張子を持つインストール ファイルを入力します。

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>構成プロファイルに自動的に追加される Windows Defender ATP 構成パッケージ <!-- 2144658 -->
Intune で [Advanced Threat Protection を使用してデバイスをオンボードする](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile)場合、現時点では、構成パッケージをダウンロードし、それを構成プロファイルに追加します。 今後の更新では、Intune で Windows Defender セキュリティ センターからパッケージを自動的に取得し、それをプロファイルに追加します。

Windows 10 以降に適用されます。

### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>[Kiosk - obsolete]\(キオスク - 古い) が灰色で表示され、変更できない <!-- 2149998 -->
[キオスクの機能](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[Windows 10 以降]** > **[デバイスの制限]**) は使用されなくなり、[Windows 10 以降用のキオスク設定](kiosk-settings.md)に置き換えられます。 **[Kiosk - Obsolete]\(キオスク - 古い)** 機能は灰色で表示されるようになり、ユーザー インターフェイスの変更や更新はできません。 

キオスク モードを有効にする場合は、[Windows 10 以降用のキオスクの設定](kiosk-settings.md)に関するページを参照してください。

Windows 10 以降、Windows Holographic for Business に適用されます

### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>サード パーティ証明機関を使用する API <!-- 2184013 -->
Java API でサード パーティ証明機関を使用して、Intune と SCEP を統合できるようになります。 その後、ユーザーは SCEP 証明書をプロファイルに追加し、MDM を使用してデバイスに適用できます。

現時点では、Intune で [Active Directory 証明書サービスを使用する SCEP 要求](certificates-scep-configure.md)がサポートされています。

### <a name="check-for-sccm-compliance----2192052---"></a>SCCM コンプライアンスの確認 <!-- 2192052 -->
今後の更新には、新しい System Center Configuration Manager (SCCM) コンプライアンス設定 (**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[Windows 10]**) が含まれます。 SCCM は Intune コンプライアンスにシグナルを送信します。 Intune の設定を使用して、すべての SCCM シグナルで "準拠" を返すように要求することができます。

たとえば、すべてのソフトウェア更新プログラムをデバイスにインストールすることを要求します。 SCCM では、この要求は "インストール済み" 状態となります。 デバイス上のプログラムが不明な状態である場合、Intune ではデバイスが非準拠となります。

Windows 10 以降に適用されます

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP トークンの期限が切れているか、ポータル サイトのライセンスが不足している場合のアラート <!-- 2237572 -->
Volume Purchase Program (VPP) を使用して、DEP 登録時にポータル サイトを事前プロビジョニングする場合、Intune では、VPP トークンの有効期限が近づいている場合やポータル サイトのライセンスが不足している場合にアラートが表示されます。

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>ポータル サイトの事前プロビジョニングに使用されている VPP トークンを削除するために必要な構成 <!-- 2237634 -->
DEP 登録時にポータル サイトの事前プロビジョニングに Volume Purchase Program (VPP) トークンが使用されている場合、そのトークンを削除するための構成が必要になります。

### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Samsung Knox Mobile Enrollment を使用して登録された Android デバイスを自動的に "企業" としてマークする <!-- 2404851 -->
既定で、Samsung Knox Mobile Enrollment を使用して登録された Android デバイスは、**[デバイスの所有権]** に**企業**としてマークされるようになります。 Knox Mobile Enrollment を使用して登録する前に、IMEI やシリアル番号を使って企業のデバイスを手動で特定する必要はなくなります。

### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>キオスク ブラウザーで [セッションの終了] ボタンの表示と非表示を切り替える <!-- 2455253 -->
キオスク ブラウザーに [セッションの終了] ボタンを表示するかどうかを構成できるようになります。 コントロールは **[デバイス構成]** > **[キオスク (プレビュー)]** > **[キオスク Web ブラウザー]** で表示できます。 有効にした場合、ユーザーがボタンをクリックしたときに、アプリでセッションを終了するための構成が求められます。 確認すると、ブラウザーで閲覧データがすべてクリアされ、既定の URL に戻ります。

### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>eSIM 携帯電話の構成プロファイルの作成 <!-- 2564077 -->
**[デバイス構成]** で、eSIM 携帯電話のプロファイルを作成できるようになります。 携帯電話会社によって提供される携帯電話のアクティブ化コードを含むファイルをインポートできます。 その後、これらのプロファイルを、Surface Pro LTE やその他の eSIM 対応デバイスなど、eSIM LTE を有効にした Windows 10 デバイスに展開することができます。

ご利用の[デバイスで eSIM プロファイルがサポートされている](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)かどうかを確認してください。

Windows 10 以降に適用されます。 




<!-- 1806 start -->


### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS でのアプリ設定によりサード パーティ製キーボードをブロックできる <!-- 1248481 -->
Intune 管理者は、iOS デバイスで、ポリシーによって保護されているアプリ内の組織データにアクセスするときのサード パーティ製キーボードの使用をブロックすることができます。 サード パーティ製キーボードをブロックするようにアプリケーション保護ポリシー (APP) が設定されていると、デバイス ユーザーは、サード パーティ製キーボードを使って初めて企業データを操作するときに、メッセージを受け取ります。 ネイティブ キーボード以外のすべてのオプションはブロックされ、デバイスのユーザーに表示されません。 デバイス ユーザーにこのダイアログ メッセージが表示されるのは 1 回だけです。 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>macOS デバイスでファイアウォール設定を使ってデバイスのコンプライアンス ポリシーを作成する <!-- 1497640 -->
macOS の新しいコンプライアンス ポリシーを作成するとき (**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[プラットフォーム: macOS]** > **[システム セキュリティ]**)、**ファイアウォール**に関するいくつかの新しい設定を使用できます。 
- **[ファイアウォール]**: ご利用の環境における着信接続の処理方法を構成します。
- **[着信接続]**: DHCP、Bonjour、IPSec など、基本的なインターネット サービスに必要な接続を除き、すべての着信接続を **[ブロック]** します。 この設定は、すべての共有サービスもブロックします。
- **[ステルス モード]**: ステルス モードを **[有効]** にして、デバイスがプローブ要求に応答するのを防ぎます。 デバイスは引き続き、許可されているアプリに関する着信要求に応答します。

適用対象: macOS 10.12 以降

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>アプリの起動時とタイムアウト時に生体認証ではないパスコードを要求する <!-- 1506985 -->

アプリの起動時と管理者指定のタイムアウト後に生体認証以外のパスコードを要求することにより、Intune は、企業データ アクセス用の生体認証 ID の使用を制限することで、モバイル アプリケーション管理 (MAM) が有効になっているアプリのセキュリティを強化します。 この設定は、Touch ID (iOS)、Face ID (iOS)、Android バイオメトリック、またはその他の将来の生体認証方法に依存して APP/MAM が有効なアプリケーションにアクセスするユーザーに影響します。 これらの設定により、Intune 管理者は、ユーザー アクセスをいっそうきめ細かく制御し、複数のフィンガープリントまたは他の生体認証アクセス方法を使うデバイスによって不適切なユーザーに会社のデータが公開されるのを防ぐことができます。 Azure Portal で **Microsoft Intune** を開きます。 **[モバイル アプリ]** > **[アプリ保護ポリシー]** > **[ポリシーの追加]** > **[設定]** の順に選びます。 特定の設定の **[アクセス]** セクションを探します。

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 言語パック <!-- 1833450 -->
Intune 管理者は、Intune によって管理されている Office 365 Pro Plus アプリに追加の言語を展開することができます。 使用可能な言語のリストには、言語パックの **種類** (コア、部分、校正) が含まれます。 Azure Portal で、**[Microsoft Intune]** > **[モバイル アプリ]** > **[アプリ]** > **[追加]** の順に選びます。 **[アプリの追加]** ブレードの **[アプリの種類]** 一覧で、**[Office 365 スイート]** の **[Windows 10]** を選びます。 **[アプリ スイートの設定]** ブレードで **[言語]** を選びます。

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>ポータル Web サイトの新しいユーザー エクスペリエンスの更新をプレビューする <!--2000968 -->
お客様からのフィードバックに基づいて、ポータル Web サイト/iOS アプリ カタログに新機能が追加されています。 Android、iOS、Windows デバイスから、既存の機能と使いやすさの大幅な向上を体験できます。 デバイス詳細、フィードバックとサポート、デバイス概要などのサイトの領域には、最新の応答性の高いデザインが採用されています。 また、次のような更新が行われています。

- すべてのデバイス プラットフォームでの簡素化されたワークフロー
- 強化されたデバイスの識別と登録のフロー
- 役に立つエラー メッセージ
- わかりやすい言語、少ない技術用語
- アプリへの直接リンクを共有する機能
- 大規模なアプリケーション カタログのパフォーマンスの向上
- すべてのユーザーに対するアクセシビリティの向上

更新は現在、プレビュー段階です。 http://aka.ms/webcpflighting でプレビューに参加するために登録することができます


### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Office 365 Pro Plus アプリの展開を編集する <!-- 2150145 -->
Microsoft Intune 管理者は、さらに向上した Office 365 Pro Plus アプリの展開の編集機能を使用できるようになります。 Azure Portal で、**[Microsoft Intune]** > **[モバイル アプリ]** > **[アプリ]** の順に選びます。 アプリの一覧から、Office 365 Pro Plus スイートを選択します。  

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>コールド アプリ起動時とタイムアウト時に生体認証ではないパスコードを要求する <!-- 1506985 --> 

コールド アプリ起動時と管理者指定のタイムアウト後に生体認証以外のパスコードを要求することにより、Intune は、企業データ アクセス用の生体認証 ID の使用を制限することで、モバイル アプリケーション管理 (MAM) が有効になっているアプリのセキュリティを強化します。 この設定は、Touch ID (iOS)、Face ID (iOS)、Android バイオメトリック、またはその他の将来の生体認証方法に依存して APP/MAM が有効なアプリケーションにアクセスするユーザーに影響します。 これらの設定により、Intune 管理者は、ユーザー アクセスをいっそうきめ細かく制御し、複数のフィンガープリントまたは他の生体認証アクセス方法を使うデバイスによって不適切なユーザーに会社のデータが公開されるのを防ぐことができます。 Azure Portal で **Microsoft Intune** を開きます。 **[モバイル アプリ]** > **[アプリ保護ポリシー]** > **[ポリシーの追加]** > **[設定]** の順に選びます。 特定の設定の **[アクセス]** セクションを探します。

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>未承認のデバイス ベンダーとモデルに基づくアプリのアクセスのブロック <!-- 1425689 ! -->
Intune の IT 管理者は、Intune App Protection ポリシーによって、Android 製造元や iOS モデルの指定された一覧を適用できます。 IT 管理者は、Android ポリシーの製造元と iOS ポリシーのデバイス モデルのセミコロン区切り一覧を提供できます。 Intune App Protection ポリシーは、Android および iOS 専用です。 この指定されたリストでは 2 つの個別操作を実行できます。
- 指定されていないデバイスでのアプリ アクセスからブロック。
- または、指定されていないデバイスでの企業データの選択的ワイプ。 

ユーザーは、ポリシーによる要件が満たされない場合、対象となるアプリケーションにアクセスすることができません。 設定に基づいて、ユーザーは、ブロックされるか、アプリ内の企業データを選択的にワイプされます。 iOS デバイスのこの機能で、最低バージョンの設定を対象アプリケーションに適用するには、アプリケーション (つまり、 WXP、Outlook、Managed Browser、Yammer) が参加して、Intune APP SDK を統合する必要があります。 この統合は、ローリング方式で行われ、特定のアプリケーション チームによって異なります。 Android でこの機能を利用するには、最新の Intune ポータル サイトが必要です。 

エンド ユーザー デバイスの Intune クライアントは、アプリケーション保護ポリシーに対して Intune ブレードで指定されている文字列の単純一致に基づいてアクションを実行します。 これは、デバイスを報告する値に完全に依存します。 そのため、IT 管理者には、意図した動作が正確であることを確認することをお勧めします。 これは、小さなユーザー グループを対象に、さまざまなデバイス製造元とモデルに基づいてこの設定をテストすることによって実現できます。 Microsoft Intune でアプリ保護ポリシーを表示および追加するには、**[Mobile Apps]** > **[アプリ保護ポリシー]** を選びます。 アプリ保護ポリシーについて詳しくは、「[アプリ保護ポリシーとは](app-protection-policy.md)」をご覧ください。


<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Windows 10 デスクトップ デバイスのすべてのユーザーに対して必要な基幹業務 (LOB) アプリを展開する機能 <!-- 1627835 RS4 -->
お客様は、必要な基幹業務 Windows 10 アプリを展開してデバイス コンテキストにインストールできるようになります。 これにより、デバイスのすべてのユーザーがこれらのアプリを使用できるようになります。 対象は Windows 10 デスクトップ デバイスだけです。

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Android 用 Intune ポータル サイト アプリでのヘルプとフィードバックのエクスペリエンスの更新 <!--1631531 -->

Android アプリのベスト プラクティスに合うように、Android 用 Intune ポータル サイト アプリのヘルプとフィードバックのエクスペリエンスが更新されます。 今後数か月かけて Android 用 Intune ポータル サイト アプリが更新され、**[ヘルプとフィードバック]** メニュー項目が **[ヘルプ]** と **[フィードバックの送信]** の異なるメニュー項目に分割されます。 **[ヘルプ]** ページには **[よく寄せられる質問]** セクションと **[メールでサポートに問い合わせる]** ボタンがあり、エンド ユーザーは Microsoft にログをアップロードしたり、会社のサポート部門に問題を説明するメールを送信したりできます。 **[フィードバックの送信]** では Microsoft の標準的なフィードバック送信を利用でき、"気に入った機能"、"気に入らない機能"、"アイデア" を選択できます。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>アプリ保護ポリシー  <!-- 679615 -->
Intune App Protection ポリシーは、既定のグローバル ポリシーを作成し、テナント全体のすべてのユーザーに保護をすばやく適用する機能を提供します。

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

現在のところ、アクティブな通知はありません。

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
