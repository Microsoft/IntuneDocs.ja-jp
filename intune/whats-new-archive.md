---
title: Microsoft Intune の過去数か月の新機能 - Azure | Microsoft Docs
titlesuffix: ''
description: Intune の新機能に関するページの過去の通知を確認する
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 45933ecab26a9c2a4139cdcd16400467bbdd5bf8
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321800"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Microsoft Intune の新機能 (過去数か月)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="november-2017"></a>2017 年 11 月

### <a name="troubleshoot-enrollment-issues-----746324---"></a>登録に関する問題をトラブルシューティングする <!-- 746324 -->

**トラブルシューティング** ワークスペースに、ユーザーの登録に関する問題が表示されるようになりました。 問題に関する詳細と推奨される修復手順は、管理者およびヘルプ デスクのオペレーターが問題をトラブルシューティングするのに役立ちます。 登録に関する特定の問題はキャプチャされず、一部のエラーには推奨される修復方法がない場合があります。

### <a name="group-assigned-enrollment-restrictions----747598---"></a>グループ割り当て登録制限 <!-- 747598 -->

Intune 管理者は[ユーザー グループに対してカスタムの登録制限として [デバイスの種類] と [デバイスの上限数] を作成できるようになりました](enrollment-restrictions-set.md)。

Intune Azure ポータルで、制限タイプごとに最大 25 個のインスタンスを作成できます。作成したインスタンスはユーザー グループに割り当てることができます。 グループに割り当てられた制限は既定の制限をオーバーライドします。

制限タイプのすべてのインスタンスは、厳密に順序付けられた一覧で保守管理されます。 この順序により、競合解決の優先度の値が決まります。 複数の制限インスタンスの影響を受けるユーザーは、優先度の値が最も高いインスタンスによって制限されます。 インスタンスの優先度は、一覧内の別の位置にドラッグすることによって変更できます。

Android For Work 登録メニューから登録制限メニューに Android For Work 設定が移行されたとき、この機能が使えるようになります。 この移行には数日かかる場合があります。11 月リリースのその他の部分に関してアカウントがアップグレードされた後に、登録制限のグループ割り当てが有効になる場合があります。

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>複数のネットワーク デバイス登録サービス (NDES) コネクタのサポート <!-- 1528104 -->

NDES を利用すれば、ドメイン資格情報なしでモバイル デバイスを実行し、Simple Certificate Enrollment Protocol (SCEP) に基づいて証明書を取得できます。
今回の更新で、複数の NDES コネクタがサポートされるようになりました。

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Android デバイスとは別に Android for Work デバイスを管理する <!-- 1490731 EEready-->

Intune は、Android プラットフォームに依存することなく、Android for Work デバイスの登録を管理します。 この設定は、**[デバイスの登録]**、 > **[登録制限]**、 > **[デバイスの種類の制限]** で管理されます。 (以前の場所は **[デバイス登録]**、 > **[Android for Work への登録]**、 > **[Android for Work の登録設定]** でした。)

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

### <a name="google-play-protect-support-on-android----908720---"></a>Android の Google Play Protect サポート <!-- 908720 -->

Android Oreo のリリースに伴い、セキュリティで保護されたアプリおよび Android イメージをユーザーや組織が実行できる、Google Play Protect という一連のセキュリティ機能が Google より提供されました。 Intune では、SafetyNet リモート構成証明をはじめとした Google Play Protect の各機能をサポートするようになりました。 管理者は、Google Play Protect が構成され正常な状態であることが求められるコンプライアンス ポリシー要件を設定できます。
**[SafetyNet デバイスの構成証明]** 設定では、デバイスが正常な状態であり危険にさらされていないことを確認するために、デバイスを Google サービスに接続する必要があります。 管理者は、インストール済みのアプリが Google Play 開発者サービスによって検証されることを必須にする、Android for Work の構成プロファイル設定を設定することもできます。 デバイスが Google Play Protect の要件に準拠していない場合、条件付きアクセスでは、ユーザーが企業リソースにアクセスできなくなる可能性があります。

- 「[デバイスのコンプライアンス ポリシーを作成して Google Play Protect を有効にする方法](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect)」を参照してください。

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>管理対象アプリから許可されるテキスト プロトコル <!-- 1414050  -->

Intune App SDK によって管理されているアプリは、SMS メッセージを送信できます。


### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>インストール保留中の状態を含むように更新されたアプリ インストール レポート<!-- 1249446 -->  

**[モバイル アプリ]** ワークロードの **[アプリ]** 一覧から表示できるアプリ別の **[アプリ インストールの状態]** レポートが、ユーザーとデバイスについて **[インストール保留中]** カウントを表示するようになりました。

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>モバイルの脅威を検出するための iOS 11 アプリ インベントリ API <!-- 1391759 -->

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

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>ハイブリッド MDM のユーザーとデバイスを Intune スタンドアロンに移行する<!-- 1463747 wnready -->
ハイブリッド MDM から Azure Portal 内の Intune にユーザーとそのデバイスを移動するための新しいプロセスとツールが利用可能になりました。これにより、次の操作を行うことができます。
- Configuration Manager コンソールから Azure Portal 内の Intune にポリシーとプロファイルをコピーする
- ユーザーのサブセットを Azure Portal 内の Intune に移動し、残りのユーザーをハイブリッド MDM で保持したままにする
- 再登録せずに、Azure Portal 内の Intune にデバイスを移行する

詳しくは、「[ハイブリッド MDM のユーザーとデバイスを Intune スタンドアロンに移行する](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)」を参照してください。

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>オンプレミスの Exchange Connector の高可用性のサポート  <!-- 676614 -->
Exchange Connector によって、指定の CAS で Exchange への接続が作成された後、コネクタで別の CAS も検出できるようになりました。 メインの CAS が利用できなくなった場合、再度利用可能になるまで、コネクタが別の CAS (ある場合) にフェールオーバーします。 詳細については、「[オンプレミスの Exchange Connector の高可用性のサポート](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support)」をご覧ください。

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>iOS デバイスをリモート再起動する (監視モードのみ) <!-- 1424595 -->

デバイス アクションを利用し、監視されている iOS 10.3 以降のデバイスの再起動をトリガーできるようになりました。 デバイス再起動アクションの利用方法については、「[Intune でデバイスをリモートで再起動する](device-restart.md)」を参照してください。

> [!Note]
> このコマンドは、監視されているデバイスと**デバイス ロック** アクセス権を要求します。 デバイスがすぐに再起動します。 パスコードでロックされている iOS デバイスが再起動後に Wi-Fi ネットワークに再び参加することはありません。再起動後、サーバーと通信できないことがあります。

### <a name="single-sign-on-support-for-ios----1333645---"></a>iOS のシングル サインオン サポート <!-- 1333645 -->  

iOS ユーザーのためにシングル サインオンを使用できます。 シングル サインオン ペイロードのユーザー資格情報を探すようにプログラミングされている iOS アプリは、このペイロード構成更新で機能します。 UPN と Intune デバイス ID を利用し、プリンシパル名と領域を構成することもできます。 詳しくは、「[Configure Intune for iOS device single sign-on](sso-ios.md)」 (iOS 用 Intune のデバイス シングル サインオンを構成する) を参照してください。

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>個人デバイスの "iPhone を探す" を追加 <!--1427287-->
iOS デバイスのアクティベーション ロックがオンになっているかどうかを表示できるようになりました。 この機能は以前、クラシック ポータルの Intune にありました。

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>管理されている macOS デバイスを Intune でリモート ロックする <!-- 1437691 -->

紛失した macOS デバイスをロックできます。6 桁の回復用 PIN を設定できます。 ロックされているとき、別のデバイス アクションが送信されるまで、**デバイス概要**ブレードにその PIN が表示されます。

詳細については、「[マネージド デバイスを Intune でリモートからロックする](device-remote-lock.md)」を参照してください。

### <a name="new-scep-profile-details-supported----1559808---"></a>サポートされる新しい SCEP プロファイル詳細 <!-- 1559808 -->

Windows、iOS、macOS、Android プラットフォームで SCEP プロファイルを作成するとき、管理者は追加設定を設定できるようになりました。  管理者は、IMEI、シリアル番号、あるいはサブジェクト名の形式の電子メールなど、一般名を設定できます。

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset----1588489---"></a>工場出荷時の設定へのリセット中にデータを保持する <!--1588489 -->
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


### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Windows 10 更新プログラム リング割り当てが表示される <!-- 1621837 -->
**トラブルシューティング**時、表示しているユーザーに関して、Windows 10 更新プログラム リング割り当てを表示することができます。  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Windows Defender Advanced Threat Protection の報告頻度設定 <!-- 1455974  -->
Windows Defender Advanced Threat Protection (WDATP) サービスを利用するとき、管理者はマネージド デバイスの報告頻度を管理できます。 新しい **[テレメトリの報告頻度を早める]** オプションを利用すると、WDATP はデータを収集し、さらに頻繁にリスクを評価します。 報告の既定値で速度とパフォーマンスが最適化されます。 報告の頻度を増やすことは、リスクの高いデバイスの場合に有益となります。 この設定は **[デバイス構成]** の **[Windows Defender ATP]** プロファイルにあります。

### <a name="audit-updates----1412961---"></a>監査更新 <!-- 1412961 -->  
Intune の監査機能により、Intune に関連する変更操作が記録されます。  あらゆる作成操作、更新操作、削除操作、リモート タスク操作が記録され、1 年間保存されます。  Azure Portal では、ワークロード別の監査データを過去 30 日分表示できます。データの絞り込みも可能です。  対応する Graph API により、前年に格納された監査データを取得できます。

監査は **[モニター]** グループの下にあります。 ワークロード別に **[監査ログ]** メニュー項目があります。

### <a name="company-portal-app-for-macos-is-available---1541700--"></a>macOS 用ポータル サイト アプリ提供開始 <!--1541700-->
macOS での Intune ポータル サイトのエクスペリエンスが更新されました。ユーザーが登録済みのすべてのデバイスで必要となるすべての情報とコンプライアンス通知が明確に表示されるように最適化されました。 また、いったん Intune ポータル サイトをデバイスに展開すると、macOS 用 Microsoft 自動更新から更新プログラムが提供されるようになります。 macOS デバイスから Intune ポータル サイトにログインすることで、新しい macOS 用 Intune ポータル サイトをダウンロードできます。

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner が承認済みアプリのモバイル アプリ管理 (MAM) リストの一部に <!-- 1248473 -->
iOS および Android 用の Microsoft Planner アプリが、承認済みアプリのモバイル アプリ管理 (MAM) の一部となりました。 このアプリは、Azure Portal の Intune App Protection ブレードからすべてのテナントに対して構成できます。
- 詳細については、[承認済みアプリの MAM リスト](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)に関するページをご覧ください。

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>iOS デバイスでのアプリごとの VPN 要件の更新頻度 <!-- 1547061 -->  
管理者が iOS デバイス上のアプリでアプリごとの VPN 要件を削除できるようになりました。影響を受けるデバイスでは、次回の Intune チェックイン後、通常 15 分以内に反映されます。  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Exchange Connector 用 System Center Operations Manager 管理パックのサポート <!-- 885457 -->
Exchange Connector 用 System Center Operations Manager (SCOM) 管理パックを Exchange Connector のログ解析に利用できるようになります。 この機能により、問題のトラブルシューティングが必要な場合に、別の方法でサービスを監視できるようになります。

### <a name="co-management-for-windows-10-devices-----1243445---"></a>Windows 10 デバイスの共同管理 <!-- 1243445 -->
共同管理は、従来の管理から最新の管理への橋渡しとなるソリューションであり、段階的なアプローチを使って移行する方向を提示します。 基本的に、共同管理は、Windows 10 デバイスを Configuration Manager と Microsoft Intune で同時に管理すると共に、Active Directory (AD) と Azure Active Directory (Azure AD) に同時に参加させることができるソリューションです。  この構成は、一度にすべてを移行できない組織が適切なペースで時間をかけて最新化するパスを提供します。  

### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>OS のバージョンによる Windows 登録の制限 <!-- 245498 -->
Intune 管理者は、デバイス登録に関して、Windows 10 の最小バージョンと最大バージョンを指定できるようになりました。 これらの制限は **[プラットフォーム構成]** ブレードで設定できます。

Intune では、Windows 8.1 の PC とスマートフォンを引き続き登録できます。 ただし、下限と上限を設定できるのは Windows 10 のバージョンだけです。 8.1 デバイスの登録を許可するには、下限を空のままにします。

### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Windows AutoPilot の未割り当てデバイスのアラート <!-- 1631236 -->
**[Microsoft Intune]**、**[デバイス登録]**、**[概要]** ページには、Windows AutoPilot の未割り当てデバイスの新しいアラートがあります。 このアラートでは、AutoPilot プログラムからのデバイスで、AutoPilot Deployment プロファイルが割り当てられていないデバイスの数が示されます。 アラート内の情報を利用してプロファイルを作成し、未割り当てデバイスに割り当てます。 アラートをクリックすると、Windows AutoPilot の完全一覧とそれらに関する詳細が表示されます。 詳細については、「[Windows AutoPilot Deployment プログラムを使用して Windows デバイスを登録する](https://docs.microsoft.com/intune/enrollment-autopilot)」を参照してください。


### <a name="refresh-button-for-devices-list-------1333581---"></a>デバイス一覧の [更新] ボタン <!-- 1333581 -->
デバイス一覧は自動的に更新されないため、新しい [更新] ボタンを利用し、一覧に表示されるデバイスを更新できます。

### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Symantec クラウド証明機関 (CA) のサポート <!-- 1333638 -->    
Intune は Symantec クラウド CA をサポートするようになり、Intune Certificate Connector は Symantec クラウド CA から Intune でマネージド デバイスに PKCS 証明書を発行できます。 Microsoft 証明機関 (CA) で Intune Certificate Connector を既に使っている場合は、Intune Certificate Connector の既存の設定を使用して、Symantec CA のサポートを追加できます。

### <a name="new-items-added-to-device-inventory-----1404455---"></a>デバイス インベントリに追加された新しい項目 <!--1404455 -->
[登録デバイスによって取得されるインベントリ](device-inventory.md)で次の新しい項目を利用できるようになりました。

- Wi-Fi MAC アドレス
- 記憶域の合計容量
- 合計空き容量
- MEID
- 通信事業者

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>デバイスでの最低限の Android セキュリティ パッチによりアプリへのアクセスを設定する <!-- 1278463 -->   
管理者は、管理されたアカウントの管理対象アプリケーションにアクセスするために、デバイスにインストールする必要がある最低限の Android セキュリティ パッチを定義することができます。

> [!Note]  
> この機能は、Google によって Android 6.0 以降のデバイスについてリリースされたセキュリティ パッチだけを制限します。

### <a name="app-conditional-launch-support----1193313---"></a>アプリの条件付き起動のサポート <!-- 1193313 -->
IT 管理者は、アプリケーションの起動時にモバイル アプリ管理 (MAM) によって数値の PIN ではなくパスコードを強制する要件を、Azure 管理ポータルで設定できるようになりました。 構成した場合、ユーザーは、MAM 対応のアプリケーションにアクセスする前に、要求された時点で、パスコードを設定および使用する必要があります。 パスコードは、少なくとも 1 つの特殊文字または大文字/小文字アルファベットを含む数値 PIN と定義されます。 Intune の今回のリリースでは、この機能を利用できるのは **iOS のみ**です。 Intune は、数値 PIN に同様の方法でパスコードをサポートし、最小の長さを設定して、文字やシーケンスの繰り返しを許可します。 この機能では、対象のアプリケーションにパスコード設定を適用するのではなく、Intune アプリ SDK とこの機能のコードとを統合するために、アプリケーション (WXP、Outlook、Managed Browser、Yammer など) の参加が必要となります。

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>デバイス インストール状態レポートでの基幹業務アプリのバージョン番号 <!-- 1233999 -->
このリリースでは、デバイス インストール状態レポートに、iOS および Android 用基幹業務アプリのバージョン番号が表示されます。 この情報を使って、アプリのトラブルシューティングや、古いバージョンのアプリを実行しているデバイスの検索を行うことができます。

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>管理者は、デバイス構成プロファイルを使ってデバイスでのファイアウォールの設定を構成できるようになる <!-- 951708 -->   
管理者は、デバイスのファイアウォールを有効にすることができ、ドメイン ネットワーク、プライベート ネットワーク、パブリック ネットワークのさまざまなプロトコルを構成することもできます。  これらのファイアウォールの設定は、"Endpoint Protection" プロファイルで確認できます。

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard は、組織での定義に従って、信頼されていない Web サイトからデバイスを保護する <!-- 958257 -->   
管理者は、Windows Information Protection ワークフローまたはデバイス構成の新しい "ネットワーク境界" プロファイルを使って、"信頼できる" サイトまたは "企業" サイトを定義できます。 64 ビット Windows 10 デバイスの信頼されたネットワーク境界内にないすべてのサイトは、Microsoft Edge で表示された場合、代わりに Hyper-V 仮想コンピューター内のブラウザーで開かれます。

Application Guard は、"Endpoint Protection" プロファイル内のデバイス構成プロファイルで確認できます。 デバイス構成プロファイルでは、管理者は、仮想化されたブラウザーとホスト マシンの相互作用、信頼されないサイトと信頼されるサイト、および仮想化されたブラウザーで生成されたファイルの保存を構成することができます。 デバイスで Application Guard を使うには、最初にネットワーク境界を構成する必要があります。 デバイスごとにネットワーク境界を 1 つだけ定義することが重要です。  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows 10 Enterprise の Windows Defender Application Control は、承認されたアプリのみを信頼するモードを提供する <!-- 1031096 -->    
毎日何千もの悪意あるファイルが作成される状況においては、ウイルス対策の署名ベースの検出を使ってマルウェアに対抗するのでは、新しい攻撃を十分に防ぐことができない可能性があります。 Windows 10 Enterprise の Windows Defender Application Control を使うと、ウイルス対策ソフトウェアや他のセキュリティ ソリューションによってブロックされない限りアプリを信頼するモードから、企業によって承認されたアプリのみをオペレーティング システムが信頼するモードにデバイスの構成を変更できます。 Windows Defender Application Control でアプリに信頼を割り当てます。

Intune を使って、アプリケーション制御ポリシーを "監査のみ" モードまたは強制モードに構成できます。 "監査のみ" モードで実行している場合、アプリはブロックされません。 "監査のみ" モードでは、すべてのイベントがローカル クライアント ログに記録されます。 また、Windows コンポーネントと Microsoft Store アプリの実行のみを許可するか、またはインテリジェント セキュリティ グラフで定義されている評判の良いアプリの実行も許可するかを構成することもできます。

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows 10 用の新しい侵入防止機能セットである Window Defender Exploit Guard <!-- 1063615 -->   
Window Defender Exploit Guard は、アプリケーションが悪用される可能性を減らすカスタム規則を含み、マクロとスクリプトの脅威を防止し、評判が低い IP アドレスへのネットワーク接続を自動的にブロックして、ランサムウェアや不明の脅威からデータを保護できます。 Windows Defender Exploit Guard は、次のコンポーネントで構成されます。

- **攻撃の回避 (ASR)** は、マクロ、スクリプト、メールの脅威を防ぐことができる規則を提供します。
- **フォルダー アクセスの制御**は、保護されているフォルダーのコンテンツへのアクセスを自動的にブロックします。
- **ネットワーク フィルター**は、アプリから評判の悪い IP/ドメインへの発信接続をブロックします。
- **Exploit Protection** は、アプリケーションを悪用から保護するために使うことができるメモリ、制御フロー、およびポリシーの制限を提供します。

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Windows 10 デバイスの Intune で PowerShell スクリプトを管理する <!-- 790537 -->

Intune 管理拡張機能を使用すると、Windows 10 デバイスで実行されている Intune で PowerShell スクリプトをアップロードできます。 この拡張機能は Windows 10 モバイル デバイス管理 (MDM) 機能を補完するもので、最新の管理に簡単に移行できます。 詳細については、「[Windows 10 デバイスの Intune で PowerShell スクリプトを管理する](intune-management-extension.md)」を参照してください。

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Windows 10 の新しいデバイスの制限設定 <!-- 1308850 -->
-    メッセージング (モバイルのみ) - テストまたは MMS のメッセージを無効化します
-    パスワード - FIPS と、認証用の Windows Hello デバイス セカンダリ デバイスの使用を有効にする設定 
-    ディスプレイ - レガシ アプリの GDI スケーリングをオンまたはオフにする設定

### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Windows 10 キオスク モード デバイスの制限 <!-- 1308872 -->   
Windows 10 デバイスのユーザーをキオスク モードに制限することができます。これは、一連の定義済みアプリにユーザーを制限します。  そのためには、Windows 10 デバイス制限プロファイルを作成し、キオスク設定を設定します。

キオスク モードは、**シングル アプリ** (1 つのアプリだけの実行をユーザーに許可) または**マルチ アプリ** (アプリのセットへのアクセスを許可) の 2 つのモードをサポートします。  ユーザー アカウントとデバイス名を定義します。これらにより、サポートされるアプリが決まります。  ユーザーはログイン時に定義済みのアプリに制限されます。  詳細については、「[AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)」を参照してください。 

キオスク モードには以下が必要です。

- Intune が MDM 機関である必要があります。
- アプリは、ターゲット デバイスに既にインストールされている必要があります。
- デバイスは、[適切にプロビジョニングされている](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)必要があります。

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>ネットワーク境界を作成するための新しいデバイス構成プロファイル <!-- 1311967 -->   
**ネットワーク境界**と呼ばれる新しいデバイス構成プロファイルが、他のデバイス構成プロファイルと同じ場所にあります。 このプロファイルを使用して、会社のもので信頼できると見なす必要があるオンライン リソースを定義します。 Windows Defender Application Guard や Windows Information Protection などの機能をデバイスで使用するには、"*事前*" にデバイスに対してネットワーク境界を定義する必要があります。 デバイスごとにネットワーク境界を 1 つだけ定義することが重要です。

信頼できるエンタープライズ クラウド リソース、IP アドレス範囲、内部プロキシ サーバーを定義できます。 定義したネットワーク境界は、Windows Defender Application Guard や Windows Information Protection 保護などの他の機能で使うことができます。

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Windows Defender ウイルス対策用の 2 つの追加設定<!-- 1338409 -->  
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

### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Windows 10 デバイスに追加された Citrix VPN <!-- 1512457 -->  
Windows 10 デバイス用に Citrix VPN を構成できます。 Windows 10 以降用に VPN を構成するときに、**[基本 VPN]** ブレードの *[接続の種類を選びます]* の一覧で、Citrix VPN を選ぶことができます。

> [!Note]
> Citrix の構成は、iOS および Android 用に存在しました。

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Wi-Fi 接続は iOS で事前共有キーに対応 <!-- 1550823 -->
ユーザーは iOS デバイスで WPA/WPA2 Personal 接続に事前共有キー (PSK) を使用するように Wi-Fi プロファイルを構成できます。 これらのプロファイルは、デバイスが Intune に登録されたとき、ユーザーのデバイスにプッシュされます。

プロファイルがデバイスにプッシュされたとき、次の手順はプロファイル構成によって決まります。  自動的に接続するように設定されている場合、ネットワークが次に必要になったとき、自動的に接続されます。  プロファイルが手動接続になっている場合、ユーザーは接続を手動で開始する必要があります。  

### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>iOS の管理対象アプリ ログにアクセス <!-- 1469920 -->
Managed Browser をインストールしているエンド ユーザーは、Microsoft が公開したあらゆるアプリの管理状態を表示し、管理対象 iOS アプリの問題を解消するためにログを送信できるようになりました。

iOS デバイスの Managed Browser でトラブルシューティング モードを有効にする方法については、「[iOS で Managed Browser を使用し、管理対象アプリ ログにアクセスする方法](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios)」を参照してください。

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>iOS 用ポータル サイト バージョン 2.9.0 でのデバイスのセットアップ ワークフローの機能強化<!-- 1417174 -->

iOS 用ポータル サイト アプリでのデバイス セットアップ ワークフローが改善されました。 言葉がよりわかりやすくなり、可能な範囲で画面をまとめました。 セットアップのテキスト全体でお客様の会社名を使用することで、表現がより会社に合ったものになっています。 この更新されたワークフローについては、 [アプリ UI ページの新機能](whats-new-app-ui.md)に関するページをご覧ください。


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>ユーザー エンティティにデータ ウェアハウス データ モデルの最新のユーザー データが含まれている<!-- 1544273 -->
Intune データ ウェアハウス データ モデルの最初のバージョンでは、最近の Intune 履歴データのみが含まれていました。 レポートの作成者は、ユーザーの最新の状態をキャプチャできませんでした。 今回の更新プログラムでは、最新のユーザー データを使用して**ユーザー エンティティ**が設定されます。


## <a name="october-2017"></a>2017 年 10 月

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>iOS と Android の基幹業務アプリのバージョン番号が表示可能 <!-- 1380712 -->

Intune では、iOS と Android の基幹業務アプリのバージョン番号が表示されるようになりました。 Azure Portal のアプリ一覧とアプリ概要ブレードで番号が表示されます。 エンド ユーザーは、ポータル サイト アプリと Web ポータルでアプリ番号を確認できます。

__バージョン番号 (フル)__ このフル バージョン番号はアプリのリリースを特定します。 この番号は _バージョン_(_ビルド_) の形式で表示されます。 たとえば、2.2(2.2.17560800) のようになります。

バージョン番号 (フル) を構成する 2 つの要素:

 - **バージョン**  
   バージョン番号は、人間が判読できるアプリのリリース番号です。 エンド ユーザーがアプリの各種リリースを区別するために使用されます。

 - **ビルド番号**  
    ビルド番号は、アプリの検出に利用される内部番号です。また、プログラミングでアプリを管理するために利用されます。 ビルド番号は、コードの変更を参照するアプリのイテレーションを参照します。

バージョン番号と基幹業務アプリの開発については、「[Microsoft Intune アプリ SDK の概要](app-sdk-get-started.md#line-of-business-app-version-numbers)」を参照してください。

### <a name="device-and-app-management-integration----677972---"></a>デバイスとアプリの管理の統合 <!-- 677972 -->   
Intune のモバイル デバイス管理 (MDM) とモバイル アプリケーション管理 (MAM) はどちらも Azure Portal からアクセスできるようになり、Intune はアプリケーション管理とデバイス管理に関する IT 管理者エクスペリエンスの統合を開始しました。 これらの変更は、デバイスとアプリの管理エクスペリエンスの簡素化を目的としたものです。

MDM と MAM の変更の詳細については、[Intune サポート チーム ブログ](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/)での案内をご覧ください。

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Apple デバイスの新しい登録アラート <!-- 1471790 -->
登録の概要ページには、IT 管理者のために、Apple デバイスの管理に便利なアラートが表示されるようになります。 Apple MDM プッシュ証明書の有効期間が近づいたり、既に過ぎているとき、Device Enrollment Program の有効期間が近づいたり、既に過ぎているとき、Device Enrollment Program に未割り当てのデバイスがあるとき、アラートが概要ページに表示されます。

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>デバイス登録のないアプリ構成のトークン置換をサポート <!-- 1080364 -->

登録されていないデバイス上のアプリに関して、アプリ構成の動的な値にトークンを利用できます。 詳細については、「[デバイス登録なしで管理対象アプリ用アプリ構成ポリシーを追加する](app-configuration-policies-managed-app.md)」を参照してください。

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Windows 10 用ポータル サイト アプリの更新内容 <!--1299474-->
Windows 10 用ポータル サイト アプリの [設定] ページが更新され、すべての設定で、設定と目的のユーザー アクションの一貫性が高まっています。 また、その他の Windows アプリのレイアウトと一致させる更新も行われています。 更新前/後のイメージは、[アプリ UI ページの新機能](whats-new-app-ui.md)に関するページでご覧いただけます。

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>Windows 10 デバイスで確認できるデバイス情報のエンドユーザーへの通知 <!--1337920-->
Windows 10 用ポータル サイト アプリの [デバイスの詳細] 画面に **[所有権の種類]** が追加されました。 これにより、ユーザーは、Intune エンドユーザー ドキュメントのこのページから直接プライバシーの詳細を確認できるようになります。この情報は、**[バージョン情報]** 画面でも確認できます。

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Android 用ポータル サイト アプリに関するフィードバック プロンプト <!--1165249-->
Android 用ポータル サイト アプリでは、エンド ユーザー フィードバックを即時要求します。 このフィードバックは Microsoft に直接送信され、エンドユーザーは一般の Google Play ストアでアプリをレビューできます。 フィードバックは必須ではなく、ユーザーは簡単にこれを拒否して、アプリの使用を続行できます。

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Android 向けポータル サイト アプリに関してユーザーの自己解決をサポートする <!-- 1573324, 1573150, 1558616, 1564878 -->

Android 向けポータル サイト アプリでは、エンド ユーザーへの指示が追加されています。それは新しいユース ケースの理解や、可能な場合にはその自己解決にも役立ちます。
- 追加が許されているデバイスの最大数に到達した場合、デバイスを削除するように、エンド ユーザーは [Azure Active Directory ポータル](https://account.activedirectory.windowsazure.com/r/#/profile)に誘導されます。
- [Samsung Knox デバイスのアクティベーション エラーを解消する](https://go.microsoft.com/fwlink/?linkid=859718)か、[節電モードをオフにする](/intune-user-help/power-saving-mode-android)ための手順がエンド ユーザーに表示されます。 いずれの解決策でも問題が解消されない場合、[Microsoft にログを送信する](/intune-user-help/send-logs-to-microsoft-android)方法を説明します。

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Android デバイスで利用できる新しい '解決' アクション <!-- 1583480 -->

Android のポータル サイト アプリの _[デバイス設定の更新]_ ページに '解決' アクションが導入されます。 このオプションを選択すると、デバイスの非準拠の原因になっている設定にエンド ユーザーが直接誘導されます。 Android 向けのポータル サイト アプリでは現在のところ、[デバイス パスコード](/intune-user-help/set-your-pin-or-password-android)、[USB デバッグ](/intune-user-help/you-need-to-turn-off-usb-debugging-android)、[不明なソース](/intune-user-help/you-need-to-turn-off-unknown-sources-android)設定に対してこのアクションがサポートされています。

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Android 用ポータル サイトのデバイスのセットアップ進行状況インジケーター <!-- 1565657 -->
Android 用ポータル サイト アプリでは、ユーザーがデバイスを登録しているときに、デバイスのセットアップ進行状況インジケーターが示されます。 このインジケーターで新しいステータスが表示されます。初めに表示されるものから挙げると、[Setting up your device...] \(デバイスをセットアップしています...\)、[Registering your device...] \(デバイスを登録しています...\)、[Finishing registering your device...] \(デバイス登録を終了しています...\)、[Finishing setting up your device...] \(デバイス セットアップを終了しています...\) です。

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>iOS 用ポータル サイトでの証明書ベースの認証のサポート <!--1029830-->
iOS 用ポータル サイト アプリでの証明書ベースの認証 (CBA) のサポートが追加されました。 CBA を使用するユーザーは、ユーザー名を入力した後、[Sign in with a certificate]\(証明書でサインインする\) リンクをタップします。 CBA は、Android および Windows 用のポータル サイト アプリで既にサポートされています。 詳細については、「[ポータル サイト アプリにサインインするには](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)」を参照してください。

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>登録の有無にかかわらず利用可能なアプリについて、登録を求められずにインストールできるようになりました。 <!-- 1334712 -->

Android ポータル サイト アプリでの登録の有無にかかわらず利用可能な業務用アプリについて、登録を求められずにインストールできます。

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Microsoft Intune で Windows AutoPilot Deployment プログラムをサポート<!-- 747617  -->
Microsoft Intune と Windows AutoPilot Deployment プログラムを使用して、IT が関与しなくても、ユーザーが自分の会社のデバイスをプロビジョニングできるようになりました。 OOBE (Out-of-Box Experience) をカスタマイズしたり、ユーザーのデバイスの Azure AD への参加および Intune への登録について、ユーザーをガイドすることができます。 Microsoft Intune と Windows AutoPilot を合わせて使用すると、オペレーティング システム イメージを展開、保持、管理する必要がなくなります。 詳細については、「[Windows AutoPilot Deployment プログラムを使用して Windows デバイスを登録する](https://docs.microsoft.com/intune/enrollment-autopilot)」を参照してください。

### <a name="quick-start-for-device-enrollment-----1425655---"></a>デバイス登録のクイック スタート<!-- 1425655 --> 
**デバイスの登録**でクイック スタートが利用できるようになり、プラットフォームの管理と登録プロセスの構成のための参考資料の表が提供されます。 各項目の簡単な説明と詳細な手順があるドキュメントへのリンクにより、簡単に使用開始するために役立つドキュメントを提供します。

### <a name="device-categorization----1427491---"></a>デバイスのカテゴリ化<!-- 1427491 -->
**[デバイス] > [概要]** ブレードの登録済みデバイス プラットフォームのグラフは、プラットフォーム (Android、iOS、macOS、Windows、Windows Mobile など) ごとにデバイスをまとめています。  他のオペレーティング システムを実行しているデバイスは "その他" にグループ化されています。  これには、Blackberry、NOKIA、およびその他のメーカー製のデバイスが含まれます。  

テナント内で影響を受けるデバイスを把握するには、**[管理] > [すべてのデバイス]** を選択してから、**[フィルター]** を使用して **[OS]** フィールドを制限します。

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium - 新しい Mobile Threat Defense パートナー   <!-- 954681 -->  
Microsoft Intune に統合された Mobile Threat Defense ソリューションである Zimperium によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

#### <a name="how-integration-with-intune-works"></a>Intune との統合のしくみ
リスクは、Zimperium を実行するデバイスから収集される製品利用統計情報に基づいて評価されます。 Intune デバイス コンプライアンス ポリシーで有効にした Zimperium リスク評価に基づき、EMS 条件付きアクセスのポリシーを構成できます。Intune デバイス コンプライアンス ポリシーは、検出された脅威に基づき、非準拠デバイスから企業リソースへのアクセスを許可したり、拒否したりするために利用できます。

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Windows 10 デバイス制限プロファイルの新しい設定 <!--- 978575, 1308849, -->  
Windows Defender SmartScreen カテゴリの Windows 10 デバイス制限プロファイルに新しい設定が追加されます。

Windows 10 デバイス制限のプロファイルの詳細については、「[Windows 10 以降のデバイスの制限設定]( device-restrictions-windows-10.md)」を参照してください。

### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Windows と Windows Mobile デバイスのリモート サポート <!-- 1070473 -->  
[TeamViewer](https://www.teamviewer.com) ソフトウェア (別売り) を使用して、Windows と Windows Mobile デバイスを実行するユーザーに Intune でリモート アシスタンスを提供できるようになりました。

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Windows Defender でデバイスをスキャンする <!-- 1280988  1280990   -->
管理された Windows 10 デバイス上で Windows Defender ウイルス対策を使って **クイック スキャン**、**フル スキャン**、**署名更新**を実行できるようになりました。 デバイスの概要ブレードから、デバイス上で実行するアクションを選びます。 コマンドがデバイスに送信される前に、アクションの確認を求められます。 

**クイック スキャン**: クイック スキャンでは、レジストリ キーや既知の Windows スタートアップ フォルダーなど、マルウェアが起動するように登録されている場所がスキャンされます。 クイック スキャンには、平均 5 分かかります。 クイック スキャンは、ファイルの開閉時やユーザーがフォルダーに移動したときにファイルをスキャンする **[Always-on real-time protection]\(リアルタイム保護を常に有効にする\)** 設定と組み合わせると、システムやカーネル内に存在する可能性があるマルウェアから保護するのに役立ちます。 完了すると、ユーザーのデバイスにスキャン結果が表示されます。 

**フル スキャン**: フル スキャンは、マルウェアの脅威が発生したデバイスで、徹底的なクリーンアップが必要な非アクティブなコンポーネントがあるかどうかを識別するために使用できます。また、オンデマンド スキャンを実行する場合に便利です。 フル スキャンは、実行に 1 時間かかる場合があります。 完了すると、ユーザーのデバイスにスキャン結果が表示されます。 

**署名更新**: 署名更新コマンドを使用すると、Windows Defender ウイルス対策のマルウェア定義と署名が更新されます。 マルウェア検出における Windows Defender ウイルス対策ソフトウェアの効果を確保するために役立ちます。 この機能は Windows 10 デバイス専用であり、デバイスのインターネット接続を一時中断します。 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>Intune Azure Portal の Intune 証明機関のページからの [有効]/[無効] ボタンの削除<!-- 1400455 -->
 Intune の証明書コネクタの設定で、余分な手順を排除しています。 現在は、証明書コネクタをダウンロードしてから、Intune コンソールでそれを有効にしています。 ただし、Intune コンソールでコネクタを無効にすると、コネクタは証明書の発行に進みます。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
10 月以降、Azure Portal の証明機関のページに、[有効]/[無効] ボタンが表示されなくなります。 コネクタ機能は変わりません。 証明書は、Intune に登録したデバイスに引き続き展開されます。 引き続き、証明書コネクタをダウンロードしてインストールすることができます。 証明書の発行を停止するには、証明書コネクタを無効にするのではなく、今すぐアンインストールします。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
現在、無効になっている証明書コネクタがある場合は、それをアンインストールする必要があります。

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Windows 10 Team デバイス制限プロファイルの新しい設定 <!--- 1308838 -->
このリリースでは、Surface Hub デバイスの制御に役立つように、Windows 10 Team デバイス制限プロファイルに多数の新しい設定が追加されています。

このプロファイルについて詳しくは、[Windows 10 Team デバイスの制限設定](device-restrictions-windows-10-teams.md)に関するページをご覧ください。

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Android デバイス ユーザーによるデバイスの日付と時刻の変更を防止する <!-- 1333292 -->
[Android カスタム デバイス ポリシー](custom-settings-android.md)を使用して、Android デバイス ユーザーがデバイスの日付や時刻を変更できないように設定できます。

この設定を行うには、./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange の設定 URI を使用して Android カスタム ポリシーを構成し、これを **TRUE** に設定して該当のグループに割り当てます。

### <a name="bitlocker-device-configuration----1397398---"></a>BitLocker デバイス構成 <!-- 1397398 -->
**[Windows 暗号化] > [Base Settings]\(基本設定\)** に、新たに **[他のディスクの暗号化に対する警告]** 設定が追加されました。この設定では、ユーザーのデバイス上で使われている可能性がある、他のディスクの暗号化についての[警告プロンプト](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption)を無効にできます。  警告プロンプトの利用には、デバイス上で BitLocker をセットアップする前にエンド ユーザーの同意が必要であり、エンド ユーザーによって承諾されるまで BitLocker のセットアップはブロックされます。  この新しい設定では、エンド ユーザーに対する警告が無効になります。


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>Intune テナントと同期されるようになった Volume Purchase Program for Business アプリ<!-- 800882 -->  
サードパーティの開発者は、iTunes Connect で指定されている承認された Volume Purchase Program (VPP) for Business メンバーにプライベートでアプリを配布できます。 VPP for Business のメンバーは、Volume Purchase Program App Store にサインインし、アプリを購入できます。

このリリースでは、エンド ユーザーが購入した VPP for Business アプリがそのユーザーの Intune テナントに同期されます。

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Apple の国別ストアを選択して VPP アプリを同期する <!-- 1332311 -->  
Volume Purchase Program (VPP) トークンをアップロードする際に、VPP 国別ストアを構成できます。 指定された VPP 国別ストアにある全ロケールに対応した VPP アプリが、Intune によって同期されます。

> [!NOTE]  
> 現在、Intune で同期されるのは、Intune テナントが作成された Intune ロケールに一致する VPP 国別ストアの VPP アプリのみです。


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Android for Work で仕事用プロファイルと個人プロファイルの間でのコピーおよび貼り付けを防ぐ <!-- 1098994 -->
このリリースでは、仕事用アプリと個人用アプリとの間でコピーおよび貼り付けができないように、Android for Work の仕事用プロファイルを構成できます。 この新しい設定は、**[仕事用プロファイルの設定]** の **[Android for Work]** プラットフォームの **[デバイスの制限]** プロファイルにあります。

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>特定地域の Apple App Store のみを対象とした iOS アプリを作成する <!-- 1281692 -->
Apple App Store 管理対象アプリの作成時に、国のロケールを指定できるようになります。

> [!Note]  
> 現在、Apple App Store の管理対象アプリは、米国のストアで販売されるものしか作成できません。

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>iOS VPP ユーザーとデバイスにライセンスされたアプリを更新する <!-- 1305564 -->  
Intune サービスを介して特定の iOS VPP トークンに対して購入されたすべてのアプリを更新するように、トークンを構成できるようになります。 アプリ ストア内の VPP アプリ更新プログラムが Intune によって検出され、デバイスのチェックイン時に自動的にデバイスにプッシュされます。

VPP トークンを設定して、自動更新を有効にする手順については、「[Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法] (/intune/vpp-apps-ios)」を参照してください。


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Intune データ ウェアハウスのデータ モデルに追加されたユーザー デバイス関連付けエンティティ コレクション <!-- 1187917 -->
ユーザーとデバイスのエンティティ コレクションを関連付けるユーザー デバイス関連付け情報を使って、レポートやデータの視覚エフェクトを作成できるようになりました。 このデータ モデルは、OData エンドポイントを使うか、カスタム クライアントを開発すると、[Data Warehouse Intune]\(データ ウェアハウス Intune\) ページから取得した Power BI ファイル (PBIX) を使ってアクセスできます。

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Windows 10 更新リングのポリシー準拠状況を確認する <!-- 1067886 -->
[ソフトウェア更新プログラム] > [更新プログラムごとのリングの展開の状態] から Windows 10 更新リングのポリシー レポートを確認できるようになります。 ポリシー レポートには、構成した更新リングの展開状態が表示されています。 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>古い iOS バージョンの iOS デバイス一覧が記載された新しいレポート<!-- 1352223 -->
**[ソフトウェア更新プログラム]** ワークスペースから **[Out-of-date iOS Devices]\(古い iOS デバイス\)** レポートが利用できます。 このレポートには、iOS の更新ポリシーが対象とする監視対象の iOS デバイスの一覧と利用可能な更新が表示されます。 デバイスごとに、デバイスが自動的に更新されない理由のステータスを確認できます。 

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>トラブルシューティングのアプリ保護ポリシー割り当てを確認する <!--  1475003 -->
今後のリリースでは、トラブルシューティング ブレードにある **[割り当て]** ボックスの一覧に、**[App protection policy]\(アプリの保護ポリシー\)** オプションが追加される予定です。 アプリの保護ポリシーを選んで、特定のユーザーに割り当てられているアプリ保護ポリシーを確認できるようになります。



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>ポータル サイトでのデバイスのセットアップ ワークフローの機能強化<!--1490692-->
Android 用のポータル サイト アプリでデバイスのセットアップ ワークフローを改良しました。 言語がよりわかりやすく、会社固有のものとなり、可能な範囲で画面をまとめるようにしました。 詳細については、「[アプリ UI の新機能](whats-new-app-ui.md#week-of-october-2-2017)」ページをご覧ください。

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Android デバイスでの連絡先へのアクセス要求に関するガイダンスの改善<!--1484985-->

Android 用ポータル サイト アプリは、連絡先アクセス許可を受け入れるようにエンド ユーザーに求めることがよくあります。 エンド ユーザーがこのアクセスを拒否すると、条件付きアクセス用のアクセス許可を付与するように通知するアプリ内通知が表示されるようになります。 

### <a name="secure-startup-remediation-for-android---1490712--"></a>Android でのセキュリティで保護された起動の修復<!--1490712-->

Android デバイスを持つエンド ユーザーは、ポータル サイト アプリのコンプライアンス非対応の理由をタップできるようになります。 可能であれば、問題を解決するのに適切な、設定アプリ内の場所がエンド ユーザーに直接表示されます。 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Android Oreo のポータル サイト アプリにエンド ユーザー向けプッシュ通知が追加<!--1475932-->

エンド ユーザーには、Android Oreo のポータル サイト アプリが Intune サービスからのポリシーの取得などのバックグラウンド タスクが実行されているときにそれを示す追加の通知が表示されます。 これにより、ポータル サイトがデバイス上でいつ管理タスクを実行しているかが、エンド ユーザーにとってより分かりやすくなります。 これは、Android Oreo のポータル サイト アプリの[ポータル サイト UI の最適化](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune)の一環です。 

Android Oreo で有効になっている新しい UI 要素がさらに最適化されています。  エンドユーザーには、ポータル サイトが Intune サービスからのポリシーの取得などのバックグラウンド タスクを実行しているときにそれを示す追加の通知が表示されます。  これにより、ポータル サイトがデバイスで管理タスクをいつ実行しているかがエンド ユーザーにわかりやすくなります。

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>仕事用プロファイルを使った Android 用ポータル サイト アプリの新しい動作 <!-- 1485783 -->

仕事用プロファイルがある Android for Work デバイスを登録すると、仕事用プロファイル内のポータル サイト アプリによって、そのデバイス上での管理タスクが実行されます。 

個人プロファイルで MAM 対応アプリを使っている場合を除き、Android 用ポータル サイト アプリを使用する機会がなくなります。 仕事用プロファイルのエクスペリエンスを向上させるために、Intune では仕事用プロファイルの登録が正常に完了した後、個人用ポータル サイト アプリが自動的に非表示になります。

Android 用ポータル サイト アプリは、[Play ストアでポータル サイト](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) を参照して **[Enable]\(有効化\)** をタップすると、個人プロファイルでいつでも有効にできます。

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Windows 8.1 および Windows Phone 8.1 のポータル サイトの維持モードへの移行 <!--1428681-->

2017 年 10 月より、Windows 8.1 および Windows Phone 8.1 用ポータル サイト アプリは、維持モードに移行されます。 つまり、当該アプリに加え、登録やコンプライアンスといった既存のシナリオは、これらのプラットフォームで引き続きサポートされます。 当該アプリは、Microsoft Store など、既存のリリース チャネル経由で引き続きダウンロード可能です。 

維持モードになると、当該アプリは、重要なセキュリティ更新プログラムのみを受信するようになります。 当該アプリの更新プログラムや機能が追加でリリースされることはありません。 新機能を使用するには、デバイスを Windows 10 や Windows 10 Mobile に更新することをお勧めします。 


### <a name="block-unsupported-samsung-knox-device-enrollment-----1490695---"></a>サポートされていない Samsung KNOX デバイスの登録をブロックする<!-- 1490695 -->

ポータル サイト アプリでは、サポートされている Samsung KNOX デバイスのみ、登録を試みます。 MDM の登録を妨げる KNOX ライセンス認証エラーの発生を回避するために、登録対象のデバイスが [Samsung によって発行されたデバイス一覧](https://www.samsungknox.com/knox-supported-devices/knox-workspace)に掲載されている場合にのみ、その登録が試行されます。 Samsung デバイスには、KNOX をサポートするモデル番号を持つものがある一方で、そうでないものもあります。 Samsung デバイスを購入および展開する前に、デバイスの再販業者に KNOX 対応の有無について確認してください。 検証済みのデバイスの完全な一覧については、「[Android and Samsung KNOX Standard policy settings (Android および Samsung KNOX Standard のポリシー設定)](/intune/supported-devices-browsers.md#intune-supported-web-browsers)」をご覧ください。

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>Android 4.3 以前のサポートの終了<!-- 1171126, 1326920 -->
Android 用の管理対象アプリとポータル サイト アプリで会社のリソースにアクセスするには、Android 4.4 以降を使用している必要があります。 12 月には、登録されているすべてのデバイスがインベントリから削除され、会社のリソースにアクセスできなくなります。 MDM を使わずにアプリの保護ポリシーを使用している場合、アプリは更新プログラムを受信できなくなり、時間の経過と共にエクスペリエンスの質が低下していきます。

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>登録されているデバイスで確認可能なデバイス情報のエンドユーザーへの通知<!--1165314-->
すべてのポータル サイト アプリの [デバイスの詳細] 画面に **[所有権の種類]** が追加されます。 これにより、ユーザーは、「[デバイスを登録した場合に会社が確認できる情報](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)」の記事から直接プライバシーの詳細を確認できるようになります。 これは近い将来、すべてのポータル サイト アプリに導入される予定です。 iOS 用については、[9 月](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017)に発表しました。

## <a name="september-2017"></a>2017 年 9 月

### <a name="intune-supports-ios-11---1428975--"></a>Intune が iOS 11 をサポート<!--1428975-->
Intune は iOS 11 をサポートします。 これについては、[Intune サポート ブログ](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/)ですでに発表しました。

### <a name="end-of-support-for-ios-80----1164477---"></a>iOS 8.0 のサポートの終了 <!-- 1164477 -->
iOS 用の管理対象アプリとポータル サイト アプリから会社のリソースにアクセスするには、iOS 9.0 以降を使用している必要があります。 この 9 月までに更新されないデバイスは、ポータル サイトまたはそれらのアプリにアクセスできなくなります。 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Windows 10 用ポータル サイト アプリに追加された更新アクション <!--1132468-->
Windows 10 向けのポータル サイト アプリでは、ユーザーがプルして更新するか、デスクトップで F5 キーを押して、アプリのデータを更新できます。

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>確認可能な iOS デバイス情報のエンドユーザーへの通知<!--739894-->

iOS 用ポータル サイト アプリの [デバイスの詳細] 画面に **[Ownership Type]\(所有権の種類\)** が追加されました。 これにより、ユーザーはこのページから直接、Intune のエンド ユーザー ドキュメントにあるプライバシーの詳細を参照できます。この情報は、[バージョン情報] 画面でも確認できます。

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>エンドユーザーの Android 用のポータル サイト アプリへのアクセスを登録なしで許可する<!---1169910--->

エンドユーザーは間もなく Android 用のポータル サイト アプリにアクセスするために、デバイスを登録しなくて済むようになります。 アプリの保護ポリシーを使用する組織のエンドユーザーが、ポータル サイト アプリを開いたときに、デバイスの登録を求めるプロンプトが表示されなくなります。 エンドユーザーはデバイスを登録することなく、ポータル サイトからアプリをインストールできるようにもなります。 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Android 用ポータル サイト アプリの文言をわかりやすいように変更 <!---1396349--->  

Android 用ポータル サイト アプリについて、エンドユーザーが登録しやすくなるよう、テキストを変更して登録プロセスを簡易化しました。 カスタム登録ドキュメントをお持ちの場合は、ドキュメントを更新して新しい画面を反映したいと思われるかもしれません。 サンプル画像は「[Intune とエンドユーザー アプリの UI の更新](whats-new-app-ui.md#week-of-september-11-2017)」のページにあります。

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Windows 情報保護許可ポリシーに追加された Windows 10 ポータル サイト アプリ <!-- 677129 -->

Windows 10 ポータル サイト アプリが更新され、Windows 情報保護 (WIP) がサポートされます。 WIP 許可ポリシーにアプリを追加できます。 この変更により、アプリを **[除外対象]** ボックスの一覧に追加する必要がなくなります。


## <a name="august-2017"></a>2017 年 8 月

### <a name="improvements-to-device-overview----1404453---"></a>デバイス機能強化の概要 <!-- 1404453 -->  
デバイス機能強化の概要に、登録済みデバイスが表示されるようになりましたが、Exchange ActiveSync で管理されるデバイスは除外されます。 Exchange ActiveSync デバイスには、登録済みデバイスと同じ管理オプションがありません。 Azure Portal の Intune で、登録済みデバイスの数とプラットフォーム別登録済みデバイスの数を表示するには、**[デバイス]**、**[概要]** の順に進みます。

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Intune で収集されるデバイス インベントリの機能強化
<!-- 961134, 1104426, 1281327, 1333543 --> このリリースでは、ユーザーが管理するデバイスで収集されるインベントリ情報が次のように改善されました。
 
-   Android devices デバイスの場合、各デバイスの最新パッチ レベルを示す列をデバイス インベントリに追加できるようになりました。 デバイスの一覧に **[セキュリティ パッチ レベル]** 列を追加し、これを表示します。
-   デバイス ビューにフィルターを適用するとき、登録日付でデバイスを絞り込めるようになりました。 たとえば、指定した日付の後に登録されたデバイスのみを表示できます。
-   **[Last Check-in Date]\(最終チェックイン日付\)** 項目で使用されるフィルターを改善しました。
-   デバイスの一覧で、会社所有デバイスの電話番号を表示できるようになりました。
さらに、フィルター ウィンドウを利用し、電話番号でデバイスを検索できます。
 
デバイス インベントリの詳細については、「[Intune デバイス インベントリを表示する方法](device-inventory.md)」を参照してください。

### <a name="conditional-access-support-for-macos-devices"></a>macOS デバイスの条件付きアクセスのサポート 
<!-- 720172 --> Mac デバイスを Intune に登録し、そのデバイス コンプライアンス ポリシーに準拠することを求める条件付きアクセス ポリシーを設定できるようになりました。 たとえば、ユーザーは macOS 用の Intune ポータル サイト アプリをダウンロードして、Mac デバイスを Intune に登録します。 Intune は、暗証番号 (PIN)、暗号化、OS バージョン、およびシステムの整合性などの要件にその Mac デバイスが準拠しているかどうかを評価します。

- macOS デバイスの条件付きアクセスのサポートについて詳しくは、[こちら](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)をご覧ください。

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>macOS 用ポータル サイト アプリはパブリック レビュー中です <!---1484796--->
macOS 用ポータル サイト アプリが Enterprise Mobility + Security の条件付きアクセス向けパブリック レビューの一部として利用可能になりました。 このリリースでは macOS 10.11 以降をサポートしています。 [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal) で入手します。 


### <a name="new-device-restriction-settings-for-windows-10"></a>Windows 10 の新しいデバイスの制限設定    
<!--1063965, 1308850  --> このリリースでは、次のカテゴリに [Windows 10 デバイス制限プロファイル](/intune/device-restrictions-windows-10)の新しい設定が追加されました。

-   Windows Defender SmartScreen
-   アプリ ストア

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Windows 10 エンドポイント保護デバイス プロファイルの BitLocker 設定の更新
<!--1459533 -->    
今回のリリースでは、Windows 10 エンドポイント保護デバイス プロファイルにおける BitLocker 設定の動作が次のように改善されました。
 
**[BitLocker OS ドライブの設定]** の **[互換性のない TPM チップでの BitLocker]** 設定で **[ブロック]** を選択すると、以前は、BitLocker が実際には許可されていました。 ブロックを選択すると BitLocker がブロックされるように修正されました。
**[BitLocker OS ドライブの設定]** の **[証明書ベースのデータ回復エージェント]** 設定で、証明書ベースのデータ回復エージェントを明示的にブロックできるようになりました。 ただし、既定では、エージェントが許可されます。
**[BitLocker 固定データ ドライブの設定]** の **[データ回復エージェント]** 設定で、データ回復エージェントを明示的にブロックできるようになりました。
詳しくは、「[Microsoft Intune での Windows 10 以降用の Endpoint Protection 設定](endpoint-protection-windows-10.md)」をご覧ください。


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Android ポータル サイト ユーザーおよびアプリ保護ポリシー ユーザーに対する新しいサインイン エクスペリエンス<!-- 621669 -->
エンドユーザーは、Android デバイスを登録しなくても、Android ポータル サイト アプリを使用して、今すぐにアプリを閲覧したり、デバイスを管理したり、IT 連絡先情報を確認したりできます。 また、エンドユーザーが既に Intune App Protection ポリシーによって保護されているアプリを使用しているときに、Android ポータル サイトを起動した場合、エンドユーザーに、デバイスの登録をするプロンプトが表示されなくなりました。

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Android ポータル サイト アプリのバッテリの最適化を切り替える新しい設定<!--1405990-->
Android ポータル サイト アプリの **[設定]** ページには、ポータル サイトと Microsoft Authenticator アプリのバッテリ最適化をユーザーが簡単にオフにできる新しい設定があります。 この設定で表示されるアプリ名は、どのアプリが職場アカウントを管理しているかによって異なります。 電子メールとデータを同期する職場アプリのパフォーマンスの向上には、バッテリの最適化をオフにすることをお勧めします。 

### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>OneNote for iOS の複数 ID のサポート      <!-- 1234281 -->
エンド ユーザーは Microsoft OneNote for iOS で複数のアカウントを利用できるようになりました (職場用と個人用)。 アプリ保護ポリシーを、個人のノートブックに適用することなく、職場のノートブックの企業データに適用できます。 たとえば、職場のノートブックでは情報を検索できるが、職場のノートブックから個人のノートブックに企業データをコピーして貼り付ける行為は禁止するポリシーを適用できます。
 
- Intune で [アプリ保護と複数の ID](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) をサポートするアプリについての詳細を参照してください。

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Samsung KNOX Standard デバイスでアプリを許可またはブロックするための新しい設定
<!-- 1305423 822899-->  
このリリースでは、次のアプリ一覧を指定できる[デバイスの制限設定](device-restrictions-android.md)が新規に追加されています。
 
- ユーザーがインストールを許可されているアプリ
- ユーザーが実行をブロックされているアプリ
- デバイスのユーザーに非表示となっているアプリ
 
アプリは、URL、パッケージ名、管理対象のアプリ一覧から指定できます。

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Intune からリンクされる新しい Azure AD のアプリ ベースの条件付きアクセス ポリシーの UI
<!-- 1016201 --> IT 管理者が、Azure AD のワークロードで新しい条件付きアクセス ポリシーの UI を使用して、アプリ ベースの条件付きポリシーを設定できるようになりました。 Azure Portal の Intune App Protection セクションにあるアプリ ベースの条件付きアクセス ポリシーは当面そのまま残り、サイド バイ サイドで強制されます。 また、Intune ワークロードから新しい条件付きアクセス ポリシー UI への便利なリンクもあります。

- Azure AD のアプリ ベースの条件付きアクセスについて詳しくは、[こちら](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)をご覧ください。



## <a name="july-2017"></a>2017 年 7 月

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Android および iOS デバイスの OS のバージョンによる登録制限 <!--- 1333256,  1245463 --->
オペレーティング システムのバージョン番号によって iOS と Android の登録を制限する機能が追加されました。 **[デバイスの種類の制限]** で、IT 管理者は、プラットフォーム構成を設定して、オペレーティング システムのバージョン番号の最小値から最大値までの間に登録を制限できるようになりました。 Android オペレーティング システムのバージョンは、Major.Minor.Build.Rev の形式で指定する必要があります (Minor、Build、Rev は任意)。 iOS のバージョンは、Major.Minor.Build の形式で指定する必要があります (Minor と Build は任意)。 [デバイス登録の制限](enrollment-restrictions-set.md)の詳細については、こちらを参照してください。

>[!NOTE]
>Apple の登録プログラムまたは Apple Configurator では、登録は制限されません。

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>個人所有の Android、iOS、および macOS デバイスの登録を制限する<!--- 1333272,  1333275, 1245709 --->
Intune では、会社デバイスの IMEI 番号のホワイトリストを作成して、個人用デバイスの登録を制限できます。 Intune では、デバイス シリアル番号を使って、この機能を iOS、Android、macOS に拡張しています。 Intune にデバイスのシリアル番号をアップロードし、それを企業所有として事前に宣言できます。 登録の制限を使用すると、個人所有のデバイス (BYOD) をブロックして、企業所有のデバイスのみの登録を許可することができます。 [デバイス登録の制限](enrollment-restrictions-set.md)の詳細については、こちらを参照してください。

シリアル番号をインポートするには、**[デバイスの登録]** > **[業務用デバイスの ID]** に進み、**[追加]** をクリックし、(ヘッダーはない、シリアル番号と IMEI 番号など詳細情報がある 2 つの列の) CSV ファイルをアップロードします。  個人所有のデバイスを制限するには、**[デバイスの登録]** > **[登録制限]** に移動します。 **[デバイスの種類の制限]** から **[既定]** を選択し、**[プラットフォーム構成]** を選択します。 個人所有の iOS、Android、および macOS デバイスを **[許可]** または **[ブロック]** できます。 


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>デバイスを Intune と強制同期する新しいデバイス アクション<!-- 711369 -->
このリリースでは、選択したデバイスの Intune への即座のチェックインを強制する新しいデバイス アクションが追加されています。 チェックインしたデバイスには、それに対して保留中のアクションまたはポリシーが即座に割り当てられます。  このアクションにより、次のスケジュールされたチェックインを待つことなく、割り当てられたポリシーの検証およびトラブルシューティングを即座に実行できるようになります。
詳細については、「[同期デバイス](device-sync.md)」を参照してください。

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>監督下の iOS デバイスに利用可能な最新のソフトウェア更新プログラムを強制的に自動インストールする<!-- 777100 -->
ソフトウェアの更新プログラム ワークスペースに用意された新しいポリシーを使用すると、監督下の iOS デバイスに利用可能な最新のソフトウェア更新プログラムを強制的に自動インストールできます。 詳細については、「[Configure iOS update policies](/intune/software-updates-ios)」 (iOS 更新プログラム ポリシーの構成) を参照してください。

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>チェック ポイント SandBlast Mobile - 新しい Mobile Threat Defense パートナー<!-- 954651, 1172027 -->
Microsoft Intune に統合された Mobile Threat Defense ソリューションであるチェックポイントの SandBlast Mobile によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

#### <a name="how-integration-with-intune-works"></a>Intune との統合のしくみ
リスクは、チェックポイントの SandBlast Mobile を実行するデバイスから収集される製品利用統計情報に基づいて評価されます。 Intune のデバイス コンプライアンス ポリシーにより有効になったチェックポイントの SandBlast Mobile のリスク評価に基づいて、EMS の条件付きアクセス ポリシーを構成できます。 検出された脅威に基づき、非準拠デバイスの企業リソースへのアクセスを許可またはブロックすることができます。


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>ビジネス向け Microsoft ストアで利用可能なアプリを展開する <!-- 748101 -->
このリリースでは、管理者はビジネス向け Microsoft ストアを使用可能として割り当てることができるようになりました。 使用可能として設定すると、エンドユーザーは、Microsoft ストアにリダイレクトされることなく、ポータル サイトのアプリまたは Web サイトからアプリをインストールできます。

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>ポータル Web サイトの UI の更新 <!--1313244 part 1-->
エンド ユーザー エクスペリエンスを向上させるために、[ポータル Web サイト](https://portal.manage.microsoft.com)の UI をいくつか更新しました。

- __アプリ タイルの機能強化__: アプリ アイコンが、アイコンの主調色に基づいて自動生成される背景で表示されます (アイコンを検出できた場合)。 適用できる場合は、アプリ タイルで以前表示されていた灰色の枠線が、この背景に代わります。

    ポータル サイト Web サイトでは、今後のリリースで可能なときには常に大きなアイコンで表示されます。 IT 管理者は、最小サイズが 120 x 120 ピクセルの高解像度アイコンを使用して、アプリを公開することをお勧めします。 

- __ナビゲーションの変更__: ナビゲーション バーの項目が、左上のハンバーガー メニューに移動されています。 カテゴリのページは削除されています。 ユーザーは参照中にカテゴリでコンテンツをフィルター処理できるようになりました。

- __おすすめアプリの更新__: サイトにおすすめとして選択したアプリを参照できる専用ページを追加し、ホームページのおすすめセクションでいくつかの UI の修正を行いました。

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>ポータル サイト Web サイトでの iBooks のサポート<!--1231841-->
ポータル サイトの Web サイトにユーザーが iBooks を参照してダウンロードできる専用ページを追加しました。 


### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>ヘルプ デスク トラブルシューティングの追加詳細 <!---  Applies to 1263399, 1326964, 1341642 --->
Intune では、トラブルシューティング ディスプレイを更新し、管理者やヘルプ デスク スタッフ向けの情報を追加しました。 グループのメンバーシップに基づいてユーザーの全割り当てをまとめた**割り当て**テーブルが表示されます。 この一覧の内容:
- モバイル アプリ
- Compliance ポリシー
- 構成プロファイル
 
また、**デバイス** テーブルに **[Azure AD 結合の種類]** 列と **[Azure AD 準拠]** 列が追加されました。 詳細については「[問題のトラブルシューティングの方法](help-desk-operators.md)」を参照してください。



### <a name="intune-data-warehouse-public-preview"></a>Intune データ ウェアハウス (パブリック プレビュー)
Intune データ ウェアハウスは、データを毎日サンプリングし、テナントの履歴ビューを提供します。 多くの分析ツールと互換性がある OData リンクである Power BI ファイル (PBIX) を使用するか、REST API と対話して、データにアクセスできます。 詳細については、「[Intune データ ウェアハウスを使用する](reports-nav-create-intune-reports.md)」を参照してください。


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Windows 10 のポータル サイト アプリで利用可能なライト モードとダーク モード<!---676547--->
エンドユーザーは Windows 10 のポータル サイト アプリのカラー モードをカスタマイズできるようになります。 ユーザーはポータル サイト アプリの [設定] セクションでこの変更をできるようになります。 変更はユーザーがアプリを再起動した後に反映されます。 Windows 10 のバージョン 1607 以降では、アプリ モードは既定でシステム設定になります。 Windows 10 のバージョン 1511 以前では、アプリ モードは既定でライト モードになります。

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>エンドユーザーは Windows 10 用のポータル サイト アプリでデバイス グループをタグ付けできる<!---807046-->
エンドユーザーは Windows 10 のポータル サイト アプリから直接タグ付けすることにより、デバイスの所属グループを選択できるようになりました。



## <a name="june-2017"></a>2017 年 6 月

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Intune 管理者のための新しいロール ベース管理アクセス   <!-- 1099990 -->  
Azure AD の条件付きアクセス ポリシーを表示、作成、変更、削除できる新しい条件付きアクセス管理者ロールが追加されます。 以前は、このアクセス許可を持つのは、グローバル管理者とセキュリティ管理者のみでした。 条件付きアクセス ポリシーにアクセスできるように、Intune 管理者にこのロールのアクセス許可が付与されます。


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>会社所有のデバイスにシリアル番号をタグ付けする <!-- 1215070 -->  
Intune では、iOS、macOS、Android のシリアル番号を会社デバイスの識別子としてアップロードできるようになりました。 この新機能では、シリアル番号を使用して個人用デバイスの登録をブロックすることはできません。登録中はシリアル番号が検証されないためです。 シリアル番号を使用して個人用デバイスをブロックする機能は、近いうちにリリースされる予定です。


### <a name="new-remote-actions-for-ios-devices----854689---"></a>iOS デバイスの新しいリモート操作 <!-- 854689 -->
このリリースでは Apple Classroom アプリを管理する新しいリモート デバイス アクションを共有の iPad デバイスに追加しました。

-   [[現在のユーザーのログアウト]](device-logout-user.md) - 選択した iOS デバイスの現在のユーザーをログアウトさせます。
-   [[ユーザーの削除]](device-remove-user.md) - iOS デバイスのローカル キャッシュから選択したユーザーを削除します。


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>iOS Classroom アプリによる共有 iPad のサポート <!-- 1044681 -->
このリリースでは、iOS Classroom アプリの管理サポートが拡張され、自分で管理している Apple ID を使って共有 iPad にログインする生徒を含めることができるようになっています。


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Intune の組み込みアプリの変更 <!-- 1332306 -->
以前は、Intune に簡単に割り当てができる組み込みのアプリが多数含まれていました。 お客様からのフィードバックに基づき、この一覧を削除しました。組み込みのアプリは今後表示されません。
ただし、組み込みのすべてのアプリが既に割り当てられている場合、そのアプリはアプリの一覧に引き続き表示されます。 これらのアプリの割り当ては必要に応じて続行することができます。
今後のリリースでは、Azure Portal から組み込みのアプリをより簡単に選択して割り当てる方法を追加する予定です。

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Office 365 アプリをより簡単にインストールする<!--- 1121362 --->
新しいタイプの **Office 365 ProPlus** アプリでは、最新バージョンの Windows 10 を実行する管理対象のデバイスに、Office 365 ProPlus 2016 アプリを簡単に割り当てることができます。 また、ライセンスを所有している場合、Microsoft Project や Microsoft Visio をインストールすることもできます。 必要なアプリはバンドルされ、Intune コンソールのアプリ一覧に 1 つのアプリとして表示されます。
詳細については、「[Windows 10 用の Office 365 アプリを追加する方法](apps-add-office365.md)」を参照してください。


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>ビジネス向け Microsoft ストアから入手したオフライン アプリのサポート <!--- 777044 --->
ビジネス向け Microsoft ストアから購入したオフライン アプリが Azure Portal に同期されます。 その後、これらのアプリをデバイス グループまたはユーザー グループに展開できます。 オフライン アプリはストアではなく Intune でインストールします。

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>Microsoft Teams が承認済みアプリのアプリ ベース CA 一覧の一部になった   <!-- 1257019 -->
iOS と Android 用の Microsoft Teams アプリが、Exchange と SharePoint Online のアプリ ベースの条件付きアクセス ポリシー向けの承認済みアプリの一部になりました。 Azure Portal の Intune アプリ保護ブレードで、現在アプリ ベースの条件付きアクセスを使っているすべてのテナントにアプリを構成できます。

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>管理対象ブラウザーとアプリ プロキシの統合<!-- 1287310 -->
Intune Managed Browser は Azure AD アプリケーション プロキシと統合できるようになり、ユーザーはリモートで作業しているときでも内部 Web サイトにアクセスできます。 ブラウザーのユーザーが通常と同じようにサイトの URL を単に入力すると、Managed Browser はアプリケーション プロキシの Web ゲートウェイを介して要求をルーティングします。 詳しくは、「[Managed Browser ポリシーを使用したインターネット アクセスの管理](app-configuration-managed-browser.md)」をご覧ください。

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Intune Managed Browser の新しいアプリ構成設定 <!-- 682951 -->
このリリースでは、iOS および Android 用の Intune Managed Browser アプリに構成が追加されました。 アプリ構成ポリシーを使って、ブラウザーの既定のホーム ページとブックマークを構成できます。
詳しくは、「[Managed Browser ポリシーを使用したインターネット アクセスの管理](app-configuration-managed-browser.md)」をご覧ください。

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Windows 10 用の BitLocker の設定  <!-- 951707 -->
新しい Intune デバイス プロファイルを使って、Windows 10 デバイス用の BitLocker の設定を構成できます。 たとえば、デバイスの暗号化を要求でき、BitLocker が有効になっているときに適用される設定をさらに構成することもできます。
詳しくは、「[Microsoft Intune での Windows 10 以降用の Endpoint Protection 設定](endpoint-protection-windows-10.md)」をご覧ください。

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Windows 10 デバイス制限プロファイルの新しい設定 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
このリリースでは、次のカテゴリに Windows 10 デバイス制限プロファイルの新しい設定が追加されました。

-  Windows Defender
-  携帯ネットワークと接続性
-  ロック画面
-  プライバシー
-  検索
-  Windows スポットライト
-  Microsoft Edge ブラウザー

Windows 10 の設定について詳しくは、「[Microsoft Intune での Windows 10 以降のデバイスの制限設定](device-restrictions-windows-10.md)」をご覧ください。


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>Android 用ポータル サイト アプリのアプリ保護ポリシーの新しいエンド ユーザー エクスペリエンス <!--1305217-->
ユーザーのフィードバックに基づいて、Android 用ポータル サイト アプリに **[会社のコンテンツにアクセスする]** ボタンが表示されるようになりました。 目的は、エンド ユーザーがアプリの保護ポリシーをサポートするアプリ、Intune モバイル アプリケーション管理の機能にのみアクセスする必要があるときに、不要な登録プロセスを経由せずに済むようにすることです。 これらの変更については、「[アプリ UI の新機能](whats-new-app-ui.md)」ページをご覧ください。

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>ポータル サイトを簡単に削除できるアクション メニューの追加<!--1164569-->
Android 用ポータル サイト アプリでは、ユーザーからのフィードバックに基づき、デバイスからポータル サイトの削除を開始できる新しいアクション メニューが追加されました。 この操作は、ユーザーがデバイスからアプリを削除できるように、Intune の管理からデバイスを削除します。 これらの変更については、[Android エンド ユーザー向けドキュメント](/intune-user-help/unenroll-your-device-from-intune-android)の[アプリ UI の新機能](whats-new-app-ui.md)に関するページで確認できます。

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Windows 10 Creators Update とアプリを同期する機能の強化 <!--676505-->
Windows 10 用ポータル サイト アプリでは、Windows 10 Creators Update (バージョン 1703) がインストールされているデバイスのアプリ インストール要求の同期が自動的に開始されるようになりました。 "同期保留中" 状態中、アプリ インストールが止まる問題を減らします。 また、ユーザーは、アプリ内からの同期を手動で開始することができます。 これらの変更については、「[アプリ UI の新機能](whats-new-app-ui.md)」ページをご覧ください。

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Windows 10 ポータル サイトの新しいガイド機能 <!---1058938--->
Windows 10 用のポータル サイト アプリで、特定または登録されていないデバイス向けのガイド付き Intune チュートリアルを利用できるようになります。 ユーザーは新たな段階的手順に従って、Azure Active Directory (条件付きアクセス機能のために必要) と MDM (デバイス管理機能のために必要) に登録できます。 このガイドには、ポータル サイトのホーム ページからアクセスできます。 ユーザーは、これらの登録を完了していない場合でも引き続きアプリを使用できますが、機能が制限されます。

この更新は、Windows 10 Anniversary Update (ビルド 1607) 以降を実行しているデバイスのみで表示されます。 これらの変更については、「[アプリ UI の新機能](whats-new-app-ui.md)」ページをご覧ください。


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Microsoft Intune 管理コンソールと条件付きアクセス管理コンソールの一般提供開始
Azure Portal の新しい Intune 管理コンソールと、条件付きアクセス管理コンソールの一般提供開始が発表されました。 Azure Portal で Intune を利用することで、Intune MAM および MDM のすべての機能を統合された 1 つの管理者エクスペリエンスで管理し、Azure AD のグループとターゲットを利用できるようになりました。 Azure の条件付きアクセスにより、Azure AD と Intune の豊富な機能が一元化されたコンソールに統合されます。 また管理者エクスペリエンスから Azure プラットフォームに移動して、最新のブラウザーを使用できます。

Intune は、**[プレビュー]** ラベルが外れた状態で Azure Portal (portal.azure.com) に表示されるようになりました。

メッセージ センターの一連のメッセージのうち、グループを移行できるようにお客様の対応をお願いするメッセージを受信された場合を除き、現時点で既存のお客様にしていただくことはありません。 こちらのバグにより、移行に時間がかかることをお知らせする通知がメッセージ センターから送信されている場合もあります。 Microsoft では、影響を受けたユーザーを移行する作業に引き続き取り組んでまいります。

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>iOS 用ポータル サイト アプリのアプリ タイルを改善
ポータル サイトに設定したブランド カラーが反映されるよう、ホーム ページのアプリ タイルのデザインを一新しました。 詳細については、[アプリ UI の新機能](whats-new-app-ui.md)に関するページをご覧ください。

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>iOS 用ポータル サイト アプリでアカウント選択の提供を開始
iOS デバイスのユーザーが、職場または学校アカウントを使用して別の Microsoft アプリにサインインしているときに、ポータル サイトにサインインしようとすると、新しいアカウントの選択が表示される場合があります。 詳細については、[アプリ UI の新機能](whats-new-app-ui.md)に関するページをご覧ください。

## <a name="may-2017"></a>2017 年 5 月

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>マネージド デバイスの登録を解除せず、MDM 機関を変更する <!--1103950-->
Microsoft サポートに問い合わせずに、また、既存のマネージド デバイスの登録解除と再登録を行わずに MDM 機関を変更できるようになりました。 Configuration Manager コンソールで、[Configuration Manager に設定]\(ハイブリッド\) から [Microsoft Intune]\(スタンドアロン\) に、またはその逆に [MDM 機関を変更](/sccm/mdm/deploy-use/change-mdm-authority)できます。


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Samsung KNOX スタートアップ PIN の通知機能の強化 <!--1087143-->
暗号化に対応するために、エンド ユーザーが Samsung KNOX デバイスにスタートアップ PIN を設定する必要がある場合、エンド ユーザーに表示される通知をタップすると、設定アプリ内の設定場所に移動します。  以前は、エンド ユーザーは通知からパスワード変更画面に進むことができました。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>共有 iPad での Apple School Manager (ASM) のサポート <!-- 748864, 770395-->

Intune では、Apple Device Enrollment Program の代わりに Apple School Manager (ASM) を使用できるようになりました。すぐに iOS デバイスを登録できます。 共有 iPad で Classroom アプリを使用するには ASM オンボードが必要です。これは、Microsoft School Data Sync (SDS) 経由で ASM から Azure Active Directory へのデータ同期を有効にする際にも必要です。 詳細については、「[Enable iOS device enrollment with Apple School Manager (Apple School Manager での iOS デバイス登録の有効化)](apple-school-manager-set-up-ios.md)」をご覧ください。

> [!NOTE]
> 共有 iPad で Classroom アプリを使用できるように構成するには、Azure に iOS 向けの Education の構成が必要ですが、現時点では提供されていません。  この機能は、近日中に追加される予定です。

### <a name="device-management"></a>デバイス管理

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>TeamViewer を利用して Android デバイスにリモート アシスタンスを提供<!-- 675418 -->

Intune では、別売りの [TeamViewer](https://www.teamviewer.com) ソフトウェアを利用して、Android デバイスを使用するユーザーにリモート アシスタンスを提供できるようになりました。 詳細については、「[Provide remote assistance for Intune managed Android devices (Intune 管理対象の Android デバイスにリモート アシスタンスを提供)](device-profile-android-teamviewer.md)」をご覧ください。

### <a name="app-management"></a>アプリ管理

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>MAM の新しいアプリ保護ポリシー条件 <!-- 679864 -->

登録ユーザーなしで、次のポリシーを強制する MAM の要件を設定できるようになりました。

- アプリケーションの最小バージョン
- オペレーティング システムの最小バージョン
- 対象アプリケーションの最小 Intune APP SDK バージョン (iOS のみ)

この機能は、Android と iOS の両方で使うことができます。 Intune は、OS プラットフォーム バージョン、アプリケーション バージョン、Intune APP SDK の最小バージョン強制に対応しています。 iOS の場合、SDK が統合されているアプリケーションでも SDK レベルで最小バージョン強制を設定できます。 アプリ保護ポリシーの最小要件が上述の 3 つの異なるレベルで満たされていない場合、ユーザーは対象アプリケーションにアクセスできません。 この時点で、ユーザーはアカウントを削除するか (複数 ID アプリケーションの場合)、アプリケーションを閉じるか、OS またはアプリケーションのバージョンを更新できます。

また、OS またはアプリケーションのアップグレードを推奨するブロック不可の通知を表示するように追加設定することもできます。 この通知は閉じて、アプリケーションを普段どおり使用できます。

詳細については、「[iOS アプリ保護ポリシー設定](app-protection-policy-settings-ios.md)」と「[Android アプリ保護ポリシー設定](app-protection-policy-settings-android.md)」をご覧ください。

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Android for Work 用のアプリ構成の設定<!-- 621621 -->
ストアの一部の Android アプリは管理対象の構成オプションをサポートしているため、IT 管理者は作業プロファイルでアプリの実行方法を制御できます。 Intune では、Azure Portal からアプリがサポートする構成を表示し、構成デザイナーまたは JSON エディターを使用してこれらの構成を設定できるようになりました。 詳細については、[Android for Work 用のアプリ構成の使用](app-configuration-policies-use-android.md)に関するページをご覧ください。

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>登録なしで利用できる MAM の新しいアプリ構成機能<!-- 677969 -->
登録チャネルがなくても MAM からアプリ構成ポリシーを作成できるようになりました。 これは、モバイル デバイス管理 (MDM) のアプリ構成で使用できるアプリ構成ポリシーと同等の機能です。 登録せずに MAM を使用してアプリを構成する例については、「[Manage Internet access using Managed browser policies with Microsoft Intune (Microsoft Intune と Managed Browser のポリシーを使用したインターネット アクセスの管理)](app-configuration-managed-browser.md)」をご覧ください。

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Managed Browser で許可される URL とブロックされる URL 一覧の構成<!-- 682960 -->
Azure Portal のアプリ構成設定を使用して、Intune Managed Browser で許可またはブロックされるドメインおよび URL の一覧を構成できるようになりました。 これらの設定は、マネージド デバイスで使用されているか、アンマネージド デバイスで使用されているかに関係なく構成できます。 詳細については、「[Manage Internet access using Managed browser policies with Microsoft Intune (Microsoft Intune と Managed Browser のポリシーを使用したインターネット アクセスの管理)](app-configuration-managed-browser.md)」をご覧ください。

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>アプリ保護ポリシー ヘルプデスクのビュー<!-- 1069473 -->
IT ヘルプデスクのユーザーは、[トラブルシューティング] ブレードで、ユーザー ライセンスの状態と、ユーザーに割り当てられているアプリのアプリ保護ポリシーの状態を確認できるようになりました。 詳細については、[トラブルシューティング](./help-desk-operators.md)に関するページをご覧ください。

### <a name="device-configuration"></a>デバイス構成

#### <a name="control-website-visits-on-ios-devices----723832---"></a>iOS デバイスの Web サイト アクセスの制御<!-- 723832 -->
iOS デバイスのユーザーがアクセスできる Web サイトを次の 2 つの方法を使って制御できるようになりました。

- Apple の組み込み Web コンテンツ フィルターを使って、許可される URL またはブロックされる URL を追加します。

- Safari ブラウザーによるアクセスを許可する Web サイトを指定します。 指定した各サイトについて、Safari にブックマークが作成されます。

詳細については、「[Web content filter settings for iOS devices (iOS デバイス用の Web コンテンツ フィルター設定)](web-content-filter-settings-ios.md)」をご覧ください。

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Android for Work アプリのデバイス アクセス許可の事前構成 <!-- 621614 -->
Android for Work デバイスの作業プロファイルに展開したアプリの場合、個々のアプリのアクセス許可状態を構成できるようになりました。  既定では、場所やデバイス カメラへのアクセスなど、デバイスのアクセス許可を必要とする Android アプリはアクセス許可の承諾または拒否をユーザーに求めます。  たとえば、アプリでデバイスのマイクが使用される場合、そのマイクを使用するアクセス許可をアプリに与えるようにエンド ユーザーに求められます。 この機能を利用すると、エンド ユーザーの代わりにアクセス許可を定義できます。  アクセス許可は、a) ユーザーに通知することなく自動的に拒否する、b) ユーザーに通知することなく自動的に承諾する、c) 承諾または拒否をユーザーに求めるのいずれかに構成できます。 詳細については、「[Microsoft Intune での Android for Work デバイスの制限設定](device-restrictions-android-for-work.md)」をご覧ください。

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Android for Work デバイスのアプリ固有 PIN を定義する <!-- 728976, 1102534 -->
管理者は、Android for Work デバイスとして管理されている Android 7.0 以上のデバイスの作業プロファイルで、作業プロファイルのアプリにのみ適用されるパスコード ポリシーを定義できます。  次のオプションがあります。

- デバイス全体のパスコード ポリシーだけを定義する - これは、デバイス全体のロックを解除するためにユーザーが使用しなければならないパスコードです。
- 作業プロファイルのパスコード ポリシーだけを定義する - 作業プロファイルのアプリを起動するたびに、ユーザーにパスコードの入力が求められます。
- デバイスと作業プロファイル ポリシーの両方を定義する - IT 管理者はデバイスのパスコード ポリシーと作業プロファイルのパスコード ポリシーをいずれも異なる強度で定義できます。たとえば、デバイスのロック解除に 4 桁の PIN を要求し、作業アプリの起動に 6 桁の PIN を要求します。

詳細については、「[Microsoft Intune での Android for Work デバイスの制限設定](device-restrictions-android-for-work.md)」をご覧ください。

> [!NOTE]
> この機能は Android 7.0 以降でのみ利用できます。  既定では、エンド ユーザーは別々に定義された 2 つの PIN を利用できます。あるいは、定義された 2 つの PIN のうちの強いほうを選択できます。

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Windows 10 デバイスの新しい設定<!-- 978585 -->
Microsoft は、無線ディスプレイ、デバイス検出、タスク切り替え、SIM カード エラー メッセージなどの機能を制御する新しい [Windows デバイス制限設定](device-restrictions-windows-10.md)を追加しています。

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>証明書の構成の更新<!-- 918991 and 823198 -->
SCEP 証明書プロファイルを作成するときに、<strong>[サブジェクト名の形式]</strong>で、<strong>[カスタム]</strong> オプションを iOS、Android、および Windows デバイスでご利用いただけます。 今回の更新までは、<strong>[カスタム]</strong> フィールドを使用できるのは iOS デバイスだけでした。 詳細については、「[SCEP 証明書プロファイルを作成する](certificates-scep-configure.md#create-a-scep-certificate-profile)」をご覧ください。

PKCS 証明書プロファイルを作成するときに、**[サブジェクトの別名]** で、**[Custom Azure AD attribute]\(Azure AD のカスタム属性\)** をご使用いただけます。 **[Custom Azure AD attribute]\(Azure AD のカスタム属性\)** を選択すると、**[部門]** オプションが使用できます。 詳細については、「[PKCS 証明書プロファイルを作成する](certficates-pfx-configure.md#create-a-pkcs-certificate-profile)」をご覧ください。

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Android デバイスがキオスク モードのときに実行できる複数アプリの構成<!-- 662059 -->
これまでは、Android デバイスがキオスク モードのときに実行できるアプリは 1 つしか設定できませんでした。 アプリ ID やストアの URL を使用するか、すでに管理している Android アプリを選択して、複数のアプリを設定できるようになりました。 詳細については、[キオスク モードの設定](device-restrictions-android.md#kiosk)に関するページをご覧ください。



## <a name="april-2017"></a>2017 年 4 月

### <a name="support-for-managing-the-apple-classroom-app"></a>Apple Classroom アプリの管理のサポート
iPad デバイスで iOS Classroom アプリを管理できるようになりました。 クラスと学生の正しいデータで教師の iPad に Classroom アプリをセットアップした後、アプリを使って制御できるように、クラスに登録されている学生の iPad を構成します。
詳しくは、「[Configure iOS education settings](education-settings-configure-ios.md)」 (iOS の教育設定を構成する) をご覧ください。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Android アプリ向けの管理対象構成オプションのサポート<!-- 621621 -->
管理対象構成オプションをサポートする Play ストアの Android アプリを、Intune で構成できるようになりました。  この機能は、アプリによってサポートされる構成値の一覧を表示できるようにし、値を構成できるガイド付きの使いやすい UI を提供します。

### <a name="new-android-policy-for-complex-pins----722069---"></a>複雑な暗証番号 (PIN) に対する新しい Android ポリシー <!-- 722069 -->
Android 5.0 以降を搭載しているデバイスの Android デバイス プロファイルに、数値複素数タイプの必須[パスワード](device-restrictions-android.md#password)を設定できるようになりました。  反復する値や連続する値 (1111 や 1234 など) を含む暗証番号 (PIN) をデバイスのユーザーが作成しないようにするには、この設定を使います。

### <a name="additional-support-for-android-for-work-devices"></a>Android for Work デバイスの追加サポート
- **パスワードと仕事用プロファイルの設定を管理する** <!-- 612808 -->

  この新しい Android for Work デバイス制限ポリシーにより、管理対象の Android for Work デバイスで、パスワードと仕事用プロファイルの設定を管理できるようになりました。

- **仕事用プロファイルと個人プロファイル間でのデータ共有を許可する** <!-- 1045102 -->

この Android for Work デバイス制限プロファイルには、仕事用プロファイルと個人用プロファイルでのデータ共有の設定ができる新しいオプションが用意されました。

- **仕事用プロファイルと個人プロファイルの間でのコピーと貼り付けを制限する** <!-- 1046094 -->

  Android for Work デバイス用の新しいカスタム デバイス プロファイルでは、仕事用アプリと個人用アプリの間でのコピーと貼り付け操作を許可するかどうかを制限できます。

詳細については、[Android for Work 用のデバイスの制限](device-restrictions-android-for-work.md)に関するページをご覧ください。

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>iOS デバイスと Android デバイスに LOB アプリを割り当てる <!-- 1057568 -->
[iOS](lob-apps-ios.md) 用 (.ipa ファイル) と [Android](lob-apps-android.md) 用 (.apk ファイル) の基幹業務 (LOB) アプリを、ユーザーまたはデバイスに割り当てることができるようになりました。


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>iOS 用の新しいデバイス ポリシー <!-- 723774, 723815, 723826, 723830 -->
- **ホーム画面のアプリ** - [iOS デバイスのホーム画面](home-screen-settings-ios.md)に表示されるアプリを制御します。 このポリシーはホーム画面のレイアウトを変更しますが、アプリの展開は行いません。

- **AirPrint デバイスへの接続** - iOS デバイスのエンド ユーザーが接続できる [AirPrint デバイス](air-print-settings-ios-macos.md) (ネットワーク プリンター) を制御します。

- **AirPlay デバイスへの接続** - iOS デバイスのエンド ユーザーが接続できる [AirPlay デバイス](airplay-settings-ios.md) (Apple TV など) を制御します。

- **ロック画面のカスタム メッセージ** - ユーザーの iOS デバイスのロック画面に表示されるカスタム メッセージを構成して、既定のメッセージと置き換えます。 詳しくは、「[iOS デバイスで紛失モードをアクティブ化する](device-lost-mode.md)」を参照してください。

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>iOS アプリのプッシュ通知を制限する <!-- 723767 -->
Intune のデバイス制限プロファイルでは、iOS デバイスに対して次の[通知設定](app-notification-settings-ios.md)を構成できるようになりました。

- 指定したアプリの通知を完全に有効または無効にします。
- 指定したアプリの通知センターでの通知を有効または無効にします。
- アラートの種類を、**なし**、**バナー**、または**モーダル アラート**に指定します。
- このアプリに対してバッジを許可するかどうかを指定します。
- 通知サウンドを許可するかどうかを指定します。

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>単一アプリ モードで自律的に実行するように iOS アプリを構成する<!-- 737837 -->
Intune のデバイス プロファイルを使って、[自律的シングル App モード](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only)で指定したアプリを実行するように iOS デバイスを構成できるようになりました。 このモードを構成した場合、指定したアプリが実行されると、デバイスはそのアプリだけを実行できるようにロックされます。 たとえば、ユーザーがデバイスでテストを受けられるようにアプリを構成するような場合です。 アプリのアクションが完了した場合、または管理者がこのポリシーを削除した場合、デバイスは通常の状態に戻ります。

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>iOS デバイスでメールと Web ブラウザー用の信頼されたドメインを構成する <!-- 723765 -->
iOS デバイス制限プロファイルから、次の[ドメイン設定](device-restrictions-ios.md#domains)を構成できるようになりました。

- **[マークされていないメール ドメイン]** - ユーザーが送信または受信するメールのうち、ここで指定したドメインと一致しないものは、信頼されていないメールとしてマークされます。

- 
  **[管理された Web ドメイン]** - ここで指定した URL からダウンロードされたドキュメントは、管理されているものと見なされます (Safari のみ)。  

- **[Safari パスワードの自動入力ドメイン]** - ユーザーは、ここで指定したパターンに一致する URL からのパスワードのみを Safari に保存できます。 この設定を使うには、デバイスが監視モードであり、複数ユーザー用に構成されていない必要があります。 (iOS 9.3 以降)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>iOS ポータル サイトで使用できる VPP アプリ <!-- 748782 -->
**利用可能な**インストールとして、iOS ボリューム購入 (VPP) アプリをエンド ユーザーに割り当てられるようになりました。 エンド ユーザーがアプリをインストールするには、Apple ストア アカウントが必要です。

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Apple VPP ストアから電子ブックを同期する <!-- 800878 -->
Intune と、Apple ボリューム購入プログラム ストアから購入した[本を同期](vpp-apps-ios.md)し、ユーザーに割り当てることができるようになりました。

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Samsung KNOX Standard デバイスのマルチ ユーザー管理 <!-- 971988 -->
Samsung KNOX Standard を実行するデバイスが、Intune による[マルチ ユーザー管理](android-enroll.md)のサポート対象になりました。 つまり、エンド ユーザーは Azure Active Directory の資格情報を使ってデバイスのサインインとサインアウトを行うことができ、デバイスは使用中かどうかに関わらず一元管理されます。  サインインしたエンド ユーザーはアプリにアクセスできます。ポリシーがあれば、それが適用されます。 ユーザーがサインアウトすると、すべてのアプリ データがクリアされます。

### <a name="additional-windows-device-restriction-settings----818566---"></a>追加の Windows デバイス制限設定 <!-- 818566 -->
追加の Microsoft Edge ブラウザー サポート、デバイス ロック画面のカスタマイズ、スタート メニューのカスタマイズ、Windows スポットライト検索セットの壁紙、プロキシ設定など、追加の [Windows デバイス制限設定](device-restrictions-windows-10.md)のサポートが追加されました。

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Windows 10 Creators Update のマルチユーザー サポート <!-- 822547 -->
Windows 10 Creators Update を実行し Azure Active Directory ドメインに参加しているデバイスの[マルチユーザー管理](windows-enroll.md)のサポートが追加されました。 つまり、異なる標準ユーザーが Azure AD 資格情報でデバイスにログインすると、ユーザー名に割り当てられているすべてのアプリとポリシーを受け取ります。 現時点では、アプリのインストールのようなセルフサービスのシナリオにポータル サイトは使用できません。

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 PC の Fresh Start <!-- 1004830 -->
Windows 10 PC で、新しい [Fresh Start デバイス アクション](device-fresh-start.md)が使用できるようになりました。  このアクションを発行すると、PC にインストールされたすべてのアプリが削除され、PC は Windows の最新バージョンに自動的に更新されます。 この機能は、新しい PC に付属することの多い事前インストール済み OEM アプリを削除するのに使うことができます。 このデバイス アクションを発行するときにユーザー データを保持するかどうかを構成できます。

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Windows 10 の追加アップグレード パス <!-- 903672 -->
以下のエディションの Windows 10 にも、[エディション アップグレード ポリシーの作成によりデバイスをアップグレード](edition-upgrade-configure-windows-10.md)できるようになりました。

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Windows 10 デバイスを一括登録する <!-- 747607 -->
Windows 構成デザイナー (WCD) で Azure Active Directory と Intune に Windows 10 Creators Update を実行する多数のデバイスを参加させることができるようになりました。 Azure AD テナントの [一括 MDM 登録](windows-bulk-enroll.md) を有効にするには、Windows 構成デザイナーを使用して Azure AD テナントにデバイスを参加させるプロビジョニング パッケージを作成し、一括登録と管理を行う会社所有のデバイスにパッケージを適用します。 パッケージがデバイスに適用されると、デバイスは Azure AD に参加し、Intune に登録され、Azure AD ユーザーがログオンできる状態になります。  Azure AD ユーザーはこれらのデバイス上の標準ユーザーであり、割り当て済みのポリシーと必須アプリを受け取ります。 現在のところ、セルフ サービスとポータル サイトのシナリオはサポートされていません。

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>暗証番号 (PIN) および管理対象記憶域の場所に対する新しい MAM 設定<!-- 581122, 736644 -->
モバイル アプリケーション管理 (MAM) シナリオに役立つ 2 つの新しいアプリ設定が使用できるようになりました。

- 
  **[Disable app PIN when device PIN is managed (デバイスの PIN が管理されるときはアプリの PIN を無効にする)]** - 登録されたデバイスにデバイス暗証番号 (PIN) が存在するかどうかを検出し、存在する場合は、アプリ保護ポリシーによってトリガーされるアプリ PIN をバイパスします。 この設定を使うと、登録されたデバイスで MAM が有効なアプリケーションを開くユーザーに対して表示される PIN 要求の回数を減らすことができます。 この機能は、Android と iOS の両方で使うことができます。

- **[会社のデータを保存できるストレージ サービスの選択]** - 会社のデータを保存する記憶域の場所を指定できます。 ユーザーは選択したストレージ ロケーション サービスに保存できます。つまり、表示されていない他のすべてのストレージ ロケーション サービスはブロックされます。

  サポートされるストレージ ロケーション サービスの一覧は次のとおりです。

  - OneDrive
  - Business SharePoint Online
  - ローカル ストレージ

### <a name="help-desk-troubleshooting-portal----907448---"></a>ヘルプ デスクのトラブルシューティング ポータル<!-- 907448 -->
新しい[トラブルシューティング ポータル](help-desk-operators.md)を使用すると、ヘルプ デスクと Intune 管理者は、ユーザーと彼らのデバイスを表示して、Intune の技術的な問題を解決するタスクを実行できます。

## <a name="march-2017"></a>2017 年 3 月

### <a name="support-for-ios-lost-mode---431695--"></a>iOS 紛失モードのサポート<!--431695-->
iOS 9.3 以降のデバイスについて、Intune で**紛失モード**のサポートが追加されました。 デバイスをロックダウンしてすべての使用を回避し、デバイスのロック画面のメッセージおよび連絡先の電話番号を表示できるようになりました。

エンドユーザーは、管理者が紛失モードを無効にするまで、デバイスのロックを解除することはできません。 紛失モードを有効にした場合、**デバイスを探索する**アクションを使用して、Intune コンソールでマップ上にデバイスの地理的な場所を表示することができます。

会社所有の iOS デバイスを DEP で登録し、監視モードに設定している必要があります。

詳細については、「[Microsoft Intune デバイスの管理とは](device-management.md)」を参照してください。

### <a name="improvements-to-device-actions-report---677150--"></a>Device Actions レポートの機能強化 <!--677150-->
Device Actions レポートの機能が強化され、パフォーマンスが向上しました。 さらに、レポートを状態別にフィルター処理できるようになりました。 たとえば、レポートをフィルター処理して、完了したデバイス アクションのみを表示できます。

### <a name="custom-app-categories---748805--"></a>カスタム アプリのカテゴリ <!--748805-->
Intune に追加するアプリのカテゴリを作成、編集、および割り当てることができるようになりました。 現時点では、カテゴリは英語でのみ指定できます。
[Intune にアプリを追加する方法](apps-add.md)に関するページを参照してください。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>登録していないデバイスを使用しているユーザーに LOB アプリを割り当てる <!--748823-->
デバイスが Intune に登録されているかどうかに関係なく、基幹業務アプリをストアからユーザーに割り当てられるようになりました。 ユーザーのデバイスが Intune に登録されていない場合は、ポータル サイト アプリではなく、ポータル Web サイトに移動してインストールする必要があります。

### <a name="new-compliance-reports---846671--"></a>新しいコンプライアンス レポート <!--846671-->
コンプライアンス レポートにより、会社内のコンプライアンスの状況を表示して、社内のユーザーがコンプライアンス関連の問題に直面したときに迅速にトラブルシューティングできるようになりました。 次の情報を表示できます。

- デバイスの総合的なコンプライアンスの状態
- 設定別のコンプライアンスの状態
- ポリシー別のコンプライアンスの状態

これらのレポートを使用して個々のデバイスをドリルダウンし、そのデバイスに影響を与えている特定の設定およびポリシーを確認することもできます。

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->
Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure Portal の Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューは Azure Portal のリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントでプレビューにアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。


## <a name="february-2017"></a>2017 年 2 月

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>モバイル デバイス登録を制限する機能 <!--747600, 795782-->
Intune では、登録を許可されるモバイル デバイス プラットフォームを制御する新しい登録制限が追加されています。 Intune では、モバイル デバイス プラットフォームが iOS、macOS、Android、Windows、Windows Mobile に分かれています。

* モバイル デバイスの登録を制限しても、PC クライアントの登録は制限されません。  
* iOS と Android のみに、個人所有デバイスの登録をブロックする 1 つの追加オプションがあります。

[この記事](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices)で説明されているように、IT 管理者が明示的に会社所有と指定しない限り、Intune はすべての新しいデバイスを個人所有としてマークします。

### <a name="view-all-actions-on-managed-devices---677150--"></a>マネージド デバイスのすべての操作を表示 <!--677150-->
新しい__デバイス操作__レポートには、デバイスでの出荷時の設定にリセットなどのリモート操作を実行したユーザーが表示され、さらにその操作の状態が表示されます。 「[デバイス管理とは](device-management.md)」を参照してください。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>管理されていないデバイスから割り当てられているアプリにアクセス可能 <!--664691-->
ポータル Web サイトでの設計変更に伴い、iOS と Android ユーザーは、管理されていないデバイスで "登録なしで使用可能" として割り当てられているアプリをインストールできるようになります。 Intune 資格情報を使用して、ユーザーはポータル Web サイトにログインし、割り当てられているアプリの一覧を表示することができます。 "登録なしで使用可能" なアプリのアプリ パッケージは、ポータル Web サイトからダウンロードできます。 この変更は、インストールするために登録が必要なアプリには影響しません。そのようなアプリをインストールする場合は、デバイスの登録が求められます。

### <a name="custom-app-categories---748805--"></a>カスタム アプリのカテゴリ <!--748805-->
Intune に追加するアプリのカテゴリを作成、編集、および割り当てることができるようになりました。 現時点では、カテゴリは英語でのみ指定できます。
[Intune にアプリを追加する方法](apps-add.md)に関するページを参照してください。

### <a name="display-device-categories---814654--"></a>デバイス カテゴリを表示する <!--814654-->
デバイスの一覧に、列としてデバイス カテゴリを表示できるようになりました。 デバイスのプロパティー ブレードのプロパティー セクションからカテゴリを編集することもできます。 [Intune にアプリを追加する方法](apps-add.md)に関するページを参照してください。

### <a name="configure-windows-update-for-business-settings---776716--"></a>ビジネス設定向けの Windows Update の構成<!--776716-->

サービスとしての Windows は、Windows 10 の更新プログラムを提供するための新しい方法です。 Windows 10 以降、すべての新しい機能更新プログラムと品質更新プログラムには、以前の更新プログラムすべての内容が含まれます。 つまり、最新の更新プログラムをインストールしている限り、Windows 10 デバイスが完全に最新の状態であることを把握できます。 以前のバージョンの Windows とは異なり、更新プログラムの一部ではなく全体をインストールすることが必要になります。

Windows Update for Business を使用することで、デバイスのグループに対して個々の更新プログラムを承認する必要がなくなるため、更新プログラム管理エクスペリエンスを簡略化できます。 更新プログラムの展開戦略を構成することで環境内のリスクを引き続き管理でき、さらに Windows Update により更新プログラムが適切なタイミングでインストールされるようになります。 Microsoft Intune では、デバイスでの更新プログラムの設定を構成でき、また更新プログラムのインストールを遅らせることができます。 Intune では更新プログラムは格納されず、更新プログラムのポリシー割り当てのみが格納されます。 デバイスは更新プログラムのため Windows Update に直接アクセスします。**Windows 10 更新プログラム リング**を構成し管理するには Intune を使用します。 更新プログラム リングには、Windows 10 更新プログラムがインストールされるタイミングと方法を構成する設定のグループが含まれています。 詳しくは、「[ビジネス設定向けの Windows Update の構成](windows-update-for-business-configure.md)」をご覧ください。
