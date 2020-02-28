---
title: 開発中 - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune の開発中の機能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7113552e09a7c7fa145a452e56575bfaf5297c3e
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514568"
---
# <a name="in-development-for-microsoft-intune---february-2020"></a>Microsoft Intune 用に開発中 - 2020 年 2 月

お客様の準備と計画をサポートするため、このページでは、開発中でまだリリースされていない Intune UI の更新と機能が一覧表示されます。 このページの情報に加えて: 

- 変更前にお客様による対処が必要であると予測される場合は、Office メッセージ センターに補足の投稿が公開されます。
- 機能の運用が始まると、機能の説明はプレビュー版も一般公開版も、このページから[新機能](whats-new.md)に関するページに移行します。
- このページと[新機能](whats-new.md)に関するページは、定期的に更新されます。 適宜確認してください。
- 戦略的な成果物とタイムラインについては、「[Microsoft 365 のロードマップ](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)」を参照してください。

> [!NOTE]
> このページには、将来のリリースでの Intune の機能に関する現在の予測が反映されています。 日付と個々の機能は変更される可能性があります。 このページは、開発中のすべての機能を説明しているわけではありません。

**RSS フィード**:ご自身のフィード リーダーに次の URL をコピーして貼り付けることで、このページが更新されたときにわかるようになります。`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>アプリ管理

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Windows でポータル サイト アプリの通知を表示する<!-- 1808082  -->
Windows デバイス上のポータル サイト アプリを更新し、アプリケーションが閉じている場合でも、ユーザーにトースト通知を表示します。 更新により、インストール状態が [完了] または [失敗] の場合にのみ、利用可能なアプリの通知が表示されます。 ポータル サイト アプリには、必要なアプリケーションの通知は表示されません。 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>ポータル サイト アプリのインストール状態メッセージを表示する<!-- 2514416  -->
ポータル サイト アプリでは、エンド ユーザーに追加のアプリ インストール状態メッセージが表示されます。 新しい Win32 依存関係機能には、次の条件が適用されます。
- アプリをインストールできませんでした。 管理者によって定義された依存関係が満たされませんでした。

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>iOS/iPadOS デバイス上の Microsoft Edge に Web クリップを再ターゲットする<!-- 5455276 -->
iOS/iPadOS デバイス上でピン留めされた Web アプリとして機能する Web クリップを更新する必要があります。 新しく展開された Web クリップを保護されたブラウザーで開く必要がある場合は、Intune Managed Browser ではなく Microsoft Edge で開きます。 既存の Web クリップを再ターゲットして、Managed Browser ではなく Microsoft Edge で開くようにする必要があります。

### <a name="macos-company-portal-user-experience-improvements---5568987---"></a>macOS ポータル サイトのユーザー エクスペリエンスの向上<!-- 5568987 -->
macOS デバイスの登録エクスペリエンスと Mac 用ポータル サイト アプリの機能強化を行っています。 次のことが可能になります。
- 登録時の Microsoft **AutoUpdate** エクスペリエンスが向上し、ユーザーが最新バージョンのポータル サイトを確実に使用できるようになります。
- 登録時のコンプライアンス チェック手順が強化されます。
- インシデント ID のコピーがサポートされるため、ユーザーは自分のデバイスから会社のサポート チームにエラーを迅速に送信することができます。

登録と Mac 用ポータルサイトアプリの詳細については、「ポータル サイト アプリを使用して macOS デバイスを登録する (https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp)」を参照してください。 


### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>ポータル サイトの Android 仕事用プロファイルの登録から削除される画面<!--6103987 -->
ユーザー エクスペリエンスを効率化するために、ポータル サイトの Android 仕事用プロファイルの登録フローから **[次の手順]** 画面が削除されます。 現在の Android 仕事用プロファイルの登録フローを確認するには、[Android の仕事用プロファイルを使用した登録]( https://docs.microsoft.com/intune-user-help/enroll-device-android-work-profile)の方法に関するページを参照してください。

### <a name="microsoft-defender-advanced-threat-protection-atp-app-for-macos---5424518-idready---"></a>macOS 用 Microsoft Defender Advanced Threat Protection (ATP) アプリ<!-- 5424518 idready -->
Intune を使用すると、macOS 用 Microsoft Defender Advanced Threat Protection (ATP) アプリを管理対象 Mac デバイスに簡単に展開できるようになります。 詳細については、「[Microsoft Defender Advanced Threat Protection for Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)」を参照してください。 

<!-- ***********************************************-->
## <a name="device-configuration"></a>デバイスの構成

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>macOS デバイス用の有線ネットワーク デバイス構成プロファイル<!-- 3508686  -->
有線ネットワークを構成する (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** >  プラットフォームの **[macOS]** > プロファイル タイプの **[ワイヤード (有線) ネットワーク]**) 新しい macOS デバイス構成プロファイルが使用できるようになります。 この機能を使用して、有線ネットワークを管理する 802.1x プロファイルを作成し、この有線ネットワークを macOS デバイスに展開します。

適用対象:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932-idready---"></a>IKEv2 VPN 接続を使用する VPN プロファイルでは iOS/iPadOS デバイスで常時接続を使用できる <!-- 1947932 idready -->
iOS/iPadOS デバイスでは、IKEv2 接続を使用する VPN プロファイルを作成することができます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** >  プラットフォームの **[iOS/iPadOS]** > プロファイル タイプの **[VPN]**)。 今後の更新では、IKEv2 を使用して常時接続を構成することができます。 構成すると、IKEv2 VPN プロファイルは自動的に接続され、VPN に接続されたままになります (またはすぐに再接続されます)。 ネットワーク間を移動したり、デバイスを再起動したりしても、接続されたままになります。

iOS/iPadOS では、常時接続 VPN は IKEv2 プロファイルに限定されます。

現在構成できる IKEv2 設定については、「[Microsoft Intune で iOS/iPadOS デバイス向けの VPN 設定を追加する](../configuration/vpn-settings-ios.md#ikev2-settings)」を参照してください。

適用対象:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>iOS/iPadOS および macOS デバイスで構成プロファイルを作成するときのユーザー インターフェイス エクスペリエンスの向上<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
iOS/iPadOS または macOS デバイス用のプロファイルを作成すると、Endpoint Management 管理センターのエクスペリエンスが更新されます。 この変更は、次のデバイス構成プロファイルに影響します (**[デバイス]** > **[構成プロファイル]** > **[プロファイルの作成]** >  プラットフォームの **[iOS]** または **[macOS]**):

- カスタム: iOS/iPadOS、macOS
- デバイスの機能: iOS/iPadOS、macOS
- デバイスの制限: iOS/iPadOS、macOS
- エンドポイント保護: macOS
- 拡張機能: macOS
- 設定ファイル: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Android Enterprise デバイスで OEMConfig 構成プロファイルを作成するときのユーザー インターフェイス エクスペリエンスの向上<!-- 5568645 idready  -->
Android Enterprise デバイスで OEMConfig プロファイルを作成または編集すると、Endpoint Management 管理センターのエクスペリエンスが更新されます。 更新されたエクスペリエンスによって、構成した設定の概要が表示されます。 この変更は、OEMConfig デバイス構成プロファイルに影響します (**[デバイス]** > **[構成プロファイル]** > **[プロファイルの作成]** >  プラットフォームの **[Android Enterprise]** > プロファイルの種類の **[OEMConfig]**)。

この機能は、以下に適用されます。
- Android エンタープライズ 


<!-- ***********************************************-->
<!--## Device enrollment-->


<!-- ***********************************************-->
## <a name="device-management"></a>デバイス管理

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Windows デバイスのプライマリ ユーザーを変更する <!-- 3794742 -->
Windows ハイブリッド デバイスと Azure AD 参加済みデバイスのプライマリ ユーザーを変更できるようになります。 これを行うには、**[Intune]** > **[デバイス]** > **[すべてのデバイス]** > デバイスを選択 > **[プロパティ]** > **[プライマリ ユーザー]** を選択します。 

### <a name="serial-number-on-the-apple-mdm-push-certificate-page--5947765---"></a>[Apple MDM プッシュ通知証明書] ページのシリアル番号<!--5947765 -->
[Apple MDM プッシュ通知証明書] ページにシリアル番号が表示されるようになります。 証明書を作成した Apple ID へのアクセスが失われた場合に、Apple MDM プッシュ通知証明書へのアクセスを回復するには、シリアル番号が必要です。 シリアル番号を表示するには、**[デバイス]** > **[iOS]** > **[iOS enrollment]\(iOS の登録\)** > **[Apple MDM プッシュ通知証明書]** に移動します。

### <a name="choose-which-iosipados-updates-to-push-to-enrolled-devices--5879689---"></a>登録されたデバイスにプッシュする iOS または iPadOS の更新プログラムを選択する<!--5879689 -->
Apple Business Manager または Apple School Manager を使用すると、登録されたデバイスにプッシュする、特定の iOS または iPadOS の更新プログラムを選択できるようになります。 これらのデバイスでは、ソフトウェア更新プログラムの可視性を一定の日数だけ遅らせるようにデバイス構成ポリシーを設定する必要があります。 この機能を確認するには、MEM > **[デバイス]** > **[iOS]** > **[Update policies for iOS/iPadOS]\(iOS または iPadOS のポリシーを更新する\)** > **[プロファイルの作成]** に移動します。

### <a name="new-update-schedule-options-for-pushing-os-updates-to-enrolled-iosipados-devices--5879689--"></a>登録された iOS デバイスまたは iPadOS デバイスに OS 更新プログラムをプッシュするための新しい更新スケジュール オプション<!--5879689-->
iOS デバイスまたは iPadOS デバイスのオペレーティング システムの更新をスケジュールするときに、次のオプションを使用できるようになります。 これは、Apple Business Manager または Apple School Manager の登録タイプを使用したデバイスに適用されます。
- 次回のチェックイン時に更新する
- スケジュールされた時刻に更新する
- スケジュールされた時刻以外に更新する

後者の 2 つのオプションでは、複数の時間帯を作成できます。

新しいオプションを確認するには、MEM > **[デバイス]** > **[iOS]** > **[Update policies for iOS/iPadOS]\(iOS または iPadOS のポリシーを更新する\)** > **[プロファイルの作成]** に移動します。


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>監視とトラブルシューティング

### <a name="improved-intune-reporting-experience---3791418-idready---"></a>Intune レポート エクスペリエンスの向上<!-- 3791418 idready -->
Intune では、新しいレポートの種類、より優れたレポート編成、より対象を絞ったビュー、より優れたレポート機能、より一貫性のあるタイムリーなデータを含め、レポート エクスペリエンスが向上しています。 レポート エクスペリエンスは、パブリック プレビューから GA (一般公開) に移行します。 また、GA リリースでは、[Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)のタイルで、ローカライズ サポート、バグ修正、設計の改善、デバイス コンプライアンス データの集計を行うことができます。

新しいレポートの種類では、次のことに重点が置かれています。
- **運用** - 正常性への悪影響に焦点を置いた最新のレコードが表示されます。 
- **組織** - 全体的な状態の概要が表示されます。
- **履歴** - 一定期間におけるパターンと傾向が表示されます。
- **スペシャリスト** - 生データを使用して独自のカスタム レポートを作成できます。

新しいレポートの最初のセットでは、デバイスのコンプライアンスに重点が置かれています。 詳細については、[ブログ - Microsoft Intune レポート フレームワーク](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553)および[Intune レポート](~/fundamentals/reports.md)に関するページを参照してください。



<!-- ***********************************************-->
## <a name="role-based-access-control"></a>ロール ベースのアクセス制御

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Intune ロールのユーザー インターフェイスが変更予定<!--5801612 idready-->
[Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) > **[テナント管理]** > **[ロール]** のユーザー インターフェイスが、ユーザーフレンドリで直感的な設計に変更されます。 このエクスペリエンスでは、現在使用しているのと同じ設定と詳細が提供されます。ただし、新しいエクスペリエンスでは、ウィザードに似たプロセスが採用されています。


<!-- ***********************************************-->
## <a name="security"></a>セキュリティ

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Android COBO デバイスでの派生資格情報のサポート<!--4839592-->
Android Enterprise の完全に管理されたデバイスで、派生資格情報を使用できるようになります。 Entrust Datacard、Intercede、および DISA Purebred の派生資格情報を取得するためのサポートが追加されます。 アプリ認証、Wi-Fi、VPN、または S/MIME 署名や、それをサポートするアプリでの暗号化に、派生資格情報を使用できるようになります。

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>ウイルス対策ポリシーを使用して Microsoft Defender ウイルス対策および Windows セキュリティ エクスペリエンスの設定を管理する<!--6131401 -->
"*エンドポイント セキュリティ*" ノードで、**ウイルス対策**の設定を構成できます。 ウイルス対策のポリシーを構成する場合は、次の 2 種類のプロファイルを使用して Windows 10 デバイスの設定を定義します。

- Microsoft Defender ウイルス対策: クラウドの保護、ウイルス対策の除外、修復、スキャン オプションなどの設定を管理します。
- Windows セキュリティ エクスペリエンス: ユーザーが自分のデバイスで Windows セキュリティ設定を体験する方法を管理します。 Microsoft Defender セキュリティ センターでエンド ユーザーが表示できる内容と、エンド ユーザーが受信する通知を構成できるようになります。 

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。


