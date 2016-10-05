---
title: "Microsoft Intune アプリ SDK を使ってみる | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba9ba203c9ec173dafd1d6f9e4828d4a8a51e1ef
ms.openlocfilehash: 136dd127c5e0f1784746b973ebc5594573f07925


---

# Microsoft Intune アプリ SDK を使ってみる

この入門ガイドを使用すると、Microsoft Intune でモバイル アプリケーション管理用のモバイル アプリをすぐに有効にできます。 [Intune アプリ SDK の概要](intune-app-sdk.md)に列挙されている Intune アプリ SDK の利点を最初に理解しておくと、役に立つ場合があります。

このガイドは、Microsoft Intune を使用したアプリケーションでモバイル アプリ管理を有効にするために必要な主要な手順について、段階的に説明します。 Intune アプリ SDK は、プラットフォーム間で類似するシナリオをサポートしており、プラットフォーム全体にわたって一貫した操作性を IT 管理者に提供することを目的としています。 ただし、プラットフォームの制限事項により、特定機能のサポートについてわずかな相違点があります。

# 概要

## Microsoft でのストア アプリの登録

**アプリが社内用であり、社外向けアプリ ストアでは提供しない場合**:

アプリを登録する**必要はありません**。 社内向け基幹業務アプリの場合、IT 管理者は Microsoft Intune を使用して社内にアプリを展開します。 Intune は、アプリが SDK でビルドされたことを検出し、IT 管理者がアプリに MAM ポリシーの設定を適用できるようにします。 「[SDK を使用する MAM に対して iOS または Android のモバイル アプリを有効にする](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk)」セクションに進んでください。

**Apple App Store や Google Play などの社外向けアプリ ストアにアプリをリリースする場合**: 

最初に Microsoft Intune にアプリを登録し、登録規約に同意する**必要があります**。 登録後、IT 管理者は Intune MAM ポリシー設定を対応アプリに適用でき、それにより Intune アプリ パートナーとして掲示されるようになります。 登録が完了し、Microsoft Intune チームによって確認されるまで、Intune 管理者は MAM ポリシーをアプリのディープ リンクに適用できません。 アプリのアイコンでアプリが Microsoft Intune MAM ポリシーをサポートすることが示されると、アプリは [Microsoft Intune パートナーのページ](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)にも追加されます。

登録プロセスを開始するには、[Microsoft Intune パートナー契約](https://connect.microsoft.com/ConfigurationManagervnext/Survey/Survey.aspx?SurveyID=17806)を**確認して署名**します。 この契約では、Microsoft Intune アプリ パートナーになる前に、会社が同意する必要のある条項について説明しています。 このドキュメントを表示するには、サインインする必要があります。 契約は、Intune アプリ SDK の Microsoft Connect サイト直下または [アンケート] タブの下にあります。 アプリの名前、会社の名前、および Google ストアまたは iTunes ストアにおけるアプリへのディープ リンクも指定してください。

![Microsoft Connect](../media/microsoft-connect.png)

登録電子メール アドレスは、登録プロセスの受信を確認および完了するために使用します。 また、何らかの問題が発生した場合の連絡にも、登録電子メール アドレスを使用します。

**登録プロセスの流れ**: 

フォームを送信すると、正常に受信したことを確認するか、または登録を完了するための追加情報を要求する目的で、Microsoft から登録電子メール アドレスを介して連絡があります。 また、アプリが正常に Microsoft Intune に登録されたり、アプリが Microsoft Intune パートナーのサイトで推奨された場合にも連絡があります。 情報の受信が確認されると、アプリのディープ リンクは、次の月の Intune サービス更新に組み込まれます。 たとえば、7 月に登録情報を完了した場合、アプリのディープ リンクは 8 月中旬にサポートされます。 ストア アプリのディープ リンクを今後変更する場合は、アプリを再登録する必要があります。 また、新しいバージョンの Intune アプリ SDK を使用してアプリを更新する場合には、ご連絡ください。

**注**: 上記のフォームおよび Intune チームとの電子メール通信で収集されたすべての情報は、 [Microsoft のプライバシーに関する声明](https://www.microsoft.com/en-us/privacystatement/default.aspx)に従って処理されます。

## SDK ファイルをダウンロードする

iOS 用および Android 用の Intune アプリ SDK は、Microsoft GitHub アカウントでホストされています。 以下のパブリック リポジトリには、それぞれ iOS 用および Android 用の SDK ファイルが含まれます。

* [iOS 用 Intune アプリ SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [Android 用 Intune アプリ SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

リポジトリの分岐と取得に使用できる GitHub アカウントにサインアップすることをお勧めします。 GitHub を使用すると、製品チームとのやり取り、問題の提出と迅速な応答、リリース ノートの表示、マイクロソフトへのフィードバックの提供が可能です。 GitHub アカウントとリポジトリに関する質問は、msintuneappsdk@microsoft.com に問い合わせてください。

## SDK を使用する MAM に対して iOS または Android のモバイル アプリを有効にする

Intune アプリ SDK を iOS アプリに統合するには、次のものが必要です。 

* 「**[iOS 用 Intune アプリ SDK 開発者ガイド](intune-app-sdk-ios.md)**」: このドキュメントでは、Intune アプリ SDK を使用したモバイル iOS アプリを有効にする方法について、段階的に説明しています。 


Intune アプリ SDK を Android アプリに統合するには、次のものが必要です。

* 「**[Android 用 Intune アプリ SDK 開発者ガイド](intune-app-sdk-android.md)**」: このドキュメントでは、Intune アプリ SDK を使用したモバイル Android アプリを有効にする方法について、段階的に説明しています。 



## アプリの製品利用統計情報を構成する

Microsoft Intune はアプリの利用統計データを収集します。

* **iOS 用 Intune アプリ SDK**: SDK により、既定では、使用状況イベントに関する SDK 製品利用統計情報がログに記録されます。 このデータは、Microsoft Intune に送信されます。

    * アプリから SDK の製品利用統計情報を Microsoft Intune に送信しない場合は、IntuneMAMSettings ディレクトリのプロパティ `MAMTelemetryDisabled` を "YES" に設定して、製品利用統計情報の送信を無効にする必要があります。

* **Android 用 Intune アプリ SDK**: SDK によって製品利用統計情報データがログに記録されることはありません。

## Microsoft Intune での MAM が有効になっているアプリのテスト

iOS または Android アプリを Intune アプリ SDK と統合するために必要な手順を完了した後、すべてのアプリ管理ポリシーが、エンドユーザーと IT 管理者に対して有効化され機能していることを確認する必要があります。 統合されたアプリをテストするには、次の手順を実行します。

<!--TODO-->

* **Microsoft Intune での MAM が有効になっているアプリのテスト**: このドキュメントでは、MAM が有効になっている iOS または Android のアプリを Microsoft Intune でテストする方法について、段階的に説明しています。 このドキュメントは SDK の GitHub リポジトリにあります。

* **Microsoft Intune アカウント**: MAM が有効になっているアプリを Microsoft Intune でテストするには、Microsoft Intune アカウントが必要です。 
    * Intune MAM に対して iOS または Android ストア アプリを有効化している ISV の場合は、登録ステップで説明した Microsoft Intune での登録が完了すると、プロモーション コードを受け取ります。 プロモーション コードを使用すると、Microsoft Intune の 1 年間の拡張使用試用版にサインアップできます。 
    * ストアに出荷されない基幹業務アプリを開発している場合は、組織を介して Microsoft Intune のアクセス権が付与されます。 この場合も、[Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) で、1 か月間の無料試用版にサインアップできます。




<!--HONumber=Sep16_HO4-->


