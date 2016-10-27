---
title: "モバイル アプリケーション管理のためにアプリを準備する | Microsoft Intune"
description: "このトピックの情報は、カスタム基幹業務アプリでモバイル アプリ管理ポリシーを使用できるようにするために、アプリ ラッピング ツールとアプリ SDK を使用するタイミングを判断するときに役立ちます。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: df1b58d5ce94c985e71f3afbe228dba9438040dc
ms.openlocfilehash: d79c498fd775ee9b3d59761fec2fe6ebba116d6d


---

# Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める
Intune アプリ ラッピング ツールまたは Intune アプリ SDK のいずれかを使うと、アプリでモバイル アプリケーション管理 (MAM) ポリシーを使用することが可能です。 ここでは、これら 2 つの方法の内容と用途について説明します。

## Intune アプリ ラッピング ツール
アプリ ラッピング ツールは、主として、内部基幹業務 (LOB) アプリケーションに使います。 このツールは、アプリのラッパーを作成するコマンド ライン アプリケーションです。このラッパーにより、アプリを Intune モバイル アプリケーション管理ポリシーで管理できるようになります。 

このツールを使うためにソース コードは必要ありませんが、署名資格情報が必要です。  署名資格情報の詳細については、[Intune のブログ](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)を参照してください。 アプリ ラッピング ツールのドキュメントとしては、[Android アプリ ラッピング ツール](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)と [iOS アプリ ラッピング ツール](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)をご覧ください。

アプリ ラッピング ツールは、Apple App Store または Google Play ストアにあるアプリ、あるいは開発ツールの統合を必要とする機能を**サポートしていません** (次の機能比較表をご覧ください)。

アプリが既に完成している場合、またはソース コードが利用できない場合は、SDK ではなく、アプリ ラッピング ツールを使用する必要があります。

**Intune に登録されていないデバイスの MAM 用アプリ ラッピング ツールの詳細については、「[Microsoft Intune に登録されていないデバイスの基幹業務アプリとデータを保護する](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md)**」を参照してください。

### サポートされるアプリ開発プラットフォーム

|**アプリ ラッピング ツール** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |Yes|[はい]|
|**Android**| いいえ |Yes|

## Intune アプリ SDK
アプリ SDK は、主として、Apple App Store または Google Play ストアにあるアプリを Intune で管理できるようにするお客様向けに設計されています。 ただし、どのようなアプリでも (基幹業務アプリでさえ)、SDK の統合を利用できます。

SDK の詳細については、「[概要](/intune/develop/intune-app-sdk)」を参照してください。 SDK で作業を開始するには、「[Microsoft Intune アプリ SDK を使ってみる](/intune/develop/intune-app-sdk-get-started)」を参照してください。

### サポートされるアプリ開発プラットフォーム

|**Intune アプリ SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|はい – Intune App SDK Xamarin コンポーネントを使用します|はい – Intune App SDK Cordova プラグインを使用します|
|**Android**| はい – Intune App SDK Xamarin コンポーネントを使用します|はい – Intune App SDK Cordova プラグインを使用します|

## 機能の比較
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
|[PIN の代わりに指紋を要求する (iOS のみ)]<br></br>**注:** MAM 専用の環境でのみ使用できます。|○||
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
### 関連項目

[Android アプリ ラッピング ツール](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[iOS アプリ ラッピング ツール](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[SDK を使用してモバイル アプリケーション管理に対応する](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Sep16_HO4-->


