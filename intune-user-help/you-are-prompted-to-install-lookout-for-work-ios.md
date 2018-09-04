---
title: iOS デバイスで Lookout for Work をインストールする必要がある | Microsoft Docs
description: iOS 用の Lookout for Work をインストールする方法について説明します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7adab655-8317-4512-ba7d-beeaa25bbf6c
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.openlocfilehash: 94a6dff4a6dac357fcbdf475ada9894f4bc039bd
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2018
ms.locfileid: "43149300"
---
# <a name="install-lookout-for-work-on-your-ios-device"></a>iOS デバイスで Lookout for Work をインストールする


作業内容にアクセスする前に、会社から潜在的なセキュリティ脅威を検出してデバイスを保護することができる、Lookout for Work アプリをインストールするように求められます。 IT 管理者の設定によって、Lookout for Work で表示されるプロンプトは異なります。


## <a name="what-you-need-to-do"></a>必要事項

1.  次のプロンプトが表示された場合は、**[インストール]** をタップし、デバイスへの Lookout for Work のインストールを許可します。

      ![アプリのインストールを促す画面のスクリーンショット。[キャンセル] ボタンと [インストール] ボタンが表示されています。](/intune-user-help/media/ios-mts-install-app-request-after-1804.png)

2. 次のメッセージが表示されたら **[設定]** をタップし、**[ロケーション サービス]** をオンにし、**[続行]** をタップします。

      ![[設定]、[ロケーション サービス] の順にタップする](./media/ios-lfw-allow-location-services.png)

3. Lookout for Work に必要なアクセス許可を確認し、**[続行]** をタップします。

      ![Lookout for Work に接続している状態になりました](./media/ios-lfw-permissions-lookout-needs.png)

4. Lookout for Work に通知の送信の許可を求めるプロンプトで **[許可]** をタップします。

     ![[設定]、[ロケーション サービス] の順にタップする](./media/ios-lfw-allow-notifications.png)

   * Lookout for Work がインストールを完了し、デバイスでセキュリティ上の脅威が検出されない場合、次の画面が表示されます。

     ![セキュリティ上の脅威はありませんでした](./media/ios-lfw-no-threats-found.png)

   * Lookout for Work によってこのデバイスでセキュリティ上の脅威が見つかった場合は、問題を解決する手順が表示されます。

## <a name="if-the-installation-doesnt-work"></a>インストールが機能しない場合

ユーザーが制御できない技術的な問題によりインストールが失敗する場合があります。 このような場合は、Lookout for Work を[アプリ ストアから手動で](https://itunes.apple.com/app/lookout-for-work/id997193468)インストールしてみてください。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。

