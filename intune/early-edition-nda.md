---
title: 初期エディション
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 606005c3d8abafe989b35841cebf8c11e1f6b04e
ms.sourcegitcommit: f69f2663ebdd9c1def68423e8eadf30f86575f7e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2018
ms.locfileid: "49075882"
---
# <a name="the-early-edition-for-microsoft-intune---october-2018"></a>Microsoft Intune の初期エディション - 2018 年 10 月

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

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>セキュリティ ベースラインに対して Microsoft 推奨の設定を使用する<!-- 2055484 -->
Intune は、セキュリティに的を絞ったその他のサービス (Windows Defender ATP や Office 365 ATP など) と統合されます。 一般的な戦略と、Microsoft 365 サービス間での結束的なエンドツーエンドのセキュリティ ワークフローをお客様から求められています。 目標としているのは、セキュリティの運用と一般的な管理者タスクをブリッジするソリューションを構築できるように戦略を調整することにあります。 Intune では、Microsoft が推奨する一連の "セキュリティ ベースライン" を公開することによって、この目標の達成を目指しています (**[Intune]** > **セキュリティ ベースライン**)。  管理者はこれらのベースラインからセキュリティ ポリシーを直接作成し、それをユーザーに展開することができるようになります。 それらのユーザーは、組織のニーズに合わせてベスト プラクティスの推奨事項をカスタマイズすることもできます。 Intune では、これらのベースラインにデバイスが準拠した状態に維持されていることが確認され、管理者には準拠した状態にないユーザーまたはデバイスが通知されます。

### <a name="remove-ability-for-admins-to-wipe-personal-devices-and-reset-passcodes----2934699---"></a>個人のデバイスをワイプしてパスコードをリセットする管理者機能を削除する<!-- 2934699 -->
会社の管理者が個人デバイスをワイプできることについてユーザー抱いている懸念を緩和するために、[ワイプ](devices-wipe.md#wipe)および[パスコードのリセット](device-passcode-reset.md)リモート操作は、個人デバイスに適用されなくなります。 ユーザーはポータル Web サイトを使用して任意のデバイスから自分のパスコードのリセットおよび自分のデバイスのワイプを行うことができます。

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices----1048100---"></a>ハイブリッド Azure AD 参加済みデバイスに対する Autopilot のサポート<!-- 1048100 -->
Autopilot を使用してハイブリッド Azure AD 参加済みデバイスを設定できるようになります。 ハイブリッド Autopilot 機能を使用するには、デバイスを組織のネットワークに参加させる必要があります。

### <a name="scope-tags-for-apps---1081941---"></a>アプリのスコープ タグ <!--1081941 -->
Intune リソースへのアクセスを制限する目的で、スコープ タグを作成できるようになります。 スコープ タグをロールの割り当てに追加し、同じスコープ タグを構成プロファイルに追加します。 そのロールでは、スコープ タグが一致する (あるいはスコープ タグがない) 構成プロファイルを持つリソースにのみアクセスできます。
スコープ タグを作成するには、**[Intune ロール]**、**[スコープ (タグ)]**、**[作成]** の順に選択します。
スコープ タグをロールの割り当てに追加するには、**[Intune ロール]**、**[すべてのロール]**、**[ポリシーおよびプロファイル マネージャー]**、**[割り当て]**、**[スコープ (タグ)]** の順に選択します。
スコープ タグを構成プロファイルに追加するには、**[デバイス構成]**、**[プロファイル]** の順に選択し、プロファイルを選択して **[プロパティ]**、**[スコープ (タグ)]** の順に選択します。

## <a name="tenant-health-dashboard----1124854---"></a>テナントの正常性ダッシュボード<!-- 1124854 -->
Intune の [テナントの状態] ページでは、テナントの状態に関する情報が 1 か所に表示されます。 このページは、次の 4 つのセクションに分かれています。  
- **テナントの詳細**: ご利用の MDM 機関、ご利用のテナントに登録されたデバイスの総数、ご利用のライセンス数などの情報が含まれています。 このセクションには、そのテナントに対する現在のサービス リリースも示されます。
- **コネクタの状態**: Apple VPP、ビジネス向け Windows ストア、証明書コネクタなど、構成されているコネクタに関する情報が含まれています。 コネクタには、その現在の状態に基づいて、*正常*、*警告*、または*異常*を示すフラグが付けられます。
- **Intune サービスの正常性**: ご利用のテナントでのアクティブなインシデントまたは障害が含まれています。 このセクション内の情報は、Office メッセージ センター ([https://portal.office.com](https://portal.office.com)) から直接取得されます。
- **Intune ニュース**: ご利用のテナントに対するアクティブなメッセージが含まれています。ご利用のテナントに最新の Intune 機能が届いたことを示す通知などがあります。 このセクション内の情報は、Office メッセージ センター ([https://portal.office.com](https://portal.office.com)) から直接取得されます。

### <a name="enrollment-abandonment-report----1382924---"></a>登録の破棄に関するレポート <!-- 1382924 -->
破棄された登録の詳細を示す新しいレポートが使用できる用になります。**[デバイスの登録]** > **[モニター]** の順に移動します。

### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>ユーザー登録なしでの WIP ポリシーの展開 <!-- 1434452 -->
使用している Windows 10 デバイスを登録することを MDM ユーザーに求めることなく、Windows 情報保護 (WIP) ポリシーを展開できるようになります。 この構成により、会社は WIP 構成に基づいて会社のドキュメントを保護することができ、一方、ユーザーは独自の Windows デバイスの管理を維持することができます。 WIP ポリシーを使用してドキュメントが保護されると、Intune 管理者は保護されたデータを選択的にワイプすることができます。 ユーザーとデバイスを選択してワイプ要求を送信することにより、WIP ポリシーを介して保護されたデータはすべて使用できなくなります。 Azure portal 内で Intune から、**[モバイル アプリ]** > **[アプリの選択的ワイプ]** の順に選択します。


### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>ポータル サイト アプリ用のカスタム ブランド イメージを追加する <!-- 1916266 -->
Microsoft Intune 管理者は、ポータル サイト アプリ内のユーザーのプロファイル ページに背景イメージとして表示されるカスタム ブランド イメージをアップロードできるようになります。 ポータル サイト アプリの構成方法の詳細については、「[Microsoft Intune ポータル サイト アプリを構成する方法](company-portal-app.md)」を参照してください。

### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Windows Autopilot に登録されたデバイスを correlator ID によってグループ化する <!-- 2075110 -->
Configuration Manager で [既存デバイス向け Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) を使用することによって登録するとき、correlator ID による Windows デバイスのグループ化が Intune によってサポートされます。 correlator ID は、Autopilot 構成ファイルのパラメーターです。 Intune では [Azure AD デバイス属性 enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) が等しい "OfflineAutopilotprofile -\<correlator ID\>" に自動的に設定されます。 これにより、オフライン Autopilot 登録用の enrollmentprofileName 属性を介して、correlator ID に基づく任意の Azure AD 動的グループを作成することができます。 


### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>iOS 電子メール プロファイルでの iOS 12 OAuth のサポート <!--2155106 -->
Intune の iOS 電子メール プロファイルで iOS 12 OAuth がサポートされます。 この機能を表示するには、**[Intune]** > **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]**  >  **OAuth**の順に選択します。 この設定をオンにすると、次の 2 つのことが行われます。
1. 既に対象となっているデバイスに新しいプロファイルが発行されます。
2. ユーザーは再び資格情報の入力を求められます。

### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Android および Android エンタープライズでの [必要なパスワードの種類] の新しい既定値の設定 <!-- 2649963 -->
新しいコンプライアンス ポリシーを作成すると (**[Intune]** > **[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[Android]** または **[Android エンタープライズ]** (プラットフォームの場合) > [システム セキュリティ])、**[必要なパスワードの種類]** の既定値が変更されます (現在の既定値: デバイスの既定値、新しい既定値: 最小数の数字、適用対象: Android、Android エンタープライズ)。

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Autopilot プロファイルを [すべてのデバイス] 仮想グループに割り当てる <!--2715522 -->
Autopilot プロファイルを [すべてのデバイス] 仮想グループに割り当てられるようになります。 これを行うには、**[デバイスの登録]** > **[Windows の登録]** > **[Deployment Profiles]\(展開プロファイル\)** の順に選択し、プロファイルを選択し、**[割り当て]**、**[割り当て先]** の順に進み、**[すべてのデバイス]** を選択します。

### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>新しい Azure Active Directory terms of use 機能 <!-- 2870393 -->
Azure Active Directory では、既存の Intune の使用条件の代わりに使用できる terms of use 機能が用意されます。 Azure AD terms of use 機能では、どの使用条件をどのタイミングで表示するかについての柔軟性が高くなり、ローカライズのサポートが強化され、使用条件の表示方法をより細かく制御でき、レポート機能が改善されています。 Azure AD terms of use 機能を使用するには、Enterprise Mobility + Security E3 スイートにも含まれている Azure Active Directory Premium P1 が必要です。


### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>エンドユーザーのコンピューター上で Office を更新するとき、Office のローカライズされた言語は Intune によって維持される <!-- 2971030 -->
エンドユーザーのコンピューターに Office が Intune によってインストールされる場合、エンド ユーザーには前の .MSI Office インストールで使用していたのと同じ言語パックが自動的に提供されます。 

<!-- 1809 start -->  

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>iOS MDM に登録されたデバイスに対する Intune APP データ転送設定 <!-- 2244713 -->
登録されたユーザーの ID を指定することにより、iOS MDM に登録されたデバイスに対する Intune APP データ転送設定の制御を区別することができます。 IntuneMAMUPN を使用しない管理者に、動作の変更は表示されなくなります。 この機能が使用できるようになると、登録されたデバイス上でのデータ転送動作を制御するために IntuneMAMUPN を使用する管理者は、新しい設定を確認し、必要に応じて、自分の APP 設定を更新する必要があります。

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Windows 10 Wi-Fi プロファイル内で事前共有キーを使用する <!-- 2662938 -->
事前共有キー (PSK) を、WPA/WPA2-パーソナル セキュリティ プロトコルと一緒に使用することで、Windows 10 向け Wi-Fi 構成プロファイルを認証できるようになります。
現時点では、Wi-Fi プロファイルをインポートするか、またはカスタム プロファイルを作成して事前共有キーを使用する必要があります。 [Windows 10 向けの Wi-Fi 設定](wi-fi-settings-windows.md)に関するページに現在の設定が一覧されています。 

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Web データ用のアプリ保護ポリシー (APP) 設定 <!-- 2662995 -->
Android デバイスと iOS デバイスの両方での Web コンテンツに対する APP ポリシー設定は、http リンクと https Web リンクの両方の処理、ならびに iOS ユニバーサル リンクおよび Android アプリ リンクを介したデータ転送の処理をより適切に行えるように更新されます。  

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>Autopilot デバイス同期の頻度が増して 12 時間ごとになる <!-- 2753673 -->
Autopilot デバイスは 24 時間ごとではなく、12 時間ごとに同期されます。

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Intune ランディング ページの更新内容とノードの名の変更 <!--2867309 -->
Intune ランディング ページに対する更新内容には、新しい監視タイルの追加、監視タイルの変更、グラフによるデータの視覚エフェクトの向上が含まれます。 **モバイルアプリ** ノードは、**クライアント アプリ**へと変更になります。

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>ポータル サイト アプリを使用したエンドユーザーのアクセスが増やされる <!-- 772203 -->
エンドユーザーは、パスワードのリセットや自分の AAD プロファイルなどの重要なアカウント アクションにポータル サイト アプリからアクセスできるようになります。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>別の MDM によって使用される Apple VPP トークン <!-- 1488946 -->
Intune では、Apple のボリューム購入プログラム (VPP) トークンが Intune と別の MDM の両方で使用されている場合、詳細が検出され、表示されます。

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>iOS のバージョン番号とビルド番号が表示される <!-- 1892471 -->
**[デバイスのポリシー準拠]** の **[デバイスのポリシー準拠]** に iOS のオペレーティング システム バージョンが表示されます。 今後の更新で、ビルド番号も表示されるようになります。
セキュリティ更新がリリースされるとき、Apple は通常、バージョン番号を現状のまま残しますが、ビルド番号を更新します。 ビルド番号を表示することで、脆弱性更新がインストールされているかどうかを簡単に確認できます。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>[デバイスのポリシー準拠] ダッシュボードのデバイスが廃止に <!-- 1981119 -->
今後の更新で、廃止になっているデバイスが [デバイスのポリシー準拠] ダッシュボードから削除されます。 それにより、コンプライアンス番号が変更されます。


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>オンプレミス コネクタの更新プロセスの変更 <!-- 2277554 -->
ユーザーからのフィードバックに基づき、オンプレミス コネクタの更新方法が変更されます。 オンプレミス コネクタの初回インストール後、更新は自動的に行われます。 この変更は新しい PFX Certificate Connector for Microsoft Intune から始まり、その後、その他の種類のオンプレミス コネクタにロールアウトされる予定です。 

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>デバイス登録マネージャ ユーザー向けのポータル サイト アプリの操作性の改善<!-- 675800 -->
デバイス登録マネージャ (DEM) が Windows 用ポータル サイト アプリにサインインすると、アプリには DEM の現在 (実行中のデバイス) のみが一覧表示されます。 この改善により、DEM に登録されたデバイスをすべて読み込もうとしたときに以前に発生していたタイムアウトが削減されます。  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Configuration Manager コンプライアンスの確認 <!-- 2192052 -->
今後の更新には、新しい System Center Configuration Manager コンプライアンス設定 (**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[Windows 10]**) が含まれます。 Configuration Manager から Intune コンプライアンスにシグナルが送信されます。 Intune の設定を使用して、すべての Configuration Manager シグナルで "準拠" を返すように要求することができます。

たとえば、すべてのソフトウェア更新プログラムをデバイスにインストールすることを要求します。 Configuration Manager では、この要求は "インストール済み" 状態となります。 デバイス上のプログラムが不明な状態である場合、Intune ではデバイスが非準拠となります。

Windows 10 以降に適用されます

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP トークンの期限が切れているか、ポータル サイトのライセンスが不足している場合のアラート <!-- 2237572 -->
Volume Purchase Program (VPP) を使用して、DEP 登録時にポータル サイトを事前プロビジョニングする場合、Intune では、VPP トークンの有効期限が近づいている場合やポータル サイトのライセンスが不足している場合にアラートが表示されます。

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS でのアプリ設定によりサード パーティ製キーボードをブロックできる <!-- 1248481 -->
Intune 管理者は、iOS デバイスで、ポリシーによって保護されているアプリ内の組織データにアクセスするときのサード パーティ製キーボードの使用をブロックすることができます。 サード パーティ製キーボードをブロックするようにアプリケーション保護ポリシー (APP) が設定されていると、デバイス ユーザーは、サード パーティ製キーボードを使って初めて企業データを操作するときに、メッセージを受け取ります。 ネイティブ キーボード以外のすべてのオプションはブロックされ、デバイスのユーザーに表示されません。 デバイス ユーザーにこのダイアログ メッセージが表示されるのは 1 回だけです。 

<!-- 1805 start -->

### <a name="require-non-biometric-after-specified-timeout----1506985---"></a>指定したタイムアウト後に生体認証以外を要求する <!-- 1506985 --> 

管理者指定のタイムアウト後に生体認証以外の PIN を要求することにより、Intune では、企業データ アクセス用の生体認証 ID の使用を制限することで、モバイル アプリケーション管理 (MAM) が有効になっているアプリのセキュリティが強化されます。 この設定は、Touch ID (iOS)、Face ID (iOS)、Android バイオメトリック、またはその他の将来の生体認証方法に依存して APP/MAM が有効なアプリケーションにアクセスするユーザーに影響します。 これらの設定により、Intune 管理者は、ユーザー アクセスをいっそうきめ細かく制御し、複数のフィンガープリントまたは他の生体認証アクセス方法を使うデバイスによって不適切なユーザーに会社のデータが公開されるのを防ぐことができます。 Azure Portal で **Microsoft Intune** を開きます。 **[モバイル アプリ]** > **[アプリ保護ポリシー]** > **[ポリシーの追加]** > **[設定]** の順に選びます。 特定の設定の **[アクセス]** セクションを探します。

<!-- 1803 start -->

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Android 用 Intune ポータル サイト アプリでのヘルプとフィードバックのエクスペリエンスの更新 <!--1631531 -->

Android アプリのベスト プラクティスに合うように、Android 用 Intune ポータル サイト アプリのヘルプとフィードバックのエクスペリエンスが更新されます。 今後数か月かけて Android 用 Intune ポータル サイト アプリが更新され、**[ヘルプとフィードバック]** メニュー項目が **[ヘルプ]** と **[フィードバックの送信]** の異なるメニュー項目に分割されます。 **[ヘルプ]** ページには **[よく寄せられる質問]** セクションと **[メールでサポートに問い合わせる]** ボタンがあり、エンド ユーザーは Microsoft にログをアップロードしたり、会社のサポート部門に問題を説明するメールを送信したりできます。 **[フィードバックの送信]** では Microsoft の標準的なフィードバック送信を利用でき、"気に入った機能"、"気に入らない機能"、"アイデア" を選択できます。



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

現在のところ、アクティブな通知はありません。

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。



