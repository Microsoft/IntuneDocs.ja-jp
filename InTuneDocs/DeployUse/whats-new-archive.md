---
title: "新機能の公開履歴 | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: 458ee268d0c6a8fa6cbe6cc23ad07f0e45eff3e5


---
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



## 2015 年 9 月
### モバイル デバイスおよびアプリ管理の更新
**すべての Intune の iOS 管理機能が iOS 9 に対応** iOS 9 の管理機能に関する詳細については、[このブログ投稿](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx)を参照してください。

**新しくなった iOS のモバイル アプリの構成ポリシー** 新しいモバイル アプリの構成ポリシーを使用すると、iOS アプリの実行時に必要となる可能性がある設定が自動的に指定されます。 たとえば、ネットワーク ポートやユーザー名を指定できます。 詳細については、「[Microsoft Intune でのモバイル アプリ構成ポリシーを使用したアプリの構成](https://technet.microsoft.com/library/mt481447.aspx)」をご覧ください。

**iOS 9 ユーザーのアプリ管理が簡単に**
このリリースでは、展開済みのアプリを iOS 9 ユーザー向けに Intune で管理できます。 以前のバージョンの iOS の場合、アプリを展開するとき、そのアプリの管理されていないバージョンが既にデバイスにインストールされているなら、まずユーザーにアプリを手動でアンインストールしてもらってからでなければ、管理されているアプリを Intune でインストールすることはできません。

 しかし、このリリースの Intune 以降では、Intune でアプリの管理を引き継ぎ、関連するモバイル アプリケーションの管理ポリシーを適用できるよう、iOS 9 デバイスのユーザーにダイアログを表示できます。

 **Windows 10 管理:** 新しい [Windows 10 の全般構成ポリシー](https://technet.microsoft.com/library/mt404697.aspx)を使用して、Windows 10 および Windows 10 Mobile を実行している登録済みデバイスのパスワード、デバイス、ブラウザーなどの設定を構成します。

 **登録済みの Windows 10 デバイスに対するアプリの作成と展開:** 新しいソフトウェア インストーラーの種類である MDM 経由の Windows インストーラー (&#42;.msi) により、Windows 10 を実行している登録済みデバイスに対して Windows インストーラー アプリを作成し、展開することができます。 詳細については、「[Microsoft Intune でのアプリ展開の開始](https://technet.microsoft.com/library/dn646955.aspx)」をご覧ください。

### Microsoft ポータル サイト アプリの変更と更新
このリリースでは、ポータル サイト アプリに次の変更が加えられました。

**iOS**
* Microsoft は、Microsoft の製品やサービスを改善するために、ポータル サイトのパフォーマンスおよび使用に関する匿名データを自動的に収集します。 エンド ユーザーがデバイスの使用状況データ設定を使用してデータの収集を無効にすることはできますが、管理者がデータの収集を制御したり、エンド ユーザーが選択した設定を変更したりすることはできません。
* iPhone 6 および iPhone 6 Plus で全画面解像度をサポート
* セキュリティ強化のためのバグ修正

### Intune ドキュメントの最新情報 -- 2015 年 9 月
**新しいトピック**

|名前|説明|
|----|--------|
|[Microsoft Intune の Windows 10 構成ポリシー設定](https://technet.microsoft.com/library/mt404697.aspx)|これは、Windows 10 および Windows 10 Mobile を実行しているデバイスの設定や機能を管理できる新しい構成ポリシーです。
| [Microsoft Intune でのモバイル アプリ構成ポリシーを使用したアプリの構成](https://technet.microsoft.com/library/mt481447.aspx)|ユーザーが iOS アプリを実行している場合に必要となる可能性のある設定を自動的に提供できる新しいポリシーの種類です。 |

**更新されたトピック**

|名前|説明|
|----|-------|
|[Microsoft Intune でポリシーを使用してコンピューターとモバイル デバイスを管理する](https://technet.microsoft.com/library/dn743712.aspx)|ポリシーの理解と作成に役立つ最新の情報が含まれるように更新されました。|

## 2015 年 8 月
### モバイル デバイスおよびアプリ管理の更新
* **Intune の登録および会社アクセスに関する使用条件** が、 [ポリシーを使って管理されるようになりました](https://technet.microsoft.com/library/mt405893.aspx)。 このため、特定のユーザー グループに対する要件に応じて、さまざまな使用条件を展開できるようになりました。 たとえば、地域に応じて定義したユーザー グループに対して、さまざまな言語の使用条件を展開できます。 また、 [使用条件の編集](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) や、バージョン番号を一定単位で増加させるかどうかの指定のほか、ポータル サイトの使用に先立ってユーザーに新しい使用条件に対する同意を求めることができるようになっています。
* **Intune ポリシーの名称が多数変更になりました** 。これは、製品内で一貫性を高め、ユーザーがポリシーを探しやすくするためのものです。 使用可能なすべての Intune ポリシーの一覧については、「[Microsoft Intune でポリシーを使用してコンピューターとモバイル デバイスを管理する](https://technet.microsoft.com/library/dn743712.aspx)」をご覧ください。
* **PKCS #12 (.PFX) 証明書プロファイル**を使用できるようになりました。これは、Android 4.0 以降および Windows 10 以降 (Desktop および Mobile) が対象です。 .PFX の使用には、NDES サーバーは必要ありません。 .PFX 証明書プロファイルの使用方法については、「[Microsoft Intune で証明書プロファイルを使用して会社のリソースへのアクセスを有効にする](http://technet.microsoft.com/library/dn818904.aspx)」を参照してください。
* **Windows 10 Desktop および Mobile に会社の境界を設定する**ことによって、詳細な VPN 設定が可能になりました。詳細については、「[Microsoft Intune での VPN プロファイルを使用したユーザー作業への接続](https://technet.microsoft.com/library/dn818905.aspx)」を参照してください。
* **Android 用の OneDrive アプリが、複数の ID をサポートするようになりました**。 この更新とモバイル アプリの管理ポリシーに対するその他の更新については、 [管理可能な Microsoft アプリケーションの一覧](https://technet.microsoft.com/library/dn708489.aspx)で説明しています。
* **iOS のアクティベーション ロックのバイパス機能**が追加されました。 会社所有の iOS デバイスがアクティべーション ロックで保護されている場合には、デバイスを消去したり、再アクティブ化したりする前に、ユーザーの Apple ID とパスワードを入力する必要があります。 そのため、ユーザーが会社を退職する際に、アクティブ化ロックをオフにせずに会社所有のデバイスを返却した場合に問題が発生することがあります。 この問題の解決方法として、[Intune のアクティブ化ロックのバイパス](https://technet.microsoft.com/library/mt414176.aspx)を使用できます。

### PC の条件付きアクセス
PC を対象とした条件付きアクセス ポリシーを構成できるようになりました。 これにより、Office デスクトップ アプリで Exchange Online および SharePoint のオンライン サービスにアクセスすることができます。
PC の条件付きアクセス ポリシーを有効にするには、PC がドメインに参加または対応している必要があります。
* PC に対する条件付きアクセスを有効にするための要件の一覧については、「[Microsoft Intune を使用して電子メールと SharePoint へのアクセスを管理する](http://technet.microsoft.com/library/dn818907)」で**条件付きアクセスの使用の準備**に関するセクションをご覧ください。
* メール アクセスに対する条件付きアクセスを有効にするときに設定できるオプションについては、「[Microsoft Intune での電子メールへのアクセスの管理](https://technet.microsoft.com/library/dn705841.aspx)」をご覧ください。
* SharePoint Online に対する条件付きアクセスを有効にするときに設定できるオプションについては、「[Microsoft Intune を使用した SharePoint Online アクセスの管理](https://technet.microsoft.com/library/dn705844.aspx)」をご覧ください。

### Microsoft ポータル サイト アプリの変更と更新
このリリースでは、ポータル サイト アプリに次の変更が加えられました。

**Android**

ユーザーがまだデバイスを管理対象として登録していない場合、サインインした後に、デバイスの登録手順が表示されるようになりました。

### Intune ドキュメントの最新情報 -- 2015 年 8 月
**新しいトピック**

|タイトル|説明|
|-----|-------|
|[Microsoft Intune でアクティブ化ロックのバイパスを使用して iOS デバイスを保護する](https://technet.microsoft.com/library/mt414176.aspx)|会社を退職したユーザーから返却されたデバイスがロックされている場合に、Intune で iOS のアクティべーション ロックをバイパスする方法について説明します。|

**更新されたトピック**

|タイトル|説明|
|-----|-------|
|[Microsoft Intune のモバイル アプリケーション管理ポリシーと共に使用できる Microsoft アプリ](https://technet.microsoft.com/library/dn708489.aspx)|モバイル アプリケーションの管理ポリシーを使って管理できるアプリに関する情報が更新されました。
|[Microsoft Intune でポリシーを使用してコンピューターとモバイル デバイスを管理する](http://technet.microsoft.com/library/dn743712.aspx)|Intune に追加された最新のポリシーについて、情報を更新しました。|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->



<!--HONumber=Jul16_HO4-->


