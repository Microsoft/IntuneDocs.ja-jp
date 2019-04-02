---
title: Microsoft Intune - Azure での Android デバイスで Zebra モビリティの拡張機能を使用して |Microsoft Docs
description: Microsoft Intune を使用して、管理および Zebra モビリティ拡張機能 (MX) と Android を実行している Zebra デバイスを使用します。 すべての手順を含む、ポータル サイト アプリをサイドロード アプリ インストール、デバイス管理者の役割を割り当てる、StageNow プロファイルの作成を参照してください。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa2734247569245794bce7fe1de68c8b20c6091f
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490606"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>使用し、Microsoft Intune で Zebra モビリティの拡張機能による Zebra デバイスの管理

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune には、アプリの管理とデバイスの設定を構成するなど、機能の豊富なセットが含まれています。 これらの組み込み機能と設定を使用して、Zebra Technologies とも呼ばれます"Zebra devices"の Android デバイスを管理できます。

Zebra に固有の他の設定を追加またはカスタマイズする場合は、使用することできますも Zebra**モビリティ拡張機能 (MX)** これらのデバイスでします。 

この機能は、以下に適用されます。

- Android

会社は、Zebra デバイスを使用して、工場での製品版の可能性があります。 など、小売業者をしているし、環境内に何千も販売関係で使用される Zebra モバイル デバイスにはが含まれています。 Intune でモバイル デバイス管理 (MDM) ソリューションの一部としてこれらのデバイスを管理できます。

Intune を使用して、デバイスに基幹業務アプリを展開する Zebra デバイスを登録できます。 [デバイス構成] プロファイルを使用して、Zebra 固有設定を管理する MX プロファイルを作成できます。

この記事では、Microsoft Intune でデバイスを Zebra で Zebra モビリティ拡張機能 (MX) を使用する方法を示します。

## <a name="before-you-begin"></a>始める前に

- Zebra Technologies から StageNow デスクトップ アプリの最新バージョンがあることを確認します。
- 必ず確認[Zebra の完全な MX 機能マトリックス](http://techdocs.zebra.com/mx/compatibility)(Zebra の web サイトを開く) を作成するプロファイルがデバイスの MX バージョン、OS バージョン、およびモデルとの互換性を確認します。
- TC20/25 デバイスなどの特定のデバイスは、StageNow ですべての利用可能な MX 機能をサポートされていません。 必ず確認[Zebra の機能のマトリックス](http://techdocs.zebra.com/mx/tc2x/)(Zebra の web サイトを開きます) で更新されたサポートについてはします。

## <a name="step-1-install-the-latest-company-portal-app"></a>手順 1: 最新のポータル サイト アプリをインストールします。

デバイスで、Google Play ストアに移動し、ダウンロードして Microsoft から Intune ポータル サイト アプリをインストールします。 Google Play からインストールすると、ポータル サイト アプリは更新プログラムを取得し、自動的に修正します。

Google Play を使用できない場合は、ダウンロード、 [Android 用 Microsoft Intune のポータル](https://www.microsoft.com/download/details.aspx?id=49140)(別の Microsoft web サイトを開きます) と[サイドロード、](#sideload-the-company-portal-app) (のこの記事)。 この方法をインストールすると、アプリの更新プログラムを受信しないまたは自動的に修正します。 定期的に更新し、アプリを手動で修正プログラムを適用する必要があります。

### <a name="sideload-the-company-portal-app"></a>ポータル サイト アプリをサイドロードする

「サイドローディング」は、アプリをインストールするには Google Play を使用しない場合です。 ポータル サイト アプリをサイドロードするには、StageNow を使用します。 

次の手順では、概要を示します。 特定の詳細については、Zebra のドキュメントを参照してください。 [StageNow を使用して、MDM に登録](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/)(Zebra の web サイトを開きます) 適切なリソースがあります。

1. StageNow でのプロファイルを作成**MDM に登録**します。
2. **展開**、MDM エージェント ファイルのダウンロードを選択します。
3. 設定、**サポート アプリ**と**構成のダウンロード**手順**いいえ**します。
4. **ダウンロード MDM**を選択します**ファイルの転送/コピー**します。 ソースと変換先の会社ポータル Android パッケージ (APK) を追加します。
5. **起動 MDM**、として既定値のまま-です。 次の詳細を追加します。

    - **[パッケージ名]**: `com.microsoft.windowsintune.companyportal`
    - **[クラス名]**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

発行プロファイルをデバイス上の StageNow アプリで使用し続けることです。 ポータル サイト アプリがインストールされ、デバイスで開きます。

> [!TIP]
> StageNow とその機能の詳細については、次を参照してください。 [StageNow Android デバイスのステージング](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html)(Zebra の web サイトを開きます)。

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>手順 2: は、ポータル サイト アプリがデバイス管理者の役割を持つことを確認します。

ポータル サイト アプリでは、Android デバイスを管理するデバイスの管理者が必要です。 デバイス管理者の役割を有効にするには、いくつか Zebra デバイスには、デバイス上のユーザー インターフェイス (UI) が含まれます。 ポータル サイト アプリ入力時にデバイスの管理者に付与するエンドユーザーに求める場合は、デバイスには、UI が含まれている[登録](#step-3-enroll-the-device-in-to-intune)(のこの記事)。

UI を使用できない場合は、使用、 **DevAdmin Manager** StageNow ポータル サイト アプリをデバイス管理者を手動で付与するプロファイルを作成するのです。

次の手順では、概要を示します。 特定の詳細については、Zebra のドキュメントを参照してください。 
[デバイスの管理者としてバッテリ スワップ モードに設定](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool)(Zebra の web サイトを開きます) 適切なリソースがあります。

1. StageNow でプロファイルを作成し、選択**Xpert モード**します。
2. 追加**DevAdmin Manager**をプロファイルします。
3. 設定**デバイス管理アクション**に**デバイス管理者として有効にする**します。
4. 設定**デバイス管理者のパッケージ名**に`com.microsoft.windowsintune.companyportal`します。
5. 設定**デバイス管理者のクラス名**に`com.microsoft.omadm.client.PolicyManagerReceiver`します。

発行プロファイルをデバイス上の StageNow アプリで使用し続けることです。 ポータル サイト アプリ デバイスの管理者ロールが付与されます。

## <a name="step-3-enroll-the-device-in-to-intune"></a>手順 3: intune でデバイスを登録します。

最初の 2 つの手順を完了すると、ポータル サイト アプリは、デバイスにインストールされます。 Intune に登録するのには、デバイスです。

[Android デバイスを登録](android-enroll.md)の手順を示します。 使用するとする可能性がありますを多く Zebra デバイスがある場合、[デバイス登録マネージャー アカウント](device-enrollment-manager-enroll.md)します。

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>手順 4: StageNow でデバイスの管理プロファイルを作成します。

StageNow を使用すると、デバイスを管理する設定を構成するプロファイルを作成します。 特定の詳細については、Zebra のドキュメントを参照してください。 [プロファイル](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/)(Zebra の web サイトを開きます) 適切なリソースがあります。

最後の手順で、StageNow でプロファイルを作成するときに選択**MDM へのエクスポート**します。 これには、XML ファイルが生成されます。 このファイルを保存します。 後の手順で必要になります。

> [!TIP]
> 組織内のデバイスに展開する前に、プロファイルをテストすることをお勧めします。 StageNow をコンピューターにプロファイルを作成する場合は、最後の手順でテストするには、使用、**テスト**オプション。 次に、デバイスの StageNow アプリ StageNow によって生成されたファイルを消費します。 
> 
> デバイスで StageNow アプリでは、プロファイルをテストするときに生成されたログを表示します。 [Zebra デバイスが Intune で Android を実行しているログオン使用 StageNow](android-zebra-mx-logs-troubleshoot.md) StageNow ログを使用してエラーを理解する情報があります。

> [!NOTE]
> パッケージの更新、または StageNow プロフィールで他のファイルを更新するアプリを参照する場合、これらの更新プログラムを取得するデバイスが必要です。 更新プログラムを取得するには、デバイスは、プロファイルが適用されるときに StageNow 配置サーバーに接続する必要があります。 
> 
> または、これらの変更を取得する Intune での組み込み機能を使用できます。 
> - アプリの管理機能を[追加](apps-add.md)、[デプロイ](apps-deploy.md)、更新、および[モニター](apps-monitor.md)アプリ。
> - 管理[システムとアプリケーションの更新プログラム](device-restrictions-android-for-work.md#device-owner-only)実行しているデバイスで Android エンタープライズ

ファイルをテストする後、次の手順では、Intune を使用してデバイスにプロファイルを展開します。

> [!NOTE]
> 各デバイスに 1 つのプロファイルを展開します。 デバイスに展開する複数の StageNow プロファイルがある場合は、StageNow のプロファイルをエクスポートし、Intune に追加する前に、1 つの XML ファイルの設定を結合します。、 
> 
> 同じ XML ファイルで同じプロパティを構成する 2 つの設定は必要ありません。 目標は、デバイスの設定との間の競合を避けるためです。

## <a name="step-5-create-a-profile-in-intune"></a>手順 5: Intune でプロファイルを作成します。

Intune で、デバイス構成プロファイルを作成します。

1. [Azure portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**[Intune]** を選択します。
2. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **名前**: 新しいプロファイルのわかりやすい名前を入力します。
    - **説明**: プロファイルの説明を入力します  この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]**: **[Android]** を選択します。
    - **プロファイルの種類**: 選択**MX プロファイル (Zebra のみ)** します。

4. **.Xml 形式で MX プロファイル**、XML のプロファイル ファイルを追加[StageNow からエクスポートした](#step-4-create-a-device-management-profile-in-stagenow)(のこの記事)。
5. **[OK]** > **[作成]** を選択して変更を保存します。 ポリシーが作成され、一覧に表示されます。

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

構成の更新の [次へ] の時間、デバイスを確認します MX プロファイルは、デバイスに展開されます。 、デバイスを登録するときに、デバイスが Intune と同期し、約 8 時間ごと。 できます[Intune での同期を強制](device-sync.md)します。 または、デバイスで、開く、**ポータル サイト アプリ** > **設定** > **同期**します。 

> [!TIP]
> - セキュリティ上の理由から、保存した後に、プロファイルの XML テキストが表示されなくなります。 テキストは暗号化されて、およびアスタリスクのみを参照してください (`****`)。 参照用に、Intune に追加する前に、MX プロファイルのコピーを保存することが推奨されます。
> 
> - Zebra デバイスに割り当てた後は、プロファイルを更新するに更新 StageNow XML ファイルを作成し、既存の Intune プロファイルを編集して、新しい StageNow XML ファイルを追加します。 この新しいファイルでは、前の StageNow ポリシー、プロファイルで上書きされます。

## <a name="next-steps"></a>次の手順

[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

[StageNow ログ Zebra デバイスのトラブルシューティングを使用して](android-zebra-mx-logs-troubleshoot.md)します。
