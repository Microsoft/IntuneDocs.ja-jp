---
# required metadata

title: Managed Browser のポリシーを使用したインターネット アクセスの管理 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune と Managed Browser のポリシーを使用したインターネット アクセスの管理
Managed Browser は、Microsoft Intune を使用して組織で展開できる、Web を参照するためのアプリケーションです。 Managed Browser ポリシーは、Managed Browser のユーザーがアクセスできる Web サイトを制限する許可リストまたはブロック リストを構成するものです。

このアプリは管理対象アプリであるため、切り取り、コピー、貼り付けの使用の制御、画面のキャプチャの防止、ユーザーがクリックしたコンテンツへのリンクのみが他の管理対象アプリで開かれるようにすることなど、さまざまなモバイル アプリケーション管理ポリシーをこのアプリにも適用できます。 詳細については、「[Microsoft Intune でモバイル アプリケーション管理ポリシーを使用してデータを保護する](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)」を参照してください。.

> [!IMPORTANT]
>ユーザーがアプリ ストアから Managed Browser をインストールし、それが Intune で管理されていない場合は、次の動作が適用されます。
iOS - Managed Browser アプリを基本的な Web ブラウザーとして使用できますが、一部の機能が使用できません。また、他の Intune で管理されたアプリのデータにアクセスできません。
Android - Managed Browser アプリは使用できません。
ユーザーが iOS 9 よりも前のバージョンが動作する iOS デバイスに自分で Managed Browser をインストールした場合は、作成したポリシーで管理されません。 ブラウザーを確実に Intune で管理するには、ユーザーにアプリをアンインストールしてもらってから、管理対象アプリとして展開する必要があります。 iOS 9 以降では、ユーザーが自分で Managed Browser をインストールした場合、ポリシーで管理することを許可するように求められます。

次の種類のデバイス用に Managed Browser のポリシーを作成することができます。

-   Android 4 以降が実行されているデバイス

-   iOS 7.1 以降を実行するデバイス

Intune Managed Browser では、[Microsoft Intune アプリケーション パートナー](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)から Web コンテンツを開くことができます。.

## Managed Browser のポリシーを作成する

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** &gt; **[ポリシーの追加]** をクリックします。.

2.  次のいずれかの種類の **ソフトウェア** ポリシーを構成します。

    -   **Managed Browser のポリシー (Android 4 以降)**

    -   **Managed Browser のポリシー (iOS 7.1 以降)**

    ポリシーの作成および展開方法の詳細については、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)」トピックを参照してください。

3.  次の表を参考に、Managed Browser のポリシーの設定を構成してください。

|設定の名前|説明|
    |----------------|--------------------|
    |**名前**|Intune コンソール内で容易に識別できるように、Managed Browser ポリシーの一意の名前を入力します。|
    |**説明**|Managed Browser ポリシーの概要や、Managed Browser ポリシーを特定するのに役立つその他の関連情報についての説明を入力します。|
    |**Managed Browser で開くことができる URL を許可リストまたはブロック リストで制限できるようにする**|次のいずれかのオプションを選択します。<br /><br />**Managed Browser が以下に示す URL のみを開けるようにする**: Managed Browser で開くことができる URL の一覧を指定します。<br /><br />**Managed Browser が以下に示す URL を開けないようにする**: Managed Browser で開けないようにブロックする URL の一覧を指定します。 **注:** 同じ Managed Browser ポリシーに、許可される URL とブロックされる URL の両方を含めることはできません。<br />指定できる URL の形式の詳細については、このトピックの「**許可される URL とブロックされる URL の形式**」をご覧ください。|

4.  終了したら、**[ポリシーの保存]** をクリックします。.

**[ポリシー]** ワークスペースの **[構成ポリシー]** ノードに新しいポリシーが表示されます。

## Managed Browser アプリ向けに展開を作成する
Managed Browser ポリシーの作成後、Managed Browser アプリ向けにソフトウェアの展開を作成し、作成した Managed Browser ポリシーに関連付けることができます。

> [!IMPORTANT]
> Managed Browser ポリシーの展開方法は、他の Intune ポリシーとは異なります。 この種類のポリシーは、Managed Browser ソフトウェア パッケージに関連付ける必要があります。

アプリを展開し、必ず **[モバイル アプリの管理]** ページで Managed Browser ポリシーを選択してそのポリシーをアプリに関連付けます。

アプリの展開方法の詳細については、「[Deploy apps in Microsoft Intune (Microsoft Intune でアプリを展開する)](deploy-apps-in-microsoft-intune.md)」を参照してください。.

## Managed Browser のセキュリティとプライバシー

-   iOS デバイスでは、証明書の有効期限が切れている Web サイトや証明書が信頼されていない Web サイトにユーザーがアクセスしても、開くことができません。

-   ユーザーが自分のデバイスの組み込みブラウザーに対して構成した設定は、Managed Browser では使用されません。 これは、Managed Browser がこれらの設定にアクセスできないためです。

-   Managed Browser に関連付けられているモバイル アプリケーション管理ポリシーで **[アクセスの際にシンプルな PIN を要求する]** オプションか **[アクセスの際に会社の資格情報を要求する]** オプションが構成されている場合は、ユーザーが認証ページのヘルプ リンクをクリックすると、Managed Browser ポリシーのブロック リストに追加されているかどうかに関係なく、ユーザーはすべてのインターネット サイトを参照することができます。

-   Managed Browser では、直接アクセスされたときのみ、サイトへのアクセスをブロックできます。 サイトへのアクセスに中間サービス (翻訳サービスなど) が使用されている場合は、アクセスをブロックすることができません。

-   認証を許可し、Intune のドキュメントにアクセスできるようにするため、**&#42;.microsoft.com** は許可リストとブロック リストの設定から除外されており、常に許可されます。

### 使用状況データをオフにする
Microsoft は、Microsoft の製品やサービスを改善するために、Managed Browser のパフォーマンスおよび使用に関する匿名データを自動的に収集します。ただし、ユーザーはデバイスの**使用状況データ**設定を使用して、データの収集を無効にすることができます。 このデータの収集方法は制御できません。

## 参照情報

### 許可される URL とブロックされる URL の形式
許可リストとブロック リストで URL を指定するときに使用できる形式とワイルドカードについて説明します。

-   ワイルドカード記号 "**&#42;**" は、以下の許可されているパターン リストの規則に従って使用できます。

-   リストに入力するときは、すべての URL の先頭に必ず **http** または **https** を付けてください。

-   アドレスにはポート番号を指定できます。 ポート番号を指定しない場合は、次の値が使用されます。

    -   http の場合はポート 80

    -   https の場合はポート 443

    **http://www.contoso.com:*;** や **http://www.contoso.com:/* のように、ポート番号にワイルドカードを使用することはできません。;**

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

### 許可リストとブロック リストの競合を解決する方法
複数の Managed Browser ポリシーがデバイスに展開され、設定が競合する場合、モード (許可またはブロック) と URL の一覧の両方が競合していると判断されます。 競合が発生した場合は、次の動作が適用されます。

-   各ポリシーのモードは同じで、URL の一覧が異なる場合、URL はデバイスに適用されません。

-   各ポリシーのモードが異なり、URL の一覧は同じである場合、URL はデバイスに適用されません。

-   デバイスが初めて Managed Browser ポリシーを受信するときに、2 つのポリシーが競合する場合、URL はデバイスに適用されません。 **[ポリシー]** ワークスペースの **[ポリシーの競合]** ノードを使用して、競合を表示します。

-   デバイスが Managed Browser ポリシーを既に受信していて、2 番目のポリシーが競合する設定で展開される場合、元の設定がデバイスに残ります。 **[ポリシー]** ワークスペースの **[ポリシーの競合]** ノードを使用して、競合を表示します。


<!--HONumber=May16_HO1-->


