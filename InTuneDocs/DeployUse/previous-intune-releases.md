---
title: "以前のリリース |Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 57570fcf2f738b68a01bb1c5fc8962c7ef117920
ms.openlocfilehash: 43546721245f92309d86c496dbcde7900a598ed0


---

# 以前の Intune のリリース
## 2016 年 7 月
### アプリ管理
#### アプリのプロビジョニング プロファイルの更新エクスペリエンスを向上
Apple iOS 基幹業務モバイル アプリは、プロビジョニング プロファイルを含み、証明書で署名されたコードと共に構築されます。 iOS デバイスでアプリを実行すると、iOS により iOS アプリの整合性の確認と、プロビジョニング プロファイルで定義されたポリシーの施行が行われます。

アプリの署名に使用するエンタープライズ署名証明書は、通常 3 年間は継続します。 ただし、プロビジョニング プロファイルは 1 年後に期限が切れます。 この更新により、証明書がまだ有効である期間中、Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルのポリシーを事前に展開するツールが用意されます。 詳細については、「[Use iOS mobile provisioning profile policies to keep your line of business apps up to date (基幹業務アプリケーションを常に最新の状態に保つために iOS モバイル プロビジョニング プロファイル ポリシーを使用する)](/intune/deploy-use/ios-mobile-app-provisioning-profiles)」を参照してください。
<!--- TFS 1280247--->
#### Intune アプリ用の Xamarin SDK の提供開始
Intune アプリ SDK Xamarin コンポーネントを使用すると、Xamarin でビルドされたモバイル iOS および Android アプリで Intune のモバイル アプリ管理機能を有効にすることができます。 [Xamarin ストア](https://components.xamarin.com/view/Microsoft.Intune.MAM)または、[Microsoft Intune の Github ページ](https://github.com/msintuneappsdk)でコンポーネントを見つけることができます。
<!--- TFS 1061478 --->

### デバイス管理
#### デバイス登録数上限の増加
Intune は、構成可能なデバイスの最大登録数をユーザーごとに 5 から 15 デバイスまで増加しました。
<!---TFS 1289896 --->

#### Intune クライアント ソフトウェアを実行する Windows PC のための TeamViewer の統合
Intune クライアントを実行する Windows PC の [TeamViewer](https://www.teamviewer.com) 統合により、Windows PC とのリモート アシスタント セッションを確立して、エンド ユーザーのヘルプ デスク部門をサポートできるようになります。 Windows 7、8、8.1、10 が対象となります。 詳細については、「[Microsoft Intune コンピューター クライアントを使用した一般的な Windows PC 管理タスク](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)」を参照してください。
<!---TFS 1284856--->

### ポータル サイトの更新
#### ポータル Web サイト
- **Windows デバイス登録時のエンドユーザー エクスペリエンスの向上**<br/>
条件付きアクセスを使用している場合の、ポータル サイト Web サイトで Windows 8.1、Windows 10 デスクトップ、および Windows 10 Mobile の登録手順が明確化されました。 今後は、「デバイス登録」および「社内参加」の手順が個別に表示されます。そのため、社内参加 (WPJ) の失敗後にデバイスの状態を確認し プロセスを完了することが簡単になります。 この手順の分離により、IT 管理者のトラブルシューティングのプロセスも簡略化されることが見込まれます。 これまで、エンド ユーザーが登録しようとして、WPJ を除くすべての登録が成功した場合、登録されたデバイスがデバイス一覧に表示されないため識別できず、ユーザーの混乱の原因となっていました。

#### Android
- **Android 用ポータル サイト アプリ**<br/>
Android エンド ユーザーに自分のデバイスに必要な証明書がないことを示すエラー メッセージが表示される場合、[How to resolve this (この問題解決する方法)] ボタンをタップすると、欠落している証明書をインストールするための[手順](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator)を取得できます。 ユーザーが手順を完了しても、追加の「証明書が見つかりません」というエラー メッセージが表示される場合は、IT 管理者に連絡し、この[リンク](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues)を提供することが求められます。このリンクには、証明書の問題を解決するために IT 管理者が使用できる手順が含まれています。

- **登録済みデバイスへのサイド ロード アプリのインストールの制限**<br/>
Android 用 Intune ポータル サイト アプリを使用してデバイスを Intune に登録している場合を除き、Android デバイスは、ポータル サイト Web サイトを通じてアプリケーションをインストールすることができなくなります。
<!---TFS 1299082--->

#### iOS
- **iOS ポータル サイト アプリのデバイス登録マネージャー アカウントへの変更**<br/>
パフォーマンスと拡張性を高めるために、Intune において、iOS のポータル サイト アプリの [**デバイス**] ウィンドウには今後、デバイス登録マネージャー (DEM) のデバイスの一部が表示されなくなります。 アプリを実行しているローカル デバイスのみ、ポータル サイト アプリ経由で登録されている場合にだけ表示されます。

ローカル デバイスに対する操作は DEM で実行できますが、他の登録デバイスのリモート管理は、Intune 管理コンソールから実行する必要があります。 また、Apple Device Enrollment Program または Apple Configurator ツールでの DEM アカウントの使用は廃止されます。 共有 iOS デバイスに関しては、どちらの登録手段も既にユーザーレスの登録がサポートされています。

共有デバイスのユーザーレスの登録が利用できない場合のみ DEM アカウントを使用してください。 詳細については、「[Microsoft Intune のデバイス登録マネージャーを使用した企業所有のデバイスの登録](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)」を参照してください。
<!---TFS 1233681--->

### Windows 機能の名前の変更
- [Microsoft Passport for Windows](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) は **Windows Hello for Business** と呼ばれるようになりました。
- [エンタープライズ データ保護](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)は **Windows Information Protection** と呼ばれるようになりました。

## 2016 年 6 月
### Intune のサービス正常性
Intune のサービス正常性に関する情報は他の Microsoft サービスと共に中央の場所に移動されました。 そのため、この情報は Office 365 管理ポータルの [サービス正常性] で参照できるようになりました。 詳細については、[このブログ投稿](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)を参照してください。

### アプリ管理
- **Windows 10 の強化されたエンタープライズ データ ポリシー構成のエクスペリエンス。** Windows 10 のエンタープライズ データ保護ポリシー構成のエクスペリエンスが、アプリ規則の作成、ネットワーク境界の定義の指定、その他のエンタープライズ データ保護の設定などにおいて強化されました。 詳細については、「[Create an enterprise data protection (EDP) policy using Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)」(Microsoft Intune を使用してエンタープライズ データ保護 (EDP) ポリシーを作成する) を参照してください。


### デバイス管理
- **望ましくない可能性があるアプリから保護するための Windows Defender ポリシー設定。** **望ましくない可能性があるアプリケーションの検出**という名前の新しい Windows Defender 設定が、Windows 10 Desktop と Mobile の全般構成ポリシーに追加されました。 この設定を使えば、Windows Defender によって望ましくない可能性があると判断されたソフトウェアの実行から、登録済みの Windows デスクトップ コンピューターを保護することができます。 このようなアプリケーションの実行からコンピューターを保護したり、望ましくない可能性があるアプリケーションがいつインストールされたのかを監査モードでレポートしたりできます。 詳細については、「[Microsoft Intune の Windows 10 ポリシー設定](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)」を参照してください。
<!---TFS 1244478--->

### 条件付きアクセス
- **Intune の Cisco ISE ネットワーク アクセス制御ポリシー。**  Cisco Identity Service Engine (ISE) 2.1 と Microsoft Intune の両方を使用する場合、ISE でネットワーク アクセス制御ポリシーを設定できます。

    このポリシーを使用すると、WiFi または VPN でネットワークに接続するデバイスは、アクセスが許可される前に、次の条件を満たすことが必要になります。

    * Intune で管理されていること
    * 展開されているすべての Intune コンプライアンス ポリシーに準拠していること

 準拠していないデバイスのエンド ユーザーは、アクセスを取得するために、デバイスを登録することと、コンプライアンス関連の問題を修正することを求められます。
- **ブラウザーの条件付きアクセス。** [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md) と [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md) 用の条件付きアクセス ポリシーを設定すると、管理下にあって、かつ条件を満たした iOS デバイスと Android デバイス上のサポートされる Web ブラウザーに、Exchange Online と SharePoint Online へのアクセスを限定することができます。 Outlook Web Access (OWA) や SharePoint サイトにエンド ユーザーが iOS または Android デバイスでサインインしようとすると、そのデバイスを Intune に登録するよう求めるメッセージが表示されます。また条件を満たしていないことが問題になっている場合は、その問題を解消してから、サインインを試行するように求められます。
<!---TFS 1175844--->

- **Dynamics CRM Online では、条件付きアクセスをサポートしています。** [Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md) 用の条件付きアクセス ポリシーを設定すると、管理下にあって、かつ条件を満たした iOS デバイスと Android デバイスに、Dynamics CRM Online へのアクセスを限定することができます。 Dynamics CRM モバイル アプリにエンド ユーザーが iOS または Android でサインインしようとすると、Intune に登録するよう求めるメッセージが表示されます。また条件を満たしていないことが問題になっている場合は、その問題を修正してから、サインインを試行するように求められます。
<!---TFS1295358--->

##E 会社のポータルの更新

#### Android 用ポータル サイト アプリ

- IT 管理者が新しい [不明なソースからのアプリのインストールをデバイスが禁止することを必須にする (Android 4.0 以上)] ポリシーを適用すると、Android 4.0 以降のデバイスを使用するエンド ユーザーには、"不明なソースからのインストールを無効にする必要があります" というメッセージが表示されます。 ユーザーは、**[設定]** > **[セキュリティ]** を選択し、**[不明なソース]** を無効にする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を無効にする必要がある理由に関する詳細[情報](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android)を確認できます。

- IT 管理者が新しい [セキュリティ上の脅威に対してデバイスがアプリのスキャンを有効にすることを必須にする (Android 4.0 以上)] ポリシーを適用すると、Android 4.0 以降のデバイスを使用するエンド ユーザーには、"端末をスキャンしてセキュリティ上の脅威を確認" というメッセージが表示されます。 ユーザーは、**[設定]** > **[Google]** > **[セキュリティ]** を選択し、**[端末をスキャンしてセキュリティ上の脅威を確認]** をオンにする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を有効にする必要がある理由に関する詳細[情報](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)を確認できます。

- IT 管理者が新しい [USB デバッグの無効化を必須にする (Android 4.2 以上)] ポリシーを適用すると、Android 4.2 以降のデバイスを使用するエンド ユーザーには、"USB デバッグを無効にする必要があります" というメッセージが表示されます。 ユーザーは、**[設定]** > **[開発者オプション]** を選択し、**[USB デバッグ]** を無効にする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を無効にする必要がある理由に関する詳細[情報](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android)を確認できます。

- IT 管理者が新しい [最低限の Android セキュリティ パッチ レベル (Android 6.0 以上)] ポリシーを適用すると、Android 6.0 以降のデバイスを使用するエンド ユーザーには、"このデバイスは Android の最小セキュリティ パッチ レベルを満たしていません" というメッセージが表示されます。 ユーザーは必要なセキュリティ パッチをインストールする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、必要なセキュリティ パッチをインストールする方法と、現在インストールされているセキュリティ パッチに関する[情報](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)を確認できます。

#### iOS ポータル サイト アプリ

- エンド ユーザーが基幹業務アプリをインストールするときの操作性が向上しています。 アプリのインストールに時間がかかる場合、ユーザーがデバイスを手動で同期させることによって、強制的に同期処理を再開することができます。 エンド ユーザー向けの手順については、「[デバイスを手動で同期する](/Intune/EndUser/sync-your-device-manually-ios)」を参照してください。

- iOS 向けの Microsoft Intune ポータル サイト アプリが更新され、iOS Version 8.0 以降をサポートするようになりました。 この更新は、デバイスで iOS Version 8.0 以降が実行されている場合にのみ、エンド ユーザーがポータル サイト アプリをインストールして Intune に新しいデバイスを登録できることを意味します。 サポートされていないバージョンの iOS が実行されているデバイスを登録済みの場合、ユーザーはそのデバイス上のポータル サイト アプリを引き続き使用できます。


## 2016 年 5 月

これらの機能はすべて、Configuration Manager と Intune のハイブリッド環境でもサポートされます。 新しいハイブリッド機能の詳細については、[ハイブリッド環境の新機能](https://technet.microsoft.com/en-us/library/mt718155.aspx)に関するページを参照してください。

### ドキュメント
プレビュー バージョンの [docs.microsoft.com](https://docs.microsoft.com/en-us/intune) へようこそ。
これはまったく新しい最新コンテンツのプラットフォームです。お客様がより簡単に Intune を理解し、使用できるように設計されています。
すべての新しい機能については、「[Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)」 (docs.microsoft.com の概要) を参照してください。

### Intune のサービス正常性
Intune のサービス正常性に関する情報は他の Microsoft サービスと共に中央の場所に移動されました。 そのため、この情報は [Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)の **[サービス正常性]** で参照できるようになりました。
詳細については、[このブログ投稿](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)を参照してください。


### アプリ管理
- **MAM SDK: PIN の長さの構成に対応。** デバイス PIN と同様、MAM アプリに使用する PIN の長さを指定できるようになります。 この場合エンド ユーザーは、管理者が設定した新しい制限に従う必要があります。 入力文字数が増える分、PIN 画面の外観が若干調整されます。 詳細については、「[MAM policy settings for Android](android-mam-policy-settings.md)」 (Android 用 MAM ポリシー設定) および「[MAM policy settings for iOS](ios-mam-policy-settings.md)」 (iOS 用 MAM ポリシー設定) を参照してください。

- **iOS および Android 用 Skype for Business。** Skype for Business を [MAM の対象にできるようになりました (登録ポリシー不要)](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)。 ユーザーがログインすると、MAM ポリシーが適用されます。

- **MAM ポリシーで管理できるようになった新しいアプリ。** Android 用の Microsoft Word、Excel、および PowerPoint の各アプリを、Intune に登録されていないデバイス上の MAM ポリシーに関連付けられるようになりました。 サポートされているアプリの完全なリストについては、[Microsoft Intune アプリケーション パートナー](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) ページの Microsoft Intune モバイル アプリケーション ギャラリーを参照してください。


### ポータル サイトの更新

#### Android 用ポータル サイト アプリ
- **エンドユーザーへのトースト通知**: エンドユーザーがポータル サイトからデバイスの登録または削除を行う際に、Android ポータル サイト アプリからのトースト通知が表示されるようになりました。

- **Android ポータル サイト アプリでのデバイス登録マネージャー アカウントへの変更。** パフォーマンスと拡張性を高めるために、Intune の Android ポータル サイト アプリの [デバイス] ペインには、すべてのデバイス登録マネージャー (DEM) デバイスが表示されなくなります。 アプリを実行しているローカル デバイスのみ、ポータル サイト アプリ経由で登録されている場合にだけ表示されます。 ローカル デバイスに対する操作は DEM で実行できますが、他の登録デバイスのリモート管理は、Intune 管理コンソールから実行する必要があります。

#### ポータル Web サイト
- **ポータル Web サイト: デバイス ID バナーによってエンド ユーザーへの情報提供を拡充。** エンド ユーザーは、ポータル Web サイトを使用する際に選択したデバイスをより簡単に特定できるようになりました。 間違ったデバイスを選択した場合は、ホーム ページ バナーの **[ここをタップ]** リンクをタップして正しいデバイスを選択できます。

## 今後の更新情報
- **メッセージ センターの UI オンボード**。 [Office 365 管理ポータル](https://portal.office.com/)に Intune を移行する取り組みの一環として、新機能をはじめとする告知にメッセージ センターを活用することとなりました。 また Office 365 Admin モバイル コンパニオン アプリをインストールすることによって通知を携帯電話で受け取り、ユーザーや配布リストに宛てて簡単にメッセージを転送することもできます。
メッセージ センターの運用は、5 月リリースからとなります。更新プログラムが完成した時点で通知します。Intune に追加された機能や強化された機能についての情報を盛り込む予定です。 メッセージ センターの情報をチェックするには、[Office 365 管理ポータル](https://portal.office.com/)にログインし、左側のナビゲーション ウィンドウでメッセージ センターのオプションを選択してください。

- **デバイス登録マネージャー アカウントへの変更**。 パフォーマンスと拡張性を高めるために、Intune の iOS ポータル サイト アプリの **[デバイス]** ペインには、**すべて**のデバイス登録マネージャー (DEM) デバイスが表示されなくなります。 アプリを実行しているローカル デバイスのみ、ポータル サイト アプリ経由で登録されている場合にだけ表示されます。 ローカル デバイスに対する操作は DEM で実行できますが、他の登録デバイスのリモート管理は、Intune 管理コンソールから実行する必要があります。 また、Apple Device Enrollment Program または Apple Configurator ツールでの DEM アカウントの使用は廃止されます。 共有 iOS デバイスに関しては、どちらの登録手段も既にユーザーレスの登録がサポートされています。 共有デバイスのユーザーレスの登録が利用できない場合のみ DEM アカウントを使用してください。

### クラウドのロードマップ
[クラウド プラットフォームのロードマップ](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)では、Intune の今後の開発に関する情報を入手できます。

### 廃止予定のサービス
- **Intune Viewer アプリ。** 新しい RMS 共有アプリのリリースに伴い、2016 年 8 月以降、次の Intune Viewer アプリを削除する予定です。
    - Intune AV Viewer
    - Intune PDF Viewer
    - Google Play の Android 用 Intune Image Viewer

  Intune Viewer アプリを使用する代わりに、Android 用の新しい Rights Management アプリ (RMS 共有) を使用することをお勧めします。そうすることで、3 つのアプリを個別にではなく、1 つのアプリを展開して、Android デバイス上の企業ファイルを安全に表示することができます。 RMS 共有アプリ (ドキュメントへのリンクを含む) の詳細を確認してください。

- **カスタム グループを対象とした通知規則の廃止。**
Intune の通知規則では、Intune からの電子メール アラートの送信先が定義されます。 現時点では、作成した Intune デバイス グループ内のデバイスのすべてのユーザーに電子メールを送信するように通知規則を構成することができます。 2016 年 6 月 1 日頃以降、ユーザーが作成したグループを対象とすることはできなくなります。

    現在、Microsoft Intune 管理コンソールから作成したグループを通知規則の対象とするには、以下の手順を実行します。

    **[管理者]** ワークスペースで、**[通知規則]** > **[新しい規則の作成]** の順にクリックします。

    通知規則の作成ウィザードの手順 2. で、規則の対象とするデバイス グループを選択します。 この "デバイス グループの選択" の手順は Intune コンソールから削除されます。

    この変更に向けた準備は次のように予定されています。
    - 2016 年 6 月に、新しいテナントでは通知規則の作成ウィザードの手順 2. が表示されなくなります。 既存のテナントは影響を受けません。
    - 2016 年 8 月頃に、既存の一部のテナントではウィザードの "デバイス グループの選択" が表示されなくなります。
    - 2016 年 10 月頃には、すべてのテナントでウィザードの "デバイス グループの選択" が表示されなくなる予定です。


- **iOS ポータル サイト アプリのサポートの変更**。 今後数か月で、iOS 用 Microsoft Intune ポータル サイト アプリが更新され、iOS 8.0 以降を実行しているデバイスのみがサポートされるようになります。 したがって、ユーザーは iOS 8.0 より前のバージョンを実行する新しいデバイスを登録できなくなります。 iOS 8.0 より前のバージョンを実行している登録済みのデバイスは引き続き管理されます。また、期間限定で、ポータル サイト アプリも引き続き使用できます。 ただし、最新バージョンのポータル サイト アプリにアクセスする場合、デバイスは iOS 8.0 以降にある必要があります。 新しい Intune の機能を最大限に活用するには、iOS 8.0 以降に更新するようユーザーに通知することをお勧めします。  


## 2016 年 4 月
これらの機能はすべて、Configuration Manager と Intune のハイブリッド環境でもサポートされます。
### アプリ管理
- **MAM ユーザー コンプライアンス。**
Azure Active Directory (AAD) テナント内の任意のユーザーについて、アプリケーション管理ポリシーの[状態](monitor-mobile-app-management-policies-with-Microsoft-Intune.md)を表示できるようになりました。 以下は、必要な操作の例です。
   - [デバイス]
   - デバイス上のアプリ

   ステータス値:

   **チェックイン**: ポリシーがユーザーに展開されていること、仕事のコンテキストでアプリが使用されていること、正常にポリシーが配信されたことを示します。

    **チェックイン未**: ポリシーはユーザーに展開されましたが、それ以降にアプリが仕事のコンテキストで使用されていないことを示します。


- **Outlook 連絡先の同期 (Android) ができないよう MAM によって制御。**
[モバイル アプリケーションの管理](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)に、デバイスを登録せずに行える新しい設定が追加されました。 この設定を使用して、Android デバイス上のネイティブのアドレス帳と連絡先との同期をアプリケーションに禁止することができます。 この設定を有効にすると、対象アプリケーションはネイティブのアドレス帳に連絡先を保存できなくなります。 この設定を無効にすると、対象アプリケーションはネイティブのアドレス帳に連絡先を保存できるようになります。 [デバイスまたはアプリをリモートからワイプ](wipe-managed-company-app-data-with-Microsoft-Intune.md)すると、ネイティブのアドレス帳に保存されているすべての連絡先が削除されます。 この新しい設定は最初に、Android デバイスの Outlook アプリケーションでサポートされます。

### デバイス管理
- **会社が所有するデバイスの電話番号の識別。** 会社の所有として分類される電話は今後、完全な電話番号で識別されます (モバイル デバイスのインベントリ レポートを実行するときなど)。 BYOD デバイスの電話番号は引き続き **** でマスクされ、表示されるのは最後の 4 桁のみとなります。


### ポータル サイトの更新
**Android 用ポータル サイト アプリ** まだ Intune にデバイスを登録していないユーザーや適切な証明書がインストールされていないユーザーには、"必要な証明書がデバイスに見つからないため、サインインできません" というメッセージが表示され、Android ポータル サイト アプリにサインインできなくなります。 このメッセージには "この問題を解決する方法" というリンクが表示され、ユーザーはこれをタップして証明書のインストール手順を参照できます。 エンド ユーザーが問題を解決するための手順については、「[デバイスに必要な証明書がない](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing)」を参照してください。

**iOS ポータル サイト アプリ** 引き下げて更新する操作に対応しました。ホーム画面上のコンテンツ (アプリやデバイスの一覧、IT 連絡先情報など) をこの操作で最新の情報に更新することができます。 準拠状況やポリシー情報については、引き下げて更新する操作ではチェックされません。これらの情報をチェックするには、現在のデバイスのタイルを選択し、**[同期]** ボタンをタップしてください。

**Windows 10 Mobile と Windows Phone 8.1 ポータル サイト アプリ** エンド ユーザーが基幹業務アプリをインストールするときの操作性が向上しています。 アプリのインストールに時間がかかる場合、ユーザーがデバイスを手動で同期させることによって、強制的に同期処理を再開することができます。 エンド ユーザー向けの手順については、[デバイスを手動で同期させることによってアプリのインストールを高速化する方法](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually)に関するページを参照してください。

**ポータル サイト Web サイト** Windows 10 Mobile ユーザーまたは Windows Phone 8.1 ユーザーが基幹業務アプリをインストールするときに、今後は新しく以下のステータスが表示されます。これらのステータスによって、インストールの状態を従来よりも詳しく知ることができます。

* **[デバイスが同期されるのを待機しています]** – ユーザーが [インストール] をタップした後、デバイスが Intune インフラストラクチャとの同期を試みます。 インストールが完了するためには、同期が完了している必要があります。 "デバイスが同期されるのを待機しています" のメッセージはリンクになっていて、同期処理に時間がかかっていたり、途中で止まったりした場合に、ユーザーがこのリンクをタップすると、デバイスを手動で Intune と同期させるための[手順](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually)が表示されます。
* **[ダウンロード中]** – ユーザーのダウンロード要求が処理されています。デバイスは、アプリのダウンロードとインストールを実行しています。

これらのステータスが追加されるまでは、表示されるステータスが "インストール中" のみで、これが何時間も画面に表示された状態に陥ることもあったため、アプリのインストールに時間がかかった場合にユーザーが混乱する原因となっていました。 新しくステータスが追加されることで、ユーザーはサポートに問い合わせなくても、"デバイスが同期されるのを待機しています" のリンクをタップし、画面の指示に従うことで同期処理を強制的に再開できるようになります。


## 2016 年 3 月
### 2016 年 3 月 29 日時点での新機能
2016 年 3 月 29 日にリリースされるすべての機能は、Windows 10 の全般構成ポリシーに対する更新を除き、ハイブリッド ユーザー (Intune に Configuration Manager が統合) でもサポートされます。 Windows 10 の全般構成ポリシーに対する更新は、近日ハイブリッドでサポート対象となる予定です。 なお、これらの一部の機能では、Configuration Manager の最新バージョンが必要であることに注意してください。

### アプリ管理
- **Outlook の連絡先の同期を防ぐ MAM コントロール (iOS)。** モバイル アプリケーションの管理に、デバイスを登録せずに行える新しい設定が用意されました。 この設定を使用すると、アプリケーションが iOS デバイスのネイティブのアドレス帳と連絡先を同期しなくなります。 この設定を有効にすると、アプリはネイティブのアドレス帳に連絡先を保存しなくなります。 この設定を無効にすると、アプリはネイティブのアドレス帳に連絡先を保存するようになります。 デバイスで選択的ワイプを実行すると、ネイティブのアドレス帳に保存されているすべての連絡先が削除されます。 この新しい設定は、iOS デバイスの Outlook アプリケーションでサポートされています。 この設定およびその他の設定の詳細については、「[MAM ポリシーの作成および展開](https://technet.microsoft.com/en-us/library/dn292747.aspx)」を参照してください。

### アクセス制御
- **Skype for Business Online では、条件付きアクセスをサポートしています。** Skype for Business Online で条件付きアクセス ポリシーを設定すると、管理されている準拠している iOS および Android デバイスからのみそれにアクセスできるようになります。 Skype for Business モバイル アプリにエンド ユーザーが iOS または Android でサインインしようとすると、Intune に登録するよう求めるメッセージが表示されます。また条件を満たしていないことが問題になっている場合は、その問題を解消してから、サインインを試行するように求められます。 詳細については、「[Manage access to Skype for Business Online](https://technet.microsoft.com/en-us/library/mt695297.aspx)」 (Skype for Business Online へのアクセスの管理) を参照してください。

### デバイス管理
- **Intune の iOS 9.3 のサポート。** Apple は、3 月 21 日 (月) に iOS 9.3 のリリースを発表しました。 Apple のこの最新バージョンのモバイル オペレーティング システムに準拠するよう懸命に努めた結果、ここで Microsoft Intune で [iOS 9.3 デバイスの管理をサポートできるようになったことを謹んで発表します](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/)。

  現在利用できる iOS デバイスを管理するすべて既存の Intune 機能は、ユーザーがデバイスを iOS 9.3 にアップグレードすることによってシームレスに機能し続けます。 さらに、ハイブリッド ユーザー (Configuration Manager を使用した Intune) も iOS 9.3 を使用できるようになりました。

- **Windows 10 の全般構成ポリシーには、登録済みの Windows 10 PC 上の Windows Defender を管理する設定が含まれるようになりました。** 詳細については、「[Microsoft Intune の Windows 10 構成ポリシー設定](https://technet.microsoft.com/en-us/library/mt404697.aspx)」を参照してください。


### 会社のポータル

- **Windows アプリ パッケージが、ポータル サイト Web サイトから直接入手できるようになりました。** Windows 8、Windows 8.1 および Windows RT PC を使用しているユーザーは、ポータル サイト Web サイトから、直接アプリ パッケージ (拡張子は .appx) をインストールできます。 これまで、アプリをインストールするには、管理者が展開するか、ユーザーがポータル サイト アプリをデバイスにインストールする必要がありました。

- **ポータル サイト Web サイトを使用すると、ユーザーはデバイスをリモートからロックできます。** ユーザーがデバイスを紛失したり、デバイスの盗難にあった場合に、デバイスをリモートでロックできる新しいリモート ロック オプションがポータル サイト Web サイトに追加されました。 [エンドユーザー向け手順](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock)を参照してください。 Intune スタンドアロンと Configuration Manager を使用した Intune の、プラットフォームでのリモート ロックのサポートは次の表のとおりです。

|プラットフォーム | サポートの詳細|
|---------|----------------|
|Android |サポート|
|iOS |サポート|
|[Windows] 10 Mobile |電話でパスコードが設定されている場合のみサポート|
|[Windows] 10 Desktop |サポートされていません|
|Windows Phone 8。1 |電話でパスコードが設定されている場合のみサポート|
|Windows Phone 8。0 |サポートされていません|
|PC (Windows 8.0 以前) |サポートされていません|
|PC (Windows 8.1) |サポートされていません|

### 2016 年 3 月 10 日時点での新機能

### アプリ管理

- **サード パーティ製 MDM ソリューションに登録されているデバイスについては、iOS の [開く] 管理を利用できる** iOS の [開く] 管理を利用するために、サードパーティ製モバイル デバイス管理 (MDM) のベンダーを使用できます。 構成プロファイルの設定で制限を設定し、「[Manage data transfer between iOS apps](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)」 (iOS アプリ間のデータ転送を管理する) を使用して、アプリを展開できます。

     この方法には、次の 2 つの主な利点があります。

     1. ユーザーは、Cloud Services またはその他のアプリから企業データにアクセスする前に、仕事用アカウントでログインすることを求められます。 これにより、データにアクセスする際にモバイル アプリ管理 (MAM) ポリシーが確実に適用されます。

     2. サードパーティ製の MDM ソリューションで展開された管理対象のメール プロファイルおよびその他の管理対象アプリは、Intune MAM ポリシーを持つアプリとの間でファイルやデータを共有できます。

- **Intune に登録されていないデバイスの Microsoft Outlook アプリを MAM ポリシーで管理できる** Intune モバイル アプリケーション管理ポリシーを使用して、Intune で登録されていないデバイス上の Microsoft Outlook アプリを管理できるようになりました。 MAM 機能を備えた最新の Microsoft Outlook アプリは、[iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8) デバイスと [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook) デバイスの両方で使用可能です。 MAM ポリシーを作成するには、「[モバイル アプリ管理ポリシーの作成および展開](https://technet.microsoft.com/library/mt627829.aspx)」の指示に従ってください。  


- **モバイル アプリの構成ポリシーによって iOS アプリのユーザーの詳細をより柔軟に指定できる** iOS アプリを開いたときに必要になる可能性のあるユーザー設定を指定できます。 たとえば、ネットワーク ポートやユーザー名を指定できます。 詳細については、「[Microsoft Intune のモバイル アプリ構成ポリシーを使用した iOS アプリの構成](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md)」を参照してください。


- **企業内の Intune で管理された iOS デバイスに Adobe Reader for Microsoft Intune を展開できる** Intune モバイル アプリケーション管理ポリシーを使用して、登録済みのデバイスで iOS 用の Adobe Reader アプリを管理できるようになりました。

- **展開された Web クリップが Managed Browser で開かれるようになった** 対象となる Web クリップを iOS および Android デバイスに展開し、Managed Browser のみを使用して開くことができます。 たとえば、社内ポータル サイトを通して社内リソースへのリンクを展開したときに、ユーザーがリンクにナビゲートすると、MAM ポリシーによって保護されている Managed Browser でリンクが直接開きます。 詳細については、「[アプリの展開](deploy-apps.md)」を参照してください。


- **Intune 管理者コンソールから Windows 10 デバイスのビジネス向け Windows ストア アプリを検索、管理、配布できる** Intune では、ビジネス向け Windows ストアのサポートを使用して、アプリを検索および管理し、管理対象 Windows 10 デバイスに配布できます。 ビジネス向け Windows ストアでは、Intune 管理者コンソール (他のアプリを管理するときに使用する同じコンソール) から、これらのアプリを展開および監視するプロセスを管理できます。 具体的には、ビジネス向け Windows ストアは「オンライン ライセンスされたアプリ」のコンテンツとライセンスを管理します。 詳細については、「[ビジネス向け Windows ストアから購入したアプリを管理する](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md)」を参照してください。


### デバイス管理
- **iOS デバイス用の PFX 証明書を配布できる** Intune 管理者は、iOS デバイスの Wi-Fi、メール、VPN 認証用の iOS PFX 証明書を作成して展開できます。 この機能は、Android および Windows 10 デバイスで既に利用可能です。 詳細については、「[証明書ポリシーを使用して会社のリソースへのアクセスを有効にする](secure-resource-access-with-certificate-profiles.md)」を参照してください。


- **ユーザーのカテゴリ選択に基づいて別のデバイス グループにアプリとポリシーを適用できる** Intune 管理者は、登録時にユーザーが選ぶカスタム デバイス カテゴリを定義できるようになりました。 たとえば、管理者は、登録するデバイスの用途が「レジ」、「配送トラック」、「インベントリ室」かどうかをユーザーに指定させることができます。 カテゴリを選ぶことで、デバイスは Intune デバイス グループのメンバーになり、このグループを使用して登録済みのデバイスに異なるアプリとポリシーを展開できます。 詳細については、「[デバイス グループのマッピングを使用してデバイスを分類する](categorize-devices-with-device-group-mapping-in-microsoft-intune.md)」を参照してください。

### Microsoft ポータル サイトの変更と更新
このリリースでは、ポータル サイトに次の変更が加えられました。

**Android 用ポータル サイト アプリ**

* モバイル アプリケーション管理 (MAM) によって管理されているアプリをユーザーが起動すると、アプリが会社によって管理されていることを通知するメッセージが表示されます。 ユーザーは、ここで「詳細情報」リンクをタップして、「管理対象アプリ」に関する[詳細情報](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps)を取得できるようになりました。 「次回から表示しない」をタップして、アプリの起動時にこのメッセージが表示されないようにすることもできます。
* ユーザーに登録プロセスを案内し、ユーザーが登録すべき理由、および登録済みのデバイスで IT 管理者が表示できる内容とできない内容について詳しく説明するための新しい画面が追加されました。 詳細については、「[登録手順](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc)」を参照してください。
* ポータル サイト アプリに登録のエラー メッセージが表示されるようになりました。 これらのメッセージは、以前はポータル サイト Web サイトに表示されていました。 この変更は、すべてのエラー メッセージが 2 つの異なる場所ではなく、1 か所にまとめて表示されることを意味しています。


**iOS ポータル サイト アプリ**
* モバイル アプリケーション管理 (MAM) によって管理されているアプリをユーザーが起動すると、アプリが会社によって管理されていることを通知するメッセージが表示されます。 ユーザーは、ここで「詳細情報」リンクをタップして、「管理対象アプリ」に関する[詳細情報](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps)を取得できるようになりました。 「次回から表示しない」をタップして、アプリの起動時にこのメッセージが表示されないようにすることもできます。
* ユーザーに登録プロセスを案内し、ユーザーが登録すべき理由、および登録済みのデバイスで IT 管理者が表示できる内容とできない内容について詳しく説明するための新しい画面が追加されました。 詳細については、「[登録手順](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device)」を参照してください。
* ポータル サイト アプリに登録のエラー メッセージが表示されるようになりました。 これらのメッセージは、以前はポータル サイト Web サイトに表示されていました。 この変更は、すべてのエラー メッセージが 2 つの異なる場所ではなく、1 か所にまとめて表示されることを意味しています。




## 2016 年 2 月
### Microsoft ポータル サイトの変更と更新

このリリースでは、ポータル サイトに次の変更が加えられました。

#### Android 用ポータル サイト アプリ
- ユーザーに登録プロセスを案内し、ユーザーが登録すべき理由、および登録済みのデバイスで IT 管理者が表示できる内容とできない内容について詳しく説明するための新しい画面が追加されました。 詳細については、「[登録手順](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc)」を参照してください。
- ポータル サイト アプリに登録のエラー メッセージが表示されるようになりました。 これらのメッセージは、以前はポータル サイト Web サイトに表示されていました。 この変更は、すべてのエラー メッセージが 2 つの異なる場所ではなく、1 か所にまとめて表示されることを意味しています。

#### iOS ポータル サイト アプリ
 - ユーザーに登録プロセスを案内し、ユーザーが登録すべき理由、および登録済みのデバイスで IT 管理者が表示できる内容とできない内容について詳しく説明するための新しい画面が追加されました。 詳細については、「[登録手順](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device)」を参照してください。

 - ポータル サイト アプリに登録のエラー メッセージが表示されるようになりました。 これらのメッセージは、以前はポータル サイト Web サイトに表示されていました。 この変更は、すべてのエラー メッセージが 2 つの異なる場所ではなく、1 か所にまとめて表示されることを意味しています。


## 2016 年 1 月

### Windows 10 機能の利用
* **正常性構成証明書サービスによる条件付きアクセス** Intune 管理者は、Intune 管理コンソールで Windows 10 デバイス正常性構成証明書の状態を確認できるようになりました。 デバイス正常性構成証明書により、管理者はクライアント コンピューターの BIOS、TPM、ブート ソフトウェア構成が信頼のおけるものであることを確認できます。 デバイス正常性構成証明書をサポートするには、クライアント デバイスが TPM 2 を有効にして Windows 10 を実行している必要があります。 デバイス正常性構成証明書には、次のそれぞれに対応しているデバイスの数が表示されます。
    * 起動時マルウェア対策
    * BitLocker
    * セキュア ブート
    * コードの整合性

    デバイス正常性の設定、収集されるデータ ポイント、正常性構成証明書レポートの詳細については、「[Introduction to device compliance policies for Microsoft Intune (Microsoft Intune のデバイス コンプライアンス ポリシーの概要)](introduction-to-device-compliance-policies-in-microsoft-intune.md)」を参照してください。 このサービスの詳細については、「[HAS サービスの詳細情報](https://msdn.microsoft.com/en-us/library/dn934876.aspx)」を参照してください。

* **Windows 10 Passport for Work ポリシーと証明書の管理** Intune では、[Microsoft Passport for Work を統合](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md)できます。これは Active Directory または Azure Active Directory アカウントを使った Windows 10 への代替サインイン方法であり、パスワード、スマート カード、または仮想スマート カードの代わりに使用されます。 Passport を使用すると、パスワードの代わりにユーザー ジェスチャを使用してログインできます。 ユーザー ジェスチャには、単純な暗証番号 (PIN)、Windows Hello などの生体認証、または指紋リーダーなどの外部のデバイスがあります。

* **特定のアプリ用の VPN** VPN 経由で会社のネットワークに自動的に接続するアプリを選ぶことができます。 VPN プロファイルを設定するときに、「Microsoft Intune での VPN プロファイルを使用したユーザー作業への接続」の説明に従って、アプリの一覧を作成します。

* **Windows 10 のフル ワイプのサポート** Intune 管理コンソールで、Intune に登録された Windows 10 Desktop デバイスのリモート フル ワイプを発行できるようになりました。 Windows 10 のフル ワイプを実行すると、デバイスが出荷時の設定にリセットされます。


### Apple Volume Purchase Program (VPP) の更新
Intune を使用して、[Apple のビジネス向け Volume Purchase Program (VPP) で購入したアプリを管理](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md)できるようになりました。 これには、Apple と Intune 間のライセンス情報の同期や、各アプリの展開したコピー数の追跡が含まれています。

### IMEI 番号を使用して企業所有のデバイスを識別できる
IMEI (International Mobile Equipment Identity: 国際移動体装置識別) 番号を持つモバイル デバイス プラットフォームの場合に [IMEI 番号をインポート](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)して、企業所有のモバイル デバイスを識別できるようになりました。 インポートされた IMEI 番号を持つデバイスを Intune に登録すると、デバイスに企業のタグが付けられます。これを使用して、個人所有のデバイスとは異なるポリシーを適用できます。

### Intune MAM ポリシーと互換性があるアプリが追加された
Intune モバイル アプリケーション管理 (MAM) ポリシーと互換性がある Microsoft パートナーのアプリが追加されました (Intune によって管理されるデバイス用)。
* Box for EMM (Box Inc 製) - iOS のみ
* Adobe Reader (Adobe 製) - Android のみ
* Foxit PDF Reader (Foxit Corporation 製) - iOS および Android


### IE9 のサポートが 1 月で終了
2016 年 2 月以降、Internet Explorer 9 は、Microsoft Intune ポータル Web サイト、Intune アカウント ポータル、Intune 管理コンソールにアクセスするための公式のブラウザーとしてサポートされなくなります。 Internet Explorer 10 以降に移行する必要があります。


>[!div class="step-by-step"]

>[&larr; **Intune の新機能**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Aug16_HO3-->


