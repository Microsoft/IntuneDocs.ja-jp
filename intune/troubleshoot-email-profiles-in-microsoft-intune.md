---
title: Microsoft Intune での電子メール プロファイルのトラブルシューティング - Azure | Microsoft Docs
description: 電子メール プロファイルに関する問題と、そのトラブルシューティングと解決方法。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 480b453aa4f08f8d2a2460e26bfdb5f05466df6e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190100"
---
# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Microsoft Intune の電子メール プロファイルに関するトラブルシューティング

一般的な電子メール プロファイルに関する問題と、そのトラブルシューティングと解決方法について説明します。

この情報を使っても問題が解決しない場合は、[Microsoft Intune のサポートを受ける](get-support.md)こともできます。

## <a name="unable-to-send-images-from--email-account"></a>電子メール アカウントから画像を送信できない
Azure クラシック ポータルでの Intune に適用されます。

電子メール アカウントを自動的に構成したユーザーが、自分のデバイスから画像を送信することができません。 このシナリオは、**[サードパーティ アプリケーションからの電子メール送信を許可する]** が有効ではない場合に発生する可能性があります。

### <a name="intune-solution"></a>Intune での解決方法

1. Microsoft Intune 管理コンソールで、**[ポリシー]** ワークロード > **[構成ポリシー]** の順に選択します。

2. 電子メール プロファイルを選択し、**[編集]** を選択します。

3. **[サード パーティ アプリケーションから電子メールを送信できるようにする]** をオンにします。

### <a name="configuration-manager-integrated-with-intune-solution"></a>Windows Intune と統合された Configuration Manager

1. Configuration Manager コンソール > **[資産とコンプライアンス]** の順に開きます。

2. **[概要]** > **[コンプライアンス設定]** > **[会社のリソースへのアクセス]** の順に展開して、**[電子メール プロファイル]** を選択します。

3. 電子メール プロファイルを右クリックし、**[プロパティ]** を開きます。

4. **[同期設定]** タブで、**[サード パーティ アプリケーションから電子メールを送信できるようにする]** をオンにします。

## <a name="device-already-has-an-email-profile-installed"></a>デバイスに電子メール プロファイルが既にインストールされている

Intune プロファイルのプロビジョニング前にユーザーが電子メール プロファイルをインストールしてある場合、Intune 電子メール プロファイルの展開結果はデバイスのプラットフォームによって変わります。

- **iOS**: Intune は、ホスト名と電子メール アドレスに基づいて既存の重複する電子メール プロファイルを検出します。 ユーザーによって作成された重複する電子メール プロファイルは、Intune の管理者が作成したプロファイルの展開をブロックします。 これは一般的な問題です。iOS ユーザーは通常、電子メール プロファイルを作成し、それから登録するためです。 ポータル サイトはユーザーに、手動で構成された電子メール プロファイルが原因で準拠していないこと知らせ、そのプロファイルを削除するようユーザーに求めます。 Intune プロファイルを展開できるように、ユーザーは電子メール プロファイルを削除する必要があります。 この問題を回避するには、プロファイルを登録し、展開を Intune に許可するようにユーザーに指示します。 次に、ユーザーが作成した電子メール プロファイルをインストールします。

- **Windows**: Intune は、ホスト名と電子メール アドレスに基づいて既存の重複する電子メール プロファイルを検出します。 Intune は、ユーザーによって作成された既存の電子メール プロファイルを上書きします。

- **Samsung KNOX Standard**: Intune は、電子メール アドレスに基づいて重複する電子メール アカウントを識別し、Intune プロファイルで上書きします。 ユーザーがそのアカウントを構成した場合、Intune プロファイルによって再び上書きされます。 このため、アカウントの構成を上書きされたユーザーが混乱する可能性があります。

Samsung KNOX では、プロファイルを識別するためにホスト名が使用されません。 異なるホスト上の同じ電子メール アドレスに展開する複数の電子メール プロファイルは、相互に上書きされるため、作成しないことをお勧めします。

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>KNOX Standard デバイスのエラー 0x87D1FDE8
**問題**: さまざまな Android デバイスで Samsung KNOX Standard の Exchange Active Sync 電子メール プロファイルを作成して展開すると、デバイスの [プロパティ] > [ポリシー] タブに **0x87D1FDE8** または "**修復できませんでした**" というエラーが報告される。

Samsung KNOX の EAS プロファイルおよびソース ポリシーの構成を確認します。 Samsung Note 同期オプションはサポートされなくなったため、このオプションをプロファイルで選択することはできません。 デバイスには、ポリシーを処理するための十分な時間を最大 24 時間設定してください。

## <a name="next-steps"></a>次の手順
この情報を使っても問題が解決しない場合は、[Microsoft Intune のサポートを受ける](get-support.md)こともできます。