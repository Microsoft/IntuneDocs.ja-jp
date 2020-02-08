---
title: Microsoft Intune で Android Enterprise デバイスに OEMConfig を使用する - Azure | Microsoft Docs
description: Microsoft Intune を使用して、Android Enterprise を実行するデバイスを OEMConfig を使って管理および使用します。 概要を含むすべての手順を参照します。前提条件を確認し、Intune で構成プロファイルを作成して、サポートされている OEMConfig アプリの一覧を確認します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2020
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
ms.openlocfilehash: 9cc568cbadb683f632ffd2365ab7023cd796f231
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886696"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Microsoft Intune で、OEMConfig を使って Android Enterprise デバイスを使用および管理する

Microsoft Intune では、OEMConfig を使用して、Android Enterprise デバイスの OEM 固有の設定を追加、作成、およびカスタマイズできます。 OEMConfig は通常、Intune に組み込まれていない設定を構成するために使用されます。 OEM (相手先ブランド供給) によって、設定が異なります。 使用可能な設定は、OEM が OEMConfig アプリに含める内容によって異なります。

この機能は、以下に適用されます。  

- Android エンタープライズ

この記事では、OEMConfig について説明し、前提条件の一覧、構成プロファイルの作成方法、Intune でサポートされている OEMConfig アプリの一覧を示します。

## <a name="overview"></a>概要

OEMConfig ポリシーは特殊な種類のデバイス構成ポリシーで、[アプリ構成ポリシー](../apps/app-configuration-policies-overview.md)に似ています。 OEMConfig は Google が定義する標準で、Android のアプリ構成を使用して、OEM (相手先ブランド供給) が作成したアプリにデバイス設定を送信します。 この標準により、OEM と EMM (エンタープライズ モビリティ管理) は、OEM 固有の機能を標準化された方法で構築およびサポートできます。 OEMConfig の詳細については、[こちら](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/)をご覧ください。

これまで、Intune などの EMM では、OEM が導入した OEM 固有の機能のサポートを手動で構築していました。 このアプローチでは、作業が重複し、導入に時間がかかります。

OEM では、OEMConfig を使用して OEM 固有の管理機能を定義するスキーマが作成されます。 OEM によりスキーマがアプリに埋め込まれ、このアプリが Google Play に公開されます。 EMM でアプリからスキーマが読み取られ、EMM 管理者コンソールにスキーマが示されます。 Intune 管理者はコンソールを使って、スキーマの設定を構成することができます。

OEMConfig アプリがデバイスにインストールされると、EMM 管理者で構成する設定を使用してデバイスが管理されます。 デバイス設定は、EMM によって作成される MDM エージェントではなく、OEMConfig アプリによって実行されます。

OEM によって管理機能が追加され、改善されると、Google Play のアプリも更新されます。 管理者として、これらの新機能と更新プログラム (修正プログラムを含む) を、EMM にこれらの更新プログラムが含まれるのを待たずに入手することができます。

> [!TIP]
> この機能がサポートされ、対応している OEMConfig アプリがあるデバイスでのみ OEMConfig を使用することができます。 具体的な詳細については、OEM にお問い合わせください。

## <a name="before-you-begin"></a>始める前に

OEMConfig を使用する場合は、次の情報に注意してください。

- Intune では、ユーザーが構成できるように、OEMConfig アプリのスキーマが示されます。 Intune では、アプリによって提供されるスキーマの検証と変更は行われません。 そのため、スキーマが正しくなかったり、データが不正確だったりしても、このデータはデバイスに送信されます。 スキーマに起因する問題が見つかった場合は、OEM にお問い合わせください。
- Intune により、アプリ スキーマの内容が影響を受けたり、制御されたりすることはありません。 たとえば、Intune では、文字列、言語、許可される操作などを制御できません。 OEMConfig を使用したデバイス管理の詳細については、OEM に問い合わせることをお勧めします。
- OEM では、いつでも、サポートされている機能とスキーマを更新し、新しいアプリを Google Play にアップロードすることができます。 Intune では、常に Google Play からの最新バージョンの OEMConfig アプリと同期しています。 Intune では、以前のバージョンのスキーマとアプリのメンテナンスは行われません。 バージョンの競合が発生した場合は、詳細について OEM に問い合わせることをお勧めします。
- 1 つの OEMConfig プロファイルをデバイスに割り当てます。 複数のプロファイルが同じデバイスに割り当てられると、一貫性のない動作が発生する可能性があります。 OEMConfig モデルでは、デバイスごとに 1 つのポリシーのみがサポートされます。

## <a name="prerequisites"></a>[前提条件]

お使いのデバイスで OEMConfig を使用するには、次の要件を満たしていることを確認してください。

- Intune に登録されている Android Enterprise デバイス。
- OEM が作成し、Google Play にアップロードした OEMConfig アプリ。 Google Play で公開されていない場合は、OEM に詳細を問い合わせてください。
- Intune 管理者が、**モバイル アプリ**、**デバイス構成**、**Android for Work** の "読み取り" アクセス許可に対するロールベースのアクセス制御 (RBAC) アクセス許可を持っている。 これらのアクセス許可が必要なのは、OEMConfig プロファイルで、管理対象アプリ構成が使用され、デバイス構成が管理されるからです。

## <a name="prepare-the-oemconfig-app"></a>OEMConfig アプリを準備する

デバイスで OEMConfig がサポートされていること、正しい OEMConfig アプリが Intune に追加されていること、アプリがデバイスにインストールされていることを確認してください。 この情報については、OEM にお問い合わせください。

> [!TIP] 
> OEMConfig アプリは OEM に固有です。 たとえば、Zebra Technologies 製デバイスにインストールされた Sony OEMConfig アプリでは何も実行されません。

1. managed Google Play ストアから OEMConfig アプリを取得します。 この手順は、[managed Google Play アプリを Android Enterprise デバイスに追加する](../apps/apps-add-android-for-work.md)方法に関するページに記載されています。
2. OEM によっては、OEMConfig アプリがプレインストールされたデバイスを出荷します。 アプリがプレインストールされていない場合は、Intune を使用して、[アプリをデバイスに追加しデプロイ](../apps/apps-deploy.md)します。

## <a name="create-an-oemconfig-profile"></a>OEMConfig プロファイルを作成する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **[プラットフォーム]** : **[Android エンタープライズ]** を選択します。
    - **プロファイルの種類**: **[OEMConfig]** を選択します。

4. **[作成]** を選択します。
5. **[Basics]\(基本\)** で次のプロパティを入力します。

    - **名前**:新しいプロファイルのわかりやすい名前を入力します。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **OEMConfig アプリ**: **[OEMConfig アプリを選択]** を選択します。

6. **[関連アプリ]** で、前に追加した既存の OEMConfig アプリを選択し、 **[選択]** をクリックします。 ポリシーを割り当てるデバイスの正しい OEMConfig アプリを選択してください。

    アプリが一覧に表示されていない場合は、managed Google Play を設定し、managed Google Play ストアからアプリを取得します。 この手順は、[managed Google Play アプリを Android Enterprise デバイスに追加する](../apps/apps-add-android-for-work.md)方法に関するページに記載されています。

    > [!IMPORTANT]
    > OEMConfig アプリを追加して Google Play に同期したのに**関連アプリ**として表示されない場合は、Intune によってアプリがオンボードされるように連絡する必要があります。 この記事の中の[新しいアプリの追加](#supported-oemconfig-apps)に関するセクションを参照してください。

7. **[次へ]** を選択します。
8. **[Configure settings]\(設定の構成\)** で、 **[構成デザイナー]** または **[JSON エディター]** を選択します。

    > [!TIP]
    > OEM ドキュメントを参照して、確実にプロパティを正しく構成します。 アプリのこれらのプロパティは、Intune ではなく OEM によって提供されます。 Intune では、プロパティまたは入力内容について最小限の検証が行われます。 たとえば、ポート番号に `abcd` を入力すると、そのままプロファイルに保存され、構成した値を使用してデバイスに展開されます。 必ず、正しい情報を入力してください。

    - **構成デザイナー**: このオプションを選択すると、アプリ スキーマ内で使用可能なプロパティが表示されるので、構成することができます。

      - 構成デザイナーのコンテキスト メニューには、より多くのオプションが使用可能であることが示されます。 たとえば、コンテキスト メニューを使用して、設定の追加、削除、および並べ替えを行うことができます。 これらのオプションは OEM によって提供されています。 これらのオプションを使用してプロファイルを作成する方法については、必ず OEM アプリのドキュメントを参照してください。

      - 多くの設定には、OEM によって提供される既定値があります。 既定値があるかどうかを確認するには、設定の横にある情報アイコンをポイントします。 ヒントには、その設定の既定値 (存在する場合) と、OEM によって提供される詳細情報が表示されます。

      - **[クリア]** をクリックすると、プロファイルから設定が削除されます。 プロファイルに設定がない場合、プロファイルが適用されても、デバイスの値は変わりません。

      - 構成デザイナーで空 (未構成) のバンドルを作成した場合は、JSON エディターに切り替えると削除されます。

    - **JSON エディター**: このオプションを選択すると、JSON エディターが開き、アプリに埋め込まれた完全な構成スキーマのテンプレートが表示されます。 エディターで、さまざまな設定に値を指定してテンプレートをカスタマイズします。 **構成デザイナー**を使用して値を変更すると、JSON エディターで、構成デザイナーの値でテンプレートが上書きされます。

      - 既存のプロファイルを更新すると、JSON エディターには、プロファイルと共に最後に保存された設定が表示されます。

      - OEMConfig スキーマは、大規模で複雑な場合があります。 別のエディターを使用してこれらの設定を更新する場合は、 **[JSON テンプレートをダウンロードします]** ボタンを選択します。 任意のエディターを使用して、構成値をテンプレートに追加します。 次に、更新した JSON をコピーして、 **[JSON エディター]** プロパティに貼り付けます。

      - JSON エディターを使用して、構成のバックアップを作成できます。 設定を構成したら、この機能を使用して、指定した値を含む JSON 設定を取得します。 JSON をコピーしてファイルに貼り付け、保存します。 これで、バックアップ ファイルが作成されました。

    構成デザイナーで変更を行うと、JSON エディターでも自動的に変更が行われます。 同様に、JSON エディターで変更を行うと、構成デザイナーで自動的に変更が行われます。 入力した内容に無効な値が含まれていると、問題を解決するまで、構成デザイナーと JSON エディターを切り替えることができません。

9. **[次へ]** を選択します。
10. **スコープ タグ** (オプション) で、`US-NC IT Team` や `JohnGlenn_ITDepartment` など、特定の IT グループにプロファイルをフィルター処理するためのタグを割り当てます。 スコープ タグの詳細については、[分散 IT に RBAC とスコープのタグを使用する](../fundamentals/scope-tags.md)に関するページを参照してください。

    **[次へ]** を選択します。

11. **[割り当て]** で、プロファイルを受け取るユーザーまたはグループを選択します。 各デバイスにプロファイルを 1 つ割り当てます。 OEMConfig モデルでは、デバイスごとに 1 つのポリシーのみがサポートされます。

    プロファイルの割り当ての詳細については、[ユーザーおよびデバイス プロファイルの割り当て](device-profile-assign.md)に関するページを参照してください。

    **[次へ]** を選択します。

12. **[確認と作成]** で、設定を確認します。 **[作成]** を選択すると、変更内容が保存され、プロファイルが割り当てられます。 また、ポリシーがプロファイル リストに表示されます。

デバイスによって次に構成の更新が確認されるときに、構成した OEM 固有の設定が OEMConfig アプリに適用されます。

> [!NOTE]
> OEMConfig 標準には現在、状態レポートは含まれていません。 そのため、既定では、プロファイルに **[Pending]\(保留中\)** の状態が示されます。

## <a name="supported-oemconfig-apps"></a>サポートされている OEMConfig アプリ

OEMConfig アプリでは、標準アプリと比較して、より複雑なスキーマをサポートできるように、Google が付与する管理構成アクセス許可が拡張されています。 現在、Intune では次の OEMConfig アプリがサポートされています。

-----------------

| OEM | バンドル ID | OEM ドキュメント (利用可能な場合) |
| --- | --- | ---|
| Samsung | com.samsung.android.knox.kpu | [Knox Service Plugin Admin Guide (Knox サービス プラグイン管理者ガイド)](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) |
| Zebra Technologies | com.zebra.oemconfig.common | [Zebra OEMConfig overview (Zebra OEMConfig の概要)](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com.datalogic.oemconfig | [User Documentation for Datalogic OEMConfig (Datalogic OEMConfig のユーザー ドキュメント)](https://datalogic.github.io/oemconfig/) |
| Honeywell | com.honeywell.oemconfig |  |
| 京セラ | jp.kyocera.enterprisedeviceconfig |  |
| Spectralink - バーコード | com.spectralink.barcode.service |  |
| Spectralink - ボタン | com.spectralink.buttons |  |
| Spectralink - デバイス | com.spectralink.slnkdevicesettings  |  |
| Spectralink - ログ記録 | com.spectralink.slnklogger |  |
| Spectralink - VQO | com.spectralink.slnkvqo |  |
| HMD Global | com.hmdglobal.app.oemconfig.ironman |  |

-----------------

お使いのデバイスに OEMConfig アプリが存在するが、上記の表にない、または Intune コンソールに表示されない場合は、`IntuneOEMConfig@microsoft.com` までメールを送信してください。

> [!NOTE]
> OEMConfig アプリは、OEMConfig プロファイルを使用して構成する前に、Intune によってオンボードされている必要があります。 アプリがサポートされたら、テナントでの設定について Microsoft に連絡する必要はありません。 このページの指示に従ってください。

## <a name="next-steps"></a>次のステップ

[プロファイルの状態を監視する](device-profile-monitor.md)。
