---
title: 初期エディション
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e24414d28b8adeae7dfbedb606ca1a7d21497a3f
ms.sourcegitcommit: 698af815f6de2c4f003f6da428bbfb0680daafa0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43093199"
---
# <a name="the-early-edition-for-microsoft-intune---august-2018"></a>Microsoft Intune の初期エディション - 2018 年 8 月

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

<!-- 1808 start -->

### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello の対象はユーザーとデバイスになります <!-- 1106609 -->
[Windows Hello for Business](windows-hello.md) ポリシーを作成すると、そのポリシーは組織内 (テナント全体) のすべてのユーザーに適用されます。 今回の更新によって、デバイス構成ポリシーを使用する特定のユーザーまたは特定のデバイスにもポリシーを適用できるようになりました (**[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]**、**[ID 保護]**、**[Windows Hello for Business]**)。

Azure portal の Intune では、Windows Hello の構成と設定は **[デバイスの登録]** と **[デバイス構成]** の両方に置かれます。 **[デバイスの登録]** の対象は組織全体 (テナント全体) であり、Windows AutoPilot (OOBE) がサポートされます。 **[デバイス構成]** の対象は、チェックイン中に適用されたポリシーを使用するデバイスとユーザーになります。

適用先:  
- Windows 10 以降
- Windows Holographic for Business

### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Windows 10 以降のデバイスで S モードを制御する - パブリック プレビュー <!-- 1958649 -->
Windows 10 デバイスの S モードを解除するデバイス構成プロファイルを作成したり、ユーザーがデバイスの S モードを解除することを禁止したりできます。 この機能は Intune の **[デバイス構成]**、**[プロファイル]**、**[Windows 10 以降]**、**[Edition upgrade and mode switch]\(エディション アップグレードとモード切替\)** にあります。
S モードの詳細は「[Windows 10 (S モード) について](https://www.microsoft.com/windows/s-mode)」でご覧いただけます。
適用対象: Windows 10 以降 (1809 以降)

### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>最新の VPN サポートの更新で iOS に対応 <!-- 2459928, 1819876, and 2650856 -->
今後の更新で次の iOS VPN クライアントがサポート対象になります。 
- F5 Access (バージョン 3.0.1 以降)
- Citrix SSO
- Palo Alto Networks GlobalProtect (バージョン 5.0 以降)、今後の更新ではさらに以下のような変更点あり:
- 既存の **F5 Access** の接続の種類が **F5 Access Legacy** に名称変更 (F5 のブランディング更新による)
- 既存の **Palo Alto Networks GlobalProtect** の接続の種類は **Legacy Palo Alto Networks GlobalProtect** に名称変更されます (Palo Alto のブランディング更新による) 

これらの接続の種類を持つ既存のプロファイルは引き続き旧 VPN クライアントで動作します。 Cisco Legacy AnyConnect、F5 Access Legacy、Citrix VPN、または Legacy Palo Alto Networks GlobalProtect with iOS を使用している場合、新しいアプリに移ってください。 iOS 12 に更新されたときに iOS デバイスで VPN アクセスを利用できるように、できるだけ速やかに移ってください。

### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>ユーザーがサインインするまで、シングル アプリ モードでポータル サイトをロックする <!--1067692 --> 
DEP 登録中、セットアップ アシスタントの代わりに、ポータル サイトを介してユーザーを認証する場合、シングル アプリ モードでポータル サイトを実行するオプションが与えられる予定です。 このオプションによってセットアップ アシスタントの完了直後にデバイスがロックされます。そのため、デバイスを利用するには、ユーザーはサインインする必要があります。 このプロセスにより、デバイスはオンボードを完了し、ユーザーが関連付けられていない状態で孤立することはありません。

### <a name="scope-tags-for-policies---1081974-eeready--"></a>ポリシーのスコープ タグ <!--1081974 eeready-->

Intune リソースへのアクセスを制限する目的で、スコープ タグを作成できるようになります。 スコープ タグをロールの割り当てに追加し、同じスコープ タグを構成プロファイルに追加します。 そのロールでは、スコープ タグが一致する (あるいはスコープ タグがない) 構成プロファイルを持つリソースにのみアクセスできます。
スコープ タグを作成するには、**[Intune ロール]**、**[スコープ (タグ)]**、**[作成]** の順に選択します。
スコープ タグをロールの割り当てに追加するには、**[Intune ロール]**、**[すべてのロール]**、**[ポリシーおよびプロファイル マネージャー]**、**[割り当て]**、**[スコープ (タグ)]** の順に選択します。
スコープ タグを構成プロファイルに追加するには、**[デバイス構成]**、**[プロファイル]** の順に選択し、プロファイルを選択して **[プロパティ]**、**[スコープ (タグ)]** の順に選択します。

### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Autopilot デバイスにユーザーとわかりやすい名前を割り当てる <!--1346521 -->
今後のパブリック プレビューでは、管理者は 1 つの AutoPilot デバイスにユーザーを割り当てることができるようになります。  管理者はまた、AutoPilot でデバイスを設定するユーザーにとってわかりやすい名前を与えることができます。

適用対象: Windows Insider 1809 以降のビルド (プレビューの間)。

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>別の MDM によって使用される Apple VPP トークン <!-- 1488946 -->
Intune では、Apple のボリューム購入プログラム (VPP) トークンが Intune と別の MDM の両方で使用されている場合、詳細が検出され、表示されます。

### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>接続の種類がカスタムと Pulse Secure の場合における、iOS のアプリごとの VPN プロファイルに対するパケット トンネル サポート <!-- 1520957 -->
iOS のアプリごとの VPN プロファイルを使用するとき、アプリ層トンネリング (アプリプロキシ) またはパケットレベル トンネリング (パケットトンネル) を使用できるようになります。 これらのオプションは、次の接続の種類で利用できます。
- カスタム VPN
- Pulse Secure: 使用する値がわからない場合、ご利用の VPN プロバイダーのドキュメントを参照してください。
適用対象: iOS

### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858-eeready---"></a>iOS の VPN プロファイルには、Zscaler を接続として利用可能 <!-- 1769858 eeready -->
iOS VPN デバイス構成プロファイルを作成するとき (**[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択し、プラットフォームに **iOS** を選択し、プロファイルの種類に **VPN** を選択する)、Cisco や Citrix など、接続の種類がいくつかあります。 今後の更新で、接続の種類として Zscaler が追加されます。 
[こちらの](vpn-settings-ios.md)iOS を実行するデバイスの VPN 設定リストには、利用できる接続の種類がまとめられています。

### <a name="block-windows-personal-device-enrollments----1849498---"></a>Windows 個人デバイス登録を禁止する <!-- 1849498 -->
Intune の[モバイル デバイス管理](windows-enroll.md)で Windows 個人デバイスの登録を禁止できるようになります。 [Intune PC エージェント](manage-windows-pcs-with-microsoft-intune.md)で登録されているデバイスはこの機能でブロックできません。
この機能を表示するには、**[デバイスの登録]**、**[デバイスの制限]** の順に選択します。
この制限をオンにしても、既に登録されているデバイスには影響がありません。
制限をオンにすると、Intune では、新しい Windows 登録要求がすべて会社の登録として認証されていることが確認されます。 次の方法は、会社の登録として認証されたものと見なされます。
- 登録ユーザーは[デバイス登録マネージャー アカウント]( device-enrollment-manager-enroll.md)を使用しています。
- デバイスは [Windows Autopilot](enrollment-autopilot.md) 経由で登録されます。
- デバイスの IMEI 番号が **[デバイスの登録]** の **[[業務用デバイスの ID]]( corporate-identifiers-add.md)** に記載されています。
- デバイスが[一括プロビジョニング パッケージ](windows-bulk-enroll.md)経由で登録されます。
- デバイスが[共同管理用の SCCM からの自動登録](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management)経由で登録されます。

無許可の登録はブロックされます。 次の登録は Intune で会社として見なされますが、Intune 管理者のデバイスごとのコントロールがないため、ブロックされます。
- [自動 MDM 登録](windows-enroll.md#enable-windows-10-automatic-enrollment)と [Windows セットアップ中の Azure Active Directory 参加](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md)。
- [自動 MDM 登録](windows-enroll.md#enable-windows-10-automatic-enrollment)と [Windows セットアップからの Azure Active Directory 参加](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md)。

次の個人登録方法もブロックされます。
- [自動 MDM 登録](windows-enroll.md#enable-windows-10-automatic-enrollment)と [Windows 設定からの職場アカウントの追加](https://docs.microsoft.com/azure/active-directory/user-help/device-management-azuread-registered-devices-windows10-setup)。
- Windows 設定からの [MDM 登録のみ]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device)オプション。

### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Autopilot プロファイルにコンピューター名パターンを指定する <!--1849855-->
Autopilot 登録中、生成するコンピューター名テンプレートを指定したり、[コンピューター名](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)を設定したりできるようになります。 これは、**[デバイスの登録]** > **[Windows の登録]** > **[Windows Autopilot Deployment service]\(Windows AutoPilot デプロイ サービス\)** > **[プロファイル]** にある Autopilot プロファイルに指定する必要があります。 英数字とハイフンのみ使用できます。
適用対象: Windows Insider 1809 以降のビルド (プレビューの間)。

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>iOS のバージョン番号とビルド番号が表示される <!-- 1892471 -->
**[デバイスのポリシー準拠]** の **[デバイスのポリシー準拠]** に iOS のオペレーティング システム バージョンが表示されます。 今後の更新で、ビルド番号も表示されるようになります。
セキュリティ更新がリリースされるとき、Apple は通常、バージョン番号を現状のまま残しますが、ビルド番号を更新します。 ビルド番号を表示することで、脆弱性更新がインストールされているかどうかを簡単に確認できます。

### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Windows Autopilot プロファイルの場合、会社のサインイン ページとドメイン エラー ページでアカウント変更オプションを非表示にする <!--1901669 -->
パブリック プレビューに、会社のサインイン ページとドメイン エラー ページでアカウント変更オプションを管理者が非表示にするための新しい Windows Autopilot プロファイル オプションが含まれます。 これらのオプションを非表示にするには、Azure Active Directory で会社のブランドを構成する必要があります。 適用対象: Windows Insider 1809 以降のビルド (プレビューの間)。

### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>iOS ソフトウェア更新がデバイスに表示されるときの遅延 <!-- 1949583 -->
Intune の **[ソフトウェアの更新]** の **[iOS のポリシーを更新する]** で、デバイスにあらゆる更新プログラムをインストールしない日時を構成できます。 今後の更新では、1 日から 90 日までの間で、ソフトウェア更新が表示されるタイミングを遅らせることができるようになります。 
[こちら](software-updates-ios.md)に Microsoft Intune で iOS 更新ポリシーを構成する方法が説明されていますが、ここに現在の設定が一覧になっています。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>[デバイスのポリシー準拠] ダッシュボードのデバイスが廃止に <!-- 1981119 -->
今後の更新で、廃止になっているデバイスが [デバイスのポリシー準拠] ダッシュボードから削除されます。 それにより、コンプライアンス番号が変更されます。

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>ポータル Web サイトの新しいユーザー エクスペリエンスの更新<!--2000968 -->
ユーザーからのフィードバックに基づき、新しい機能がポータル サイト Web サイトに追加されます。 Android、iOS、Windows デバイスから、既存の機能と使いやすさの大幅な向上を体験できます。 デバイス詳細、フィードバックとサポート、デバイス概要などのサイトの領域には、最新の応答性の高いデザインが採用されています。 また、次のような更新が行われています。
- すべてのデバイス プラットフォームでの簡素化されたワークフロー
- 強化されたデバイスの識別と登録のフロー
- 役に立つエラー メッセージ
- わかりやすい言語、少ない技術用語
- アプリへの直接リンクを共有する機能
- 大規模なアプリケーション カタログのパフォーマンスの向上
- すべてのユーザーに対するアクセシビリティの向上

### <a name="office-365-proplus-version----2213968-eeready---"></a>Office 365 ProPlus バージョン <!-- 2213968 eeready -->
Intune を利用して Office 365 ProPlus アプリを Windows 10 デバイスに割り当てるとき、Office のバージョンを選択できるようになります。 Azure portal で、**[Microsoft Intune]**、**[アプリ]**、**[アプリの追加]** の順に選択します。 次に、**[種類]** ドロップダウン リストから **[Office 365 ProPlus Suite (Windows 10)]** を選択します。 **[アプリ スイートの設定]** を選択し、関連ブレードを表示します。 **[更新チャネル]** を **[毎月]** などの値に設定します。 任意で、**[はい]** を選択し、エンド ユーザー デバイスから Office のその他のバージョン (msi) を削除します。 **[特定]** を選択すると、選択されているチャネルで特定のバージョンの Office がエンド ユーザー デバイスにインストールされます。 この時点で、使用する**特定のバージョン**の Office を選択できます。 使用できるバージョンは随時変更されます。 そのため、新しいデプロイを作成するとき、利用できるバージョンが新しく、特定の古いバージョンを利用できないことがあります。 現在のデプロイでは引き続き古いバージョンをデプロイできますが、バージョンの一覧はチャネル単位で継続的に更新されます。 詳細については、「[Office 365 ProPlus 更新プログラム チャネルの概要](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)」をご覧ください。

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>セットアップ アシスタント中、一部の画面をスキップするようにプロファイルを構成する <!-- 2276470 -->
macOS 登録プロファイルを作成するとき、セットアップ アシスタントを使用中のユーザーに表示される次の画面のスキップを構成できるようになります。
- Android 移行
- ディスプレイの色調
- プライバシー
- iCloudStorage

### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>オンプレミス コネクタの更新プロセスの変更 <!-- 2277554 -->
ユーザーからのフィードバックに基づき、オンプレミス コネクタの更新方法が変更されます。 オンプレミス コネクタの初回インストール後、更新は自動的に行われます。 この変更は新しい PFX Certificate Connector for Microsoft Intune から始まり、その後、その他の種類のオンプレミス コネクタにロールアウトされる予定です。 

### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Windows 10 VPN の DNS 登録設定をサポート <!-- 2282852 -->
カスタム プロファイルを使用しなくても、内部 DNS を使用し、VPN インターフェイスに割り当てられている IP アドレスを動的に登録するように Windows 10 VPN プロファイルを構成できるようになります。
Windows 10 VPN 設定に関する[こちら](vpn-settings-windows-10.md)のページに現在利用できる VPN プロファイル設定の一覧があります。 

### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-for-work-devices----2451462---"></a>iOS デバイスと Android for Work デバイスでアプリを制限し、会社のリソースへのアクセスをブロックする <!-- 2451462 -->
**[デバイスのポリシー準拠]**、**[ポリシー]**、**[ポリシーの作成]**、**[Android for Work]**、**[システム セキュリティ]** の順に選択したところに、**制限付きアプリケーション**の新しい設定が置かれる予定です。 この新しい設定ではコンプライアンス ポリシーが使用され、特定のアプリがデバイスにインストールされている場合、会社のリソースへのアクセスがブロックされます。 制限付きアプリケーションがデバイスから削除されるまで、デバイスは非準拠と見なされます。
適用先: 
- iOS

### <a name="export-azure-classic-portal-compliance-policies-to-csv-file----2469637---"></a>Azure クラシック ポータル コンプライアンス ポリシーを .csv ファイルにエクスポートする <!-- 2469637 -->
Azure クラシック ポータルで作成されたコンプライアンス ポリシーは非推奨になる予定です。  非推奨になったとき、既存のポリシーは確認したり、削除したりできますが、更新することはできません。 コンマ区切りファイル (.csv ファイル) としてポリシーをエクスポートできます。 エクスポート後、ファイルに含まれる詳細を利用し、Intune Azure portal でこれらのポリシーを再作成してください。
> [!IMPORTANT]
> Azure クラシック ポータルが廃止されると、ポリシーにアクセスできません。ポリシーを表示することもできません。 そのため、必ずポリシーをエクスポートし、Azure クラシック ポータルが廃止になる前に Azure portal で再作成してください。

### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>"削除" と "ワイプ" への用語変更 <!-- 2175759 -->
Graph API との一貫性を保つために、Intune のユーザー インターフェイスとドキュメントにおいて次の用語が変更されます。
- **[会社データの削除]** は **[削除]** に変更されます
- **[出荷時の設定にリセット]** は **[ワイプ]** に変更されます

### <a name="delete-jamf-devices----2653306---"></a>Jamf デバイスを削除する <!-- 2653306 -->
**[デバイス]** に移動し、Jamf デバイスを選択して、**[削除]** を選択することにより、Jamf で管理されたデバイスを削除できます。

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

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>構成プロファイルに自動的に追加される Windows Defender ATP 構成パッケージ <!-- 2144658 -->
Intune で [Advanced Threat Protection を使用してデバイスをオンボードする](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile)場合、現時点では、構成パッケージをダウンロードし、それを構成プロファイルに追加します。 今後の更新では、Intune で Windows Defender セキュリティ センターからパッケージを自動的に取得し、それをプロファイルに追加します。

Windows 10 以降に適用されます。

### <a name="check-for-sccm-compliance----2192052---"></a>SCCM コンプライアンスの確認 <!-- 2192052 -->
今後の更新には、新しい System Center Configuration Manager (SCCM) コンプライアンス設定 (**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[Windows 10]**) が含まれます。 SCCM は Intune コンプライアンスにシグナルを送信します。 Intune の設定を使用して、すべての SCCM シグナルで "準拠" を返すように要求することができます。

たとえば、すべてのソフトウェア更新プログラムをデバイスにインストールすることを要求します。 SCCM では、この要求は "インストール済み" 状態となります。 デバイス上のプログラムが不明な状態である場合、Intune ではデバイスが非準拠となります。

Windows 10 以降に適用されます

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP トークンの期限が切れているか、ポータル サイトのライセンスが不足している場合のアラート <!-- 2237572 -->
Volume Purchase Program (VPP) を使用して、DEP 登録時にポータル サイトを事前プロビジョニングする場合、Intune では、VPP トークンの有効期限が近づいている場合やポータル サイトのライセンスが不足している場合にアラートが表示されます。

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>ポータル サイトの事前プロビジョニングに使用されている VPP トークンを削除するために必要な構成 <!-- 2237634 -->
DEP 登録時にポータル サイトの事前プロビジョニングに Volume Purchase Program (VPP) トークンが使用されている場合、そのトークンを削除するための構成が必要になります。

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Windows インストーラーの追加のセキュリティ設定 <!-- 2282430 -->
ユーザーがアプリのインストールを制御することを許可できます。 有効にすると、セキュリティ違反が原因で本来は停止される可能性があるインストールを続行することが許可されます。 Windows インストーラーによってシステムに任意のプログラムをインストールする場合、管理者特権のアクセス許可を使用するよう Windows インストーラーに指示することができます。 さらに、Windows Information Protection (WIP) アイテムのインデックス付け、および暗号化されていない場所に格納されたそれらのアイテムに関するメタデータを有効にすることができます。 このポリシーが無効な場合、WIP で保護されたアイテムにはインデックスが付けられず、Cortana またはエクスプローラーの結果に表示されません。 既定では、これらのオプションの機能は無効になっています。 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS でのアプリ設定によりサード パーティ製キーボードをブロックできる <!-- 1248481 -->
Intune 管理者は、iOS デバイスで、ポリシーによって保護されているアプリ内の組織データにアクセスするときのサード パーティ製キーボードの使用をブロックすることができます。 サード パーティ製キーボードをブロックするようにアプリケーション保護ポリシー (APP) が設定されていると、デバイス ユーザーは、サード パーティ製キーボードを使って初めて企業データを操作するときに、メッセージを受け取ります。 ネイティブ キーボード以外のすべてのオプションはブロックされ、デバイスのユーザーに表示されません。 デバイス ユーザーにこのダイアログ メッセージが表示されるのは 1 回だけです。 

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

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>コールド アプリ起動時とタイムアウト時に生体認証ではないパスコードを要求する <!-- 1506985 --> 

コールド アプリ起動時と管理者指定のタイムアウト後に生体認証以外のパスコードを要求することにより、Intune は、企業データ アクセス用の生体認証 ID の使用を制限することで、モバイル アプリケーション管理 (MAM) が有効になっているアプリのセキュリティを強化します。 この設定は、Touch ID (iOS)、Face ID (iOS)、Android バイオメトリック、またはその他の将来の生体認証方法に依存して APP/MAM が有効なアプリケーションにアクセスするユーザーに影響します。 これらの設定により、Intune 管理者は、ユーザー アクセスをいっそうきめ細かく制御し、複数のフィンガープリントまたは他の生体認証アクセス方法を使うデバイスによって不適切なユーザーに会社のデータが公開されるのを防ぐことができます。 Azure Portal で **Microsoft Intune** を開きます。 **[モバイル アプリ]** > **[アプリ保護ポリシー]** > **[ポリシーの追加]** > **[設定]** の順に選びます。 特定の設定の **[アクセス]** セクションを探します。

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



