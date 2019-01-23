---
title: 初期エディション - Microsoft Intune
titlesuffix: ''
description: Microsoft Intune の初期エディション
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: d1b553d262200e58a4c06dd0f4bcb72ca1398080
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2019
ms.locfileid: "54386986"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>Microsoft Intune の初期エディション - 2019 年 1 月

> [!Note]
> NDA 通知: Intune に関して以下の機能が現在開発されています。 この情報は、NDA に基づき、非常に限られた範囲で共有されます。 Twitter、UserVoice、Reddit などの、ソーシャル メディアやパブリック Web サイトには、この情報を投稿しないでください。 

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている、NDA に基づいて共有される新機能のリストを提供します。 ここに記載されている情報は、限られた範囲について開示されたものであり、また今後変更される可能性があります。 ツイート、UserVoice への投稿、またそれ以外の方法で、社外でこの情報を共有したりしないでください。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Microsoft 製品グループにお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune

<!-- 1901 start -->

### <a name="android-enterprise-apps----1352553----"></a>Android エンタープライズ アプリ<!-- 1352553  -->
Microsoft Intune からマネージド Google Play アプリを削除できます。 マネージド Google Play アプリを削除するには、Azure portal で Microsoft Intune を開き、**[クライアント アプリ]** > **[アプリ]** の順に選択します。 アプリの一覧から、マネージド Google Play アプリの右側にある省略記号 (...) を選択し、表示された一覧で **[削除]** を選択します。 アプリの一覧からマネージド Google Play アプリを削除すると、そのマネージド Google Play アプリは自動的に未承認になります。

### <a name="managed-google-play-app-type----1352580---"></a>マネージド Google Play アプリの種類<!-- 1352580 -->
**マネージド Google Play** アプリの種類では、特定の[マネージド Google Play アプリ](https://play.google.com/work/search?q=microsoft&c=apps)を Intune に追加できます。 Intune の管理者は、Intune でマネージド Google Play アプリを参照、検索、承認、同期および割り当てできます。 マネージド Google Play コンソールに別途移動する必要がなく、また再認証する必要もありません。 Intune で、**[クライアント アプリ]** > **[アプリ]** > **[追加]** を選択します。 **[アプリケーションの種類]** 一覧で、アプリの種類として **[マネージド Google Play]** を選択します。

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>オンラインでライセンスされたビジネス向け Microsoft Store アプリの展開 <!-- 1672660  -->
オンラインでライセンスされた必要なビジネス向け Microsoft Store アプリをデバイスのコンテキストで割り当てることができます。 このようにして、ビジネス向け Microsoft Store アプリを展開すると、デバイス上のすべてのユーザーにアプリをインストールできます。 対象は Windows 10 RS4 以上のデスクトップ デバイスのみです。 デバイスのコンテキストでインストールするオプションは、MSFB オンラインのライセンスされたアプリのクライアント アプリの割り当てページにあります。

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>セットアップ アシスタント中、一部の画面をスキップするようにプロファイルを構成する <!-- 2276470  -->
macOS の登録プロファイルの作成時、ユーザーにセットアップ アシスタントで表示される次のいずれかの画面をスキップするよう構成できます。
- Android 移行
- ディスプレイの色調
- プライバシー
- iCloudStorage

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522----"></a>Autopilot プロファイルを [すべてのデバイス] 仮想グループに割り当てる <!--2715522  -->
Autopilot プロファイルを [すべてのデバイス] 仮想グループに割り当てられるようになります。 これを行うには、**[デバイスの登録]** > **[Windows の登録]** > **[Deployment Profiles]\(展開プロファイル\)** の順に選択し、プロファイルを選択し、**[割り当て]**、**[割り当て先]** の順に進み、**[すべてのデバイス]** を選択します。 Autopilot プロファイルについて詳しくは、「[Windows Autopilot を使用して Windows デバイスを登録する](enrollment-autopilot.md)」をご覧ください。

### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324----"></a>デバイスの構成プロファイルを使用した監視対象の iOS デバイスの壁紙のカスタマイズ <!-- 2809324  -->
iOS デバイス用のデバイス構成プロファイルを作成するとき、**[デバイスの構成]** > **[プロファイル]** > **[プロファイルの作成]** > **プラットフォーム用の iOS** > プロファイルの種類用の **[デバイスの制限]** で一部の設定を許可したり制限できます。 この更新には、管理者が .png、.jpg、または .jpeg 画像を壁紙として使用したり、画像をプレビューしたり、壁紙をユーザーが変更するのをブロックする新しい**壁紙**の設定があります。 壁紙の設定は、監視対象のデバイスにのみ適用できます。 現在の設定の一覧については、[iOS デバイスの制限設定](device-restrictions-ios.md)に関するページを参照してください。

### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Win32 アプリのトースト通知 <!-- 3136566   -->
アプリ割り当てごとに、エンドユーザーにトースト通知が表示されるのを抑制することができます。 Intune で **[クライアント アプリ]** > **[アプリ]**> アプリを選択 > **[Assignemnts]\(割り当て\)** > **[グループを含める]** を選択します。 

### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396---"></a>Android エンタープライズの [デバイスの制限] > [デバイスの所有者] での [Bluetooth 経由での連絡先の共有] の削除 <!-- 3598396 -->
Android エンタープライズ デバイス用にデバイスの制限プロファイルを作成した場合、**[Bluetooth 経由での連絡先の共有 ]** 設定があります。 この更新では、**[Bluetooth 経由での連絡先の共有]** の設定が削除されます (**[デバイスの構成]** > **[プロファイル]** > **[プロファイルの作成]** > **プラットフォーム用の Android エンタープライズ** > **[デバイスの制限] > プロファイルの種類の [デバイスの所有者]** > **[全般]**)。 

**[Bluetooth 経由での連絡先の共有]** 設定は、Android エンタープライズのデバイス所有者の管理ではサポートされていません。 したがって、この設定が削除されると、この設定が環境で有効および構成されていた場合でもいかなるデバイスやテナントにも影響はありません。

現在の設定一覧を確認するには、[Android エンタープライズ デバイスの機能を許可または制限する設定](device-restrictions-android-for-work.md)に関するページを参照してください。

適用先:Android エンタープライズ デバイスの所有者

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android エンタープライズ APP-WE アプリの展開 <!-- 1171203 -->
登録のないアプリ保護ポリシー (APP-WE) の展開シナリオでの Android では、managed Google Play を使用してストア アプリと LOB アプリをユーザーに展開できます。 具体的には、IT はエンド ユーザーに、不明なソースからのインストールを許可することによってデバイスのセキュリティ状態を損なう必要がないアプリ カタログとインストール エクスペリエンスを提供できます。 さらに、この展開シナリオでは、向上したエンド ユーザー エクスペリエンスが提供されます。

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>256 ビット暗号化キーをサポートするようになる Intune App SDK <!-- 1832174 -->
アプリ保護ポリシーによって暗号化が有効にされると、Android 用 Intune App SDK では 256 ビット暗号化キーが使用されるようになります。 古いバージョンの SDK を使用するコンテンツやアプリとの互換性のため、SDK では引き続き 128 ビット キーのサポートが提供されます。


### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Intune ポリシーでの認証方法とポータル サイト アプリのインストールの更新 <!-- 1927359 -->
Apple の会社用デバイスの登録方法のいずれかを使ってセットアップ アシスタント経由で既に登録されているデバイスの場合、Intune では、特定のデバイスで App Store からインストールされる場合に、ポータル サイト アプリがサポートされなくなります。 この変更は、登録時に Apple セットアップ アシスタントで認証を行う場合にのみ関係があります。 また、この変更は、以下から登録される iOS デバイスのみに影響します。  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple Device Enrollment Program (DEP)

App Store からポータル サイト アプリをインストールした後、これらのデバイスを登録しようとすると、エラーが発生します。 登録時に Intune によって自動的にプッシュされた場合、これらのデバイスはポータル サイトだけを使用することが期待されます。 Azure portal での Intune の登録プロファイルは、デバイスの認証方法およびポータル サイト アプリを受信するかどうかを指定できるように更新されます。 DEP デバイス ユーザーがポータル サイトを使用するようにしたい場合は、登録プロファイルでユーザー設定を指定する必要があります。 さらに、ポータル サイト アプリの **[デバイスの特定]** 画面はまもなく古くなります。  
既に登録されている DEP デバイスにポータル サイトをインストールするには、Intune で [クライアント アプリ] に移動し、アプリ構成ポリシーでマネージド アプリとしてプッシュする必要があります。 これらの手順を実行する方法の詳細については、将来のドキュメントで説明します。

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>管理者以外のユーザーが、Azure AD 参加済み Windows 10 デバイスで BitLocker を有効にできる <!-- 2147379 -->
Windows 10 デバイスで BitLocker の設定を有効にすると (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > プラットフォームとして **[Windows 10 以降] を選択** > プロファイルの種類として **[Endpoint Protection]** > **[Windows 暗号化]**)、BitLocker の設定が追加されます。 この更新には、標準ユーザー (管理者以外) が暗号化を有効にするのを許可する新しい BitLocker の設定が含まれます。 現在の設定を確認するには、[Windows 10 用の Endpoint Protection 設定](endpoint-protection-windows-10.md#windows-encryption)に関する記事をご覧ください。


### <a name="additional-settings-for-outlook----3301182---"></a>Outlook <!-- 3301182 --> の追加設定
Intune を使用して、Outlook for iOS と Outlook for Android の追加設定を構成できるようになりました。  これらの設定には以下が含まれます。
- 職場または学校のアカウントを iOS および Android の Outlook でのみ使用することを許可する
- Office 365 およびハイブリッド先進認証オンプレミス アカウントの先進認証をデプロイする
- 基本認証が選択されている場合に、メール プロファイルのユーザー名フィールドで `SAMAccountName` を使用する
- 連絡先の保存を許可する
- 外部受信者メール ヒントを構成する
- **優先受信トレイ**を構成する
- Outlook for iOS へのアクセスに生体認証を要求する 
- 外部の画像をブロックする

> [!NOTE]
> Intune アプリ保護ポリシーを使用して企業 ID のアクセスを管理している場合は、**生体認証を要求する**オプションを有効にしないよう考慮する必要があります。 詳細については、[iOS のアクセス要件](app-protection-policy-settings-ios.md#access-settings)および [Android のアクセス要件](app-protection-policy-settings-android.md#access-settings)について、**アクセスのための企業認証情報の要求**に関する記事を参照してください。

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>管理用テンプレートがパブリック プレビューになり、専用の構成プロファイルに移動される <!-- 3322847 -->
Intune の管理用テンプレート (**[デバイス構成]** > **[管理用テンプレート]**) は現在、プライベート プレビュー段階です。 この更新プログラムでは: 管理用テンプレートには Intune で管理可能な約 300 の設定が含まれます。 以前は、これらの設定はグループ ポリシー エディターにのみ存在しました。
管理用テンプレートはパブリック プレビューで使用できます。管理用テンプレートは、**[デバイス構成]** > **[管理用テンプレート]** から、**[デバイス構成]** > **[プロファイル]** >**[プロファイルの作成]** を選択し、**[プラットフォーム]** で **[Windows 10 以降]** を選択し、**[プロファイルの種類]** で **[管理用テンプレート]** を選択した場所に移動されています。
レポートが有効にされます。適用先: Windows 10 以降

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Intune の macOS ポータル サイトのダーク モード <!-- 3300524 -->
Intune の macOS ポータル サイトで、macOS 用にダーク モードがサポートされるようになりました。 macOS 10.14 以降のデバイスでダーク モードを有効にすると、Intune ポータル サイトではそのモードの色に外観を調整します。

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>セキュリティ ベースラインに対して Microsoft 推奨の設定を使用する<!-- 2055484 -->
Intune は、セキュリティに的を絞ったその他のサービス (Windows Defender ATP や Office 365 ATP など) と統合されます。 一般的な戦略と、Microsoft 365 サービス間での結束的なエンドツーエンドのセキュリティ ワークフローをお客様から求められています。 目標としているのは、セキュリティの運用と一般的な管理者タスクをブリッジするソリューションを構築できるように戦略を調整することにあります。 Intune では、Microsoft が推奨する一連の "セキュリティ ベースライン" を公開することによって、この目標の達成を目指しています (**[Intune]** > **セキュリティ ベースライン**)。  管理者はこれらのベースラインからセキュリティ ポリシーを直接作成し、それをユーザーに展開することができるようになります。 それらのユーザーは、組織のニーズに合わせてベスト プラクティスの推奨事項をカスタマイズすることもできます。 Intune では、これらのベースラインにデバイスが準拠した状態に維持されていることが確認され、管理者には準拠した状態にないユーザーまたはデバイスが通知されます。

### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>登録なしの WIP デバイスに対する選択的ワイプのサポート <!-- 1434452 -->
登録なしの Windows Information Protection (WIP-WE) を使うと、MDM への完全な登録を必要とせずに Windows 10 デバイス上の企業データを保護することができます。 WIP-WE ポリシーを使用してドキュメントが保護されると、Intune 管理者は保護されたデータを選択的にワイプすることができます。 ユーザーとデバイスを選択してワイプ要求を送信することにより、WIP-WE ポリシーを介して保護されたデータはすべて使用できなくなります。 Azure portal 内で Intune から、**[モバイル アプリ]** > **[アプリの選択的ワイプ]** の順に選択します。

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Web データ用のアプリ保護ポリシー (APP) 設定 <!-- 2662995 -->
Android デバイスと iOS デバイスの両方での Web コンテンツに対する APP ポリシー設定は、http リンクと https Web リンクの両方の処理、ならびに iOS ユニバーサル リンクおよび Android アプリ リンクを介したデータ転送の処理をより適切に行えるように更新されます。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>別の MDM によって使用される Apple VPP トークン <!-- 1488946 -->
Intune では、Apple のボリューム購入プログラム (VPP) トークンが Intune と別の MDM の両方で使用されている場合、詳細が検出され、表示されます。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>[デバイスのポリシー準拠] ダッシュボードのデバイスが廃止に <!-- 1981119 -->
今後の更新で、廃止になっているデバイスが [デバイスのポリシー準拠] ダッシュボードから削除されます。 それにより、コンプライアンス番号が変更されます。



<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Configuration Manager コンプライアンスの確認 <!-- 2192052 -->
今後の更新には、新しい System Center Configuration Manager コンプライアンス設定 (**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[Windows 10]**) が含まれます。 Configuration Manager から Intune コンプライアンスにシグナルが送信されます。 Intune の設定を使用して、すべての Configuration Manager シグナルで "準拠" を返すように要求することができます。

たとえば、すべてのソフトウェア更新プログラムをデバイスにインストールすることを要求します。 Configuration Manager では、この要求は "インストール済み" 状態となります。 デバイス上のプログラムが不明な状態である場合、Intune ではデバイスが非準拠となります。

Windows 10 以降に適用されます



## <a name="notices"></a>通知

現在のところ、アクティブな通知はありません。

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。



