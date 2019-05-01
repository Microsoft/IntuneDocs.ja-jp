---
title: Microsoft Intune で Windows 10 デバイス用のテンプレートを使用する - Azure | Microsoft Docs
description: Microsoft Intune で管理用テンプレートを使用して、Windows 10 デバイスの設定のグループを作成します。 デバイス構成プロファイルでこれらの設定を使用して、Office プログラムの制御、Internet Explorer の機能のセキュリティ保護、OneDrive へのアクセスの制御、リモート デスクトップ機能の使用、自動再生の有効化、電源管理の設定、HTTP 印刷の使用、さまざまなユーザー ログオン オプションの使用、およびイベント ログ サイズの制御を行います。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/27/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 704abe5e03410b52d54c7729e1832e527ae4dfb6
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61504316"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Windows 10 テンプレートを使用し、Microsoft Intune でグループ ポリシー設定を構成する

組織内でデバイスを管理する際には、さまざまなデバイス グループに適用される設定のグループを作成する必要があります。 たとえば、いくつかのデバイス グループがあるとします。 グループ A には、特定の設定のセットを割り当てます。 グループ B には、別の設定のセットを割り当てます。 また、構成できる設定の単純なビューも必要です。

このタスクを完了するには、Microsoft Intune で**管理用テンプレート**を使用します。 管理用テンプレートには、Internet Explorer、Microsoft Office プログラム、リモート デスクトップの機能の制御、OneDrive へのアクセス、ピクチャ パスワードまたは PIN によるサインインなどを行う、数百の設定が含まれます。 これらのテンプレートは、Active Directory (AD) のグループ ポリシー (GPO) 設定に似ており、XML を使用する、[ADMX によって支援される設定](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies)です (別のドキュメント サイトを開きます)。 ただし、Intune のテンプレートは 100% クラウド ベースです。 これらのテンプレートは、設定を構成して必要な設定を見つけるための、より単純かつ明快な方法を提供します。

**管理用テンプレート**は Intune 内に構築されており、OMA-URI の使用を含め、カスタマイズを必要としません。 モバイル デバイス管理 (MDM) ソリューションの一部として、これらのテンプレート設定を総合ポータルとして使用し、Windows 10 デバイスを管理します。

この記事では、Windows 10 デバイス用のテンプレートを作成する手順を示し、Microsoft Intune で使用可能なすべての設定をフィルター処理する方法について説明します。 テンプレートを作成すると、デバイス構成プロファイルが作成されます。 その後、組織内でこのプロファイルを Windows 10 デバイスに割り当てるかデプロイできます。

## <a name="create-a-template"></a>テンプレートを作成する

1. [Azure portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**[Intune]** を選択します。
2. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **名前**: プロファイルの名前を入力します。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]**:**[Windows 10 以降]** を選択します。
    - **[プロファイルの種類]**:**[管理用テンプレート (プレビュー)]** を選択します。

4. **[作成]** を選択します。 新しいウィンドウで、**[設定]** を選択します。 すべての設定が一覧表示されます。戻る矢印と次へ矢印を使用して、さらに設定を表示できます。

    ![設定のサンプル一覧を表示し、戻るボタンと次へボタンを使用する](./media/administrative-templates-windows/sample-settings-list-next-page.png)

5. 任意の設定を選択します。 たとえば、**[ファイルのダウンロードの許可]** を選択します。 設定の詳細説明が表示されます。 **[有効化]**、**[無効化]** を選択するか、または設定を **[未構成]** (既定値) のままにします。 詳細説明では、**[有効化]**、**[無効化]**、または **[未構成]** を選択したときの動作についても説明します。
6. **[OK]** を選択して変更を保存します。

設定の一覧を移動し、環境内で必要な設定の構成に進みます。 次に例をいくつか示します。

- **[VBA マクロ通知設定]** を使用して、Word や Excel などのさまざまな Microsoft Office プログラムで VBA マクロを処理します。
- **[ファイルのダウンロードの許可]** 設定を使用して、Internet Explorer からのダウンロードを許可または禁止します。
- **[Require a password when a computer wakes (plugged in)]\(コンピューターのスリープ解除 (電源接続) 時にパスワードを要求する\)** を使用して、デバイスがスリープ モードから回復したときにユーザーにパスワードを求めるよう設定します。
- **[未署名の ActiveX コントロールのダウンロード]** 設定を使用して、Internet Explorer からユーザーが未署名の ActiveX コントロールをダウンロードできないようブロックします。
- **[システムの復元をオフにする]** 設定を使用して、デバイスでユーザーがシステムの復元を実行するのを許可または禁止します。
- ほかにも多数の設定があります。

## <a name="find-some-settings"></a>一部の設定を見つける

これらのテンプレートで使用できる設定は数百に及びます。 特定の設定を見つけやすくするには、組み込みの機能を使用します。

- テンプレートで **[設定]**、**[状態]**、または **[パス]** 列を選択して、一覧を並べ替えます。 たとえば、**[パス]** 列を選択して、`Microsoft Excel` パス内のすべての設定を表示します。

  ![[パス] をクリックしてアルファベット順に並べ替える](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- テンプレートで**検索**ボックスを使用して、特定の設定を見つけます。 たとえば、「 `copy`」というメッセージを探してみてください。 「`copy`」を含むすべての設定が表示されます。

  ![[パス] をクリックしてアルファベット順に並べ替える](./media/administrative-templates-windows/search-copy-settings.png)

  もう 1 つの例として、「`microsoft word`」を検索します。 Microsoft Word プログラムに対して設定できるすべての設定が表示されます。 「`explorer`」を検索して、テンプレートに追加できる Internet Explorer のすべての設定を確認します。

この機能では、[Windows ポリシー CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies) が使用されます (別のドキュメント サイトを開きます)。 CSP は、Home、Professional、Enterprise など、さまざまなエディションの Windows で動作します。 CSP が特定のエディションで動作するかどうかを確認するには、[Windows ポリシー CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies) に移動してください (別のドキュメント サイトを開きます)。

## <a name="next-steps"></a>次の手順

テンプレートは作成されましたが、まだ何も行われていません。 次に、[テンプレート (プロファイルとも呼ばれる) を割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
