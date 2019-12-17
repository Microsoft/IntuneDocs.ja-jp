---
title: 開発中 - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune の開発中の機能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04b284a62076122cec70b6b455151a0377470521
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74540733"
---
# <a name="in-development-for-microsoft-intune---december-2019"></a>Microsoft Intune の開発中の機能 - 2019 年 12 月

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

### <a name="ios-user-licensed-vpp-apps---5619268-idready---"></a>iOS ユーザーライセンスの VPP アプリ<!-- 5619268 idready -->
ユーザー登録 iOS デバイスの場合、エンドユーザーには、利用可能として展開されたデバイスライセンス VPP アプリケーションが表示されなくなります。 ただし、エンドユーザーには、ポータルサイト内のすべてのユーザーライセンス VPP アプリが引き続き表示されます。 VPP アプリの詳細については、「[Apple Volume Purchase Program で購入した iOS アプリと macOS アプリを Microsoft Intune で管理する方法](~/apps/vpp-apps-ios.md)」をご覧ください。

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745-idready---"></a>メモリ暗号化された macOS デバイスから個人用回復キーを取得する<!-- 4851745 idready -->
エンドユーザーは、iOS ポータルサイトアプリを使用して個人の回復キー (FileVault キー) を取得できます。 個人用回復キーを持つデバイスは、Intune に登録され、Intune 経由で FileVault を使用して暗号化する必要があります。 IOS ポータルサイトアプリを使用すると、エンドユーザーは Safari web ビューを開き、個人用回復キーを取得できます。 Intune で、*暗号化および登録された macOS デバイス* >  **[デバイス]** を選択し > **回復キーを取得**します。 FileVault の詳細については、「 [FileVault encryption For macOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos)」を参照してください。

### <a name="microsoft-app-icons-update--4677605--"></a>Microsoft アプリアイコンの更新<!--4677605-->
アプリの [ターゲット設定] ウィンドウで、アプリ保護ポリシーとアプリ構成ポリシーの Microsoft アプリに使用されるアイコンが更新されます。

### <a name="smime-support-for-microsoft-outlook-mobile---2669398----"></a>Microsoft Outlook Mobile の S/MIME サポート<!-- 2669398  -->
Intune では、iOS および Android の Outlook Mobile で使用できる S/MIME 署名証明書と暗号化証明書の配信がサポートされます。 関連情報については、「 [iOS デバイスの電子メール設定](~/configuration/email-settings-ios.md)と[Android デバイス用電子メール設定](~/configuration/email-settings-android.md)」を参照してください。

### <a name="custom-settings-support-for-macos-applications---4736278----"></a>MacOS アプリケーションのカスタム設定のサポート<!-- 4736278  -->
Intune ではカスタム設定がサポートされているため、特定のキーと値を既存の設定プロパティリスト (plist) ファイルに追加して、macOS アプリとデバイスを構成することができます。 管理された基本設定をサポートしていないアプリもあれば、特定の設定のみを管理できる場合もあります。 設定はデバイスチャネルのみを使用して展開されます。 デバイスチャネルの設定を対象とするプロパティリストファイルまたは .xml ファイルのみをアップロードする必要があります。

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Windows でポータルサイトアプリの通知を表示する<!-- 1808082  -->
Windows デバイス上のポータルサイトアプリを更新して、アプリケーションが閉じられた場合でも、ユーザーにトースト通知を表示します。 更新プログラムでは、インストールの状態が [完了] または [失敗] の場合にのみ、利用可能なアプリの通知が表示されます。 ポータルサイトアプリには、必要なアプリケーションの通知は表示されません。

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>ポータルサイトアプリのインストールステータスメッセージを表示する<!-- 2514416  -->
ポータルサイトアプリには、エンドユーザーに追加のアプリインストールステータスメッセージが表示されます。 新しい Win32 依存関係機能には、次の条件が適用されます。
- アプリをインストールできませんでした。 管理者によって定義された依存関係が満たされませんでした。

### <a name="configure-app-notification-content-for-organization-accounts---2576686---"></a>組織アカウントのアプリ通知コンテンツを構成する<!-- 2576686 -->
Android および iOS デバイスの Intune アプリを使用すると、組織アカウントのアプリ通知コンテンツを制御できます。 この機能を使用するには、アプリケーションからのサポートが必要であり、すべてのアプリ対応アプリケーションで利用できるとは限りません。 APP について詳しくは、[アプリ保護ポリシーの概要](../apps/app-protection-policy.md)に関するページをご覧ください。

<!-- ***********************************************-->
## <a name="device-configuration"></a>デバイス構成

### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998-idready---"></a>Android エンタープライズデバイス所有者デバイスの管理キーストアで証明書資格情報を構成できないようにする<!-- 3311998 idready -->
Android エンタープライズデバイス所有者のデバイスでは、管理キーストアで証明書の資格情報を構成できないようにする新しい設定があります (**デバイスの構成** > **プロファイル** > **プロファイルの作成** > **Android Enterprise** for platform >**デバイスの所有者のみ >** プロファイルの種類 >**ユーザー + アカウント**)。

現在の設定を確認するには、[Intune を使用して Android エンタープライズ デバイスの機能を許可または制限する設定](../configuration/device-restrictions-android-for-work.md)に関するページを参照してください。

適用対象:
- 専用デバイスと完全に管理されたデバイスを含む、Android Enterprise デバイスの所有者

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686-idready---"></a>MacOS デバイス用のワイヤード (有線) ネットワークデバイス構成プロファイル<!-- 3508686 idready -->
MacOS デバイスでは、今後の更新プログラムに、ワイヤード (有線) ネットワーク (**デバイス構成** > **プロファイル** > 構成する新しいデバイス構成プロファイルが含まれます。このプロファイルでは、**プロファイルの種類**として、プラットフォーム >**ワイヤード (有線) ネットワーク**のプロファイル > **作成**します。 この機能を使用して、ワイヤード (有線) ネットワークを管理する 802.1 x プロファイルを作成し、これらのワイヤード (有線) ネットワークを macOS デバイスに展開します。

適用対象:
- macOS

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Android Enterprise work プロファイルの Wi-fi プロファイルに自動プロキシ設定を追加する<!-- 4490822 idready -->
Android Enterprise Work Profile デバイスでは、Wi-fi プロファイルを作成できます。 Wi-fi エンタープライズタイプを選択した場合は、Wi-fi ネットワークで使用されている拡張認証プロトコル (EAP) の種類を入力することもできます。

今後の更新では、エンタープライズの種類を選択すると、プロキシサーバーの URL (`proxy.contoso.com`など) を含む自動プロキシ設定を入力できるようになります。

構成できる Wi-fi の現在の設定については、 [Microsoft Intune で Android Enterprise と android キオスクを実行するデバイスの wi-fi 設定を追加](../configuration/wi-fi-settings-android-enterprise.md)する方法に関するページを参照してください。

適用対象:
- Android Enterprise 仕事用プロファイル

### <a name="enable-network-access-control-nac-with-cisco-anyconnect-vpn-on-ios-devices---4860111-idready---"></a>IOS デバイスで Cisco AnyConnect VPN を使用してネットワークアクセス制御 (NAC) を有効にする<!-- 4860111 idready -->
IOS デバイスでは、VPN プロファイルを作成し、Cisco AnyConnect (**デバイス構成** > **プロファイル** > さまざまな接続の種類を使用することができます。プロファイルを > **作成**するには、 **[プロファイルの**種類] > [プロファイルの種類] > [接続の種類] [ **cisco anyconnect** **]) を**含みます。 

今後の更新プログラムでは、Cisco AnyConnect でネットワークアクセス制御 (NAC) を有効にすることができます。 この機能を使用するには、以下を行います。

1. [Cisco Identity Services Engine 管理者ガイド](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)の「Azure で Cisco Identity services ENGINE (ISE) を構成するための**MDM サーバーとしての Microsoft Intune の構成**」の手順を使用します。
2. Intune デバイス構成プロファイルで、 **[ネットワーク Access Control (NAC) を有効にする]** 設定を選択します。

使用可能なすべての VPN 設定を表示するには、「 [iOS デバイスで vpn 設定を構成](../configuration/vpn-settings-ios.md)する」を参照してください。

適用対象:
- iOS

### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578-idready---"></a>IOS、iPadOS、および macOS デバイス上のアプリと web サイトのシングルサインオンエクスペリエンスが更新されました<!-- 4999578 idready -->
Intune では、iOS、iPadOS、および macOS デバイスに対して、より多くのシングルサインオン設定を追加しています。 現時点では、Intune で資格情報 SSO アプリ拡張機能と Apple の組み込み Kerberos 拡張機能を構成できます。 今後の更新プログラムでは、組織または id プロバイダーによって作成されたリダイレクト SSO アプリ拡張機能を構成できます。 

これらの設定を使用して、OAuth や SAML2 などの先進認証方法を使用するアプリと web サイトにシームレスなシングルサインオンエクスペリエンスを構成します。 

構成できる SSO アプリ拡張機能の設定を確認するには、「 [iOS で](../configuration/ios-device-features-settings.md#single-sign-on-app-extension)sso を使用する」および「 [macOS で sso](../configuration/macos-device-features-settings.md#single-sign-on-app-extension)」を参照してください。

適用対象:
- iOS/iPadOS
- macOS

### <a name="require-use-of-approved-keyboards-on-android--4761794-idready---"></a>Android で承認済みのキーボードの使用を必須にする<!--4761794 IDready -->
管理対象の Android アプリで使用する承認されたキーボードの一覧を指定できます。 管理対象アプリから、ユーザーはデバイスに既にインストールされている承認済みのキーボードのいずれかに切り替えるよう求められます。また、必要に応じて、承認されたキーボードのいずれかをダウンロードしてセットアップするために Google Play ストアに指示されます。 ユーザーは、アクティブなキーボードが承認されたキーボードの1つである場合にのみ、管理対象アプリのテキストフィールドを編集できます。

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices---3246388----"></a>Windows 10 以降のデバイスでの Wi-fi プロファイルでの PKCS 証明書の使用<!-- 3246388  -->
現時点では、SCEP 証明書を使用して Windows Wi-fi プロファイルを認証することができます (**デバイス構成** > **プロファイル** > **プロファイルの作成** > プラットフォーム用の**Windows 10以降** > プロファイルの種類 **Wi-fi** > **エンタープライズ** >  **EAP の種類**)。 Windows Wi-fi プロファイルで PKCS 証明書を使用できるようになります。 この機能により、ユーザーはテナント内の新規または既存の PKCS 証明書プロファイルを使用して Wi-fi プロファイルを認証できます。 

Wi-fi プロファイルの詳細については、「 [Intune で Windows 10 以降のデバイスの wi-fi 設定を追加](../configuration/wi-fi-settings-windows.md)する」を参照してください。

適用対象:
- Windows 10 以降

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824----"></a>iOS デバイスでメール デバイス構成プロファイルを作成するときの新しい ExchangeActiveSync 設定<!-- 4892824  --> 
iOS および iPadOS デバイスにおいて、デバイス構成プロファイルでメール接続を構成できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS および iPadOS]** (プラットフォーム) > **[メール]** (プロファイルの種類))。 

次のような新しい ExchangeActiveSync 設定を使用できます。
- 電子メール、予定表、連絡先など、同期する (または同期をブロックする) サービスを選択します。
- デバイスでこれらのサービスの同期設定を変更することをユーザーに許可 (またはブロック) します。 

現在の設定を確認するには、「 [Intune で iOS デバイスの電子メールプロファイル設定](../configuration/email-settings-ios.md)」にアクセスしてください。

適用対象:
- iOS 13.0 以降
- iPadOS 13.0 以降

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices---5353228----"></a>Android Enterprise デバイス所有者および専用デバイスにユーザーが個人用 Google アカウントを追加できないようにする<!-- 5353228  -->
Android Enterprise デバイス所有者と専用デバイス上でユーザーが個人用 Google アカウントを作成できないようにすることができます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Android Enterprise]** (プラットフォーム) > **[デバイスの所有者のみ] > [デバイスの制限]** (プロファイルの種類) > **[ユーザーとアカウント] 設定**)。

現在構成できる設定を確認するには、「[Intune を使用して機能を許可または制限するように Android エンタープライズ デバイスを設定する](../configuration/device-restrictions-android-for-work.md)」をご覧ください。

適用対象:
- Android Enterprise デバイス所有者
- Android Enterprise 専用デバイス

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile---5468501----"></a>iOS デバイス制限プロファイルから Siri コマンド設定のサーバー側のログ記録が削除されます<!-- 5468501  -->
IOS デバイスでは、デバイスの制限プロファイルを作成して、Siri コマンドのサーバー側のログ記録を構成することができます (**デバイスの構成** > **プロファイル** >  > **iOS/Ipados**の**プロファイルを作成**し、プロファイル > の種類 >**組み込みアプリ**に対する**デバイスの制限**)。 **Siri コマンド設定のサーバー側のログ記録**が削除されます。

この設定は、Intune 管理コンソールから削除されます。 この設定が構成されている既存のポリシーでは引き続き設定が表示されますが、この設定はデバイスには影響しません。 既存のポリシーから設定を削除する場合は、ポリシーにアクセスし、軽微な編集を行って保存すると、ポリシーが更新されます。

構成できる設定を確認するには、「[Intune を使用した機能を許可または制限するための iOS および iPadOS デバイスの設定](../configuration/device-restrictions-ios.md)」をご覧ください。

適用対象:
- iOS

<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
<!--## Device management-->


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>監視とトラブルシューティング

### <a name="centralized-audit-logs--5603185-5697164--"></a>一元化された監査ログ<!--5603185, 5697164-->
新しい一元化された監査ログエクスペリエンスでは、すべてのカテゴリの監査ログが1ページに収集されます。 ログをフィルター処理して、探しているデータを取得できるようになります。 監査ログを表示するには、[**テナント管理** > **監査ログ**] にアクセスします。 詳細については、「 [Intune での監査ログの今後の変更」を](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Upcoming-change-to-Audit-logs-in-Intune/ba-p/1015858)参照してください。

<!-- ***********************************************-->
<!--## Role-based access control-->


<!-- ***********************************************-->

## <a name="security"></a>セキュリティ

### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529-idready---"></a>PKCS 証明書プロファイルを使用して、証明書を使用してデバイスをプロビジョニングする<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529 IDready -->
PKCS 証明書プロファイルを使用して、デバイスに証明書を発行することができます。これにより、ユーザーベースの証明書の現在のサポートが拡大されます。 デバイスベースの証明書は、Android、iOS、および Windows の各プラットフォームでサポートされ、Wi-fi および VPN プロファイルに使用できます。

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。


