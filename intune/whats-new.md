---
title: "Microsoft Intune の新機能"
titlesuffix: Azure portal
description: "Intune Azure Portal の新機能を確認する"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 12/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a7edb2137051f4b0f70ebd59835ae1219f95ceba
ms.sourcegitcommit: 6d5c919286b0e285f709d9b918624b927f99f979
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune の新機能

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

週ごとにまとめた、Microsoft Intune の新機能をご覧ください。 [今後の変更](#whats-coming)、サービスに関する[重要なお知らせ](#notices)、[過去のリリース](whats-new-archive.md)に関する情報も確認できます。

> [!Note]
> ハイブリッド モバイル デバイス管理 (MDM) での新機能について詳しくは、[ハイブリッドの新機能に関するページ](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を確認してください。


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   



## <a name="week-of-december-4-2017"></a>2017 年 12 月 4 日の週

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune では Windows Information Protection (WIP) で拒否されたアプリがサポートされる<!-- 1479103 -->
拒否されたアプリを Intune で指定することができます。 アプリが拒否された場合、企業の情報へのアクセスがブロックされます。これは事実上、許可されたアプリ リストの反対です。 詳しくは、[Windows 情報保護の推奨される拒否リスト](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection)を参照してください。


## <a name="week-of-november-27-2017"></a>2017 年 11 月 27 日の週

### <a name="device-enrollment"></a>デバイスの登録
 
#### <a name="troubleshoot-enrollment-issues-----746324---"></a>登録に関する問題をトラブルシューティングする <!-- 746324 --> 

**トラブルシューティング** ワークスペースに、ユーザーの登録に関する問題が表示されるようになりました。 問題に関する詳細と推奨される修復手順は、管理者およびヘルプ デスクのオペレーターが問題をトラブルシューティングするのに役立ちます。 登録に関する特定の問題はキャプチャされず、一部のエラーには推奨される修復方法がない場合があります。 

#### <a name="group-assigned-enrollment-restrictions----747598---"></a>グループ割り当て登録制限 <!-- 747598 -->
 
Intune 管理者は[ユーザー グループに対してカスタムの登録制限として [デバイスの種類] と [デバイスの上限数] を作成できるようになりました](enrollment-restrictions-set.md)。
 
Intune Azure Portal で、制限タイプごとに最大 25 個のインスタンスを作成できます。作成したインスタンスはユーザー グループに割り当てることができます。 グループに割り当てられた制限は既定の制限をオーバーライドします。
 
制限タイプのすべてのインスタンスは、厳密に順序付けられた一覧で保守管理されます。 この順序により、競合解決の優先度の値が決まります。 複数の制限インスタンスの影響を受けるユーザーは、優先度の値が最も高いインスタンスによって制限されます。 インスタンスの優先度は、一覧内の別の位置にドラッグすることによって変更できます。 
 
Android For Work 登録メニューから登録制限メニューに Android For Work 設定が移行されたとき、この機能が使えるようになります。 この移行には数日かかる場合があります。11 月リリースのその他の部分に関してアカウントがアップグレードされた後に、登録制限のグループ割り当てが有効になる場合があります。

#### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>複数のネットワーク デバイス登録サービス (NDES) コネクタのサポート <!-- 1528104 -->

NDES を利用すれば、ドメイン資格情報なしでモバイル デバイスを実行し、Simple Certificate Enrollment Protocol (SCEP) に基づいて証明書を取得できます。 今回の更新で、複数の NDES コネクタがサポートされるようになりました。 

#### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Android デバイスとは別に Android for Work デバイスを管理する <!-- 1490731 EEready-->
 
**注**: 以下の変更は 11 月の更新をもってロールアウトが開始されます。ただし、自分のアカウントでは実行に時間がかかることがあります。 変更が自分のアカウントに適用されると、Office 365 ポータルで確認通知が届きます。 ロールアウト後、管理機能の追加のオプションを使用できるようになります。 ロールアウト中、エンド ユーザーのエクスペリエンスに対する変更はありません。
 
Intune は、Android プラットフォームに依存することなく、Android for Work デバイスの登録を管理します。 この設定は、**[デバイスの登録]**、 > **[登録制限]**、 > **[デバイスの種類の制限]** で管理されます。 (以前の場所は **[デバイス登録]**、 > **[Android for Work への登録]**、 > **[Android for Work の登録設定]** でした。)
 
既定では、Android for Work デバイス設定は Android デバイスの設定と同じになります。 ただし、Android for Work 設定を変更した後は、同じではなくなります。
 
個人の Android for Work 登録をブロックした場合、会社の Android デバイスのみを Android for Work として登録できます。
 
新しい設定を使用する場合、次の点を考慮してください。
 
##### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>以前に Android for Work 登録をオンボードしたことがない
 
新しい Android for Work プラットフォームは、既定の [デバイスの種類の制限] でブロックされます。 この機能をオンボードした後は、デバイスを Android for Work に登録できます。 そのためには、既定値を変更するか、新しい [デバイスの種類の制限] を作成して既定の [デバイスの種類の制限] に代えます。
 
##### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Android for Work 登録をオンボードした
 
以前にオンボードしている場合、状況は選んだ設定によって変わります。
 
| Setting | 既定の [デバイスの種類の制限] の Android for Work の状態 | 注 |
| --- | --- | --- |
| **すべてのデバイスを Android として管理する** | ［ブロック済み］ | すべての Android デバイスを Android for Work なしで登録する必要があります。 |
| **サポートされているデバイスを Android for Work として管理する** | 許可済み | Android for Work 対応のすべての Android デバイスを Android for Work に登録する必要があります。 |
| **これらのグループに所属するユーザーのサポートされているデバイスのみを Android for Work として管理する** | ［ブロック済み］ | 既定値をオーバーライドする別個の [デバイスの種類の制限] ポリシーが作成されました。 このポリシーによって、以前に選択したグループで Android for Work 登録が許可されます。 選択されたグループ内のユーザーには、Android for Work デバイスの登録が引き続き許可されます。 その他すべてのユーザーには、Android for Work の登録が禁止されます。 |
 
いずれの場合でも、意図した規制が維持されます。 自分の環境で Android for Work のグローバル許可またはグループ別許可を維持するための操作は必要ありません。

### <a name="app-management"></a>アプリ管理
  
#### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>インストール保留中の状態を含むように更新されたアプリ インストール レポート<!-- 1249446 -->  

**[モバイル アプリ]** ワークロードの **[アプリ]** 一覧から表示できるアプリ別の **[アプリ インストールの状態]** レポートが、ユーザーとデバイスについて **[インストール保留中]** カウントを表示するようになりました。

#### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>モバイルの脅威を検出するための iOS 11 アプリ インベントリ API <!-- 1391759 -->

Intune は個人のデバイスと会社所有のデバイスの両方からアプリ インベントリ情報を収集し、Lookout for Work など、MTD (Mobile Threat Detection/モバイル脅威検出) プロバイダーが取得できるようにします。 iOS 11 以降のデバイスを所有するユーザーからアプリ インベントリを収集できます。

**アプリ インベントリ**  
iOS 11 以降を内蔵した会社所有デバイスと個人所有デバイスの両方からのインベントリが MTD サービス プロバイダーに送信されます。 アプリ インベントリのデータ:

 - アプリ ID
 - アプリ バージョン
 - アプリ バージョン (短い形式)
 - アプリ名
 - アプリ バンドル サイズ
 - アプリの動的サイズ
 - アプリの有効性が確認されているかどうか
 - アプリが管理されているかどうか


### <a name="device-management"></a>デバイス管理

#### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>ハイブリッド MDM のユーザーとデバイスを Intune スタンドアロンに移行する<!-- 1463747 wnready -->
ハイブリッド MDM から Azure Portal 内の Intune にユーザーとそのデバイスを移動するために、新しいプロセスとツールを用意しました。これにより、次の操作を行うことができます。
- Configuration Manager コンソールから Azure Portal 内の Intune にポリシーとプロファイルをコピーする
- ユーザーのサブセットを Azure Portal 内の Intune に移動し、残りのユーザーをハイブリッド MDM で保持したままにする
- 再登録せずに、Azure Portal 内の Intune にデバイスを移行する
 
詳しくは、「[ハイブリッド MDM のユーザーとデバイスを Intune スタンドアロンに移行する](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)」を参照してください。

#### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>オンプレミスの Exchange Connector の高可用性のサポート  <!-- 676614 -->
オンプレミスの Exchange Connector に複数のクライアント アクセス サーバー (CAS) ロールを持たせることができます。 たとえば、メインの CAS に障害が発生した場合、他の CAS にフォールバックするクエリを Exchange Connector が受け取るようにできます。 この機能により、サービスが中断されないことが保証されます。

#### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>iOS デバイスをリモート再起動する (監視モードのみ) <!-- 1424595 -->

デバイス アクションを利用し、監視されている iOS 10.3 以降のデバイスの再起動をトリガーできるようになりました。 デバイス再起動アクションの利用方法については、「[Intune でデバイスをリモートで再起動する](device-restart.md)」を参照してください。

> [!Note]
> このコマンドは、監視されているデバイスと**デバイス ロック** アクセス権を要求します。 デバイスがすぐに再起動します。 パスコードでロックされている iOS デバイスが再起動後に Wi-Fi ネットワークに再び参加することはありません。再起動後、サーバーと通信できないことがあります。

#### <a name="single-sign-on-support-for-ios----1333645---"></a>iOS のシングル サインオン サポート <!-- 1333645 -->  

iOS ユーザーのためにシングル サインオンを使用できます。 シングル サインオン ペイロードのユーザー資格情報を探すようにプログラミングされている iOS アプリは、このペイロード構成更新で機能します。 UPN と Intune デバイス ID を利用し、プリンシパル名と領域を構成することもできます。 詳しくは、「[Configure Intune for iOS device single sign-on](sso-ios.md)」 (iOS 用 Intune のデバイス シングル サインオンを構成する) を参照してください。

#### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>個人デバイスの "iPhone を探す" を追加 <!--1427287-->
iOS デバイスのアクティベーション ロックがオンになっているかどうかを表示できるようになりました。 この機能は以前、クラシック ポータルの Intune にありました。


#### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>管理されている macOS デバイスを Intune でリモート ロックする <!-- 1437691 -->

紛失した macOS デバイスをロックできます。6 桁の回復用 PIN を設定できます。 ロックされているとき、別のデバイス アクションが送信されるまで、**デバイス概要**ブレードにその PIN が表示されます。

詳細については、「[管理されたデバイスを Intune でリモートからロックする](device-remote-lock.md)」を参照してください。

#### <a name="new-scep-profile-details-supported----1559808---"></a>サポートされる新しい SCEP プロファイル詳細 <!-- 1559808 -->

Windows、iOS、macOS、Android プラットフォームで SCEP プロファイルを作成するとき、管理者は追加設定を設定できるようになりました。  管理者は、IMEI、シリアル番号、あるいはサブジェクト名の形式の電子メールなど、一般名を設定できます。

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747----"></a>Intune のデバイス コンプライアンス エンジンを使用した Jamf に登録された macOS デバイスの管理 <!---1592747 --->
2018 年初めより、Jamf から Intune に macOS デバイスの状態情報が送信されるようになります。その情報はその後、Intune コンソールで定義されたポリシーへの準拠が評価されます。 条件付きアクセスでは、デバイスのコンプライアンス対応状態や、その他の条件 (場所やユーザー リスクなど) に基づいて、Azure AD に接続されたクラウド アプリケーションやオンプレミス アプリケーション (Office 365 など) にアクセスする macOS デバイスにコンプライアンスを適用します。

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

#### <a name="retain-data-during-a-factory-reset----1588489---"></a>工場出荷時の設定へのリセット中にデータを保持する <!--1588489 -->
Windows 10 バージョン 1709 以降を工場出荷時の設定にリセットすると、新しい機能が使用できるようになります。 工場出荷時の設定へのリセット中、デバイス登録やプロビジョニングされているその他のデータを保持するかどうかを管理者は指定することができます。 

工場出荷時の状態にリセットしても、次のデータが維持されます。
- デバイスに関連付けられているユーザー アカウント
- コンピューターの状態 (ドメイン参加、Azure Active Directory に参加)
- MDM 登録
- OEM でインストールされたアプリ (ストア アプリと Win32 アプリ)
- ユーザー プロファイル
- ユーザー プロファイル以外のユーザー データ
- ユーザー自動ログオン
 
次のデータは保持されません。
- ユーザー ファイル
- ユーザーがインストールしたアプリ (ストア アプリと Win32 アプリ)
- 初期値ではないデバイス設定

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング
#### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Windows 10 更新プログラム リング割り当てが表示される <!-- 1621837 -->
**トラブルシューティング**時、表示しているユーザーに関して、Windows 10 更新プログラム リング割り当てを表示することができます。  

#### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings------1455974-----"></a>Windows Defender Advanced Threat Protection の報告頻度設定 <!--- 1455974  --->
Windows Defender Advanced Threat Protection (WDATP) サービスを利用するとき、管理者は管理対象デバイスの報告頻度を管理できます。 新しい **[テレメトリの報告頻度を早める]** オプションを利用すると、WDATP はデータを収集し、さらに頻繁にリスクを評価します。 報告の既定値で速度とパフォーマンスが最適化されます。 報告の頻度を増やすことは、リスクの高いデバイスの場合に有益となります。 この設定は **[デバイス構成]** の **[Windows Defender ATP]** プロファイルにあります。

#### <a name="audit-updates----1412961---"></a>監査更新 <!-- 1412961 -->  
Intune の監査機能により、Intune に関連する変更操作が記録されます。  あらゆる作成操作、更新操作、削除操作、リモート タスク操作が記録され、1 年間保存されます。  Azure Portal では、ワークロード別の監査データを過去 30 日分表示できます。データの絞り込みも可能です。  対応する Graph API により、前年に格納された監査データを取得できます。 

監査は **[モニター]** グループの下にあります。 ワークロード別に **[監査ログ]** メニュー項目があります。 




## <a name="week-of-november-20-2017"></a>2017 年 11 月 20 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="google-play-protect-support-on-android----908720---"></a>Android の Google Play Protect サポート <!-- 908720 -->

Android Oreo のリリースに伴い、セキュリティで保護されたアプリおよび Android イメージをユーザーや組織が実行できる、Google Play Protect という一連のセキュリティ機能が Google より提供されました。 Intune では、SafetyNet リモート構成証明をはじめとした Google Play Protect の各機能をサポートします。 管理者は、Google Play Protect が構成され正常な状態であることが求められるコンプライアンス ポリシー要件を設定できます。
**[SafetyNet デバイスの構成証明]** 設定では、デバイスが正常な状態であり危険にさらされていないことを確認するために、デバイスを Google サービスに接続する必要があります。 管理者は、インストール済みのアプリが Google Play 開発者サービスによって検証されることを必須にする、Android for Work の構成プロファイル設定を設定することもできます。 条件付きアクセスでは、デバイスが Google Play Protect の要件に準拠していない場合に、ユーザーが企業リソースにアクセスできなくなる可能性があります。

- 「[デバイスのコンプライアンス ポリシーを作成して Google Play Protect を有効にする方法](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect)」を参照してください。

#### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>管理対象アプリから許可されるテキスト プロトコル <!-- 1414050  -->

Intune App SDK によって管理されているアプリは、SMS メッセージを送信できます。

## <a name="week-of-november-13-2017"></a>2017 年 11 月 13 日の週

### <a name="intune-apps"></a>Intune アプリ
#### <a name="company-portal-app-for-macos-is-available---1541700--"></a>macOS 用ポータル サイト アプリ提供開始 <!--1541700-->
macOS での Intune ポータル サイトのエクスペリエンスが更新されました。ユーザーが登録済みのすべてのデバイスで必要となるすべての情報とコンプライアンス通知が明確に表示されるように最適化されました。 また、いったん Intune ポータル サイトをデバイスに展開すると、macOS 用 Microsoft 自動更新から更新プログラムが提供されるようになります。 macOS デバイスから Intune ポータル サイトにログインすることで、新しい macOS 用 Intune ポータル サイトをダウンロードできます。

#### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner が承認済みアプリのモバイル アプリ管理 (MAM) リストの一部に <!-- 1248473 -->
iOS および Android 用の Microsoft Planner アプリが、承認済みアプリのモバイル アプリ管理 (MAM) の一部となりました。 このアプリは、Azure Portal の Intune App Protection ブレードからすべてのテナントに対して構成できます。
- 詳細については、[承認済みアプリの MAM リスト](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)に関するページをご覧ください。

#### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>iOS デバイスでのアプリごとの VPN 要件の更新頻度 <!-- 1547061 -->  
管理者が iOS デバイス上のアプリでアプリごとの VPN 要件を削除できるようになりました。影響を受けるデバイスでは、次回の Intune チェックイン後、通常 15 分以内に反映されます。  

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング
#### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Exchange Connector 用 System Center Operations Manager 管理パックのサポート <!-- 885457 -->
Exchange Connector 用 System Center Operations Manager (SCOM) 管理パックを Exchange Connector のログ解析に利用できるようになります。 これにより、問題のトラブルシューティングが必要な場合に、別の方法でサービスを監視できるようになります。

## <a name="week-of-november-6-2017"></a>2017 年 11 月 6 日の週

### <a name="device-enrollment"></a>デバイスの登録
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>Windows 10 デバイスの共同管理 <!-- 1243445 -->
共同管理は、従来の管理から最新の管理への橋渡しとなるソリューションであり、段階的なアプローチを使って移行する方向を提示します。 基本的に、共同管理は、Windows 10 デバイスを Configuration Manager と Microsoft Intune で同時に管理すると共に、Active Directory (AD) と Azure Active Directory (Azure AD) に同時に参加させることができるソリューションです。  この構成は、一度にすべてを移行できない組織が適切なペースで時間をかけて最新化するパスを提供します。  

#### <a name="new-enrollment-status-page-for-windows-10-enrollments---1063201--"></a>Windows 10 の登録の新しい登録状態ページ<!--1063201-->    
ユーザーが Windows 10 デバイスを登録したときに表示される案内メッセージを構成できるようになりました。 **登録ステータス画面**を使って、Windows 10 デバイスを登録するときにエンド ユーザーに表示されるカスタム メッセージとハイパーリンクを構成します。  **登録ステータス画面**では、デバイスに適用されているポリシー設定の進行状況もエンド ユーザーに対して表示されます。  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>OS のバージョンによる Windows 登録の制限 <!-- 245498 -->
Intune 管理者は、デバイス登録に関して、Windows 10 の最小バージョンと最大バージョンを指定できるようになりました。 これらの制限は **[プラットフォーム構成]** ブレードで設定できます。

Intune では、Windows 8.1 の PC とスマートフォンを引き続き登録できます。 ただし、下限と上限を設定できるのは Windows 10 のバージョンだけです。 8.1 デバイスの登録を許可するには、下限を空のままにします。

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Windows AutoPilot の未割り当てデバイスのアラート <!-- 1631236 -->
**[Microsoft Intune]**、**[デバイス登録]**、**[概要]** ページには、Windows AutoPilot の未割り当てデバイスの新しいアラートがあります。 このアラートでは、AutoPilot プログラムからのデバイスで、AutoPilot Deployment プロファイルが割り当てられていないデバイスの数が示されます。 アラート内の情報を利用してプロファイルを作成し、未割り当てデバイスに割り当てます。 アラートをクリックすると、Windows AutoPilot の完全一覧とそれらに関する詳細が表示されます。 詳細については、「[Windows AutoPilot Deployment プログラムを使用して Windows デバイスを登録する](https://docs.microsoft.com/intune/enrollment-autopilot)」を参照してください。

### <a name="device-management"></a>デバイス管理

#### <a name="refresh-button-for-devices-list-------1333581---"></a>デバイス一覧の [更新] ボタン <!-- 1333581 -->
デバイス一覧は自動的に更新されないため、新しい [更新] ボタンを利用し、一覧に表示されるデバイスを更新できます。

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Symantec クラウド証明機関 (CA) のサポート <!-- 1333638 -->    
Intune は Symantec クラウド CA をサポートするようになり、Intune Certificate Connector は Symantec クラウド CA から Intune で管理対象デバイスに PKCS 証明書を発行できます。 Microsoft 証明機関 (CA) で Intune Certificate Connector を既に使っている場合は、Intune Certificate Connector の既存の設定を利用して、Symantec CA のサポートを追加できます。

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>デバイス インベントリに追加された新しい項目 <!--1404455 -->
このリリースでは、[登録デバイスによって取得されるインベントリ](device-inventory.md)に次の新しい項目を追加しました。

- Wi-Fi MAC アドレス
- 記憶域の合計容量
- 合計空き容量
- MEID
- 通信事業者


### <a name="app-management"></a>アプリ管理
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>デバイスでの最低限の Android セキュリティ パッチによりアプリへのアクセスを設定する <!-- 1278463 -->   
管理者は、管理されたアカウントの管理対象アプリケーションにアクセスするために、デバイスにインストールする必要がある最低限の Android セキュリティ パッチを定義することができます。

> [!Note]  
> この機能は、Google によって Android 6.0 以降のデバイスについてリリースされたセキュリティ パッチだけを制限します。

#### <a name="app-conditional-launch-support----1193313---"></a>アプリの条件付き起動のサポート <!-- 1193313 -->
IT 管理者は、アプリケーションの起動時にモバイル アプリ管理 (MAM) によって数値の PIN ではなくパスコードを強制する要件を、Azure 管理ポータルで設定できるようになりました。 構成した場合、ユーザーは、MAM 対応のアプリケーションにアクセスする前に、要求された時点で、パスコードを設定および使用する必要があります。 パスコードは、少なくとも 1 つの特殊文字または大文字/小文字アルファベットを含む数値 PIN と定義されます。 Intune の今回のリリースでは、この機能を利用できるのは **iOS のみ**です。 Intune は、数値 PIN に同様の方法でパスコードをサポートし、最小の長さを設定して、文字やシーケンスの繰り返しを許可します。 この機能では、対象のアプリケーションにパスコード設定を適用するのではなく、Intune アプリ SDK とこの機能のコードとを統合するために、アプリケーション (WXP、Outlook、Managed Browser、Yammer など) の参加が必要となります。

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>デバイス インストール状態レポートでの基幹業務アプリのバージョン番号 <!-- 1233999 -->
このリリースでは、デバイス インストール状態レポートに、iOS および Android 用基幹業務アプリのバージョン番号が表示されます。 この情報を使って、アプリのトラブルシューティングや、古いバージョンのアプリを実行しているデバイスの検索を行うことができます。


### <a name="device-configuration"></a>デバイス構成
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>管理者は、デバイス構成プロファイルを使ってデバイスでのファイアウォールの設定を構成できるようになる <!-- 951708 -->   
管理者は、デバイスのファイアウォールを有効にすることができ、ドメイン ネットワーク、プライベート ネットワーク、パブリック ネットワークのさまざまなプロトコルを構成することもできます。  これらのファイアウォールの設定は、"Endpoint Protection" プロファイルで確認できます。

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard は、組織での定義に従って、信頼されていない Web サイトからデバイスを保護する <!-- 958257 -->   
管理者は、Windows Information Protection ワークフローまたはデバイス構成の新しい "ネットワーク境界" プロファイルを使って、"信頼できる" サイトまたは "企業" サイトを定義できます。 64 ビット Windows 10 デバイスの信頼されたネットワーク境界内にないすべてのサイトは、Microsoft Edge で表示された場合、代わりに Hyper-V 仮想コンピューター内のブラウザーで開かれます。

Application Guard は、"Endpoint Protection" プロファイル内のデバイス構成プロファイルで確認できます。 デバイス構成プロファイルでは、管理者は、仮想化されたブラウザーとホスト マシンの相互作用、信頼されないサイトと信頼されるサイト、および仮想化されたブラウザーで生成されたファイルの保存を構成することができます。 デバイスで Application Guard を使うには、最初にネットワーク境界を構成する必要があります。 デバイスごとにネットワーク境界を 1 つだけ定義することが重要です。  

#### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows 10 Enterprise の Windows Defender Application Control は、承認されたアプリのみを信頼するモードを提供する <!-- 1031096 -->    
毎日何千もの悪意あるファイルが作成される状況においては、ウイルス対策の署名ベースの検出を使ってマルウェアに対抗するのでは、新しい攻撃を十分に防ぐことができない可能性があります。 Windows 10 Enterprise の Windows Defender Application Control を使うと、ウイルス対策ソフトウェアや他のセキュリティ ソリューションによってブロックされない限りアプリを信頼するモードから、企業によって承認されたアプリのみをオペレーティング システムが信頼するモードにデバイスの構成を変更できます。 Windows Defender Application Control でアプリに信頼を割り当てます。

Intune を使って、アプリケーション制御ポリシーを "監査のみ" モードまたは強制モードに構成できます。 "監査のみ" モードで実行している場合、アプリはブロックされません。 "監査のみ" モードでは、すべてのイベントがローカル クライアント ログに記録されます。 また、Windows コンポーネントと Windows ストア アプリの実行のみを許可するか、またはインテリジェント セキュリティ グラフで定義されている評判の良いアプリの実行も許可するかを構成することもできます。

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows 10 用の新しい侵入防止機能セットである Window Defender Exploit Guard <!-- 1063615 -->   
Window Defender Exploit Guard は、アプリケーションが悪用される可能性を減らすカスタム規則を含み、マクロとスクリプトの脅威を防止し、評判が低い IP アドレスへのネットワーク接続を自動的にブロックして、ランサムウェアや不明の脅威からデータを保護できます。 Windows Defender Exploit Guard は、次のコンポーネントで構成されます。

- **攻撃の回避 (ASR)** は、マクロ、スクリプト、メールの脅威を防ぐことができる規則を提供します。
- **フォルダー アクセスの制御**は、保護されているフォルダーのコンテンツへのアクセスを自動的にブロックします。
- **ネットワーク フィルター**は、アプリから評判の悪い IP/ドメインへの発信接続をブロックします。
- **Exploit Protection** は、アプリケーションを悪用から保護するために使うことができるメモリ、制御フロー、およびポリシーの制限を提供します。


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Windows 10 デバイスの Intune で PowerShell スクリプトを管理する <!-- 790537 -->

Intune 管理拡張機能を使用すると、Windows 10 デバイスで実行されている Intune で PowerShell スクリプトをアップロードできます。 この拡張機能は Windows 10 モバイル デバイス管理 (MDM) 機能を補完するもので、最新の管理に簡単に移行できます。 詳細については、「[Windows 10 デバイスの Intune で PowerShell スクリプトを管理する](intune-management-extension.md)」を参照してください。

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Windows 10 の新しいデバイスの制限設定 <!-- 1308850 -->
-    メッセージング (モバイルのみ) - テストまたは MMS のメッセージを無効化します
-    パスワード - FIPS と、認証用の Windows Hello デバイス セカンダリ デバイスの使用を有効にする設定 
-    ディスプレイ - レガシ アプリの GDI スケーリングをオンまたはオフにする設定

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Windows 10 キオスク モード デバイスの制限 <!-- 1308872 -->   
Windows 10 デバイスのユーザーをキオスク モードに制限することができます。これは、一連の定義済みアプリにユーザーを制限します。  そのためには、Windows 10 デバイス制限プロファイルを作成し、キオスク設定を設定します。

キオスク モードは、**シングル アプリ** (1 つのアプリだけの実行をユーザーに許可) または**マルチ アプリ** (アプリのセットへのアクセスを許可) の 2 つのモードをサポートします。  ユーザー アカウントとデバイス名を定義します。これらにより、サポートされるアプリが決まります。  ユーザーはログイン時に定義済みのアプリに制限されます。  詳細については、「[AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)」を参照してください。 

キオスク モードには以下が必要です。

- Intune が MDM 機関である必要があります。
- アプリは、ターゲット デバイスに既にインストールされている必要があります。
- デバイスは、[適切にプロビジョニングされている](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)必要があります。

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>ネットワーク境界を作成するための新しいデバイス構成プロファイル <!-- 1311967 -->   
**ネットワーク境界**と呼ばれるデバイス構成プロファイルを作成しました。他のデバイス構成プロファイルと同じ場所にあります。 このプロファイルを使用して、会社のもので信頼できると見なす必要があるオンライン リソースを定義します。 Windows Defender Application Guard や Windows Information Protection などの機能をデバイスで使用するには、"*事前*" にデバイスに対してネットワーク境界を定義する必要があります。 デバイスごとにネットワーク境界を 1 つだけ定義することが重要です。

信頼できるエンタープライズ クラウド リソース、IP アドレス範囲、内部プロキシ サーバーを定義できます。 定義したネットワーク境界は、Windows Defender Application Guard や Windows Information Protection 保護などの他の機能で使うことができます。

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Windows Defender ウイルス対策用の 2 つの追加設定<!-- 1338409 -->  
**ファイル ブロック レベル**

| | |
|---|---|
| 未構成 | **未構成**は、Windows Defender ウイルス対策の既定のブロック レベルを使用し、正当なファイルが検出されるリスクを高めることなく強力な検出を提供します。 |
| 高 | **高**は、強力なレベルの検出を適用します。
| 高 +  | **高 +** は、高いレベルに加えて、クライアントのパフォーマンスに影響を与える可能性がある保護手段を提供します。
| ゼロ トレランス  | **ゼロ トレランス**は、不明な実行可能ファイルをすべてブロックします。 |

まれですが、**高**に設定すると、一部の正当なファイルが検出される可能性があります。
ファイル ブロック レベルは既定の**未構成**に設定することをお勧めします。

**クラウドによるファイル スキャンの時間延長**  

| | |
|--|--|
| 秒数 (0 - 50) | Windows Defender ウイルス対策がクラウドからの結果の待機中にファイルをブロックする最大時間を指定します。 既定値は 10 秒です。ここで指定した延長時間 (最大 50 秒) は、この 10 秒間に追加されます。 ほとんどの場合、スキャンは最大値よりはるかに短い時間で済みます。 時間を延長すると、クラウドは疑わしいファイルを徹底的に調査できます。 この設定を有効にし、少なくとも 20 秒の追加を指定することをお勧めします。 |

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Windows 10 デバイスに追加された Citrix VPN <!-- 1512457 -->  
Windows 10 デバイス用に Citrix VPN を構成できます。 Windows 10 以降用に VPN を構成するときに、**[基本 VPN]** ブレードの *[接続の種類を選びます]* の一覧で、Citrix VPN を選ぶことができます。

> [!Note]
> Citrix の構成は、iOS および Android 用に存在しました。

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Wi-Fi 接続は iOS で事前共有キーに対応 <!-- 1550823 -->
ユーザーは iOS デバイスで WPA/WPA2 Personal 接続に事前共有キー (PSK) を使用するように Wi-Fi プロファイルを構成できます。 これらのプロファイルは、デバイスが Intune に登録されたとき、ユーザーのデバイスにプッシュされます。

プロファイルがデバイスにプッシュされたとき、次の手順はプロファイル構成によって決まります。  自動的に接続するように設定されている場合、ネットワークが次に必要になったとき、自動的に接続されます。  プロファイルが手動接続になっている場合、ユーザーは接続を手動で開始する必要があります。  

### <a name="intune-apps"></a>Intune アプリ

#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>iOS の管理対象アプリ ログにアクセス <!-- 1469920 -->
Managed Browser をインストールしているエンド ユーザーは、Microsoft が公開したあらゆるアプリの管理状態を表示し、管理対象 iOS アプリの問題を解消するためにログを送信できるようになりました。

iOS デバイスの Managed Browser でトラブルシューティング モードを有効にする方法については、「[iOS で Managed Browser を使用し、管理対象アプリ ログにアクセスする方法](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios)」を参照してください。

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>iOS 用ポータル サイト バージョン 2.9.0 でのデバイスのセットアップ ワークフローの機能強化<!---1417174--->

iOS 用ポータル サイト アプリでのデバイス セットアップ ワークフローを改善しました。 言葉がよりわかりやすくなり、可能な範囲で画面をまとめました。 また、セットアップのテキスト全体でお客様の会社名を使用することで、表現がより会社に合ったものになっています。 この更新されたワークフローについては、 [アプリ UI ページの新機能](whats-new-app-ui.md)に関するページをご覧ください。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>ユーザー エンティティにデータ ウェアハウス データ モデルの最新のユーザー データが含まれている<!-- 1544273 -->
Intune データ ウェアハウス データ モデルの最初のバージョンでは、最近の Intune 履歴データのみが含まれていました。 レポートの作成者は、ユーザーの最新の状態をキャプチャできませんでした。 今回の更新プログラムでは、最新のユーザー データを使用して**ユーザー エンティティ**が設定されます。


## <a name="week-of-october-30-2017"></a>2017 年 10 月 30 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>iOS と Android の基幹業務アプリのバージョン番号が表示可能 <!-- 1380712 -->

Intune では、iOS と Android の基幹業務アプリのバージョン番号が表示されるようになりました。 Azure Portal のアプリ一覧とアプリ概要ブレードで番号が表示されます。 エンド ユーザーは、ポータル サイト アプリと Web ポータルでアプリ番号を確認できます。

__バージョン番号 (フル)__ このフル バージョン番号はアプリのリリースを特定します。 この番号は _バージョン_(_ビルド_) の形式で表示されます。 たとえば、2.2(2.2.17560800) のようになります。

バージョン番号 (フル) を構成する 2 つの要素:

 - **バージョン**  
   バージョン番号は、人間が判読できるアプリのリリース番号です。 エンド ユーザーがアプリの各種リリースを区別するために使用されます。

 - **ビルド番号**  
    ビルド番号は、アプリの検出に利用される内部番号です。また、プログラミングでアプリを管理するために利用されます。 ビルド番号は、コードの変更を参照するアプリのイテレーションを参照します。

バージョン番号と基幹業務アプリの開発については、「[Microsoft Intune アプリ SDK の概要](app-sdk-get-started.md#line-of-business-app-version-numbers)」を参照してください。

#### <a name="device-and-app-management-integration----677972---"></a>デバイスとアプリの管理の統合 <!-- 677972 -->   
Intune のモバイル デバイス管理 (MDM) とモバイル アプリケーション管理 (MAM) はどちらも Azure Portal からアクセスできるようになり、Intune はアプリケーション管理とデバイス管理に関する IT 管理者エクスペリエンスの統合を開始しました。 これらの変更は、デバイスとアプリの管理エクスペリエンスの簡素化を目的としたものです。

MDM と MAM の変更の詳細については、[Intune サポート チーム ブログ](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/)での案内をご覧ください。

#### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Apple デバイスの新しい登録アラート <!-- 1471790 -->
登録の概要ページには、IT 管理者のために、Apple デバイスの管理に便利なアラートが表示されるようになります。 Apple MDM プッシュ証明書の有効期間が近づいたり、既に過ぎているとき、Device Enrollment Program の有効期間が近づいたり、既に過ぎているとき、Device Enrollment Program に未割り当てのデバイスがあるとき、アラートが概要ページに表示されます。

#### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>デバイス登録のないアプリ構成のトークン置換をサポート <!-- 1080364 -->

登録されていないデバイス上のアプリに関して、アプリ構成の動的な値にトークンを利用できます。 詳細については、「[デバイス登録なしで管理対象アプリ用アプリ構成ポリシーを追加する](app-configuration-policies-managed-app.md)」を参照してください。

### <a name="intune-apps"></a>Intune アプリ

#### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Windows 10 用ポータル サイト アプリの更新内容 <!--1299474-->
Windows 10 用ポータル サイト アプリの [設定] ページが更新され、すべての設定で、設定と目的のユーザー アクションの一貫性が高まっています。 また、その他の Windows アプリのレイアウトと一致させる更新も行われています。 更新前/後のイメージは、[アプリ UI ページの新機能](whats-new-app-ui.md)に関するページでご覧いただけます。

#### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>Windows 10 デバイスで確認できるデバイス情報のエンドユーザーへの通知 <!--1337920-->
Windows 10 用ポータル サイト アプリの [デバイスの詳細] 画面に **[所有権の種類]** が追加されました。 これにより、ユーザーは、Intune エンドユーザー ドキュメントのこのページから直接プライバシーの詳細を確認できるようになります。この情報は、**[バージョン情報]** 画面でも確認できます。

#### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Android 用ポータル サイト アプリに関するフィードバック プロンプト <!--1165249-->
Android 用ポータル サイト アプリでは、エンド ユーザー フィードバックを即時要求します。 このフィードバックは Microsoft に直接送信され、エンドユーザーは一般の Google Play ストアでアプリをレビューできます。 フィードバックは必須ではなく、ユーザーは簡単にこれを拒否して、アプリの使用を続行できます。

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

#### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Android 向けポータル サイト アプリに関してユーザーの自己解決をサポートする <!---1573324, 1573150, 1558616, 1564878--->

Android 向けポータル サイト アプリでは、エンド ユーザーへの指示が追加されています。それは新しいユース ケースの理解や、可能な場合にはその自己解決にも役立ちます。
- 追加が許されているデバイスの最大数に到達した場合、デバイスを削除するように、エンド ユーザーは (Azure Active Directory ポータル)[https://account.activedirectory.windowsazure.com/r/#/profile] に誘導されます。
- [Samsung KNOX デバイスのアクティベーション エラーを解消する](https://go.microsoft.com/fwlink/?linkid=859718)か、[節電モードをオフにする](/intune-user-help/power-saving-mode-android)ための手順がエンド ユーザーに表示されます。 いずれの解決策でも問題が解消されない場合、[Microsoft にログを送信する](/intune-user-help/send-logs-to-microsoft-ios)方法を説明します。

#### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Android デバイスで利用できる新しい '解決' アクション <!---1583480--->

Android のポータル サイト アプリの _[デバイス設定の更新]_ ページに '解決' アクションが導入されます。 このオプションを選択すると、デバイスの非準拠の原因になっている設定にエンド ユーザーが直接誘導されます。 Android 向けのポータル サイト アプリでは現在のところ、[デバイス パスコード](/intune-user-help/set-your-pin-or-password-android)、[USB デバッグ](/intune-user-help/you-need-to-turn-off-usb-debugging-android)、[不明なソース](/intune-user-help/you-need-to-turn-off-unknown-sources-android)設定に対してこのアクションがサポートされています。

#### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Android 用ポータル サイトのデバイスのセットアップ進行状況インジケーター <!---1565657--->
Android 用ポータル サイト アプリでは、ユーザーがデバイスを登録しているときに、デバイスのセットアップ進行状況インジケーターが示されます。 このインジケーターで新しいステータスが表示されます。初めに表示されるものから挙げると、[Setting up your device...] \(デバイスをセットアップしています...\)、[Registering your device...] \(デバイスを登録しています...\)、[Finishing registering your device...] \(デバイス登録を終了しています...\)、[Finishing setting up your device...] \(デバイス セットアップを終了しています...\) です。

## <a name="week-of-october-23-2017"></a>2017 年 10 月 23 日の週

### <a name="intune-apps"></a>Intune アプリ
#### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>iOS 用ポータル サイトでの証明書ベースの認証のサポート <!--1029830-->
iOS 用ポータル サイト アプリでの証明書ベースの認証 (CBA) のサポートが追加されました。 CBA を使用するユーザーは、ユーザー名を入力した後、[Sign in with a certificate]\(証明書でサインインする\) リンクをタップします。 CBA は、Android および Windows 用のポータル サイト アプリで既にサポートされています。 詳細については、「[ポータル サイト アプリにサインインするには](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)」を参照してください。

#### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>登録の有無にかかわらず利用可能なアプリについて、登録を求められずにインストールできるようになりました。 <!-- 1334712 -->

Android ポータル サイト アプリでの登録の有無にかかわらず利用可能な業務用アプリについて、登録を求められずにインストールできます。

## <a name="week-of-october-16-2017"></a>2017 年 10 月 16 日の週
### <a name="device-enrollment"></a>デバイスの登録
#### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Microsoft Intune で Windows AutoPilot Deployment プログラムをサポート<!-- 747617  -->
Microsoft Intune と Windows AutoPilot Deployment プログラムを使用して、IT が関与しなくても、ユーザーが自分の会社のデバイスをプロビジョニングできるようになりました。 OOBE (Out-of-Box Experience) をカスタマイズしたり、ユーザーのデバイスの Azure AD への参加および Intune への登録について、ユーザーをガイドすることができます。 Microsoft Intune と Windows AutoPilot を合わせて使用すると、オペレーティング システム イメージを展開、保持、管理する必要がなくなります。 詳細については、「[Windows AutoPilot Deployment プログラムを使用して Windows デバイスを登録する](https://docs.microsoft.com/intune/enrollment-autopilot)」を参照してください。

#### <a name="quick-start-for-device-enrollment-----1425655---"></a>デバイス登録のクイック スタート<!-- 1425655 --> 
**デバイスの登録**でクイック スタートが利用できるようになり、プラットフォームの管理と登録プロセスの構成のための参考資料の表が提供されます。 各項目の簡単な説明と詳細な手順があるドキュメントへのリンクにより、簡単に使用開始するために役立つドキュメントを提供します。

#### <a name="device-categorization----1427491---"></a>デバイスのカテゴリ化<!-- 1427491 -->
**[デバイス] > [概要]** ブレードの登録済みデバイス プラットフォームのグラフは、プラットフォーム (Android、iOS、macOS、Windows、Windows Mobile など) ごとにデバイスをまとめています。  他のオペレーティング システムを実行しているデバイスは "その他" にグループ化されています。  これには、Blackberry、NOKIA、およびその他のメーカー製のデバイスが含まれます。  

テナント内で影響を受けるデバイスを把握するには、**[管理] > [すべてのデバイス]** を選択してから、**[フィルター]** を使用して**[OS]** フィールドを制限します。

### <a name="device-management"></a>デバイス管理
#### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium - 新しい Mobile Threat Defense パートナー   <!-- 954681 -->  
Microsoft Intune に統合された Mobile Threat Defense ソリューションである Zimperium によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

##### <a name="how-integration-with-intune-works"></a>Intune との統合のしくみ
リスクは、Zimperium を実行するデバイスから収集される製品利用統計情報に基づいて評価されます。 Intune デバイス コンプライアンス ポリシーで有効にした Zimperium リスク評価に基づき、EMS 条件付きアクセスのポリシーを構成できます。Intune デバイス コンプライアンス ポリシーは、検出された脅威に基づき、非準拠デバイスから企業リソースへのアクセスを許可したり、拒否したりするために利用できます。

#### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Windows 10 デバイス制限プロファイルの新しい設定 <!--- 978575, 1308849, -->  
Windows Defender SmartScreen カテゴリの Windows 10 デバイス制限プロファイルに新しい設定が追加されます。

Windows 10 デバイス制限のプロファイルの詳細については、「[Windows 10 以降のデバイスの制限設定]( device-restrictions-windows-10.md)」を参照してください。

#### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Windows と Windows Mobile デバイスのリモート サポート <!-- 1070473 -->  
[TeamViewer](https://www.teamviewer.com) ソフトウェア (別売り) を使用して、Windows と Windows Mobile デバイスを実行するユーザーに Intune でリモート アシスタンスを提供できるようになりました。

#### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Windows Defender でデバイスをスキャンする <!-- 1280988  1280990   -->
管理された Windows 10 デバイス上で Windows Defender ウイルス対策を使って **クイック スキャン**、**フル スキャン**、**署名更新**を実行できるようになりました。 デバイスの概要ブレードから、デバイス上で実行するアクションを選びます。 コマンドがデバイスに送信される前に、アクションの確認を求められます。 

**クイック スキャン**: クイック スキャンでは、レジストリ キーや既知の Windows スタートアップ フォルダーなど、マルウェアが起動するように登録されている場所がスキャンされます。 クイック スキャンには、平均 5 分かかります。 クイック スキャンは、ファイルの開閉時やユーザーがフォルダーに移動したときにファイルをスキャンする **[Always-on real-time protection]\(リアルタイム保護を常に有効にする\)** 設定と組み合わせると、システムやカーネル内に存在する可能性があるマルウェアから保護するのに役立ちます。 完了すると、ユーザーのデバイスにスキャン結果が表示されます。 

**フル スキャン**: フル スキャンは、マルウェアの脅威が発生したデバイスで、徹底的なクリーンアップが必要な非アクティブなコンポーネントがあるかどうかを識別するために使用できます。また、オンデマンド スキャンを実行する場合に便利です。 フル スキャンは、実行に 1 時間かかる場合があります。 完了すると、ユーザーのデバイスにスキャン結果が表示されます。 

**署名更新**: 署名更新コマンドを使用すると、Windows Defender ウイルス対策のマルウェア定義と署名が更新されます。 マルウェア検出における Windows Defender ウイルス対策ソフトウェアの効果を確保するために役立ちます。 この機能は Windows 10 デバイス専用であり、デバイスのインターネット接続を一時中断します。 

#### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>Intune Azure Portal の Intune 証明機関のページからの [有効]/[無効] ボタンの削除<!-- 1400455 -->
 Intune の証明書コネクタの設定で、余分な手順を排除しています。 現在は、証明書コネクタをダウンロードしてから、Intune コンソールでそれを有効にしています。 ただし、Intune コンソールでコネクタを無効にすると、コネクタは証明書の発行に進みます。

##### <a name="how-does-this-affect-me"></a>ユーザーへの影響
10 月以降、Azure Portal の証明機関のページに、[有効]/[無効] ボタンが表示されなくなります。 コネクタ機能は変わりません。 証明書は、Intune に登録したデバイスに引き続き展開されます。 引き続き、証明書コネクタをダウンロードしてインストールすることができます。 証明書の発行を停止するには、証明書コネクタを無効にするのではなく、今すぐアンインストールします。

##### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
現在、無効になっている証明書コネクタがある場合は、それをアンインストールする必要があります。

### <a name="device-configuration"></a>デバイス構成
#### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Windows 10 Team デバイス制限プロファイルの新しい設定 <!--- 1308838 -->
このリリースでは、Surface Hub デバイスの制御に役立つように、Windows 10 Team デバイス制限プロファイルに多数の新しい設定が追加されています。

このプロファイルについて詳しくは、[Windows 10 Team デバイスの制限設定](device-restrictions-windows-10-teams.md)に関するページをご覧ください。

#### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Android デバイス ユーザーによるデバイスの日付と時刻の変更を防止する <!-- 1333292 -->
[Android カスタム デバイス ポリシー](custom-settings-android.md)を使用して、Android デバイス ユーザーがデバイスの日付や時刻を変更できないように設定できます。

この設定を行うには、./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange の設定 URI を使用して Android カスタム ポリシーを構成し、これを **TRUE** に設定して該当のグループに割り当てます。

#### <a name="bitlocker-device-configuration----1397398---"></a>BitLocker デバイス構成 <!-- 1397398 -->
**[Windows 暗号化] > [Base Settings]\(基本設定\)** に、新たに **[他のディスクの暗号化に対する警告]** 設定が追加されました。この設定では、ユーザーのデバイス上で使われている可能性がある、他のディスクの暗号化についての[警告プロンプト](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption)を無効にできます。  警告プロンプトの利用には、デバイス上で BitLocker をセットアップする前にエンドユーザーの同意が必要であり、エンドユーザーによって承諾されるまで BitLocker のセットアップはブロックされます。  この新しい設定では、エンドユーザーに対する警告が無効になります。


### <a name="app-management"></a>アプリ管理
#### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>Intune テナントと同期されるようになった Volume Purchase Program for Business アプリ<!-- 800882 -->  
サードパーティの開発者は、iTunes Connect で指定されている承認された Volume Purchase Program (VPP) for Business メンバーにプライベートでアプリを配布できます。 VPP for Business のメンバーは、Volume Purchase Program App Store にサインインし、アプリを購入できます。

このリリースでは、エンド ユーザーが購入した VPP for Business アプリがそのユーザーの Intune テナントに同期されます。

#### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Apple の国別ストアを選択して VPP アプリを同期する <!-- 1332311 -->  
Volume Purchase Program (VPP) トークンをアップロードする際に、VPP 国別ストアを構成できます。 指定された VPP 国別ストアにある全ロケールに対応した VPP アプリが、Intune によって同期されます。

> [!NOTE]  
> 現在、Intune で同期されるのは、Intune テナントが作成された Intune ロケールに一致する VPP 国別ストアの VPP アプリのみです。


### <a name="intune-apps"></a>Intune アプリ
#### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Android for Work で仕事用プロファイルと個人プロファイルの間でのコピーおよび貼り付けを防ぐ <!-- 1098994 -->
このリリースでは、仕事用アプリと個人用アプリとの間でコピーおよび貼り付けができないように、Android for Work の仕事用プロファイルを構成できます。 この新しい設定は、**[仕事用プロファイルの設定]** の **[Android for Work]** プラットフォームの **[デバイスの制限]** プロファイルにあります。

#### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>特定地域の Apple App Store のみを対象とした iOS アプリを作成する <!-- 1281692 -->
Apple App Store 管理対象アプリの作成時に、国のロケールを指定できるようになります。

> [!Note]  
> 現在、Apple App Store の管理対象アプリは、米国のストアで販売されるものしか作成できません。

####  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>iOS VPP ユーザーとデバイスにライセンスされたアプリを更新する <!-- 1305564 -->  
Intune サービスを介して特定の iOS VPP トークンに対して購入されたすべてのアプリを更新するように、トークンを構成できるようになります。 アプリ ストア内の VPP アプリ更新プログラムが Intune によって検出され、デバイスのチェックイン時に自動的にデバイスにプッシュされます。

VPP トークンを設定して、自動更新を有効にする手順については、「[Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法] (/intune/vpp-apps-ios)」を参照してください。


### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング
#### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Intune データ ウェアハウスのデータ モデルに追加されたユーザー デバイス関連付けエンティティ コレクション <!-- 1187917 -->
ユーザーとデバイスのエンティティ コレクションを関連付けるユーザー デバイス関連付け情報を使って、レポートやデータの視覚エフェクトを作成できるようになりました。 このデータ モデルは、OData エンドポイントを使うか、カスタム クライアントを開発すると、[Data Warehouse Intune]\(データ ウェアハウス Intune\) ページから取得した Power BI ファイル (PBIX) を使ってアクセスできます。

#### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Windows 10 更新リングのポリシー準拠状況を確認する <!-- 1067886 -->
[ソフトウェア更新プログラム] > [更新プログラムごとのリングの展開の状態] から Windows 10 更新リングのポリシー レポートを確認できるようになります。 ポリシー レポートには、構成した更新リングの展開状態が表示されています。 

#### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>古い iOS バージョンの iOS デバイス一覧が記載された新しいレポート<!-- 1352223 -->
**[ソフトウェア更新プログラム]** ワークスペースから **[Out-of-date iOS Devices]\(古い iOS デバイス\)** レポートが利用できます。 このレポートには、iOS の更新ポリシーが対象とする監視対象の iOS デバイスの一覧と利用可能な更新が表示されます。 デバイスごとに、デバイスが自動的に更新されない理由のステータスを確認できます。 

#### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>トラブルシューティングのアプリ保護ポリシー割り当てを確認する <!--  1475003 -->
今後のリリースでは、トラブルシューティング ブレードにある **[割り当て]** ボックスの一覧に、**[App protection policy]\(アプリの保護ポリシー\)** オプションが追加される予定です。 アプリの保護ポリシーを選んで、特定のユーザーに割り当てられているアプリ保護ポリシーを確認できるようになります。



## <a name="week-of-october-2-2017"></a>2017 年 10 月 2 日の週
### <a name="intune-apps"></a>Intune アプリ
#### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>ポータル サイトでのデバイスのセットアップ ワークフローの機能強化<!--1490692-->
Android 用のポータル サイト アプリでデバイスのセットアップ ワークフローを改良しました。 言語がよりわかりやすく、会社固有のものとなり、可能な範囲で画面をまとめるようにしました。 詳細については、「[アプリ UI の新機能](whats-new-app-ui.md#week-of-october-2-2017)」ページをご覧ください。

#### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Android デバイスでの連絡先へのアクセス要求に関するガイダンスの改善<!--1484985-->

Android 用ポータル サイト アプリは、連絡先アクセス許可を受け入れるようにエンド ユーザーに求めることがよくあります。 エンド ユーザーがこのアクセスを拒否すると、条件付きアクセス用のアクセス許可を付与するように通知するアプリ内通知が表示されるようになります。 

#### <a name="secure-startup-remediation-for-android---1490712--"></a>Android でのセキュリティで保護された起動の修復<!--1490712-->

Android デバイスを持つエンド ユーザーは、ポータル サイト アプリのコンプライアンス非対応の理由をタップできるようになります。 可能であれば、問題を解決するのに適切な、設定アプリ内の場所がエンド ユーザーに直接表示されます。 

#### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Android Oreo のポータル サイト アプリにエンド ユーザー向けプッシュ通知が追加<!--1475932-->

エンド ユーザーには、Android Oreo のポータル サイト アプリが Intune サービスからのポリシーの取得などのバックグラウンド タスクが実行されているときにそれを示す追加の通知が表示されます。 これにより、ポータル サイトがデバイス上でいつ管理タスクを実行しているかが、エンド ユーザーにとってより分かりやすくなります。 これは、Android Oreo のポータル サイト アプリの[ポータル サイト UI の最適化](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune)の一環です。 

Android Oreo で有効になっている新しい UI 要素がさらに最適化されています。  エンドユーザーには、ポータル サイトが Intune サービスからのポリシーの取得などのバックグラウンド タスクを実行しているときにそれを示す追加の通知が表示されます。  これにより、ポータル サイトがデバイスで管理タスクをいつ実行しているかがエンド ユーザーにわかりやすくなります。

#### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>仕事用プロファイルを使った Android 用ポータル サイト アプリの新しい動作 <!---1485783--->

仕事用プロファイルがある Android for Work デバイスを登録すると、仕事用プロファイル内のポータル サイト アプリによって、そのデバイス上での管理タスクが実行されます。 

個人プロファイルで MAM 対応アプリを使っている場合を除き、Android 用ポータル サイト アプリを使用する機会がなくなります。 仕事用プロファイルのエクスペリエンスを向上させるために、Intune では仕事用プロファイルの登録が正常に完了した後、個人用ポータル サイト アプリが自動的に非表示になります。

Android 用ポータル サイト アプリは、[Play ストアでポータル サイト](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) を参照して **[Enable]\(有効化\)** をタップすると、個人プロファイルでいつでも有効にできます。

#### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Windows 8.1 および Windows Phone 8.1 のポータル サイトの維持モードへの移行 <!--1428681-->

2017 年 10 月より、Windows 8.1 および Windows Phone 8.1 用ポータル サイト アプリは、維持モードに移行されます。 つまり、当該アプリに加え、登録やコンプライアンスといった既存のシナリオは、これらのプラットフォームで引き続きサポートされます。 当該アプリは、Microsoft Store など、既存のリリース チャネル経由で引き続きダウンロード可能です。 

維持モードになると、当該アプリは、重要なセキュリティ更新プログラムのみを受信するようになります。 当該アプリの更新プログラムや機能が追加でリリースされることはありません。 新機能を使用するには、デバイスを Windows 10 や Windows 10 Mobile に更新することをお勧めします。 


### <a name="device-enrollment"></a>デバイスの登録

#### <a name="block-unsupported-samsung-knox-device-enrollment------1490695----"></a>サポートされていない Samsung KNOX デバイスの登録をブロックする<!--- 1490695 --->

ポータル サイト アプリでは、サポートされている Samsung KNOX デバイスのみ、登録を試みます。 MDM の登録を妨げる KNOX ライセンス認証エラーの発生を回避するために、登録対象のデバイスが [Samsung によって発行されたデバイス一覧](https://www.samsungknox.com/knox-supported-devices/knox-workspace)に掲載されている場合にのみ、その登録が試行されます。 Samsung デバイスには、KNOX をサポートするモデル番号を持つものがある一方で、そうでないものもあります。 Samsung デバイスを購入および展開する前に、デバイスの再販業者に KNOX 対応の有無について確認してください。 検証済みのデバイスの完全な一覧については、「[Android and Samsung KNOX Standard policy settings](/intune/supported-devices-browsers.md#intune-supported-devices)」 (Android および Samsung KNOX Standard のポリシー設定) をご覧ください。

#### <a name="end-of-support-for-android-43-and-lower----1171126-1326920----"></a>Android 4.3 以前のサポートの終了<!---1171126, 1326920 --->
Android 用の管理対象アプリとポータル サイト アプリで会社のリソースにアクセスするには、Android 4.4 以降を使用している必要があります。 12 月には、登録されているすべてのデバイスがインベントリから削除され、会社のリソースにアクセスできなくなります。 MDM を使わずにアプリの保護ポリシーを使用している場合、アプリは更新プログラムを受信できなくなり、時間の経過と共にエクスペリエンスの質が低下していきます。

#### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>登録されているデバイスで確認可能なデバイス情報のエンドユーザーへの通知<!--1165314-->
すべてのポータル サイト アプリの [デバイスの詳細] 画面に **[所有権の種類]** が追加されます。 これにより、ユーザーは、「[デバイスを登録した場合に会社が確認できる情報](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)」の記事から直接プライバシーの詳細を確認できるようになります。 これは近い将来、すべてのポータル サイト アプリに導入される予定です。 iOS 用については、[9 月](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017)に発表しました。


## <a name="week-of-september-25-2017"></a>2017 年 9 月 25 日の週

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="intune-supports-ios-11---1428975--"></a>Intune が iOS 11 をサポート<!--1428975-->
Intune は iOS 11 をサポートします。 これについては、[Intune サポート ブログ](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/)ですでに発表しました。

#### <a name="end-of-support-for-ios-80----1164477---"></a>iOS 8.0 のサポートの終了 <!---1164477--->
iOS 用の管理対象アプリとポータル サイト アプリから会社のリソースにアクセスするには、iOS 9.0 以降を使用している必要があります。 この 9 月までに更新されないデバイスは、ポータル サイトまたはそれらのアプリにアクセスできなくなります。 

### <a name="intune-apps"></a>Intune アプリ

#### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Windows 10 用ポータル サイト アプリに追加された更新アクション <!--1132468-->
Windows 10 向けのポータル サイト アプリでは、ユーザーがプルして更新するか、デスクトップで F5 キーを押して、アプリのデータを更新できます。



## <a name="notices"></a>通知

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Android デバイスとは別に Android for Work デバイスを管理する <!-- 1490731 EEready-->
 
**注**: 以下の変更は 11 月の更新をもってロールアウトが開始されます。ただし、自分のアカウントでは実行に時間がかかることがあります。 変更が自分のアカウントに適用されると、Office 365 ポータルで確認通知が届きます。 ロールアウト後、管理機能の追加のオプションを使用できるようになります。 ロールアウト中、エンド ユーザーのエクスペリエンスに対する変更はありません。
 
Intune は、Android プラットフォームに依存することなく、Android for Work デバイスの登録を管理します。 この設定は、**[デバイスの登録]**、 > **[登録制限]**、 > **[デバイスの種類の制限]** で管理されます。 (以前の場所は **[デバイス登録]**、**[Android for Work への登録]**、**[Android for Work の登録設定]** でした。)
 
既定では、Android for Work デバイス設定は Android デバイスの設定と同じになります。 ただし、Android for Work 設定を変更した後は、同じではなくなります。
 
個人の Android for Work 登録をブロックした場合、会社の Android デバイスのみを Android for Work として登録できます。
 
新しい設定を使用する場合、次の点を考慮してください。
 
#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>以前に Android for Work 登録をオンボードしたことがない
 
新しい Android for Work プラットフォームは、既定の [デバイスの種類の制限] でブロックされます。 この機能をオンボードした後は、デバイスを Android for Work に登録できます。 そのためには、既定値を変更するか、新しい [デバイスの種類の制限] を作成して既定の [デバイスの種類の制限] に代えます。
 
#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Android for Work 登録をオンボードした
 
以前にオンボードしている場合、状況は選んだ設定によって変わります。
 
| Setting | 既定の [デバイスの種類の制限] の Android for Work の状態 | 注 |
| --- | --- | --- |
| **すべてのデバイスを Android として管理する** | ［ブロック済み］ | すべての Android デバイスを Android for Work なしで登録する必要があります。 |
| **サポートされているデバイスを Android for Work として管理する** | 許可済み | Android for Work 対応のすべての Android デバイスを Android for Work に登録する必要があります。 |
| **これらのグループに所属するユーザーのサポートされているデバイスのみを Android for Work として管理する** | ［ブロック済み］ | 既定値をオーバーライドする別個の [デバイスの種類の制限] ポリシーが作成されました。 このポリシーによって、以前に選択したグループで Android for Work 登録が許可されます。 選択されたグループ内のユーザーには、Android for Work デバイスの登録が引き続き許可されます。 その他すべてのユーザーには、Android for Work の登録が禁止されます。 |
 
いずれの場合でも、意図した規制が維持されます。 自分の環境で Android for Work のグローバル許可またはグループ別許可を維持するための操作は必要ありません。

### <a name="deprecating-support-for-os-x-mavericks-1010-and-previous-versions-of-macos---1489263-plan-for-change-for-1802--"></a>OS X Mavericks 10.10 と以前のバージョンの macOS のサポートは廃止に <!--1489263, plan for change for 1802-->
2018 年 2 月に OS X Yosemite 10.10 と以前のバージョンの macOS を搭載したデバイスの登録が廃止されることをお知らせします。 Intune は OS X El Capitan 10.11 以降を完全サポートします。

### <a name="new-path-for-managed-devices-in-graph-api----1586728---"></a>Graph API での管理対象デバイスに対する新しいパス <!-- 1586728 -->
Graph API のベータ版で管理対象デバイスにアクセスするために使用されるパスが変更されています。 

| | |
|--|--|
| 現在のパス |  https://graph.microsoft.com/beta/managedDevices |
| 新しいパス | https://graph.microsoft.com/beta/deviceManagement/managedDevices |

10 月中は両方のパスを使うことができます。 10 月のサービス リリース後は、新しいパスのみが機能します。  Graph API を使用して管理対象デバイスにアクセスしている場合は、スクリプトとアプリケーションを新しいパスで更新して確認してください。 追加の変更については、毎月の [Graph API 変更ログ](https://developer.microsoft.com/graph/docs/concepts/changelog)でご確認ください。


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->
Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure Portal の Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューは Intune クラシック ポータルのリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントで Azure Portal にアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Azure Portal で置き換えられる管理ロール
Intune クラシック ポータル (Silverlight) で使用される既存のモバイル アプリケーション管理 (MAM) の管理ロール (共同作成者、所有者、および読み取り専用) は、Intune Azure Portal の新しいロール ベースの管理制御 (RBAC) の完全なセットで置き換えられます。 Azure Portal に移行すると、管理者をこれらの新しい管理ロールに割り当て直す必要があります。 RBAC と新しいロールの詳細については、[Microsoft Intune のロール ベースのアクセス制御](/intune/role-based-access-control)に関する記事を参照してください。



## <a name="whats-coming"></a>今後の更新情報

### <a name="conditional-access-policies-for-intune-will-only-be-available-from-the-azure-portal-----1737088---"></a>Intune の条件付きアクセス ポリシーは、Azure Portal からのみ利用できる<!-- 1737088 --> 
Microsoft では、条件付きアクセスを構成および管理する場所を単純化しています。 現在、Intune App Protection (MAM) ブレードと [Microsoft Azure Portal](https://manage.windowsazure.com) のクラシック Azure AD エクスペリエンスから条件付きアクセスを管理できます。 1 月以降は、**[Azure Active Directory]**  >  **[条件付きアクセス]**からのみ [Azure Portal](https://portal.azure.com) のポリシーを構成したり管理したりすることができます。 便宜上、**[Intune]**  >  **[条件付きアクセス]**の、Azure Portal 内にある Intune からこのブレードにアクセスすることもできます。

### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine---1592747--"></a>Intune のデバイス コンプライアンス エンジンを使用した Jamf に登録された macOS デバイスの管理 <!--1592747-->
2018 年初めより、Jamf から Intune に macOS デバイスの状態情報が送信されるようになります。その情報はその後、Intune コンソールで定義されたポリシーへの準拠が評価されます。 条件付きアクセスでは、デバイスのコンプライアンス対応状態や、その他の条件 (場所やユーザー リスクなど) に基づいて、Azure AD に接続されたクラウド アプリケーションやオンプレミス アプリケーション (Office 365 など) にアクセスする macOS デバイスにコンプライアンスを適用します。

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Intune iOS ポータル サイト アプリのサポートの変更  <!-- 1164474  -->
間もなく、iOS 用 Microsoft Intune ポータル サイト アプリが新しいバージョンになり、iOS 9.0 以降を実行しているデバイスのみがサポートされるようになります。 iOS 8 をサポートするバージョンのポータル サイトは、今後、非常に短い時間だけ使用を続けることができます。 ただし、MAM が有効な iOS アプリも使っている場合は、iOS 9.0 以降しかサポートされないので、エンド ユーザーを最新の OS に更新させる必要があります。 

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
具体的な日付は決まっていませんが、計画できるように事前にお知らせします。 ユーザーが iOS 9 以降に更新したことを確認し、ポータル サイト アプリのリリース時にはポータル サイト アプリを更新するようエンドユーザーに要求してください。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
新しい Intune の機能を最大限に活用するには iOS 9.0 以降に更新するようユーザーに推奨します。  新しいバージョンのポータル サイトをインストールして新しい機能を活用するようユーザーに推奨します。

Azure Portal の Intune で [デバイス] の [すべてのデバイス] に移動し、iOS のバージョンでフィルター処理して、現在 iOS 9 より前のオペレーティング システムを使っているデバイスを確認します。


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->
Apple は、Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。

Microsoft では、新しい ATS 要件を適用する Apple TestFlight プログラムから、iOS 用ポータル サイト アプリのバージョンを入手できるようにしています。 ATS コンプライアンスをテストできるように、このバージョンを試す場合は、お客様の姓名、電子メール アドレス、および会社名を <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> に電子メールで送信してください。 詳細については、[Intune サポートのブログ](https://aka.ms/compportalats)をご覧ください。

## <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [ポータル Web サイトの UI の新機能](whats-new-app-ui.md)
* [以前の月の新機能](whats-new-archive.md)
