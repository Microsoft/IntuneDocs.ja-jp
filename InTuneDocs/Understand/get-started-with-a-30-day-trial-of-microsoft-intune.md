---
title: "Intune の評価ガイド | Microsoft Intune"
description: "Intune の無料の 30 日間評価版を設定する方法の概要と前提条件"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 08/09/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: 559917b5b3c12534a5aa5d5eb5247d36e4ac1728


---

# <a name="intune-evaluation-guide"></a>Intune の評価ガイド
モバイル デバイスとコンピューターを管理する Intune の無料の 30 日間評価版を迅速かつ簡単に設定できます。 評価版ではいくつかの簡単な手順を行うだけで、最大 100 のユーザーとデバイスの追加、グループの設定、コンプライアンス ポリシーの構成、モバイル デバイスとコンピューターの登録と管理を行うことができます。

このトピックでは、Intune の特長と機能を評価できるよう、Intune の評価版の稼働方法とサービスの概要の理解に関する基本的な内容を学習します。

次の 5 分間のデモ ビデオを視聴すると、Microsoft Intune の無料評価版の使用開始とデバイスの管理がきわめて簡単であることがわかります。 ビデオの最初の部分で "使用中止となった" ポータルについて説明します。別のポータルを使用することになりますが、手順は基本的に同じです。 ポータルに関する詳細は[ここ](https://docs.microsoft.com/intune/deploy-use/account-portal-merged-with-Office-365)で確認できます。

<iframe width="675" height="480" src="https://www.youtube.com/embed/ltcZvm4VOFU" frameborder="0" allowfullscreen></iframe>

## <a name="before-you-begin"></a>始める前に
Intune の使用を開始する前に、以下のものが必要となります。

-   Silverlight 対応 Web ブラウザーを備えたデバイス。これは、Intune ユーザーのアカウントを作成するための Web サイト (**Office 365 管理センター**) や、デバイス、グループ、ポリシーの管理を行う Web サイト (**Intune 管理コンソール**) にアクセスする際に使用します。

-   Web ブラウザーを備えた 2 台目のデバイス。こちらは、Intune ユーザーがポータル サイトをどのように使用してデバイスを登録および管理するかを確認するためのテストに使用します。 このほか、ユーザーがアプリを検索およびインストールするときの状況や、管理者に支援を依頼する局面を確認するためのテストにも使用します。 2 台目のデバイスがない場合は、Intune の管理に、使用する同じブラウザーの "プライバシー モード" 設定を使ってもかまいません (例: Internet Explorer の場合、**[ツール]** &gt; **[InPrivate ブラウズ]** をクリックします)。

-   既存の Microsoft Online Services アカウントがある場合、そのアカウントの管理者の資格情報が必要です。 そのようなアカウントが存在しない場合、またはこの Intune テナントを評価目的でのみ使用する場合、テナント管理者の資格情報は不要です。

-   iOS または Windows Phone 8.1 デバイスを Intune 評価版で管理する場合、証明書 (またはキー) とそれを取得するためのアカウントが必要になります (以下の表を参照してください)。 Android デバイスの場合、特別な証明書は必要ありません。

    |プラットフォーム|証明書の要件|説明|
    |------------|----------------------------|--------------------|
    |Windows Phone 8。1 |ポータル サイト アプリをストアからインストールする Windows Phone 8.1 のユーザーについては証明書は不要です。 |この要件は、管理下にあるユーザーが、ポータル サイト アプリを Windows Phone 8.1 以降のデバイスでストアから取得することを前提としています。 |
    |Windows 10、Windows RT 8.1、Windows 8.1 デバイス|Windows RT デバイスまたは Windows デバイスを登録するうえでの証明書の要件はありません。|[Microsoft Intune を使用して Windows PC クライアントをインストールする](/Intune/Deploy-Use/install-the-windows-pc-client-with-microsoft-intune)。|
    |iOS 7.1 以降|Apple Push Notification サービス証明書を取得する。|「[Microsoft Intune を使用した iOS および Mac の管理のセットアップ](/Intune/Deploy-Use/set-up-ios-and-mac-management-with-microsoft-intune)」で説明しているように、Apple に Apple Push Notification サービス証明書を要求する必要があります。|

## <a name="steps-to-complete-a-30day-evaluation-of-intune"></a>Intune の 30 日間評価版の完了手順
- [手順 1: 30 日間評価版にサインインまたはサインアップします](get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)。 Intune にサインアップまたはサインインする前に、既存のアカウントを使用してサインインするか、Microsoft Intune の 30 日間評価版にのみ使用する一時的なアカウントを作成するかを検討する必要があります。
- [手順 2: ユーザーを追加します](get-started-with-a-30-day-trial-of-microsoft-intune-step-2.md)。 アカウントを設定したので、個別のユーザー アカウントを Intune に追加するか、一括でユーザーを追加します (このセクションの手順を参照してください)。 操作を開始する前に、Intune が管理者アカウントを処理する方法について理解することが重要です。
- [手順 3: ユーザーとデバイスを編成するグループを作成します](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)。 Intune の [グループ] を使用すると、デバイスとユーザーを柔軟に管理できます。 グループは、組織ごとのニーズ (地理的位置、部門、ハードウェアの特性など) に合わせて設定できます。一連のユーザーに対するポリシーの設定から、一連のデバイスに対するアプリケーションの展開まで、さまざまな管理タスクをそれらのグループを使って一度に実行することができます。
- [手順 4: ポリシーを作成してアプリを発行します](get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)。 モバイル デバイスのセキュリティ設定を制御したり、コンピューターの Windows ファイアウォールや Endpoint Protection の設定を管理したり、アプリケーションを展開したりする作業は、Intune のポリシー設定を使用して効率的に行うことができます。
- [手順 5: モバイル デバイスを登録してアプリをインストールします](get-started-with-a-30-day-trial-of-microsoft-intune-step-5.md)。 Intune を使用してモバイル デバイス管理をセットアップするには、モバイル デバイス管理機関を設定し、特定のデバイス プラットフォームの管理を有効にして、ポータル サイト アプリを使ってデバイスを登録する必要があります。 その後、発行した Microsoft Skype アプリケーションを展開できます。
- [手順 6: その他のオプションと機能](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)。 ビジネス上のニーズに応じて、アラート、レポートなど、その他の Intune 機能を使用する方法を選択します。
- [手順 7: 次のステップ](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md)。 Intune の有料サブスクリプションに移行し、Intune の "FastTrack センターの特典" を活用する準備をします。


### <a name="next-steps"></a>次のステップ
これで 30 日間評価版を使用する準備が整いました。

>[!div class="step-by-step"]
[**Intune にサインアップ** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)

### <a name="see-also"></a>関連項目
[Intune のクイック スタート ガイド](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune)



<!--HONumber=Nov16_HO1-->


