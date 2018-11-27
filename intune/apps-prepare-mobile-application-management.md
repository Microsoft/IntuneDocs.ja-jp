---
title: Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める
description: このトピックの情報は、カスタム基幹業務アプリでモバイル アプリ管理ポリシーを使用できるようにするために、アプリ ラッピング ツールとアプリ SDK を使用するタイミングを判断するときに役立ちます。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 8841354b268f70634a61040fb06ed857120e9cfc
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181974"
---
# <a name="prepare-line-of-business-apps-for-app-protection-policies"></a>アプリ保護ポリシーを利用するために基幹業務アプリで準備を行う

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Intune アプリ ラッピング ツールまたは Intune アプリ SDK のどちらかを使って、アプリでアプリ保護ポリシーを使えるようにできます。 ここでは、これら 2 つの方法の内容と用途について説明します。

## <a name="intune-app-wrapping-tool"></a>Intune アプリ ラッピング ツール
アプリ ラッピング ツールは、主として、**内部**基幹業務 (LOB) アプリケーションに使います。 このツールは、アプリのラッパーを作成するコマンド ライン アプリケーションです。このラッパーにより、アプリを Intune アプリ保護ポリシーで管理できるようになります。 独立系ソフトウェア ベンダー (ISV) から提供されるアプリを保護するときは、ラッピングされたアプリが ISV によってサポートされるかどうかを明確にすることが重要です。

このツールを使うためにソース コードは必要ありませんが、署名資格情報が必要です。 署名資格情報の詳細については、[Intune のブログ](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)を参照してください。 アプリ ラッピング ツールのドキュメントとしては、[Android アプリ ラッピング ツール](app-wrapper-prepare-android.md)と [iOS アプリ ラッピング ツール](app-wrapper-prepare-ios.md)をご覧ください。

アプリ ラッピング ツールは、Apple App Store または Google Play ストアのアプリを**サポートしていません**。 また、開発ツールの統合が必要な一部の機能もサポートしていません (次の機能比較表を参照してください)。

Intune に登録されていないデバイスのアプリ保護ポリシー用アプリ ラッピング ツールの詳細については、「[Microsoft Intune に登録されていないデバイスの基幹業務アプリとデータを保護する](/intune-classic/deploy-use/protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune)」を参照してください。

### <a name="reasons-to-use-the-app-wrapping-tool"></a>アプリ ラッピング ツールを使用する理由
* アプリに組み込みのデータ保護機能がない。
* アプリが単純である。
* アプリが内部的に展開される。
* アプリのソース コードにアクセスできない。
* 自分で開発したアプリではない。
* アプリのユーザー認証エクスペリエンスが最小限である。

### <a name="supported-app-development-platforms"></a>サポートされるアプリ開発プラットフォーム

|**アプリ ラッピング ツール** | **Xamarin** |**Cordova** |
|------|----|----|
|**Android** |はい|はい|
|**Android**|いいえ - [Intune App SDK Xamarin Bindings](app-sdk-xamarin.md) を使用します。|はい|

## <a name="intune-app-sdk"></a>Intune App SDK
App SDK は、主として、Apple App Store または Google Play ストアにあるアプリを Intune で管理できるようにするお客様向けに設計されています。 ただし、どのようなアプリでも (基幹業務アプリでさえ)、SDK の統合を利用できます。

SDK の詳細については、「[概要](app-sdk.md)」を参照してください。 SDK で作業を開始するには、「[Microsoft Intune App SDK を使ってみる](app-sdk-get-started.md)」を参照してください。

### <a name="reasons-to-use-the-sdk"></a>SDK を使用する理由
* アプリに組み込みのデータ保護機能がない。
* アプリが複雑で、多くのエクスペリエンスを含んでいる。
* アプリが Google Play や Apple の App Store などのパブリック アプリ ストアに展開される。
* 自分が開発したアプリであり、SDK を使用するための技術的な背景を備えている。
* アプリに他の SDK 統合がある。
* アプリが頻繁に更新される。

### <a name="supported-app-development-platforms"></a>サポートされるアプリ開発プラットフォーム

|**Intune App SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**Android**|はい – [Intune App SDK Xamarin Bindings](app-sdk-xamarin.md) を使用します。|[いいえ]|
|**Android**| はい – [Intune App SDK Xamarin Bindings](app-sdk-xamarin.md) を使用します。|[いいえ]|

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
|他のアプリとの間で切り取り、コピー、貼り付けを制限する|○|○|
|[アクセスには簡易暗証番号が必要]|○|○|
|[組み込みアプリ PIN を Intune PIN で置き換える]|○||
|[PIN をリセットするまでの試行数を指定する]|○|○|
|PIN の代わりに指紋を要求する|○|○|
|PIN の代わりに顔認識を許可する (iOS のみ)|○|○|
|[アクセスには会社の資格情報が必要]|○|○|
|[脱獄またはルート化されたデバイスで管理対象アプリが実行されないようにブロックする]|○|○|
|[アプリ データの暗号化]|○|○|
|[指定した時間 (分) 後にアクセス要件を再確認する]|○|○|
|[オフラインの猶予期間を指定する]|○|○|
|[画面キャプチャをブロック (Android のみ)]|○|○|
|デバイスの登録なしで MAM をサポート|○|○|
|完全なワイプ|○|○|
|選択的なワイプ <br></br>**注:** iOS では、管理プロファイルを削除するとアプリも削除されます。|○||
|[[名前を付けて保存] を禁止する]|○||
|対象となるアプリケーションの構成|○||
|[マルチ ID アプリのサポート]|○||
|カスタマイズ可能なスタイル |○|||
|Citrix mVPN でのオンデマンドのアプリケーション VPN 接続|○|○| 
|連絡先の同期を無効にする|○|○|
|印刷を無効にする|○|○|
|アプリの最小バージョン要件|○|○|
|オペレーティング システムの最小要件 (iOS および Android のみ)|○|○|
|Android の最小セキュリティ パッチ バージョン要件 (Android のみ)|○|○|
|iOS 用 Intune SDK の最小要件 (iOS のみ)|○|○|

## <a name="next-steps"></a>次の手順

アプリ保護ポリシーと Intune の詳細については、次のトピックをご覧ください。

  - [Android アプリ ラッピング ツール](app-wrapper-prepare-android.md)</br>
  - [iOS アプリ ラッピング ツール](app-wrapper-prepare-ios.md)</br>
  - [SDK を使用してモバイル アプリケーション管理に対応する](/intune-classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management)
