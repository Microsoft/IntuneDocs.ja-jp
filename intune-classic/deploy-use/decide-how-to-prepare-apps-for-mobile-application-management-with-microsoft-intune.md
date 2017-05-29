---
title: "Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める | Microsoft Docs"
description: "このトピックの情報は、カスタム基幹業務アプリでモバイル アプリ管理ポリシーを使用できるようにするために、アプリ ラッピング ツールとアプリ SDK を使用するタイミングを判断するときに役立ちます。"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: oldang
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 8ee746ec2ccd9b924c242e956a8c89fba248ca96
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="prepare-line-of-business-apps-for-mam"></a>基幹業務アプリを MAM 向けに準備する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune アプリ ラッピング ツールまたは Intune アプリ SDK のいずれかを使うと、アプリでモバイル アプリケーション管理 (MAM) ポリシーを使用することが可能です。 ここでは、これら 2 つの方法の内容と用途について説明します。

## <a name="intune-app-wrapping-tool"></a>Intune アプリ ラッピング ツール
アプリ ラッピング ツールは、主として、内部基幹業務 (LOB) アプリケーションに使います。 このツールは、アプリのラッパーを作成するコマンド ライン アプリケーションです。このラッパーにより、アプリを Intune MAM ポリシーで管理できるようになります。

このツールを使うためにソース コードは必要ありませんが、署名資格情報が必要です。  署名資格情報の詳細については、[Intune のブログ](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)を参照してください。 アプリ ラッピング ツールのドキュメントとしては、[Android アプリ ラッピング ツール](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)と [iOS アプリ ラッピング ツール](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)をご覧ください。

アプリ ラッピング ツールは、Apple App Store または Google Play ストアのアプリを**サポートしていません**。 また、開発ツールの統合が必要な一部の機能もサポートしていません (次の機能比較表を参照してください)。


Intune に登録されていないデバイスの MAM 用アプリ ラッピング ツールの詳細については、「[Microsoft Intune に登録されていないデバイスの基幹業務アプリとデータを保護する](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md)」を参照してください。

### <a name="reasons-to-use-the-app-wrapping-tool"></a>アプリ ラッピング ツールを使用する理由:
* アプリに組み込みのデータ保護機能がない。
* アプリが単純である。
* アプリが内部的に展開される。
* アプリのソース コードにアクセスできない。
* 自分で開発したアプリではない。
* アプリのユーザー認証エクスペリエンスが最小限である。


### <a name="supported-app-development-platforms"></a>サポートされるアプリ開発プラットフォーム

|**アプリ ラッピング ツール** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |Yes|Yes|
|**Android**| いいえ |Yes|

## <a name="intune-app-sdk"></a>Intune アプリ SDK
アプリ SDK は、主として、Apple App Store または Google Play ストアにあるアプリを Intune で管理できるようにするお客様向けに設計されています。 ただし、どのようなアプリでも (基幹業務アプリでさえ)、SDK の統合を利用できます。

SDK の詳細については、「[概要](../develop/intune-app-sdk.md)」を参照してください。 SDK で作業を開始するには、「[Microsoft Intune アプリ SDK を使ってみる](../develop/intune-app-sdk-get-started.md)」を参照してください。

### <a name="reasons-to-use-the-sdk"></a>SDK を使用する理由
* アプリに組み込みのデータ保護機能がない。
* アプリが複雑で、多くのエクスペリエンスを含んでいる。
* アプリが Google Play や Apple の App Store などのパブリック アプリ ストアに展開される。
* 自分が開発したアプリであり、SDK を使用するための技術的な背景を備えている。
* アプリに他の SDK 統合がある。
* アプリが頻繁に更新される。

### <a name="supported-app-development-platforms"></a>サポートされるアプリ開発プラットフォーム

|**Intune アプリ SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|はい – [Intune App SDK Xamarin コンポーネント](../develop/intune-app-sdk-xamarin.md)を使用します。|はい – [Intune App SDK Cordova プラグイン](../develop/intune-app-sdk-cordova.md)を使用します。|
|**Android**| はい – [Intune App SDK Xamarin コンポーネント](../develop/intune-app-sdk-xamarin.md)を使用します。|はい – [Intune App SDK Cordova プラグイン](../develop/intune-app-sdk-cordova.md)を使用します。|

## <a name="feature-comparison"></a>機能の比較
アプリ SDK とアプリ ラッピング ツールに対して利用できる設定を、次の表に示します。

> [!NOTE]
> アプリ ラッピング ツールは、スタンドアロンの Intune または Configuration Manager と統合した Intune で使用できます。

|機能|アプリ SDK|アプリ ラッピング ツール|
|-----------|---------------------|-----------|
|[Web コンテンツを会社の管理対象ブラウザーで表示するように制限する]|○|○|
|[Android、iTunes、iCloud のバックアップを禁止する]|○|○|
|[アプリで他のアプリへのデータ転送を許可する]|○|○|
|[アプリで他のアプリからのデータの受信を許可する]|○|○|
|[切り取り、コピー、および他のアプリでの貼り付けを制限する]|○|○|
|[アクセスには簡易暗証番号が必要]|○|○|
|[組み込みアプリ PIN を Intune PIN で置き換える]|○||
|[PIN をリセットするまでの試行数を指定する]|○|○|
|PIN の代わりに指紋を要求する |○|○|
|[アクセスには会社の資格情報が必要]|○|○|
|[脱獄またはルート化されたデバイスで管理対象アプリが実行されないようにブロックする]|○|○|
|[アプリ データの暗号化]|○|○|
|[指定した時間 (分) 後にアクセス要件を再確認する]|○|○|
|[オフラインの猶予期間を指定する]|○|○|
|[画面キャプチャをブロック (Android のみ)]|○|○|
|完全なワイプ|○|○|
|選択的なワイプ <br></br>**注:** iOS では、管理プロファイルを削除するとアプリも削除されます。|○||
|[[名前を付けて保存] を禁止する] |○||
|[マルチ ID アプリのサポート]|○||
|デバイスの登録なしで MAM をサポート|○|○|
|カスタマイズ可能なスタイル |○|||
### <a name="see-also"></a>関連項目

[Android アプリ ラッピング ツール](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[iOS アプリ ラッピング ツール](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[SDK を使用してモバイル アプリケーション管理に対応する](use-the-sdk-to-enable-apps-for-mobile-application-management.md)

