---
title: "Intune のクイック スタート ガイド |Microsoft Intune"
description: "Intune サブスクリプションの使用を開始するための要件と前提条件"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0c1e08cc49d75303f6793894e3c8a040f6e7a8b1
ms.openlocfilehash: aecd5f76e234835c38bf47d8de7e13034d683998


---


# Intune のクイック スタート ガイド
このクイック スタート ガイドでは、Microsoft Intune の有料サブスクリプションをセットアップして、組織で使用しているモバイル デバイスと Windows PC を迅速かつ簡単に管理する手順について説明します。 各手順に順番に従っても、特定の環境やビジネス ニーズに適用できない手順をスキップして先に進んでもかまいません。

>[!NOTE]
>この記事では、スタンドアロン サービスとしての Intune のセットアップについて説明します。 または、現在コンピューターとサーバーの管理に Microsoft System Center Configuration Manager を使っている場合は、[Configuration Manager を拡張してモバイル デバイスを管理する](https://technet.microsoft.com/library/jj884158.aspx)ことができます。 そのためには、Intune と Configuration Manager をモバイル デバイス管理 (MDM) のハイブリッド デプロイメントで接続します。

このクイック スタート ガイドには、「[Intune の評価ガイド](/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)」に記載されいるのと同じ手順がたくさん含まれています。 ただし、評価した後で、モバイル デバイスの管理を開始する準備ができたら、いくつかの追加要件に対応する必要があります。

-   オンプレミスの Active Directory アカウントと Intune および Azure Active Directory を同期します。

-   ドメイン レジストラーでパブリック ドメインと DNS サービス レコードを更新します。

-   本番環境での用途を目的として Intune 機能をカスタマイズします。

>[!TIP]
>対象となるプランで Microsoft Intune のライセンスを 150 個以上ご購入いただいた場合に、*FastTrack センター特典*をご利用いただけます。これは、Intune 向けに環境を整えるために Microsoft スペシャリストの支援を受けることができるサービスです。 詳しくは、「[Microsoft Intune のサービス特典の説明](https://technet.microsoft.com/library/mt228265.aspx)」をご覧ください。


## 始める前に
有料サブスクリプションの利用を開始し、Intune を展開して、既存のネットワーク インフラストラクチャに変更を加える準備が整ってから、このガイドを利用してください。 たとえば、単純に内部/外部 DNS レコードを追加したり更新したりすることから、既存の Active Directory ユーザー アカウントを Azure Active Directory に同期したりすることまで、さまざまな変更が考えられます。 Intune の各種モバイル デバイス管理機能を利用するときは、それが何であれ、既存のネットワーク コンポーネントやサービスとの相性について慎重に検討する必要があります。 具体的には、次の点を確認します。

-   **ユーザーの ID 管理**: 中規模から大規模の多くの組織が Intune でユーザーの ID を管理する場合、最適かつ最も利便性が高いのは、Azure Active Directory を介して既存のディレクトリ サービスを Intune に接続する方法です。 特に、Office 365 や Exchange Online など、Intune 以外の Microsoft クラウド サービスを既にご利用のお客様には、この方法をお勧めします。 [Microsoft Azure Active Directory Connect](https://www.microsoft.com/download/details.aspx?id=47594) を使用して既存のユーザー アカウントを同期化すると、短時間で簡単に、オンプレミスの Active Directory を Azure Active Directory に接続し、シングル サインオンのユーザー認証エクスペリエンスを構成することができます。

-   **DNS への影響**: Intune に最初にサインアップしたときに取得した既定の onmicrosoft.com ドメインではなく、独自のドメイン名を使用する場合は、パブリック DNS レコードの更新が必要になります。 組織で使用しているすべてのデバイスを管理するには、モバイル デバイスが Intune サービスを検出でき、サブスクリプションの管理サービスが正常に機能するように、DNS レコードを更新する必要があります。

## 必要なもの
確認点は以上です。 Intune の有料サブスクリプションの利用を開始する場合、以下のものが必要です。

### Silverlight 対応 Web ブラウザーがインストールされているデバイス
これは、デバイス、アプリ、およびポリシーを管理する Intune 管理コンソールにアクセスするために必要です。 また、モバイル デバイスから会社のポータル アプリにアクセスせずに、Web ベースの Intune 会社のポータルにアクセスする場合にも、Web ブラウザーが必要です。 簡略化するために、Intune の管理に使用するのと同じブラウザーの "プライバシー モード" 設定を使用できます (例: Internet Explorer の場合、**[ツール]** &gt; **[InPrivate ブラウズ]** の順にクリックします)。

>[!TIP]
>この要件により、Intune 管理コンソールにアクセスする場合に、Microsoft Edge ブラウザーはサポートされません。


### モバイル デバイスの証明書
iOS または Windows Phone デバイスを Intune で管理している場合、証明書とそれを取得するためのアカウントが必要になります。 Android デバイスを管理する場合、特別な証明書は必要ありません。

- 会社のポータル アプリをストアからインストールする **Windows Phone 8.1** のユーザーについては証明書は不要です。 ただし、**Windows Phone 8.0** の場合、または Intune を使用して会社のポータル アプリを Windows Phone 8.1 デバイスに展開する場合、[Symantec のコード署名証明書](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)が必要となります。

>[!NOTE]
>このクイック スタート ガイドは、管理下にあるユーザーが、会社のポータル アプリを Windows Phone 8.1 以降のデバイスでストアから取得することを前提としています。 Windows Phone 8.0 のサポートについては、「[Microsoft Intune を使用して Windows Phone 8.0 の管理をセットアップする](/Intune/deploy-use/set-up-windows-phone-8.0-management-with-microsoft-intune)」をご覧ください。

- **Windows PC** または **Windows RT デバイス**については、Windows PC をデバイスとして登録する場合や、[Microsoft Intune の Windows PC クライアントをインストールする](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune)場合、証明書は必要ありません。

- **iOS** または **Mac OS X** デバイスについては、「[Microsoft Intune を使用して iOS および Mac の管理をセットアップする](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)」の手順 3 で説明しているように、Apple に Apple Push Notification サービス証明書を要求する必要があります。

## 次のステップ
Intune のクイック スタート ガイドを使用する準備が整いました。

>[!div class="step-by-step"]
[**Intune にサインインする** &rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)



<!--HONumber=Aug16_HO5-->


