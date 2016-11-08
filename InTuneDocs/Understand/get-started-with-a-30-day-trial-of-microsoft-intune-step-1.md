---
title: "Microsoft Intune の 30 日間評価版にサインアップする | Microsoft Intune"
description: "Intune の無料の 30 日間評価版にサインアップする方法、およびサインアップする前の考慮事項"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 08/09/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dad88d43-0054-4be6-9e5d-ada5a957dd6c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: 0eb72fba9bd299a29c8da1b3477582fb4a0a31ab


---

# <a name="sign-up-for-a-30day-evaluation-of-microsoft-intune"></a>Microsoft Intune の 30 日間評価版にサインアップする

モバイル デバイスとコンピューターを管理する Microsoft Intune は、30 日間の無料評価版を迅速かつ簡単に設定できます。 評価版ではいくつかの簡単な手順を行うだけで、最大 100 のユーザーとデバイスの追加、グループの設定、コンプライアンス ポリシーの構成、モバイル デバイスとコンピューターの登録と管理を行うことができます。 このトピックでは、Intune の特長と機能を評価できるよう、Intune の評価版の稼働方法とサービスの概要の理解に関する基本的な内容を学習します。

## <a name="what-to-consider-before-you-sign-up"></a>サインアップする前の考慮事項

Intune にサインアップまたはサインインするには、あらかじめ次の点を考慮しておく必要があります。

-   Microsoft Online Services の職場または学校アカウントが既に組織に存在するかどうか

-   マイクロソフト エンタープライズ契約または同等のボリューム ライセンス契約を Microsoft との間で締結しているかどうか

-   30 日間の評価期間後に Intune テナントを使用する予定であるかどうか

|以下のいずれかに該当する場合は "新しい" アカウントにサインアップ|以下に該当する場合、職場または学校アカウントでサインイン|
|-----------------------------------------------------------------|------------------------------------------------|
|**職場または学校アカウントを持っていない。** 職場または学校アカウントは、Microsoft とボリューム ライセンス契約を結んだとき、または Office 365 をサブスクライブしたときに支給されます。 組織が Enterprise Agreement または同等のボリューム ライセンス契約を Microsoft と結んでいない場合 (または Office 365 アカウントを持っていない場合)、Microsoft Online Services へのサインインに使用できる Microsoft Online Services アカウントを持っていません。<br /><br />**30 日の評価期間後に Intune テナントを破棄する。** 評価のみを目的として Intune の無料評価版のサブスクリプションを使用している場合で、なおかつ評価後に、Intune サービスのセットアップとデバイスのプロビジョニングをやり直す場合は、新しいアカウントにサインアップする必要があります。 Intune と System Center 2012 Configuration Manager を使用する予定の場合に推奨されるオプションです。<br /><br />新しいアカウントにサインアップする場合、後で既存の職場アカウントまたは学校アカウントを使用するように変更してそのアカウントを管理したり、既存のボリューム ライセンス契約と結合したりすることはできません。|**ボリューム ライセンス契約または Office 365 アカウントのサブスクリプションで支給された職場または学校アカウントがあり、評価版を使用して Intune を評価する。**<br /><br />既存のアカウントで Intune をセットアップする場合、作業前に「[デバイスを管理する方法を選択する](/intune/get-started/choose-how-to-manage-devices)」の内容を確認することをお勧めします。|

## <a name="sign-up-or-sign-in-to-intune"></a>Intune にサインアップまたはサインインする

1.  まず、 [ここをクリックして Intune のサインアップ ページにアクセスします](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)。

2.  **[サインアップ]** ページには 2 つのオプションがあります。

    -   **Microsoft Online Services の会社または学校のアカウントを使用してサブスクライブする**:既に会社または学校のアカウントがあり、そのアカウントを使用して両方のサービスにサブスクライブする場合は、[ **サインイン** ] をクリックします。 複数のサービスで同じアカウントを使用する場合、それらのサービスでは同一の Azure AD インフラストラクチャが使用され、Azure AD のテナントになります。 Azure AD は、Microsoft Cloud Services の中核ディレクトリとなり、ID 管理機能を使用できます。

    -   **Intune にのみサブスクライブする**: まだクラウド サービスにサブスクライブしていない場合、[サインアップ] ページのフォームに必要事項を記入して、Intune にサブスクライブします。

        > [!NOTE]
        > 既定では、ドメイン名は、サブスクリプションと、Intune に追加するユーザー アカウントに関連付けられます。 サブスクライブ後、既に所有しているカスタム ドメイン名を追加して使用するか、無料の **onmicrosoft.com** ドメインを引き続き使用できます。

サインアップ フォームに入力して、Microsoft Online サブスクリプション契約に同意すると、テナントの管理者アカウントを使用して自動的に Office 365 管理センターにサインインします。 また、アカウント情報が記載された電子メール メッセージが、サインアップ中に指定した電子メール アドレスに送信されます。 このメールで、サブスクリプションがアクティブになったことが確認されます。

### <a name="next-steps"></a>次のステップ
これで終了です。 *Microsoft Intune の評価*チュートリアルの手順 1 が完了しました。

>[!div class="step-by-step"]

>[&larr; **はじめに**](get-started-with-a-30-day-trial-of-microsoft-intune.md)     [**ユーザーの追加** &rarr;](get-started-with-a-30-day-trial-of-microsoft-intune-step-2.md)  



<!--HONumber=Nov16_HO1-->


