---
title: Microsoft Intune の新機能 - Azure | Microsoft Docs
titlesuffix: ''
description: Intune Azure Portal の新機能を確認する
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/09/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 89264dbd2024b976d7c57278b188223679b33836
ms.sourcegitcommit: ae27c04a68ee893a5a6be4c56fe143263749a0d7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49169568"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune の新機能
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

週ごとにまとめた、Microsoft Intune の新機能をご覧ください。 [今後の変更](#whats-coming)、サービスに関する[重要なお知らせ](#notices)、[過去のリリース](whats-new-archive.md)に関する情報も確認できます。 いくつかの機能については、数週間にわたってロールアウトされ、一部のお客様は最初の週にご利用になれない可能性があります。

> [!Note]
> ハイブリッド モバイル デバイス管理 (MDM) での新機能については、[ハイブリッドの新機能に関するページ](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を確認してください。


<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->   

## <a name="week-of-october-1-2018"></a>2018 年 10 月 1 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>ポータル サイト アプリを使用したキーのプロファイル プロパティへのアクセス <!-- 772203 -->
エンド ユーザーがポータル サイト アプリからキー アカウントのプロパティと、パスワード リセットなどのアクションにアクセスできるようになりました。 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS でのアプリ設定によりサード パーティ製キーボードをブロックできる <!-- 1248481 -->
Intune 管理者は、iOS デバイスで、ポリシーによって保護されているアプリ内の組織データにアクセスするときのサード パーティ製キーボードの使用をブロックできます。 サード パーティ製キーボードをブロックするようにアプリケーション保護ポリシー (APP) が設定されていると、デバイス ユーザーは、サード パーティ製キーボードを使って初めて企業データを操作するときに、メッセージを受け取ります。 ネイティブ キーボード以外のすべてのオプションはブロックされ、デバイスのユーザーに表示されません。 デバイス ユーザーにこのダイアログ メッセージが表示されるのは 1 回だけです。 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>管理対象の Android デバイスと iOS デバイスでの Intune アプリのユーザー アカウント アクセス <!-- 1248496 -->
Microsoft Intune 管理者は、マネージド デバイス上の Microsoft Office アプリケーションにどのユーザー アカウントを追加するかを制御することができます。 許可されている組織ユーザー アカウントのみにアクセスを制限したり、登録済みデバイス上の個人アカウントをブロックしたりできます。 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>iOS と Android 向けの Outlook アプリの構成ポリシー <!--1828527 -->
基本認証と ActiveSync プロトコルを活用するオンプレミス ユーザーのために、iOS と Android 向けの Outlook アプリの構成ポリシーを作成できるようになりました。 追加の構成設定は iOS と Android 向けの Outlook に対して有効になったときに追加されます。

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 言語パック <!-- 1833450 -->
Intune 管理者は、Intune によって管理されている Office 365 Pro Plus アプリに追加の言語を展開することができます。 使用可能な言語のリストには、言語パックの **種類** (コア、部分、校正) が含まれます。 Azure Portal で、**[Microsoft Intune]** > **[クライアント アプリ]** > **[アプリ]** > **[追加]** の順に選びます。 **[アプリの追加]** ブレードの **[アプリの種類]** 一覧で、**[Office 365 スイート]** の **[Windows 10]** を選びます。 **[アプリ スイートの設定]** ブレードで **[言語]** を選びます。

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Windows 基幹業務 (LOB) アプリのファイル拡張子 <!-- 1884873 -->
Windows LOB アプリのファイル拡張子に、*.msi*、*.appx*、*.appxbundle*、*.msix* および *.msixbundle* が含まれるようになりました。 Microsoft Intune にアプリを追加するには、**[クライアント アプリ]** > **[アプリ]** > **[追加]** の順に選択します。 **[アプリの追加]** ウィンドウが表示され、そこで **[アプリの種類]** を選択できます。 Windows LOB アプリの場合は、アプリの種類として **[基幹業務]** アプリを選び、**[アプリのパッケージ ファイル]** を選択して、適切な拡張子を持つインストール ファイルを入力します。

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Intune を使用する Windows 10 アプリの展開 <!-- 2309001 -->
管理者は Intune を利用することで、基幹業務 (LOB) と Microsoft Store for Business アプリの既存サポートを基盤に、組織の既存アプリケーションの多くを Windows 10 デバイスのエンド ユーザーにデプロイできます。 管理者は、MSI、Setup.exe、MSP など、さまざまな形式で Windows 10 ユーザー用のアプリケーションを追加、インストール、アンインストールできます。 Intune は要件ルールを評価してからダウンロードとインストールを開始し、Windows 10 Action Center を利用して状態や再起動の必要性をエンド ユーザーに通知します。 この機能によって、このワークロードを Intune やクラウドに移行することに関心がある組織に対してブロックが効果的に解除されます。 この機能は現在パブリック プレビューの段階にあり、これから数か月の間に重要な新機能を追加する予定です。 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>エンド ユーザー デバイスとアプリのコンテンツのメニュー <!-- 2771453 -->
エンド ユーザーはデバイス上のコンテキスト メニューとアプリを使用して、デバイスの名前変更、準拠状況の確認などの一般的なアクションをトリガーできるようになりました。 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Windows ポータル サイトのキーボード ショートカット <!-- 2771518 -->
エンドユーザーは、Windows ポータル サイトでキーボード ショートカット (アクセラレータ) を使用してアプリとデバイスのアクションをトリガーできるようになりました。

### <a name="device-configuration"></a>デバイス構成

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Windows 10 を実行するデバイスの VPN 構成プロファイルで DNS サフィックスを作成する<!-- 1333668 -->
VPN デバイス構成プロファイルを作成するとき (**[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択し、プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[VPN]** を選択します)、DNS 設定を入力します。 この更新プログラムでは、Intune で **DNS サフィックス**を複数入力することもできるようになりました。 DNS サフィックスを使用する場合は、完全修飾ドメイン名 (FQDN) ではなく、短い名前を使用してネットワーク リソースを検索できます。 この更新プログラムでは、Intune で DNS サフィックスの順序を変更することもできます。
[Windows 10 VPN 設定](vpn-settings-windows-10.md#dns-settings)によって、現在の DNS 設定が一覧表示されます。
適用: Windows 10 デバイス

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Android エンタープライズ作業プロファイル向けの常時 VPN のサポート <!-- 1333705 -->
この更新プログラムでは、管理対象の作業プロファイルが与えられた Android エンタープライズ デバイスで常時 VPN 接続を使用できます。 常時 VPN 接続では接続状態が常に維持されるか、ユーザーが自分のデバイスをロックしたとき、デバイスが再起動したとき、ワイヤレス ネットワークに変更があったとき、すぐに再接続されます。 接続を "ロックダウン" モードにすることもできます。このモードでは、VPN 接続が有効になるまですべてのネットワーク トラフィックがブロックされます。
**[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択し、プラットフォームに **[Android エンタープライズ]** を選択し、**[デバイスの制限]** を選択し、設定に **[接続]** を選択することで常時 VPN を有効にできます。

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>ユーザーのいないデバイスに SCEP 証明書を発行する <!-- 1744554 -->
現在のところ、証明書はユーザーに発行されます。 この更新プログラムでは、キオスクのようなユーザーのいないデバイスも含め、デバイスに SCEP 証明書を発行できます (**[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択し、プラットフォームに **[Windows 10 以降]** を選択し、プロファイルに **[SCEP 証明書]** を選択します)。 その他の更新プログラム:
- SCEP プロファイルの**サブジェクト** プロパティがカスタム テキストボックスになり、新しい変数を含めることができます。 
- SCEP プロファイルの**サブジェクト代替名 (SAN)** プロパティが表形式になり、新しい変数を含めることができます。 この表では、管理者は属性を追加し、カスタム テキストボックスに値を入力できます。 SAN では次の属性がサポートされます。 
  - DNS
  - 電子メール アドレス
  - UPN

  これらの新しい変数は、カスタム値ボックスに静的テキストで追加できます。 たとえば、`DNS = {{AzureADDeviceId}}.domain.com` という DNS 属性を追加できます。

  > [!NOTE]
  > SAN の静的テキストの場合、中かっこ { }、セミコロン ;、パイプ記号 | は使用できません。 `Subject` または `Subject alternative name` に受け取らせるには、中かっこで囲む新しいデバイスの証明書変数を 1 つに限る必要があります。 

新しいデバイスの証明書変数:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` は Windows とドメインに参加しているデバイスでのみ機能します。 
>  -  サブジェクトまたは SAN の IMEI、シリアル番号、完全修飾ドメイン名などのデバイスのプロパティをデバイス証明書に指定する場合、これらのプロパティは、デバイスにアクセスできる人物が偽装する可能性があることに注意してください。 

[[SCEP 証明書プロファイルを作成する]](certificates-scep-configure.md#create-a-scep-certificate-profile) には、SCEP 構成プロファイルの作成時、現在の変数が一覧表示されます。 

適用対象: Windows 10 以降と iOS、Wi-Fi でサポート。

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>非準拠デバイスのリモート ロック <!-- 2064495 -->
デバイスが非準拠のとき、そのデバイスをリモートでロックするアクションをコンプライアンス ポリシーで作成できます。 Intune で **[デバイスのポリシー準拠]** を選択して新しいポリシーを作成するか、既存のポリシーを選択し、**[プロパティ]** を選択します。 **[コンプライアンス非対応に対するアクション]**、**[追加]** の順に選択し、デバイスのリモート ロックを選択します。
サポート対象: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 以降 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Azure portal で Windows 10 以降のキオスク プロファイルを改善 <!-- 2748224 -->
この更新プログラムでは、Windows 10 キオスク デバイスの構成プロファイルが次のように改善されています (**[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択し、プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[キオスク プレビュー]** を選択します)。 
- 現在のところ、同じデバイスで複数のキオスク プロファイルを作成できます。 この更新プログラムで Intune はデバイスあたりキオスク プロファイルを 1 つだけサポートするようになります。 1 台のデバイスに複数のキオスク プロファイルが必要な場合は、カスタム URI を使用できます。
- **マルチアプリ キオスク** プロファイルでは、アプリケーション グリッドの**スタート メニュー レイアウト**でアプリケーション タイルのサイズと順序を選択できます。 さらにカスタマイズする場合、続けて XML ファイルをアップロードできます。
- キオスク ブラウザーの設定が**キオスク**設定に移動します。 現在のところ、Azure portal には**キオスク Web ブラウザー**設定に独自のカテゴリがあります。
適用対象: Windows 10 以降




### <a name="device-enrollment"></a>デバイスの登録

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Autopilot に関してまだ登録されていない登録 Win 10 デバイスに Autopilo プロファイルを適用する <!-- 1558983 -->
Autopilot に関してまだ登録されていない登録 Win 10 デバイスに Autopilo プロファイルを適用できます。 Autopilot プロファイルで **[すべての対象デバイスを Autopilot に変換する]** オプションを選択し、非 Autopilot デバイスを Autopilot デプロイ サービスに自動登録します。 登録が処理されるまで 48 時間待ちます。 デバイスが登録解除されリセットされると、Autopilot によってそのデバイスがプロビジョニングされます。

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>登録ステータス ページ プロファイルを複数作成し、Azure AD グループに割り当てる <!-- 2526564 -->
登録ステータス ページ プロファイルを複数[作成し、Azure AD グループに割り当てる](windows-enrollment-status.md)ことができるようになりました。

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Intune で Device Enrollment Program から Apple Business Manager に移行する <!--2748613-->
Apple Business Manager (ABM) は Intune で動作します。Device Enrollment Program (DEP) から ABM にアカウントをアップグレードできます。 Intune でのプロセスは同じです。 DEP から ABM に Apple をアップグレードするには、[ https://support.apple.com/en-us/HT208817]( https://support.apple.com/en-us/HT208817) に移動します。

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>デバイス登録概要ページのアラートと登録ステータスのタブ <!--2748656-->
デバイス登録概要ページでは、アラートや登録エラーが別々のタブに表示されるようになりました。

### <a name="device-management"></a>デバイス管理

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Android デバイスでアプリを制限し、会社のリソースへのアクセスをブロックする <!-- 2451462  -->  
**[デバイス コンプライアンス]**、**[ポリシー]**、**[ポリシーの作成]**、**[Android]**、**[システム セキュリティ]** の順に選択すると、*[デバイス セキュリティ]* セクションの下に **[制限付きアプリ]** という新しい設定が表示されます。 **[制限付きアプリ]** 設定ではコンプライアンス ポリシーが使用され、特定のアプリがデバイスにインストールされている場合、会社のリソースへのアクセスがブロックされます。 制限付きアプリケーションがデバイスから削除されるまで、デバイスは非準拠と見なされます。
適用先: 
- Android




## <a name="week-of-september-24-2018"></a>2018 年 9 月 24 日の週

### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Microsoft 365 デバイス管理の管理センター <!-- 3078424 -->
Microsoft 365 で Microsoft が約束することの 1 つは簡単な管理です。長年、Intune や Azure AD 条件付きアクセスなどのエンドツーエンド シナリオを届けるべく、Microsoft はバックエンド Microsoft 365 サービスを統合してきました。 新しい [Microsoft 365 管理センター](http://devicemanagement.microsoft.com)は、管理業務を連結、簡素化、統合する場所です。 デバイス管理のスペシャリスト向けワークスペースでは、組織で必要とされるあらゆるデバイス/アプリ管理情報/作業に簡単にアクセスできます。 企業のエンドユーザー コンピューティング チームにとってはこれが主要なクラウド ワークスペースになるものと Microsoft は予想しています。

### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>サードパーティ証明書機関 (CA) のサポート追加 <!-- 3093107 -->
Simple Certificate Enrollment Protocol (SCEP) を利用することで、Windows、iOS、Android、macOS を搭載するモバイル デバイスで新しい証明書を発行したり、証明書を更新したりできるようになりました。

### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>Intune サポートが iOS 10 以降に <!-- 2454656 -->  
今後、Intune の登録、ポータル サイト、Managed Browser は iOS 10 以降を搭載して iOS デバイスのみでサポートされます。 組織で影響を受けるデバイスやユーザーを確認するには、Azure portal で Intune にアクセスし、**[デバイス]**、**[すべてのデバイス]** の順に選択します。 OS で絞り込み、**[列]** をクリックして OS バージョン詳細を表示します。 サポートされている OS バージョンにデバイスをアップグレードするようにユーザーに依頼します。  

以下に一覧したデバイスのいずれかを所有している場合、または以下に一覧したデバイスのいずれかを登録する場合、それらのデバイスは iOS 9 以前しかサポートしていないので注意してください。  Intune ポータル サイトに引き続きアクセスするには、iOS 10 以降をサポートするデバイスにそれらのデバイスをアップグレードする必要があります。  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (第 3 世代) 
* iPad Mini (第 1 世代)  

## <a name="week-of-september-17-2018"></a>2018 年 9 月 17 日の週

### <a name="app-management"></a>アプリ管理

### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>アプリ保護ステータス タイルの重複削除 <!-- 3083391 -->
**[iOS のユーザーの状態]** タイルと **[Android のユーザーの状態]** タイルは、**[クライアント アプリ - 概要]** ページと **[クライアント アプリ - アプリ保護ステータス]** ページの両方に表示されていました。 重複を避けるために、**[クライアント アプリ - 概要]** ページからステータス タイルが削除されました。 

## <a name="week-of-august-27-2018"></a>2018 年 8 月 27 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>接続の種類がカスタムと Pulse Secure の場合における、iOS のアプリごとの VPN プロファイルに対するパケット トンネル サポート <!-- 1520957 -->
iOS のアプリごとの VPN プロファイルを使用するときに、アプリ層トンネリング (アプリプロキシ) またはパケット レベル トンネリング (パケットトンネル) を使用することを選択できます。 これらのオプションは、次の接続の種類で利用できます。
- カスタム VPN
- Pulse Secure: 使用する値がわからない場合、ご利用の VPN プロバイダーのドキュメントを参照してください。

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>iOS ソフトウェア更新がデバイスに表示されるときの遅延 <!-- 1949583 -->
Intune の **[ソフトウェアの更新]** の **[iOS のポリシーを更新する]** で、デバイスにあらゆる更新プログラムをインストールしない日時を構成できます。 今後の更新では、1 日から 90 日までの間で、ソフトウェア更新が表示されるタイミングを遅らせることができるようになります。 
[こちら](software-updates-ios.md)に Microsoft Intune で iOS 更新ポリシーを構成する方法が説明されていますが、ここに現在の設定が一覧になっています。

#### <a name="office-365-proplus-version----2213968---"></a>Office 365 ProPlus バージョン <!-- 2213968 -->
Intune を利用して Office 365 ProPlus アプリを Windows 10 デバイスに割り当てるとき、Office のバージョンを選択できるようになります。 Azure portal で、**[Microsoft Intune]**、**[アプリ]**、**[アプリの追加]** の順に選択します。 次に、**[種類]** ドロップダウン リストから **[Office 365 ProPlus Suite (Windows 10)]** を選択します。 **[アプリ スイートの設定]** を選択し、関連ブレードを表示します。 **[更新チャネル]** を **[毎月]** などの値に設定します。 任意で、**[はい]** を選択し、エンド ユーザー デバイスから Office のその他のバージョン (msi) を削除します。 **[特定]** を選択すると、選択されているチャネルで特定のバージョンの Office がエンド ユーザー デバイスにインストールされます。 この時点で、使用する**特定のバージョン**の Office を選択できます。 使用できるバージョンは随時変更されます。 そのため、新しいデプロイを作成するとき、利用できるバージョンが新しく、特定の古いバージョンを利用できないことがあります。 現在のデプロイでは引き続き古いバージョンをデプロイできますが、バージョンの一覧はチャネル単位で継続的に更新されます。 詳細については、「[Office 365 ProPlus 更新プログラム チャネルの概要](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)」をご覧ください。

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Windows 10 VPN の DNS 登録設定をサポート <!-- 2282852 -->
この更新では、カスタム プロファイルを使用しなくても、内部 DNS を使用し、VPN インターフェイスに割り当てられている IP アドレスを動的に登録するように、Windows 10 VPN プロファイルを構成できるようになります。
現在の VPN プロファイルの設定に関する詳細については、「[Intune での Windows 10 VPN の設定](vpn-settings-windows-10.md)」を参照してください。 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>macOS ポータル インストーラーはインストーラー ファイル名にバージョン番号を含む <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759-wnready---"></a>iOS のアプリの自動更新 <!-- 2729759 wnready -->
アプリの自動更新は、iOS バージョン 11.0 以上のデバイスとユーザー ライセンスされたアプリの両方で機能します。




### <a name="device-configuration"></a>デバイス構成

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello の対象はユーザーとデバイスになります <!-- 1106609 -->
[Windows Hello for Business](windows-hello.md) ポリシーを作成すると、そのポリシーは組織内 (テナント全体) のすべてのユーザーに適用されます。 今回の更新によって、デバイス構成ポリシーを使用する特定のユーザーまたは特定のデバイスにもポリシーを適用できるようになりました (**[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]**、**[ID 保護]**、**[Windows Hello for Business]**)。
Azure portal の Intune では、Windows Hello の構成と設定は、**[デバイスの登録]** と **[デバイス構成]** の両方に存在するようになりました。 **[デバイスの登録]** の対象は組織全体 (テナント全体) であり、Windows AutoPilot (OOBE) がサポートされます。 **[デバイス構成]** の対象は、チェックイン中に適用されたポリシーを使用するデバイスとユーザーになります。
この機能は、以下に適用されます。  
- Windows 10 以降
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>iOS の VPN プロファイルには、Zscaler を接続として利用可能 <!-- 1769858 -->
iOS VPN デバイス構成プロファイルを作成するとき (**[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択し、プラットフォームに **iOS** を選択し、プロファイルの種類に **VPN** を選択する)、Cisco や Citrix など、接続の種類がいくつかあります。 この更新では、接続の種類として Zscaler が追加されます。 
[こちらの](vpn-settings-ios.md)iOS を実行するデバイスの VPN 設定リストには、利用できる接続の種類がまとめられています。

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>Windows 10 用の Enterprise Wi-Fi プロファイルに対する FIPS モード <!-- 1879077 -->
Intune Azure portal 内の Windows 10 用の Enterprise Wi-Fi プロファイルに対して、Federal Information Processing Standards (FIPS) モードを有効にできるようになりました。 Wi-Fi プロファイルで有効にする場合は、ご使用の Wi-Fi インフラストラクチャで FIPS モードを有効にしていることを確認してください。
「[Intune での Windows 10 以降のデバイス向けの Wi-Fi 設定](wi-fi-settings-windows.md)」では、Wi-Fi プロファイルを作成する方法について示します。

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Windows 10 以降のデバイスで S モードを制御する - パブリック プレビュー <!-- 1958649 -->
この機能更新プログラムでは、Windows 10 デバイスの S モードを解除するデバイス構成プロファイルを作成したり、ユーザーがデバイスの S モードを解除することを禁止したりできます。 この機能は Intune の **[デバイス構成]** > **[プロファイル]** >  **[Windows 10 以降]** > **[Edition upgrade and mode switch]\(エディション アップグレードとモード切替\)** にあります。
S モードの詳細は「[Windows 10 (S モード) について](https://www.microsoft.com/windows/s-mode)」でご覧いただけます。
適用対象: 一番新しい [Windows Insider](https://docs.microsoft.com/en-us/windows-insider/at-work-pro/) ビルド (プレビュー段階)。


#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>構成プロファイルに自動的に追加される Windows Defender ATP 構成パッケージ <!-- 2144658 -->
Intune で [Advanced Threat Protection を使用してデバイスをオンボードする](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile)場合、前もって構成パッケージをダウンロードし、それを構成プロファイルに追加する必要があります。 この更新では、Intune で Windows Defender Security Center からパッケージを自動的に取得し、それをプロファイルに追加します。
Windows 10 以降に適用されます。

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>デバイスのセットアップ中に接続するためのユーザーが必要 <!--2311457-->
Windows 10 のセットアップ中にネットワーク ページから進む前に、デバイスがネットワークに接続することを要求するように、デバイス プロファイルを設定できるようになりました。 この機能はプレビュー中ですが、Windows Insider ビルド 1809 以降ではこの設定を使用する必要があります。
適用対象: 一番新しい [Windows Insider](https://docs.microsoft.com/en-us/windows-insider/at-work-pro/) ビルド (プレビュー段階)。


#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>iOS デバイスと Android エンタープライズ デバイスでアプリを制限し、会社のリソースへのアクセスをブロックする <!-- 2451462 -->
**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[iOS]** > **[システム セキュリティ]** の順に選択したところに、**制限付きアプリケーション**の新しい設定があります。 この新しい設定ではコンプライアンス ポリシーが使用され、特定のアプリがデバイスにインストールされている場合、会社のリソースへのアクセスがブロックされます。 制限付きアプリケーションがデバイスから削除されるまで、デバイスは非準拠と見なされます。
適用対象: iOS

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>最新の VPN サポートの更新で iOS に対応 <!-- 2459928, 1819876, and 2650856 -->
この更新では、次の iOS VPN クライアントがサポート対象になります。 
- F5 Access (バージョン 3.0.1 以降)
- Citrix SSO
- Palo Alto Networks GlobalProtect バージョン 5.0 以降。この更新では以下もサポートされます。
- 既存の **F5 Access** の接続の種類は、iOS 用の **F5 Access Legacy** という名前に変更されました。
- 既存の **Palo Alto Networks GlobalProtect** の接続の種類の名前は、iOS 用の **Palo Alto Networks GlobalProtect (Legacy)** に変更されます。
これらの接続の種類を持つ既存のプロファイルは、引き続きそれぞれのレガシ VPN クライアントで動作します。 Cisco Legacy AnyConnect、F5 Access Legacy、Citrix VPN、または Palo Alto Networks GlobalProtect バージョン 4.1 以前を iOS で使用している場合、新しいアプリに移ってください。 iOS 12 に更新されたときに iOS デバイスで VPN アクセスを利用できるように、できるだけ速やかに移ってください。
iOS 12 と VPN プロファイルの詳細については、[Microsoft Intune サポート チームのブログ](https://go.microsoft.com/fwlink/?linkid=2013806)に関するページを参照してください。

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>Azure クラシック ポータルのコンプライアンス ポリシーをエクスポートして、Intune Azure portal でこれらのポリシーを再作成する <!-- 2469637 -->
Azure クラシック ポータルで作成されたコンプライアンス ポリシーは非推奨になる予定です。 既存のコンプライアンス ポリシーは確認したり、削除したりできますが、更新することはできません。 現在の Intune Azure portal に任意のコンプライアンス ポリシーを移行する必要がある場合は、コンマ区切りファイル (*.csv* ファイル) としてポリシーをエクスポートできます。 その後、ファイルの詳細を使って、Intune Azure portal でこれらのポリシーを再作成します。

> [!IMPORTANT]
> Azure クラシック ポータルが廃止されると、ご自分のコンプライアンス ポリシーにアクセスしたり、表示したりすることはできなくなります。 そのため、Azure クラシック ポータルが廃止される前に、必ずご利用のポリシーをエクスポートし、Azure portal で再作成してください。

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile - 新しい Mobile Threat Defense パートナー <!-- 22662717 -->
Microsoft Intune に統合された Mobile Threat Defense ソリューションである Better Mobile によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>ユーザーがサインインするまで、シングル アプリ モードでポータル サイトをロックする <!--1067692 --> 
DEP 登録中、セットアップ アシスタントの代わりに、ポータル サイトを介してユーザーを認証する場合、シングル アプリ モードでポータル サイトを実行するオプションを使用できるようになりました。 このオプションによってセットアップ アシスタントの完了直後にデバイスがロックされます。そのため、デバイスを利用するには、ユーザーはサインインする必要があります。 このプロセスにより、デバイスはオンボードを完了し、ユーザーが関連付けられていない状態で孤立することはありません。

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Autopilot デバイスにユーザーとわかりやすい名前を割り当てる <!--1346521 -->
[ユーザーを 1 つの Autopilot デバイスに割り当てる](enrollment-autopilot.md)ことができるようになりました。 管理者はまた、AutoPilot でデバイスを設定するユーザーにとってわかりやすい名前を与えることができます。
適用対象: 一番新しい [Windows Insider](https://docs.microsoft.com/en-us/windows-insider/at-work-pro/) ビルド (プレビュー段階)。

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>VPP デバイス ライセンスを使用して DEP 登録時にポータル サイトを事前プロビジョニングする <!-- 1608345 -->
Volume Purchase Program (VPP) デバイス ライセンスを使用して、Device Enrollment Program (DEP) 登録時にポータル サイトを事前プロビジョニングすることができます。 そのためには、[登録プロファイルを作成または編集する](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)ときに、ポータル サイトをインストールするために使用する VPP トークンを指定します。 トークンの期限が切れていないことと、ポータル サイト アプリの十分なライセンスがあることを確認してください。 トークンの期限が切れているか、ライセンスが不足している場合、Intune は代わりに App Store ポータル サイトをプッシュします (この場合、Apple ID の入力が求められます)。

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>ポータル サイトの事前プロビジョニングに使用されている VPP トークンを削除するために必要な構成 <!-- 2237634 -->
DEP 登録時にポータル サイトの事前プロビジョニングに Volume Purchase Program (VPP) トークンが使用されている場合、そのトークンを削除するための構成が必要になりました。

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Windows 個人デバイス登録を禁止する <!-- 1849498 -->
Intune の[モバイル デバイス管理](windows-enroll.md)で [Windows 個人デバイスの登録を禁止](enrollment-restrictions-set.md#set-device-type-restrictions)できます。 [Intune PC エージェント](manage-windows-pcs-with-microsoft-intune.md)で登録されているデバイスはこの機能でブロックできません。 この機能は次の数週間でロールアウトされます。そのため、ユーザー インターフェイスにはすぐに表示されないことがあります。

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Autopilot プロファイルにコンピューター名パターンを指定する <!--1849855-->
Autopilot の登録時に、生成する[コンピューター名テンプレートを指定](enrollment-autopilot.md#create-an-autopilot-deployment-profile)したり、[コンピューター名](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)を設定したりできます。 適用対象: 一番新しい [Windows Insider](https://docs.microsoft.com/en-us/windows-insider/at-work-pro/) ビルド (プレビュー段階)。


#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Windows Autopilot プロファイルの場合、会社のサインイン ページとドメイン エラー ページでアカウント変更オプションを非表示にする <!--1901669 -->
会社のサインイン ページとドメイン エラー ページでアカウント変更オプションを管理者が非表示にするための[新しい Windows Autopilot プロファイル オプション](enrollment-autopilot.md#create-an-autopilot-deployment-profile)があります。 これらのオプションを非表示にするには、Azure Active Directory で会社のブランドを構成する必要があります。 適用対象: 一番新しい [Windows Insider](https://docs.microsoft.com/en-us/windows-insider/at-work-pro/) ビルド (プレビュー段階)。



### <a name="device-management"></a>デバイス管理

#### <a name="delete-jamf-devices----2653306--"></a>Jamf デバイスを削除する <!-- 2653306-->
**[デバイス]** に移動し、Jamf デバイスを選択して、**[削除]** を選択することにより、Jamf で管理されたデバイスを削除できます。

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>"削除" と "ワイプ" への用語変更 <!-- 2175759 -->
Graph API との一貫性を保つために、Intune のユーザー インターフェイスとドキュメントにおいて次の用語が変更されています。
- **[会社データの削除]** は、"廃止" に変更されます
- **[出荷時の設定にリセット]** は **[ワイプ]** に変更されます

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>管理者が MDM プッシュ通知証明書を削除しようとする場合の確認ダイアログ <!-- 297909500-->
任意のユーザーが Apple MDM プッシュ通知証明書を削除しようとすると、確認ダイアログ ボックスには関連する iOS と macOS デバイスの数が表示されます。 証明書が削除された場合、これらのデバイスは再登録される必要があります。

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Windows インストーラーの追加のセキュリティ設定 <!-- 2282430 -->
ユーザーがアプリのインストールを制御することを許可できます。 有効にすると、セキュリティ違反が原因で本来は停止される可能性があるインストールを続行することが許可されます。 Windows インストーラーによってシステムに任意のプログラムをインストールする場合、管理者特権のアクセス許可を使用するよう Windows インストーラーに指示することができます。 さらに、Windows 情報保護 (WIP) アイテムのインデックス付け、および暗号化されていない場所に格納されたそれらのアイテムに関するメタデータを有効にすることができます。 このポリシーが無効な場合、WIP で保護されたアイテムにはインデックスが付けられず、Cortana またはエクスプローラーの結果に表示されません。 既定では、これらのオプションの機能は無効になっています。 

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>ポータル Web サイトの新しいユーザー エクスペリエンスの更新<!--2000968 -->
顧客からのフィードバックに基づいて、Intune ポータル サイト Web サイトに新機能を追加しています。 ご利用のデバイスから、既存の機能と使いやすさの大幅な向上を体験できます。 &ndash;デバイス詳細、フィードバックとサポート、デバイス概要など&ndash;のサイトの領域には、最新の応答性の高いデザインが採用されています。 また、次のような更新が行われています。

- すべてのデバイス プラットフォームでの簡素化されたワークフロー
- 強化されたデバイスの識別と登録のフロー
- 役に立つエラー メッセージ
- 技術的な専門用語を減らした、わかりやすい言語
- アプリへの直接リンクを共有する機能
- 大規模なアプリケーション カタログのパフォーマンスの向上
- すべてのユーザーに対するアクセシビリティの向上  

[Intune ポータル サイト Web サイトのドキュメント](https://docs.microsoft.com/en-us/intune-user-help/using-the-intune-company-portal-website)は、これらの変更を反映するように更新されています。 アプリの拡張機能の例を表示するには、「[Intune とエンド ユーザー アプリの UI の更新](whats-new-app-ui.md)」を参照してください。  

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>コンプライアンス レポートでの脱獄の高度な検出 <!-- 2198738 -->
脱獄の高度な検出の設定の状態は、管理コンソール内のすべてのコンプライアンス レポートに表示されるようになりました。

### <a name="role-based-access-control"></a>ロールベースのアクセス制御

#### <a name="scope-tags-for-policies---1081974---"></a>ポリシーのスコープ タグ <!--1081974 -->
Intune リソースへのアクセスを制限するために、[スコープのタグを作成](scope-tags.md)できます。 スコープ タグをロールの割り当てに追加し、同じスコープ タグを構成プロファイルに追加します。 そのロールでは、スコープ タグが一致する (あるいはスコープ タグがない) 構成プロファイルを持つリソースにのみアクセスできます。

## <a name="week-of-august-14-2018"></a>2018 年 8 月 14 日の週

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Apple Device Enrollment Program の macOS によるサポート <!-- 747651 -->
Intune は、Apple Device Enrollment Program (DEP) への macOS デバイスの登録をサポートするようになりました。 詳細については、「[Apple の Device Enrollment Program を使用して macOS デバイスを自動登録する](device-enrollment-program-enroll-macos.md)」を参照してください。

## <a name="week-of-july-23-2018"></a>2018 年 7 月 23 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>macOS の基幹業務 (LOB) アプリのサポート <!-- 1895847 -->
Microsoft Intune では、macOS LOB アプリを **[必須]** として、または **[Available with enrollment]\(登録して利用可能\)** として展開することができます。 エンド ユーザーは、macOS 用のポータル サイトまたは[ポータル サイト Web サイト](https://portal.manage.microsoft.com)を使用して、アプリを **[利用可能]** として展開してもらうことができます。

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>キオスク モードに対応する iOS 組み込みアプリのサポート <!-- 2051098 -->
ストア アプリおよび管理対象アプリに加えて、iOS デバイス上でキオスク モードで実行される組み込みアプリ (Safari など) を選択できるようになりました。

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Office 365 Pro Plus アプリの展開を編集する <!-- 2150145 -->
Microsoft Intune 管理者は、Office 365 Pro Plus アプリのデプロイを編集するための強化された機能を使用できます。 さらに、スイートのいずれかのプロパティを変更するのに、デプロイを削除しなくてもよくなりました。 Azure portal で、**[Microsoft Intune]** > **[クライアント アプリ]** > **[アプリ]** の順に選択します。 アプリの一覧から、Office 365 Pro Plus スイートを選択します。  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>更新された Android 用 Intune アプリ SDK が使用可能 <!-- 2744271-->

Android P のリリースをサポートする Android 用 Intune アプリ SDK の更新バージョンが使用可能になりました。 Android 用 Intune SDK を使用しているアプリ開発者は、Intune アプリ SDK の更新バージョンをインストールして、Android P デバイス上でも Android アプリの Intune 機能が正常に動作するようにする必要があります。 このバージョンの Intune アプリ SDK には、SDK の更新を実行する組み込みのプラグインが用意されています。 統合されている既存のコードを書き直す必要はありません。 詳細については、[Android 用 Intune SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-android) に関するページをご覧ください。 Intune に対して古いバッジのスタイルを使用している場合は、ブリーフケース アイコンを使用することをお勧めします。 ブランド化について詳しくは、[この GitHub リポジトリ](https://github.com/msintuneappsdk/intune-app-partner-badge)をご覧ください。


### <a name="device-configuration"></a>デバイス構成

#### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>S/MIME を使用して暗号化し、ユーザーの複数のデバイスに署名する <!-- 1333642 -->
この更新プログラムには、新しくインポートされる証明書プロファイル (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]**、該当するプラットフォーム、**[PKCS のインポートされた証明書]** プロファイルの種類の順に選択) を使用する S/MIME メールの暗号化が含まれます。 Intune では、PFX 形式で証明書をインポートできます。 その後、Intune はその同じ証明書を、単一ユーザーによって登録された複数のデバイスに配信できます。 これには、次のものも含まれます。

- ネイティブ iOS メール プロファイルでは、PFX 形式でインポートされた証明書を使用する S/MIME 暗号化を有効にすることができます。
- Windows Phone 10 デバイス上のネイティブ メール アプリでは、自動的に S/MIME 証明書が使用されます。
- プライベート証明書は複数のプラットフォームに配信できます。 しかし、すべてのメール アプリで S/MIME がサポートされるわけではありません。
- 他のプラットフォームでは、S/MIME を有効にするようにメール アプリを手動で構成する必要がある場合があります。  
- S/MIME 暗号化をサポートするメール アプリでは、発行元の証明書ストアからの読み取りなど、MDM ではサポートできない方法で S/MIME メール暗号化のための証明書の検索を処理する場合があります。

サポート対象: Windows、Windows Phone 10、macOS、iOS、Android

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>macOS デバイスでファイアウォール設定を使ってデバイスのコンプライアンス ポリシーを作成する <!-- 1497640 -->
macOS の新しいコンプライアンス ポリシーを作成するとき (**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[プラットフォーム: macOS]** > **[システム セキュリティ]**)、**ファイアウォール**に関するいくつかの新しい設定を使用できます。 

- **[ファイアウォール]**: ご利用の環境における着信接続の処理方法を構成します。
- **[着信接続]**: DHCP、Bonjour、IPSec など、基本的なインターネット サービスに必要な接続を除き、すべての着信接続を **[ブロック]** します。 この設定は、すべての共有サービスもブロックします。
- **[ステルス モード]**: ステルス モードを **[有効]** にして、デバイスがプローブ要求に応答するのを防ぎます。 デバイスは引き続き、許可されているアプリに関する着信要求に応答します。

適用対象: macOS 10.12 以降

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Windows 10 以降用の新しい Wi-Fi デバイス構成プロファイル <!-- 1879077 -->
現時点では、XML ファイルを使用して、Wi-Fi プロファイルをインポートおよびエクスポートすることができます。 この更新プログラムを使用すると、他のプラットフォームの場合と同じように、Intune で直接 Wi-Fi デバイス構成プロファイルを作成できるようになります。

プロファイルを作成するには、**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[Windows 10 以降]** > **[Wi-Fi]** の順に開きます。 

Windows 10 以降に適用されます。

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>[Kiosk - obsolete]\(キオスク - 古い) が灰色で表示され、変更できない <!-- 2149998 -->
[キオスクの機能](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[Windows 10 以降]** > **[デバイスの制限]**) は使用されなくなり、[Windows 10 以降用のキオスク設定](kiosk-settings.md)に置き換えられます。 この更新プログラムを使用すると、**[Kiosk - Obsolete]\(キオスク - 古い)** 機能は灰色で表示され、ユーザー インターフェイスの変更や更新はできません。 

キオスク モードを有効にする場合は、[Windows 10 以降用のキオスクの設定](kiosk-settings.md)に関するページを参照してください。

Windows 10 以降、Windows Holographic for Business に適用されます

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>サード パーティ証明機関を使用する API <!-- 2184013 -->
この更新プログラムでは、Java API でサード パーティ証明機関を使用して、Intune と SCEP を統合できるようになります。 その後、ユーザーは SCEP 証明書をプロファイルに追加し、MDM を使用してデバイスに適用できます。

現時点では、Intune で [Active Directory 証明書サービスを使用する SCEP 要求](certificates-scep-configure.md)がサポートされています。

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>キオスク ブラウザーで [セッションの終了] ボタンの表示と非表示を切り替える <!-- 2455253 -->
キオスク ブラウザーに [セッションの終了] ボタンを表示するかどうかを構成できるようになりました。 コントロールは **[デバイス構成]** > **[キオスク (プレビュー)]** > **[キオスク Web ブラウザー]** で表示できます。 有効にした場合、ユーザーがボタンをクリックしたときに、アプリでセッションを終了するための構成が求められます。 確認すると、ブラウザーで閲覧データがすべてクリアされ、既定の URL に戻ります。

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>eSIM 携帯電話の構成プロファイルの作成 <!-- 2564077 -->
**[デバイス構成]** では、eSIM 携帯電話のプロファイルを作成することができます。 携帯電話会社によって提供される携帯電話のアクティブ化コードを含むファイルをインポートできます。 その後、これらのプロファイルを、Surface Pro LTE やその他の eSIM 対応デバイスなど、eSIM LTE を有効にした Windows 10 デバイスに展開することができます。

ご利用の[デバイスで eSIM プロファイルがサポートされている](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)かどうかを確認してください。

Windows 10 以降に適用されます。 




### <a name="device-enrollment"></a>デバイスの登録

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Samsung Knox Mobile Enrollment を使用して登録された Android デバイスを自動的に "企業" としてマークする。 <!-- 2404851 -->
既定で、Samsung Knox Mobile Enrollment を使用して登録された Android デバイスは、**[デバイスの所有権]** に**企業**としてマークされるようになりました。 Knox Mobile Enrollment を使用して登録する前に、IMEI やシリアル番号を使って企業のデバイスを手動で特定する必要はありません。

### <a name="device-management"></a>デバイス管理

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>デバイス ブレードでのデバイスの一括削除 <!-- 1793693 -->

[デバイス] ブレードでは、一度に複数のデバイスを削除できるようになりました。 **[デバイス]** > **[すべてのデバイス]**、削除するデバイス、**[削除]** の順に選択します。 削除できないデバイスについては、アラートが表示されます。

## <a name="week-of-july-16-2018"></a>2018 年 7 月 16 日の週  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Windows 用ポータル サイト アプリ内での同期の機会の増加  
Windows 用ポータル サイト アプリでは、Windows タスク バーと [スタート] メニューから直接同期を開始できるようになりました。 この機能は、唯一のタスクがデバイスを同期して、企業リソースへのアクセスを取得することで場合に特に便利です。 この新しい機能にアクセスするには、ご利用のタスク バーまたは [スタート] メニューに固定されているポータル サイト アイコンを右クリックします。 メニュー オプション (ジャンプ リストとも呼ばれる) で、**[Sync this device]\(このデバイスを同期\)** を選択します。 ポータル サイトが開いて、**[設定]** ページが表示され、同期が開始されます。新しい機能については、[UI の新機能](whats-new-app-ui.md)に関するページを参照してください。   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Windows 用ポータル サイト アプリでの新しい参照エクスペリエンス  

Windows 用ポータル サイト アプリでアプリを参照または検索するときに、既存の **[タイル]** ビューと新しく追加された **[詳細]** ビューを切り替えることができるようになりました。 新しいビューには、名前、発行元、発行日、インストール状態などのアプリケーションの詳細が一覧表示されます。  

**[アプリ]** ページの **[インストール済み]** ビューでは、完了済みと進行中のアプリのインストールに関する詳細を確認できます。 新しいビューの外観を確認するには、[UI の新機能](whats-new-app-ui.md)を参照してください。  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>デバイス登録マネージャー向けのポータル サイト アプリの操作性の改善  
デバイス登録マネージャー (DEM) が Windows 用ポータル サイト アプリにサインインすると、アプリには DEM の現在 (実行中のデバイス) のみが一覧表示されるようになります。 この改善により、DEM に登録されたデバイスをすべて表示しようとしたときに以前に発生していたタイムアウトが削減されます。  


## <a name="week-of-july-9-2018"></a>2018 年 7 月 9 日の週

### <a name="app-management"></a>アプリ管理

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>未承認のデバイス ベンダーとモデルに基づくアプリのアクセスのブロック <!-- 1425689 ! -->
Intune の IT 管理者は、Intune App Protection ポリシーによって、Android 製造元や iOS モデルの指定された一覧を適用できます。 IT 管理者は、Android ポリシーの製造元と iOS ポリシーのデバイス モデルのセミコロン区切り一覧を提供できます。 Intune App Protection ポリシーは、Android および iOS 専用です。 この指定されたリストでは 2 つの個別操作を実行できます。
- 指定されていないデバイスでのアプリ アクセスからブロック。
- または、指定されていないデバイスでの企業データの選択的ワイプ。 

ユーザーは、ポリシーによる要件が満たされない場合、対象となるアプリケーションにアクセスすることができません。 設定に基づいて、ユーザーは、ブロックされるか、アプリ内の企業データを選択的にワイプされます。 iOS デバイス上でこの機能を利用するには、対象のアプリケーションに適用するこの機能の Intune アプリ SDK を統合するアプリケーション (WXP、Outlook、Managed Browser、Yammer など) の参加が必要となります。 この統合は、ローリング方式で行われ、特定のアプリケーション チームによって異なります。 Android でこの機能を利用するには、最新の Intune ポータル サイトが必要です。 

エンド ユーザー デバイスの Intune クライアントは、アプリケーション保護ポリシーに対して Intune ブレードで指定されている文字列の単純一致に基づいてアクションを実行します。 これは、デバイスを報告する値に完全に依存します。 そのため、IT 管理者には、意図した動作が正確であることを確認することをお勧めします。 これは、小さなユーザー グループを対象に、さまざまなデバイス製造元とモデルに基づいてこの設定をテストすることによって実現できます。 Microsoft Intune で、アプリ保護ポリシーを表示および追加するには、**[クライアント アプリ]** > **[アプリ保護ポリシー]** の順に選択します。 アプリ保護ポリシーの詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」および「[Intune でアプリ保護ポリシーのアクセス アクションを利用し、データを選択的にワイプする](app-protection-policies-access-actions.md)」を参照してください。

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>macOS ポータル サイトのプレリリース ビルドへのアクセス <!-- 1734766 -->
Microsoft AutoUpdate を使用すれば、Insider Program に参加することにより、早期にビルドを受け取るためにサインアップできます。 サインアップすると、エンド ユーザーが使用できるようになる前に更新されたポータル サイトを使用できます。 詳細については、[Microsoft Intune に関するブログ](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/) を参照してください。

## <a name="week-of-july-2-2018"></a>2018 年 7 月 2 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>デバイスごとに iOS アプリ構成の状態を監視する <!-- 880037 -->
Microsoft Intune 管理者は、各マネージド デバイスの iOS アプリ構成状態を監視できます。 Azure Portal の **[Microsoft Intune]** から、**[デバイス]** > **[すべてのデバイス]** の順に選びます。 管理対象デバイスの一覧から、デバイスのブレードを表示する特定のデバイスを選びます。 デバイスのブレードで、**[アプリの構成]** を選びます。

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>アプリ保護ポリシーのアクションにアクセスする <!-- 1483510 -->
非準拠デバイスを明示的にワイプ、ブロック、または警告するようアプリ保護ポリシーを構成することができます。 "*ワイプ*" アクションによって、デバイスから会社の企業データが削除されます。 ワイプが発生した場合、デバイスのユーザーにはワイプの理由と修復手順の両方が通知されます。 最低 OS バージョンなどの一部の設定については、ブロックとワイプなど、複数のアクションを適用できます。 これらのアクションは、アプリが起動されるとトリガーされるので注意してください。

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>組織のアプリ データの選択的ワイプ <!-- 1507030 -->
管理者は、アプリケーション保護ポリシー (APP) アクセス設定の条件が満たされないときの新しいアクションとして、組織のデータの選択的ワイプを構成できるようになりました。  この機能を使うと、管理者は事前に構成した条件に基づいて、アプリケーションから組織の機密データを自動的に保護したり削除したりできます。

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>VPP を通じて購入した iOS アプリの取り消し <!-- 1777384 -->
Microsoft Intune 管理者は、ボリューム購入プログラム (VPP) で購入した iOS アプリのうち選択したもののライセンスをすべて取り消すことができます。 ユーザー ライセンスされたアプリがユーザーに割り当てられなくなった場合、該当するユーザーに通知することができます。 アプリのライセンスを取り消しても、関連する VPP アプリがデバイスからアンインストールされるわけではありません。 VPP アプリをアンインストールするには、割り当てアクションを **[アンインストール]** に変更する必要があります。 回収されたライセンスの数は、Intune の **[アプリ]** ワークロードの **[ライセンスされたアプリ]** ノードに反映されます。 iOS VPP アプリの詳細については、「[Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法](vpp-apps-ios.md)」をご覧ください。

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>ポータル サイト アプリの非準拠メッセージの更新 <!-- 1832222 -->
デバイスが準拠していない場合にそのデバイスのユーザーに表示されるメッセージが変更されました。 メッセージの元の意味は変わりませんが、専門用語を減らして、よりわかりやすくするために更新されました。 また、ドキュメントと修復手順へのリンクが最新の状態を保つために更新されました。
以下の更新前と後のテキストは、表示されるメッセージングの改善の一例です。
- **前**: *このデバイスは、IT 管理者によって要求された指定の期間に Intune サービスに接続していません。この問題を解決するためには、デバイスでポータル サイト アプリを開いて [コンプライアンスの確認] ボタンをクリックしてください。*
- **後**: *デバイスはしばらくの間、組織でチェックインされていません。接続を再確立するには、デバイスでポータル サイト アプリを開き、デバイスの [設定の確認] をタップします。*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>iOS VPP アプリのライセンスを取り消す <!-- 1863797 -->
管理者は、ユーザーまたはデバイスに割り当てられている iOS VPP アプリのライセンスを回収することができます。 iOS VPP アプリをアンインストールしても、アプリのライセンスを回収できます。 アプリをアンインストールする前に、アプリの対象となっているグループからユーザーまたはデバイスを削除する必要があります。 グループからユーザーまたはデバイスを削除することで、アプリの再インストールが回避されます。 これらの手順が完了したら、別のユーザーまたはデバイスにアプリ ライセンスを割り当てることができます。 iOS VPP アプリのライセンスの詳細については、「[Microsoft Intune での iOS のボリューム購入アプリの管理](vpp-apps-ios.md)」をご覧ください。

### <a name="device-configuration"></a>デバイス構成

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>[職場または学校にアクセスする] 設定を用いたデバイス カテゴリの選択<!-- 1058963 eenotready --> 
[デバイス グループ マッピング](https://docs.microsoft.com/en-us/intune/device-group-mapping)を有効にした場合、**[設定]** > **[アカウント]** > **[職場または学校にアクセスする]** の **[接続]** から登録後、または Windows 10 のユーザーはデバイス カテゴリの選択を求められるようになります。 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>電子メール プロファイルのアカウント ユーザー名として sAMAccountName を使用する <!-- 1500307 -->
Android、iOS、および Windows 10 用の電子メール プロファイルのアカウント ユーザー名として、オンプレミスの **sAMAccountName** を使うことができます。 また、Azure Active Directory (Azure AD) の `domain` または `ntdomain` 属性から、ドメインを取得できます。 または、カスタムの静的ドメインを入力します。

この機能を使うには、オンプレミスの Active Directory 環境から Azure AD に `sAMAccountName` 属性を同期する必要があります。

[Android](email-settings-android.md)、[iOS](email-settings-ios.md)、[Windows 10 以降](email-settings-windows-10.md)に適用される

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>競合しているデバイス構成プロファイルの確認 <!-- 1556983 -->
**[デバイス構成]** には、既存のプロファイルのリストが表示されます。 今回の更新プログラムでは、競合しているプロファイルに関する詳細を示す新しい列が追加されます。 競合する行を選択することで、競合しているプロファイルと設定を確認できます。 

詳細については、[構成プロファイルの管理](device-profile-monitor.md#view-conflicts)に関するページを参照してください。

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>デバイスのポリシー準拠でのデバイスの新しい状態 <!-- 2308882 -->
**[デバイスのポリシー準拠]** > **[ポリシー]**、該当するポリシー、**[概要]** の順に選択すると、次の新しい状態が追加されます。
- 成功
- エラー
- 競合
- 保留中
- 適用不可。異なるプラットフォームのデバイス数を示すイメージも表示されます。 たとえば、iOS プロファイルを見ている場合、新しいタイルでは、そのプロファイルに割り当てられている iOS 以外のデバイスの数も示されます。 [デバイス コンプライアンス ポリシー](compliance-policy-monitor.md#view-status-of-device-policies)に関するポリシーを参照してください。

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>デバイスのコンプライアンスはサード パーティのウイルス対策ソリューションをサポートする <!-- 2325484 -->
デバイス コンプライアンス ポリシーを作成するとき (**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[プラットフォーム: Windows 10 以降]** > **[設定]** > **[システム セキュリティ]**)、新しい **[[デバイスのセキュリティ]](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)** オプションがあります。 
- **[ウイルス対策]**: **[必要]** に設定すると、Windows Security Center に登録されている Symantec や Windows Defender などのウイルス対策ソリューションを使って、コンプライアンスを確認できます。 
- **[スパイウェア対策]**: **[必要]** に設定すると、Windows Security Center に登録されている Symantec や Windows Defender などのスパイウェア対策ソリューションを使って、コンプライアンスを確認できます。 

適用対象: Windows 10 以降 

### <a name="device-enrollment"></a>デバイスの登録

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>登録プログラム トークンのリスト内にあるプロファイルを持たないデバイスを示す列 <!-- 1853904 -->
登録プログラムのトークン リストには、プロファイルが割り当てられていないデバイスの数を示す新しい列があります。 この列は、管理者が、そのようなデバイスをユーザーに渡す前に、プロファイルを割り当てるのに役立ちます。 新しい列を参照するには、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** の順に選択します。

### <a name="device-management"></a>デバイス管理

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Android for Work および Play for Work の Google 名の変更 <!--842873 -->
Intune では、Google ブランドの変更を反映するように "Android for Work" の用語が更新されました。 "Android for Work" および "Play for Work" という用語は使われなくなりました。 コンテキストに応じて異なる用語が使われます。
- "Android エンタープライズ" は、最新の Android 管理スタック全体を指します。
- "Work profile" または "Profile Owner" は、作業プロファイルで管理されている BYOD デバイスを指します。
- "Managed Google Play" は、Google アプリ ストアを指します。

#### <a name="rules-for-removing-devices----1609459---"></a>デバイス削除のルール <!-- 1609459 -->
設定した日数の間チェックインしていないデバイスを自動的に削除する新しいルールを使用できます。 新しいルールを表示するには、**[Intune]** ウィンドウ、**[デバイス]**、**[デバイスのクリーンアップ ルール]** の順に選択します。

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>Android デバイスの会社所有、単一使用のサポート <!-- 1630973 -->

Intune は、高度に管理されてロック ダウンされた、キオスク スタイルの Android デバイスをサポートするようになりました。 これにより、管理者は、デバイスの使用を 1 つのアプリまたはアプリの小さなセットにさらにロックダウンし、ユーザーが他のアプリを有効にしたり、デバイスで他の操作を実行したりすることを禁止できます。 Android キオスクを設定するには、Intune > **[デバイスの登録]** > **[Android の登録]** > **[Kiosk and task device enrollments]\(キオスクおよびタスク デバイス登録\)** の順に進みます。 詳細については、[Android エンタープライズ キオスク デバイスの登録の設定](android-kiosk-enroll.md)に関するページを参照してください。

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>アップロードされた重複する業務用デバイス ID の行ごとのレビュー <!-- 2203794-->
業務用 ID をアップロードすると、重複の一覧が提供され、既存の情報を置き換えるか、保持することができるようになりました。 **[デバイスの登録]** > **[業務用デバイスの ID]** > **[ID の追加]** を選ぶと、重複がある場合はレポートが表示されます。 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>業務用デバイスの ID を手動で追加する <!-- 2203803 -->
業務用デバイスの ID を手動で追加できるようになりました。 **[デバイスの登録]** > **[業務用デバイスの ID]** > **[追加]** の順に選びます。 

## <a name="week-of-june-25-2018"></a>2018 年 6 月 25 日の週

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo - 新しい Mobile Threat Defense パートナー <!-- 1169249 -->

Microsoft Intune に統合されたモバイル脅威保護ソリューションである Pradeo によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

## <a name="week-of-june-18-2018"></a>2018 年 6 月 18 日の週

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Edge モバイルでの Intune アプリ保護ポリシーのサポート <!-- 1817882 -->

モバイル デバイス向けの Microsoft Edge ブラウザーで、Intune で定義されるアプリ保護ポリシーがサポートされるようになりました。

## <a name="week-of-june-11-2018"></a>2018 年 6 月 11 日の週

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>NDES 証明書コネクタで FIPS モードを使用する<!-- 1333688 -->
Federal Information Processing Standard (FIPS) モードが有効な NDES 証明書コネクタをコンピューターにインストールすると、証明書の発行や無効化が期待どおりに動作しません。 この更新プログラムでは、NDES 証明書コネクタに FIPS のサポートが含まれています。 

この更新プログラムには、次も含まれています。

- NDES 証明書コネクタには、Windows Server 2016 と Windows Server 2012 R2 に自動的に含まれる .NET 4.5 Framework が必要です。 これまでは、最小で .NET 3.5 Framework バージョンが必須でした。
- NDES 証明書コネクタには、TLS 1.2 のサポートが含まれています。 したがって、NDES 証明書コネクタがインストールされているサーバーが TLS 1.2 をサポートする場合、TLS 1.2 が使用されます。 サーバーが TLS 1.2 をサポートしない場合、TLS 1.1 が使用されます。 現在、デバイスとサーバー間の認証には、TLS 1.1 が使用されています。

詳細については、[SCEP 証明書の構成と使用](certificates-scep-configure.md)と、[PKCS 証明書の構成と使用](certficates-pfx-configure.md)に関するページを参照してください。

## <a name="week-of-june-4-2018"></a>2018 年 6 月 4 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>キオスク モードのビジネス向け Microsoft Store アプリの関連付けられたアプリ ユーザー モデル ID (AUMID) を取得する <!-- 1560077 ! -->
Intune で、ビジネス向け Microsoft Store (WSfB) アプリのアプリ ユーザー モデル ID (AUMID) を取得して、キオスク プロファイルの構成を改善できるようになりました。

ビジネス向け Microsoft Store アプリについて詳しくは、「[ビジネス向け Microsoft Store からのアプリの管理](windows-store-for-business.md)」をご覧ください。

#### <a name="new-company-portal-branding-page----1916370---"></a>新しいポータル サイトのブランド化ページ <!-- 1916370 -->
ポータル サイトのブランド化ページには、新しいレイアウト、メッセージ、ヒントがあります。


### <a name="device-configuration"></a>デバイス構成

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>Palo Alto Networks GlobalProtect VPN プロファイルのサポート <!-- 1333680 ! -->
今回の更新で、Intune での VPN プロファイルの VPN 接続の種類として、Palo Alto Networks GlobalProtect を選択できるようになりました (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[プロファイルの種類]** > **[VPN]**)。 このリリースでは、次のプラットフォームがサポートされます。 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>ローカル デバイス セキュリティ オプションの設定への追加 <!-- 1403702 -->
Windows 10 デバイスに対して追加のローカル デバイス セキュリティ オプションの設定を構成できるようになりました。 追加設定を利用できるのは、Microsoft ネットワーク クライアント、Microsoft ネットワーク サーバー、ネットワーク アクセスとセキュリティ、および対話型ログオンなどに関する部分です。 これらの設定は、Windows 10 デバイスの構成ポリシーを作成するときに、[Endpoint Protection] カテゴリに表示されます。

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Windows 10 デバイスでキオスク モードを有効にする <!-- 1560072 ! -->
Windows 10 デバイスでは、構成プロファイルを作成して、キオスク モードを有効にすることができます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[Windows 10]** > **[デバイスの制限]** > **[キオスク]**)。 この更新では、**[キオスク (プレビュー)]** の設定の名前が **[キオスク (古い)]** に変更されています。 **[キオスク (古い)]** は使用を推奨されませんが、7 月の更新までは機能し続けます。 **[キオスク (古い)]** は新しい **[キオスク]** プロファイルの種類に置き換えられ (**[プロファイルの作成]** > **[Windows 10]** > **[キオスク (プレビュー)]**)、Windows 10 RS4 以降でキオスクを構成する設定が含まれます。

Windows 10 以降に適用されます。

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>デバイス プロファイルのグラフィカル ユーザー グラフが戻った <!-- 2160133 -->
デバイス プロファイルのグラフィカルなグラフに表示される数値カウントの向上で (**[デバイス構成]** > **[プロファイル]** > 既存のプロファイルを選択 > **[概要]**)、グラフィカルなユーザー グラフが一時的に削除されました。

この更新では、グラフィカル ユーザー グラフが元に戻り、Azure portal に表示されます。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118-wnready---"></a>ユーザー認証なしの Windows Autopilot 登録のサポート <!-- 1165118 wnready -->
Intune では、ユーザー認証なしの Windows Autopilot 登録がサポートされるようになりました。 これは Windows Autopilot Deployment プロファイルの新しいオプションであり、"Autopilot Deployment モード" が "自己配置" に設定されます。  デバイスでは Windows 10 Insider プレビュー ビルド 17672 以降を実行しており、この種類の登録を正常に完了させるために TPM 2.0 チップがある必要があります。 ユーザー認証は不要であるため、このオプションを割り当てる必要があるのは、物理的に制御できるデバイスのみとなります。

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Autopilot の OOBE を構成するときの新しい言語/リージョンの設定 <!-- 1821766 -->
Out of Box Experience (OOBE) の間に、Autopilot プロファイルの言語とリージョンを設定する、新しい構成設定を使用できます。 新しい設定を表示するには、**[デバイスの登録]** > **[Windows の登録]** > **[Deployment profiles]\(展開プロファイル\)** > **[プロファイルの作成]** > **[配置モード]** = **[Self-deploying]\(自己配置\)** > **[既定値が構成済み]** の順に選択します。

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>デバイス キーボードを構成するための新しい設定 <!-- 1821768 -->
Out of Box Experience (OOBE) の間に、Autopilot プロファイルのキーボードを構成する新しい設定を使用できます。 新しい設定を表示するには、**[デバイスの登録]** > **[Windows の登録]** > **[Deployment profiles]\(展開プロファイル\)** > **[プロファイルの作成]** > **[配置モード]** = **[Self-deploying]\(自己配置\)** > **[既定値が構成済み]** の順に選択します。

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Autopilot プロファイルの対象がグループに移動 <!-- 1877935 -->
AutoPilot 展開プロファイルは AutoPilot デバイスを含む Azure AD のグループに割り当てることができます。

### <a name="device-management"></a>デバイス管理

#### <a name="set-compliance-by-device-location----851881----"></a>デバイスの場所によるコンプライアンスの設定 <!-- 851881 ! -->
状況によっては、ネットワーク接続で定義される特定の場所に、企業リソースへのアクセスを制限することが必要な場合あります。 デバイスの IP アドレスに基づき、コンプライアンス ポリシーを作成できるようになりました (**[デバイスのポリシー準拠]** > **[場所]**)。 デバイスが IP 範囲外に移動した場合、デバイスは会社のリソースにアクセスできません。

適用対象: Android デバイス 6.0 以降 (ポータル サイト アプリ更新済み)

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Windows 10 Enterprise RS4 Autopilot デバイスでのコンシューマー アプリおよびエクスペリエンスの禁止<!-- 1621980 -->
Windows 10 Enterprise RS4 Autopilot デバイスへのコンシューマー アプリおよびエクスペリエンスのインストールを禁止することができます。 この機能を表示するには、**[Intune]** > **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[プラットフォーム]** = **[Windows 10 or later]\(Windows 10 以降\)** > **[プロファイルの種類]** = **[デバイスの制限]** > **[構成]** > **[Windows スポットライト]** > **[コンシューマー向けの機能]** の順に移動します。 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>Windows 10 ソフトウェア更新プログラムの最新のものをアンインストールする <!-- 1732948 -->
Windows 10 コンピューターで重大な問題が見つかった場合は、最新の機能更新プログラムまたは最新の品質更新プログラムをアンインストール (ロールバック) できます。 機能更新プログラムまたは品質更新プログラムをアンインストールできるのは、デバイスが存在するサービス チャネルの場合のみです。 アンインストールすると、Windows 10 コンピューター上の以前の更新プログラムを復元するためのポリシーがトリガーされます。 機能更新プログラムの場合、最新バージョンのアンインストールを適用できる期間を 2 日から 60 日間で制限できます。 ソフトウェア更新プログラムのアンインストール オプションを設定するには、Azure Portal 内の **[Microsoft Intune]** ブレードで **[ソフトウェア更新プログラム]** を選択します。 次に、**[ソフトウェア更新プログラム]** ブレードで **[Windows 10 更新プログラムのリング]** を選択します。 これで、**[概要]** セクションから **[アンインストール]** オプションを選択できます。

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>すべてのデバイスで IMEI およびシリアル番号を検索する <!-- 1793685 -->
[すべてのデバイス] ブレードで IMEI およびシリアル番号を検索できるようになりました (電子メール、UPN、デバイス名、管理名は引き続き使用できます)。 Intune で、**[デバイス]** > **[すべてのデバイス]** の順に選択し、検索ボックスに検索語句を入力します。

#### <a name="management-name-field-will-be-editable----1875989---"></a>管理名フィールドが編集可能になる <!-- 1875989 -->
デバイスの **[プロパティ]** ブレードで、管理名フィールドを編集できるようになりました。 このフィールドを編集するには、**[デバイス]** > **[すべてのデバイス]** > デバイスを選択 > **[プロパティ]** の順に選びます。 管理名フィールドを使って、デバイスを一意に識別できます。

#### <a name="new-all-devices-filter-device-category----1878520---"></a>新しいすべてのデバイス フィルター: デバイスのカテゴリ <!-- 1878520 -->
デバイスのカテゴリごとに **[すべてのデバイス]** リストをフィルター処理できるようになりました。 これを行うには、**[デバイス]** > **[すべてのデバイス]** > **[フィルター]** > **[デバイスのカテゴリ]** の順に選択します。

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>TeamViewer を使用して iOS デバイスと MacOS デバイスの画面を共有する <!-- 1985547 -->
管理者は [TeamViewer](device-profile-android-teamviewer.md) に接続し、iOS および macOS デバイスとの画面共有セッションを開始できるようになりました。 iPhone、iPad、macOS ユーザーは、他のデスクトップ デバイスまたはモバイル デバイスと画面をライブで共有できます。 

#### <a name="multiple-exchange-connector-support----2070451---"></a>複数の Exchange Connector のサポート <!-- 2070451 -->
テナントごとの Microsoft Intune Exchange Connector の数が 1 個だけという制限がなくなりました。 Intune で複数の Exchange Connector がサポートされ、複数のオンプレミス Exchange の組織で Intune の条件付きアクセスを設定できるようになりました。

Intune のオンプレミス Exchange Connector を使うと、デバイスが Intune に登録されているかどうか、およびデバイスが Intune のデバイス コンプライアンス ポリシーに準拠しているかどうかに基づいて、お使いのオンプレミスの Exchange メールボックスに対するデバイス アクセスを管理できます。 コネクタを設定するには、Azure Portal から Intune のオンプレミス Exchange Connector をダウンロードして、Exchange の組織内のサーバーにインストールします。 Microsoft Intune ダッシュ ボードで **[オンプレミス アクセス]** を選択し、**[セットアップ]** で **[Exchange ActiveSync のコネクタ]** を選択します。 Exchange のオンプレミス コネクタをダウンロードし、Exchange の組織内のサーバーにインストールします。 テナントごとに 1 個という Exchange Connector の制限がなくなったので、他に Exchange の組織がある場合は、他の各 Exchange の組織にも同じ手順でコネクタをダウンロードしてインストールできます。

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>新しいデバイス ハードウェアの詳細: CCID <!-- 2156657 -->
CCID (Chip Card Interface Device) 情報がデバイスごとに含まれるようになりました。 これを表示するには、**[デバイス]** > **[すべてのデバイス]** の順に選択します。次に、該当するデバイス、**[ハードウェア]** の順に選び、**[ネットワークの詳細]** の下を確認します。

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>スコープ グループとしてすべてのユーザーとすべてのデバイスを割り当てる <!-- 2196803 -->
スコープ グループ内のすべてのユーザー、すべてのデバイス、およびすべてのユーザーとすべてのデバイスを割り当てられるようになりました。 これを行うには、**[Intune の役割]** > **[すべてのロール]** > **[Policy and profile manager]\(ポリシーとプロファイル マネージャー\)** > **[割り当て]** の順に選び、割り当てを選んで、**[スコープ (グループ)]** を選びます。

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806-wnready--"></a>iOS および macOS デバイスの UDID 情報が含まれるようになりました <!-- 2219806 wnready-->
iOS および macOS デバイスの UDID (一意のデバイス識別子) を表示するには、**[デバイス]** > **[すべてのデバイス]** の順に選択します。次に、該当するデバイス、**[ハードウェア]** の順に選びます。 UDID は会社のデバイスでのみ利用できます (**[デバイス]** > **[すべてのデバイス]**、該当するデバイス、**[プロパティ]** > **[デバイスの所有権]** の順に選択して設定した場合)。

### <a name="intune-apps"></a>Intune アプリ

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>アプリのインストールのトラブルシューティングの向上 <!-- 928990 -->
Microsoft Intune の MDM で管理されたデバイスでは、アプリのインストールが失敗することがあります。 アプリのインストールが失敗した場合、失敗の理由を理解したり、問題をトラブルシューティングするのが難しい場合があります。 アプリ トラブルシューティング機能のパブリック プレビューが提供されています。 各デバイスの下に **[管理対象アプリ]** という新しいノードがあります。 これには、Intune MDM 経由で配布されたアプリが表示されます。 ノード内では、アプリのインストール状態が一覧表示されます。 個々のアプリを選ぶと、その特定のアプリのトラブルシューティング ビューが表示されます。 トラブルシューティング ビューでは、アプリが作成、変更、ターゲット指定、デバイス配布されたときなど、アプリのエンド ツー エンドのライフサイクルが表示されます。 さらに、アプリのインストールが成功しなかった場合は、エラー コードとエラーの原因に関する便利なメッセージが表示されます。 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Intune アプリ保護ポリシーと Microsoft Edge <!-- 1818968 -->
モバイル デバイス (iOS および Android) 向けの Microsoft Edge ブラウザーで、Microsoft Intune アプリ保護ポリシーがサポートされるようになりました。 Microsoft Edge アプリケーションで企業の Azure AD アカウントを使用してサインインした iOS および Android デバイスのユーザーは、Intune によって保護されます。 iOS デバイスでは、**Web コンテンツの管理対象ブラウザーを必要とする**ポリシーにより、ユーザーは Microsoft Edge が管理されている場合にその Microsoft Edge でリンクを開くことができます。

## <a name="week-of-may-14-2018"></a>2018 年 5 月 14 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>ポリシー、アプリ、証明書、およびネットワーク プロファイルのインストールを必要にする <!-- 1553555 -->

管理者は、AutoPilot デバイスのプロビジョニングの間、Intune がポリシー、アプリ、証明書、ネットワーク プロファイルをインストールするまで、エンド ユーザーによる Windows 10 RS4 デスクトップへのアクセスをブロックすることができます。 詳細については、「[登録ステータス ページを設定する](windows-enrollment-status.md)」を参照してください。

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>アプリ保護ポリシーの構成 <!-- 2144597 Part 2 -->

Azure portal では、Intune App Protection サービス ブレードに移動する代わりに、Intune に移動するようになりました。 Intune 内のアプリ保護ポリシーのための場所は 1 つだけになりました。 すべてのアプリ保護ポリシーが Intune の**アプリ保護ポリシー**の **[モバイル アプリ]** ブレードに置かれていることに注意してください。 この統合は、クラウド管理の簡素化に役立ちます。 ただし、すべてのアプリ保護ポリシーが既に Intune にあり、以前に構成した任意のポリシーを変更することができます。 Intune アプリ ポリシー保護 (APP) および条件付きアクセス (CA) ポリシーは現在、**[条件付きアクセス]** の下にあります。[条件付きアクセス] は、**[Microsoft Intune]** ブレードの **[管理]** セクション、または **[Azure Active Directory]** ブレードの **[セキュリティ]** セクションにあります。 条件付きアクセス ポリシーの変更の詳細については、「[Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)」を参照してください。 詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」を参照してください。

## <a name="week-of-may-7-2018"></a>2018 年 5 月 7 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Samsung Knox Mobile Enrollment のサポート <!--1112863-->

Knox Mobile Enrollment (KME) で Intune を使用すると、企業が所有する多数の Android デバイスを登録できます。 WiFi または移動体通信ネットワークのユーザーは、初めてデバイスをオンにしたときに、ほんの数タップで登録できます。 Knox Deployment App を使うと、Bluetooth または NFC を使ってデバイスを登録することもできます。 詳しくは、「[Samsung の Knox Mobile Enrollment を使用して Android デバイスを自動的に登録する](android-samsung-knox-mobile-enroll.md)」をご覧ください。

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Windows 10 用 Intune ポータル サイトでのヘルプの要求 <!-- 1874137 -->

ユーザーが問題に関するヘルプを入手するワークフローを開始すると、Windows 10 用 Intune ポータル サイトは Microsoft に直接アプリのログを送信するようになります。 これにより、Microsoft に問題を送ってすばやくトラブルシューティングして解決できます。

## <a name="week-of-april-23-2018"></a>2018 年 4 月 23 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Android での MAM PIN のパスコードのサポート<!-- 1438086 -->

Intune 管理者は、アプリケーション起動要件を設定して、数値の MAM PIN の代わりにパスコードを強制することができます。 構成した場合、ユーザーは、MAM 対応のアプリケーションにアクセスする前に、要求された時点で、パスコードを設定および使用する必要があります。 パスコードは、少なくとも 1 つの特殊文字または大文字/小文字アルファベットを含む数値 PIN と定義されます。 Intune によるパスコードのサポート方法は既存の数値 PIN と似ており、管理コンソールで最小の長さを設定したり、文字やシーケンスの繰り返しを許可したりできます。 この機能を利用するには、Android に最新バージョンの Intune ポータル サイトが必要です。 この機能は、iOS では既に利用できます。

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>macOS の基幹業務 (LOB) アプリのサポート <!-- 1473977 -->
Microsoft Intune では、Azure Portal から macOS LOB アプリをインストールできます。 GitHub で利用可能なツールを使って前処理した macOS LOB アプリを、Intune に追加できます。 Azure portal で、**[Intune]** ブレードから **[クライアント アプリ]** を選択します。 **[クライアント アプリ]** ブレードで、**[アプリ]** > **[追加]** の順に選択します。 **[アプリの追加]** ブレードで、**[基幹業務アプリ]** を選択します。 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Android for Work (AFW) のアプリの割り当てに対する組み込みのすべてのユーザー グループとすべてのデバイス グループ <!-- 1813073 -->
組み込みの**すべてのユーザー** グループと**すべてのデバイス** グループを AFW アプリの割り当てに利用することができます。 詳細については、「[Microsoft Intune でのアプリ割り当ての組み込みと除外](apps-inc-exl-assignments.md)」を参照してください。

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>ユーザーがアンインストールした必要なアプリは Intune によって再インストールされる <!-- 1947010 -->
エンド ユーザーが必要なアプリをアンインストールした場合、Intune は 7 日間の再評価サイクルを待機するのではなく、24 時間以内に該当するアプリを自動的に再インストールします。

### <a name="device-configuration"></a>デバイス構成

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>デバイス プロファイル チャートと状態リストでグループ内のすべてのデバイスが表示されるようになる <!-- 1449153 -->
デバイス プロファイルを構成するときは (**[デバイス構成]** > **[プロファイル]**)、iOS などのデバイス プロファイルを選択します。 このプロファイルを、iOS デバイスと iOS 以外のデバイスを含むグループに割り当てます。 グラフィカル チャートの数では、プロファイルが iOS デバイス "*および*" iOS 以外のデバイスに適用されているように示されます (**[デバイス構成]** > **[プロファイル]** > 既存のプロファイルを選択 > **[概要]**)。 **[概要]** タブでグラフィカル チャートを選択すると、**[デバイスの状態]** に、iOS デバイスだけではなく、グループ内のすべてのデバイスが一覧表示されます。 

この更新により、グラフィカル チャート (**[デバイス構成]** > **[プロファイル]** > 既存のプロファイルを選択 > **[概要]**) では、特定のデバイス プロファイルの数のみが表示されるようになります。 たとえば、構成デバイス プロファイルが iOS デバイスに適用される場合、チャートの一覧には iOS デバイスの数だけが表示されます。 グラフィカル チャートを選択すると開く **[デバイスの状態]** では、iOS デバイスだけが一覧表示されます。

この更新が行われている間、グラフィカル ユーザー チャートは一時的に削除されます。 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>Windows 10 の Always On VPN <!--1333666 -->

現在、[Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) は、OMA-URI を使って作成されたカスタム仮想プライベート ネットワーク (VPN) プロファイルを使うことで、Windows 10 デバイスで使用できます。

この更新では、管理者は Azure Portal の Intune で直接、Windows 10 VPN プロファイルに対する Always On を有効にできるようになります。 Always On VPN プロファイルは、次のときに自動的に接続します。

- ユーザーが自分のデバイスにサインインしたとき
- デバイスでネットワークが変更されたとき
- デバイスの画面がオフにされた後でオンに戻されたとき

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育プロファイル用の新しいプリンター設定 <!-- 1308900 -->

教育プロファイルの場合、**[プリンター]** カテゴリで新しい設定 **[プリンター]**、**[通常使うプリンター]**、**[新しいプリンターの追加]** を利用できます。

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>個人プロファイルでの発信者番号通知 - Android for Work <!--1098984 -->
デバイス上で個人プロファイルを使用する場合、勤務先の作業連絡先からの発信者番号の詳細がエンド ユーザーに表示されない場合があります。 

この更新プログラムでは、**[Android for Work]** > **[デバイスの制限]** > **[仕事用プロファイルの設定]** に、次の新しい設定が表示されます。
- 個人プロファイルに勤務先の連絡先の発信者番号を表示する

有効にすると (構成されていない場合)、勤務先の連絡先の発信者番号の詳細が個人プロファイルに表示されます。 ブロックすると、勤務先の連絡先の発信者番号は個人プロファイルに表示されません。 

適用対象: Android OS v6.0 以降の Android 仕事用プロファイル デバイス

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Endpoint Protection の設定に追加された新しい Windows Defender Credential Guard の設定 <!--1102252 --><!--from 1802 and 1804-->

この更新により、[Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**[デバイス構成]** > **[プロファイル]** > **[Endpoint Protection]**) に、次の設定が含まれます。 

- **Windows Defender Credential Guard**: 仮想化ベースのセキュリティによる Credential Guard が有効になります。 **[Platform Security Level with Secure Boot]\(セキュア ブートでのプラットフォーム セキュリティ レベル\)** と **[仮想化ベースのセキュリティ]** の両方が有効な場合にこの機能を有効にすると、次回の再起動時に資格情報を保護することができます。 次のオプションがあります。
  - **[無効]**: 以前に Credential Guard が **[ロックなしで有効化]** オプションで有効になっていた場合に、Credential Guard をリモートで無効にします。

  - **[UEFI ロックで有効化]**: レジストリ キーまたはグループ ポリシーを使って Credential Guard を無効にできないようにします。 この設定を使用した後に Credential Guard を無効にする場合は、グループ ポリシーを [無効] に設定する必要があります。 次に、実際に存在するユーザーの各コンピューターからセキュリティ機能を削除します。 この手順により、UEFI に存在した構成がクリアされます。 UEFI の構成が保持されている限り、Credential Guard は有効になっています。

  - **[ロックなしで有効化]**: グループ ポリシーを使ってリモートで Credential Guard を無効にできるようにします。 この設定を使うデバイスは、Windows 10 (バージョン 1511) 以降を実行している必要があります。

Credential Guard を構成すると、次の関連するテクノロジが自動的に有効になります。 

  - **[Enable Virtualization-based Security (VBS)]\(仮想化ベースのセキュリティ (VBS) を有効にする\)**: 次回の再起動で仮想化ベースのセキュリティ (VBS) が有効になります。 仮想化ベースのセキュリティは、Windows ハイパーバイザーを使用してセキュリティ サービスのサポートを提供し、セキュア ブートを要求します。
  - **[Secure Boot with Direct Memory Access (DMA)]\(直接メモリ アクセス (DMA) によるセキュア ブート\)**: セキュア ブートおよび直接メモリ アクセスによる VBS が有効になります。 DMA 保護は、ハードウェアのサポートを必要とし、正しく構成されたデバイスでのみ有効にされます。 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>SCEP 証明書でのカスタム サブジェクト名の使用 <!-- 2064190 -->
SCEP 証明書プロファイルでカスタム サブジェクトの共通名 **OnPremisesSamAccountName** を使うことができます。 たとえば、`CN={OnPremisesSamAccountName})` のように使用できます。

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977---"></a>Android for Work でカメラと画面キャプチャをブロックする <!-- 1098977 -->
Android デバイスのデバイス制限を構成するときに、次の 2 つの新しいプロパティをブロックに利用できます。 
- カメラ: デバイスのすべてのカメラへのアクセスを禁止します
- 画面キャプチャ: 画面のキャプチャをブロックし、セキュリティで保護されたビデオ出力を持たないディスプレイ デバイスにコンテンツが表示されないようにします

Android for Work に適用されます。


### <a name="device-enrollment"></a>デバイスの登録

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>macOS High Sierra 10.13.2 以降のデバイスでのユーザーの新しい登録手順 <!--1734567 -->
macOS High Sierra 10.13.2 では、"ユーザー承認済み" MDM 登録の概念が導入されました。 承認済みの登録で、セキュリティ上重要な一部の設定の Intune による管理が許可されます。 詳細については、Apple のサポート ドキュメント https://support.apple.com/HT208019 をご覧ください。

macOS ポータル サイトを使って登録されたデバイスは、エンド ユーザーがシステム環境設定を開いて手動で承認しない限り、"ユーザー承認されていない" ものと見なされます。 そのため、macOS ポータル サイトでは、macOS 10.13.2 以降のユーザーは、登録プロセスの最後に、登録の手動承認に移動するようになりました。 Intune 管理コンソールでは、登録されているデバイスがユーザー承認済みかどうかが示されます。



### <a name="device-management"></a>デバイス管理

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>Advanced Threat Protection (ATP) と Intune は完全に統合されています <!-- 1629303 -->

[Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) では、Windows 10 デバイスのリスク レベルが表示されます。 Windows Defender Security Center (ATP Portal) では、Microsoft Intune への接続を作成できます。 作成後、許容できる脅威レベルの決定に Intune コンプライアンス ポリシーが使用されます。 その脅威レベルを超えた場合、Azure Active Directory (AD) の条件付きアクセス ポリシーによって、組織内のさまざまなアプリへのアクセスを阻止できます。

この機能によって ATP はファイルをスキャンし、脅威を検出し、Windows 10 デバイス上のあらゆるリスクを報告できます。

[Intune で条件付きアクセスによる ATP を有効にする](advanced-threat-protection.md)方法に関するページを参照してください。

#### <a name="support-for-user-less-devices----1637553---"></a>ユーザーのいないデバイスのサポート <!-- 1637553 -->
Intune は、Microsoft Surface Hub など、ユーザーのいないデバイスでコンプライアンスを評価する機能をサポートします。 コンプライアンス ポリシーは、特定のデバイスを対象にすることができます。 したがって、ユーザーが関連付けられていないデバイスのコンプライアンス (および非コンプライアンス) を判断できます。

#### <a name="delete-autopilot-devices----1713650---"></a>Autopilot デバイスの削除 <!-- 1713650 -->
Intune 管理者は、[Autopilot デバイスを削除する](enrollment-autopilot.md#delete-autopilot-devices)ことができます。

#### <a name="improved-device-deletion-experience---1832333---"></a>デバイス削除エクスペリエンスの向上 <!--1832333 -->
[Intune からデバイスを削除する](devices-wipe.md#delete-devices-from-the-intune-portal)前に、会社のデータを削除したり、デバイスを工場出荷時の状態にリセットしたりする必要はなくなります。

新しいエクスペリエンスを表示するには、Intune にサインインし、**[デバイス]** > **[すべてのデバイス]** > デバイスの名前 > **[削除]** の順に選びます。

ワイプ/使用停止の確認が必要な場合は、**[削除]** の前に **[会社データを削除する]** と **[出荷時の設定にリセット]** を実行して、標準のデバイス ライフサイクル ルートを使うことができます。 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>紛失モードになったときに iOS で音を鳴らす <!-- 1947769 -->
監視対象の iOS デバイスがモバイル デバイス管理 (MDM) の[紛失モード](device-lost-mode.md)になったときに、[音を鳴らす](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device)ことができます (**[デバイス]** > **[すべてのデバイス]** > iOS デバイスを選択 > **[概要]** > **[詳細]**)。 音は、デバイスが紛失モードではなくなるまで、またはユーザーがデバイスで音を無効にするまで、鳴り続けます。 iOS デバイス 9.3 以降に適用されます。

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Intune デバイスで行った Web 検索の結果のブロックまたは許可 <!--1972804-->

管理者は、デバイスで行った Web 検索の結果をブロックできるようになりました。

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Apple MDM プッシュ通知証明書のアップロード失敗のエラー メッセージの改善 <!-- 2172331 -->

既存の MDM 証明書を更新するときは同じ Apple ID を使う必要があることが、エラー メッセージで説明されます。

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>仮想マシンでの macOS 用ポータル サイトのテスト <!-- 2216679 -->

Parallels Desktop と VMware Fusion の仮想マシンで IT 管理者が macOS 用ポータル サイト アプリをテストするために役立つガイドを公開しました。 詳しくは、「[テスト用に仮想 macOS マシンを登録する](macos-enroll.md#enroll-virtual-macos-machines-for-testing)」を参照してください。


### <a name="user-interface"></a>ユーザー インターフェイス

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Windows 10 ポータル サイトのデバイス タイルの改善 <!--2213364 -->

目の不自由なユーザーでもアクセスしやすく、画面読み上げツールでの動作が改善されるように、タイルが更新されました。

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>macOS のポータル サイト アプリでの診断レポートの送信 <!-- 2216677 -->
macOS デバイスのポータル サイト アプリが更新され、ユーザーが Intune 関連のエラーを報告しやすくなりました。 ポータル サイト アプリから、従業員は次の操作を行うことができます。

- Microsoft 開発者チームに直接診断レポートをアップロードする。
- 会社の IT サポート チームにインシデント ID をメールで送ります。

詳細については、[macOS のエラーの送信](/intune-user-help/send-errors-macos)に関するページを参照してください。

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune が Windows 10 ポータル サイト アプリの Fluent Design System に対応 <!-- 1195010 WNready -->
Windows 10 の Intune ポータル サイト アプリが [Fluent Design System のナビゲーション ビュー](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics)に合わせて更新されました。 アプリの側面だけでなく、すべてのトップ レベルのページに静的な縦方向リストが表示されます。 リンクをクリックすると、ページをすばやく表示したり、ページを切り替えたりできます。 これは現在作成中の更新の一部であり、今後さらにアダプティブで馴染みがあり、使いやすい Intune の機能を提供していきます。 更新された外観を確認するには、[アプリ UI の新機能](whats-new-app-ui.md)に関するページを参照してください。

## <a name="week-of-april-16-2018"></a>2018 年 4 月 16 日の週

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>iOS 向け Cisco AnyConnect クライアントを使用する <!-- 1333708 -->

iOS 用に新しい VPN プロファイルを作成するとき、**[Cisco AnyConnect]** と **[Cisco Legacy AnyConnect]** の 2 つの選択肢から選択できるようになりました。 Cisco AnyConnect プロファイルは、4.0.7x 以降のバージョンに対応しています。 既存の iOS Cisco AnyConnect VPN プロファイルは **[Cisco Legacy AnyConnect]** と表示されるようになり、現在と同じように Cisco AnyConnect 4.0.5x 以前のバージョンで引き続き動作します。

> [!NOTE]
> この変更は iOS にのみ適用されます。 Android、Android for Work、macOS プラットフォームの Cisco AnyConnect オプションは、これまでどおり 1 つだけです。

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Jamf 登録 macOS デバイスを Intune に登録できるようになりました <!-- 2370684 -->

macOS ポータル サイトのバージョン 1.3 と 1.4 では、Jamf デバイスが Intune に正常に登録されませんでした。 macOS ポータル サイトのバージョン 1.4.2 でこの問題が解決されました。


## <a name="week-of-april-9-2018"></a>2018 年 4 月 9 日の週  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Android 用ポータル サイト アプリでのヘルプ エクスペリエンスの更新 <!-- 1631531 -->

Android プラットフォームのベスト プラクティスに合うように、Android 用ポータル サイト アプリのヘルプ エクスペリエンスが更新されました。 ご使用のアプリで問題が発生した場合は、**[メニュー]** > **[ヘルプ]** の順にタップして、次のことが行えます。
- 診断ログを Microsoft にアップロードする。
- 問題とインシデント ID を記載した電子メールを社内のサポート担当者に送信する。  

更新されたヘルプ エクスペリエンスを確認するには、[[Send logs using email]\(メールでログを送信\)](/intune-user-help/send-logs-to-your-it-admin-by-email-android) および [[Send errors to Microsoft]\(エラーを Microsoft に送信\)](/intune-user-help/send-logs-to-microsoft-android) に進みます。


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>新しい登録エラー傾向グラフと失敗の理由テーブル <!-- 1471783 -->

[Enrollment Overview]\(登録の概要\) ページで、登録エラーの傾向と、上位 5 つのエラーの原因を表示することができます。 グラフやテーブルをクリックすると、トラブルシューティングのアドバイスや改善の提案の詳細にドリル ダウンすることができます。

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>アプリの保護ポリシーを構成する場所の更新 <!-- 2144597 -->

Azure Portal の Microsoft Intune サービスで、**[Intune アプリ保護]** サービス ブレードから **[モバイル アプリ]** ブレードに一時的にリダイレクトします。 すべてのアプリ保護ポリシーが Intune のアプリ構成の **[モバイル アプリ]** ブレードに既に置かれていることに注意してください。 Intune App Protection に移動する代わりに、Intune に移動します。 2018 年 4 月にリダイレクトを停止し、**[Intune App Protection]** サービス ブレードを完全に削除する予定です。したがって、Intune 内のアプリ保護ポリシーのための場所は 1 つだけになります。 

**ユーザーへの影響**
この変更は、Intune スタンドアロンのお客様とハイブリッド (Intune と Configuration Manager) のお客様の両方に影響します。 この統合は、クラウド管理の簡素化に役立ちます。

**この変更に対して必要な準備**
**[Intune アプリ保護]** サービス ブレードの代わりにお気に入りとして **Intune** に登録し、Intune の **[モバイル アプリ]** ブレードのアプリ保護ポリシーのワークフローを習熟してください。 リダイレクトを短期間行い、その後 **[アプリ保護]** ブレードを削除します。 ただし、すべてのアプリ保護ポリシーが既に Intune にあり、任意の条件付きアクセス ポリシーを変更することができます。 条件付きアクセス ポリシーの変更の詳細については、「[Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)」を参照してください。 詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」を参照してください。 


## <a name="week-of-april-2-2018"></a>2018 年 4 月 2 日の週

### <a name="intune-apps"></a>Intune アプリ

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>iOS 用ポータル サイト アプリに関するユーザー エクスペリエンスの更新プログラム <!--1412866 -->
iOS 用のポータル サイト アプリに対して、主要なユーザー エクスペリエンスの更新プログラムをリリースする予定です。 この更新プログラムでは、最新のルック アンド フィールを含む完全なビジュアル再設計が行われています。 アプリの機能を維持した上で、操作性とアクセシビリティが向上しています。  

また、次のような更新が行われています。
- iPhone X のサポート。
- アプリの起動および読み込み応答を速くして、ユーザー時間を節約。
- 最新の状態情報をユーザーに提供するための進行状況バーを追加。
- ログのアップロード方法を改善。これにより、問題が生じた場合に、その内容を簡単にレポートできる。  

更新された外観を確認するには、[アプリ UI の新機能](whats-new-app-ui.md)に関するページを参照してください。

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Intune APP および CA を使用したオンプレミス Exchange データの保護 <!-- 1056954 -->
Intune アプリ ポリシー保護 (APP) および条件付きアクセス (CA) を使用して、Outlook Mobile によるオンプレミスの Exchange データへのアクセスを保護できるようになりました。 Azure portal 内でアプリ保護ポリシーを追加または変更するには、**[Microsoft Intune]** > **[クライアント アプリ]** > **[アプリ保護ポリシー]** の順に選択します。 この機能を使用する前に、[iOS および Android 用 Outlook の要件](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx)を満たしていることを確認します。

## <a name="notices"></a>通知

### <a name="plan-for-change-intune-will-move-to-support-macos-1012-and-higher-in-december---2970975--"></a>変更の計画: Intune は 12 月に macOS 10.12 以降対応になります <!--2970975--> 

Apple が macOS 10.14 を公開しました。 それに続いて、2018 年 12 月、Intune は macOS 10.12 以降対応になります。 

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響

12 月以降、macOS 10.11 以前がインストールされているデバイスを使用しているエンド ユーザーは Intune に登録する目的でポータル サイトを使用できなくなります。 引き続きサポートを受け、新しい機能を受け取るには、macOS 10.12 以降にデバイスをアップグレードし、ポータル サイト アプリを最新版にアップグレードする必要があります。 

macOS 10.12 以降は現在、以下でサポートされています。 
- MacBook (2009 年後半以降) 
- iMac (2009 年後半以降)
- MacBook Air (2010 年後半以降)  
- MacBook Pro (2010 年後半以降) 
- Mac Mini (2010 年後半以降) 
- Mac Pro (2010 年後半以降) 

12 月以降、上記の一覧にある以外のデバイスをお持ちのエンドユーザーは、macOS 向けポータル サイト アプリの最新版にアクセスできなくなります。 macOS 10.12 以前のサポートのないバージョンを実行している既存の登録デバイスは引き続き管理対象であり、Intune 管理コンソールに表示されます。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備

- 2018 年 12 月までに、サポートされる OS バージョンにデバイスをアップグレードすることがエンド ユーザーに求められます。 
- 影響を受けるデバイスまたはユーザーについては、Azure コンソールの Intune レポートで確認してください。 [デバイス]、[すべてのデバイス]、の順に移動し、[OS] で絞り込みます。 組織の人で、macOS 10.11 を実行しているデバイスを持つ人を特定するのに役立つ列を追加できます。 
- ハイブリッド モバイル デバイス管理 (MDM) を使用している場合、Configuration Manager コンソールで [資産とコンプライアンス]、[デバイス] の順に選択し、列を右クリックして [オペレーティング システム] 列と [クライアント バージョン] 列を追加し、OS で絞り込みます。 ハイブリッド MDM が非推奨になりました。できるだけ早く、Azure での Intune に移行してください。 
 
#### <a name="additional-information"></a>追加情報
詳細については、「[ポータル サイト アプリで Intune に macOS デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp)」を参照してください。
 

### <a name="plan-for-change-new-intune-support-experience-for-premier-customers"></a>変更の計画: Premier のお客様のための新しい Intune サポート 
Microsoft Premier をご利用のお客様は現在、Microsoft Premier Online (MPO) ポータル (premier.microsoft.com) と Azure での Intune (portal.azure.com) を利用し、Intune のサポート要求を作成できます。 2018 年 12 月 3 日以降、Premier サポートを引き続き強化するには、Azure での Intune でのみサポート要求を作成できます。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
12 月 3 日以降、MPO ではサポート要求を作成できなくなります。  作成しようとすると、無視できないプロンプトが表示され、Azure での Intune にリダイレクトされます。 この "Azure での Intune" でサポート要求を作成できますが、作成された要求は、問題を診断し、遅れることなく解決する目的で、Intune 専用の Microsoft サポートに送信されます。 MPO で作成されたサポート要求は Azure portal で表示できません。そのため、MPO でサポート要求を作成することは止めてください。  

ハイブリッド MDM (ハイブリッド モバイル デバイス管理) を使用するか、共同管理を使用する場合、引き続き MPO を使用して Configuration Manager のサポート要求を作成できますが、Intune のサポート要求作成には Azure portal を使用してください。 もう一度お伝えしますが、ハイブリッド MDM は非推奨になりました。Azure での Intune への移行をできるだけ早く計画してください。 詳細については、「[Move from Hybrid Mobile Device Management to Intune on Azure](https://aka.ms/hybrid_notification)」 (ハイブリッド MDM から Azure での Intune に移行する) を参照してください。

役割としてグローバル管理者、Intune サービス管理者、サービス サポート管理者が与えられているユーザーのみが Azure portal でサポート チケットを作成できます。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
- MPO の使用を止め、Azure での Intune を使用し、Intune のすべてのサポート要求を作成し、管理します。  
- ヘルプデスクに通知し、必要に応じてドキュメントを更新します。
- グローバル管理者または Intune サービス管理者の役割を持たないユーザーが現在、MPO でサポート要求を作成している場合、引き続き Azure portal でサポート チケットを作成できるように、Azure Active Directory でそれらのユーザーにサービス サポート管理者の役割を与えてください。
- 詳細や便利なリンクについては、[追加情報] をクリックしてください。

#### <a name="additional-information"></a>追加情報
詳細については、[Microsoft Intune サポート チームのブログ投稿](https://aka.ms/IntuneSupport_MPO_to_Azure)を参照してください。


### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>アクションの実行: Intune でお使いの Android デバイスの制限またはコンプライアンス ポリシー パスワードの設定を更新してください。
Intune では、Android 4.4 以降のデバイスについて使用可能なパスワードの種類 "既定のデバイス" が削除されます。 Android プラットフォームと既定のデバイスの違いにより、そのポリシーはデバイスによってオプションとして扱われることがよくあります。 Android でこの設定が強制される場合についての混乱を解消するため、次回のリリースでこの設定を UI から削除します。 
#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
- デバイスでパスワードを要求することが望ましい場合は、"既定のデバイス" を使用する代わりに、Android プラットフォームのプロファイルを編集して、必要なパスワードの種類を明確に示すことをお勧めします。
- パスワードを作成するかどうかをエンド ユーザーに決定させることが望ましい場合は、[未構成] ボタンを選択します。 UI からこの設定が削除される時点で、設定がまだ有効になっていた場合は、次にプロファイルを編集するときに、[既定のデバイス] 以外の値を選択するよう求められます。
この変更に対して必要な準備
お使いの Android および Android エンタープライズ デバイスの制限とコンプライアンスのポリシーで、パスワードの設定を確認します。 これらの設定は、コンプライアンスのためのシステム セキュリティ ポリシー、およびデバイスの制限に関するデバイスのパスワードまたは作業プロファイルの設定にあります。 追加情報には、詳細情報およびこれらの設定の構成画面のスクリーンショットへのリンクがあります。
#### <a name="additional-information"></a>追加情報
https://aka.ms/PasswordSettings 

### <a name="plan-for-change-change-password-at-next-auth-added-to-intune---1873216---"></a>変更の計画: [次回の認証でパスワードを変更する] 設定を Intune に追加する <!-- 1873216 -->
9 月のサービス リリースで、Intune では、macOS バージョン 10.13 以降を実行しているデバイスについて、Apple が新しく公開した **[次回の認証でパスワードを変更する]** 設定を統合する予定です。 この設定の導入前は、MDM プロバイダーは、デバイスのパスコードがポリシーに準拠するように変更されたことを確認できませんでした。 Intune の構成とコンプライアンスのポリシーでは、次回デバイスのパスワードが変更されること、それがポリシー準拠として見なされることのみを検証されます。 Apple のこの新しい機能が追加されると、macOS ユーザーには、パスワードがポリシーに準拠していても更新するように要求が届きます。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
Intune またはハイブリッド MDM を使用している macOS デバイス ポリシーの環境に影響が出ます。 今回、Apple が **[次回の認証でパスワードを変更する]** 設定を備えたことで、Intune では、パスワード ポリシーがプッシュされたときにパスワードを更新するようにユーザーに強制できます。 デバイスがポリシー準拠であると見なされるまで会社のリソースをブロックすると、エンド ユーザーは自分のパスワードをリセットするまで、電子メールや SharePoint サイトなど、会社のリソースにアクセスできなくなる可能性があります。 今後、構成とコンプライアンスのパスワード ポリシーが更新されるたびに、対象となるユーザーには自分のパスワードの更新が強制されます。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
ヘルプデスクにお知らせください。 この macOS デバイス ポリシーを強制しない場合、既存の macOS ポリシーの割り当てを解除すること、あるいは削除さすることをお勧めします。 顧客調査により、ほとんどの顧客がこの変更の影響を受けないことが示されています。 ほとんどのエンド ユーザーはパスワードの登録要求またはリセット要求が届くと自分のパスワードを更新し、ポリシー準拠の状態を維持します。

### <a name="plan-for-change-intune-moving-to-tls-12"></a>変更の計画: Intune の TLS 1.2 への移行
2018 年 10 月 31 日以降、Intune では、サービスが既定でより安全であることを保障するため、また Microsoft Office 365 などの他の Microsoft 製品と並んでクラス最高の暗号化を提供できるよう、トランスポート層セキュリティ (TLS) プロトコル バージョン 1.2 をサポートするようになりました。 Office では、この変更を MC128929 でご連絡しています。

ポータル サイトも 2018 年 10 月 31 日に TLS 1.2 対応になります。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
2018 年 10 月 31 日以降、Intune では TLS プロトコル バージョン 1.0 または 1.1 はサポートしなくなります。 問題なく Intune に接続できるようにするには、すべてのクライアントとサーバー、およびブラウザーとサーバーの組み合わせで、接続を確保するために TLS バージョン 1.2 を使用する必要があります。 これらの変更は Intune ではサポートされていないが、引き続き Intune からポリシーを受け取っていて TLS バージョン 1.2 を使用できないエンド ユーザー デバイスには影響することに注意してください。 これには、Android 4.3 以前を実行するデバイスも含まれます。 影響を受けるデバイスやブラウザーの一覧については、以下の「追加情報」を参照してください。

2018 年 10 月 31 日以降、古い TLS のバージョンの使用に関連した問題が発生する場合、解決策の一環として TLS 1.2 に更新するか、TLS 1.2 をサポートするデバイスに更新する必要があります。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
環境から TLS 1.0 と 1.1 の依存関係を積極的に削除し、可能な場合にはオペレーティング システム レベルで TLS 1.0 と 1.1 を無効にすることをお勧めします。 今日、TLS 1.2 への移行を計画しましょう。 現在 Intune ではサポートされていないが、ポリシーを依然受け取っていて、TLS バージョン 1.2 では通信できないデバイス一覧を以下のサポートのブログ投稿で確認してください。 会社のリソースにアクセスできなくなることを、エンド ユーザーに通知する必要がある場合があります。

**追加情報**: [Intune moving to TLS 1.2 for encryption](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/) (Intune の暗号化の TLS 1.2 への移行)


### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>変更の計画: MDM 管理に今すぐ Azure で Intune を使用する <!-- 1227338 -->
1 年以上前、[Azure の Intune のパブリック プレビュー](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/)を発表し、その後、6 か月前に Intune の[新しい管理者エクスペリエンスを一般公開](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/)しました。 Intune スタンドアロンをご利用の場合、2018 年 8 月 31 日以降、従来の Silverlight コンソールではモバイル デバイス管理 (MDM) を使用できなくなります。 MDM が必要な場合は、代わりに [Azure 上の Intune](https://aka.ms/Intune_on_Azure) を使用できます。 まだ MDM に従来のコンソールを使用している場合は、使用を止め、Azure 上の Intune に慣れてください。 この変更によるエンド ユーザーへの影響はない予定です。 従来の PC 管理は Silverlight に残ります。 この変更とその影響については、[こちら](https://aka.ms/Intune_on_Azure_mdm)を参照してください。

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->
Apple は、Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。 詳細については、[Intune サポート ブログ](https://aka.ms/compportalats)を参照してください。



## <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](https://www.microsoft.com/cloud-platform/roadmap)
* [ポータル Web サイトの UI の新機能](whats-new-app-ui.md)
* [以前の月の新機能](whats-new-archive.md)
