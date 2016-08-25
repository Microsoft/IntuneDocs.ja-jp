---
title: "Microsoft Intune アプリ SDK を使ってみる | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b7f62c5ee18d8f69fa174f09a1c46b6925c7517c
ms.openlocfilehash: a042f0c6206e9aaf4ec0eb012a70930aa95ecc47


---

# Microsoft Intune アプリ SDK を使ってみる

この入門ガイドを使用すると、Microsoft Intune でモバイル アプリケーション管理用のモバイル アプリをすぐに有効にできます。 [Intune アプリ SDK の概要](intune-app-sdk.md)に列挙されている Intune アプリ SDK の利点を最初に理解しておくと、役に立つ場合があります。

このガイドは、Microsoft Intune を使用したアプリケーションでモバイル アプリ管理を有効にするために必要な主要な手順について、段階的に説明します。 Intune アプリ SDK は、プラットフォーム間で類似するシナリオをサポートしており、プラットフォーム全体にわたって一貫した操作性を IT 管理者に提供することを目的としています。 ただし、プラットフォームの制限事項により、特定機能のサポートについてわずかな相違点があります。

# 概要

## Microsoft Connect の登録

Intune アプリ SDK には、現在 Microsoft Connect 経由でアクセスでき、その際にはサインアップが必要です。 これを行うには、会社の電子メールを使用して [Microsoft アカウント](https://connect.microsoft.com/ConfigurationManagervnext/InvitationUse.aspx?ProgramID=8967&InvitationID=8967-YJYJ-8G6X)に登録します。

登録は、Intune チームが要求を確認するまで、保留中の状態になります。 通常、2 から 3 営業日以内に応答があります。 承認されると、該当するプラットフォーム用の Intune アプリ SDK および関連ガイドすべてをダウンロードするためのリンクを含む、電子メール通知を受け取ります。 これらのガイドには、MSDN サイトからアクセスすることもできます。

## Microsoft Intune でのストア アプリの登録

**有効にするアプリが社内向けであり、Apple や Google のアプリ ストアで入手できるようにしない場合**: アプリを登録する必要はありません。 このような内部的なアプリの場合、IT 管理者が、Microsoft Intune コンソールに展開対象のアプリを直接ロードします。アプリが SDK を使用して構築されていることが Intune によって検出されると、IT 管理者に対して、MAM ポリシーを適用するオプションが提示されます。 「[SDK を使用する MAM に対して iOS または Android のモバイル アプリを有効にする](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk)」というセクションにスキップすることができます。

**Apple または Google のいずれかのアプリ ストアで顧客が入手できるようにするアプリを開発中の ISV の場合**: 最初に Microsoft Intune でアプリを登録して、登録の条項に同意する必要があります。 この時点で、アプリのディープ リンクを指定できます。 その後、IT 管理者は、アプリに Intune MAM ポリシーを適用できます。 登録が完了し、Microsoft Intune チームによって確認されるまで、アプリのディープ リンクには、管理コンソールで MAM ポリシーを適用するオプションはありません。 Microsoft では、このアプリで Microsoft Intune MAM ポリシーがサポートされていることが顧客にわかるように、アプリを登録する Microsoft Intune パートナーの Web サイトも管理します。

登録プロセスを開始するには、[Microsoft Intune パートナー契約](https://connect.microsoft.com/ConfigurationManagervnext/Survey/Survey.aspx?SurveyID=17806)を**確認して署名**します。 この契約では、Microsoft Intune アプリ パートナーになる前に、会社が同意する必要のある条項について説明しています。 このドキュメントを表示するには、サインインする必要があります。 契約は、Intune アプリ SDK の Microsoft Connect サイト直下または [アンケート] タブの下にあります。 アプリの名前、会社の名前、および Google ストアまたは iTunes ストアにおけるアプリへのディープ リンクも指定してください。

![Microsoft Connect](../media/microsoft-connect.png)

登録電子メール アドレスは、登録プロセスの受信を確認および完了するために使用します。 また、何らかの問題が発生した場合の連絡にも、登録電子メール アドレスを使用します。

**登録プロセスの流れ**: フォームを送信すると、正常に受信したことを確認するか、または登録を完了するための追加情報を要求する目的で、Microsoft から登録電子メール アドレスを介して連絡があります。 また、アプリが正常に Microsoft Intune に登録されたり、アプリが Microsoft Intune パートナーのサイトで推奨された場合にも連絡があります。 情報の受信が確認されると、アプリのディープ リンクは、次の月の Intune サービス更新に組み込まれます。 たとえば、7 月に登録情報を完了した場合、アプリのディープ リンクは 8 月中旬にサポートされます。 ストア アプリのディープ リンクを今後変更する場合は、アプリを再登録する必要があります。 また、新しいバージョンの Intune アプリ SDK を使用してアプリを更新する場合には、ご連絡ください。

**注**: 上記のフォームおよび Intune チームとの電子メール通信で収集されたすべての情報は、 [Microsoft のプライバシーに関する声明](https://www.microsoft.com/en-us/privacystatement/default.aspx)に従って処理されます。

## SDK を使用する MAM に対して iOS または Android のモバイル アプリを有効にする

iOS モバイル アプリを有効にするには、次のものが必要です。

1. 「**[iOS 用 Intune アプリ SDK 開発者ガイド](intune-app-sdk-ios.md)**」: このドキュメントでは、Intune アプリ SDK を使用したモバイル iOS アプリを有効にする方法について、段階的に説明しています。 このドキュメントは、Intune アプリ SDK パッケージの一部としてダウンロードしたドキュメント フォルダー内にあります。
2. **iOS 用 Intune アプリ SDK**: Microsoft Intune からダウンロードした Intune アプリ SDK パッケージの一部として、署名付きフォルダー "iOS 用 Intune アプリ SDK" があります。 このフォルダーには、iOS 用 Intune アプリ SDK のすべてのコンテンツが含まれています。

Intune アプリ SDK を使用した Android モバイル アプリを有効にするには、次のものが必要です。

1. 「**[Android 用 Intune アプリ SDK 開発者ガイド](intune-app-sdk-android.md)**」: このドキュメントでは、Intune アプリ SDK を使用したモバイル Android アプリを有効にする方法について、段階的に説明しています。 このドキュメントは、Intune アプリ SDK パッケージの一部としてダウンロードしたドキュメント フォルダー内にあります。
2. **Android 用 Intune アプリ SDK**: Microsoft Intune からダウンロードした Intune アプリ SDK パッケージの一部として、署名付きフォルダー "Android 用 Intune アプリ SDK" があります。 このフォルダーには、Android 用 Intune アプリ SDK のすべてのコンテンツが含まれています。

## アプリの製品利用統計情報をオフにする

**iOS 用 Intune アプリ SDK**: SDK により、既定では、使用状況イベントに関する SDK 製品利用統計情報がログに記録されます。 このデータは、Microsoft Intune に送信されます。

アプリケーションから SDK の製品利用統計情報を Microsoft Intune に送信しない場合は、 **IntuneMAMSettings** のプロパティ `MAMTelemetryDisabled` を [はい] に設定して、SDK 製品利用統計情報の送信を `IntuneMAMSettings`。

**Android 用 Intune アプリ SDK**: SDK により、SDK 製品利用統計情報がログに記録されることはありません。

## Microsoft Intune での MAM が有効になっているアプリのテスト

iOS または Android の Intune アプリ SDK の有効化 (Intune アプリ SDK の統合) に必要な手順を完了した後、すべてのアプリ管理ポリシーが、エンドユーザーと IT 管理者に対して有効化され機能していることを確認する必要があります。 有効化されたアプリをテストするには、次の手順を実行します。

1. **Microsoft Intune での MAM が有効になっているアプリのテスト**: このドキュメントでは、MAM が有効になっている iOS または Android のアプリを Microsoft Intune でテストする方法について、段階的に説明しています。 このドキュメントは、Intune アプリ SDK パッケージの一部としてダウンロードしたドキュメント フォルダー内にあります。
2. **Microsoft Intune アカウント**: MAM が有効になっているアプリを Microsoft Intune でテストするには、Microsoft Intune アカウントが必要です。 MAM に対して iOS または Android ストア アプリを有効化している ISV の場合は、登録ステップで説明した Microsoft Intune での登録が完了すると、プロモーション コードを受け取ります。 プロモーション コードを使用すると、Microsoft Intune の 1 年間の拡張使用試用版にサインアップできます。 ストアに出荷されない基幹業務アプリ を開発している場合は、組織を介して Microsoft Intune のアクセス権が付与されます。 この場合も、[Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) で、1 か月間の無料試用版にサインアップできます。




<!--HONumber=Jun16_HO4-->


