---
# required metadata

experiment_id: lindavr-abtest-20160527
title: 新機能 | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune の新機能

## 2016 年 5 月


TeamViewer 統合を除き、以下のすべての機能がハイブリッド展開 (Configuration Manager と Intune) でもサポートされます。 新しいハイブリッド機能の詳細については、[ハイブリッド環境の新機能](https://technet.microsoft.com/en-us/library/mt718155.aspx)に関するページを参照してください。

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

### デバイス管理

- **Windows PC のリモート アシスタンス セッション。** Intune クライアント ソフトウェアによって管理される Windows PC の TeamViewer 統合により、Windows PC でリモート アシスタント セッションを確立し、ヘルプ デスク部門をサポートできるようになります。 サポートされている PC には、Windows 7、8、8.1 および Windows 10 が含まれます。
詳細については、「[Microsoft Intune コンピューター クライアントを使用した一般的な Windows PC 管理タスク](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#respond-to-a-remote-assistance-request)」を参照してください。

### ポータル サイトの更新

#### Android 用ポータル サイト アプリ

- **エンドユーザーへのトースト通知**: エンドユーザーがポータル サイトからデバイスの登録または削除を行う際に、Android ポータル サイト アプリからのトースト通知が表示されるようになりました。

- **Android ポータル サイト アプリでのデバイス登録マネージャー アカウントへの変更。** パフォーマンスと拡張性を高めるために、Intune の Android ポータル サイト アプリの [デバイス] ペインには、すべてのデバイス登録マネージャー (DEM) デバイスが表示されなくなります。 アプリを実行しているローカル デバイスのみ、ポータル サイト アプリ経由で登録されている場合にだけ表示されます。 ローカル デバイスに対する操作は DEM で実行できますが、他の登録デバイスのリモート管理は、Intune 管理コンソールから実行する必要があります。
-
#### ポータル Web サイト

**ポータル Web サイト: デバイス ID バナーによってエンド ユーザーへの情報提供を拡充。** エンド ユーザーは、ポータル Web サイトを使用する際に選択したデバイスをより簡単に特定できるようになりました。 間違ったデバイスを選択した場合は、ホーム ページ バナーの **[ここをタップ]** リンクをタップして正しいデバイスを選択できます。


## 今後の更新情報

- **メッセージ センターの UI オンボード** [Office 365 管理ポータル](https://portal.office.com/)に Intune を移行する取り組みの一環として、新機能をはじめとする告知にメッセージ センターを活用することとなりました。 また Office 365 Admin モバイル コンパニオン アプリをインストールすることによって通知を携帯電話で受け取り、ユーザーや配布リストに宛てて簡単にメッセージを転送することもできます。
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



## 以前の Intune のリリース
過去 6 か月間に公開された Intune のリリースについては、「[以前の Intune のリリース](previous-intune-releases.md)」の記事をご覧ください。
> [!div class="op_single_selector"]
- [2016 年 4 月](previous-intune-releases.md)
- [2016 年 3 月](previous-intune-releases.md)
- [2016 年 2 月](previous-intune-releases.md)
- [2016 年 1 月](previous-intune-releases.md)
- [2015 年 12 月](previous-intune-releases.md)
- [2015 年 11 月](previous-intune-releases.md)




### 関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)


<!--HONumber=Jun16_HO1-->


