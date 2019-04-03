---
title: で開発 - Microsoft Intune
titlesuffix: ''
description: Microsoft Intune の機能の開発
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e068e2c9834290b705e8e7bc2f895636415f9ba
ms.sourcegitcommit: 69aaf89140f82f344404e75a69dc59d8a1585b10
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675444"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>Microsoft Intune の - 年 2019年 4 月の開発

準備が整っているし、計画、このページで支援するために Intune UI の更新プログラムし、機能をリストは、開発中がリリースされていません。 さらに

- 予想、変更する前にアクションを実行する必要があります、無償の Office メッセージ センター投稿を公開しますします。
- 機能がプレビューとして、運用環境で起動するか、一般公開機能の説明はこのページを無効と移動にときに、[は新しいページ](whats-new.md)します。
- このページと[は新しいページ](whats-new.md)定期的に更新されます。 適宜確認してください。
- 参照してください、 [M365 ロードマップ](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)の戦略的な成果物、およびタイムライン。

> [!Note]
> これらの項目には、将来のリリースで導入される Intune の機能について Microsoft の現在の予測が反映されます。 日付と個々 の機能を変更することがあります。 開発ではすべてのアイテムでは、このページで、機能の説明があります。

**RSS フィード**: ご自身のフィード リーダーに次の URL をコピーして貼り付けることで、このページの更新時に通知を受け取ることができます。`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>ログイン設定を設定し、macOS デバイスでの再起動オプションを制御します。 <!-- 1210083 -->
MacOS デバイスでデバイス構成プロファイルを作成することができます (**デバイス構成** > **プロファイル** > **プロファイルを作成する**>選択**macOS**プラットフォーム >**デバイス機能**のプロファイルの種類)。 新しいログイン ウィンドウの設定はカスタム バナーを表示するなどの項目が含まれます、どのユーザー サインインを表示またはや、電源設定を非表示に選択します。

現在の設定を確認するには[macOS デバイスの機能設定](macos-device-features-settings.md)します。

適用されます macOS。

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Windows Defender ファイアウォールの詳細設定 <!-- 1311949 -->
さらに、Intune を使用して、Windows Defender のクライアントでのカスタム ファイアウォール規則を管理することが間もなくなります。 ルールは、アプリケーション、ネットワーク アドレス、およびポートに受信および送信の動作を指定できます。 

### <a name="require-app-protection-conditional-access----1634317---"></a>アプリ保護の条件付きアクセスが必要です。  <!--1634317 -->
使用できる*必要なアプリ保護ポリシー*をユーザーが条件付きアクセスを保護するデータにアクセスすることを防ぐためにサインインが完了する前に、ユーザーのアプリに適用がポリシーを確認します。 ポリシーの保証には、最初の使用経験が遅く、中には、ネットワークの問題、管理構成の誤り、またはアプリケーション保護ポリシーを阻止する意図的な取り組みに対して保護するのに役立ちます。 

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----16726660---"></a>オンラインでライセンスされたビジネス向け Microsoft Store アプリの展開 <!-- 16726660 -->
オンラインでライセンスされた必要なビジネス向け Microsoft Store アプリをデバイスのコンテキストで割り当てることができます。 このようにして、ビジネス向け Microsoft Store アプリを展開すると、デバイス上のすべてのユーザーにアプリをインストールできます。 対象は Windows 10 RS4 以上のデスクトップ デバイスのみです。 デバイスのコンテキストでインストールするオプションは、MSFB オンラインのライセンスされたアプリのクライアント アプリの割り当てページにあります。

### <a name="include-and-exclude-mixture-of-user-groups-and-device-groups-when-assigning-policies-and-profiles----1807547---"></a>ポリシーとプロファイルを割り当てるときに、ユーザー グループとデバイス グループの組み合わせを含めたり除外したり <!-- 1807547 -->
コンプライアンス ポリシーまたは構成プロファイルに割り当てるときに割り当てることができますをセキュリティ グループにユーザーまたはデバイスとします。 現時点では、含めるし、ユーザーのグループのみを除外する*または*およびデバイス グループのみを除外します。 含めるとグループの組み合わせを除外するなどのユーザー グループを含めることはできません*と*デバイス グループを除外します。

さまざまなユーザー グループおよびデバイス グループを含めたり除外したりすることができます。 ユーザーのグループを含めるし、デバイスのグループを除外することができます。 たとえば、割り当てる、ユーザーのグループに、デバイス構成プロファイルを展開またはが個人のデバイスを除外します。

[デバイス構成プロファイルを割り当てる](device-profile-assign.md)ユーザー グループとデバイス グループにプロファイルを割り当てる方法に関する詳細が含まれています。

適用対象: すべてのプラットフォーム

### <a name="retire-noncompliant-devices----1827291---"></a>非準拠デバイスをインベントリから削除します。 <!-- 1827291 -->
コンプライアンス違反のデバイスをインベントリからの新しいコンプライアンス アクションを追加しようとしています。 コンプライアンス違反のデバイスをインベントリから削除、そこからすべての会社のデータを削除し、デバイスが Intune によって管理されているから削除されます。 日で構成されている値に達すると、このアクションが実行されます。 最小値は 30 日間です。 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>MacOS デバイスでのカーネルの拡張機能の設定を構成します。 <!-- 2043024 -->
MacOS デバイスでデバイス構成プロファイルを作成することができます (**デバイス構成** > **プロファイル** > **プロファイルを作成する**>選択**macOS**プラットフォーム)。 新しい設定のグループで、構成し、デバイス上でカーネルの拡張機能を使用します。

適用対象: macOS 10.13.2 以降

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>セットアップ アシスタント中、一部の画面をスキップするようにプロファイルを構成する <!-- 2276470 -->
macOS 登録プロファイルを作成するとき、セットアップ アシスタントを使用中のユーザーに表示される次の画面のスキップを構成できるようになります。
- Android 移行
- ディスプレイの色調
- プライバシー
- iCloudStorage 新しいプロファイルを作成するかプロファイルを編集する場合は、選択したスキップする画面が Apple MDM サーバーと同期している必要があります。 ユーザーは、プロファイルの変更を取得するときに遅延が発生しないように、手動でのデバイスの同期を発行できます。
詳しくは、「[Device Enrollment Program または Apple School Manager を使用して macOS デバイスを自動登録する](device-enrollment-program-enroll-macos.md)」をご覧ください。

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>デバイスのユーザーは、インストールまたはインストールしようとしたすべての管理対象アプリを表示できます。 <!-- 2352913 -->
Windows 用の会社ポータルには、すべての管理対象アプリが一覧表示&ndash;必須および利用可能の両方&ndash;ユーザーのデバイスにインストールされています。 ユーザーはビューを試行し、保留中のアプリのインストールとその現在の状態になります。 組織は、必須か使用可能、アプリにすることがなさない、会社のアプリがインストールされていないことを説明するメッセージが表示されます。 ユーザーは並べ替えやインストールの状態で、アプリをフィルタ リングすることもできます。

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Apple VPP トークンのスコープのタグ <!--2371886 -->
Apple VPP トークンにスコープのタグを追加することができます。 同じスコープのタグが割り当てられたユーザーだけでは、そのタグを持つ、Apple VPP トークンへのアクセスがあります。 VPP アプリとそのトークンを使用して購入電子ブックは、そのスコープのタグを継承します。 スコープのタグの詳細については、次を参照してください。[使用 RBAC とスコープのタグ](scope-tags.md)します。

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>ときに、[適用性ルール] を使用して Windows 10 デバイス構成プロファイルを作成します。 <!-- 2549910 -->
Windows 10 デバイス構成プロファイルを作成する (**デバイス構成** > **プロファイル** > **プロファイルを作成する** > **Windows 10**プラットフォーム)。 作成することができます、**適用性ルール**のため、プロファイルは、特定のエディションまたは特定のバージョンにのみ適用されます。 たとえば、いくつかの BitLocker 設定を有効にするプロファイルを作成します。 プロファイルを追加すると、プロファイルは、Windows 10 Enterprise を実行しているデバイスにのみ適用されますので、適用性ルールを使用します。

適用先: 
- Windows 10 以降

### <a name="enable-win32-app-dependencies----2617348---"></a>Win32 アプリの依存関係を有効にします。 <!-- 2617348 -->
パブリック プレビュー - 管理者は、ことができますに Win32 アプリをインストールする前に他のアプリが依存関係としてインストールされている必要があります。 具体的には、デバイスは、Win32 アプリのインストール前に依存するアプリをインストールする必要があります。 この機能は、Intune の管理エージェントがサービスに 1,904年にアップグレードした後 1 ~ 2 の追加週間かかる場合がありますが (1.18.120.0 より大きい) 1904年バージョンにアップグレードされた後でのみ提供されます。 Intune では、次のように選択します。**クライアント アプリ** > **アプリ** > **追加**を表示する、**アプリの追加**ブレード。 選択**Windows アプリ (Win32)** として、**アプリの種類**します。 詳細については、次を参照してください。 [Intune スタンドアロンの Win32 アプリ管理](apps-win32-app-management.md)します。

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Android エンタープライズ デバイスの所有者の新しいデバイス制限の設定: ユーザーがマルチ アプリ キオスク モードを実行する専用の Android エンタープライズ デバイスで Wi-fi ネットワークに接続できるように <!--3041940 -->
管理者は、ユーザーがマルチ アプリ キオスク モードの実行専用の Android エンタープライズ デバイスで Bluetooth を構成できる新しい設定を切り替えるにはできます。 Intune コンソールでこの設定を表示するには、次のように選択します**Intune** > **デバイス構成** > **プロファイル** >  **。プロファイルを作成する**> 選択**Android エンタープライズ**プラットフォーム >**デバイスの所有者のみ、デバイスの制限**プロファイルの種類の >**設定**  > **専用デバイス**> 選択**マルチ アプリ**から、**キオスク モード**設定のドロップダウンします。 オプションと呼ばれる**Wi-fi 構成**を有効になります。 

適用対象: Android Enterprise 専用マルチ アプリ キオスク モードを実行しているデバイス。 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Android エンタープライズ デバイスの所有者の新しいデバイス制限の設定: ユーザーが Bluetooth と専用の Android エンタープライズ デバイスでペアリングを構成できるように <!--3041941 -->
管理者は、ユーザーがマルチ アプリ キオスク モードの実行専用の Android エンタープライズ デバイスで Bluetooth を構成できる新しい設定を切り替えるにはできます。 Intune コンソールでこの設定を表示するには、次のように選択します**Intune** > **デバイス構成** > **プロファイル** >  **。プロファイルを作成する**> 選択**Android エンタープライズ**プラットフォーム >**デバイスの所有者のみ、デバイスの制限**プロファイルの種類の >**設定**  > **専用デバイス**> 選択**マルチ アプリ**から、**キオスク モード**設定のドロップダウンします。 オプションと呼ばれる**Bluetooth 構成**を有効になります。 

適用対象: Android Enterprise 専用マルチ アプリ キオスク モードを実行しているデバイス。 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>セキュリティ基準のステータス (パブリック プレビュー) の監視します。 <!-- 3082047 --> 
監視する場合、*デバイス状態*、セキュリティ ベースラインのビューによってが整理状態基準カテゴリで、このような*ロック上*、 *BitLocker*、および*ブラウザー*します。 すべての利用可能な基準のカテゴリが表示されます。 各カテゴリのデバイスの数は、特定の基準のカテゴリが一致しない、構成が間違っているかは適用されませんを確認します。

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Defender ATP の (パブリック プレビュー) での Intune セキュリティ タスク <!-- 3208597 -->
パブリック プレビューとして受信して、Intune はすぐにセキュリティ タスクの追加新たに発表された Microsoft Defender 脅威と脆弱性を管理します。  この統合により、セキュリティ操作の管理者では、Windows Defender ATP (WDATP) は、Intune 管理者に新たな脅威の推奨される修復をより効率的に通信できます。 セキュリティ タスクの追加は、検出、優先順位付け、およびエンドポイントの脆弱性や構成の誤りを修復するリスク ベースのアプローチを追加します。

Intune でのセキュリティ タスクについての詳細については、に関するブログの投稿を参照してください。 [Intune セキュリティ タスクを使用して Microsoft Defender ATP の脅威と脆弱性の管理を拡張する](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857)します。 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>作成し、Intune で OEMConfig デバイス構成プロファイルを使用 <!-- 3305883 -->
Intune では、OEMConfig で Android エンタープライズ デバイスの構成をサポートします。 具体的には、デバイス構成プロファイルを作成し、OEMConfig を使用して Android エンタープライズ デバイスの設定を適用 (**デバイス構成** > **プロファイル** > **プロファイルを作成する** > **Android エンタープライズ**プラットフォーム)。

Oem のサポートは、OEM ごとに現在です。 OEMConfig アプリの一覧で、OEMConfig アプリを使用できない場合にお問い合わせください。`IntuneOEMConfig@microsoft.com`します。

適用先: 
- Android エンタープライズ

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>Android エンタープライズ デバイスの所有者の新しいデバイスの制限設定 <!-- 3574254 -->
Android エンタープライズ デバイスの場合は、許可するか、機能、パスワードの規則の設定を制限するデバイス制限プロファイルを作成することができます (**デバイス構成** > **プロファイル** > **プロファイルを作成する**> 選択**Android エンタープライズ**プラットフォーム >**デバイスの所有者のみ > デバイスの制限**プロファイルの種類の)。 

完全に管理されたデバイスは、Google Play ストアでアプリへのアクセスを完全に許可する、パスワードの設定を含む、新しい設定と使用可能な詳細になります。 

現在の設定一覧を確認するには、[Android エンタープライズ デバイスの機能を許可または制限する設定](device-restrictions-android-for-work.md)に関するページを参照してください。 

適用対象: Android エンタープライズ デバイスを完全に管理します。

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Windows 10 デバイスのコンプライアンス ポリシーでの TPM チップセットのチェック <!-- 3617671 -->
多くの Windows 10 および以降のデバイスは、トラステッド プラットフォーム モジュール (TPM) チップのセットを使ってください。 新しいコンプライアンス設定には、デバイスに TPM があるか確認します。

[Windows 10 およびそれ以降のコンプライアンス ポリシー設定](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)現在の設定を一覧表示されます。

適用先: 
- Windows 10 以降

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>Intune に登録されたにインストールされる Win32 アプリを構成する Azure AD 参加済みデバイス <!-- 3695227 -->
ことができます参加済みデバイスの割り当て、Win32 アプリが Intune にインストールするのには、Azure AD を登録します。 Intune での Win32 アプリに関する詳細については、次を参照してください。 [Win32 アプリ管理](apps-win32-app-management.md)します。

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Windows Defender Advanced Threat Protection ベースライン <!-- 3754134 -->
Windows Defender Advanced Threat Protection 設定を構成する際に新しい基準を追加しようとしています。

### <a name="device-overview-shows-primary-user---794259---"></a>デバイスの概要には、プライマリのユーザーが表示されます。 <!--794259 -->
デバイスの概要 ページは、ユーザー デバイス アフィニティ ユーザー (UDA) とも呼ばれる、プライマリのユーザーに表示されます。 デバイスのプライマリ ユーザーを表示するには、次のように選択します。 **Intune** > **デバイス** > **すべてのデバイス**> デバイスを選択します。 上部近くにプライマリ ユーザーが表示されます、**概要**ページ。

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>完全に管理された Android エンタープライズ デバイスの拡張サポート <!-- 3903241, 3903244, 3903246 -->
完全に管理された Android エンタープライズ デバイスのサポートを拡張していきます ([で 2019 年 1 月の最初に発表された](whats-new.md#week-of-january-14-2019)次を含めます。
- コンプライアンス
- 条件付きアクセス
- 新しいエンド ユーザー アプリ

Android のフル マネージド デバイスを設定するには、**[デバイスの登録]** > **[Android の登録]** > **[Corporate-owned, fully managed user devices]\(会社が所有する完全に管理されたユーザー デバイス\)** に移動します。 プレビューでは、完全に管理された Android デバイスはサポートといくつかの Intune 機能は、完全に機能できない可能性があります。 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>Android エンタープライズ仕事用プロファイル デバイスの報告、追加の Managed Google Play アプリ <!-- 4105925 -->
Managed Google Play アプリの Android エンタープライズ仕事用プロファイル デバイスに展開されている場合は、デバイスにインストールされているアプリの特定のバージョン番号を表示することがなります。 これは、必要なアプリのみに適用されます。 将来のリリースでは、使用可能なアプリの同じ機能を有効になります。

### <a name="ios-third-party-keyboards----4111843---"></a>iOS サード パーティ製キーボード <!-- 4111843 -->
Intune アプリ保護ポリシー (アプリ) のサポート、**サードパーティ製キーボード**iOS プラットフォームの変更のための設定になります。 Intune 管理コンソールでこの設定を構成することはできませんし、Intune アプリ SDK でクライアントには適用されません。

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>Windows 更新プログラムをスキャンからユーザーをブロック <!-- 3316758 -->
Windows 更新プログラムをスキャンからのユーザーをブロックするために使用できる新しい Windows 更新プログラム リング設定を追加いたします。 この設定は、ポータル内から使用可能ではありませんが、Intune Graph API を使用して構成することができます。

### <a name="windows-update-notifications----3316782---"></a>Windows の更新通知 <!-- 3316782 -->
Windows の更新の通知をユーザーに表示を構成できるように Windows 更新プログラム リングの構成にサポートを追加いたします。 この設定は、ポータル内から使用可能ではありませんが、Intune Graph API を使用して構成することができます。

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>12 の iOS デバイスのユーザーの登録をポータル サイトへの変更 <!--3448635 --> 
IOS 用ポータル サイトを更新して、アプリの登録画面と Apple iOS 12.2 でリリースされた MDM 登録の変更とを連携させる手順がいます。 更新されたワークフローには、ユーザーに求めるようになりましたが。

- (Safari) を使用して、ポータル サイト web サイトを開き、ポータル サイト アプリに戻る前に管理プロファイルをダウンロードする Safari を許可します。
- 自分のデバイスに管理プロファイルをインストール、設定アプリを開きます。
- 登録を完了してポータル サイト アプリに戻ります。

これらの変更を準備する方法の詳細については、次を参照してください。、 [Microsoft Tech Community post](https://aka.ms/CP_changes_iOS12)します。 それまでは、会社のポータルで新しい iOS の登録をサポートするために更新しました」の手順[Intune に iOS デバイスを登録](https://docs.microsoft.com/en-us/intune/ios-enroll)します。 これらのドキュメントの変更は、Apple iOS 12.2 のバージョンのリリース後、ライブになります。 

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>診断設定に簡単にアクセス <!-- 3804627 -->
新しいオプションを追加しています、**監査ログ**ブレードにすべての監査ログのワークロードを直接開くに使用できる Intune コンソールで、*診断設定*ページ。

## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。


