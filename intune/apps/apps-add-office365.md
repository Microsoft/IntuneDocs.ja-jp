---
title: Microsoft Intune を使用して Windows 10 デバイスに Office 365 アプリを追加する
titleSuffix: ''
description: Microsoft Intune を使用し、Office 365 アプリを Windows 10 デバイスにインストールする方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86d02ae1277ff2fd6dfce9bf206628f5dc1c2a84
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755328"
---
# <a name="add-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Microsoft Intune を使用して Windows 10 デバイスに Office 365 アプリを追加する

アプリの割り当て、監視、構成、または保護を行うには、対象のアプリを事前に Intune に追加しておく必要があります。 使用できる[種類のアプリ](apps-add.md#app-types-in-microsoft-intune)の 1 つに Windows 10 向け Office 365 アプリがあります。 Intune でこの種類のアプリを選択することで、Windows 10 を実行し、自分で管理しているデバイスに Office 365 アプリを割り当て、インストールできます。 ライセンスを所有している場合は、Microsoft Project Online デスクトップ クライアントおよび Microsoft Visio Online Plan 2 のアプリを割り当て、インストールすることもできます。 利用できる Office 365 は、Azure 内の Intune コンソールのアプリ一覧に単一のエントリとして表示されます。

> [!NOTE]
> Microsoft Intune で展開された Office 365 ProPlus アプリをアクティブ化するには、Office 365 ProPlus ライセンスを使用する必要があります。 現時点では、Office 365 Business Edition は Intune ではサポートされていません。

## <a name="before-you-start"></a>開始する前に

> [!IMPORTANT]
> .msi Office アプリがエンド ユーザー デバイスにある場合、それらのアプリを安全にアンインストールするには **MSI 削除**機能を使用する必要があります。 そうしないと、Intune 配信の Office 365 アプリをインストールできません。

- これらのアプリを展開するデバイスでは、Windows 10 Creators Update 以降を実行している必要があります。
- Intune は、Office 365 スイートの Office アプリの追加のみをサポートします。
- Intune でアプリ スイートをインストールするときに、Office アプリが開いている場合は、インストールが失敗し、ユーザーは保存されていないファイルのデータを失う可能性があります。
- このインストール方法は、Windows Home、Windows Team、Windows Holographic、または Windows Holographic for Business の各デバイスではサポートされていません。
- Intune では、Intune を使用して Office 365 アプリを既に展開しているデバイス上の Microsoft Store から Office 365 デスクトップ アプリ (Office Centennial アプリとして知られる) をインストールすることをサポートしていません。 この構成をインストールすると、データが損失したり壊れたりする可能性があります。
- 必須または使用可能なアプリを複数割り当てる場合、後の割り当ては前の割り当てに追加されるのではありません。 後のアプリ割り当ては、それより前にインストールされて存在するアプリの割り当てを上書きします。 たとえば、Office アプリの最初のセットに Word が含まれ、後のセットには含まれない場合、Word はアンインストールされます。 この条件は、Visio または Project アプリケーションには適用されません。
- 複数の Office 365 の展開は、現在はサポートされていません。 1 つの展開だけが、デバイスに配信されます
- **[Office バージョン]** : Office の 32 ビットまたは 64 ビット バージョンのどちらを割り当てるかを選択します。 32 ビットと 64 ビットのどちらのデバイスでも 32 ビット バージョンをインストールできますが、64 ビットのデバイスには 64 ビット バージョンしかインストールできません。
- **[Remove MSI from end-user devices]** \(エンドユーザーのデバイスから MSI を削除する\): エンドユーザーのデバイスから、既にある Office .MSI アプリを削除するかどうか選択します。 エンドユーザーのデバイスに、既に .MSI アプリがある場合、インストールは成功しません。 インストールされるアプリは、 **[アプリ スイートの構成]** でインストール対象として選択されたアプリに限りません。すべての Office (MSI) アプリがエンド ユーザー デバイスから削除されます。 詳細については、「[Remove existing MSI versions of Office when upgrading to Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version)」 (Office 365 ProPlus へのアップグレード時に Office の既存の MSI バージョンを削除する) を参照してください。 エンドユーザーのコンピューターに Office が Intune によって再インストールされる場合、エンド ユーザーには前の .MSI Office インストールで使用していたのと同じ言語パックが自動的に提供されます。

## <a name="select-the-office-365-suite-app-type"></a>Office 365 Suite アプリの種類を選択する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** の順に選択します。
3. **[アプリケーションの種類の選択]** ペインの **[Office 365 スイート]** セクションで **[Windows 10]** を選択します。
4. **[選択]** をクリックします。 **[Add Office 365 Suite]\(Office 365 スイートの追加\)** ステップが表示されます。


## <a name="step-1---app-suite-information"></a>ステップ 1 - アプリ スイートの情報

この手順では、アプリ スイートに関する情報を指定します。 この情報は、Intune でアプリ スイートを識別し、ユーザーが会社のポータルでアプリを探す場合に役立ちます。

1. **[アプリ スイートの情報]** ページで、既定値を確認または変更できます。
    - **[スイート名]** : 会社のポータルに表示される、アプリ スイートの名前を入力します。 使用するスイート名はすべて一意にします。 同じアプリ スイート名が 2 つ存在する場合、会社のポータルではそのアプリのいずれかのみがユーザーに表示されます。
    - **[スイートの説明]** : アプリ スイートの説明を入力します。 たとえば、含めるように選択したアプリを一覧表示できます。
    - **[発行元]** : Microsoft が発行者として表示されます。
    - **[カテゴリ]** : (省略可能) 1 つ以上の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 この設定を行うと、会社のポータルを閲覧するときに、ユーザーがアプリ スイートを探しやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]** : ユーザーがアプリを参照するとき、会社のポータルのメイン ページにアプリ スイートが目立つように表示するには、このオプションを選びます。
    - **[情報 URL]** : このアプリに関する情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[プライバシー URL]** : このアプリのプライバシー情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[開発者]** : Microsoft が開発者として表示されます。
    - **[所有者]** : Microsoft が所有者として表示されます。
    - **[メモ]** : このアプリに関連付けるメモを入力します。
    - **[ロゴ]** : ユーザーがポータル サイトを閲覧するとき、アプリと一緒に Office 365 のロゴが表示されます。
2. **[次へ]** をクリックして、 **[アプリ スイートの構成]** ページを表示します。

## <a name="step-2---option-1-configure-app-suite-using-the-configuration-designer"></a>ステップ 2 - (**オプション 1**) 構成デザイナーを使用してアプリ スイートを構成する 

**[構成設定の形式]** を選択することで、アプリ設定を構成するための方法を選択できます。 [設定の形式] オプション:
- 構成デザイナー
- XML データを入力する

**[構成デザイナー]** を選択すると、 **[アプリの追加]** ペインが変更されて、さらに 3 つの設定領域が表示されます。
- アプリ スイートの構成
- アプリ スイートの情報
- プロパティ

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

1. **[Configuration app suite]\(構成アプリ スイート\)** ページで、 **[構成デザイナー]** を選択します。
   - **[Select Office apps]\(Office アプリを選択する\)** : ドロップダウン リストでアプリを選択して、デバイスに割り当てる標準の Office アプリを選択します。
   - **[Select other Office apps (license required)]\(その他の Office アプリを選択する (ライセンスが必要)\)** : デバイスに割り当てる追加の Office アプリがあり、そのライセンスを持っている場合は、ドロップダウン リストからそのアプリを選択します。 このようなアプリには、Microsoft Project Online デスクトップ クライアントや Microsoft Visio Online プラン 2 などのライセンスされたアプリなどがあります。
   - **[アーキテクチャ]** : Office ProPlus の **32 ビット**または **64 ビット** バージョンのどちらを割り当てるかを選択します。 32 ビットと 64 ビットのどちらのデバイスでも 32 ビット バージョンをインストールできますが、64 ビットのデバイスには 64 ビット バージョンしかインストールできません。
    - **[更新プログラム チャネル]** : デバイス上で Office を更新する方法を選択します。 さまざまな更新プログラム チャネルについて詳しくは、「[Office 365 ProPlus 更新プログラム チャネルの概要](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)」をご覧ください。 次の中から選択します。
        - **毎月**
        - **Monthly (Targeted)** \(毎月 (対象指定)\)
        - **Semi-Annual**\(半期\)
        - **Semi-Annual (Targeted)** \(半期 (対象指定)\)

        チャネルを選択すると、以下を選択できるようになります。
        - **[Remove other versions]\(その他のバージョンを削除する\)** : **[はい]** を選択すると、他のバージョンの Office (MSI) をユーザー デバイスから削除されます。 エンドユーザー デバイスから既存の Office .MSI アプリを削除する場合は、このオプションを選択します。 エンドユーザーのデバイスに、既に .MSI アプリがある場合、インストールは成功しません。 インストールされるアプリは、 **[アプリ スイートの構成]** でインストール対象として選択されたアプリに限りません。すべての Office (MSI) アプリがエンド ユーザー デバイスから削除されます。 詳細については、「[Remove existing MSI versions of Office when upgrading to Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version)」 (Office 365 ProPlus へのアップグレード時に Office の既存の MSI バージョンを削除する) を参照してください。 エンドユーザーのコンピューターに Office が Intune によって再インストールされる場合、エンド ユーザーには前の .MSI Office インストールで使用していたのと同じ言語パックが自動的に提供されます。 
        - **[Version to install]\(インストールするバージョン\)** : インストールする Office のバージョンを選択します。
        - **[特定バージョン]** : 上記の設定の **[Version to install]\(インストールするバージョン\)** として **[特定]** を選択した場合は、選択したチャネルの特定のバージョンの Office をエンド ユーザー デバイスにインストールすることを選択できます。 
            
            使用できるバージョンは随時変更されます。 そのため、新しいデプロイを作成するとき、利用できるバージョンが新しく、特定の古いバージョンを利用できないことがあります。 現在のデプロイでは引き続き古いバージョンをデプロイできますが、バージョンの一覧はチャネル単位で継続的に更新されます。
            
            デバイスのピン設定されているバージョンが更新される場合 (または他の任意のプロパティが更新される場合)、それが利用可能としてデプロイされる場合、デバイスのチェックインが発生するまでに前のバージョンがインストールされた場合は、インストール済みであるという状態が報告されます。 デバイスのチェックインが起こった場合、状態は一時的に不明に変わりますが、これはユーザーには表示されません。 ユーザーがより新しいバージョンのインストールを開始した場合、ユーザーには状態が [インストール済み] と変更され表示されます。
            
            詳細については、「[Office 365 ProPlus 更新プログラム チャネルの概要](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)」をご覧ください。
    - **[共有コンピューターのライセンス認証を使用]** : 複数のユーザーでコンピューターを共有する場合は、このオプションを選びます。 詳細については、[Office 365 に対する共有コンピューターのライセンス認証の概要](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus)に関するページを参照してください。
    - **[アプリのソフトウェア ライセンス条項を自動的に受け入れる]** : エンド ユーザーにライセンス契約への承諾を要求しない場合は、このオプションを選びます。 その後、Intune で契約書を自動的に承諾します。
    - **[言語]** : Office は、エンド ユーザーのデバイス上の Windows にインストールされている任意のサポート言語で自動的にインストールされます。 アプリ スイートと共に追加の言語をインストールする場合は、このオプションを選択します。 <p></p>
        Intune によって管理されている Office 365 Pro Plus アプリに追加の言語を展開することができます。 使用可能な言語のリストには、言語パックの **種類** (コア、部分、校正) が含まれます。 Azure portal で、 **[Microsoft Intune]**  >  **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** を選択します。 **[アプリの追加]** ウィンドウの **[アプリの種類]** の一覧で、 **[Office 365 スイート]** の **[Windows 10]** を選びます。 **[アプリ スイートの設定]** ウィンドウで **[言語]** を選びます。 詳細については、「[Office 365 ProPlus での言語の展開の概要](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus)」を参照してください。
2. **[次 へ]** をクリックして **[スコープ タグ]** ページを表示します。

## <a name="step-2---option-2-configure-app-suite-using-xml-data"></a>ステップ 2 - (**オプション 2**) XML データを使用してアプリ スイートを構成する 

**[アプリ スイートの構成]** ページの **[Setting format]\(設定形式\)** ドロップダウン ボックスで **[XML データを入力する]** オプションを選択した場合は、カスタム構成ファイルを使用して Office アプリ スイートを構成できます。

![Office 365 構成デザイナーの追加](./media/apps-add-office365/apps-add-office365-01.png)

1. 構成 XML が追加されます。
2. **[次 へ]** をクリックして **[スコープ タグ]** ページを表示します。

XML データの入力の詳細については、「[Office 展開ツールのオプションの構成](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)」を参照してください。

## <a name="step-3---select-scope-tags-optional"></a>ステップ 3 - スコープのタグを選択する (省略可能)
スコープのタグを使って、Intune のクライアント アプリの情報を表示できるユーザーを決定することができます。 スコープのタグの詳細については、[分散 IT のためのロールベースのアクセス制御とスコープのタグの使用](../fundamentals/scope-tags.md)に関するページをご覧ください。

1. **[スコープ タグを選択]** をクリックして、必要に応じてアプリ スイートのスコープ タグを追加します。 
2. **[次へ]** をクリックして、 **[割り当て]** ページを表示します。

## <a name="step-4---assignments"></a>ステップ 4 - 割り当て

1. アプリ スイートのグループ割り当てについて、 **[必須]** 、 **[登録済みデバイスで使用可能]** 、または **[アンインストール]** を選択します。 詳細については、「[ユーザーとデバイスを整理するためのグループを追加する](~/fundamentals/groups-add.md)」と「[Microsoft Intune を使用してアプリをグループに割り当てる](apps-deploy.md)」を参照してください。
2. **[次へ]** をクリックして、 **[確認と作成]** ページを表示します。 

## <a name="step-5---review--create"></a>ステップ 5 - 確認と作成

1. アプリ スイートに入力した値と設定を確認します。
2. 完了したら、 **[作成]** をクリックしてアプリを Intune に追加します。

    作成した Office 365 Window 10 アプリ スイートの **[概要]** ブレードが表示されます。

## <a name="deployment-details"></a>展開の詳細

[Office 構成サービス プロバイダー (CSP) の](https://docs.microsoft.com/windows/client-management/mdm/office-csp) によって Intune から展開ポリシーがターゲット コンピューターに割り当てられると、エンド デバイスで *officecdn.microsoft.com* の場所からインストール パッケージが自動的にダウンロードされます。 *Program Files* ディレクトリには 2 つのディレクトリが表示されます。

![Program Files ディレクトリ内の Office インストール パッケージ](./media/apps-add-office365/office-folder.png)

*Microsoft Office* ディレクトリの下には、インストール ファイルが格納される新しいフォルダーが作成されます。

![Microsoft Office ディレクトリの下に作成された新しいフォルダー](./media/apps-add-office365/created-folder.png)

*Microsoft Office 15* ディレクトリの下には、Office のクイック実行インストール ランチャー ファイルが格納されます。 割り当ての種類が必須の場合は、インストールが自動的に開始されます。

![クイック実行インストール ランチャー ファイル](./media/apps-add-office365/clicktorun-files.png)

Office 365 スイートの割り当てが必須として構成されている場合、インストールはサイレント モードになります。 インストールが成功すると、ダウンロードされたインストール ファイルは削除されます。 割り当てが**使用可能**として構成されている場合、Office アプリケーションは Intune ポータル サイト アプリケーションに表示され、エンド ユーザーはインストールを手動でトリガーできます。

## <a name="troubleshooting"></a>トラブルシューティング
Intune では、[Office 展開ツール](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool)により、[Office 365 CDN](https://docs.microsoft.com/office365/enterprise/content-delivery-networks) を使ってクライアント コンピューターに Office 365 ProPlus がダウンロードされて展開されます。 不必要な待機時間の発生を防ぐため、「[Managing Office 365 endpoints (Office 365 のエンドポイントの管理)](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints)」で説明されているベスト プラクティスを参考にして、CDN トラフィックが中央のプロキシ経由でルーティングされるのではなく、クライアントが CDN に直接アクセスできるように、ネットワークを構成してください。

インストールまたは実行時に問題が発生する場合は、対象のデバイスで [Microsoft Office 365 サポート/回復アシスタント](https://diagnostics.office.com)を実行してください。

### <a name="additional-troubleshooting-details"></a>他のトラブルシューティングの詳細

O365 アプリをデバイスにインストールできない場合は、問題が Intune 関連か OS/Office 関連かを明らかにする必要があります。 2 つのフォルダー *Microsoft Office* と *Microsoft Office 15* がデバイスの *Program Files* ディレクトリに表示される場合は、Intune によって展開が正常に開始されたことを確認できます。 *Program Files* に 2 つのフォルダーが表示されない場合は、次のことを確認する必要があります。

- デバイスが Microsoft Intune に適切に登録されています。 
- デバイスにアクティブなネットワーク接続があります。 デバイスが機内モードである場合、オフになっている場合、またはサービスがない場所にある場合は、ネットワーク接続が確立されるまでポリシーは適用されません。
- Intune と Office 365 両方のネットワーク要件が満たされており、次の記事に基づいて、関連する IP 範囲にアクセスできます。

  - [Intune のネットワーク構成の要件と帯域幅](https://docs.microsoft.com/intune/network-bandwidth-use)
  - [Office 365 の URL と IP アドレスの範囲](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

- 適切なグループに O365 アプリ スイートが割り当てられています。 

さらに、*C:\Program Files\Microsoft Office\Updates\Download* ディレクトリのサイズ を監視します。 Intune クラウドからダウンロードされたインストール パッケージは、この場所に格納されます。 サイズが増えない場合、または非常にゆっくりとしか増えない場合は、ネットワークの接続と帯域幅を再確認することをお勧めします。

Intune とネットワーク インフラストラクチャの両方が想定どおりに動作していることを確認したら、OS の観点から問題をさらに分析する必要があります。 次の条件を考慮します。

- ターゲット デバイスでは、Windows 10 Creators Update 以降が実行されている必要があります。
- Intune によってアプリケーションが展開される間、既存の Office アプリを開かないようにします。
- Office の既存の MSI バージョンを、デバイスから適切に削除します。 Intune では、Office MSI と互換性のないクイック実行が利用されます。 この動作については、次のドキュメントで詳しく説明されています。<br>
  [同一コンピューターでクイック実行および Window インストーラーを使ってインストールされた Office はサポートされない](https://support.office.com/article/office-installed-with-click-to-run-and-windows-installer-on-same-computer-isn-t-supported-30775ef4-fa77-4f47-98fb-c5826a6926cd)
- サインイン ユーザーは、デバイスにアプリケーションをインストールするためのアクセス許可を持っている必要があります。
- Windows イベント ビューアーのログ **[Windows ログ]**  ->  **[アプリケーション]** を基にして、問題がないことを確認します。
- インストールの間に、Office インストールの詳細ログをキャプチャします。 この操作を行うには、次の手順に従います。<br>
    1. ターゲット コンピューターで Office インストールの詳細ログを有効にします。 これを行うには、次のコマンドを実行してレジストリを変更します。<br>
        `reg add HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /t REG_DWORD /d 3`<br>
    2. Office 365 スイートをターゲット デバイスにもう一度展開します。<br>
    3. 約 15 から 20 分待ってから、 **%temp%** フォルダーおよび **%windir%\temp** フォルダーに移動し、**更新日時**で並べ替えて、再現時刻に従って変更された " *<コンピューター名>-<タイムスタンプ>.log*" ファイルを選択します。<br>
    4. 次のコマンドを実行して、詳細ログを無効にします。<br>
        `reg delete HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /f`<br>
        詳細ログでは、インストール プロセスに関するさらに詳細な情報を確認できます。

## <a name="errors-during-installation-of-the-app-suite"></a>アプリ スイートのインストール中のエラー

詳細なインストール ログを表示する方法については、「[How to enable Office 365 ProPlus ULS logging (Office 365 ProPlus ULS のログ記録を有効にする方法)](/office/troubleshoot/diagnostic-logs/how-to-enable-office-365-proplus-uls-logging)」をご覧ください。

次の表は、発生する可能性がある一般的なエラー コードとその意味を一覧表示しています。

### <a name="status-for-office-csp"></a>Office CSP の状態

| 状態 | フェーズ | [説明] |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460 (ERROR_TIMEOUT) | ダウンロード | Office 展開ツールのダウンロードに失敗しました |
| 13 (ERROR_INVALID_DATA) | - | ダウンロードした Office 展開ツールの署名を確認できません |
| CertVerifyCertificateChainPolicy からのエラー コード | - | ダウンロードした Office 展開ツールの証明書の確認に失敗しました |
| 997 | WIP | インストール |
| 0 | インストール後 | インストールが正常に完了しました |
| 1603 (ERROR_INSTALL_FAILURE) | - | 前提条件のチェックでエラーになりました。例: SaS (2016 MSI がインストールされたときに、インストールを試行した) バージョンがそれ以外と一致しない |
| 0x8000ffff (E_UNEXPECTED) | - | マシン上にクイック実行 Office がないときに、アンインストールしようとしました |
| 17002 | - | シナリオ (インストール) の完了に失敗しました。 考えられる理由: ユーザーによるインストールの取り消し、別のインストールによるインストールの取り消し、インストール中のディスク容量不足、不明な言語 ID |
| 17004 | - | 不明な SKU |


### <a name="office-deployment-tool-error-codes"></a>Office 展開ツールのエラー コード

| 通信の種類 | リターン コード | UI | メモ |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------|
| アクティブなクイック実行のインストールがないときに、アンインストールします | -2147418113、0x8000ffff または 2147549183 | エラー コード:30088-1008 エラー コード: 30125-1011 (404) | Office 展開ツール |
| MSI バージョンがインストールされているときに、インストールします | 1603 | - | Office 展開ツール |
| インストールが、ユーザーまたは別のインストールによって取り消されました | 17002 | - | クイック実行 |
| 32 ビットがインストールされているデバイス上に 64 ビットをインストールしようとします。 | 1603 | - | Office 展開ツールのリターン コード |
| 不明な SKU をインストールしようとします (有効な SKU でのみ渡す必要があるため、Office CSP の正当なユース ケースではない) | 17004 | - | クイック実行 |
| 領域不足 | 17002 | - | クイック実行 |
| クイック実行のクライアントが開始に失敗しました (原因不明) | 17000 | - | クイック実行 |
| クイック実行のクライアントがシナリオをキューに登録するのに失敗しました (原因不明) | 17001 | - | クイック実行 |

## <a name="next-steps"></a>次のステップ

- アプリ スイートを追加のグループに割り当てる方法については、「[アプリをグループに割り当てる](/intune-azure/manage-apps/deploy-apps)」を参照してください。
