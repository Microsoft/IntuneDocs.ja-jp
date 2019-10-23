---
title: Microsoft Intune に関してエンド ユーザーを教育する方法
titleSuffix: Microsoft Intune
description: Intune の展開を成功に導くために、デバイス ユーザーと情報を共有します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 06/01/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 48914533-f138-4dc0-8b93-4cea3ac61f7b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c959102383f44eb35e1a923f39325007c6624b5
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502897"
---
# <a name="how-to-educate-your-end-users-about-microsoft-intune"></a>Microsoft Intune に関してエンド ユーザーを教育する方法

Microsoft Intune は、会社のデータを保護しながら、従業員がモバイル デバイスを使用できるようにします。 組織内で Intune の展開をテストするには、[無料試用版](free-trial-sign-up.md)をお試しいただけます。

Microsoft Intune を実装する際には、従業員がデバイスの管理およびエンタープライズ モビリティの必要性を理解することが重要です。 会社からの説明がなければ、ユーザーによっては自分のプライバシーが侵害されていると感じるかもしれません。 Intune を [BYOD ソリューション](/enterprise-mobility-security/solutions/byod-design-considerations-guide)として展開する場合、プライバシーに対するユーザーの懸念は増します。

> [!Important]
> 会社がデバイスを管理する必要がある理由に関するユーザーの懸念を理解し、積極的に対処することは、確実にロールアウトするために不可欠となります。

導入を成功させるために必要なことは、新しい機能的テクノロジを社内全体に配布することだけではありません。 ユーザーに新しいテクノロジを理解してもらい受け入れてもらうことも必要です。 そのため、Intune によって提供されるデータ セキュリティをユーザーが理解し、受け入れることが重要になります。

## <a name="things-to-consider-about-your-users"></a>ユーザーに関する考慮事項

__ユーザーのテクノロジ経験レベル__ テクノロジに対するユーザーの知識と経験は、多様であると考えられます。 これらの経験には、家族旅行を写真撮影したといったような有意義なものもあれば、デバイスを不意に台所の流しに落としてしまったなどという苦い経験もあるのではないでしょうか。 経験は、個人使用およびビジネス使用でのユーザーのテクノロジに対する取り組み方に影響を与えます。

__ユーザーにとってのモビリティ管理の意味__ ユーザーは自分のデバイスや情報に対して会社が有する (または有していない) アクセス権について、完全に理解していない可能性があります。 ユーザーはおそらく、IT 管理者やリーダーが自分の行動を把握する可能性があることを懸念するでしょう。 経験の浅いデバイス ユーザーは、デバイスでのアクティビティはすべてプライベートなものだと認識している可能性があります。

__ユーザーにとって Intune が不便な点__  ユーザーによるアプリのインストール、デバイスの登録、およびコンプライアンスの維持にかかる時間を認識し尊重します。 すべての Intune 展開における最優先事項は、会社のデータ セキュリティを確保することです。 ただし、次のようにポリシーを強要した場合、デバイス管理に対するユーザーの態度に悪影響を与える可能性があります。  

- 個人のデバイスに対して不当にパスコードを求める
- 必要なアプリの更新プログラムを、ビジネスに不可欠な電話の途中で送信する  

このようなポリシーは、従業員の生産性にも悪影響を及ぼす可能性がります。

## <a name="things-you-should-do"></a>必要な手順

次に示すヒントの一覧を参照することで、デバイス ユーザーに対する組織の Intune 展開が容易になります。

* __要領をよくする。__ Intune ドキュメントは、ユーザーがデバイスの登録やトラブルシューティングなどの Intune 固有のタスクを実行するのに役立ちます。 ユーザーはポータル サイトから、クリック操作により、一部の記事に直接アクセスすることができます。 これらの特定の記事は、ポータル サイト アプリのインストール、Intune の登録、デバイス上でユーザーが実行可能な一般的なタスク、およびトラブルシューティングを説明する上で役立ちます。 このドキュメントの一覧は、記事「[管理デバイスを使用して作業する](https://docs.microsoft.com/intune-user-help/use-managed-devices-to-get-work-done)」でも確認できます。

* __アクセスしやすくする。__ デバイスの問題に関するヘルプ情報を検索できる場所をユーザーに伝えます。 [ポータル サイトをカスタマイズ](../apps/company-portal-app.md)する場合は、IT 管理者の連絡先情報を必ず含めてください。

* __個人向けにする。__ 組織の展開に関する具体的な手順を提供します。 このアクションにより、経験を考慮していることをユーザーに示します。 こちらのカスタマイズ可能な [Intune 導入キット](https://aka.ms/IntuneAdoptionKit)を使用して、独自にユーザー向けの登録手順を作成することができます。

* __さまざまなコミュニケーションの方法を見つける。__ ユーザーによって、[学習スタイルが異なり](https://www.umassd.edu/dss/resources/faculty--staff/how-to-teach-and-accommodate/how-to-accommodate-different-learning-styles/)、また好まれる情報の使用方法が異なります。 視覚的な学習として、Intune では Channel 9 で[さまざまな種類のデバイスを登録する方法を紹介するビデオ](https://channel9.msdn.com/Series/IntuneEnrollment)を提供しています。 ビデオは、独自の [SharePoint サイト](https://support.office.com/article/Embed-a-video-from-Office-365-Video-59e19984-c34e-4be8-889b-f6fa93910581)に直接埋め込むことができます。 ビデオまたはオーディオ トラックのローカル コピーをダウンロードすることもできます。

* __意識する。__ Intune ユーザーの経験は生産性にも影響します。 ユーザーの経験を理解することで、デバイスおよびユーザーの問題のトラブルシューティングをより簡単に行うことができます。 たとえば、ユーザーがアプリを取得する方法を学習し理解することができます。 この情報を前もって把握しておくことにより、問題の診断および解決をより簡単かつ迅速に行うことができます。

* **Android**
  * [Android デバイスを Intune で使用する](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)
  * [Android ユーザーがアプリを入手する方法](end-user-apps-android.md)

* **Android**
  * [iOS デバイスを Intune で使用する](https://docs.microsoft.com/intune-user-help/using-your-ios-device-with-intune)
  * [iOS ユーザーがアプリを入手する方法](end-user-apps-ios.md)

* **Windows**
  * [Windows デバイスを Intune で使用する](https://docs.microsoft.com/intune-user-help/using-your-windows-device-with-intune)
  * [Windows ユーザーがアプリを入手する方法](end-user-apps-windows.md)

* __積極的に行動する。__ ユーザー デバイスに対する管理の内容について明らかにします。 収集するデータの種類とその理由をユーザーに伝えます。 すべてのデータの使用をどのように計画しているかを知らせます。 [Microsoft は、お客様がクラウド内のご自身の顧客データの処理方法について、可能な限り多くの情報を把握しておく必要があることを理解しています。](https://www.microsoft.com/trustcenter/about/transparency)また、この理念により、Intune に関するユーザーの満足度を高めることができると信じています。

> [!Note]
> 可能な限り透明性を維持することは、確実に展開するために不可欠となります。

信頼と適切に作成されたコンプライアンス ポリシーを結び付けることが重要です。 特定の種類の個人データが調べられる*可能性がある*としても、それは*やむを得ない*ことだということをユーザーは認識する必要があります。 プライバシーの侵害に関する責任について、ユーザーが理解できるように説明してください。 また、法務部門と人事部門で声明を作成しておくことで、従業員のプライバシーに関する懸念を十分に和らげることができる場合があります。
