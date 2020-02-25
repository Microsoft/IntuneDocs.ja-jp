---
title: Microsoft Intune の新機能 - Azure | Microsoft Docs
titleSuffix: ''
description: Intune Azure Portal の新機能を確認する
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7018e2ab4290219c752f44b4b391822438461e8e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415078"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune の新機能

週ごとにまとめた、Microsoft Intune の新機能をご覧ください。 また、[重要なお知らせ](#notices)、[過去のリリース](whats-new-archive.md)、および [Intune サービスの更新プログラムのリリース方法](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)に関する情報もあります。 

> [!Note]
> 個々の[マンスリー更新プログラム](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)は、展開に最大 3 日かかることがあります。順序は次のとおりです。
>
> - 1 日目:アジア太平洋 (APAC)
> - 2 日目:ヨーロッパ、中東、アフリカ (EMEA)
> - 3 日目:北米
> - 4 日目以降:政府機関向け Intune
>
> 一部の機能は数週間にわたってロールアウトされ、一部のお客様は最初の週にご利用になれない可能性があります。
>
> リリースの今後の機能の一覧については、[開発中のページ](in-development.md)を参照してください。

**RSS フィード**:ご自身のフィード リーダーに次の URL をコピーして貼り付けることで、このページの更新時に通知を受け取ることができます。`https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  

<!-- ########################## -->
## <a name="week-of-february-10-2020"></a>2020 年 2 月 10 日の週

### <a name="windows-7-ends-extended-support---3042987--"></a>Windows 7 の延長サポートの終了 <!--3042987-->
Windows 7 の延長サポートは、2020 年 1 月 14 日に終了しました。 同時に、Intune では Windows 7 を稼働しているデバイスのサポートが非推奨になりました。 PC の保護に役立つ技術的なサポートや自動更新が利用できなくなりました。 Windows 10 にアップグレードする必要があります。 詳細については、[変更の計画に関するブログ記事](https://aka.ms/Windows7_Intune)を参照してください。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理

#### <a name="microsoft-edge-version-77-and-later-on-windows-10-devices---5843584---"></a>Windows 10 デバイスの Microsoft Edge バージョン 77 以降<!-- 5843584 -->
Intune で、Windows 10 デバイスでの Microsoft Edge バージョン 77 以降のアンインストールがサポートされるようになりました。 詳細については、「[Microsoft Edge for Windows 10 を Microsoft Intune に追加する](~/apps/apps-windows-edge.md)」を参照してください。

#### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>ポータル サイトの Android 仕事用プロファイルの登録から削除される画面<!--6103987 -->
ユーザー エクスペリエンスを効率化するために、ポータル サイトの Android 仕事用プロファイルの登録フローから **[次の手順]** 画面が削除されました。 更新後の Android 仕事用プロファイルの登録フローを確認するには、[Android 仕事用プロファイルへの登録](/intune-user-help/enroll-device-android-work-profile)に関する記事を参照してください。  

#### <a name="company-portal-app-improved-performance---6178652---"></a>ポータル サイト アプリのパフォーマンスの向上<!-- 6178652 -->
ポータル サイト アプリが更新され、Surface Pro X などの ARM64 プロセッサを使用したデバイス向けのパフォーマンスの向上がサポートされました。これまでは、ポータル サイトはエミュレートされた ARM32 モードで動作していました。 現在、バージョン 10.4.7080.0 以降では、ポータル サイト アプリは ARM64 用にネイティブ コンパイルされています。 ポータル サイト アプリの詳細については、「[Microsoft Intune ポータル サイト アプリを構成する方法](~/apps/company-portal-app.md)」をご覧ください。

<!-- ########################## -->
## <a name="week-of-january-27-2020"></a>2020 年 1 月 27 日の週

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理

#### <a name="intune-support-for-additional-microsoft-edge-version-77-deployment-channel-for-macos---5983950----"></a>macOS 用の追加の Microsoft Edge バージョン 77 展開チャネルの Intune サポート<!-- 5983950  -->
Microsoft Intune で、macOS 用 Microsoft Edge アプリの追加の **[安定]** 展開チャネルがサポートされるようになりました。 **[安定]** チャネルは、Microsoft Edge をエンタープライズ環境で幅広く展開する場合に推奨されるチャネルです。 これは 6 週間ごとに更新され、各リリースには **[Beta]** チャネルからの機能強化が組み込まれています。 **[安定]** および **[Beta]** チャネルに加えて、Intune では **[Dev]** チャネルもサポートされています。 パブリック プレビューでは、macOS 用の Microsoft Edge バージョン 77 以降の [安定] および [Dev] チャネルが提供されます。 ブラウザーの自動更新は、既定で有効になっています。 詳細については、[Microsoft Intune を使用した macOS デバイスへの Microsoft Edge の追加](~/apps/apps-edge-macos.md)に関する記事をご覧ください。

#### <a name="retirement-of-intune-managed-browser--5728447---"></a>Intune Managed Browser の提供終了<!--5728447 -->
Intune Managed Browser の提供は終了します。 保護された Intune ブラウザー エクスペリエンスには Microsoft Edge を使用してください。 詳細については、「[アクションの実行:保護されている Intune ブラウザーエクスペリエンスに Microsoft Edge を使用する](~/fundamentals/whats-new.md#take-action-use-microsoft-edge-for-your-protected-intune-browser-experience)」エントリ (下の「[通知](~/fundamentals/whats-new.md#notices)」セクション内) をご覧ください。

<!-- ########################## -->
## <a name="week-of-january-20-2020-2001-service-release"></a>2020 年 1 月 20 日の週 (2001 サービス リリース)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理

#### <a name="user-experience-change-when-adding-apps-to-intune---4705829-----"></a>Intune にアプリを追加するときのユーザー エクスペリエンスの変更<!-- 4705829   -->
Intune を使用してにアプリを追加するときに、新しいユーザー エクスペリエンスを確認できます。 このエクスペリエンスでは、以前使用していたのと同じ設定と詳細が提供されます。ただし、新しいエクスペリエンスでは、Intune にアプリを追加する前に、ウィザードに似たプロセスが実行されます。 この新しいエクスペリエンスでは、アプリを追加する前にレビュー ページも提供されます。 [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)から、 **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** の順に選択します。 詳しくは、「[Microsoft Intune にアプリを追加する](~/apps/apps-add.md)」をご覧ください。

#### <a name="require-win32-apps-to-restart----5622282-----"></a>Win32 アプリの再起動を要求する <!-- 5622282   -->
正常にインストールされた後、Win32 アプリの再起動を要求することができます。 また、再起動が発生するまでの時間 (猶予期間) を選択することもできます。

#### <a name="user-experience-change-when-configuring-apps-in-intune---4207990-----"></a>Intune でアプリを構成するときのユーザー エクスペリエンスの変更<!-- 4207990   -->
Intune でアプリ構成ポリシーを作成するときに、新しいユーザー エクスペリエンスを確認できます。 このエクスペリエンスでは、以前使用していたのと同じ設定と詳細が提供されます。ただし、新しいエクスペリエンスでは、Intune にポリシーを追加する前に、ウィザードに似たプロセスが実行されます。 [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) から、 **[アプリ]**  >  **[アプリ構成ポリシー]**  >  **[追加]** の順に選択します。 詳細については、「[Microsoft Intune 用アプリ構成ポリシー](~/apps/app-configuration-policies-overview.md)」を参照してください。 

#### <a name="intune-support-for-additional-microsoft-edge-for-windows-10-deployment-channel---5861774---"></a>追加の Windows 10 用 Microsoft Edge 展開チャネルの Intune サポート<!-- 5861774 -->
Microsoft Intune で、Windows 10 用 Microsoft Edge (バージョン 77 以降) アプリの追加の **[安定]** 展開チャネルがサポートされるようになりました。 **[安定]** チャネルは、Windows 10 用 Microsoft Edge をエンタープライズ環境で幅広く展開する場合に推奨されるチャネルです。 このチャネルは 6 週間ごとに更新され、各リリースには **[Beta]** チャネルからの機能強化が組み込まれています。 **[安定]** および **[Beta]** チャネルに加えて、Intune では **[Dev]** チャネルもサポートされています。 詳細については、[Windows 10 用 Microsoft Edge - アプリ設定の構成](~/apps/apps-windows-edge.md#configure-app-settings)に関する記事をご覧ください。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>デバイスの構成

#### <a name="improved-user-interface-experience-when-configuring-exchange-activesync-on-premises-connector-ui---5695492-----"></a>Exchange ActiveSync のオンプレミス コネクタ UI を構成するときのユーザー インターフェイス エクスペリエンスの向上<!-- 5695492   -->
[Exchange ActiveSync のオンプレミス コネクタを構成する](../protect/exchange-connector-install.md)ためのエクスペリエンスが更新されました。 更新されたエクスペリエンスでは、1 つのペインを使用して、オンプレミス コネクタの詳細を構成、編集、および要約することができます。 

#### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-----"></a>Android エンタープライズ仕事用プロファイルの Wi-Fi プロファイルに自動プロキシ設定を追加する<!-- 4490822   -->
Android Enterprise 仕事用プロファイル デバイスで、Wi-Fi プロファイルを作成できます。 Wi-Fi Enterprise の種類を選択した場合は、Wi-Fi ネットワークで使用される拡張認証プロトコル (EAP) の種類を入力することもできます。

今回、Enterprise の種類を選択したときに、プロキシ サーバーの URL (例: `proxy.contoso.com`) などの自動プロキシ設定も入力できるようになりました。

現在構成できる Wi-Fi の設定については、[Microsoft Intune で Android エンタープライズおよび Android キオスクを稼働しているデバイス用の Wi-Fi 設定を追加する方法](../configuration/wi-fi-settings-android-enterprise.md)に関する記事を参照してください。

適用対象:
- Android Enterprise 仕事用プロファイル

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>デバイスの登録

#### <a name="block-android-enrollments-by-device-manufacturer--5197392----"></a>デバイスの製造元で Android の登録をブロックする<!--5197392  -->
デバイスの製造元に基づいてデバイスの登録をブロックすることができます。 これは、Android デバイス管理者と Android Enterprise 仕事用プロファイル デバイスに適用されます。 登録制限を確認するには、[[Microsoft Endpoint Manager admin center]](https://go.microsoft.com/fwlink/?linkid=2109431) >  **[デバイス]**  >  **[登録制限]** の順に移動します。

#### <a name="improvements-to-the-iosipados-create-enrollment-type-profile-ui---6055005---"></a>iOS、iPadOS の [登録の種類のプロファイルの作成] UI の機能強化<!-- 6055005 -->
iOS、iPadOS のユーザー登録に関して、 **[登録の種類のプロファイルの作成]** の **[設定]** ページが合理化され、 **[登録の種類]** の選択プロセスが強化されました (機能は同じです)。 新しい UI を確認するには、[[Microsoft Endpoint Manager admin center]](https://go.microsoft.com/fwlink/?linkid=2109431) >  **[デバイス]**  >  **[iOS]**  >  **[iOS の登録]**  >  **[登録の種類]**  >  **[プロファイルの作成]**  >  **[設定]** の順に移動します。 詳細については、「[Intune でユーザー登録プロファイルを作成する](../enrollment/ios-user-enrollment.md#create-a-user-enrollment-profile-in-intune)」を参照してください。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>デバイス管理

#### <a name="new-information-in-device-details---4471759-5604099----"></a>デバイスの詳細の新しい情報<!-- 4471759 5604099  -->
デバイスの **[概要]** ページに、次の情報が追加されました。
- メモリ容量 (デバイスの物理メモリの容量)
- ストレージ容量 (デバイスの物理ストレージの容量) 
- CPU アーキテクチャ


#### <a name="ios-bypass-activation-lock-remote-action-renamed-to-disable-activation-lock---5904591----"></a>iOS の [アクティベーション ロックのバイパス] リモート操作の [アクティベーション ロックの無効化] への名前変更 <!--5904591  -->
リモート操作 **[アクティベーション ロックのバイパス]** の名前が、 **[アクティベーション ロックの無効化]** に変更されています。 詳細については、[Intuneで iOS のアクティベーション ロックを無効にする方法](../remote-actions/device-activation-lock-bypass.md)に関する記事をご覧ください。

#### <a name="windows-10-feature-update-deployment-support-for-autopilot-devices---5948137-----"></a>Autopilot デバイスに対する Windows 10 機能更新プログラムの展開のサポート<!-- 5948137   -->
Intune では、[Windows 10 機能更新プログラムの展開](../protect/windows-update-for-business-configure.md#windows-10-feature-updates)を使用して Autopilot に登録されたデバイスを対象にすることができるようになりました。

Windows 10 の機能更新ポリシーは、Autopilot の Out-of-Box Experience (OOBE) 中には適用できず、デバイスのプロビジョニングの完了後 (通常は 1 日)、最初の Windows Update のスキャン時にのみ適用されます。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="windows-autopilot-deployment-reports-preview----3856172-----"></a>Windows Autopilot の展開レポート (プレビュー) <!-- 3856172   -->
新しいレポートでは、Windows Autopilot によって展開された各デバイスについて詳しく報告されます。 詳しくは、[Autopilot の展開レポート](../enrollment/enrollment-autopilot.md#autopilot-deployments-report)に関するページをご覧ください。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>ロール ベースのアクセス制御

#### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-----"></a>新しい Intune 組み込みロールであるエンドポイント セキュリティ マネージャー<!--4253397   -->
新しい Intune 組み込みロール: エンドポイント セキュリティ マネージャーを利用できます。 この新しいロールにより、管理者には、Intune の Endpoint Manager ノードへのフル アクセス権、およびその他の領域への読み取り専用アクセス権が付与されます。 このロールは、Azure AD の "セキュリティ管理者" ロールを拡張したものです。 現在、ロールとしてグローバル管理者のみを使用している場合、変更は必要ありません。 ロールを使用し、エンドポイント セキュリティ マネージャーで提供される粒度が必要な場合は、使用可能であればそのロールを割り当てます。 組み込みロールの詳細については、[ロールベースのアクセス制御](role-based-access-control.md)に関するページを参照してください。

<!-- ########################## -->
## <a name="week-of-january-6-2020"></a>2020 年 1 月 6 日の週

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理

#### <a name="smime-support-for-microsoft-outlook-for-ios---2669398---"></a>Microsoft Outlook for iOS での S/MIME のサポート<!-- 2669398 -->
Intune では、iOS デバイス上の Outlook for iOS で使用できる S/MIME 署名証明書と暗号化証明書の配信がサポートされています。 詳細については、「[iOS 向けおよび Android 向け Outlook の秘密度ラベルと保護](https://aka.ms/omsmime)」を参照してください。

#### <a name="cache-win32-app-content-using-microsoft-connected-cache-server---6030314---"></a>Microsoft 接続キャッシュ サーバーを使用して Win32 アプリのコンテンツをキャッシュする<!-- 6030314 -->
Configuration Manager の配布ポイントに Microsoft 接続キャッシュ サーバーをインストールして、Intune Win32 アプリのコンテンツをキャッシュできます。 詳細については、「Configuration Manager における Microsoft 接続済みキャッシュ」の「[Intune Win32 アプリのサポート](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune)」を参照してください。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>ロール ベースのアクセス制御

#### <a name="windows-10-administrative-templates-admx-profiles-now-support-scope-tags---5137390---"></a>Windows 10 管理用テンプレート (ADMX) プロファイルでのスコープ タグのサポートの開始 <!--5137390 -->
スコープ タグを管理用テンプレート プロファイル (ADMX) に割り当てることができるようになりました。 これを行うには、 **[Intune]**  >  **[デバイス]**  >  **[構成プロファイル]** に移動し、一覧から管理用テンプレート プロファイルを選択して、 **[プロパティ]**  >  **[スコープ タグ]** を選択します。 スコープ タグの詳細については、「[スコープ タグを他のオブジェクトに割り当てる](../fundamentals/scope-tags.md#assign-scope-tags-to-other-objects)」をご覧ください。

<!-- ########################## -->
## <a name="week-of-december-30-2019"></a>2019 年 12 月 30 日の週

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理

#### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745---"></a>MEM 暗号化 macOS デバイスから個人用回復キーを取得する<!-- 4851745 -->
エンド ユーザーは、iOS ポータル サイト アプリを使用して個人用回復キー (FileVault キー) を取得できます。 個人用回復キーを持つデバイスは、Intune に登録され、Intune により FileVault を使用して暗号化されている必要があります。 iOS ポータル サイト アプリを使うと、エンド ユーザーは、 **[回復キーを取得する]** をクリックして、暗号化された macOS デバイス上の個人用回復キーを取得できます。 また、 **[デバイス]**  > "*暗号化されて登録された macOS デバイス*" >  **[回復キーの取得]** を選択することで、Intune から回復キーを取得することもできます。 FileVault の詳細については、「[macOS 用 FileVault 暗号化](~/protect/encrypt-devices.md#filevault-encryption-for-macos)」を参照してください。

#### <a name="ios-and-ipados-user-licensed-vpp-apps---5619268---"></a>iOS と iPadOS のユーザー ライセンス VPP アプリ<!-- 5619268 -->
ユーザーが登録した iOS および iPadOS デバイスの場合、エンド ユーザーには、利用可能として展開された、新しく作成されたデバイス ライセンス VPP アプリケーションが表示されなくなります。 ただし、エンド ユーザーには、Intune ポータル サイト内のすべてのユーザー ライセンス VPP アプリが引き続き表示されます。 VPP アプリの詳細については、「[Apple Volume Purchase Program で購入した iOS アプリと macOS アプリを Microsoft Intune で管理する方法](~/apps/vpp-apps-ios.md)」をご覧ください。

<!-- ########################## -->
## <a name="week-of-december-23-2019"></a>2019 年 12 月 23 日の週

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理

#### <a name="notice---windows-10-1703-rs2-will-be-moving-out-of-support----5026679---"></a>注意 - Windows 10 1703 (RS2) がサポート対象外になる <!-- 5026679 -->
2018 年 10 月 9 日以降、Windows 10 1703 (RS2) は、Home、Pro、および Pro for Workstations の各エディションに対する Microsoft プラットフォーム サポートの対象外になりました。 Windows 10 Enterprise および Education エディションについては、Windows 10 1703 (RS2) は 2019 年 10 月 8 日にプラットフォーム サポートの対象外になりました。 2019 年 12 月 26 日以降、Windows ポータル サイト アプリケーションの最小バージョンは Windows 10 1709 (RS3) に更新されます。 1709 より前のバージョンが実行されているコンピューターでは、アプリケーションの更新されたバージョンを Microsoft Store から受け取ることができなくなります。 古いバージョンの Windows 10 を管理しているお客様には、メッセージ センター経由でこの変更を既にお知らせしてあります。 詳細については、「[Windows ライフサイクルのファクト シート](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)」を参照してください。

<!-- ########################## -->

## <a name="week-of-december-16-2019"></a>2019 年 12 月 16 日の週

### <a name="device-configuration"></a>デバイスの構成

#### <a name="updates-to-administrative-templates-for-windows-10-devices----5941568---"></a>Windows 10 デバイス用の管理用テンプレートの更新 <!-- 5941568 -->

Microsoft Intune の ADMX テンプレートを使用して、Microsoft Edge、Office、Windows の設定を制御および管理できます。 Intune の管理用テンプレートでは、次のポリシー設定が更新されました。

- Microsoft Edge バージョン 78 および 79 のサポートが追加されました。
- [Office 365 ProPlus、Office 2019、Office 2016 のための管理用テンプレート ファイル (ADMX/ADML) および Office カスタマイズ ツール](https://www.microsoft.com/download/details.aspx?id=49030)には、2019 年 11 月 11 日の ADMX ファイルが含まれています。

Intune での ADMX テンプレートの詳細については、「[Windows 10 テンプレートを使用し、Microsoft Intune でグループ ポリシー設定を構成する](../configuration/administrative-templates-windows.md)」を参照してください。

適用対象:

- Windows 10 以降

## <a name="week-of-december-9-2019-1912-service-release"></a>2019 年 12 月 9 日の週 (1912 サービス リリース)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理

#### <a name="migrating-to-microsoft-edge-for-managed-browsing-scenarios---5173762---"></a>マネージド ブラウジング シナリオのための Microsoft Edge への移行<!-- 5173762 -->
Intune Managed Browser の提供終了が近づいているため、アプリ保護ポリシーを変更して、ユーザーを Edge に移動するために必要な手順を簡略化しました。 アプリ保護ポリシー設定 **[その他のアプリでの Web コンテンツの転送を制限する]** のオプションを、次のいずれかになるように更新しました。

- すべてのアプリ
- Intune Managed Browser
- Microsoft Edge
- アンマネージド ブラウザー 

**[Microsoft Edge]** を選択すると、マネージド ブラウジング シナリオには Microsoft Edge が必要であることを通知する、条件付きアクセス メッセージングがエンド ユーザーに表示されます。 自身の AAD アカウントを使用して Microsoft Edge をダウンロードし、サインインするように求められます (まだ行っていない場合)。  これは、アプリの構成設定 `com.microsoft.intune.useEdge` が **True** に設定されている MAM 対応アプリをターゲットにすることと同じです。 **ポリシーで管理されているブラウザー**設定を使用していた既存のアプリ保護ポリシーでは、 **[Intune Managed Browser]** が選択されるようになります。動作が変更されることはありません。 これは、**useEdge** アプリの構成設定を **True** に設定している場合は、ユーザーに Microsoft Edge を使用するようにメッセージングが表示されることを意味します。 アプリ保護ポリシーを更新するためにマネージド ブラウジング シナリオを利用しているすべてのお客様に、 **[その他のアプリでの Web コンテンツの転送を制限する]** を使用して、ユーザーがどのアプリからリンクを起動しているかに関係なく、Microsoft Edge に移行するための適切なガイダンスがユーザーに表示されるようにすることをお勧めします。 

#### <a name="configure-app-notification-content-for-organization-accounts---2576686----"></a>組織アカウント向けのアプリ通知の内容を構成する<!-- 2576686  -->
Android および iOS デバイスで Intune アプリ保護ポリシー (APP) を使用すると、組織アカウントに対するアプリ通知の内容を制御できます。 オプション ([許可]、[組織データをブロック]、[ブロック済み]) を選択して、選択したアプリでの組織アカウント向けの通知の表示方法を指定できます。この機能は、アプリケーションからのサポートを必要とし、APP 対応のすべてのアプリケーションで使用できるとは限りません。 Outlook for iOS バージョン 4.15.0 (以降) および Outlook for Android 4.83.0 (以降) では、この設定がサポートされます。 コンソールでは設定を使用できますが、機能が有効になるのは 2019 年 12 月 16 日以降です。 アプリの詳細については、「[アプリ保護ポリシーとは](../apps/app-protection-policy.md)」を参照してください。

#### <a name="microsoft-app-icons-update--4677605----"></a>Microsoft アプリ アイコンの更新<!--4677605  -->
アプリ保護ポリシーとアプリ構成ポリシーのアプリ ターゲット設定ウィンドウで Microsoft アプリに対して使用されるアイコンが更新されました。

#### <a name="require-use-of-approved-keyboards-on-android--4761794----"></a>Android で承認済みキーボードの使用を要求する<!--4761794  -->
アプリ保護ポリシーの一部として、[**承認済みキーボード**](../apps/app-protection-policy-settings-android.md#data-protection)の設定を指定し、マネージド Android アプリで使用できる Android キーボードを管理できます。 ユーザーがマネージド アプリを開いたとき、そのアプリに対する承認済みキーボードが使われていない場合は、デバイスに既にインストールされている承認済みキーボードのいずれかに切り替えるように求められます。 必要に応じて、承認済みキーボードを Google Play ストアからダウンロードするためのリンクが表示されます。このリンクを使用して、インストールとセットアップを行うことができます。 アクティブなキーボードが承認済みキーボードでない場合、ユーザーがマネージド アプリで編集できるのはテキスト フィールドだけです。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>デバイスの構成

#### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578----"></a>iOS、iPadOS、macOS デバイスでのアプリと Web サイトに対するシングル サインオン エクスペリエンスが更新された<!-- 4999578  -->
Intune では、iOS、iPadOS、macOS デバイス向けのシングル サインオン (SSO) の設定が追加されました。 組織または ID プロバイダーによって作成されたリダイレクト SSO アプリ拡張機能を構成できるようになりました。 これらの設定は、OAuth や SAML2 などの最新の認証方法を使用するアプリと Web サイトに対してシームレスなシングル サインオン エクスペリエンスを構成するために使用します。 

これらの新しい設定では、SSO アプリ拡張機能および Apple の組み込み Kerberos 拡張機能に対する以前の設定が拡張されます ( **[デバイス]**  >  **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS/iPadOS]** または **[macOS]** (プラットフォームの種類) > **[デバイス機能]** (プロファイルの種類))。 

構成できるすべての SSO アプリ拡張機能の設定については、[iOS での SSO](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) および [macOS での SSO](../configuration/macos-device-features-settings.md#single-sign-on-app-extension) に関する記事を参照してください。

適用対象:

- iOS/iPadOS
- macOS

#### <a name="we-have-updated-two-device-restriction-settings-for-ios-and-ipados-devices-to-correct-their-behavior---5701352------"></a>動作を修正するため、iOS および iPadOS デバイスに対する 2 つのデバイス制限設定を更新した<!-- 5701352    -->
iOS デバイスの場合、 **[無線による PKI の更新を許可する]** および **[USB 制限モードをブロックする]** が有効なデバイス制限プロファイルを作成できま ( **[デバイス]**  >  **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS/iPadOS]** (プラットフォーム) > **[デバイスの制限]** (プロファイルの種類))。 このリリースより前では、次の設定の UI 設定と説明は正しくありませんでしたが、現在は修正されています。 このリリース以降では、設定の動作は次のようになります。

**[無線による PKI の更新をブロックする]** : **[Block]\(ブロックする\)** に設定すると、デバイスがコンピューターに接続されていない場合、ユーザーはソフトウェア更新プログラムを受信できません。 **[未構成]** (既定値): コンピューターに接続されていなくても、デバイスはソフトウェア更新プログラムを受信できます。
- 以前のこの設定では、次のように構成できます: **[許可]** を選択すると、ユーザーはデバイスをコンピューターに接続せずにソフトウェア更新プログラムを受信できるようになります。
**[デバイスのロック中に USB アクセサリの使用を許可する]** : **[許可]** を選択すると、USB アクセサリは 1 時間以上ロックされているデバイスとデータを交換できます。 **[未構成]** (既定値) では、デバイスでの USB 制限モードは更新されず、USB アクセサリは、1 時間以上ロックされている場合、デバイスからのデータの転送をブロックされます。
- 以前のこの設定では、次のように構成できます: **[ブロック]** を選択すると、監視対象のデバイスで USB 制限モードが無効になります。

構成できる設定の詳細については、「[Intune を使用した機能を許可または制限するための iOS および iPadOS デバイスの設定](../configuration/device-restrictions-ios.md)」を参照してください。

この機能は、以下に適用されます。

- iOS/iPadOS

#### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>macOS デバイス用の有線ネットワーク デバイス構成プロファイル<!-- 3508686  -->
   > [!NOTE]
   > この機能は遅れていますが、間もなくリリースされる予定です。

#### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998---"></a>Android Enterprise デバイス所有者デバイスでマネージド キーストア内の証明書資格情報をユーザーが構成できないようにする<!-- 3311998 -->
Android Enterprise デバイス所有者デバイスでは、マネージド キーストア内の証明書資格情報をユーザーが構成できないようにする新しい設定を構成できます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Android Enterprise]** (プラットフォーム) > **[デバイスの所有者のみ] > [デバイスの制限]** (プロファイルの種類) > **[ユーザーとアカウント]** )。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>デバイス管理

#### <a name="protected-wipe-action-now-available--51150000---"></a>保護されたワイプ アクションを使用できるようになった<!--51150000 -->
デバイスのワイプ アクションを使用して、デバイスの保護されたワイプを実行できるようになりました。 保護されたワイプは標準のワイプと同じですが、デバイスの電源をオフにしても回避できない点が異なります。 保護されたワイプは、成功するまでデバイスをリセットしようとします。 一部の構成では、このアクションによってデバイスを再起動できなくなる場合があります。 詳細については、[デバイスのインベントリからの削除またはワイプ](../remote-actions/devices-wipe.md)に関する記事を参照してください。

#### <a name="device-ethernet-mac-address-added-to-devices-overview-page--5562275---"></a>デバイスの [概要] ページにデバイスのイーサネット MAC アドレスが追加された<!--5562275 -->
デバイスの詳細ページで、デバイスのイーサネット MAC アドレスを確認できるようになりました ( **[デバイス]**  >  **[すべてのデバイス]** > デバイスを選択 > **[概要]** )。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>デバイス セキュリティ

#### <a name="improved-experience-on-a-shared-device-when-device-based-conditional-access-policies-are-enabled---1734096----"></a>デバイス ベースの条件付きアクセス ポリシーが有効になっているときの、共有デバイスでのエクスペリエンスが向上した<!-- 1734096  -->
ポリシーの適用時にユーザーの最新のコンプライアンス評価をチェックすることで、デバイス ベースの条件付きアクセス ポリシーの対象となっている複数のユーザーが使用する共有デバイスでのエクスペリエンスが向上しました。 詳細については、以下の概要記事を参照してください。
- [Azure での条件付きアクセスの概要](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Intune でのデバイス コンプライアンスの概要](../protect/device-compliance-get-started.md)

#### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529----"></a>PKCS 証明書プロファイルを使用し、証明書でデバイスをプロビジョニングする<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529  -->
Wi-Fi や VPN のようなプロファイルに関連付けられている場合に、PKCS 証明書プロファイルを使用して、Android for Work、iOS、および Windows を実行する "*デバイス*" に証明書を発行できるようになりました。 以前は、それら 3 つのプラットフォームではユーザー ベースの証明書のみがサポートされており、デバイス ベースのサポートは macOS に限定されていました。

> [!NOTE]
> PKCS 証明書プロファイルは、Wi-Fi プロファイルではサポートされていません。 代わりに、[EAP の種類](../configuration/wi-fi-settings-windows.md#enterprise-profile)を使用する場合は SCEP 証明書プロファイルを使用します。

デバイス ベースの証明書を使用するには、サポートされるプラットフォーム用の [PKCS 証明書プロファイルを作成する](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile)ときに、 **[設定]** を選択します。 **[証明書の種類]** の設定が表示されるようになり、そこでは [デバイス] または [ユーザー] のオプションがサポートされています。



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="centralized-audit-logs--5603185-5697164---"></a>一元化された監査ログ<!--5603185, 5697164 -->
新しい一元化された監査ログ エクスペリエンスでは、すべてのカテゴリの監査ログが 1 ページに収集されるようになりました。 ログをフィルター処理して、探しているデータを取得できます。 監査ログを表示するには、 **[テナント管理]**  >  **[監査ログ]** に移動します。 

#### <a name="scope-tag-information-included-in-audit-log-activity-details--5763534---"></a>監査ログ アクティビティの詳細に組み込まれたスコープ タグ情報<!--5763534 -->
監査ログ アクティビティの詳細に、スコープ タグ情報が含まれるようになりました (スコープ タグをサポートする Intune オブジェクトの場合)。 監査ログの詳細については、[監査ログを使用したイベントの追跡と監視](monitor-audit-logs.md)に関する記事を参照してください。


<!-- ########################## -->
## <a name="week-of-december-2-2019"></a>2019 年 12 月 2 日の週

#### <a name="new-microsoft-endpoint-configuration-manager-co-management-licensing--5027281--"></a>新しい Microsoft Endpoint Configuration Manager の共同管理ライセンス<!--5027281-->
ソフトウェア アシュアランスをお持ちの Configuration Manager のお客様は、Windows 10 PC 向けの Intune 共同管理を利用できるようになりました。共同管理のために追加の Intune ライセンスを購入する必要はありません。 Windows 10 を共同管理するために個別の Intune または EMS ライセンスをエンド ユーザーに割り当てる必要はなくなりました。
- Configuration Manager によって管理され、共同管理に登録されているデバイスは、Intune スタンドアロン MDM のマネージド PC とほぼ同じ権限を持ちます。 ただし、これらをリセットすると、オートパイロットを使用して再プロビジョニングすることはできません。
- 他の方法を使用して Intune に登録された Windows 10 デバイスには、Intune のフル ライセンスが必要です。
- その他のプラットフォームのデバイスには、引き続き Intune のフル ライセンスが必要です。

詳細については、[ライセンス条項](https://www.microsoft.com/en-us/Licensing/product-licensing/products)を参照してください。


<!-- ########################## -->
## <a name="week-of-november-18-2019-1911-service-release"></a>2019 年 11 月 18 日の週 (1911 サービス リリース)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>アプリ データを選択的にワイプするときの UI の更新<!-- 4102028 -->
Intune でアプリ データを選択的にワイプするための UI が更新されました。 UI に対する次のような変更があります。
- ウィザード方式による簡単操作が 1 つのウィンドウ内に凝縮されました。
- 作成フローを更新し、割り当てを含めました。
- プロパティを表示するときに、新しいポリシーを作成する前に、プロパティを編集するときに、まとめページに全部設定されます。 また、プロパティを編集するとき、編集されるプロパティのカテゴリから項目の一覧のみがまとめに表示されます。

詳細については、「[Intune で管理されているアプリから会社のデータをワイプする方法](~/apps/apps-selective-wipe.md)」を参照してください。

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>iOS と iPadOS のサードパーティ キーボードのサポート<!-- 4922950 -->
2019 年 3 月に、iOS アプリ保護ポリシー設定の "サードパーティのキーボード" のサポートが削除されたことが発表されました。 この機能は、iOS と iPadOS の両方のサポートと共に Intune に再び備わります。 この設定を有効にするには、新規または既存の iOS および iPadOS アプリ保護ポリシーの **[データ保護]** タブを開いて、 **[データ転送]** で **[サードパーティのキーボード]** 設定を見つけます。

このポリシー設定の動作は、以前の実装と若干異なります。 SDK バージョン 12.0.16 以降を使用するマルチ ID アプリでは、この設定が **[ブロック]** に構成されているアプリ保護ポリシーにより、エンド ユーザーは組織と個人の両方のアカウントでサードパーティのキーボードを選択できなくなります。 SDK バージョン 12.0.12 以前を使用しているアプリでは、引き続き[既知の問題: 個人用アカウントの iOS でサードパーティのキーボードがブロックされない](https://aka.ms/3rdparty_iOS_Intune)という問題に関するブログ投稿に記載された動作が発生します。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>デバイスの構成

#### <a name="target-macos-user-groups-to-require-jamf-management---4061739----"></a>Jamf による管理を必要とする macOS ユーザー グループをターゲットにする<!-- 4061739  --> 
[Jamf による macOS デバイスの管理](../protect/conditional-access-integrate-jamf.md)を利用する特定のユーザー グループをターゲットにすることができます。 これにより、macOS デバイスのサブセットに Jamf コンプライアンス統合を適用しながら、その他のデバイスを Intune によって管理することができます。 Jamf 統合を既に使用している場合は、すべてのユーザーが既定で統合のターゲットとなります。

#### <a name="new-exchange-activesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824-----"></a>iOS デバイスでメール デバイス構成プロファイルを作成するときの新しい Exchange ActiveSync 設定<!-- 4892824   --> 
iOS および iPadOS デバイスにおいて、デバイス構成プロファイルでメール接続を構成できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS および iPadOS]** (プラットフォーム) > **[メール]** (プロファイルの種類))。 

次のような新しい Exchange ActiveSync 設定を使用できます。
- **[同期する Exchange データ]** :予定表、連絡先、アラーム、メモ、メールに対して同期する (または同期をブロックする) Exchange サービスを選択します。
- **[同期の設定の変更をユーザーに許可する]** :デバイスでこれらのサービスの同期設定を変更することをユーザーに許可 (またはブロック) します。  

これらの設定の詳細については、[Intune での iOS デバイスのメール プロファイル設定](../configuration/email-settings-ios.md)に関するページを参照してください。 

適用対象:

- iOS 13.0 以降
- iPadOS 13.0 以降

#### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-fully-managed-and-dedicated-devices---5353228-----"></a>Android Enterprise のフル マネージド専用デバイスにユーザーが個人用 Google アカウントを追加できないようにする<!-- 5353228   -->
Android Enterprise のフル マネージド専用デバイスには、ユーザーが個人用 Google アカウントを作成できないようにする新しい設定があります ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Android Enterprise]** (プラットフォーム) > **[デバイスの所有者のみ] > [デバイスの制限]** (プロファイルの種類) > **[ユーザーとアカウント] 設定** >  **[個人用 Google アカウント]** )。

構成できる設定を確認するには、「[Intune を使用して機能を許可または制限するように Android エンタープライズ デバイスを設定する](../configuration/device-restrictions-android-for-work.md)」をご覧ください。

適用対象:

- Android エンタープライズのフル マネージド デバイス
- Android Enterprise 専用デバイス

#### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-iosipados-device-restrictions-profile----5468501-----"></a>iOS および iPadOS デバイス制限プロファイルから Siri コマンド設定のサーバー側のログ記録が削除されます <!-- 5468501   -->
iOS および iPadOS デバイスでは、Microsoft Endpoint Manager 管理コンソールから **Siri コマンド**設定のサーバー側のログ記録が削除されます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS および iPadOS]** (プラットフォーム) > **[デバイスの制限]** (プロファイルの種類) > **[組み込みアプリ]** )。 

この設定は、デバイスには影響を与えません。 既存のプロファイルから設定を削除するには、プロファイルを開いて変更を加え、プロファイルを保存します。 プロファイルが更新され、デバイスから設定が削除されます。

構成できるすべての設定を確認するには、[Intune を使用した機能を許可または制限するための iOS および iPadOS デバイスの設定](../configuration/device-restrictions-ios.md)に関するページを参照してください。

適用対象:

- iOS/iPadOS

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Windows 10 機能更新プログラム (パブリック プレビュー)<!-- 2384877 -->
[Windows 10 機能更新プログラム](../protect/windows-update-for-business-configure.md#windows-10-feature-updates)を Windows 10 デバイスに展開できるようになりました。 Windows 10 機能更新プログラムは、デバイスにインストールして維持する必要がある Windows 10 のバージョンを設定できる、新しいソフトウェア更新プログラムのポリシーです。 この新しいポリシーの種類は、既存の Windows 10 更新プログラムのリングと共に使用できます。

Windows 10 機能更新ポリシーを受け取ったデバイスでは、指定されたバージョンの Windows がインストールされ、そのポリシーが編集または削除されるまでそのバージョンにとどまります。 より新しいバージョンの Windows を稼働しているデバイスは、その現在のバージョンにとどまります。 Windows の特定のバージョンで固定されているデバイスでも、Windows 10 更新プログラムのリングから、そのバージョンの品質更新プログラムおよびセキュリティ更新プログラムをインストールできます。

この新しい種類のポリシーは、今週テナントへのロールアウトが開始されます。 ご自分のテナントでまだこのポリシーを使用できない場合は、間もなく使用できるようになります。

#### <a name="add-and-change-key-information-in-plist-files-for-macos-applications---4736278---"></a>macOS アプリケーションの plist ファイルのキー情報を追加および変更する<!-- 4736278 -->
macOS デバイスでは、アプリまたはデバイスに関連付けられているプロパティ リスト ファイル (.plist) をアップロードするデバイス構成プロファイルを作成できるようになりました ( **[デバイス]**  >  **[構成プロファイル]**  >  **[プロファイルの作成]**  >  **[macOS]** (プラットフォーム) > **[設定ファイル]** (プロファイルの種類))。

マネージド基本設定は一部のアプリでのみサポートされており、これらのアプリではすべての設定を管理できるとは限りません。 ユーザー チャネルの設定ではなく、デバイス チャネルの設定を構成するプロパティ リスト ファイルを必ずアップロードします。

この機能の詳細については、[Microsoft Intune を使用した macOS デバイスへのプロパティ リスト ファイルの追加](../configuration/preference-file-settings-macos.md)に関するページを参照してください。

適用対象:

- 10.7 以降を実行している macOS デバイス

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>デバイス管理

#### <a name="edit-device-name-value-for-autopilot-devices---2640074---"></a>Autopilot デバイスの [デバイス名] 値を編集する<!-- 2640074 -->
Azure AD 参加済み Autopilot デバイスの [デバイス名] 値を編集できます。  詳細については、[Autopilot デバイスの属性の編集](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes)に関するページを参照してください。

#### <a name="edit-group-tag-value-for-autopilot-devices---4816775-----"></a>Autopilot デバイスの [グループ タグ] 値を編集する<!-- 4816775   -->
Autopilot デバイスの [グループ タグ] 値を編集できます。 詳細については、[Autopilot デバイスの属性の編集](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes)に関するページを参照してください。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="updated-support-experience---5012398---"></a>更新されたサポート エクスペリエンス<!-- 5012398 -->

本日から、[Intune のヘルプとサポートの取得](get-support.md)に関する、更新および合理化されたコンソール内のエクスペリエンスがテナントにロールアウトされます。 お客様がまだこの新しいエクスペリエンスを利用できない場合は、間もなく利用できるようになります。

コンソール内でのよくあるイシューの検索とフィードバック、およびサポートへの問い合わせに使用するワークフローが改善されました。 サポート イシューを作成するときに、コールバックまたはメールの返信をいつ受け取ることができるのかについての推定が、リアルタイムで表示されます。また、Premier および統合サポートのお客様は、より迅速なサポートを受けるために、それぞれのイシューについて、簡単に重大度を指定できます。

#### <a name="improved-intune-reporting-experience-public-preview----3791418---"></a>Intune レポート エクスペリエンスの向上 (パブリック プレビュー) <!-- 3791418 -->
Intune では、新しいレポートの種類、より優れたレポート編成、より対象を絞ったビュー、より優れたレポート機能、より一貫性のあるタイムリーなデータを含め、レポート エクスペリエンスが向上しています。 新しいレポートの種類では、次のことに重点が置かれています。
- **運用** - 正常性への悪影響に焦点を置いた最新のレコードが表示されます。 
- **組織** - 全体的な状態の概要が表示されます。
- **履歴** - 一定期間におけるパターンと傾向が表示されます。
- **スペシャリスト** - 生データを使用して独自のカスタム レポートを作成できます。

新しいレポートの最初のセットでは、デバイスのコンプライアンスに重点が置かれています。 詳細については、[ブログ - Microsoft Intune レポート フレームワーク](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553)および[Intune レポート](~/fundamentals/reports.md)に関するページを参照してください。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>ロール ベースのアクセス制御

#### <a name="duplicate-custom-or-built-in-roles----1081938-----"></a>カスタム ロールまたは組み込みロールを複製する <!-- 1081938   -->
組み込みロールとカスタム ロールをコピーできるようになりました。 詳細については、[ロールのコピー](../fundamentals/create-custom-role.md#copy-a-role)に関するページを参照してください。

#### <a name="new-permissions-for-school-administrator-role----5621805----"></a>学校管理者ロールの新しいアクセス許可 <!-- 5621805  -->  
学校管理者ロール > **[アクセス許可]**  >  **[登録プログラム]** に、2 つの新しいアクセス許可である **[プロファイルの割り当て]** と **[デバイスの同期]** が追加されました。 [デバイスの同期] アクセス許可を使用すると、グループ管理者は Windows Autopilot デバイスを同期できます。 [プロファイルの割り当て] アクセス許可を使用すると、これらの管理者はユーザーが開始した Apple 登録プロファイルを削除できます。 また、Autopilot デバイスの割り当てと Autopilot 展開プロファイルの割り当てを管理するためのアクセス許可も付与されます。 すべての学校管理者またはグループ管理者のアクセス許可の一覧については、[グループ管理者の割り当て](https://docs.microsoft.com/intune-education/group-admin-delegate)に関するページを参照してください。 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="security"></a>セキュリティ

#### <a name="bitlocker-key-rotation---2564951----"></a>BitLocker キーの交換<!-- 2564951  -->
Intune デバイス アクションを使用することで、Windows バージョン 1909 以降を実行するマネージド デバイスの [BitLocker 回復キーをリモートで交換](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys)できます。 回復キーが交換されるようにするには、回復キーの交換をサポートするようにデバイスを構成する必要があります。  

#### <a name="updates-to-dedicated-device-enrollment-to-support-scep-device-certificate-deployment----5198878----"></a>SCEP デバイス証明書の展開をサポートするための専用デバイス登録の更新 <!-- 5198878  -->
Intune では、Wi-Fi プロファイルに証明書ベースでアクセスできるよう、Android Enterprise 専用デバイスへの SCEP デバイス証明書の展開がサポートされるようになりました。 展開が機能するには、Microsoft Intune アプリがデバイス上に存在する必要があります。 そのため、Android Enterprise 専用デバイスの登録エクスペリエンスが更新されました。 新しい登録は、今までと同様に (QR、NFC、ゼロタッチ、またはデバイス識別子を使用して) 開始されますが、ユーザーが Intune アプリをインストールすることが必要になりました。 既存のデバイスでは、アプリのインストールがローリング方式で自動的に開始されます。

#### <a name="intune-audit-logs-for-business-to-business-collaboration--5670211---"></a>企業間コラボレーションのための Intune 監査ログ<!--5670211 -->
企業間 (B2B) コラボレーションにより、会社のアプリケーションやサービスを他の組織のゲスト ユーザーと安全に共有しながら、自社データの管理を維持することができます。 Intune では、B2B ゲスト ユーザーの監査ログがサポートされるようになりました。 たとえば、ゲスト ユーザーが変更を行うと、Intune では監査ログを使用してこのデータをキャプチャできます。 詳細については、[Azure Active Directory B2B でのゲスト ユーザー アクセス](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)に関するページを参照してください。


<!-- ########################## -->
## <a name="week-of-november-11-2019"></a>2019 年 11 月 11 日の週  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理  

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>ポータル サイトにおける macOS の登録エクスペリエンスの改善 <!-- 5074349  -->  
macOS の登録エクスペリエンス用のポータル サイトには、よりシンプルな登録プロセスが備わっています。これにより、iOS の登録エクスペリエンス用のポータル サイトと、より厳密な一致がとれます。 デバイス ユーザーに次が表示されるようになりました。  

* より洗練されたユーザー インターフェイス。  
* 強化された登録チェックリスト。  
* デバイスの登録方法に関するより明確な説明。  
* 強化されたトラブルシューティング オプション。  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>Windows ポータル サイト アプリから起動する Web アプリ<!-- 5030972 -->
エンドユーザーは、Windows ポータル サイト アプリから直接 Web アプリを起動できるようになりました。 エンドユーザーは、Web アプリを選択してから、 **[ブラウザーで開く]** オプションを選択できます。 発行された Web URL は、Web ブラウザー内で直接開かれます。 この機能は、次の週にわたってロールアウトされます。 Web アプリの詳細については、「[Web アプリを Microsoft Intune に追加する](~/apps/web-app.md)」をご覧ください。  


#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950----"></a>Windows 10 のポータル サイトにおける新しい割り当ての種類の列 <!-- 5459950  -->
ポータル サイト > **[インストール済みアプリ]**  >  **[割り当ての種類]** 列の名前が、 **[組織で必要]** に変更されました。  その列の下に、アプリが組織によって必須、省略可能のいずれに設定されているかを示す **[はい]** または **[いいえ]** の値がユーザーに表示されます。 デバイス ユーザーが利用可能なアプリの概念について混乱していたため、このような変更が行われました。 ユーザーは、「[デバイスにアプリをインストールして共有する](/intune-user-help/install-apps-cpapp-windows)」で、ポータル サイトからのアプリのインストールに関する詳細情報を参照できます。 ユーザーに対するポータル サイト アプリの構成方法の詳細については、「[Microsoft Intune ポータル サイト アプリを構成する方法](~/apps/company-portal-app.md)」をご覧ください。  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>2019 年 11 月 4 日の週

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>デバイス セキュリティ

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>セキュリティ ベースラインが Microsoft Azure Government でサポートされる<!-- 4062552 -->

*Microsoft Azure Government* でホストされている Intune のインスタンスで、[セキュリティ ベースライン](../protect/security-baselines.md)を使用して、ユーザーとデバイスのセキュリティ保護と保護を行えるようになりました。

## <a name="whats-new-archive"></a>新機能の公開履歴
以前の月については、[新機能の公開履歴](whats-new-archive.md)を参照してください。

## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
