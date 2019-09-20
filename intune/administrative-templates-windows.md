---
title: Microsoft Intune で Windows 10 デバイス用のテンプレートを使用する - Azure | Microsoft Docs
description: Microsoft Intune で管理用テンプレートを使用して、Windows 10 デバイスの設定のグループを作成します。 デバイス構成プロファイルでこれらの設定を使用して、Office プログラムや Microsoft Edge の制御、Internet Explorer の機能のセキュリティ保護、OneDrive へのアクセスの制御、リモート デスクトップ機能の使用、自動再生の有効化、電源管理の設定、HTTP 印刷の使用、さまざまなユーザー サインイン オプションの使用、イベント ログ サイズの制御を行います。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b41405e2256d6d2608b05a9c7e8a40cbb3ab349
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071066"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Windows 10 テンプレートを使用し、Microsoft Intune でグループ ポリシー設定を構成する

組織でデバイスを管理するとき、さまざまなデバイス グループに適用される設定のグループを作成することが推奨されます。 たとえば、いくつかのデバイス グループがあるとします。 グループ A には、特定の設定のセットを割り当てます。 グループ B には、別の設定のセットを割り当てます。 また、構成できる設定の単純なビューも必要です。

このタスクを完了するには、Microsoft Intune で**管理用テンプレート**を使用します。 管理用テンプレートには、Microsoft Edge バージョン 77 以降、Internet Explorer、Microsoft Office プログラム、リモート デスクトップ、OneDrive、パスワードと PIN などの機能を制御するための、数百の設定が含まれています。 グループ管理者は、これらの設定により、クラウドを使ってグループ ポリシーを管理できます。

Windows の設定は、Active Directory (AD) のグループ ポリシー (GPO) 設定に似ています。 これらの設定は、Windows に組み込みの、XML を使用する [ADMX ベースの設定](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) です。 Office と Microsoft Edge の設定には ADMX が取り込まれていて、[Office の管理用テンプレート ファイル](https://www.microsoft.com/download/details.aspx?id=49030)と [Microsoft Edge 管理用テンプレート ファイル](https://www.microsoftedgeinsider.com/enterprise)で ADMX 設定が使われています。 しかし、Intune のテンプレートは 100% クラウド ベースです。 これらによって、設定を構成し、必要な設定を見つけるための、簡単で明快な方法が提供されます。

**管理用テンプレート**は Intune 内に構築されており、OMA-URI の使用を含め、カスタマイズを必要としません。 モバイル デバイス管理 (MDM) ソリューションの一部として、これらのテンプレート設定を総合ポータルとして使用し、Windows 10 デバイスを管理します。

この記事では、Windows 10 デバイス用のテンプレートを作成する手順を示し、Intune で使用可能なすべての設定をフィルター処理する方法について説明します。 テンプレートを作成すると、デバイス構成プロファイルが作成されます。 その後、組織内でこのプロファイルを Windows 10 デバイスに割り当てるかデプロイできます。

## <a name="before-you-begin"></a>始める前に

- これらの設定の一部は、Windows 10 バージョン 1703 (RS2) 以降で使用可能です。 すべての Windows エディションに含まれているわけではない設定もあります。 最適なエクスペリエンスを得るには、Windows 10 Enterprise バージョン 1903 (19H1) 以降を使用することをお勧めします。

- Windows の設定では、[Windows ポリシー CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies) が使用されます。 CSP は、Home、Professional、Enterprise など、さまざまなエディションの Windows で動作します。 CSP が特定のエディションで動作するかどうかを確認するには、[Windows ポリシー CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies) に移動してください。

## <a name="create-a-template"></a>テンプレートを作成する

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **名前**: プロファイルの名前を入力します。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]** : **[Windows 10 以降]** を選択します。
    - **[プロファイルの種類]** : **[管理用テンプレート]** を選択します。

4. **[作成]** を選択します。 新しいウィンドウで、 **[設定]** を選択します。 すべての設定が一覧表示されます。戻る矢印と次へ矢印を使用して、さらに設定を表示できます。

    ![設定のサンプル一覧を表示し、戻るボタンと次へボタンを使用する](./media/administrative-templates-windows/administrative-templates-sample-settings-list.png)

    > [!TIP]
    > Intune の Windows の設定は、ローカル グループ ポリシー エディター (`gpedit`) に表示されるオンプレミスのグループ ポリシー パスに関連付けられます。

5. 既定では、ドロップダウン リストに **[すべての製品]** が表示されます。 リストから設定をフィルター処理し、**Windows** の設定のみを表示したり、**Office** の設定のみを表示したり、**Edge バージョン 77 以降**の設定のみを表示したりすることもできます。

    ![Intune の管理用テンプレートで、リストをフィルター処理して Windows または Office の設定をすべて表示する](./media/administrative-templates-windows/administrative-templates-choose-windows-office-all-products.png)

    > [!NOTE]
    > Microsoft Edge の設定の適用対象:
    >
    > - Microsoft Edge バージョン 77 以降。 Microsoft Edge バージョン 45 以前を構成するには、[Microsoft Edge ブラウザーでのデバイスの制限の設定](device-restrictions-windows-10.md#microsoft-edge-browser)に関する記事を参照してください。
    > - Windows 10 RS4 以降 ([KB 4512509](https://support.microsoft.com/kb/4512509) インストール済み)
    > - Windows 10 RS5 以降 ([KB 4512534](https://support.microsoft.com/kb/4512534) インストール済み)
    > - Windows 10 19H1 以降 ([KB 4512941](https://support.microsoft.com/kb/4512941) インストール済み)

6. 任意の設定を選択します。 たとえば、 **[Office]** でフィルター処理して、 **[参照の制限を有効にする]** を選択します。 設定の詳細説明が表示されます。 **[有効]** 、 **[無効]** を選択するか、または設定を **[未構成]** (既定値) のままにします。 詳細な説明では、 **[有効]** 、 **[無効]** 、または **[未構成]** を選択したときの動作についても説明されています。
7. **[OK]** を選択して変更を保存します。

設定の一覧を移動し、環境内で必要な設定の構成に進みます。 次に例をいくつか示します。

- **[VBA マクロ通知設定]** を使用して、Word や Excel などのさまざまな Microsoft Office プログラムで VBA マクロを処理します。
- **[ファイルのダウンロードの許可]** 設定を使用して、Internet Explorer からのダウンロードを許可または禁止します。
- **[コンピューターのスリープ状態の解除時にパスワードを要求する (電源接続時)]** を使用し、デバイスがスリープ モードから回復したときにユーザーにパスワードを求めるように設定します。
- **[未署名の ActiveX コントロールのダウンロード]** 設定を使用して、Internet Explorer からユーザーが未署名の ActiveX コントロールをダウンロードできないようブロックします。
- **[システムの復元をオフにする]** 設定を使用して、デバイスでユーザーがシステムの復元を実行するのを許可または禁止します。
- **[Allow importing of favorites]\(お気に入りのインポートを許可する\)** 設定を使用し、別のブラウザーから Microsoft Edge にお気に入りをインポートする行為をユーザーに許可または禁止します。
- ほかにも多数の設定があります。

## <a name="find-some-settings"></a>一部の設定を見つける

これらのテンプレートで使用できる設定は数百に及びます。 特定の設定を見つけやすくするには、組み込みの機能を使用します。

- 使用するテンプレートで **[設定]** 、 **[状態]** 、 **[設定の種類]** 、または **[パス]** 列を選択し、一覧を並べ替えます。 たとえば、 **[パス]** 列を選択して、`Microsoft Excel` パス内のすべての設定を表示します。

  ![Intune の管理用テンプレートで、[パス] をクリックしてグループ ポリシーまたは ADMX パスでグループ化されたすべての設定を表示する](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- テンプレートで**検索**ボックスを使用して、特定の設定を見つけます。 設定のタイトル、またはパスで検索できます。 たとえば、「 `copy`」というメッセージを探してみてください。 「`copy`」を含むすべての設定が表示されます。

  ![Intune の管理用テンプレートで、「copy」で検索して Windows または Office の設定をすべて表示する](./media/administrative-templates-windows/search-copy-settings.png) 

  もう 1 つの例として、「`microsoft word`」を検索します。 Microsoft Word プログラムに対して設定できるすべての設定が表示されます。 「`explorer`」を検索して、テンプレートに追加できる Internet Explorer のすべての設定を確認します。

## <a name="next-steps"></a>次の手順

テンプレートは作成されましたが、まだ何も行われていません。 次に、[テンプレート (プロファイルとも呼ばれる) を割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
