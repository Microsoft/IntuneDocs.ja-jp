---
title: Microsoft Intune 用アプリ構成ポリシー
titleSuffix: ''
description: Microsoft Intune の iOS または Android デバイスでアプリ構成ポリシーを使用する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c9dc1d95806bcddf423bb4d92dbdf4961c15809
ms.sourcegitcommit: b0d683917af83170f85022b270270d8ced8e301c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76812476"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Microsoft Intune 用アプリ構成ポリシー

アプリ構成ポリシーを使用すると、エンドユーザーに割り当てられるポリシーに、アプリの実行前に構成設定を割り当てることができるため、アプリ設定の問題を排除するのに役立ちます。 エンドユーザーのデバイスでアプリを構成すると、設定が自動的に提供されるので、エンドユーザーが操作する必要はありません。 構成設定はアプリごとに一意です。 

iOS アプリと Android アプリの両方に構成設定を提供するアプリ構成ポリシーを作成し、使用することができます。 これらの構成設定では、アプリの構成と管理を使用して、アプリをカスタマイズできます。 構成ポリシーの設定は、通常、アプリの初回実行時に、アプリでこれらの設定が確認されるときに使用されます。 

たとえば、アプリ構成設定では、次の詳細のいずれかを指定する必要があります。

- カスタム ポート番号
- 言語の設定
- セキュリティ設定
- 会社のロゴなどのブランドの設定

エンドユーザーが代わりにこれらの設定を入力した場合は、正しく実行されない可能性があります。 アプリ構成ポリシーを使用すると、企業全体で一貫性を保ち、エンドユーザーが自力で設定を構成しようとしたときに発生するヘルプデスクへの問い合わせを減らすことができます。 アプリ構成ポリシーを使用すると、新しいアプリの導入が簡単で迅速になります。

使用できる構成パラメーターは、最終的にアプリの開発者によって決定されます。 アプリで構成がサポートされているかどうか、使用できる構成については、アプリケーション ベンダーのドキュメントを確認してください。 一部のアプリケーションでは、使用できる構成設定が Intune によって設定されます。 

> [!NOTE]
> マネージド Google Play ストアでは、構成をサポートするアプリは次のようにマークされます。
> 
> ![構成済みのアプリのスクリーンショット](./media/app-configuration-policies-overview/configured-app.png)
>
> Android デバイスの [登録の種類] としてマネージド デバイスを使用している場合は、[Google Play ストア](https://play.google.com/store/apps)ではなく、[マネージド Google Play ストア](https://play.google.com/work)のアプリのみが表示されます。 マネージド Google Play ストアは、Android for Work (AfW) や Android Enterprise とも呼ばれることがあり、アプリの構成をサポートするアプリ バージョンを含む仕事用プロファイル内のアプリです。

[含める割り当てと除外する割り当て](apps-inc-exl-assignments.md)の組み合わせを使って、エンドユーザーとデバイスのグループにアプリ構成ポリシーを割り当てることができます。 アプリ構成ポリシーを追加すると、アプリ構成ポリシーの割り当てを設定できます。 ポリシーの割り当てを設定するときに、ポリシーを適用するエンドユーザーの[グループ](../fundamentals/groups-add.md)を含めたり、除外したりできます。 含めるグループを選ぶとき、含める特定のグループを選ぶか、組み込みグループを選ぶことができます。 組み込みグループには、**すべてのユーザー**、**すべてのデバイス**、**すべてのユーザーとすべてのデバイス**が含まれます。

Intune でアプリ構成ポリシーを使用するには、次の 2 つのオプションがあります。
- **マネージド デバイス**: デバイスは、Intune で MDM (モバイル デバイス管理) プロバイダーとして管理されます。 アプリの構成をサポートするようにアプリを設計する必要があります。
- **マネージド アプリ**: Intune App SDK を統合するために開発されたアプリです。 これは、登録なしのモバイル アプリケーション管理 ([MAM-WE](app-management.md#mobile-application-management-mam-basics)) と呼ばれます。 アプリをラップして、Intune App SDK を実装およびサポートすることもできます。 アプリのラップの詳細については、「[アプリ保護ポリシーを利用するために基幹業務アプリで準備を行う](../developer/apps-prepare-mobile-application-management.md)」を参照してください。

    > [!NOTE]
    > Intune マネージド アプリでは、Intune アプリ保護ポリシーと共に展開されている場合、Intune アプリ構成ポリシーの状態が 30 分間隔でチェックインされます。 Intune アプリ保護ポリシーがユーザーに割り当てられていない場合、Intune アプリ構成ポリシーのチェックイン間隔は 720 分に設定されます。

## <a name="apps-that-support-app-configuration"></a>アプリ構成をサポートするアプリ

### <a name="managed-devices"></a>マネージド デバイス
サポートするアプリにアプリ構成ポリシーを使用できます。 Intune 内でアプリ構成をサポートするには、OS による定義に従って、アプリ構成の使用をサポートするようにアプリが記述されている必要があります。 サポートするアプリ構成キーについて詳しくは、アプリ ベンダーにお問い合わせください。

### <a name="managed-apps"></a>Managed apps
[Intune App SDK](../developer/app-sdk.md) をアプリに組み込むか、[Intune アプリ ラッピング ツール](../developer/apps-prepare-mobile-application-management.md)を使用してアプリの開発後にラップして、基幹業務アプリを準備することができます。 Intune App SDK では、アプリの開発者が必要なコード変更が最小限に抑えられます。 詳細については、「[Intune App SDK の概要](../developer/app-sdk.md)」を参照してください。 Intune App SDK と Intune アプリ ラッピング ツールの比較については、「[アプリ保護ポリシーを利用するために基幹業務アプリで準備を行う](../developer/apps-prepare-mobile-application-management.md#feature-comparison)」を参照してください。

**[デバイス登録の種類]** として **[マネージド アプリ]** を選択することで、具体的にはデバイス管理に登録されていないデバイス上の Intune 構成ポリシーによって構成されたアプリが参照されます。このとき、 **[マネージド デバイス]** は MDM チャネルを介して展開されるアプリに適用されるため、Intune によって管理されます。 これらの説明に基づいて適切な選択肢を選びます。 

![デバイス登録の種類](./media/app-configuration-policies-overview/device-enrollment-type.png)

> [!NOTE]
> Microsoft Outlook などの複数 ID アプリの場合は、ユーザー設定を考慮することができます。 たとえば、優先受信トレイではユーザー設定が尊重され、構成は変更されません。 その他のパラメーターを使用すると、ユーザーが設定を変更できるかどうかを制御できます。 詳細については、[iOS および Android 用 Outlook のアプリ構成設定の展開](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)に関する記事を参照してください。

## <a name="validate-the-applied-app-configuration-policy"></a>適用されたアプリ構成ポリシーを検証する

次の 3 つの方法を使用して、アプリ構成ポリシーを検証できます。

   1. デバイス上で視覚的に行います。 アプリ構成ポリシーで適用される動作を対象とするアプリはありますか。
   2. 診断ログを使用します (以下の「診断ログ」セクションを参照してください)。
   3. Intune ポータルで。 ポリシーの **[監視]** セクションには、関連する状態を指定できます。

      ![デバイスのインストール状態の最初のスクリーンショット](./media/app-configuration-policies-overview/device-install-status-1.png)

      ![デバイスのインストール状態の 2 つ目のスクリーンショット](./media/app-configuration-policies-overview/device-install-status-2.png)

      さらに、画面左側にある **[Intune]**  ->  **[デバイス]**  ->  **[すべてのデバイス]** で、 **[アプリの構成]** オプションを選択すると、割り当てられているすべてのポリシーとその状態が表示されます。

      ![アプリ構成のスクリーンショット](./media/app-configuration-policies-overview/app-configuration.png)

## <a name="diagnostic-logs"></a>診断ログ

### <a name="ios-configuration-on-unmanaged-devices"></a>アンマネージド デバイスでの iOS の構成

マネージド アプリの構成では、アンマネージド デバイス上で **Intune 診断ログ**を使用して iOS 構成を検証できます。 以下の手順に加えて、Microsoft Edge を使用してマネージド アプリのログにアクセスできます。 詳細については、「[iOS で Microsoft Edge を使用してマネージド アプリのログにアクセスする](~/apps/manage-microsoft-edge.md#use-microsoft-edge-on-ios-to-access-managed-app-logs)」をご覧ください。

1. デバイスにまだインストールされていない場合は、App Store から **Microsoft Edge** をダウンロードしてインストールします。 詳細については、「[保護されている Microsoft Intune アプリ](apps-supported-intune-apps.md)」を参照してください。
2. **Microsoft Edge** を起動して、ナビゲーション バーから **[バージョン情報]**  >  **[Intune ヘルプ]** を選択します。
3. **[開始する]** をクリックします。
4. **[Share Logs]\(ログの共有\)** をクリックします。
5. 選択したメール アプリを使用して自分にログを送信し、お使いの PC で表示できるようにします。 
6. テキスト ファイル ビューアーで **IntuneMAMDiagnostics.txt** を確認します。
7. `ApplicationConfiguration` を探します。 結果は次のようになります。

    ``` JSON
        {
            (
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.BlockListURLs";
                    Value = "https://www.aol.com";
                },
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.bookmarks";
                    Value = "Outlook Web|https://outlook.office.com||Bing|https://www.bing.com";
                }
            );
        },
        {
            ApplicationConfiguration =             
            (
                {
                Name = IntuneMAMUPN;
                Value = "CMARScrubbedM:13c45c42712a47a1739577e5c92b5bc86c3b44fd9a27aeec3f32857f69ddef79cbb988a92f8241af6df8b3ced7d5ce06e2d23c33639ddc2ca8ad8d9947385f8a";
                },
                {
                Name = "com.microsoft.outlook.Mail.NotificationsEnabled";
                Value = false;
                }
            );
        }
    ```

アプリケーションの構成の詳細は、テナント用に構成されているアプリケーション構成ポリシーと一致している必要があります。 

![対象アプリの構成](./media/app-configuration-policies-overview/targeted-app-configuration-3.png)

### <a name="ios-configuration-on-managed-devices"></a>マネージド デバイス上の iOS 構成

マネージド アプリの構成では、マネージド デバイス上で **Intune 診断ログ**を使用して iOS 構成を検証できます。

1. デバイスにまだインストールされていない場合は、App Store から **Microsoft Edge** をダウンロードしてインストールします。 詳細については、「[保護されている Microsoft Intune アプリ](apps-supported-intune-apps.md)」を参照してください。
2. **Microsoft Edge** を起動して、ナビゲーション バーから **[バージョン情報]**  >  **[Intune ヘルプ]** を選択します。
3. **[開始する]** をクリックします。
4. **[Share Logs]\(ログの共有\)** をクリックします。
5. 選択したメール アプリを使用して自分にログを送信し、お使いの PC で表示できるようにします。 
6. テキスト ファイル ビューアーで **IntuneMAMDiagnostics.txt** を確認します。
7. `AppConfig` を探します。 結果は、テナント用に構成されたアプリケーション構成ポリシーと一致している必要があります。

### <a name="android-configuration-on-managed-devices"></a>マネージド デバイス上の Android の構成

マネージド アプリの構成では、マネージド デバイス上で **Intune 診断ログ**を使用して iOS 構成を検証できます。

Android デバイスからログを収集するには、管理者またはエンド ユーザーが USB 接続 (またはデバイス上の**エクスプローラー**に相当する機能) を使用して、デバイスからログをダウンロードする必要があります。 手順は次のとおりです。

1. USB ケーブルを使用して、Android デバイスをコンピューターに接続します。
2. コンピューター上で、デバイスの名前が付けられたディレクトリを探します。 そのディレクトリで `Android Device\Phone\Android\data\com.microsoft.windowsintune.companyportal` を見つけます。
3. `com.microsoft.windowsintune.companyportal` フォルダー内の Files フォルダーを開き、`OMADMLog_0` を開きます。
3. `AppConfigHelper` を検索し、アプリ構成関連のメッセージを見つけます。 結果は次のデータ ブロックのようになります。

    `2019-06-17T20:09:29.1970000       INFO   AppConfigHelper     10888  02256  Returning app config JSON [{"ApplicationConfiguration":[{"Name":"com.microsoft.intune.mam.managedbrowser.BlockListURLs","Value":"https:\/\/www.aol.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.bookmarks","Value":"Outlook Web|https:\/\/outlook.office.com||Bing|https:\/\/www.bing.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.homepage","Value":"https:\/\/www.arstechnica.com"}]},{"ApplicationConfiguration":[{"Name":"IntuneMAMUPN","Value":"AdeleV@M365x935807.OnMicrosoft.com"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled","Value":"false"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled.UserChangeAllowed","Value":"false"}]}] for user User-875363642`
    
## <a name="graph-api-support-for-app-configuration"></a>Graph API のアプリ構成のサポート

アプリ構成タスクは、Graph API で実行することができます。 詳細については、[Graph API のリファレンスの MAM を対象とした構成](https://docs.microsoft.com/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta)に関するページを参照してください。Intune と Graph の詳細については、「[Microsoft Graph での Intune の操作](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-beta)」をご覧ください。

## <a name="troubleshooting"></a>トラブルシューティング

### <a name="using-logs-to-show-a-configuration-parameter"></a>ログを使用して構成パラメーターを表示する
適用されていることが確認されていても動作しないように見える構成パラメーターがログに表示される場合は、アプリ開発者による構成の実装に問題がある可能性があります。 最初にそのアプリの開発者に連絡するか、その知識ベースを確認することで、Microsoft へのサポートの問い合わせを減らすことができます。 アプリ内での構成の処理方法に問題がある場合は、そのアプリの今後更新されるバージョンで対処する必要があります。

## <a name="next-steps"></a>次のステップ

### <a name="managed-devices"></a>マネージド デバイス

- iOS デバイスでアプリ構成を使用する方法について学びます。  「[管理対象の iOS デバイス用アプリ構成ポリシーを追加する](app-configuration-policies-use-ios.md)」をご覧ください。
- Android デバイスにアプリ構成を使用する方法について学びます。  「[管理対象の Android デバイス用アプリ構成ポリシーを追加する](app-configuration-policies-use-android.md)」を参照してください。

### <a name="managed-apps"></a>Managed apps

- 管理対象アプリにアプリ構成を使用する方法について学びます。 「[デバイス登録なしで管理対象アプリ用アプリ構成ポリシーを追加する](app-configuration-policies-managed-app.md)」を参照してください。
