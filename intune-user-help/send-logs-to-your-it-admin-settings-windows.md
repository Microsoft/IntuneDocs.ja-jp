---
title: 会社のサポートに Windows 10 デバイスのログを送信する | Microsoft Docs
description: Intune に Windows 10 1511 デバイスを登録する
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/09/2019
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
ms.openlocfilehash: 88107a580eb72f647bb7c32d52ed5d3c848cd392
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203316"
---
# <a name="send-logs-to-your-company-support-from-the-settings-app-for-windows-10"></a>会社のサポートに、設定アプリから Windows 10 のログを送信する

設定アプリを使用して、Windows 10 用ポータル サイトのトラブルシューティングを行います。 Windows 10 デバイス上でアプリを使用しているときに問題が発生した場合は、電子メールでサポート チームに問い合わせることができます。 ポータル サイト アプリで発生したイベントとエラーは、お使いのデバイス上の_診断ログ_という特別なドキュメントに保存されています。 これらのログには、エラーに関する追加の分析情報が含まれており、エクスポートすると、サポート チームにとって有益です。

1. **設定**アプリを開くには、**[スタート]** メニュー > **[設定]** に移動します。 検索バーで "*設定*" を検索することもできます。
2. **[アカウント]** > **[職場または学校にアクセスする]** の順に移動します。
3. **[管理ログ ファイルのエクスポート]** を選択します。

   ![[関連設定] の下にエクスポートのオプションが表示された [職場または学校にアクセスする] 画面。](./media/w10-export-logs.png)

4. ログが **C:\Users\Public\Public Documents\MDMDiagnostics** に保存されます。 2 つのファイルが作成されます。1 つはログ自体、もう 1 つは特殊なドキュメントで、管理者は Microsoft Excel などの別のプログラムでログを確認できます。 これらのファイル両方を電子メールに添付し、その電子メールを管理者に送信します。これを複数回行う場合は、単純に、ログが作成された日からファイルを選択します。 

また、[ポータル サイト アプリからのログ](send-logs-to-your-it-admin-cp-windows.md)を送信して、問題が見つかったときに会社のサポートがトラブルシューティングしやすくする必要がある場合もあります。 

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。
