---
title: "iOS ログを Microsoft 開発者に送信する | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 733a590e-836f-4941-bfd9-6ae53ba25e06
searchScope:
- User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 1ba0dab35e0da6cfe744314a4935221a206fcea7
ms.openlocfilehash: 4abb070d6cf4f8200bdf1b9380ade7db81535622
ms.lasthandoff: 03/13/2017


---

# <a name="send-logs-to-the-company-portal-developers-for-ios-devices"></a>ログを iOS デバイス向けポータル サイトの開発者に送信する | Microsoft Docs

ポータル サイト アプリが、予期せず終了することがあります。 これは、マイクロソフトがお客様の操作性を向上させ、このような問題が今後発生しないようにするために、アプリの開発者がお客様からのご意見を待ち望んでいる問題です。 この情報は、デバイスの _diagnostic log_ という名前の特殊なドキュメントに保存されています。

この問題が発生した場合、ポータル サイト チームは根本原因を探し、診断するための情報が必要になります。 ここで実行する必要がある操作は、次のとおりです。

1.    問題の再現を試みてください。 できなくても問題ありませんが、再現できると次の手順が簡単になります。
2.    __[設定]__  >  __[プライバシー]__  >  __[Diagnostics & Usage (診断情報と使用状況)]__  >  __[Diagnostics & Usage Data (診断情報と使用状況データ)]__ に移動します。 これは、クラッシュから一般的な使用パターンまで、発生したアプリ アクティビティの一覧です。個人情報は含まれていません。 この一覧は、最も新しいものから順番に表示されます。 この問題を再現できなかった場合、これが、このページのアプリ アクティビティの一覧に表示される最初の項目になります。 問題を再現できなかった場合、"ポータル サイト" で始まる最初の項目が見つかるまで下へスクロールし、見つかったらタップして開きます。
3.    キーを押したまま、レポート内のすべてのテキストが選択されるまで、小さい青いドットを上下にドラッグします。 ポップアップ メニューの __[コピー]__ をタップします。
4.    電子メール アプリを開き、電子メールの本文にその内容を貼り付けます。 電子メールを <a href="mailto:IntuneCPiOSfeedback@microsoft.com?subject=My Company Portal App Closed Unexpectedly&body=Press and hold, then paste your copied Company Portal app logs here.">IntuneCPiOSfeedback@microsoft.com</a> に送信します。

サポートが必要な場合は、 IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。

