---
title: "Managed Browser で Web アクセスを管理する |Microsoft Docs"
description: "Managed Browser アプリケーションを展開して、Web 閲覧と他のアプリへの Web データ転送を制限します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 49ad005846265deb7d4b34b52a1c139e8f61372b
ms.contentlocale: ja-jp
ms.lasthandoff: 05/31/2017


---

# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>Microsoft Intune と Managed Browser のポリシーを使用したインターネット アクセスの管理

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Managed Browser は、Microsoft Intune を使用して組織で展開できる、Web を参照するためのアプリケーションです。 Managed Browser ポリシーは、Managed Browser のユーザーがアクセスできる Web サイトを制限する許可リストまたはブロック リストを構成するものです。

このアプリは Intune SDK と統合されているので、アプリ保護ポリシーを適用することもできます。 これらのポリシーでは、切り取り、コピー、貼り付けの使用を制御したり、画面のキャプチャを禁止したり、ユーザーが選択したコンテンツへのリンクのみを他の管理対象アプリで開けるようにしたりします。 詳細については、「[Microsoft Intune コンソールでモバイル アプリケーション管理ポリシーを構成して展開する](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)」で説明されている方法を参照してください。

>[!IMPORTANT]
>Managed Browser アプリは、デバイス上の別のアプリがアクセス保護ポリシーを取得した場合にのみ、Intune アクセス保護ポリシーを取得して適用します。<br><br> また、ユーザーがアプリ ストアから Managed Browser をインストールし、それが Intune で管理されていない場合は、次の動作が適用されます。<br /><br />
>**iOS** - Managed Browser アプリを基本的な Web ブラウザーとして使用できますが、一部の機能が使用できません。また、他の Intune で管理されたアプリのデータにアクセスできません。<br />
**Android** - Managed Browser アプリは使用できません。<br /><br />
ユーザーが iOS 9 よりも前のバージョンが搭載された iOS デバイスに自分で Managed Browser をインストールした場合は、作成したポリシーで管理されません。 ブラウザーを Intune で確実に管理するには、ユーザーにアプリをアンインストールしてもらった後に、管理対象アプリとして展開する必要があります。 iOS 9 以降では、ユーザーは自分で Managed Browser をインストールした場合、それがポリシーの管理対象となることを認めるように求められます。

次の種類のデバイス用に Managed Browser のポリシーを作成することができます。

-   Android 4 以降が実行されているデバイス

-   iOS 8.0 以降を実行するデバイス

Intune Managed Browser では、[Microsoft Intune アプリケーション パートナー](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx)から Web コンテンツを開くことができます。

## <a name="create-a-managed-browser-policy"></a>Managed Browser のポリシーを作成する

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** &gt; **[ポリシーの追加]** を選択します。

2.  次のいずれかの種類の **ソフトウェア** ポリシーを構成します。

    -   **Managed Browser (Android 4 以降)**

    -   **Managed Browser (iOS 8.0 以降)**

    ポリシーの作成および展開方法の詳細については、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)」トピックを参照してください。

3.  次を参考に、Managed Browser のポリシーの設定を構成してください。

    - **名前**。 Intune コンソール内で容易に識別できるように、Managed Browser ポリシーの一意の名前を入力します。
    - **説明**。 Managed Browser ポリシーの概要や、Managed Browser ポリシーを特定するのに役立つその他の関連情報についての説明を入力します。
    - **Managed Browser で開くことができる URL を許可リストまたはブロック リストで制限できるようにする**。 次のいずれかのオプションを選択します。
        - **管理対象ブラウザーで以下のリストにある URL だけを開くことを許可**。 Managed Browser で開くことができる URL のリストを指定します。
        - **Managed Browser で以下のリストにある URL を開くことを禁止**。 Managed Browser で開くことができないようにする URL のリストを指定します。
**注:** 同じ Managed Browser ポリシーに、許可される URL とブロックされる URL の両方を含めることはできません。
指定できる URL の形式の詳細については、このトピックの「**許可される URL とブロックされる URL の形式**」をご覧ください。

4.  終了したら、**[ポリシーの保存]** を選びます。

**[ポリシー]** ワークスペースの **[構成ポリシー]** ノードに新しいポリシーが表示されます。

## <a name="create-a-deployment-for-the-managed-browser-app"></a>Managed Browser アプリ向けに展開を作成する
Managed Browser ポリシーの作成後、Managed Browser アプリ向けにソフトウェアの展開を作成し、作成した Managed Browser ポリシーに関連付けることができます。

> [!IMPORTANT]
> Managed Browser ポリシーの展開方法は、他の Intune ポリシーとは異なります。 この種類のポリシーは、Managed Browser ソフトウェア パッケージに関連付ける必要があります。

アプリを展開し、必ず **[モバイル アプリの管理]** ページで Managed Browser ポリシーを選択してそのポリシーをアプリに関連付けます。

アプリの展開方法の詳細については、「[Microsoft Intune でアプリを展開する](deploy-apps-in-microsoft-intune.md)」を参照してください。

## <a name="security-and-privacy-for-the-managed-browser"></a>Managed Browser のセキュリティとプライバシー

-   iOS デバイスでは、証明書の有効期限が切れている Web サイトや証明書が信頼されていない Web サイトにユーザーがアクセスしても、開くことができません。

-   ユーザーが自分のデバイスの組み込みブラウザーに対して構成した設定は、Managed Browser では使用されません。 これは、Managed Browser がこれらの設定にアクセスできないためです。

-   Managed Browser に関連付けられているモバイル アプリケーション管理ポリシーで **[アクセスの際にシンプルな PIN を要求する]** オプションか **[アクセスの際に会社の資格情報を要求する]** オプションが構成されている場合は、ユーザーが認証ページのヘルプ リンクを選択すると、Managed Browser ポリシーのブロック リストに追加されているかどうかに関係なく、ユーザーはすべてのインターネット サイトを参照することができます。

-   Managed Browser では、直接アクセスされたときのみ、サイトへのアクセスをブロックできます。 サイトへのアクセスに中間サービス (翻訳サービスなど) が使用されている場合は、アクセスをブロックすることができません。

-   認証を許可し、Intune のドキュメントにアクセスできるようにするため、**&#42;.microsoft.com** は許可リストとブロック リストの設定から除外されており、 常に許可されます。

### <a name="turn-off-usage-data"></a>使用状況データをオフにする
Microsoft は、Microsoft の製品やサービスを改善するために、Managed Browser のパフォーマンスおよび使用に関する匿名データを自動的に収集します。 ただし、ユーザーはデバイスの **[使用状況データ]** 設定を使用して、データの収集を無効にすることができます。 このデータの収集方法は制御できません。

## <a name="reference-information"></a>参照情報

### <a name="url-format-for-allowed-and-blocked-urls"></a>許可される URL とブロックされる URL の形式
許可リストとブロック リストで URL を指定するときに使用できる形式とワイルドカードについて説明します。

-   ワイルドカード記号 (**&#42;**) は、以下の許可されているパターン リストの規則に従って使用できます。

-   リストに入力するときは、すべての URL の先頭に必ず **http** または **https** を付けてください。

-   アドレスにはポート番号を指定できます。 ポート番号を指定しない場合は、次の値が使用されます。

    -   http の場合はポート 80

    -   https の場合はポート 443

    ポート番号にワイルドカードを使用することはできません。 たとえば、**http&colon;//www&period;contoso&period;com:*;** や **http&colon;//www&period;contoso&period;com: /*;** はサポートされていません。

-   URL を指定するときに使用できるパターンの詳細については、次の表を参照してください。

|[URL]|説明|［一致する］|［次の値に一致しない］|
    |-------|---------------|-----------|------------------|
    |http://www.contoso.com|単一のページと一致する|www.contoso.com|host.contoso.com<br /><br />www.contoso.com/images<br /><br />contoso.com/|
    |http://contoso.com|単一のページと一致する|contoso.com/|host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com|
    |http://www.contoso.com/&#42;|www.contoso.com で始まるすべての URL と一致する|www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows|host.contoso.com<br /><br />host.contoso.com/images|
    |http://&#42;.contoso.com/&#42;|contoso.com の下のすべてのサブドメインに一致する|developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/videos|contoso.host.com|
    |http://www.contoso.com/images|単一のフォルダーと一致する|www.contoso.com/images|www.contoso.com/images/dogs|
    |http://www.contoso.com:80|ポート番号を使用し、単一のページと一致する|http://www.contoso.com:80||
    |https://www.contoso.com|セキュリティで保護された単一のページと一致する|https://www.contoso.com|http://www.contoso.com|
    |http://www.contoso.com/images/&#42;|1 つのフォルダーおよびすべてのサブフォルダーと一致する|www.contoso.com/images/dogs<br /><br />www.contoso.com/images/cats|www.contoso.com/videos|

-   指定することができない入力例を次に示します。

    -   &#42;.com

    -   &#42;.contoso/&#42;

    -   www.contoso.com/&#42;images

    -   www.contoso.com/&#42;images&#42;pigs

    -   www.contoso.com/page&#42;

    -   IP アドレス

    -   https://&#42;

    -   http://&#42;

    -   http://www.contoso.com:&#42;

    -   http://www.contoso.com: /&#42;

### <a name="how-conflicts-between-the-allow-and-block-list-are-resolved"></a>許可リストとブロック リストの競合を解決する方法
複数の Managed Browser ポリシーがデバイスに展開され、設定が競合する場合、モード (許可またはブロック) と URL の一覧の両方が競合していると判断されます。 競合が発生した場合は、次の動作が適用されます。

-   各ポリシーのモードは同じで、URL の一覧が異なる場合、URL はデバイスに適用されません。

-   各ポリシーのモードが異なり、URL の一覧は同じである場合、URL はデバイスに適用されません。

-   デバイスが初めて Managed Browser ポリシーを受信するときに、2 つのポリシーが競合する場合、URL はデバイスに適用されません。 **[ポリシー]** ワークスペースの **[ポリシーの競合]** ノードを使用して、競合を表示します。

-   デバイスが Managed Browser ポリシーを既に受信していて、2 番目のポリシーが競合する設定で展開される場合、元の設定がデバイスに残ります。 **[ポリシー]** ワークスペースの **[ポリシーの競合]** ノードを使用して、競合を表示します。

