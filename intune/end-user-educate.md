---
title: "Microsoft Intune に関してエンド ユーザーを教育する方法 | Microsoft Intune"
description: "Intune の展開を成功に導くために、エンド ユーザーと情報を共有しましょう。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/10/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 48914533-f138-4dc0-8b93-4cea3ac61f7b
ms.reviewer: robstack
ms.suite: ems
ms.openlocfilehash: d940bc937caf966dd2d8c2ce01570bfa09a65bfb
ms.sourcegitcommit: ca10ab40fe40e5c9f4b6f6f4950b551eecf4aa03
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2017
---
# <a name="how-to-educate-your-end-users-about-microsoft-intune"></a>Microsoft Intune に関してエンド ユーザーを教育する方法

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Microsoft Intune は、会社のデータを保護した状態で、従業員がモバイル デバイスを使用できるようにします。 [無料試用版](app-sdk.md)で Intune を評価するなど、確実に展開するための手順が多数あります。

こうしたテクノロジでは、デバイスを管理する理由の重要性について、ユーザーの理解を確保することはできません。 実際にエンド ユーザーの多くは、特に Intune を [BYOD ソリューション](/enterprise-mobility-security/solutions/byod-design-considerations-guide)として展開する場合に、プライバシーが侵害されるように感じることがあります。

> [!Important]
> 会社がデバイスを管理する必要がある理由に関するエンド ユーザーの懸念を理解し、積極的に対処することは、確実にロールアウトするために不可欠となります。

導入は従業員にテクノロジを浸透させ、機能させるだけでなく、Intune で提供される安全なアクセスを受け入れるエンド ユーザーを増やすことを意味します。 一般的に、ユーザーにはエンタープライズ モビリティの目的や、エンタープライズ モビリティでできること (およびできないこと) について、知っておくべきことを説明していないため、エンタープライズ モビリティに脅威を感じるかもしれません。

## <a name="things-to-consider-about-your-end-users"></a>エンド ユーザーに関する考慮事項

__エンド ユーザーの経験レベル__ エンド ユーザーは、さまざまなテクノロジに広範囲におよぶ経験がある可能性があります。 これらの経験は役に立つ場合と役に立たない場合があり、子供の写真を撮ったなどの忘れられない経験から、デバイスを流しに落としてしまい、バックアップしていなかったデータをすべて失ったなどの経験にいたるまでさまざまなものがあります。 こうした経験は、テクノロジのアプローチ方法や、デバイスの個人的用途とビジネス用途の認識に色濃く反映されます。

__モビリティ管理の意味__ ユーザーは、デバイスや情報に対するアクセス権について、完全に理解していない可能性があります。 ユーザーは、IT 管理者やリーダーが自分のあらゆる行動を把握する可能性があることを懸念するかもしれません。 これは特に経験の浅いユーザーに対して憂慮すべき点です。経験の浅いユーザーは、デバイスでのアクティビティはすべてプライベートなものだと認識している可能性があります。 経験豊富なユーザーは、"ビッグ ブラザー" (政府や権力のある人) がデバイスをひそかに見張っているのではと懸念し、その懸念を同僚に伝える可能性があります。

__エンド ユーザーに不便な点__ アプリのインストール、デバイスの登録、およびコンプライアンスの維持には時間がかかります。 会社のデータ セキュリティを確保することは、Intune の展開の最優先事項ですが、個人のデバイスに対する不当にパスコードを求めると、ユーザーは自身のデバイスの管理も不快に思います。 ビジネスに不可欠な電話会議の途中で必要なアプリの更新プログラムを送信すると、ユーザーの生産性が低くなり、モバイル デバイスの使用が逆効果となる可能性があります。

## <a name="things-you-should-do"></a>必要な手順

このようなユーザーの懸念を緩和することで、展開がよりスムーズになります。 エンド ユーザーがデバイスの管理を受け入れやすくするために検討すべき方法を以下にリストします。

* __要領をよくする。__ Intune ドキュメントにはさまざまな内容が含まれています。これは、エンド ユーザーが、デバイスの登録やトラブルシューティングなどの、特定のタスクを実行する方法を理解するのに役立ちます。 その中の記事はポータル サイトからリンクされており、ポータル サイト アプリのインストールと Intune の登録、デバイス上でユーザーが実行可能な一般的なタスク、およびトラブルシューティングに関するセクションに分けられています。 このドキュメントは、[管理デバイスを使用して作業する](/intune-user-help/use-managed-devices-to-get-work-done)方法の説明ページで見つけることができます。

* __アクセスしやすくする。__ エンド ユーザーは、デバイスに関する支援を受けることができる場所を知っておく必要があります。 [ポータル サイトをカスタマイズする](company-portal-customize.md)ときは、ユーザーが必要に応じて支援を受けることができるように、IT 管理者の連絡先情報を必ず含めてください。

* __個人向けにする。__ 展開について具体的でない手順を示すと、エンド ユーザーは経験が考慮されていないと思うかもしれません。 [IT 管理者向けのカスタマイズ可能なエンド ユーザー Intune 登録テンプレート](https://gallery.technet.microsoft.com/office/Intune-End-User-Enrollment-3a0c9b0c)を使用して、独自にエンドユーザー向けの登録手順を作成することができます。

* __さまざまなコミュニケーションの方法を見つける。__ [学習スタイルが異なる](https://www.umassd.edu/dss/resources/facultystaff/howtoteachandaccommodate/howtoaccommodatedifferentlearningstyles/)のと同じように、ユーザーによって、好まれる情報の使用方法は異なります。 ドキュメントよりもビデオを好むユーザーのために、Channel 9 で[さまざまな種類のデバイスを登録する方法を紹介するビデオ](https://channel9.msdn.com/Series/IntuneEnrollment)などを提供しています。 これらのビデオは、独自の [SharePoint サイト](https://support.office.com/article/Embed-a-video-from-Office-365-Video-59e19984-c34e-4be8-889b-f6fa93910581)に直接埋め込むことも、ビデオまたは単なるオーディオ トラックのローカル コピーとしてダウンロードできるようにすることもできます。

* __意識する。__ エンド ユーザーの経験は生産性に影響します。経験を理解することで、発生している問題のトラブルシューティングをより簡単に行うことができます。 また、エンド ユーザーがアプリを取得する方法を理解することで、発生している問題を診断しやすくなり、より迅速に問題を解決できます。

* **Android**
  * [Android デバイスを Intune で使用する](/intune-user-help/using-your-android-device-with-intune)
  * [Android ユーザーがアプリを入手する方法](end-user-apps-android.md)

* **iOS**
  * [iOS デバイスを Intune で使用する](/intune-user-help/using-your-ios-device-with-intune)
  * [iOS ユーザーがアプリを入手する方法](end-user-apps-ios.md)

* **Windows**
  * [Windows デバイスを Intune で使用する](/intune-user-help/using-your-windows-device-with-intune)
  * [Windows ユーザーがアプリを入手する方法](end-user-apps-windows.md)

* __積極的に行動する。__ デバイスでの管理内容をユーザーに明確に伝えます。 収集するデータの種類とその理由を伝えます。 すべての資産データの使用をどのように計画しているかを知らせます。 [Microsoft は、お客様がクラウド内のご自身の顧客データの処理方法について、可能な限り多くの情報を把握しておく必要があることを理解しています。](https://www.microsoft.com/trustcenter/about/transparency)また、この理念により、Intune に関するエンド ユーザーの満足度を高めることができると信じています。

>[!Note]
> 可能な限り透明性を維持することは、確実に展開するために不可欠となります。

信頼と適切に作成されたコンプライアンス ポリシーを結び付けてみて、特定の種類の個人データを調べる*可能性がある*としても、それは*やむを得ない*ことだということと、プライバシーの侵害に関する責任について、エンド ユーザーが確実に認識するようにしてください。 また、法務部門と人事部門で声明を作成しておくことは、特に頑固な従業員を説得するのに役立ちます。
