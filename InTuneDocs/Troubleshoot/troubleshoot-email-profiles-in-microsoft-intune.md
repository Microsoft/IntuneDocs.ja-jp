---
title: "電子メール プロファイルに関するトラブルシューティング | Microsoft Docs"
description: "電子メール プロファイルに関する問題と、そのトラブルシューティングと解決方法。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: 017a7912cb991f00916373acc18f4ab2b97ce8ed


---

# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Microsoft Intune の電子メール プロファイルに関するトラブルシューティング

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

ここでは、電子メール プロファイルに関する問題と、そのトラブルシューティングと解決方法について説明します。

この情報で問題が解決しない場合、さらに役立つ方法を探すには、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」を参照してください。


## <a name="unable-to-send-images-from--email-account"></a>電子メール アカウントから画像を送信できない
電子メール アカウントを自動的に構成したユーザーが、自分のデバイスから画像を送信することができません。
**[サード パーティ アプリケーションから電子メールを送信できるようにする]** がオフになっている場合に、この問題が発生します。

### <a name="intune-solution"></a>Intune での解決方法

1.  Microsoft Intune 管理コンソールで、**[ポリシー]** ワークロード &gt;**[構成ポリシー]** の順に選択します。

2.  電子メール プロファイルを選択し、**[編集]** を選択します。

3.  **[サード パーティ アプリケーションから電子メールを送信できるようにする]** をオンにします。

### <a name="configuration-manager-integrated-with-intune-solution"></a>Windows Intune と統合された Configuration Manager

1.  Configuration Manager コンソール &gt;**[資産とコンプライアンス]** の順に開きます。

2.  **[概要]**  -&gt;** [コンプライアンス設定]**  -&gt;** [会社のリソースへのアクセス]** の順に展開して、**[電子メール プロファイル]** を選択します。

3.  電子メール プロファイルを右クリックし、**[プロパティ]** を開きます。

4.  **[同期設定]** タブで、**[サード パーティ アプリケーションから電子メールを送信できるようにする]** をオンにします。


## <a name="device-already-has-an-email-profile-installed"></a>デバイスに電子メール プロファイルが既にインストールされている

Intune によるプロファイルのプロビジョニングの前にユーザーが電子メール プロファイルをインストールしてある場合、Intune による電子メール プロファイルの展開の結果はデバイスのプラットフォームに依存します。

-**iOS**: Intune は、ホスト名と電子メール アドレスに基づいて既存の重複する電子メール プロファイルを検出します。 ユーザーによって作成された重複する電子メール プロファイルは、Intune の管理者が作成したプロファイルの展開をブロックします。 これは一般的な問題です。iOS ユーザーは通常、電子メール プロファイルを作成し、それから登録するためです。 ポータル サイトは、手動で設定した電子メール プロファイルに起因してポリシーに準拠していないことをユーザーに通知し、そのプロファイルを取り除くようにユーザーに要求します。Intune プロファイルを展開できるように、ユーザーは電子メール プロファイルを取り除く必要があります。 この問題を防ぐには、電子メール プロファイルをインストールする前に登録し、Intune によるプロファイルの展開を許可するようにユーザーに指示します。

-**Windows**: Intune は、ホスト名と電子メール アドレスに基づいて既存の重複する電子メール プロファイルを検出します。 Intune は、ユーザーによって作成された既存の電子メール プロファイルを上書きします。

-**Samsung KNOX Standard**: Intune は、電子メール アドレスに基づいて重複する電子メール アカウントを識別し、Intune プロファイルで上書きします。 ユーザーがそのアカウントを構成した場合、Intune プロファイルによって再び上書きされます。 このため、アカウントの構成を上書きされたユーザーが混乱する可能性があることに注意してください。

Samsung KNOX はプロファイルを識別するためにホスト名を使用しないため、複数の電子メール プロファイルを作成して異なるホスト上の同じ電子メール アドレスに展開することはお勧めしません。プロファイルが相互に上書きされます。

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>KNOX Standard デバイスのエラー 0x87D1FDE8
**問題**: さまざまな Android デバイスで Samsung KNOX Standard の Exchange Active Sync 電子メール プロファイルを作成して展開すると、デバイスの [プロパティ] &gt; [ポリシー] タブに **0x87D1FDE8** または [**修復できませんでした**] というエラーが報告される。

Samsung KNOX の EAS プロファイルおよびソース ポリシーの構成を確認します。 Samsung Note 同期オプションはサポートされなくなったため、このオプションをプロファイルで選択することはできません。 デバイスには、ポリシーを処理するための十分な時間を最大 24 時間設定してください。

## <a name="next-steps"></a>次のステップ
このトラブルシューティング情報を使っても問題が解決しない場合は、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」の説明に従って Microsoft サポートにお問い合わせください。



<!--HONumber=Dec16_HO5-->


