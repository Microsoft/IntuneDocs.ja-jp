---
title: "新機能 | Microsoft Intune"
description: "Microsoft Intune の今月の新機能と過去のリリースの情報について説明します"
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79617dd41e51402a73759da792f581028095a2f5
ms.openlocfilehash: 65e53ad6a74fbf0e9249c367f517ab52ea0efa80


---

# Microsoft Intune の新機能
Microsoft Intune の今回のリリースの新機能について説明します。 また、過去のリリースに関する情報だけでなく、準備する必要がある今後の変更についても説明します。

今回のリリースの新機能を次に示します。 Windows Defender ポリシー設定の更新を除き、すべての新機能は、ハイブリッド環境 (Configuration Manager と Intune) でもサポートされます。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx)を参照してください。

## 2016 年 6 月
### Intune のサービス正常性
Intune のサービス正常性に関する情報は他の Microsoft サービスと共に中央の場所に移動されました。 そのため、この情報は Office 365 管理ポータルの [サービス正常性] で参照できるようになりました。 詳細については、[このブログ投稿](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)を参照してください。

## アプリ管理
- **Windows 10 の強化されたエンタープライズ データ ポリシー構成のエクスペリエンス。** Windows 10 のエンタープライズ データ保護ポリシー構成のエクスペリエンスが、アプリ規則の作成、ネットワーク境界の定義の指定、その他のエンタープライズ データ保護の設定などにおいて強化されました。 詳細については、「[Create an enterprise data protection (EDP) policy using Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)」(Microsoft Intune を使用してエンタープライズ データ保護 (EDP) ポリシーを作成する) を参照してください。


## デバイス管理
- **望ましくない可能性があるアプリから保護するための Windows Defender ポリシー設定。** **望ましくない可能性があるアプリケーションの検出**という名前の新しい Windows Defender 設定が、Windows 10 Desktop と Mobile の全般構成ポリシーに追加されました。 この設定を使えば、Windows Defender によって望ましくない可能性があると判断されたソフトウェアの実行から、登録済みの Windows デスクトップ コンピューターを保護することができます。 このようなアプリケーションの実行からコンピューターを保護したり、望ましくない可能性があるアプリケーションがいつインストールされたのかを監査モードでレポートしたりできます。 詳細については、「[Microsoft Intune の Windows 10 ポリシー設定](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)」を参照してください。
<!---TFS 1244478--->

## 条件付きアクセス
- **Intune の Cisco ISE ネットワーク アクセス制御ポリシー。**  Cisco Identity Service Engine (ISE) 2.1 と Microsoft Intune の両方を使用する場合、ISE でネットワーク アクセス制御ポリシーを設定できます。

    このポリシーを使用すると、WiFi または VPN でネットワークに接続するデバイスは、アクセスが許可される前に、次の条件を満たすことが必要になります。

    * Intune で管理されていること
    * 展開されているすべての Intune コンプライアンス ポリシーに準拠していること

 準拠していないデバイスのエンド ユーザーは、アクセスを取得するために、デバイスを登録することと、コンプライアンス関連の問題を修正することを求められます。
- **ブラウザーの条件付きアクセス。** [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md) と [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md) 用の条件付きアクセス ポリシーを設定すると、管理下にあって、かつ条件を満たした iOS デバイスと Android デバイス上のサポートされる Web ブラウザーに、Exchange Online と SharePoint Online へのアクセスを限定することができます。 Outlook Web Access (OWA) や SharePoint サイトにエンド ユーザーが iOS または Android デバイスでサインインしようとすると、そのデバイスを Intune に登録するよう求めるメッセージが表示されます。また条件を満たしていないことが問題になっている場合は、その問題を解消してから、サインインを試行するように求められます。
<!---TFS 1175844--->

- **Dynamics CRM Online では、条件付きアクセスをサポートしています。** [Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md) 用の条件付きアクセス ポリシーを設定すると、管理下にあって、かつ条件を満たした iOS デバイスと Android デバイスに、Dynamics CRM Online へのアクセスを限定することができます。 Dynamics CRM モバイル アプリにエンド ユーザーが iOS または Android でサインインしようとすると、Intune に登録するよう求めるメッセージが表示されます。また条件を満たしていないことが問題になっている場合は、その問題を修正してから、サインインを試行するように求められます。
<!---TFS1295358--->

## ポータル サイトの更新

### Android 用ポータル サイト アプリ

- IT 管理者が新しい [不明なソースからのアプリのインストールをデバイスが禁止することを必須にする (Android 4.0 以上)] ポリシーを適用すると、Android 4.0 以降のデバイスを使用するエンド ユーザーには、"不明なソースからのインストールを無効にする必要があります" というメッセージが表示されます。 ユーザーは、**[設定]** > **[セキュリティ]** を選択し、**[不明なソース]** を無効にする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を無効にする必要がある理由に関する詳細[情報](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android)を確認できます。

- IT 管理者が新しい [セキュリティ上の脅威に対してデバイスがアプリのスキャンを有効にすることを必須にする (Android 4.0 以上)] ポリシーを適用すると、Android 4.0 以降のデバイスを使用するエンド ユーザーには、"端末をスキャンしてセキュリティ上の脅威を確認" というメッセージが表示されます。 ユーザーは、**[設定]** > **[Google]** > **[セキュリティ]** を選択し、**[端末をスキャンしてセキュリティ上の脅威を確認]** をオンにする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を有効にする必要がある理由に関する詳細[情報](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)を確認できます。

- IT 管理者が新しい [USB デバッグの無効化を必須にする (Android 4.2 以上)] ポリシーを適用すると、Android 4.2 以降のデバイスを使用するエンド ユーザーには、"USB デバッグを無効にする必要があります" というメッセージが表示されます。 ユーザーは、**[設定]** > **[開発者オプション]** を選択し、**[USB デバッグ]** を無効にする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を無効にする必要がある理由に関する詳細[情報](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android)を確認できます。

- IT 管理者が新しい [最低限の Android セキュリティ パッチ レベル (Android 6.0 以上)] ポリシーを適用すると、Android 6.0 以降のデバイスを使用するエンド ユーザーには、"このデバイスは Android の最小セキュリティ パッチ レベルを満たしていません" というメッセージが表示されます。 ユーザーは必要なセキュリティ パッチをインストールする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、必要なセキュリティ パッチをインストールする方法と、現在インストールされているセキュリティ パッチに関する[情報](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)を確認できます。

### iOS ポータル サイト アプリ

- エンド ユーザーが基幹業務アプリをインストールするときの操作性が向上しています。 アプリのインストールに時間がかかる場合、ユーザーがデバイスを手動で同期させることによって、強制的に同期処理を再開することができます。 エンド ユーザー向けの手順については、「[デバイスを手動で同期する](/Intune/EndUser/sync-your-device-manually-ios)」を参照してください。

- iOS 向けの Microsoft Intune ポータル サイト アプリが更新され、iOS Version 8.0 以降をサポートするようになりました。 この更新は、デバイスで iOS Version 8.0 以降が実行されている場合にのみ、エンド ユーザーがポータル サイト アプリをインストールして Intune に新しいデバイスを登録できることを意味します。 サポートされていないバージョンの iOS が実行されているデバイスを登録済みの場合、ユーザーはそのデバイス上のポータル サイト アプリを引き続き使用できます。


## 今後の更新情報

### クラウドのロードマップ
[クラウド プラットフォームのロードマップ](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)では、Intune の今後の開発に関する情報を入手できます。

### 廃止予定のサービス
- **Intune Viewer アプリ。** 新しい RMS 共有アプリのリリースに伴い、2016 年 8 月以降、次の Intune Viewer アプリを削除する予定です。
    - Intune AV Viewer
    - Intune PDF Viewer
    - Google Play の Android 用 Intune Image Viewer

  Intune Viewer アプリを使用する代わりに、Android 用の新しい Rights Management アプリ (RMS 共有) を使用することをお勧めします。そうすることで、3 つのアプリを個別にではなく、1 つのアプリを展開して、Android デバイス上の企業ファイルを安全に表示することができます。

- **カスタム グループを対象とした通知規則の廃止。**
Intune の通知規則では、Intune からの電子メール アラートの送信先が定義されます。 現時点では、作成した Intune デバイス グループ内のデバイスのすべてのユーザーに電子メールを送信するように通知規則を構成することができます。 2016 年 6 月 1 日頃以降、ユーザーが作成したグループを対象とすることはできなくなります。

    現在、Microsoft Intune 管理コンソールから作成したグループを通知規則の対象とするには、以下の手順を実行します。

    **[管理者]** ワークスペースで、**[通知規則]** > **[新しい規則の作成]** の順にクリックします。

    通知規則の作成ウィザードの手順 2. で、規則の対象とするデバイス グループを選択します。 この "デバイス グループの選択" の手順は Intune コンソールから削除されます。

    この変更に向けた準備は次のように予定されています。
    - 2016 年 8 月に、新しいテナントでは通知規則の作成ウィザードの手順 2 が表示されなくなります。 既存のテナントは影響を受けません。
    - 2016 年 9 月頃に、既存の一部のテナントではウィザードの "デバイス グループの選択" が表示されなくなります。
    - 2016 年 11 月頃には、すべてのテナントでウィザードの "デバイス グループの選択" が表示されなくなる予定です。


- **iOS ポータル サイト アプリのサポートの変更**。 7 月には、iOS 用 Microsoft Intune ポータル サイト アプリのすべてのユーザーが、アプリの最新バージョンを使用するように要求されます。 新しいユーザーは最新バージョンのみをダウンロードでき、現在のユーザーは最新バージョンへの更新を求められます。 最新バージョンを使用するには iOS 8.0 以降が必要であり、デバイスで以前の iOS バージョンを実行している場合は、デバイスを iOS 8.0 以降に更新したうえでポータル サイト アプリを最新バージョンに更新するまで、ポータル サイトを使用できず、登録することもできません。 iOS 8.0 以前のバージョンを実行している登録済みのデバイスは、引き続き管理対象であり、Intune 管理コンソールに表示されます。





## 以前の Intune のリリース
過去 6 か月間に公開された Intune のリリースについては、「[以前の Intune のリリース](previous-intune-releases.md)」の記事をご覧ください。



### 関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Jul16_HO1-->


