---
title: "Intune のクイック スタート ガイド |Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed26d65b98a0ae1bbc4fbac682fb53fddd50b4e5
ms.openlocfilehash: ca0ca74357b59d9cc6fbf4ec7eb237dff972c411


---


# Intune のクイック スタート ガイド
このクイック スタート ガイドでは、Microsoft Intune の有料サブスクリプションをセットアップして、組織で使用しているモバイル デバイスと Windows PC の管理を迅速かつ簡単に開始する手順について説明します。 各手順に順番に従っても、特定の環境やビジネス ニーズに適用できない手順をスキップして先に進んでもかまいません。

>[!NOTE]
>この記事では、スタンドアロン サービスとしての Intune のセットアップについて説明します。 また、現在、Microsoft System Center Configuration Manager を使用して、コンピューターとサーバーを管理している場合は、ハイブリッド MDM 展開で Intune と Configuration Manager を接続することで、[モバイル デバイスを管理できるように Configuration Manager を拡張](https://technet.microsoft.com/library/jj884158.aspx)して、モバイル デバイスも管理することができます。

このクイック スタート ガイドの手順には、「[Intune の評価ガイド](/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)」に記載されいるのと同じ手順がたくさん含まれています。 ただし、評価した後で、モバイル デバイスの管理を開始する準備ができたら、いくつかの追加要件に対応する必要があります。 追加要件は、現在のネットワーク インフラストラクチャやビジネス要件によって異なります。次に例を示します。

-   オンプレミスの Active Directory アカウントと Intune および Azure Active Directory との同期化

-   ドメイン レジストラーでのパブリック ドメインと DNS サービス レコードの更新

-   本番環境での用途を目的とした Intune のカスタマイズ

>[!TIP]
>対象となるプランで Microsoft Intune のライセンスを 150 個以上ご購入いただいた場合に、"FastTrack センター特典" をご利用いただけます。これは、Intune 向けに環境を整えるために Microsoft スペシャリストの支援を受けることができるサービスです。 詳しくは、「[Microsoft Intune のサービス特典の説明](https://technet.microsoft.com/library/mt228265.aspx)」をご覧ください。


## 始める前に
有料サブスクリプションの利用を開始し、Intune を展開して、既存のネットワーク インフラストラクチャに変更を加える準備が整ってから、このガイドを利用してください。 たとえば、単純に内部/外部 DNS レコードを追加したり更新したりすることから、既存の Active Directory ユーザー アカウントを Azure Active Directory に同期したりすることまで、さまざまな変更が考えられます。 Intune の各種モバイル デバイス管理機能を利用するときは、それが何であれ、既存のネットワーク コンポーネントやサービスとの相性について慎重に検討する必要があります。 具体的には、次の点を確認します。

-   **ユーザーの ID 管理**: 中規模から大規模の多くの組織が Intune でユーザーの ID を管理する場合、最適かつ最も利便性が高いのは、Azure Active Directory を介して既存のディレクトリ サービスを Intune に接続する方法です。 特に、Office 365 や Exchange Online など、Intune 以外の Microsoft クラウド サービスを既にご利用のお客様には、この方法をお勧めします。 [Microsoft Azure Active Directory Connect](https://www.microsoft.com/download/details.aspx?id=47594) を使用して既存のユーザー アカウントを同期化すると、短時間で簡単に、オンプレミスの Active Directory を Azure Active Directory に接続し、シングル サインオンのユーザー認証を構成することができます。

-   **DNS への影響**: Intune に最初にサインアップしたときに取得した既定の onmicrosoft.com ドメインではなく、独自のドメイン名を使用する場合は、パブリック DNS レコードの更新が必要になります。 組織で使用しているすべてのデバイスを管理するには、モバイル デバイスが Intune サービスを検出でき、サブスクリプションの管理サービスが正常に機能するように、DNS レコードを更新する必要があります。

## 必要なもの
確認点は以上です。 Intune の有料サブスクリプションの利用を開始する場合、以下のものが必要となります。

### Silverlight 対応 Web ブラウザーがインストールされているデバイス
これは、デバイス、アプリ、およびポリシーを管理する Intune 管理コンソールにアクセスするために必要です。 また、モバイル デバイスからポータル サイト アプリにアクセスせずに、Web ベースのポータル サイトにアクセスする場合にも、Web ブラウザーが必要です。 簡略化するために、Intune の管理に使用するのと同じブラウザーの "プライバシー モード" 設定を使用できます (例: Internet Explorer の場合、**[ツール]** &gt; **[InPrivate ブラウズ]** の順にクリックします)。

>[!TIP]
>この要件により、Intune 管理コンソールにアクセスする場合に、Microsoft Edge ブラウザーはサポートされません。


### モバイル デバイスの証明書
iOS または Windows Phone デバイスを Intune で管理する場合、証明書とそれを取得するためのアカウントが必要になります。 Android デバイスを管理する場合、特別な証明書は必要ありません。

- ポータル サイト アプリをストアからインストールする **Windows Phone 8.1** のユーザーについては証明書は不要です。 ただし、**Windows Phone 8.0** の場合、または Intune を使用してポータル サイト アプリを Windows Phone 8.1 デバイスに展開する場合、[Symantec のコード署名証明書](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)が必要となります。

>[!NOTE]
>このクイック ガイドは、管理下にあるユーザーが、ポータル サイト アプリを Windows Phone 8.1 以降のデバイスでストアから取得することを前提としています。 Windows Phone 8.0 のサポートについては、「[Microsoft Intune を使用して Windows Phone 8.0 の管理をセットアップする](/Intune/deploy-use/set-up-windows-phone-8.0-management-with-microsoft-intune)」をご覧ください。

- **Windows PC** または **Windows RT デバイス**については、Windows PC をデバイスとして登録する場合や、[Microsoft Intune の Windows PC クライアントをインストールする](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune)場合、証明書は必要ありません。

- **iOS** または **Mac OS X** デバイスについては、「[Microsoft Intune を使用して iOS および Mac の管理をセットアップする](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)」の手順 3. で説明しているように、Apple に Apple Push Notification サービス証明書を要求する必要があります。

### 次の手順
Intune のクイック スタート ガイドを使用する準備が整いました。

>[!div class="step-by-step"]
[**Intune にサインインする** &rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)



<!--HONumber=Jun16_HO4-->


