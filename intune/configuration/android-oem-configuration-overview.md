---
title: Microsoft Intune で Android Enterprise デバイスに OEMConfig を使用する - Azure | Microsoft Docs
description: Microsoft Intune を使用して、OEMConfig で Android Enterprise を実行するデバイスを管理および使用します。 概要を含むすべての手順を参照し、「前提条件」を参照し、Intune で構成プロファイルを作成して、サポートされている OEMConfig アプリの一覧を確認します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e514c10ea61bb12ef3c4626b077aa105b66866f1
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206875"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Microsoft Intune の OEMConfig で Android エンタープライズデバイスを使用および管理する



Microsoft Intune では、OEMConfig を使用して、Android エンタープライズデバイスの OEM 固有の設定を追加、作成、およびカスタマイズできます。 OEMConfig は通常、Intune に組み込まれていない設定を構成するために使用されます。 OEM (相手先ブランド供給) によって、設定が異なります。 使用可能な設定は、OEM が OEMConfig アプリに含める内容によって異なります。

この機能は、以下に適用されます。  

- Android エンタープライズ

この記事では、OEMConfig、前提条件の一覧、構成プロファイルの作成方法、Intune でサポートされている OEMConfig アプリの一覧を示します。

## <a name="overview"></a>概要

OEMConfig ポリシーは、[アプリ構成ポリシー](../apps/app-configuration-policies-overview.md)に似た特殊な種類のデバイス構成ポリシーです。 OEMConfig は Google によって定義された標準であり、Android のアプリ構成を利用して、Oem (相手先ブランド供給メーカー) によって作成されたアプリにデバイス設定を送信します。 この標準により、oem と Emm (エンタープライズモビリティ管理) は、OEM 固有の機能を標準化された方法で構築およびサポートできます。 [OEMConfig の詳細について](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/)は、こちらをご覧ください。

以前は、Intune などの Emm は oem によって導入された OEM 固有の機能のサポートを手動で作成しています。 このアプローチによって、重複する工数が生じ、導入に時間がかかることがあります。

OEMConfig では、oem 固有の管理機能を定義するスキーマを作成します。 OEM は、アプリにスキーマを埋め込み、このアプリを Google Play に配置します。 EMM は、アプリからスキーマを読み取り、EMM 管理者コンソールでスキーマを公開します。 コンソールでは、Intune 管理者がスキーマの設定を構成できます。

OEMConfig アプリをデバイスにインストールすると、EMM 管理者コンソールで構成された設定を使用してデバイスが管理されます。 デバイスの設定は、EMM によって作成された MDM エージェントではなく、OEMConfig アプリによって実行されます。

OEM が管理機能を追加して改善すると、OEM は Google Play でもアプリを更新します。 管理者は、これらの新機能と更新プログラム (修正プログラムを含む) を、Emm にこれらの更新プログラムが含まれるのを待たずに入手できます。

> [!TIP]
> OEMConfig は、この機能をサポートし、対応する OEMConfig アプリを持つデバイスでのみ使用できます。 具体的な詳細については、OEM に問い合わせてください。

## <a name="before-you-begin"></a>始める前に

OEMConfig を使用する場合は、次の情報に注意してください。

- Intune は、構成できるように OEMConfig アプリのスキーマを公開します。 Intune は、アプリによって提供されるスキーマを検証または変更しません。 スキーマが正しくない場合、またはデータが不正確な場合、このデータはデバイスに送信されたままになります。 スキーマで発生した問題が見つかった場合は、OEM に関するガイダンスを参照してください。
- Intune は、アプリスキーマの内容に影響を与えることも制御しません。 たとえば、Intune には、文字列、言語、許可される操作などの制御がありません。 OEMConfig を使用してデバイスを管理するための詳細とベストプラクティスについては、OEM に問い合わせることをお勧めします。
- Oem は、いつでも、サポートされている機能とスキーマを更新し、新しいアプリを Google Play にアップロードできます。 Intune は、常に最新バージョンの OEMConfig アプリを Google Play から同期します。 Intune では、以前のバージョンのスキーマやアプリは維持されません。 バージョンの競合が発生した場合、詳細については、OEM に連絡することをお勧めします。
- 1つの OEMConfig プロファイルをデバイスに割り当てます。 同じデバイスに複数のプロファイルが割り当てられている場合は、動作に一貫性がない可能性があります。 OEMConfig モデルでは、デバイスごとに1つのポリシーのみがサポートされます。

## <a name="prerequisites"></a>[前提条件]

デバイスで OEMConfig を使用するには、次の要件があることを確認してください。

- Intune に登録されている Android Enterprise デバイス。
- OEM によってビルドされ、Google Play にアップロードされた OEMConfig アプリ。 Google Play ない場合は、OEM に詳細を問い合わせてください。
- Intune 管理者は、**モバイルアプリ**、**デバイス構成**、および**Android for Work**の "読み取り" アクセス許可に対するロールベースのアクセス制御 (RBAC) アクセス許可を持っています。 これらのアクセス許可は、OEMConfig プロファイルが管理対象アプリ構成を使用してデバイス構成を管理するために必要です。

## <a name="prepare-the-oemconfig-app"></a>OEMConfig アプリを準備する

デバイスで OEMConfig がサポートされていること、正しい OEMConfig アプリが Intune に追加されていること、アプリがデバイスにインストールされていることを確認してください。 この情報については、OEM にお問い合わせください。

> [!TIP] 
> OEMConfig アプリは OEM に固有のものです。 たとえば、ゼブラ Technologies デバイスにインストールされた Sony OEMConfig アプリは何も実行しません。

1. マネージ Google Play ストアから OEMConfig アプリを取得します。 この手順は、[managed Google Play アプリを Android Enterprise デバイスに追加する](../apps/apps-add-android-for-work.md)方法に関するページに記載されています。
2. 一部の Oem は、OEMConfig アプリがプレインストールされているデバイスを出荷する場合があります。 アプリがプレインストールされていない場合は、Intune を使用し[て、デバイスにアプリを追加して展開](../apps/apps-deploy.md)します。

## <a name="create-an-oemconfig-profile"></a>OEMConfig プロファイルを作成する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **名前**:新しいプロファイルのわかりやすい名前を入力します。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]** : **[Android エンタープライズ]** を選択します。
    - **プロファイルの種類**: **[oemconfig]** を選択します。

4. **関連付けられているアプリ** を選択し、前に追加した既存の oemconfig アプリを選択し > **OK**をクリックします。 ポリシーを割り当てるデバイスの正しい OEMConfig アプリを選択してください。

    アプリが一覧に表示されない場合は、マネージ Google Play を設定し、管理対象の Google Play ストアからアプリを取得します。 この手順は、[managed Google Play アプリを Android Enterprise デバイスに追加する](../apps/apps-add-android-for-work.md)方法に関するページに記載されています。

    > [!IMPORTANT]
    > OEMConfig アプリを追加し、それを Google Play に同期していても、**関連付けら**れているアプリとして表示されていない場合は、Intune に連絡してアプリをオンボードする必要がある場合があります。 「[新しいアプリの追加](#supported-oemconfig-apps)」 (この記事) を参照してください。

5. **[設定の構成]** で、**構成デザイナー**または**JSON エディター**を使用するように選択します。

    > [!TIP]
    > プロパティが正しく構成されていることを確認するには、OEM ドキュメントを参照してください。 これらのアプリのプロパティは、Intune ではなく OEM によって含まれています。 Intune では、プロパティの検証や入力を最小限に抑えます。 たとえば、ポート番号に `abcd` を入力すると、プロファイルはその状態で保存され、構成した値を使用してデバイスに展開されます。 正しい情報を入力してください。

    - **構成デザイナー**: このオプションを選択すると、アプリスキーマ内で使用可能なプロパティが表示されます。

      - 構成デザイナーのコンテキストメニューには、より多くのオプションが使用可能であることが示されています。 たとえば、コンテキストメニューを使用して、設定の追加、削除、および並べ替えを行うことができます。 これらのオプションは OEM によって提供されます。 これらのオプションを使用してプロファイルを作成する方法については、必ず OEM アプリのドキュメントを参照してください。

      - 多くの設定には、OEM によって提供される既定値があります。 既定値があるかどうかを確認するには、設定の横にある情報アイコンをポイントします。 ツールヒントには、その設定の既定値 (該当する場合) と、OEM によって提供される詳細情報が表示されます。

      - **[クリア]** をクリックすると、プロファイルから設定が削除されます。 プロファイルに設定がない場合、プロファイルが適用されても、デバイスの値は変わりません。

      - 構成デザイナーで空の (未構成の) バンドルを作成した場合は、JSON エディターに切り替えると削除されます。

    - **Json エディター**: このオプションを選択すると、アプリに埋め込まれた完全な構成スキーマのテンプレートが json エディターで開きます。 エディターで、さまざまな設定の値を使用してテンプレートをカスタマイズします。 **構成デザイナー**を使用して値を変更すると、JSON エディターによってテンプレートが上書きされ、構成デザイナーの値が使用されます。

      - 既存のプロファイルを更新している場合、JSON エディターには、プロファイルと共に最後に保存された設定が表示されます。

      - OEMConfig スキーマは、大規模で複雑な場合があります。 別のエディターを使用してこれらの設定を更新する場合は、 **[JSON テンプレートのダウンロード]** ボタンを選択します。 任意のエディターを使用して、構成値をテンプレートに追加します。 次に、更新された JSON をコピーして、 **json エディター**プロパティに貼り付けます。

      - JSON エディターを使用して、構成のバックアップを作成できます。 設定を構成したら、この機能を使用して、の値で JSON の設定を取得します。 JSON をコピーしてファイルに貼り付け、保存します。 これで、バックアップファイルが作成されました。

    構成デザイナーで行った変更は、JSON エディターでも自動的に行われます。 同様に、JSON エディターで行った変更は、構成デザイナーで自動的に行われます。 入力に無効な値が含まれている場合は、問題を解決するまで、構成デザイナーと JSON エディターを切り替えることはできません。

6. **[OK]**  >  **[追加]** を選択して変更を保存します。 ポリシーが作成され、一覧に表示されます。

必ず[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)してください。

 > [!NOTE]
 > 各デバイスにプロファイルを 1 つ割り当てます。 OEMConfig モデルでは、デバイスごとに1つのポリシーのみがサポートされます。

次回デバイスが構成の更新を確認するときに、構成した OEM 固有の設定が OEMConfig アプリに適用されます。

> [!NOTE]
> OEMConfig standard には、現在状態レポートが含まれていません。 既定では、プロファイルの状態は **[保留中]** になります。

## <a name="supported-oemconfig-apps"></a>サポートされている OEMConfig アプリ

標準アプリと比較して、OEMConfig アプリでは、より複雑なスキーマをサポートするために Google によって付与された管理構成の特権が拡張されます。 現在、Intune では次の OEMConfig アプリがサポートされています。

-----------------

| OEM | バンドル ID | OEM ドキュメント (利用可能な場合) |
| --- | --- | ---|
| Samsung | com. android. knox. kpu | [Knox サービスプラグイン管理者ガイド](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) |
| ゼブラテクノロジ | ゼブラを構成します。 | [ゼブラ OEMConfig の概要](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com. datalogic. oemconfig | [Datalogic OEMConfig のユーザードキュメント](https://datalogic.github.io/oemconfig/) |
| Honeywell | honeywell 構成 |  |
| Kyocera | kyocera。 enterprisedeviceconfig |  |
| Spectralink-バーコード | spectralink. サービス |  |
| Spectralink | spectralink |  |
| Spectralink-デバイス | spectralink を設定します。  |  |
| Spectralink-ログ記録 | spectralink. slnklogger |  |
| Spectralink - VQO | spectralink. slnkvqo |  |

-----------------

デバイスに対して OEMConfig アプリケーションが存在するが、上の表にない場合、または Intune コンソールに表示されない場合は、電子メール `IntuneOEMConfig@microsoft.com`を送信してください。

> [!NOTE]
> Oemconfig アプリは、OEMConfig プロファイルを使用して構成する前に、Intune によってオンボードされている必要があります。 アプリがサポートされたら、テナントでの設定について Microsoft に連絡する必要はありません。 このページの指示に従ってください。

## <a name="next-steps"></a>次のステップ

- [プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
