---
title: 開発中 - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune の開発中の機能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
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
ms.openlocfilehash: 7bba992c79f69a126f0199d9cdac52779910ff38
ms.sourcegitcommit: 068c4e4bc6e6d778ece4a83d000128c4d2b732db
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910323"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>開発中の Microsoft Intune - May 2019 年 5 月

お客様による準備と計画を支援するため、このページには Intune の UI の更新と、開発中でまだリリースされていない機能がリストされています。 さらに

- お客様による変更前の対処が必要であると予測される場合は、補足の Office メッセージ センター投稿を公開します。
- 機能が運用環境でプレビューまたは一般公開としてリリースされると、機能の説明はこのページから[新機能ページ](whats-new.md)に移されます。
- このページと[新機能ページ](whats-new.md)は定期的に更新されます。 適宜確認してください。
- 戦略的成果物とタイムラインについては、[Microsoft 365 のロードマップ](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)を参照してください。

> [!Note]
> これらの項目には、将来のリリースで導入される Intune の機能に関する Microsoft の現在の予測が反映されています。 日付と個々の機能は変更されることがあります。 すべての開発中の項目について、このページに機能の説明があるわけではりません。

**RSS フィード**: ご自身のフィード リーダーに次の URL をコピーして貼り付けることで、このページの更新時に通知を受け取ることができます。`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune


<!-- 1905 start-->


### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Apple ポータルでデバイスを削除すると、Intune ポータルに反映される <!--2489996 -->
Apple の Device Enrollment Program または Apple Business Manager ポータルからデバイスが削除されると、そのデバイスは Intune から次回の同期中に自動的に削除されます。

### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>キーワード検索のベースライン サポート  <!-- 3082036         -->
まもなく、セキュリティのベースライン プロファイルを作成または編集中、コンソールに表示される設定をフィルター処理するために "*検索*" を使用できるようになります。   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Graph API を使用してデバイスを一括でリセットおよびワイプする <!-- 3295288 -->
Graph API を使用して 100 台までのデバイスを一括でリセットおよびワイプできるようになります。

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Windows 10 デバイスのコンプライアンス ポリシーでの TPM チップセットのチェック <!-- 3617671 -->
Windows 10 以降のデバイスの多くには、トラステッド プラットフォーム モジュール (TPM) チップセットが含まれています。 この更新プログラムには、デバイスの TPM チップのバージョンを確認する新しいコンプライアンス設定が含まれています。 

[Windows 10 以降のコンプライアンス ポリシー設定](compliance-policy-create-windows.md#device-security)で、この設定が説明されています。

適用対象: Windows 10 以降

### <a name="intune-management-extension-powershell-scripts-----3734186------"></a>Intune 管理拡張機能の PowerShell スクリプト  <!-- 3734186    -->
PowerShell スクリプトをユーザーの管理者特権を使用してデバイス上で実行するよう構成できるようになります。 詳細については、「[Intune で Windows 10 デバイスに対して PowerShell スクリプトを使用する](intune-management-extension.md)」を参照してください。

### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-supervised-devices----4097904----"></a>エンド ユーザーが個人用ホットスポットを変更できないようにし、iOS が監視するデバイス上での Siri サーバーのログ記録を無効にする <!-- 4097904  --> 
iOS デバイス上にデバイスの制限プロファイルを作成します (**[デバイスの構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[iOS]** (プラットフォーム) > **[デバイスの制限]** (プロファイルの種類))。 この更新プログラムには構成できる新しい設定が含まれています。

- 個人用ホットスポット
- Siri サーバー ログ

現在の設定を確認するには、[機能を許可または制限する iOS デバイスの設定](device-restrictions-ios.md)に関するページを参照してください。 

iOS デバイス 12.2 以降に適用されます。

### <a name="new-classroom-app-device-restriction-settings-for-dep-enrolled-macos-devices----4097905----"></a>DEP 登録された macOS デバイスの新しい Classroom アプリ デバイス制限の設定 <!-- 4097905  --> 
macOS デバイス用のデバイス構成プロファイルを作成できます (**[デバイスの構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[macOS]** (プラットフォーム) > **[デバイスの制限]** (プロファイルの種類))。 この更新プログラムには、DEP 登録デバイス用の新しい Classroom アプリ設定と、iCloud フォト ライブラリを無効にするためのオプションが含まれています。

現在の設定を確認するには、「[Intune を使用して機能を許可または制限するように macOS デバイスを設定する](device-restrictions-macos.md)」を参照してください。

適用対象: macOS 10.14.4 以降

### <a name="android-enterprise-app-management----4459905-idready---"></a>Android Enterprise アプリの管理 <!-- 4459905 idready -->
IT 管理者がより簡単に Android Enterprise 管理を構成および使用できるよう、Intune では 4 つの一般的な Android Enterprise 関連のアプリが Intune 管理コンソールに自動的に追加されます。 4 つの Android Enterprise アプリは次のとおりです。

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Android Enterprise フル マネージド シナリオで使用されます。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 2 要素検証を使用している場合、アカウントへのサインインを支援します。
- **[Intune ポータル サイト](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - アプリ保護ポリシー (APP) と Android Enterprise 仕事用プロファイルのシナリオで使用されます。
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - Android Enterprise 専用またはキオスクのシナリオで使用されます。

以前は、IT 管理者はセットアップの一部として、手動でこれらのアプリを [Managed Google Play ストア](https://play.google.com/store/apps)で探して承認する必要がありました。 この変更により、以前の手動による手順は不要となり、お客様は Android Enterprise 管理をより簡単に素早く使用できるようになります。

管理者は Intune テナントを Managed Google Play に最初に接続したときに、これらの 4 つのアプリが自動的に Intune アプリ一覧に追加されていることを確認できます。 詳細については、[Managed Google Play アカウントへの Intune アカウントの接続](connect-intune-android-enterprise.md)に関するページを参照してください。 自分のテナントを既に接続済みであるか、Android Enterprise を既に使用済みのテナントの場合、管理者が行う必要のある処理はありません。 これらの 4 つのアプリは、2019 年 5 月のサービス ロール アウトの完了から 7 日以内に自動的に表示されます。

<!-- 1904 start-->

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Windows Defender ファイアウォールの詳細設定 <!-- 1311949 -->
まもなく、Intune を使用して Windows Defender 用のクライアント上のカスタム ファイアウォール規則を管理することができるようになります。 規則では、アプリケーション、ネットワーク、アドレス、ポートに対する受信と送信の動作を指定できます。 


### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>デバイスのユーザーは、インストール済みまたはインストールしようとしたすべての管理対象アプリを表示できる <!-- 2352913 -->
Windows 用ポータル サイトに、ユーザーのデバイスにインストールされている、必須および使用可能両方のすべての管理対象アプリがリストされます。 ユーザーは、試行した、および保留中のアプリのインストールと、それらの現在の状態を表示することができるようになります。 組織でアプリが必須または使用可能とされていない場合、会社のアプリは全くインストールされていないというメッセージがユーザーに表示されます。 ユーザーはまた、インストールの状態でアプリを並べ替えまたはフィルタリングすることができます。

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Windows 10 デバイス構成プロファイルを作成するときは "適用規則" を使用する <!-- 2549910 -->
Windows 10 デバイス構成プロファイルを作成します (**[デバイスの構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[Windows 10]** (プラットフォーム))。 **適用規則**を作成し、プロファイルが特定のエディションまたは特定のバージョンにのみ適用されるようにすることができます。 たとえば、いくつかの BitLocker 設定を有効にするプロファイルを作成します。 プロファイルを追加したら、適用規則を使用して Windows 10 Enterprise を実行しているデバイスにのみプロファイルを適用します。

適用対象: 
- Windows 10 以降

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Defender ATP 用の Intune セキュリティ タスク (パブリック プレビュー) <!-- 3208597 -->
Intune では間もなくパブリック プレビューとして、新たに発表された Microsoft Defender Threat & Vulnerability Management 用のセキュリティ タスクが追加されます。  この統合により、Windows Defender ATP (WDATP) のセキュリティ操作管理者は、新たな脅威に対して推奨される修復をより効率的に Intune 管理者に伝えることができます。 セキュリティ タスクの追加により、エンドポイントの脆弱性と構成不備を検出、優先順位付け、修復するためのリスクベースのアプローチが追加されます。

Intune のセキュリティ タスクに関する詳細については、[Intune セキュリティ タスクの使用による Microsoft Defender ATP の Threat and Vulnerability Management の拡張](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857)に関するブログを参照してください。 

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Windows Defender Advanced Threat Protection ベースライン <!-- 3754134 -->
Windows Defender Advanced Threat Protection 設定の構成に役立つ新しいベースラインが追加されます。



## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。


