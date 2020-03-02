---
title: Microsoft Intune の一般的な使用方法
description: Microsoft Intune を使用すると管理に役立つ、最も一般的なタスクの 6 つについて説明します。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 11/29/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 67d9b5df39311d58571f875b8d41c16088010fad
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514304"
---
# <a name="common-ways-to-use-microsoft-intune"></a>Microsoft Intune の一般的な使用方法

実装を始める前に、自社のエンタープライズ モビリティの関係者と、Intune の使用におけるビジネス目標に関する認識を合わせておくことが重要です。 これは、エンタープライズ モビリティを初めて導入する場合も、別の製品から移行する場合も同様です。  

エンタープライズ モビリティ関連のニーズは動的に進化しており、これらのニーズに対応する Microsoft のアプローチが市場の他のソリューションとは異なる場合もあります。 ビジネス目標に関する認識を合わせる最善の方法は、実現するシナリオの目標を従業員、パートナー、IT 部門に対して明確にすることです。  

以下では、Intune を使用する 6 つの一般的なシナリオについて簡単に説明します。また、各シナリオを計画および展開する方法を詳しく説明する記事のリンクも示します。

>[!NOTE]
>Microsoft IT は Intune を使用して、企業のデータを保護しながら、Microsoft の従業員が個人のモバイル デバイスで会社のリソースにアクセスすることを可能にしています。 Microsoft IT が Intune とその他のサービスをどのように使用して ID、デバイス、アプリ、およびデータを管理しているか、[こちらのテクニカル ケース スタディ](https://www.microsoft.com/itshowcase/Article/Content/588)でその方法の詳細をご確認ください。  

>[!IMPORTANT]
>Microsoft では、iOS/iPadOS デバイスに対する最近の "Trident" マルウェア攻撃を考慮して、モバイル デバイスを確実に最新の状態にしたいと考えています。 そのため、「[Ensuring mobile devices are up to date using Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/)」(モバイル デバイスを確実に最新の状態にする) というブログの投稿を公開しました。 このブログでは、Intune でデバイスを保護し、最新の状態に保つためのさまざまな方法について説明しています。

## <a name="protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>モバイル デバイスで安全にアクセスできるようにオンプレミスの電子メールとデータを保護する

ほとんどのエンタープライズ モビリティ戦略は、従業員がインターネットに接続しているモバイル デバイスを使用して電子メールに安全にアクセスできるようにするための計画で始まります。 組織の多くは、まだ自社ネットワークでホストするオンプレミスのデータとアプリケーション サーバーを使用しています (Microsoft Exchange など)。

Intune と Microsoft Enterprise Mobility + Security (EMS) では、Exchange Server 向けに独自の統合された[条件付きアクセス ソリューション](../protect/conditional-access.md)が提供されています。これにより、デバイスが Intune に登録されるまで、モバイル アプリは電子メールにアクセスできなくなります。 この種類の電子メール アクセスは、別のゲートウェイ コンピューターを会社のネットワークのエッジに展開することなく実装できます。

また、基幹業務アプリケーション サーバーのような、オンプレミス データへの安全なアクセスを必要とするモバイル アプリへのアクセスを有効にすることもできます。 通常、この種のアクセスを行うには、アクセス制御用に [Intune で管理された証明書](../protect/certificates-configure.md)と、境界内の標準の VPN ゲートウェイまたはプロキシ (Microsoft Azure Active Directory アプリケーション プロキシなど) を組み合わせて使用します

このようなケースで企業のデータにアクセスする唯一の方法は、デバイスを管理システムに登録することです。 デバイスが登録されると、管理システムでポリシーに準拠していることが確認されてから、デバイスが会社のデータにアクセスできるようになります。 さらに、Intune の[アプリ ラッピング ツールと App SDK](../developer/apps-prepare-mobile-application-management.md) は、アクセスされるデータを基幹業務アプリケーション内に保持することで、コンシューマー向けのアプリケーションやサービスに会社のデータを渡せないようにします。

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->

## <a name="protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>モバイル デバイスで安全にアクセスできるように Office 365 の電子メールとデータを保護する

Office 365 の企業データ (電子メール、ドキュメント、インスタント メッセージ、連絡先) の保護は、非常に簡単かつシームレスに行えます。

Intune と Microsoft Enterprise Mobility + Security によって提供される統合された条件付きアクセス ソリューションにより、会社のコンプライアンス要件 ([多要素認証](../enrollment/multi-factor-authentication.md)、Intune での登録、管理されたアプリの使用、サポート対象の OS のバージョン、デバイスの PIN、リスクの低いユーザー プロファイルなど) を満たしていない限り、どのユーザーやアプリ、デバイスも Office 365 のデータにアクセスできないようにすることができます。

それぞれのアプリ ストアの Office モバイル アプリは Intune で構成できるデータ封じ込めポリシーに対応しています。 そのため、IT 部門で管理されていないアプリ (ネイティブの電子メール アプリなど) や記憶域の場所 (Dropbox など) とのデータの共有を防ぐことができます。 こうした機能はすべて Office 365 と EMS に組み込まれているので、 新たにインフラストラクチャを展開する必要はありません。

Office 365 の一般的な展開方法では、デバイスを企業のアプリ、証明書、Wi-Fi、VPN 構成を使用して完全にセットアップする必要がある場合 (通常は会社所有のデバイスの場合)、そのデバイスを管理システムに登録する必要があります。  

ただし、個人的に所有しているデバイスなどで、ユーザーが会社の電子メールとドキュメントへのアクセスのみ必要な場合は、[アプリ保護ポリシー](../apps/app-protection-policies.md)を適用してある Office モバイル アプリを使用すれば、デバイスの登録を省略できます。  

どちらの方法でも、Office 365 のデータは定義されているポリシーによって保護されます。

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->

## <a name="offer-a-bring-your-own-device-program-to-all-employees"></a>すべての従業員に "Bring your own device" プログラムを提供する

"Bring your own device" (BYOD) は、ハードウェアの経費を削減し、従業員のモバイル生産性向上のための選択肢を増やす手段として、組織の間で普及が進み続けています。 今では、ほぼすべての従業員が個人の電話を所有しています。そのような環境で、業務用のデバイスを別に支給するメリットはあるでしょうか。 BYOD の主な課題は、個人のデバイスを管理システムに登録することを従業員に納得してもらうことです。だれも、会社の IT 部門にデバイスの中身を覗かれたり操作されたりしたくはないでしょう。  

デバイスの登録が現実的でない場合のために、Intune には単に[企業データを含むアプリケーションを管理する](../apps/app-protection-policies.md)だけの BYOD アプローチも用意されています。 Intune は、Office モバイル アプリのようにアプリが会社と個人の両方のデータにアクセスする場合でも、会社のデータを保護することができます。  

この場合、管理者は Office モバイル アプリから Office 365 にアクセスするようユーザーに要求し、データを保護するポリシー (暗号化、PIN による保護など) を使用してアプリを構成する必要があります。 これらのアプリ保護ポリシーにより、管理対象外のアプリとストレージの場所 (アプリの内外を問わず) へのデータ損失を防ぎます。 たとえば、どちらも Outlook Mobile 内で構成されたプロファイルであっても、会社の電子メール プロファイルからコンシューマー向けの電子メール プロファイルにテキストがコピーされないようにします。 同様の構成は、BYOD ユーザーに必要な他のサービスやアプリケーションにも展開できます。

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## <a name="issue-corporate-owned-phones-to-your-employees"></a>社員向けに企業所有の携帯電話を用意する

現在は多くの社員がモバイル環境で働いています。他社との競争に勝つためには、モバイル デバイスでの生産性向上が必要不可欠です。 彼らはいつでも、どこにいても、会社のアプリとデータのすべてにシームレスにアクセスできる必要があります。 管理者は、会社のデータをセキュリティで保護しながら、管理コストは低く抑える必要があります。  

Intune の[一括プロビジョニングと管理のソリューション](../enrollment/device-enrollment.md)は、Apple Device Enrollment Program や Samsung Knox モバイル セキュリティ プラットフォームなど、今日の市場における主要な企業デバイス管理プラットフォームと統合されています。 Intune でデバイス構成を一元的に作成することで、企業デバイスのプロビジョニングを高度に自動化することができます。  

新しい iPhone を従業員に手渡すシーンを想像してみてください。 従業員が電源につなぎ、企業ブランドのセットアップ フローを進めて自分で認証を行います。 iPhone は、[セキュリティ ポリシー](../configuration/device-profiles.md)でシームレスに構成されます。

次に、従業員は Intune ポータル サイト アプリを起動し、任意で使用できる会社のアプリにアクセスします。

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## <a name="issue-limited-use-shared-tablets-to-your-employees"></a>社員向けに制限付きの共有タブレットを用意する

社員はますますモバイル テクノロジを使用するようになっています。 たとえば、小売店舗の従業員の間で共有タブレットを使用することは、今ではめずらしいことではありません。  販売処理や在庫チェックなど、タブレットを使用することで顧客とのやり取りがスムーズに行えるようになります。

こうしたケースでは、ユーザー エクスペリエンスの簡潔さが重要です。 そのため、タブレットは通常、1 つの基幹業務アプリだけが使用可能になっている、制限付きモードで従業員に渡されます。 Intune を使用すると、[iOS や Android](../configuration/device-profiles.md) などの共有デバイスを制限付きモードで実行するように構成し、一括でプロビジョニングしてセキュリティで保護し、一元的に管理できます。

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## <a name="enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk"></a>公共の場所から Office 365 に安全にアクセスできるようにする

従業員は、展示会場やホテルのロビーにある公共のコンピューターなど、会社が管理できないデバイスやアプリ、ブラウザーを使用しなければならない場合があります。

そのような場所から会社の電子メールにアクセスすることを従業員に許可すべきでしょうか。 Intune と Microsoft Enterprise Mobility + Security を使用している場合、答えは単純に "いいえ" であり、[電子メールへのアクセスを組織が管理しているデバイスに制限します](../protect/conditional-access.md)。 これにより、従業員が厳密に認証されるため、信頼されていないコンピューターに誤って会社のデータを残してしまうことがなくなります。
