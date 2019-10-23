---
title: 開発中 - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune の開発中の機能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea5fae72f6e2057ef0b03a7bd295085ed1ac3bbd
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601548"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>Microsoft Intune 用に開発中 - 2019 年 10 月

お客様の準備と計画をサポートするため、このページでは、開発中でまだリリースされていない Intune UI の更新と機能が一覧表示されます。 このページの情報に加えて、次のようになります。

- 変更前にお客様による対処が必要であると予測される場合は、Office メッセージ センターに補足の投稿が公開されます。
- 機能が運用環境に入ると、プレビュー版でも一般公開版でも、機能の説明はこのページから[新](whats-new.md)機能に移行します。
- このページと[新機能](whats-new.md)に関するページは、定期的に更新されます。 適宜確認してください。
- 戦略的な成果物とタイムラインについては、「[Microsoft 365 のロードマップ](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)」を参照してください。

> [!NOTE]
> このページには、今後のリリースでの Intune の機能に関する現在の期待が反映されています。 日付と個々の機能は変更される可能性があります。 このページでは、開発のすべての機能について説明していません。

**RSS フィード**: ご自身のフィード リーダーに次の URL をコピーして貼り付けることで、このページが更新されたときにわかるようになります。`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

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

### <a name="apply-dark-mode-in-ios-company-portal----4911422----"></a>IOS ポータルサイトでのダークモードの適用 <!-- 4911422  -->
ダークモードは、iOS ポータルサイトに対して計画されています。 会社のアプリをダウンロードし、デバイスを管理し、任意の配色で IT サポートを受けることができます。 iOS ポータル サイトの詳細については、「[Microsoft Intune ポータル サイト アプリを構成する方法](../apps/company-portal-app.md)」をご覧ください。

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Windows 10 の S モードデバイスで Win32 アプリを実行する <!-- 3747604  --> 
Windows 10 S モードで管理されているデバイスに Win32 アプリをインストールして実行することができます。 Windows Defender Application Control (WDAC) PowerShell ツールを使用して、S モード用に1つ以上の補足ポリシーを作成します。 Device Guard 署名ポータルを使用して、補足ポリシーに署名します。 次に、Intune を使用してポリシーをアップロードして配布します。 

Intune では、 **[クライアントアプリ]** [Windows 10  >  の**補足ポリシー**] の順に選択することで、この機能を確認できます。 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>日付と時刻に基づいてアプリの可用性を設定する <!-- 3510685  -->
管理者は、必要なアプリの開始時刻と期限を構成することができます。 開始時に、Intune 管理拡張機能はアプリのコンテンツをダウンロードしてキャッシュします。 アプリは期限時にインストールされます。 利用可能なアプリの場合、開始時刻によって、アプリがポータルサイトに表示されるタイミングが決まります。 

日付と時刻に基づいてアプリの可用性を設定するには:

1. Intune で、 **[クライアント アプリ]**  >  **[アプリ]** を選択します。 
1. 一覧からアプリを選択するか、 **[追加]** を選択して新しいアプリを追加します。 
1. アプリブレードで **[割り当て]** を選択し  >  **[グループの追加]** を選択します。 
1. **[割り当ての種類]** を **[必須]** に設定し、 **[含まれているグループ]** を選択します。 
1. [**すべてのユーザーにこのアプリを必須**にする **] を [はい]** に設定します。 
1. **[編集]** を選択して、**エンドユーザーエクスペリエンス**オプションを変更します。 
1. **[エンドユーザーエクスペリエンス]** ブレードで、必要に応じて**ソフトウェアの使用可能な時間**を設定します。 

詳しくは、「[Microsoft Intune にアプリを追加する](../apps/apps-add.md)」をご覧ください。

### <a name="require-win32-apps-to-restart----3136567----"></a>Win32 アプリの再起動が必要 <!-- 3136567  -->
インストールが正常に完了したら、Win32 アプリを再起動するように要求することができます。 再起動するまでの時間 (猶予期間) を選択できます。

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>Windows でポータルサイトアプリの通知を表示する <!-- 1808082  -->
Windows デバイス上のポータルサイトアプリを更新して、アプリケーションが閉じられた場合でも、ユーザーにトースト通知を表示します。 更新プログラムでは、インストールの状態が [完了] または [失敗] の場合にのみ、利用可能なアプリの通知が表示されます。 ポータルサイトアプリには、必要なアプリケーションの通知は表示されません。

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>ポータルサイトアプリのインストールステータスメッセージを表示する <!-- 2514416  -->
ポータルサイトアプリには、エンドユーザーに追加のアプリインストールステータスメッセージが表示されます。 新しい Win32 依存関係機能には、次の条件が適用されます。
- アプリをインストールできませんでした。 管理者によって定義された依存関係が満たされませんでした。
- アプリは正常にインストールされましたが、再起動が必要です。
- アプリはインストールの処理中ですが、続行するには再起動が必要です。

### <a name="assign-the-microsoft-edge-beta-for-macos----4678761----"></a>MacOS 用 Microsoft Edge ベータ版の割り当て <!-- 4678761  -->
最新バージョンの Microsoft Edge ベータ版を macOS デバイス用の Intune に追加して割り当てることができます。 

MacOS デバイス用の Microsoft Edge ベータ版を割り当てるには、次のようにします。
1. Intune で、[**クライアント** >  **アプリ** ] を選択して、**Microsoft Edge-macOS** >  アプリ  > **追加**します。 
1. Microsoft Edge beta を目的のグループに割り当てます。 Microsoft AutoUpdate (MAU) は Microsoft Edge を最新の状態に保ちます。 
 
Microsoft Edge の詳細については、「 [Microsoft Intune で Microsoft edge を使用して web アクセスを管理する](../apps/manage-microsoft-edge.md)」を参照してください。

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>組織アカウントのアプリ通知コンテンツを構成する <!-- 2576686 -->
Android および iOS デバイスの Intune アプリを使用すると、組織アカウントのアプリ通知コンテンツを制御できます。 この機能を使用するには、アプリケーションからのサポートが必要であり、すべてのアプリ対応アプリケーションで利用できるとは限りません。 APP について詳しくは、[アプリ保護ポリシーの概要](../apps/app-protection-policy.md)に関するページをご覧ください。


<!-- ***********************************************-->
## <a name="device-configuration"></a>デバイス構成

### <a name="new-device-firmware-configuration-interface-profile-for-devices-that-run-windows-10-and-later----2266073----"></a>Windows 10 以降を実行するデバイス用の新しいデバイスファームウェア構成インターフェイスプロファイル <!-- 2266073  -->
Windows 10 以降では、デバイス構成プロファイルを作成して、設定と機能を制御できます。 

1. **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択します。
1. [プラットフォーム] には、 **[Windows 10 以降]** を選択します。 
 
新しいデバイスファームウェア構成インターフェイスの種類によって、Intune で UEFI (BIOS) 設定を管理できるようになります。

構成できる現在の設定の詳細については、「 [Microsoft Intune のデバイスプロファイルを使用してデバイスの機能と設定を適用](../configuration/device-profiles.md)する」を参照してください。

この機能は、Windows 10 RS5 (1809) 以降のデバイスの選択に適用されます。
 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>デバイスの登録

### <a name="for-ios-devices-customize-the-enrollment-privacy-window-of-company-portal----4394993----"></a>IOS デバイスの場合は、ポータルサイトの [登録のプライバシー] ウィンドウをカスタマイズします。 <!-- 4394993  -->
Markdown を使うことで、iOS の登録時にエンド ユーザーに表示されるポータル サイトのプライバシー ウィンドウをカスタマイズできます。 具体的には、組織がデバイス上で参照または実行できない項目の一覧をカスタマイズできます。

<!-- ***********************************************-->
## <a name="device-management"></a>デバイス管理


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>自動操縦デバイスのグループタグの値を編集する<!-- 4816775 -->
自動操縦デバイスの**グループタグ**の値は、次のように編集できます。

1. [ **Intune**  > **デバイスの登録**] を選択し、[windows の**登録**]  >  [**windows 自動** >   > **デバイス**] を選択します。
1. デバイスを選択します。
1. 右側のペインで、**グループタグ**の値を変更します。
1. **[保存]** を選択します。

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Jamf の管理を必要とする macOS ユーザーグループをターゲットにする <!-- 4061739 -->
特定のユーザーグループを対象にして、macOS デバイスを Jamf で管理するように要求することができます。 このターゲット設定を使用すると、Jamf コンプライアンス統合を macOS デバイスのサブセットに適用できますが、他のデバイスは Intune によって引き続き管理されます。 ターゲットを設定することにより、ユーザーのデバイスを1つのモバイルデバイス管理 (MDM) システムから別のデバイスに段階的に移行することもできます。

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>MacOS デバイスへのソフトウェア更新プログラムの展開 <!-- 3194876 -->
MacOS デバイスのグループにソフトウェア更新プログラムを展開できるようになります。 この機能には、重要な、ファームウェア、構成ファイル、およびその他の更新プログラムが含まれます。 次のデバイスのチェックイン時に更新を送信できます。 または、毎週のスケジュールを選択して、設定した期間内に更新プログラムを展開することもできます。 

この機能は、ヘルプデスクが完全に仕事をしているときに、標準の勤務時間外または時間外にデバイスを更新する場合に役立ちます。 また、更新プログラムが展開されているすべての macOS デバイスの詳細なレポートも表示されます。 デバイスごとにレポートを表示して、特定の更新プログラムの状態を確認することができます。

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>監視とトラブルシューティング

### <a name="android-report-on-the-devices-overview-page----2984353----"></a>[デバイスの概要] ページの Android レポート <!-- 2984353  -->
**[デバイスの概要]** ページに新しいレポートを追加します。 このレポートには、各デバイス管理ソリューションに登録されている Android デバイスの数が表示されます。 このグラフには、仕事用プロファイルのデバイス数、完全管理型、専用デバイス、およびデバイス管理者が登録されています。 

レポートを表示するには、[ **Intune** >  台の**デバイス** >  の**概要**] を選択します。

### <a name="updated-support-experience-------5012398------"></a>更新されたサポートエクスペリエンス   <!--  5012398    -->
継続的な改善の一環として、Intune のコンソール内サポートエクスペリエンスを更新します。  一般的な問題についてコンソール内での検索とフィードバックを改善し、サポートに連絡するためのワークフローを効率化します。     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
