---
title: "Managed Browser アプリで Web アクセスを管理する"
titleSuffix: Intune on Azure
description: "Managed Browser アプリケーションを展開して、Web 閲覧と他のアプリケーションへの Web データ転送を制限します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 7db72e25c8ba5846a50989b17d2c7adfb6f1c44e
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>Microsoft Intune での Managed Browser のポリシーを使用したインターネット アクセスの管理

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Managed Browser は、パブリック アプリ ストアからダウンロードできる、組織内で使用するための Web 閲覧アプリです。 Intune では Managed Browser を使用することで、Web データを保護した状態で、企業サイトにアクセスしたり、MyApps サービスを通してシングル サインオンで SaaS アプリにアクセスしたりできます。 さらに、URL とドメインの一覧を使用して Managed Browser を事前構成し、企業コンテキスト内でユーザーがアクセスできるサイトを制限することもできます。

このアプリは Intune SDK と統合されているので、アプリ保護ポリシーを適用することもできます。 これらのポリシーでは、切り取り、コピー、貼り付けの使用を制御したり、画面のキャプチャを禁止したり、ユーザーが選択したコンテンツへのリンクのみを他の管理対象アプリで開けるようにしたりします。 詳細については、「[アプリ保護ポリシーとは](/intune/app-protection-policy)」をご覧ください。
これらの設定は、Intune に登録されているデバイスや別のデバイス管理製品に登録されているデバイスに適用できるほか、一切管理されていないデバイスにも適用できます。

>[!IMPORTANT]
>Managed Browser アプリは、デバイス上の別のアプリがアクセス保護ポリシーを取得した場合にのみ、Intune アクセス保護ポリシーを取得して適用します。<br><br> 

ユーザーがアプリ ストアから Managed Browser をインストールし、それを Intune で管理していない場合は、Microsoft MyApps サイトを通したシングル サインオンをサポートする通常の Web ブラウザーとして使用できます。 ユーザーは直接 MyApps サイトにアクセスし、プロビジョニングされた SaaS アプリケーションのすべてを表示できます。
Managed Browser が Intune で管理されていない場合、Intune で管理されている他のアプリケーションのデータにアクセスすることはできません。 


Managed Browser のポリシーを作成できるのは、以下のデバイスです。

-   Android 4 以降が実行されているデバイス

-   iOS 8.0 以降を実行するデバイス

Intune Managed Browser では、[Microsoft Intune アプリケーション パートナー](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx)から Web コンテンツを開くことができます。

## <a name="create-a-managed-browser-app-configuration"></a>Managed Browser アプリの構成を作成する

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune アプリ保護]** の順に選択します。
3. Intune モバイル アプリケーション管理ダッシュボードの **[設定]** ブレードで、**[アプリの構成]** を選択します。
4. **[アプリの構成]** ブレードで、**[構成の追加]** を選択します。
5. **[アプリの構成を追加する]** ブレードで **[名前]** に入力し、必要に応じてアプリ構成設定の **[説明]** に入力します。
5. **[必要なアプリの選択]** を選択した後、**[対象アプリ]** ブレードで、iOS 用、Android 用、またはその両方の **Managed Browser** を選択します。
6. **[OK]** を選択し、**[アプリの構成を追加する]** ブレードに戻ります。
7. **[構成の定義]** を選択します。 **[構成]** ブレードで、Managed Browser の構成を指定するキーと値のペアを定義します。
定義できる別のキーと値のペアについては、このトピックの後半のセクションで説明します。
8. 終了したら、 **[OK]**をクリックします。
9. **[アプリの構成を追加する]** ブレードで、**[作成]** を選択します。
10. 新しい構成が作成され、**[アプリの構成]** ブレードに表示されます。




## <a name="assign-the-configuration-settings-you-created"></a>作成した構成設定を割り当てる

設定をユーザーの Azure AD グループに割り当てます。 そのユーザーが Managed Browser アプリをインストールしていれば、そのアプリは指定された設定で管理されます。

1. Intune モバイル アプリケーション管理ダッシュボードの **[設定]** ブレードで、**[アプリの構成]** を選択します。
2. アプリの構成の一覧から、割り当てる構成を選択します。
3. 次のブレードで、**[ユーザー グループ]** を選択します。
4. **[ユーザー グループ]** ブレードで、アプリの構成を割り当てる Azure AD グループを選択し、**[OK]** を選択します。


## <a name="how-to-specify-allowed-and-blocked-urls-for-the-managed-browser"></a>Managed Browser で許可する URL とブロックする URL を指定する方法

Managed Browser アプリの構成を作成する手順に従い、以下のキーと値のペアを指定します。

### <a name="key"></a>キー

次の中から選択します。

- 許可する URL を指定する場合 (ここで指定した URL にのみアクセスでき、他のサイトにはアクセスできない): **com.microsoft.intune.mam.managedbrowser.AllowListURLs**
- ブロックする URL を指定する場合 (他のサイトにはすべてアクセスできる): **com.microsoft.intune.mam.managedbrowser.BlockListURLs**

>[!IMPORTANT]
>両方のキーを指定しないでください。 両方のキーが同じユーザーを対象とする場合、許可のキーが最も制限の厳しいオプションとして使用されます。
>また、会社の Web サイトなど、重要なページをブロックしないようにご注意ください。

### <a name="value"></a>値

キーに対応する値は URL のリストです。 許可またはブロック対象のすべての URL をパイプ **|** で区切り、単一の値として入力します。

例: 

- **URL1|URL2|URL3**
- **http://*.contoso.com/*|https://*.bing.com/*|https://expenses.contoso.com**

使用できる URL 形式の例について詳しくは、このトピックの参照情報セクションをご覧ください。


## <a name="security-and-privacy-for-the-managed-browser"></a>Managed Browser のセキュリティとプライバシー

-   iOS デバイスでは、証明書の有効期限が切れている Web サイトや証明書が信頼されていない Web サイトにユーザーがアクセスしても、開くことができません。

-   ユーザーが自分のデバイスの組み込みブラウザーに対して構成した設定は、Managed Browser では使用されません。 これは、Managed Browser がこれらの設定にアクセスできないためです。

-   Managed Browser に関連付けられているモバイル アプリケーション管理ポリシーで **[アクセスの際にシンプルな PIN を要求する]** オプションか **[アクセスの際に会社の資格情報を要求する]** オプションが構成されている場合は、ユーザーが認証ページのヘルプ リンクを選択すると、Managed Browser ポリシーのブロック リストに追加されているかどうかに関係なく、ユーザーはすべてのインターネット サイトを閲覧することができます。

-   Managed Browser では、サイトへの直接のアクセスのみをブロックできます。 サイトへのアクセスに中間サービス (翻訳サービスなど) が使用されている場合は、アクセスをブロックすることができません。

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



