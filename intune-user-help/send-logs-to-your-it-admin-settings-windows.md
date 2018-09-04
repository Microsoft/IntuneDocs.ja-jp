---
title: 会社のサポートに Windows 10 デバイスのログを送信する | Microsoft Docs
description: Intune に Windows 10 1511 デバイスを登録する
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/25/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 038747fb-5b52-47c4-a2b6-f9218da4cfe1
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 1e9b9908fcc48e9137c07f9a5397661d66e5be95
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2018
ms.locfileid: "43146741"
---
# <a name="send-logs-to-your-company-support-from-the-settings-app-for-windows-10"></a>会社のサポートに、設定アプリから Windows 10 のログを送信する

会社で管理している Windows 10 デバイスを使用している間にエラーが発生した場合は、会社のサポートによる問題のトラブルシューティングに役立つように、エラー情報を電子メールで送信できます。 この情報は、デバイスの _diagnostic log_ という名前の特殊なドキュメントに保存されています。

1. **[スタート] メニュー**に移動し、**[設定]** ボタンを選択して、**[Windows の設定]** アプリを開きます。 検索バーで "設定" を検索することもできます。
2. **[アカウント]** > **[職場または学校にアクセスする]** の順に移動します。
3. [管理ログ ファイルのエクスポート] を選択します。

   ![[関連設定] の下にエクスポートのオプションが表示された [職場または学校にアクセスする] 画面。](./media/w10-export-logs.png)

4. ログが **C:\Users\Public\Public Documents\MDMDiagnostics** に保存されます。 2 つのファイルが作成されます。1 つはログ自体、もう 1 つは特殊なドキュメントで、管理者は Microsoft Excel などの別のプログラムでログを確認できます。 これらのファイル両方を電子メールに添付し、その電子メールを管理者に送信します。これを複数回行う場合は、単純に、ログが作成された日からファイルを選択します。 

また、[ポータル サイト アプリからのログ](send-logs-to-your-it-admin-cp-windows.md)を送信して、問題が見つかったときに会社のサポートがトラブルシューティングしやすくする必要がある場合もあります。 

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。
