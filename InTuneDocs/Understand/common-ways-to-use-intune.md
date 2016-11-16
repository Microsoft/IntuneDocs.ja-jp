---
title: "Intune の一般的な使用方法 |Microsoft Intune"
description: "Intune でできる最も一般的なタスクのうち 6 つを表示する"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: robstackmsft
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 198f7911db02b349c5be280a382ea26dea383b5b
ms.openlocfilehash: 292a7967deebbcca39d2debc5d8ea9478d08137a


---

# <a name="common-ways-to-use-intune"></a>Intune の一般的な使用方法

実装を始める前に、自社のエンタープライズ モビリティの関係者と、ビジネス目標に関する認識を合わせておくことが重要です。  これは、エンタープライズ モビリティを初めて導入する場合も、別の製品から移行する場合も同様です。  エンタープライズ モビリティ関連のニーズは動的に進化しており、これらのニーズに対応する Microsoft のアプローチが市場の他のソリューションとは異なる場合もあります。  ビジネス目標に関する認識を合わせる最善の方法は、有効にするシナリオで実現したいことを、従業員、パートナー、IT に対して明確にすることです。  以下では、Intune を使用する 6 つの一般的なシナリオについて簡単に説明します。また、各シナリオを計画および展開する方法を詳しく説明する記事のリンクも示します。

>[!NOTE]
>Microsoft IT は Intune を使用して、企業のデータを保護しながら、Microsoft の従業員が個人のモバイル デバイスで会社のリソースにアクセスすることを可能にしています。 Microsoft IT が Intune とその他のサービスをどのように使用して ID、デバイス、アプリ、およびデータを管理しているか、[こちらのテクニカル ケース スタディ](https://www.microsoft.com/itshowcase/Article/Content/588)でその方法の詳細をご確認ください。  

>[!IMPORTANT]
>モバイル デバイスを確実に最新の状態にする<br>
>iOS デバイスへの "Trident" マルウェアによる最近の攻撃を踏まえ、ブログ記事「[Ensuring mobile devices are up to date using Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/)」(Microsoft Intune でモバイル デバイスを確実に更新する) を新たに公開しました。デバイスを安全に、かつ最新の状態に保つために役立つ Intune のさまざまな使い方について説明しています。

## <a name="securing-your-onpremises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>モバイル デバイスで安全にアクセスできるようにオンプレミスの電子メールとデータを保護する
ほとんどのエンタープライズ モビリティ戦略は、従業員がモバイル デバイスを使用してインターネット上の電子メールに安全にアクセスできるようにするための計画で始まります。 組織の多くは、まだ自社ネットワークでホストするオンプレミスのデータとアプリケーション サーバーを使用しています (Microsoft Exchange など)。 Intune と Microsoft Enterprise Mobility + Security (EMS) が提供する Exchange Server 向けの統合された[条件付きアクセス ソリューション](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)により、企業ネットワークに別のゲートウェイ マシンを展開することなく、Intune でデバイスを登録するまで、どのモバイル アプリからも電子メールにアクセスできないようにすることができます。

電子メール以外にも、基幹業務アプリケーション サーバーのような、オンプレミス データへの安全なアクセスを必要とするモバイル アプリへのアクセスを有効にすることもできます。  このようにするには一般的に、[Intune で管理される証明書](/intune/deploy-use/secure-resource-access-with-certificate-profiles)を使用してアクセスを制御することに加えて、標準的な VPN ゲートウェイまたはプロキシ (たとえば Microsoft Azure AD アプリケーション プロキシ) を境界に配備します。  このようなケースで企業のデータにアクセスする唯一の方法は、デバイスを管理システムに登録することです。  登録後は、管理システムによって、会社のデータにアクセスするデバイスがポリシーに準拠していることが確認されます。  さらに、Intune の[アプリ ラッピング ツールとアプリ SDK](/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune) を使用すると、コンシューマー向けのアプリケーションやサービスに会社のデータが渡されることのないよう、アクセスされるデータを基幹業務アプリケーション内に保持するのに役立ちます。

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->

## <a name="securing-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>モバイル デバイスで安全にアクセスできるように Office 365 の電子メールとデータを保護する
Office 365 の企業データ (電子メール、ドキュメント、インスタント メッセージ、連絡先) の保護は、非常に簡単かつシームレスに行えます。 Intune と Microsoft Enterprise Mobility + Security が提供する統合された条件付きアクセス ソリューションにより、会社のコンプライアンス要件 ([多要素認証](/intune/deploy-use/protect-windows-devices-with-multi-factor-authentication)、Intune での登録、管理されたアプリの使用、サポート対象の OS のバージョン、デバイスの PIN、リスクの低いユーザー プロファイルなど) を満たしていない限り、どのユーザーやアプリ、デバイスも Office 365 のデータにアクセスできないようにすることができます。 それぞれのアプリ ストアの Office モバイル アプリは Intune で構成できるデータ封じ込めポリシーに対応しており、IT が管理していないアプリ (ネイティブ電子メール アプリなど) やストレージの場所 (Dropbox など) とデータが共有されないようにすることができます。  こうした機能はすべて Office 365 と EMS に組み込まれているので、  新たにインフラストラクチャを展開する必要はありません。

Office 365 の一般的な展開方法では、デバイスを企業のアプリ/証明書/Wi-Fi/VPN 構成を使用して完全にプロビジョニングする必要がある場合 (通常は企業所有のデバイスの場合)、そのデバイスを管理システムに登録する必要があります。  ただし、ユーザーが個人的に所有しているデバイスで会社の電子メールやドキュメントにアクセスする必要があるだけの場合は、([データ封じ込めポリシーを適用](/intune/deploy-use/protect-apps-and-data-with-microsoft-intune)している) Office モバイル アプリを使用すれば、デバイスの登録を省略することができます。  どちらの方法でも、Office 365 のデータは定義されているポリシーによって保護されます。

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->

## <a name="offer-a-bring-your-own-device-byod-program-to-all-employees"></a>すべての従業員に "Bring your own device" (BYOD) プログラムを提供する
BYOD は、ハードウェアの経費を削減し、従業員のモバイル生産性向上のための選択肢を増やす手段として、組織の間で普及が進み続けています。 今では、ほぼすべての従業員が個人の電話を所有しています。そのような環境で、業務用のデバイスを別に支給するメリットはあるでしょうか。 BYOD の主な課題は、個人のデバイスを管理システムに登録することを従業員に納得してもらうことです。だれも、会社の IT 部門にデバイスの中身を覗かれたり操作されたりしたくはないでしょう。  

デバイスの登録が現実的でない場合のために、Intune には単に[企業データを含むアプリケーションを管理する](/intune/deploy-use/protect-apps-and-data-with-microsoft-intune)だけの BYOD アプローチも用意されています。  Intune は、Office モバイル アプリのようにアプリが会社と個人の両方のデータにアクセスする場合でも、会社のデータを保護することができます。  この場合、管理者は Office モバイル アプリから Office 365 にアクセスするようユーザーに要求し、データを保護するポリシー (暗号化、PIN による保護など) を使用してアプリを構成する必要があります。  これらのポリシーにより、管理対象外のアプリとストレージの場所 (アプリの内外を問わず) へのデータ損失を防ぎます。  たとえば、どちらも Outlook Mobile 内で構成されたプロファイルであっても、会社の電子メール プロファイルからコンシューマー向けの電子メール プロファイルにテキストがコピーされないようにします。  同様の構成は、BYOD ユーザーに必要な他のサービスやアプリケーションにも展開できます。

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## <a name="issue-corporateowned-phones-to-your-information-workers"></a>インフォメーション ワーカー向けに企業所有の携帯電話を用意する
今日のほとんどのインフォメーション ワーカーはモバイル環境で働いています。他社との競争に勝つためには、モバイル デバイスでの生産性向上が必要不可欠です。  彼らはいつでも、どこにいても、会社のアプリとデータのすべてにシームレスにアクセスできる必要があります。  管理者は、会社のデータをセキュリティで保護しながら、管理コストは低く抑える必要があります。  

Intune の[一括プロビジョニングと管理のソリューション](/intune/deploy-use/manage-corporate-owned-devices)は、Apple Device Enrollment Program や Samsung KNOX モバイル セキュリティ プラットフォームなど、今日の市場における主要な企業デバイス管理プラットフォームと統合されています。  Intune でデバイス構成を一元的に作成することで、企業デバイスのプロビジョニングを高度に自動化することができます。  

新しい iPhone を従業員に手渡すシーンを想像してみてください。 従業員が電源につなぎ、企業ブランドのセットアップ フローを進めて自分で認証を行います。 iPhone は、[セキュリティ ポリシー](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) (ハード ドライブの暗号化、デバイスの PIN など)、[電子メール/Wi Fi/VPN/証明書プロファイル](/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune)、および[アプリ](/intune/deploy-use/add-apps)のベースライン セットでシームレスに構成されます。 次に、従業員は Intune ポータル サイト アプリを起動し、任意で使用できる会社のアプリにアクセスします。

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## <a name="issue-limiteduse-shared-tablets-to-your-task-workers"></a>タスク ワーカー向けに制限付きの共有タブレットを用意する
タスク ワーカーはますますモバイル テクノロジを使用するようになっています。  たとえば、小売店舗の従業員の間で共有タブレットを使用することは、今ではめずらしいことではありません。  販売処理や在庫チェックなど、タブレットを使用することで顧客とのやり取りがスムーズに行えるようになります。  こうしたケースでは、ユーザー エクスペリエンスの簡潔さが重要です。  そのため、タブレットは通常、1 つの基幹業務アプリだけが使用可能になっている、制限付きモードで従業員に渡されます。  Intune を使用すると、[iOS](/intune/deploy-use/ios-policy-settings-in-microsoft-intune#general-configuration-policy-settings) や [Android](/intune/deploy-use/android-policy-settings-in-microsoft-intune#general-configuration-policy) などの共有タブレットを制限付きモードで実行するように構成し、一括でプロビジョニングしてセキュリティで保護し、一元的に管理できます。

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## <a name="enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk"></a>公共の場所から Office 365 に安全にアクセスできるようにする
従業員は、展示会場やホテルのロビーにある公共のコンピューターなど、会社が管理できないデバイスやアプリ、ブラウザーを使用しなければならない場合があります。 そのような場所から会社の電子メールにアクセスすることを従業員に許可すべきでしょうか。 Intune と Microsoft Enterprise Mobility + Security を使用している場合、<!--you have choices. The-->答えは単純に "いいえ" であり、[電子メールへのアクセスを組織が管理しているデバイスに制限します](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)。  <!-- Alternatively, you can choose to allow limited access to these untrusted computers by requiring multi-factor authentication and only allowing browser access (Outlook Web Access) in a mode where files cannot be downloaded (e.g. email attachments).--> これにより、従業員が厳密に認証されるので、信頼されていないコンピューターに誤って会社のデータを残してしまうことがなくなります。

<!-- Learn more about how to plan and deploy Intune to support kiosks. -->



<!--HONumber=Nov16_HO2-->


