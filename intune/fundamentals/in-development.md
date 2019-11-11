---
title: 開発中 - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune の開発中の機能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3720b0b9a67f0c3462993feef4162ef35f7f3f92
ms.sourcegitcommit: d1b36501186e867355843ddd67c795ade800b76a
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182925"
---
# <a name="in-development-for-microsoft-intune---november-2019"></a>Microsoft Intune 用に開発中 - 2019 年 11 月

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

### <a name="smime-support-for-microsoft-outlook-mobile----2669398----"></a>Microsoft Outlook Mobile の S/MIME サポート <!-- 2669398  -->
Intune では、iOS および Android の Outlook Mobile で使用できる S/MIME 署名証明書と暗号化証明書の配信がサポートされます。 関連情報については、「 [iOS デバイスの電子メール設定](~/configuration/email-settings-ios.md)と[Android デバイス用電子メール設定](~/configuration/email-settings-android.md)」を参照してください。

### <a name="custom-settings-support-for-macos-applications----4736278----"></a>MacOS アプリケーションのカスタム設定のサポート <!-- 4736278  -->
Intune ではカスタム設定がサポートされているため、特定のキーと値を既存の設定プロパティリスト (plist) ファイルに追加して、macOS アプリとデバイスを構成することができます。 管理された基本設定をサポートしていないアプリもあれば、特定の設定のみを管理できる場合もあります。 設定はデバイスチャネルのみを使用して展開されます。 デバイスチャネルの設定を対象とするプロパティリストファイルまたは .xml ファイルのみをアップロードする必要があります。

### <a name="assignment-type-value-in-windows-company-portal----5459950----"></a>Windows ポータルサイトの割り当ての種類の値 <!-- 5459950  -->
Windows ポータルサイトアプリの **[インストールされているアプリ]** ページが更新されます。 **[インストールさ]** れたアプリ ページの **[割り当ての種類]** 列が、"組織で必要" という名前に更新されました。 指定できる値は **[はい]** または **[いいえ]** で、必要なアプリと使用可能なアプリを指定します。 この変更は、いくつかのエンドユーザーの混乱に応じて行われています。 Windows ポータル サイトの詳細については、「[Microsoft Intune ポータル サイト アプリを構成する方法](~/apps/company-portal-app.md)」をご覧ください。

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

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>組織アカウントのアプリ通知コンテンツを構成する <!-- 2576686 -->
Android および iOS デバイスの Intune アプリを使用すると、組織アカウントのアプリ通知コンテンツを制御できます。 この機能を使用するには、アプリケーションからのサポートが必要であり、すべてのアプリ対応アプリケーションで利用できるとは限りません。 APP について詳しくは、[アプリ保護ポリシーの概要](../apps/app-protection-policy.md)に関するページをご覧ください。


<!-- ***********************************************-->
## <a name="device-configuration"></a>デバイス構成

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices----3246388----"></a>Windows 10 以降のデバイスでの Wi-fi プロファイルでの PKCS 証明書の使用 <!-- 3246388  -->
現時点では、SCEP 証明書を使用して Windows Wi-fi プロファイルを認証することができます (**デバイスの構成** > **プロファイル** >  > **プロファイルを作成**するには、 **windows 10 以降**のプラットフォーム > **wi-fi**プロファイルの種類 > **Enterprise** > **EAP の種類**)。 Windows Wi-fi プロファイルで PKCS 証明書を使用できるようになります。 この機能により、ユーザーはテナント内の新規または既存の PKCS 証明書プロファイルを使用して Wi-fi プロファイルを認証できます。 

Wi-fi プロファイルの詳細については、「 [Intune で Windows 10 以降のデバイスの wi-fi 設定を追加](../configuration/wi-fi-settings-windows.md)する」を参照してください。

適用対象:
- Windows 10 以降

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices----4892824----"></a>IOS デバイスで電子メールデバイス構成プロファイルを作成するときの新しい ExchangeActiveSync 設定 <!-- 4892824  --> 
IOS/iPadOS デバイスでは、デバイス構成プロファイルに電子メール接続を構成することができます (**デバイス構成** ** > プロファイル** >  **[プロファイルの作成]**  > **iOS/Ipados** for platform >**電子メール**プロファイルの種類の場合)。 

次のような新しい ExchangeActiveSync 設定を使用できます。
- 電子メール、予定表、連絡先など、同期する (または同期をブロックする) サービスを選択します。
- ユーザーが自分のデバイスでこれらのサービスの同期設定を変更することを許可 (またはブロック) します。 

現在の設定を確認するには、「 [Intune で iOS デバイスの電子メールプロファイル設定](../configuration/email-settings-ios.md)」にアクセスしてください。

適用対象:
- iOS 13.0 以降
- iPadOS 13.0 以降

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices----5353228----"></a>ユーザーが個人の Google アカウントを Android エンタープライズデバイス所有者と専用デバイスに追加できないようにする <!-- 5353228  -->
Android enterprise デバイス所有者と専用デバイス (**デバイス構成** > **プロファイル** > **android Enterprise** > **プロファイルを作成**するために、ユーザーが個人の Google アカウントを作成できないようにすることができます。プラットフォーム >**デバイス所有者**は、プロファイルの種類 >**ユーザーとアカウントの設定**) に対してのみデバイスの制限を > ます。

現在構成できる設定を確認するには、「[Intune を使用して機能を許可または制限するように Android エンタープライズ デバイスを設定する](../configuration/device-restrictions-android-for-work.md)」をご覧ください。

適用対象:
- Android Enterprise デバイス所有者
- Android Enterprise 専用デバイス

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile----5468501----"></a>Siri コマンド設定のサーバー側ログは、iOS デバイス制限プロファイルで削除されました <!-- 5468501  -->
IOS デバイスでは、デバイスの制限プロファイルを作成して、Siri コマンドのサーバー側のログ記録を構成することができます (**デバイスの構成** > **プロファイル** >  > **iOS/ipados**のプラットフォーム用の**プロファイルを作成**します。プロファイルの種類 >**組み込みアプリ**) に関する**デバイスの制限**> ます。 **Siri コマンド設定のサーバー側のログ記録**が削除されます。

この設定は、Intune 管理コンソールから削除されます。 この設定が構成されている既存のポリシーでは引き続き設定が表示されますが、この設定はデバイスには影響しません。 既存のポリシーから設定を削除する場合は、ポリシーにアクセスし、軽微な編集を行って保存すると、ポリシーが更新されます。

構成できる設定を確認するには、「[Intune を使用した機能を許可または制限するための iOS および iPadOS デバイスの設定](../configuration/device-restrictions-ios.md)」をご覧ください。

適用対象:
- iOS


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>デバイス管理

### <a name="edit-device-name-value-for-autopilot-devices---2640074----"></a>自動操縦デバイスのデバイス名の値を編集する<!-- 2640074  -->
Azure AD に参加している自動操縦デバイスのデバイス名の値を編集できるようになります。 これを行うには、 > **Intune**の **[デバイスの登録]**  > [windows の > **登録**] の順に選択し、[ **windows の自動操縦** > **デバイス**] > デバイスを選択 > 右側のウィンドウの **[デバイス名]** の値を変更します。>**保存**します。


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>自動操縦デバイスのグループタグの値を編集する<!-- 4816775 -->
自動操縦デバイスの**グループタグ**の値は、次のように編集できます。

1. [**Intune** > **デバイスの登録**] を選択し、[windows の**登録**] > [**windows 自動** >  > **デバイス**] を選択します。
1. デバイスを選択します。
1. 右側のペインで、**グループタグ**の値を変更します。
1. **[保存]** を選択します。

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Jamf の管理を必要とする macOS ユーザーグループをターゲットにする <!-- 4061739 -->
特定のユーザーグループを対象にして、macOS デバイスを Jamf で管理するように要求することができます。 このターゲット設定を使用すると、Jamf コンプライアンス統合を macOS デバイスのサブセットに適用できますが、他のデバイスは Intune によって引き続き管理されます。 ターゲットを設定することにより、ユーザーのデバイスを1つのモバイルデバイス管理 (MDM) システムから別のデバイスに段階的に移行することもできます。

<!-- ***********************************************-->
## <a name="intune-apps"></a>Intune アプリ

### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>ポータルサイトでの macOS の登録エクスペリエンスが向上しました <!-- 5074349  -->
MacOS の登録エクスペリエンスのポータルサイトには、より簡単な登録プロセスが用意されています。これは、iOS の登録エクスペリエンスのポータルサイトにより密接に連携します。 デバイスのユーザーには次のように表示されます。  

* Sleeker ユーザーインターフェイス。  
* 強化された登録チェックリスト。  
* デバイスを登録する方法について、より明確に説明します。  
* トラブルシューティングオプションの向上。  

### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857----"></a>Android 用ポータルサイトアプリでの改良されたチェックリストの設計<!-- 5550857  -->
Android 用のポータルサイトアプリのセットアップチェックリストは、軽量のデザインと新しいアイコンによって更新されます。 変更は、iOS 用ポータルサイトアプリに対して行われた最新の更新プログラムと一致します。

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>監視とトラブルシューティング

### <a name="updated-support-experience-------5012398------"></a>更新されたサポートエクスペリエンス   <!--  5012398    -->
継続的な改善の一環として、Intune のコンソール内サポートエクスペリエンスを更新します。  一般的な問題についてコンソール内での検索とフィードバックを改善し、サポートに連絡するためのワークフローを効率化します。     

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>ロールベースのアクセス制御

### <a name="duplicate-custom-or-built-in-roles----1081938---"></a>カスタムロールまたは組み込みロールの重複 <!-- 1081938 -->
組み込みロールとカスタムロールをコピーすることができます。 これを行うには、[ **Intune** > **ロール** > **すべてのロール**] の順に選択し > **[複製]** > 一覧でロールを選択します。 一意の新しい名前を入力してください。

<!-- ***********************************************-->

## <a name="security"></a>セキュリティ

### <a name="bitlocker-key-rotation--------2564951--------"></a>BitLocker キーのローテーション     <!-- 2564951      -->
Intune を使用して、Windows バージョン1909以降を実行している管理対象デバイスの BitLocker 回復キーをローテーションすることができます。 

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
