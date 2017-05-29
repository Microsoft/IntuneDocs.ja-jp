---
title: "Microsoft Intune の 30 日間無料試用版にサインアップする | Microsoft Docs"
description: "Microsoft Intune の 30 日間無料評価版にサインアップし、設定します。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 560765fa9d9afa4a1050515e1b2304c998f8c158
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Microsoft Intune の無料試用版にサインアップ

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

この記事では、Intune 試用版にサインアップし、ユーザーを追加する方法について説明します。これを読んだ後に、関連する試用版ガイドを読み、Intune によるモバイル デバイスの管理方法を確認できます。 <!---or app data when devices are not enrolled in Intune.--->

>[!Note]
> 2016 年 12 月以降、Microsoft Intune は Azure ポータルに移行します。一部の無料試用版のサインアップは Azure ポータルの Intune、他のサインアップはクラシック Intune になります。 試用版が Azure ポータルの場合、この記事の手順を実行した後に、[Intune Azure プレビューに関するコンテンツ](/intune/what-is--intune)を参照してください。

## <a name="assumptions"></a>前提条件
サインアップに関するこの記事と試用版ガイドでは、試用版が評価目的のみで使用されること、サブスクライブするときにクリーンな環境から始めることを前提としています。

試用版の開始を簡単にするために、Intune だけを利用するとても単純な環境を構築しています。また、Intune が唯一のデバイス管理方法 (モバイル デバイス管理機関) になるものと想定しています。 ただし、より詳しく知りたい方のために、ガイド全体を通してより技術的なコンテンツも紹介します。

試用版ではサブスクリプション版と同じ機能が利用できます。唯一の違いは、試用版のユーザー アカウントが 100 個に制限されていることです。

## <a name="sign-up-for-your-trial"></a>試用版にサインアップする
[Intune サインアップ](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) ページにアクセスしてフォームに入力し、試用版サブスクリプションにサインアップします。

職場や学校のアカウントを Intune 試用版に使用する場合、代わりに[このリンクにあるサインイン方法](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-1)に従ってください。 ただし、この記事と試用版ガイドでは、職場や学校のアカウントを使用していないものと想定しています。

> [!TIP]
> IT 業務とユーザーのほとんどが自分とは別の場所にある場合、試用版にその場所を設定し、性能を試験できます。

### <a name="post-sign-up-considerations"></a>サインアップ後の考慮事項
評価版にサインアップすると、アカウント情報の記載された電子メール メッセージが、サインアップ過程で登録した電子メール アドレスに送信されます。 このメールで、評価版がアクティブになったことが確認されます。

サインアップ プロセスが完了すると、Office 365 管理センターを使用して、ユーザーを追加し、ライセンスを割り当てるページに移動します。 次回**クラシック Intune** (https://manage.microsoft.com) にサインインすると、Intune 管理コンソールに自動的に移動します。

試用版が **Azure ポータル**の場合、https://portal.azure.com にアクセスし、Intune 試用版の資格情報を使用してサインインします。

## <a name="add-users"></a>ユーザーの追加
Office 365 管理センターを離れ、Intune に移動する前に、試用版アカウントにユーザーを追加する必要があります。

Office 365 管理センターでは、.csv ファイルをアップロードしてユーザーを個別または一括で追加できます。 ここでは個別追加と一括追加の両方を行います。 ただし、運用環境では、おそらく Azure Active Directory ユーザー アカウントを活用することになります。それに関しては、「[入門ガイド](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3)」と本記事の「[次のステップ](#Next-steps)」セクションを参照してください。

### <a name="add-an-individual-user"></a>個々のユーザーを追加する
1. いずれかのユーザー追加オプションを選択し、フォームを開きます。そのフォームでユーザーを作成できます。 アスタリスク (\*) の付いている項目だけが入力必須となります。
![[ユーザーの追加] ボタンのオプションの画像](./media/sign-up/add-user.png)


2.  ユーザーを追加するとき、最初の手順は、Intune の仮パスワードが記載されたメールをユーザーに送信することです。 今回は評価が目的のため、職場の自分のメール アドレスを利用します。自分でログオン情報を受け取り、ユーザーに送信されるメールを確認します。 次に、ユーザー ID を利用し、テスト デバイスを登録します。<br/>

 ![ユーザーの追加の最後の手順の画像](./media/sign-up/new-user-2.png)

3. 作成したユーザーに監理者の役割を与える場合、Office 365 管理センターでその役割を編集できます。ユーザーの一覧からユーザー名を選択し、[役割] 行で **[編集]** を選択し、ユーザーの役割の一覧を表示します。そこから役割を選択し、そのユーザーに割り当てることができます。

 ![ユーザーの役割のオプションの画像](./media/sign-up/change-user-role.png)

### <a name="import-multiple-users"></a>複数のユーザーをインポートする
1. **[その他]** 一覧には、複数のユーザーをインポートするためのウィザードがあります。

 ![複数のユーザーを追加するオプションの画像](./media/sign-up/add-multiple-users.png)

2. テンプレート ファイルをダウンロードし、それにユーザー データを入力すれば、正しい .csv ファイルを作成できます。 ヘッダーとサンプル ユーザー情報を含む .csv ファイルをダウンロードし、各フィールドに必要なデータの種類を確認します。

 ![一括登録ウィザードの最初の手順の画像](./media/sign-up/bulk-enroll-step-1.png)


3. .csv ファイルを作成して保存したら、**[参照]** を選択し、そのファイルを選択します。 確認し、**[次へ]** を選択します。 ユーザーがアップロードされ、アクティブなユーザーの一覧に追加されます。

> [!NOTE]
> 管理対象のデバイスを登録するまで、ユーザーは Intune に表示されません。

次に Intune に移動し、ユーザー、そのデバイス、そのアプリの管理を開始します。

## <a name="keeping-the-admin-experiences-straight"></a>管理者の経験を続ける
### <a name="classic-intune"></a>クラシック Intune
クラシック Intune で使用するポータルは 2 つあります。
- Office 365 管理センター ([portal.office.com](https://portal.office.com))
- Intune 管理コンソール ([manage.microsoft.com](https://manage.microsoft.com))

通常、次に示すように、Intune 管理コンソールで作業します。 これがグループ、ポリシー、デバイス、アプリを設定し、管理する場所となります。

![Intune 管理コンソールの画像](./media/sign-up/intune-admin-console.png)

ただし、次に示すように、ユーザーを追加したり、ユーザーやアカウントのその他の設定 (請求やサポートなど) を管理したりするときは、Office 365 管理センターを利用します。

![Office 365 管理センターの画像](./media/sign-up/office-admin-center.png)

Office 365 管理センターから Intune 管理コンソールに移動できます。 管理センターは、左のナビゲーション ウィンドウの最後の項目の下にあります。 **[Intune]** を選択し、新しいタブで Intune 管理コンソールを開きます。

![Intune 管理コンソールへのリンクの画像](./media/sign-up/link-to-intune.png)

Intune から Office 365 管理センターに戻るには、[グループの概要] ページで [**ユーザーの追加**] タスクを選択します。

![Office 365 管理センターに戻るリンクの画像](./media/sign-up/task-add-users.png)

### <a name="intune-azure-preview"></a>Intune Azure プレビュー
Intune Azure プレビューで使用するポータルは 3 つあります。
- Office 365 管理センター ([portal.office.com](https://portal.office.com))
- Azure の Intune ダッシュボード ([portal.azure.com](https://portal.azure.com))
- クラシック Intune 管理コンソール ([manage.microsoft.com](https://manage.microsoft.com))

Azure で Intune に初めてサインインすると、Azure ダッシュボードに表示されないことがあります。 Intune サービスを Azure ダッシュボードに追加するには:
1. ダッシュボードの左にある Azure サービスの一覧で **[その他のサービス >]** を選択し、検索ボックスに「Intune」と入力します。
2. 一覧から **[Intune]** を選択し、星を選択してサービスの一覧にサービスを追加します。<br/> ![サービス一覧から Intune を選択する画像](./media/sign-up/azure-add-intune1.png)
3. サービス一覧から **[Intune]** を選択し、Intune ダッシュボードを開きます。

通常、次のように、Intune ダッシュボードで作業します。 これがグループ、ポリシー、デバイス、アプリを設定し、管理する場所となります。 ダッシュボードからクラシック Intune 管理コンソールを開くには、**[クラシック Intune ポータルを開く]** タイルを選択します。 Intune Azure プレビューに戻るには、ブラウザーのアドレス バーに「https://portal.azure.com」と入力し、サービス一覧から **[Intune]** をもう一度選択します。

 ![Intune ダッシュボードの画像](./media/sign-up/intune-azure-dashboard.png)


ただし、次に示すように、ユーザーを追加したり、ユーザーやアカウントのその他の設定 (請求やサポートなど) を管理したりするときは、Office 365 管理センターを利用します。

![Office 365 管理センターの画像](./media/sign-up/office-admin-center.png)

Office 365 管理センターから Intune ダッシュボードに移動するには、ブラウザーのアドレス バーに「https://portal.azure.com」と入力します。 サービス一覧から **[Intune]** を選択します。

Intune から Office 365 管理センターに戻るには、ブラウザーのアドレス バーに「https://portal.office.com」と入力します。 既に Intune にログインしている場合は、Office 365 管理センターがそのまま表示されます。

## <a name="next-steps"></a>次のステップ
### <a name="classic-intune"></a>クラシック Intune
評価シナリオ: [Microsoft Intune でモバイル デバイス管理を評価する](mobile-device-management-trial-guide-microsoft-intune.md)

### <a name="intune-azure-preview"></a>Intune Azure プレビュー
詳細については、「[Intune in the Azure portal preview](/intune/what-is-intune)」(Azure プレビュー ポータルの Intune) を参照してください。

### <a name="integration-with-other-products"></a>他の製品との統合
Intune で Azure Active Directory ユーザー アカウントを使用する方法に関するページ:
- [ID の要件](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [ディレクトリ同期の要件](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [多要素認証の要件](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

[Intune と System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management) を使用する方法に関するページ

