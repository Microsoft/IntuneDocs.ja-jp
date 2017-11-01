---
title: "Microsoft Intune アプリ SDK の概要"
description: "Microsoft Intune でモバイル アプリケーション管理 (MAM) 用のモバイル アプリをすぐに有効にできます。"
keywords: 
author: mattbriggs
manager: angrobe
ms.author: mabriggs
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 65350c9a247c5820cb2080d8230d308a37e98d7c
ms.sourcegitcommit: 42a0e4c83e33c1a25506ca75d673e861e9206945
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2017
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Microsoft Intune アプリ SDK の概要

このガイドを利用すると、Microsoft Intune でアプリ保護ポリシーに対してモバイル アプリをすぐに有効にできます。 まず、「[Intune アプリ SDK の概要](app-sdk.md)」で説明されている Intune アプリ SDK の利点を理解しておくことをお勧めします。

Intune アプリ SDK は、iOS と Android で類似するシナリオをサポートしており、プラットフォーム全体にわたって一貫した操作性を IT 管理者に提供することを目的としています。 ただし、各プラットフォームの制限により、特定機能のサポートについてわずかな相違点があります。

## <a name="register-your-store-app-with-microsoft"></a>Microsoft でのストア アプリの登録

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>アプリが組織内向けであり、一般に公開できない場合:

アプリを登録する*必要はありません*。 社内向け基幹業務アプリの場合、IT 管理者社内にアプリを展開します。 Intune は、アプリが SDK でビルドされたことを検出し、IT 管理者がアプリ保護ポリシーを適用できるようにします。 「[アプリ保護ポリシーに対して iOS または Android アプリを有効にする](#enable-your-iOS-or-Android-app-for-app-protection-policy)」セクションに進んでください。

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Apple App Store や Google Play などのパブリック アプリ ストアにアプリをリリースする場合:

最初に Microsoft Intune にアプリを登録し、登録規約に同意する_**必要があります**_。 その後、IT 管理者はアプリ保護ポリシーを対応アプリに適用できるようになり、そのアプリは Intune アプリ パートナーとしてリストされます。

登録が完了し、Microsoft Intune チームによって確認されるまで、Intune 管理者はアプリ保護ポリシーをアプリのディープ リンクに適用できません。 アプリは、[Microsoft Intune パートナーのページ](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)にも追加されます。 ここには、Intune のアプリ保護ポリシーに対応していることを示すアプリのアイコンが表示されます。

登録プロセスを開始するには、[Microsoft Intune アプリ パートナー アンケート](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u)に記入します。

Microsoft が、アンケートに入力された電子メール アドレスを使用してご連絡し、登録プロセスを続行します。 また、何らかの問題が発生した場合の連絡にも、登録電子メール アドレスを使用します。

> [!NOTE]
> アンケートおよび Microsoft Intune チームとの電子メール通信で収集されたすべての情報は、[Microsoft のプライバシーに関する声明](https://www.microsoft.com/privacystatement/default.aspx)に従って処理されます。

**登録プロセスの流れ**:

1. アンケートを送信すると、正常に受信したことを確認するか、または登録を完了するための追加情報を要求する目的で、Microsoft から登録電子メール アドレスにご連絡します。

2. 必要な情報をすべて受け取った後、Microsoft は署名のために Microsoft Intune アプリ パートナー契約をお送りします。 この契約には、Microsoft Intune アプリ パートナーになる上でお客様の会社が同意する必要のある条項が記載されています。

3. また、アプリが正常に Microsoft Intune サービスに登録されたり、アプリが [Microsoft Intune パートナー](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)のサイトで推奨されたりした場合にも連絡があります。

4. 最後に、アプリのディープ リンクが、次の月の Intune サービス更新に追加されます。 たとえば、7 月に登録情報を完了した場合、ディープ リンクのサポートは 8 月中旬になります。

アプリのディープ リンクを今後変更する場合は、アプリを再登録する必要があります。

> [!NOTE]
> 新しいバージョンの Intune アプリ SDK を使用してアプリを更新する場合には、ご連絡ください。



## <a name="download-the-sdk-files"></a>SDK ファイルをダウンロードする

ネイティブ iOS 用および Android 用の Intune アプリ SDK は、Microsoft GitHub アカウントでホストされています。 ネイティブ iOS 用および Android 用の SDK ファイルは、それぞれ以下のパブリック リポジトリにあります。

* [iOS 用 Intune アプリ SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [Android 用 Intune アプリ SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

アプリが Xamarin アプリまたは Cordova アプリの場合は、次の SDK バリアントを使用してください。

* [Intune App SDK Xamarin コンポーネント](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Intune App SDK Cordova プラグイン](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

リポジトリのフォークとプルに使用できる GitHub アカウントにサインアップすることをお勧めします。 GitHub では、Microsoft 製品チームとのやり取り、問題の提出と迅速な応答、リリース ノートの表示、Microsoft へのフィードバックの提供が可能です。 Intune アプリ SDK GitHub についてご不明な点がある場合は、msintuneappsdk@microsoft.com にお問い合わせください。





## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>アプリ保護ポリシーに対して iOS または Android アプリを有効にする

以下の開発者ガイドのいずれかが必要になります。これらは、Intune アプリ SDK をご使用のアプリに統合するのに役立ちます。

* **[iOS 用 Intune アプリ SDK 開発者ガイド](app-sdk-ios.md)**: このドキュメントでは、Intune アプリ SDK を使用したネイティブ iOS アプリを有効にする方法について、段階的に説明しています。

* **[Android 用 Intune アプリ SDK 開発者ガイド](app-sdk-android.md)**: このドキュメントでは、Intune アプリ SDK を使用したネイティブ Android アプリを有効にする方法について、段階的に説明しています。

* **[Intune App SDK Cordova プラグイン ガイド](app-sdk-cordova.md)**: このドキュメントは、iOS アプリと Android アプリを Cordova を使用してビルドし、Intune アプリ保護ポリシーを適用するのに役立ちます。

* **[Intune App SDK Xamarin コンポーネント ガイド](app-sdk-xamarin.md)**: このドキュメントは、iOS アプリと Android アプリを Cordova を使用してビルドし、Intune アプリ保護ポリシーを適用するのに役立ちます。



## <a name="enable-your-ios-or-android-app-for-app-based-conditional-access"></a>アプリ ベースの条件付きアクセスに対して iOS または Android アプリを有効にする
 
 アプリの保護ポリシーに対してアプリを有効することに加えて、Azure Active Directory (AAD) アプリ ベースの条件付きアクセスでアプリが正常に機能するには、次の条件が必須です。
 
 * アプリのビルドには [Azure Active Directory Authentication Library](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-authentication-libraries) が使用されていて、AAD ブローカー認証に対してアプリが有効になっている。
 
 * アプリの [AAD クライアント ID](https://docs.microsoft.com/en-us/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#optional-configure-a-native-client-application) は、iOS および Android のプラットフォーム全体で一意である必要がある。
 
 
 

## <a name="configure-telemetry-for-your-app"></a>アプリの製品利用統計情報を構成する

Microsoft Intune はアプリの利用統計データを収集します。

* **iOS 用 Intune アプリ SDK**: SDK により、既定では、使用状況イベントに関する SDK 製品利用統計情報がログに記録されます。 このデータは、Microsoft Intune に送信されます。

    * アプリから SDK の製品利用統計情報を Microsoft Intune に送信しない場合は、IntuneMAMSettings ディレクトリのプロパティ `MAMTelemetryDisabled` を "YES" に設定して、製品利用統計情報の送信を無効にする必要があります。


* **Android 用 Intune アプリ SDK**: SDK によって製品利用統計情報データがログに記録されることはありません。

## <a name="next-steps-after-integration"></a>統合後の次の手順

### <a name="test-your-app"></a>アプリのテスト
iOS または Android アプリを Intune アプリ SDK と統合するために必要な手順を完了した後、すべてのアプリ保護ポリシーが、ユーザーと IT 管理者に対して有効化され、機能していることを確認する必要があります。統合されたアプリをテストするには、次の手順を実行します。

* **Microsoft Intune のテスト アカウント**: Intune アプリ保護機能に対して Intune 対応アプリをテストするには、Microsoft Intune のアカウントが必要です。

    * Intune アプリ保護ポリシーに対して iOS または Android ストア アプリを有効化している ISV の場合は、登録ステップで説明した Microsoft Intune での登録が完了すると、プロモーション コードを受け取ります。 プロモーション コードを使用すると、Microsoft Intune の 1 年間の拡張使用試用版にサインアップできます。

    * ストアに出荷されない基幹業務アプリを開発している場合は、組織を介して Microsoft Intune へのアクセス権が付与されます。 この場合も、[Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) で、1 か月間の無料試用版にサインアップできます。

* **Intune のアプリ保護ポリシー**: Intune のすべてのアプリ保護ポリシーに対して、ご使用のアプリをテストするには、ポリシー設定ごとに想定される動作を把握する必要があります。 [iOS アプリ保護ポリシー](/intune-classic/deploy-use/ios-mam-policy-settings)と [Android アプリ保護ポリシー](/intune-classic/deploy-use/android-mam-policy-settings)の説明を参照してください。

* **トラブルシューティング**: アプリのユーザー操作を手動でテストしているときに問題が発生した場合は、「[モバイル アプリケーション管理に関するトラブルシューティング](/intune-classic/troubleshoot/troubleshoot-mam)」を確認してください。 この記事では、Intune 対応アプリで発生する可能性のある一般的な問題と表示されるダイアログおよびエラー メッセージについて説明しています。 

### <a name="badge-your-app-optional"></a>アプリにバッジを付ける (省略可能)

Intune アプリ保護ポリシーがアプリで機能していることを確認したら、アプリ アイコンに Intune アプリ保護ロゴ バッジを付けることができます。

このバッジは、アプリに Intune アプリ保護ポリシーが適用されていることを、IT 管理者、エンド ユーザー、および Intune の見込み顧客に示すものです。 Intune の顧客によるアプリの使用と採用を促します。

ブリーフケース アイコンのバッジは、次のサンプルのように表示されます。

![バッジの例 1](./media/badge-example-1.png) ![バッジの例 2](./media/badge-example-2.png)

**アプリにバッジを付けるために必要なもの**:

* **.eps** ファイルを読み取れるイメージ操作アプリケーション、または **.ai** ファイルを読み取れる Adobe アプリケーション。

* [Intune アプリ バッジのアセットとガイドライン](https://github.com/msintuneappsdk/intune-app-partner-badge)は、Microsoft Intune GitHub にあります。
