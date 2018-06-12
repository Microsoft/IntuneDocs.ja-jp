---
title: 初期エディション
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 95ad588b084319cd8a0f5f5c5d92da0e892eed50
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745045"
---
# <a name="the-early-edition-for-microsoft-intune---june-2018"></a>Microsoft Intune の初期エディション - 2018 年 6 月

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能の一覧を提供しています。 ここに記載されている情報は、限られた範囲について開示されたものであり、また今後変更される可能性があります。 社外ではこの情報を共有しないでください。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Microsoft 製品グループにお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

> [!Note]
>Intune に関して以下の機能が現在開発されています。 新しいハイブリッド機能については、[ハイブリッド環境の新機能](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)に関するページをご覧ください。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune

<!-- 1806 start -->

### <a name="corporate-owned-single-use-cosu-support-for-android-devices----1630973---"></a>Android デバイスの会社所有、単一使用 (COSU) のサポート <!-- 1630973 -->

Intune は、高度に管理されてロック ダウンされた、キオスク スタイルの Android デバイスをサポートします。 これにより、管理者は、デバイスの使用を 1 つのアプリまたはアプリの小さなセットにさらにロックダウンし、ユーザーが他のアプリを有効にしたり、デバイスで他の操作を実行したりすることを禁止できます。

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Apple Device Enrollment Program の macOS によるサポート <!-- 747651 -->

Intune は、Apple Device Enrollment Program (DEP) への macOS デバイスの登録をサポートします。 これを実行するには、次のようにします。

1. deploy.apple.com で、MDM サーバーに macOS のシリアル番号を割り当てます。
2. シリアル番号を Intune にインポートします。
3. macOS デバイスに固有の登録プログラム プロファイルを作成します。

### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Android for Work および Play for Work の Google 名の変更 <!--842873 -->
Intune は、Google ブランドの変更を反映するように "Android for Work" の用語を更新します。  "Android for Work" および "Play for Work" という用語は使われなくなります。 コンテキストに応じて異なる用語が使われます。

- "Android エンタープライズ" は、最新の Android 管理スタック全体を指します。
- "Work Profile" または "Profile Owner" は、作業プロファイルで管理されている BYOD デバイスを指します。
- "Managed Google Play" は、Google アプリ ストアを指します。

### <a name="monitor-ios--app-configuration-status-per-device----880037-eeready-eestaged---"></a>デバイスごとに iOS アプリ構成の状態を監視する <!-- 880037 eeready eestaged -->

Microsoft Intune 管理者は、各管理対象デバイスの iOS アプリ構成状態を監視できます。 Azure Portal の **[Microsoft Intune]** から、**[デバイス]** > **[すべてのデバイス]** の順に選びます。 管理対象デバイスの一覧から、デバイスのブレードを表示する特定のデバイスを選びます。 デバイスのブレードで、**[アプリの構成]** を選びます。  

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS でのアプリ設定によりサード パーティ製キーボードをブロックできる <!-- 1248481 -->
Intune 管理者は、iOS デバイスで、ポリシーによって保護されているアプリ内の組織データにアクセスするときのサード パーティ製キーボードの使用をブロックすることができます。 サード パーティ製キーボードをブロックするようにアプリケーション保護ポリシー (APP) が設定されていると、デバイス ユーザーは、サード パーティ製キーボードを使って初めて企業データを操作するときに、メッセージを受け取ります。 ネイティブ キーボード以外のすべてのオプションはブロックされ、デバイスのユーザーに表示されません。 デバイス ユーザーにこのダイアログ メッセージが表示されるのは 1 回だけです。 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>macOS デバイスでファイアウォール設定を使ってデバイスのコンプライアンス ポリシーを作成する <!-- 1497640 -->
macOS の新しいコンプライアンス ポリシーを作成するとき (**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[プラットフォーム: macOS]** > **[システム セキュリティ]**)、**ファイアウォール**に関するいくつかの新しい設定を使用できます。 
- **[ファイアウォール]**: ご利用の環境における着信接続の処理方法を構成します。
- **[着信接続]**: DHCP、Bonjour、IPSec など、基本的なインターネット サービスに必要な接続を除き、すべての着信接続を **[ブロック]** します。 この設定は、すべての共有サービスもブロックします。
- **[ステルス モード]**: ステルス モードを **[有効]** にして、デバイスがプローブ要求に応答するのを防ぎます。 デバイスは引き続き、許可されているアプリに関する着信要求に応答します。

適用対象: macOS 10.12 以降

### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>電子メール プロファイルのアカウント ユーザー名として sAMAccountName を使用する <!-- 1500307 -->

Android、iOS、および Windows 10 用の電子メール プロファイルのアカウント ユーザー名として、オンプレミスの **sAMAccountName** を使うことができます。 また、Azure Active Directory (Azure AD) の `domain` または `ntdomain` 属性から、ドメインを取得できます。 または、カスタムの静的ドメインを入力します。

この機能を使うには、オンプレミスの Active Directory 環境から Azure AD に `sAMAccountName` 属性を同期する必要があります。

適用対象: Android、iOS、Windows 10 以降

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>アプリの起動時とタイムアウト時に生体認証ではないパスコードを要求する <!-- 1506985 -->

アプリの起動時と管理者指定のタイムアウト後に生体認証以外のパスコードを要求することにより、Intune は、企業データ アクセス用の生体認証 ID の使用を制限することで、モバイル アプリケーション管理 (MAM) が有効になっているアプリのセキュリティを強化します。 この設定は、Touch ID (iOS)、Face ID (iOS)、Android バイオメトリック、またはその他の将来の生体認証方法に依存して APP/MAM が有効なアプリケーションにアクセスするユーザーに影響します。 これらの設定により、Intune 管理者は、ユーザー アクセスをいっそうきめ細かく制御し、複数のフィンガープリントまたは他の生体認証アクセス方法を使うデバイスによって不適切なユーザーに会社のデータが公開されるのを防ぐことができます。 Azure Portal で **Microsoft Intune** を開きます。 **[モバイル アプリ]** > **[アプリ保護ポリシー]** > **[ポリシーの追加]** > **[設定]** の順に選びます。 特定の設定の **[アクセス]** セクションを探します。

### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>組織のアプリ データの選択的ワイプ <!-- 1507030 -->
管理者は、アプリケーション保護ポリシー (アプリ) アクセス設定の条件が満たされないときの新しいアクションとして、組織のデータの選択的ワイプを構成することができます。  この機能を使うと、管理者は事前に構成した条件に基づいて、アプリケーションから組織の機密データを自動的に保護したり削除したりできます。

### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>VPP を通じて購入した iOS アプリの取り消し <!-- 1777384 -->
Microsoft Intune 管理者は、ボリューム購入プログラム (VPP) で購入した iOS アプリのうち選択したもののライセンスを取り消すことができます。 アプリが割り当てられなくなるユーザーに通知することができます。 アプリのライセンスを取り消しても、関連する VPP アプリがデバイスからアンインストールされるわけではありません。 VPP アプリをアンインストールするには、割り当てアクションを **[アンインストール]** に変更する必要があります。 回収されたライセンスの数は、Intune の **[アプリ]** ワークロードの **[ライセンスされたアプリ]** ノードに反映されます。 iOS VPP アプリの詳細については、「[Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法](vpp-apps-ios.md)」をご覧ください。

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 言語パック <!-- 1833450 -->
Intune 管理者は、Intune によって管理されている Office 365 Pro Plus アプリに追加の言語を展開することができます。 使用可能な言語のリストには、言語パックの **種類** (コア、部分、校正) が含まれます。 Azure Portal で、**[Microsoft Intune]** > **[モバイル アプリ]** > **[アプリ]** > **[追加]** の順に選びます。 **[アプリの追加]** ブレードの **[アプリの種類]** 一覧で、**[Office 365 スイート]** の **[Windows 10]** を選びます。 **[アプリ スイートの設定]** ブレードで **[言語]** を選びます。

### <a name="revoke-ios-vpp-app-license----1863797---"></a>iOS VPP アプリのライセンスを取り消す <!-- 1863797 -->
管理者は、ユーザーまたはデバイスに割り当てられている iOS VPP アプリのライセンスを回収することができます。 iOS VPP アプリをアンインストールしても、アプリのライセンスを回収できます。 その後は、別のユーザーまたはデバイスにアプリ ライセンスを割り当てることができます。 iOS VPP アプリのライセンスの詳細については、「[Microsoft Intune での iOS のボリューム購入アプリの管理](vpp-apps-ios.md)」をご覧ください。

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>ポータル Web サイトの新しいユーザー エクスペリエンスの更新<!--2000968 -->
ユーザーからのフィードバックに基づいて、Intune ポータル サイト Web サイトに新機能が追加されています。 Android、iOS、Windows デバイスから、既存の機能と使いやすさの大幅な向上を体験できます。 デバイス詳細、フィードバックとサポート、デバイス概要などのサイトの領域には、最新の応答性の高いデザインが採用されています。 また、次のような更新が行われています。

- すべてのデバイス プラットフォームでの簡素化されたワークフロー
- 強化されたデバイスの識別と登録のフロー
- 役に立つエラー メッセージ
- わかりやすい言語、少ない技術用語
- アプリへの直接リンクを共有する機能
- 大規模なアプリケーション カタログのパフォーマンスの向上
- すべてのユーザーに対するアクセシビリティの向上

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Office 365 Pro Plus アプリの展開を編集する <!-- 2150145 -->
Microsoft Intune 管理者は、さらに向上した Office 365 Pro Plus アプリの展開の編集機能を使用できるようになります。 Azure Portal で、**[Microsoft Intune]** > **[モバイル アプリ]** > **[アプリ]** の順に選びます。 アプリの一覧から、Office 365 Pro Plus スイートを選択します。  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>アップロードされた重複する業務用デバイス ID の行ごとのレビュー <!-- 2203794 -->
業務用 ID をアップロードすると、重複の一覧が提供され、既存の情報を置き換えるか、保持することができます。 **[デバイスの登録]** > **[業務用デバイスの ID]** > **[ID の追加]** を選ぶと、重複がある場合はレポートが表示されます。 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>業務用デバイスの ID を手動で追加する <!-- 2203803 -->
業務用デバイスの ID を手動で追加することができます。 **[デバイスの登録]** > **[業務用デバイスの ID]** > **[追加]** の順に選びます。

### <a name="new-status-for-devices-in-device-configuration----2308882---"></a>デバイス構成でのデバイスの新しい状態 <!-- 2308882 -->
**[デバイス構成]** > **[概要]** に、次の新しい状態が追加されます。
- 成功
- エラー
- 競合
- 保留中
- 適用不可。異なるプラットフォームのデバイス数を示すイメージも表示されます。 たとえば、iOS プロファイルを見ている場合、新しいタイルでは、そのプロファイルに割り当てられている iOS 以外のデバイスの数も示されます。 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>デバイスのコンプライアンスはサード パーティのウイルス対策ソリューションをサポートする <!-- 2325484 -->
デバイス コンプライアンス ポリシーを作成するとき (**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[プラットフォーム: Windows 10 以降]** > **[設定]** > **[システム セキュリティ]**)、新しい **[デバイスのセキュリティ]** オプションがあります。 
- **[ウイルス対策]**: **[必要]** に設定すると、Windows Security Center に登録されている Symantec などのウイルス対策ソリューションを使って、コンプライアンスを確認できます。 
- **[スパイウェア対策]**: **[必要]** に設定すると、Windows Security Center に登録されている Symantec などのスパイウェア対策ソリューションを使って、コンプライアンスを確認できます。 

適用対象: Windows 10 以降 

<!-- 1805 start -->

### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Palo Alto Networks GlobalProtect VPN プロファイルのサポート <!-- 1333680 eeready ! -->

今回の更新で、Intune での VPN プロファイルの VPN 接続の種類として、Palo Alto Networks GlobalProtect を選択できるようになりました (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[プロファイルの種類]** > **[VPN]**)。 このリリースでは、次のプラットフォームがサポートされます。 

- iOS
- Windows 10

### <a name="set-compliance-by-device-location----851881----"></a>デバイスの場所によるコンプライアンスの設定 <!-- 851881 ! -->
状況によっては、ネットワーク接続で定義される特定の場所に、企業リソースへのアクセスを制限することが必要な場合あります。 デバイスの IP アドレスに基づき、コンプライアンス ポリシーを作成できます (**[デバイスのポリシー準拠]** > **[場所]**)。 デバイスが IP 範囲外に移動した場合、デバイスは会社のリソースにアクセスできません。

適用対象: Android デバイス 6.0 以降 (ポータル サイト アプリ更新済み)

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>アプリのインストールのトラブルシューティングの向上 <!-- 928990 -->
Microsoft Intune の MDM で管理されたデバイスでは、アプリのインストールが失敗することがあります。 アプリのインストールが失敗した場合、失敗の理由を理解したり、問題をトラブルシューティングするのが難しい場合があります。 アプリ トラブルシューティング機能のパブリック プレビューが提供されています。 各デバイスの下に **[管理対象アプリ]** という新しいノードがあります。 これには、Intune MDM 経由で配布されたアプリが表示されます。 ノード内では、アプリのインストール状態が一覧表示されます。 個々のアプリを選ぶと、その特定のアプリのトラブルシューティング ビューが表示されます。 トラブルシューティング ビューでは、アプリが作成、変更、ターゲット指定、デバイス配布されたときなど、アプリのエンド ツー エンドのライフサイクルが表示されます。 さらに、アプリのインストールが成功しなかった場合は、エラー コードとエラーの原因に関する便利なメッセージが表示されます。

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>コールド アプリ起動時とタイムアウト時に生体認証ではないパスコードを要求する <!-- 1506985 --> 

コールド アプリ起動時と管理者指定のタイムアウト後に生体認証以外のパスコードを要求することにより、Intune は、企業データ アクセス用の生体認証 ID の使用を制限することで、モバイル アプリケーション管理 (MAM) が有効になっているアプリのセキュリティを強化します。 この設定は、Touch ID (iOS)、Face ID (iOS)、Android バイオメトリック、またはその他の将来の生体認証方法に依存して APP/MAM が有効なアプリケーションにアクセスするユーザーに影響します。 これらの設定により、Intune 管理者は、ユーザー アクセスをいっそうきめ細かく制御し、複数のフィンガープリントまたは他の生体認証アクセス方法を使うデバイスによって不適切なユーザーに会社のデータが公開されるのを防ぐことができます。 Azure Portal で **Microsoft Intune** を開きます。 **[モバイル アプリ]** > **[アプリ保護ポリシー]** > **[ポリシーの追加]** > **[設定]** の順に選びます。 特定の設定の **[アクセス]** セクションを探します。

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>未承認のデバイス ベンダーとモデルに基づくアプリのアクセスのブロック <!-- 1425689 ! -->
Intune の IT 管理者は、Intune App Protection ポリシーによって、Android 製造元や iOS モデルの指定された一覧を適用できます。 IT 管理者は、Android ポリシーの製造元と iOS ポリシーのデバイス モデルのセミコロン区切り一覧を提供できます。 Intune App Protection ポリシーは、Android および iOS 専用です。 この指定されたリストでは 2 つの個別操作を実行できます。
- 指定されていないデバイスでのアプリ アクセスからブロック。
- または、指定されていないデバイスでの企業データの選択的ワイプ。 

ユーザーは、ポリシーによる要件が満たされない場合、対象となるアプリケーションにアクセスすることができません。 設定に基づいて、ユーザーは、ブロックされるか、アプリ内の企業データを選択的にワイプされます。 iOS デバイスのこの機能で、最低バージョンの設定を対象アプリケーションに適用するには、アプリケーション (つまり、 WXP、Outlook、Managed Browser、Yammer) が参加して、Intune APP SDK を統合する必要があります。 この統合は、ローリング方式で行われ、特定のアプリケーション チームによって異なります。 Android でこの機能を利用するには、最新の Intune ポータル サイトが必要です。 

エンド ユーザー デバイスの Intune クライアントは、アプリケーション保護ポリシーに対して Intune ブレードで指定されている文字列の単純一致に基づいてアクションを実行します。 これは、デバイスを報告する値に完全に依存します。 そのため、IT 管理者には、意図した動作が正確であることを確認することをお勧めします。 これは、小さなユーザー グループを対象に、さまざまなデバイス製造元とモデルに基づいてこの設定をテストすることによって実現できます。 Microsoft Intune でアプリ保護ポリシーを表示および追加するには、**[Mobile Apps]** > **[アプリ保護ポリシー]** を選びます。 アプリ保護ポリシーについて詳しくは、「[アプリ保護ポリシーとは](app-protection-policy.md)」をご覧ください。

### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Windows 10 デバイスでキオスク モードを有効にする <!-- 1560072 ! -->
Windows 10 デバイスでは、構成プロファイルを作成して、キオスク モードを有効にすることができます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[Windows 10]** > **[デバイスの制限]** > **[キオスク]**)。 この更新では、**[キオスク (プレビュー)]** の設定の名前が **[キオスク (古い)]** に変更されています。 **[キオスク (古い)]** は使用を推奨されませんが、7 月の更新までは機能し続けます。 **[キオスク (古い)]** は新しい **[キオスク]** プロファイルの種類に置き換えられ (**[プロファイルの作成]** > **[Windows 10]** > **[キオスク (プレビュー)]**)、Windows 10 RS4 以降でキオスクを構成する設定が含まれます。

Windows 10 以降に適用されます。

### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>キオスク モードのビジネス向け Microsoft Store アプリの関連付けられたアプリ ユーザー モデル ID (AUMID) を取得する <!-- 1560077 ! -->
Intune は、ビジネス向け Microsoft Store (WSfB) アプリのアプリ ユーザー モデル ID (AUMID) を取得して、キオスク プロファイルの構成の向上を提供できます。

ビジネス向け Microsoft Store アプリについて詳しくは、「[ビジネス向け Microsoft Store からのアプリの管理](windows-store-for-business.md)」をご覧ください。

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>アプリ保護ポリシーのアクションにアクセスする <!-- 1483510 EEready -->
まもなく、非準拠デバイスを明示的にワイプ、ブロック、または警告するようアプリ保護ポリシーを構成できるようになります。 最新のアクション "*ワイプ*" は、デバイスから会社の企業データを削除します。 ワイプが発生した場合、デバイスのユーザーにはワイプの理由と修復手順の両方が通知されます。 最低 OS バージョンなどの一部の設定については、ブロックとワイプなど、複数のアクションを適用できます。 これらのアクションは、アプリが起動されるとトリガーされます。

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>Windows デバイスの新しいインベントリ情報 <!-- 1333569 eeready -->

Windows デバイスの場合は、**[ハードウェア]** タブ (**[グループ]** > **[すべてのモバイル デバイス]** > **[デバイス]** > ユーザーのデバイスを選択 > **[プロパティの表示]** > **[ハードウェア]**) で、次のインベントリ情報をデバイスごとに使用できます。
- TPM
- ウイルス対策
- スパイウェア対策
- ファイアウォール
- UAC
- バッテリ
- [ドメイン名]

CSP でこのデータを取得する方法については、「[DeviceStatus CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp)」で DeviceStatus のエントリをご覧ください。

### <a name="intune-and-the-microsoft-edge-browser----1818969---"></a>Intune と Microsoft Edge ブラウザー <!-- 1818969 -->
モバイル デバイス (iOS および Android) 向けの Microsoft Edge ブラウザーが、Intune アプリ保護ポリシーをサポートするようになります。 企業の Azure AD アカウントで Edge ブラウザー アプリケーションにサインインしたユーザーは、Intune によって保護されます。 

### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Autopilot の OOBE を構成するときの新しい言語/リージョンの設定 <!-- 1821766 -->
Out of Box Experience (OOBE) の間に、Autopilot プロファイルの言語とリージョンを設定する、新しい構成設定を使用できます。

### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>デバイス キーボードを構成するための新しい設定 <!-- 1821768 -->
Out of Box Experience (OOBE) の間に、Autopilot プロファイルのキーボードを構成する新しい設定を使用できます。

### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>TeamViewer を使用して iOS デバイスと MacOS デバイスの画面を共有する <!-- 1985547 -->
現在、TeamViewer を使用して、[Intune で管理された Android および Windows デバイス](device-profile-android-teamviewer.md)をリモート管理することができますです。

管理者は、TeamViewer に接続し、iOS および macOS デバイスとの画面共有セッションを開始できます。 iPhone、iPad、macOS ユーザーは、他のデスクトップ デバイスまたはモバイル デバイスと画面をライブで共有できます。 

### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>デバイス プロファイルのグラフィカル ユーザー グラフが戻った <!-- 2160133 -->
デバイス プロファイルのグラフィカルなグラフに表示される数値カウントの向上で (**[デバイス構成]** > **[プロファイル]** > 既存のプロファイルを選択 > **[概要]**)、グラフィカルなユーザー グラフが一時的に削除されました。

この更新では、グラフィカル ユーザー グラフが元に戻り、Azure portal に表示されます。

### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>スコープ グループとしてすべてのユーザーとすべてのデバイスを割り当てる <!-- 2196803 -->
スコープ グループ内のすべてのユーザー、すべてのデバイス、およびすべてのユーザーとすべてのデバイスを、割り当てることができるようになります。 これを行うには、**[Intune の役割]** > **[すべてのロール]** > **[Policy and profile manager]\(ポリシーとプロファイル マネージャー\)** > **[割り当て]** の順に選び、割り当てを選んで、**[スコープ (グループ)]** を選びます。

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Autopilot プロファイルの対象がグループに移動 <!-- 1877935 -->
現在は、AutoPilot のデプロイ プロファイルは選択したデバイスに割り当てることができます。 この機能のリリース後、これらのプロファイルを割り当てるには次のようにします。
- AutoPilot デバイスを含む (Azure AD) グループを作成します
- 目的のプロファイルを Azure AD グループに割り当てます。 AutoPilot プロファイルは、そのグループ内の AutoPilot デバイスに割り当てられるようになります。

### <a name="management-name-field-will-be-editable----1875989---"></a>管理名フィールドが編集可能になる <!-- 1875989 -->
デバイスの **[プロパティ]** ブレードで、管理名フィールドを編集できるようになります。 このフィールドを編集するには、**[デバイス]** > **[すべてのデバイス]** > デバイスを選択 > **[プロパティ]** の順に選びます。 管理名フィールドを使って、デバイスを一意に識別できます。

<!-- 1804 start -->

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>ローカル デバイス セキュリティ オプションの設定への追加 <!-- 1403702 -->
Windows 10 デバイスに対して追加のローカル デバイス セキュリティ オプションの設定を構成することができます。 追加設定を利用できるのは、Microsoft ネットワーク クライアント、Microsoft ネットワーク サーバー、ネットワーク アクセスとセキュリティ、および対話型ログオンなどに関する部分です。 これらの設定は、Windows 10 デバイスの構成ポリシーを作成するときに、[Endpoint Protection] カテゴリに表示されます。

### <a name="rules-for-removing-devices----1609459---"></a>デバイス削除のルール <!-- 1609459 -->
設定した日数の間チェックインしていないデバイスを自動的に削除する新しい規則を使用できます。 新しいルールを表示するには、**[Intune]** ウィンドウ、**[デバイス]**、**[Device removal rules]\(デバイス削除ルール\)** の順に選択します。

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Windows 10 Enterprise RS4 Autopilot デバイスでのコンシューマー アプリおよびエクスペリエンスの禁止<!-- 1621980 -->
Windows 10 Enterprise RS4 Autopilot デバイスへのコンシューマー アプリおよびエクスペリエンスのインストールを禁止することができます。 この機能を表示するには、**[Intune]** > **[デバイスの登録]** > **[Windows の登録]** > **[Windows AutoPilot profiles]\(Windows AutoPilot プロファイル\)** > **[新規作成]** > **[登録設定]** の順に移動します。 

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>複数の Exchange Connector のサポート <!-- 2070451 -->

テナントごとの Microsoft Intune Exchange Connector の数が 1 個だけという制限がなくなりました。 Intune は複数の Exchange Connector をサポートするようになるので、複数のオンプレミス Exchange の組織で Intune の条件付きアクセスを設定できます。

Intune のオンプレミス Exchange Connector を使うと、デバイスが Intune に登録されているかどうか、およびデバイスが Intune のデバイス コンプライアンス ポリシーに準拠しているかどうかに基づいて、お使いのオンプレミスの Exchange メールボックスに対するデバイス アクセスを管理できます。 コネクタを設定するには、Azure Portal から Intune のオンプレミス Exchange Connector をダウンロードして、Exchange の組織内のサーバーにインストールします。 Microsoft Intune ダッシュ ボードで **[オンプレミス アクセス]** を選択し、**[セットアップ]** で **[Exchange ActiveSync のコネクタ]** を選択します。 Exchange のオンプレミス コネクタをダウンロードし、Exchange の組織内のサーバーにインストールします。 テナントごとに 1 個という Exchange Connector の制限がなくなったので、他に Exchange の組織がある場合は、他の各 Exchange の組織にも同じ手順でコネクタをダウンロードしてインストールできます。

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Windows 10 デスクトップ デバイスのすべてのユーザーに対して必要な基幹業務 (LOB) アプリを展開する機能 <!-- 1627835 RS4 -->
お客様は、必要な基幹業務 Windows 10 アプリを展開してデバイス コンテキストにインストールできるようになります。 これにより、デバイスのすべてのユーザーがこれらのアプリを使用できるようになります。 対象は Windows 10 デスクトップ デバイスだけです。

### <a name="company-portal-enrollment-improved----1874230--"></a>会社ポータルの登録の機能強化 <!-- 1874230-->
Windows 10 ビルド 1703 以降の Intune ポータル サイトを使ってデバイスを登録するユーザーは、アプリを離れることなく登録の最初の手順を完了できます。

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



