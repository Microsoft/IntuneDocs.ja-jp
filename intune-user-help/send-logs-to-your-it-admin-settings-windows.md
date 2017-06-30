---
title: "IT 管理者に Windows 10 デバイスのログを送信する | Microsoft Docs"
description: "Intune に Windows 10 1511 デバイスを登録する"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 038747fb-5b52-47c4-a2b6-f9218da4cfe1
searchScope:
- User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ed0e84c16ea540c08e97cb55ef8a09cbc7339f6
ms.openlocfilehash: be9976f03bf749222ca372040d4d936e6a8fd26b
ms.contentlocale: ja-jp
ms.lasthandoff: 05/25/2017


---

# <a name="send-logs-to-your-it-admin-from-the-settings-app-for-windows-10"></a>IT 管理者に、設定アプリから Windows 10 のログを送信する

会社で管理している Windows 10 デバイスを使用している間にエラーが発生した場合は、IT 管理者による問題のトラブルシューティングに役立つように、エラー情報を電子メールで送信できます。 この情報は、デバイスの _diagnostic log_ という名前の特殊なドキュメントに保存されています。

1.    **[スタート] メニュー**に移動し、**[設定]** ボタンを選択して、**[Windows の設定]** アプリを開きます。 検索バーで "設定" を検索することもできます。
2.    **[アカウント]** > **[職場または学校にアクセスする]** の順に移動します。
3.    [管理ログ ファイルのエクスポート] を選択します。

  ![[関連設定] の下にエクスポートのオプションが表示された [職場または学校にアクセスする] 画面。](./media/w10-export-logs.png)

4. ログが **C:\Users\Public\Public Documents\MDMDiagnostics** に保存されます。 2 つのファイルが作成されます。1 つはログ自体、もう 1 つは特殊なドキュメントで、管理者は Microsoft Excel などの別のプログラムでログを確認できます。 これらのファイル両方を電子メールに添付し、その電子メールを管理者に送信します。 これを複数回行う場合は、単純に、ログが作成された日からファイルを選択します。 

また、[ポータル サイト アプリからのログ](send-logs-to-your-it-admin-cp-windows.md)を送信して、問題が見つかったときに IT 管理者がトラブルシューティングするのを助ける必要がある場合もあります。 

サポートが必要な場合は、 IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。

