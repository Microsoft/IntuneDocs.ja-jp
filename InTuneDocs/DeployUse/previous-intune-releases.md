---
title: "以前のリリース |Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.reviewer: mamoriss
ms.suite: ems
ms.sourcegitcommit: 3080d23f464e96315ed9e5fd59774ba9f1b2dd86
ms.openlocfilehash: 65d582958d77150091880cce72e079b87308209f


---

# 以前の Intune のリリース
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
- **MAM SDK: PIN の長さの構成に対応。** デバイス PIN と同様、MAM アプリに使用する PIN の長さを指定できるようになります。 この場合エンド ユーザーは、管理者が設定した新しい制限に従う必要があります。 入力文字数が増える分、PIN 画面の外観が若干調整されます。 詳細については、[Android 用 MAM ポリシー設定](/intune/deploy-use/android-mam-policy-settings)および [iOS 用 MAM ポリシー設定](/intune/deploy-use/ios-mam-policy-settings)に関するページを参照してください。

- **iOS および Android 用 Skype for Business。** Skype for Business を [MAM の対象にできるようになりました (登録ポリシー不要)](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)。 ユーザーがログインすると、MAM ポリシーが適用されます。

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

## 2015 年 12 月
### Microsoft ポータル サイトの変更と更新
このリリースでは、ポータル サイトに次の変更が加えられました。

**Android 用ポータル サイト アプリ**

新しい Google 要件に準拠するために、次の変更が加えられました。 Android 6.0 以降のデバイスでは、ユーザーに対して次の 2 つの新しいメッセージが表示されます。
* 電話での通話とその管理をポータル サイトに許可しますか?
* デバイス上の写真、メディア、およびファイルへのアクセスをポータル サイトに許可しますか?

これらの 2 つのメッセージの詳細については、次の表をご覧ください。



メッセージ テキスト  |電話での通話とその管理をポータル サイトに許可しますか?  
---------|---------
メッセージの意味     |  ユーザーのデバイスの電話番号と IMEI が Intune サービスに送信され、ハードウェア ページの管理コンソールに表示されるようにします。   </br></br>**注: ポータル サイト アプリは電話での通話やその管理を行いません。** このメッセージ テキストは Google によって制御されているので、変更することはできません。 </br></br>**[ハードウェア]** ページを参照するには、**[グループ]** > **[すべてのモバイル デバイス]** >  **[デバイス]** に移動します。 ユーザーのデバイスを選択し、**[プロパティの表示]** > **[ハードウェア]** に移動します。    
メッセージが表示される場所とタイミング  | ユーザーがデバイスの登録を開始するために最初にポータル サイト アプリにサインインするときに、メッセージが表示されます。|         
ユーザーがアクセスを許可した場合の動作  |  デバイスの電話番号と IMEI は、管理コンソールのハードウェア ページに表示されます。 |         
ユーザーがアクセスを拒否した場合の動作     | ユーザーは引き続きポータル サイト アプリを使用して、デバイスを登録できますが、管理コンソールのハードウェア ページでユーザーのデバイスの電話番号と IMEI は空白になります。       </br></br> アクセスを拒否すると、ユーザーがポータル サイト アプリに 2 回目にサインインしたときに、メッセージに **[今後このメッセージを表示しない]** チェック ボックスが表示されます。ユーザーはこれを選ぶことによって、メッセージが再び表示されないようにできます。</br></br>ユーザーがアクセスを許可し、その後アクセスを拒否した場合は、登録後、次回ユーザーがポータル サイト アプリにサインインしたときに、メッセージが表示されます。</br></br>後でアクセスを許可する場合は、**[設定]** >  **[アプリ]** >  **[ポータル サイト]** > **[アクセス許可]** > **[電話]** に移動して、アクセス許可を有効にします。
詳細情報     |  ユーザー向け: 「[ポータル サイトにサインインする](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_signin_cp)」  </br></br>IT プロフェッショナル向け: この表の情報は、[ユーザーがポータル サイト アプリのメッセージを理解するためのページ](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)にも掲載されています。   

メッセージ テキスト  |デバイス上の写真、メディア、およびファイルへのアクセスをポータル サイトに許可しますか?  
---------|---------
メッセージの意味     |  デバイスがデータ ログをデバイスの SD カードに書き込めるようにして、USB ケーブルを使用したログの移動を可能にします。   </br></br>**注: ポータル サイト アプリはユーザーの写真、メディア、ファイルにアクセスしません。** このメッセージ テキストは Google によって制御されているので、変更することはできません。     
メッセージが表示される場所とタイミング  | ユーザーが **[データの送信]** をタップして IT 管理者にデータ ログを送信するときに、メッセージが表示されます。|         
ユーザーがアクセスを許可した場合の動作  |  ログは SD カードにコピーされます。 |         
ユーザーがアクセスを拒否した場合の動作     | ユーザーは引き続きデータ ログを送信できますが、ログはデバイスの SD カードにコピーされません。       </br></br> アクセスを拒否すると、ユーザーがポータル サイト アプリに 2 回目にサインインしたときに、メッセージに **[今後このメッセージを表示しない]** チェック ボックスが表示されます。ユーザーはこれを選ぶことによって、メッセージが再び表示されないようにできます。</br></br>ユーザーがアクセスを許可し、その後アクセスを拒否した場合は、次回ユーザーがログを送信しようとすると、メッセージが表示されます。</br></br>後でアクセスを許可する場合は、**[設定]** >  **[アプリ]** >  **[ポータル サイト]** > **[アクセス許可]** > **[ストレージ]** に移動して、アクセス許可を有効にします。
詳細情報     |  ユーザー向け: 「[メールを使用して診断データのログを IT 管理者に送信する](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_send_diag_logs)」  </br></br>IT プロフェッショナル向け: この表の情報は、[ユーザーがポータル サイト アプリのメッセージを理解するためのページ](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)にも掲載されています。   


**iOS ポータル サイト アプリ**
* ユーザーは、Microsoft Outlook や他のメール アプリを使用して、IT 管理者に診断ログを送信できるようになりました。 以前は、ネイティブ アプリのみが使用できました。
* Apple のデバイス登録プログラム (DEP) および会社に登録されたデバイスのサポートが強化されました。 詳細については、「[You are asked to identify your device when you're trying to enroll (登録時にデバイスの識別を求められる)](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_id_your_device)」をご覧ください。
* ユーザーの登録されているデバイスの一覧には、ユーザーが現在使用しているデバイスの横に緑色のチェック マークが表示されるようになりました。 このチェック マークが追加される前は、ユーザーは使用している登録済みデバイスを判別できませんでした。

**Microsoft ポータル サイト アプリ**

Microsoft は、Microsoft の製品やサービスを改善するために、ポータル サイトのパフォーマンスおよび使用に関する匿名データを自動的に収集します。 エンド ユーザーがデバイスの使用状況データ設定を使用してデータの収集を無効にすることはできますが、管理者がデータの収集を制御したり、エンド ユーザーが選択した設定を変更したりすることはできません。



## 2015 年 11 月
### アプリ管理
Intune は、企業データがコンシューマー アプリまたはサービスに漏洩しないようにするモバイル アプリケーション管理 (MAM) ポリシーをサポートしています。 従来、これらのポリシーはモバイル デバイス管理 (MDM) の対象として Intune に登録されたデバイスで実行されているモバイル アプリにのみ適用されていました。

今月の更新プログラムによって、Intune の MAM 機能が新しいクラスのデバイスに拡大されます。 Intune に登録されたデバイスだけでなく、次のデバイスにも MAM ポリシーを適用できるようになりました。
* 他のデバイス管理 (MDM) ソリューションによって管理されているデバイス。
* デバイス管理システムに登録されていないデバイス (通常は持ち込み (BYO) デバイス)

これらの新しい MAM 機能の詳細については、次のブログ記事をご覧ください。
* [Enhancing managed mobile productivity (管理対象のモバイル生産性の向上)](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)
* [Announcing new Microsoft Enterprise Mobility capabilities (Microsoft Enterprise Mobility の新機能のお知らせ)](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)

さらに、Intune の MAM 機能に関する重要ポイントと追加情報を次に示します。
* Office Mobile アプリ、Intune SDK を採用しているサード パーティ製アプリ、または Intune によってラップされた基幹業務アプリなどの Intune 対応アプリ内では、企業データがコンシューマー データから分離されます。
* 会社のデータを業務用アプリ間で共有 (**切り取り/コピー/貼り付け**) しながら、会社のデータが個人のアプリで共有されるのを防止できます。 詳細については、「[MAM ポリシーによるアプリ データ保護のしくみ](https://technet.microsoft.com/library/mt627825.aspx)」を参照してください。 このシナリオ例 (「[Microsoft Word アプリを作業タスクと個人用タスクで使用する](https://technet.microsoft.com/library/mt627827.aspx)」) は、個人のアプリで会社のデータが共有されるのを防止する方法を示しています。
* アプリ単位の PIN、別名保存の制御、アプリ間での管理対象データの共有などの主要なデータ損失防止ポリシー。 すべてのポリシーの一覧については、「[Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](https://technet.microsoft.com/library/mt627829.aspx)」をご覧ください。
* Word、Excel、PowerPoint、Outlook、OneNote、OneDrive for Business は、いずれもこれらの新機能を備えており、デバイス登録を使用しなくても管理できます。 Apple ストアまたは Google Play ストアの標準の Office アプリには、データ損失保護機能がネイティブで組み込まれており、アプリ ラッピングやサイドローディングは必要ありません。
* 使用方法については、「[Azure ポータルでモバイル アプリ管理ポリシーを使ってみる](https://technet.microsoft.com/library/mt627830.aspx)」をご覧ください。 モバイル アプリ管理ポリシーを構成して展開する方法については、「[Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](https://technet.microsoft.com/library/mt627829.aspx)」をご覧ください。
* エンドユーザーが会社の資格情報を使用してアプリから認証を受けると、データ損失保護機能が自動的に設定されます。 「[Microsoft Intune のモバイル アプリ管理ポリシーに関連付けられているアプリのエンド ユーザー エクスペリエンス](https://technet.microsoft.com/library/mt627827.aspx)」には、iOS および Android デバイスで OneDrive にアクセスするシナリオ例が記載されています。
* iOS デバイスと Android デバイスの両方で動作します。

「[Microsoft Intune のモバイル アプリケーション管理ポリシーと共に使用できる Microsoft アプリ](https://technet.microsoft.com/library/dn708489.aspx)」の一覧は、最新のアプリを示すように更新されています。

### デバイス管理
 **Mac OS X デバイスの管理** Intune を使用して、Mac OS X デバイスを登録および管理できるようになりました。 Mac OS X デバイスを使用して、次の作業を行うことができます。
* Intune で管理するデバイスを登録する。 「[Microsoft Intune を使用した iOS および Mac の管理のセットアップ](https://technet.microsoft.com/library/dn408185.aspx)」をご覧ください。
* 一般的な構成ポリシーを使用してデバイスの設定を制御する。 「[Microsoft Intune の Mac OS X 構成ポリシー設定](https://technet.microsoft.com/library/mt627823.aspx)」をご覧ください。
* Apple Configurator で作成した Mac OS X の設定を展開する。 「[Microsoft Intune の Mac OS X カスタム ポリシー設定](https://technet.microsoft.com/library/mt627820.aspx)」をご覧ください。
* Mac OS X デバイスからハードウェアおよびソフトウェア インベントリを収集する。 「[Microsoft Intune でインベントリを使用してデバイスを把握する](https://technet.microsoft.com/library/jj733634.aspx)」をご覧ください。
* 管理する Mac OS X デバイスの詳細情報を表示する新しいレポートを実行する。 「[レポートの使用に関する Microsoft Intune 操作について](https://technet.microsoft.com/library/dn646977.aspx)」をご覧ください。

**Windows 10 デバイスの新しい Edge ブラウザーの設定** 設定および Microsoft Edge ブラウザーの機能を管理できるようにする Windows 10 の一般的な構成ポリシーに新しい設定が追加されました。 「[Microsoft Intune の Windows 10 構成ポリシー設定](https://technet.microsoft.com/library/mt404697.aspx)」をご覧ください。

**電子メール プロファイル** Windows 10 Desktop デバイスと Windows 10 Mobile デバイス用に、新しいメール プロファイル ポリシーが追加されました。 「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](https://technet.microsoft.com/library/dn646984.aspx)」をご覧ください。

**新しいコンプライアンス ポリシー設定** コンプライアンス ポリシーの一覧に、次の新しいセキュリティおよびシステム ポリシー設定が追加されました。
* 会社のリソースにアクセスする Windows 8.1 以降のデバイスに最新の更新プログラムがインストールされていることを確認するには、**[自動更新を必須にする]** 設定を使用します。 自動的にインストールする更新プログラムの種類 (重要としてマークされているすべての更新プログラムか、重要または推奨としてマークされたすべての更新のいずれか) を指定することもできます。 コンプライアンス ポリシー設定の完全な一覧については、「[Microsoft Intune のデバイス コンプライアンス ポリシーの管理](https://technet.microsoft.com/library/dn705843.aspx)」をご覧ください。
* 新しい **[デバイスがアイドル状態から戻るときに、パスワードを必要とする]** 設定と既存の **[デバイスの画面がロックされるまでの非アクティブな時間 (分)]** 設定を組み合わせることで、エンドユーザーがしばらくの間非アクティブだったデバイスを使用するときにパスワードの入力を求めるコンプライアンス設定を作成できます。

**条件付きアクセス ポリシーの新しいオプション** 新規または既存の条件付きアクセス ポリシーで、**すべてのユーザー**に条件付きアクセス ポリシーを適用できます。 Intune と Office 365 のライセンスを取得しているすべてのユーザーは、各自のデバイスを登録するように求められます。また、デバイス プラットフォームが Intune でサポートされていない場合は、[Active Directory 認証ベースのサインイン (先進認証) ](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/)を使用するクライアント アプリケーションのアクセスがブロックされます。

条件付きアクセス ポリシーを**すべてのプラットフォーム**に適用するように指定することもできます。  [Active Directory 認証ベースのサインイン (先進認証)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/) を使用しているクライアント アプリケーションはすべて、条件付きアクセス ポリシーに従います。プラットフォームが Intune でサポートされていない場合、そのアクセスはブロックされます。

### Microsoft ポータル サイトの変更と更新
このリリースでは、ポータル サイト アプリに次の変更が加えられました。

* **Android**: ユーザーが Android ポータル サイト アプリの目的を理解できるように、ポータル サイト アプリにようこそ画面が追加されました。 この画面は、Intune のサブスクライバーでない会社のユーザーによるアプリのダウンロードを減らすことを目的としています。

* **iOS**: [ポータル サイト Web サイト](https://portal.manage.microsoft.com)を使用した Mac OS X デバイスの登録が Intune でサポートされるようになりました。 手順については、「[Intune に Mac OS X デバイスを登録する](https://technet.microsoft.com/library/mt598622.aspx)」を参照してください。

* **ポータル サイト Web サイト**: Intune にデバイスを登録しているユーザーは、ポータル サイト Web サイトの **[パスコードのリセット]** オプションを使用してパスコードをリセットできるようになりました。 以前は、IT 管理者だけがユーザーのパスコードをリセットできました。 パスコードのリセットのオプションは Windows 8.1 および Windows RT のデバイスではサポートされていません。またオプションは、モバイル デバイス管理 (MDM) または Exchange ActiveSync を使用した MDM にデバイスが登録されている場合のみ表示されます。 ユーザーの手順については、「[パスコードのリセット](https://technet.microsoft.com/library/mt590895.aspx)」を参照してください。

### グローバル管理者ライセンスの変更点
10 月に、グローバル管理者 (テナント管理者とも呼ばれる) は別個の Intune または Enterprise Mobility Suite (EMS) ライセンスがなくても日常的な管理タスクを続行できることを公表しました。 ただし、グローバル管理者が自分自身のデバイスの登録、会社のデバイスの登録、Intune ポータル サイトの使用などを行うためにサービスを使用する場合は、他のユーザーと同じように Intune または EMS のライセンスが必要になります。 次に、追加の詳細情報を示します。
* Intune ポータル サイトで、エンド ユーザーは次の作業ができます。
    * 自分のデバイスを登録する
    * 自分のデバイスの状態を表示する
    * グローバル管理者が組織に展開したソフトウェアをダウンロードする
    * グローバル管理者が IT 部門への問い合わせ方法を示すために発行したリンクを見つける

    [ポータル サイトの説明](https://technet.microsoft.com/library/dn646966.aspx#BKMK_CompanyPortal)および[ポータル サイトのカスタマイズ方法](https://technet.microsoft.com/library/dn646983.aspx#BKMK_ConfigureCompanyPortal)をご覧ください。
* 組織の代表として Intune または EMS を購入するためにサインアップしたユーザーは、自動的にテナント内の最初のグローバル管理者になります。 この秋から、[Office 365 ポータル](http://portal.office.com/)への移行と [Intune アカウント ポータル](http://account.manage.microsoft.com/)の提供終了に伴って、Intune は Intune または EMS ライセンスをその最初のグローバル管理者に自動的に割り当てるようになりました。 追加された他のグローバル管理者は、別個の Intune または EMS ライセンスがなくても日常的な管理を続行できます。 エンド ユーザーとして活動し、自分自身 (または会社) のデバイスを登録したり、ポータル サイトからソフトウェアをダウンロードしたりする場合は、他のユーザーと同じようにライセンスが必要になります。
* この変更は段階的に行われ、2016 年 1 月から開始されます。
* Microsoft パートナーについては、この変更が顧客の代理でサービスを管理するための機能に影響することはありません。 エンドユーザー タスクについては、ユーザーがデバイスを登録して、ポータル サイトにアクセスしたり、そこからソフトウェアをダウンロードしたりするためには、Intune または EMS ライセンスが必要になります。

この変更に関するご質問は、Intune のサポート チームにお気軽にお寄せください。
* [Microsoft Intune サポート窓口](https://technet.microsoft.com/library/jj839713.aspx)
* [コミュニティ サポート](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

設計変更要求 (DCR) やバグなど、Microsoft Intune の一般的なフィードバックについては、[Intune User Voice](https://microsoftintune.uservoice.com/) にアクセスしてください。


### Intune ドキュメントの最新情報 -- 2015 年 11 月
**新しいトピック**
* [Microsoft Intune の Mac OS X 構成ポリシー設定](https://technet.microsoft.com/library/mt627823.aspx): Mac OS X デバイスのデバイス設定および機能を制御する方法。
* [Microsoft Intune の Mac OS X カスタム ポリシー設定](https://technet.microsoft.com/library/mt627820.aspx): Apple Configurator ツールを使用して作成した Mac OS X デバイスの設定を展開する方法。
* [Microsoft Intune を使用したデータ損失防止のアプリ ポリシーの構成](https://technet.microsoft.com/library/mt627825.aspx): モバイル アプリ管理ポリシーでサポートされるシナリオと、ポリシーによってデータを保護するしくみに関する情報が記載されています。
* [Azure ポータルでモバイル アプリ管理ポリシーを使ってみる](https://technet.microsoft.com/library/mt627830.aspx): Azure プレビュー ポータルでモバイル アプリ管理ポリシーを使用するために必要なもの。
* [Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](https://technet.microsoft.com/library/mt627829.aspx): Azure プレビュー ポータルでモバイル アプリ管理ポリシーを作成する方法の詳細なチュートリアルが含まれています。
* [Microsoft Intune でのモバイル アプリ管理ポリシーの監視](https://technet.microsoft.com/library/mt627824.aspx): Azure プレビュー ポータルを使用してモバイル アプリ管理ポリシーを監視する方法に関する情報。
* [Microsoft Intune モバイル アプリ管理ポリシーと iOS の Open In](https://technet.microsoft.com/library/mt627821.aspx): モバイル アプリ管理ポリシーと iOS の Open In 機能の連携動作に関する情報。
* [Microsoft Intune モバイル アプリ管理ポリシーに関連付けられているアプリのエンドユーザー エクスペリエンス](https://technet.microsoft.com/library/mt627827.aspx): モバイル アプリ管理ポリシーに関連付けられているアプリを使用した場合のエンドユーザー エクスペリエンスがどのようなものか。
* [管理対象の業務用アプリのデータを Microsoft Intune でワイプする](https://technet.microsoft.com/library/mt627826.aspx): 業務用アプリのデータを削除する方法。

**更新されたトピック**
* [Microsoft Intune の Windows 10 構成ポリシー設定](https://technet.microsoft.com/library/mt404697.aspx): 新しい Edge ブラウザーの設定が追加されました。
* [Microsoft Intune を使用した iOS および Mac の管理のセットアップ](http://technet.microsoft.com/library/dn408185.aspx): Mac OS X デバイスの登録方法に関する情報が追加されました。
* [Microsoft Intune でインベントリを使用してデバイスを把握する](https://technet.microsoft.com/library/jj733634.aspx): Mac OS X デバイスから収集されるインベントリに関する情報が追加されました。 また、すべてのデバイス プラットフォームの最新情報を反映してトピックが更新されました。
* [レポートの使用に関する Microsoft Intune 操作について](https://technet.microsoft.com/library/dn646977.aspx): 管理対象の Mac OS X デバイスに関する情報を表示するために使用する 2 つの新しいレポートに関する情報が追加されました。
* [Microsoft Intune のデバイス コンプライアンス ポリシーの管理](https://technet.microsoft.com/library/dn705843.aspx): 自動更新の要求とデバイスがアイドル状態から戻ったときのパスワードの要件に関する新しいコンプライアンス ポリシーの情報が追加されました。
* [Microsoft Intune での電子メールへのアクセスの管理](https://technet.microsoft.com/library/dn705841.aspx): すべてのプラットフォームおよびすべてのユーザーに条件付きアクセス ポリシーを適用する機能に関する情報が追加されました。
* [Microsoft Intune を使用した SharePoint Online アクセスの管理](https://technet.microsoft.com/library/dn705844.aspx): すべてのプラットフォームおよびすべてのユーザーに条件付きアクセス ポリシーを適用する機能に関する情報が追加されました。

## 2015 年 10 月

### Exchange On-Premises の条件付きアクセスの更新
**グローバル Exchange ルールがブロックまたは検疫に設定されているときに、Intune に登録された準拠デバイスに対して Exchange Active Sync メールへのアクセスを許可できるようになりました**。これまでは、登録された準拠デバイスに対してメール アクセスを許可するには、既定のグローバル Exchange ルールを**許可**に設定する必要がありました。

このサービスの更新により、条件付きアクセスでこの設定が不要になりました。 Exchange 環境で、既定のグローバル ルールを**ブロック/検疫**に設定する必要がある場合は、単純に Exchange On-Premises の条件付きアクセス ポリシーのページの **[既定ルールの上書き]** チェック ボックスをオンにします。 「[Microsoft Intune での電子メールへのアクセスの管理](https://technet.microsoft.com/library/dn705841.aspx)」には、ルールと、その結果発生するエンド ユーザー通知の詳細が含まれています。

**新しいワンクリックによる検疫操作:** 検疫のメール操作を単純化し、ワンクリックでの登録が可能になりました。 このサービスの更新により、エンド ユーザーは検疫の電子メールのリンクを 1 回クリックするだけでポータル サイト アプリ内の登録プロセスを完了できるようになりました。
### モバイル デバイスおよびアプリ管理の更新
**Android:** ブログ記事「[Microsoft Intune Provides Day 0 Support for Android Marshmallow (Microsoft Intune が Android Marshmallow の同日サポートを提供)](http://blogs.technet.com/b/microsoftintune/archive/2015/10/09/microsoft-intune-to-provide-day-0-support-for-android-marshmallow.aspx)」で説明されているとおり、Intune のすべての管理機能が Android 6.0 (Marshmallow) に対応するようになりました。

**iOS:** iOS 7.1 より前のバージョンを実行している iOS デバイスには新しいアプリの展開を作成できなくなりました。 iOS 7.1 以前のバージョンを実行しているデバイスに対する既存のアプリ展開は、引き続き Intune で動作し、管理されます。

**Windows 10:** Intune はソフトウェア インストーラーの種類として **Windows アプリ パッケージ**を使用する Windows 10 ユニバーサル アプリの展開に対応するようになりました。 詳細と要件については、「[Microsoft Intune でのアプリ展開の開始](http://technet.microsoft.com/en-US/library/dn646955.aspx)」を参照してください。


### Microsoft ポータル サイト アプリの変更と更新
このリリースでは、ポータル サイト アプリに次の変更が加えられました。**iOS** ユーザーが IT 管理者に診断ログを送信しやすいよう、ポータル サイト アプリに新しいボタンが追加されました。

|ボタン名|表示内容|
|------------|---------------|
|レポート|エラー アラート メッセージ|
|診断レポートの送信|ポータル サイト アプリの画面について|


>[!div class="step-by-step"]

>[&larr; **[!div class="step-by-step"]**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Jul16_HO1-->


