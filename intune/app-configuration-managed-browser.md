---
title: "Managed Browser アプリで Web アクセスを管理する"
titlesuffix: Azure portal
description: "Managed Browser アプリケーションを展開して、Web 閲覧と他のアプリケーションへの Web データ転送を制限します。"
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 11/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7619efc305881f1ad56a7c14e5d92c05fb0c6d77
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>Microsoft Intune で Managed Browser ポリシーを使ってインターネット アクセスを管理する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Managed Browser は、公開アプリ ストアからダウンロードできる、組織内で使用するための Web 閲覧アプリです。 Intune で構成されている場合、Managed Browser では次の管理が可能です。
- Web データを保護した状態で、企業サイトにアクセスしたり、MyApps サービスを通してシングル サインオンで SaaS アプリにアクセスしたりできる。
- URL とドメインの一覧を使用して事前構成し、企業コンテキスト内でユーザーがアクセスできるサイトを制限することができる。
- ホームページ、および指定したブックマークを使用して事前定義できる。

このアプリは Intune SDK と統合されているため、次のようなアプリ保護ポリシーを適用することもできます。
- 切り取り、コピー、貼り付けの使用をコントロールする
- 画面の取り込みを禁止する
- ユーザーが選択したコンテンツへのリンクのみを他の管理対象アプリで開けるようにする

詳細については、「[アプリ保護ポリシーとは](/intune/app-protection-policy)」を参照してください。

これらの設定は以下のものに適用できます。

- Intune に登録されたデバイス
- 別の MDM 製品に登録されたデバイス
- 管理されていないデバイス

ユーザーがアプリ ストアから Managed Browser をインストールし、それを Intune で管理していない場合は、Microsoft MyApps サイトを通したシングル サインオンをサポートする通常の Web ブラウザーとして使用できます。 ユーザーは直接 MyApps サイトにアクセスし、プロビジョニングされた SaaS アプリケーションのすべてを表示できます。
Managed Browser が Intune で管理されていない場合、Intune で管理されている他のアプリケーションのデータにアクセスすることはできません。 

Managed Browser では、Secure Sockets Layer バージョン 3 (SSLv3) 暗号化プロトコルをサポートしません。

Managed Browser のポリシーを作成できるのは、以下のデバイスです。

-   Android 4 以降が実行されているデバイス

-   iOS 8.0 以降を実行するデバイス

>[!IMPORTANT]
>2017 年 10 月の時点で、Android アプリで使用する Intune Managed Browser アプリは、Android 4.4 以降を実行しているデバイスのみをサポートします。 iOS の Intune Managed Browser アプリは、iOS 9.0 以降を実行しているデバイスのみをサポートします。
>以前のバージョンの Android および iOS は、Managed Browser の使用を続けることができますが、新しいバージョンのアプリをインストールすることはできません。また、アプリのすべての機能にアクセスできるとは限りません。 サポートされるオペレーティング システム バージョンにこれらのデバイスを更新することをお勧めします。


Intune Managed Browser では、[Microsoft Intune アプリケーション パートナー](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx)から Web コンテンツを開くことができます。

## <a name="create-a-managed-browser-app-configuration"></a>Managed Browser アプリの構成を作成する

1.  Azure ポータルにサインインします。
2.  **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3.  [管理] リストの **[アプリの構成]** ブレードで、**[アプリ構成ポリシー]** を選択します。
4.  **[アプリ構成ポリシー]** ブレードで **[追加]** を選択します。
5.  **[アプリの構成を追加する]** ブレードで **[名前]** に入力し、必要に応じてアプリ構成設定の **[説明]** に入力します。
6.  **[デバイス登録の種類]** には、**[管理対象アプリ]** を選択します。
7.  **[必要なアプリの選択]** を選択して、**[対象アプリ]** ブレードで、iOS、Android、またはその両方に **[Managed Browser]** を選択します。
8.  **[OK]** を選択し、**[アプリの構成を追加する]** ブレードに戻ります。
9.  **[構成の設定]** を選択します。 **[構成]** ブレードで、Managed Browser の構成を指定するキーと値のペアを定義します。 定義できる別のキーと値のペアについては、この記事の後半のセクションで説明します。
10. 終了したら、**[OK]** を選択します。
11. **[アプリの構成を追加する]** ブレードで、**[作成]** を選択します。
12. 新しい構成が作成され、**[アプリの構成]** ブレードに表示されます。

>[!IMPORTANT]
>現在、Managed Browser は、自動登録に依存しています。 デバイス上の別のアプリケーションに適用するアプリの構成については、既に Intune アプリの保護ポリシーで管理されている必要があります。

## <a name="assign-the-configuration-settings-you-created"></a>作成した構成設定を割り当てる

設定をユーザーの Azure AD グループに割り当てます。 ユーザーが Managed Browser アプリをインストールしている場合、そのアプリは指定された設定で管理されます。

1. Intune モバイル アプリケーション管理ダッシュボードの **[設定]** ブレードで、**[アプリの構成]** を選択します。
2. アプリの構成の一覧から、割り当てる構成を選択します。
3. 次のブレードで、**[ユーザー グループ]** を選択します。
4. **[ユーザー グループ]** ブレードで、アプリの構成を割り当てる Azure AD グループを選択し、**[OK]** を選択します。


## <a name="how-to-configure-application-proxy-settings-for-the-managed-browser"></a>Managed Browser のアプリケーション プロキシ設定を構成する方法

Intune Managed Browser と [Azure AD アプリケーション プロキシ]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)は、iOS および Android デバイスのユーザーに対して、次のシナリオをサポートするために一緒に使用することができます。

- ユーザーがダウンロードして、Microsoft Outlook アプリにサインインします。 Intune アプリの保護ポリシーが自動的に適用されます。 保護ポリシーでは、保存されたデータを暗号化し、ユーザーが企業ファイルを管理されていないアプリまたはデバイス上の場所に転送できないようにします。 ユーザーが Outlook 内のイントラネット サイトへのリンクをクリックすると、そのリンクを別のブラウザーではなく、Managed Browser アプリ内で開くように指定することができます。 Managed Browser は、このイントラネット サイトがアプリケーション プロキシを使用してユーザーに公開されていることを認識します。 ユーザーは、適用される多要素認証で認証するためにアプリケーション プロキシを使い、イントラネット サイトに到達する前に条件付きアクセスを使って自動的にルーティングされます。 このサイトは、ユーザーがリモートにいるときに、以前は見つけることができませんでしたが、アクセスできるようになり、Outlook のリンクが期待どおりに動作するようになりました。
- リモート ユーザーが Managed Browser アプリケーションを開き、内部 URL を使用してイントラネット サイトに移動します。 Managed Browser は、このイントラネット サイトがアプリケーション プロキシ経由でユーザーに公開されていることを認識します。 ユーザーは、適用される多要素認証で認証するためにアプリケーション プロキシを使い、イントラネット サイトに到達する前に条件付きアクセスを使って自動的にルーティングされます。 このサイトは、ユーザーがリモートにいるときに、以前は見つけることができませんでしたが、アクセスできるようになりました。

### <a name="before-you-start"></a>開始する前に

- Azure AD アプリケーション プロキシ経由の内部アプリケーションをセットアップします。
    - アプリケーション プロキシを構成し、アプリケーションを公開するには、[セットアップに関するドキュメント]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started#how-to-get-started)を参照してください。 
- Managed Browser アプリの最小バージョン 1.2.0 を使用する必要があります。
- Managed Browser アプリのユーザーは、[Intune アプリの保護ポリシー]( app-protection-policy.md)をアプリに割り当てています。
注: Managed Browser に最新のアプリケーション プロキシのリダイレクト データが反映されるまでには、最長で 24 時間かかります。

#### <a name="step-1-enable-automatic-redirection-to-the-managed-browser-from-outlook"></a>ステップ 1: Outlook から Managed Browser への自動リダイレクトを有効にする
Outlook は、アプリ保護ポリシーの **[Managed Browser に表示する Web コンテンツを制限する]** 設定を有効にして構成される必要があります。

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-managed-browser"></a>ステップ 2: Managed Browser に割り当てられたアプリ構成ポリシーを割り当てる
この手順では、アプリ プロキシのリダイレクトを使用するように、Managed Browser アプリを構成します。 Managed Browser アプリの構成を作成する手順に従い、以下のキーと値のペアを指定します。

|||
|-|-|
|キー|値|
|**com.microsoft.intune.mam.managedbrowser.AppProxyRedirection**|**true**|


## <a name="how-to-configure-the-homepage-for-the-managed-browser"></a>Managed Browser のホームページを構成する方法

この設定では、ユーザーが Managed Browser を開始するか、新しいタブを作成したときに表示するホームページを構成することができます。Managed Browser アプリの構成を作成する手順に従い、以下のキーと値のペアを指定します。

|||
|-|-|
|キー|値|
|**com.microsoft.intune.mam.managedbrowser.homepage**|有効な URL を指定します。 セキュリティ対策のため、誤った URL はブロックされます。<br>例: **https://www.bing.com**|


## <a name="how-to-configure-bookmarks-for-the-managed-browser"></a>Managed Browser のブックマークを構成する方法

この設定では、Managed Browser のユーザーが使用できるブックマークのセットを構成できます。

- これらのブックマークは、ユーザーが削除または変更することはできません。
- これらのブックマークは、リストの上部に表示されます。 ユーザーが作成したブックマークは、これらのブックマークの下に表示されます。
- アプリ プロキシのリダイレクトを有効にした場合は、内部 URL または外部 URL を使用してアプリ プロキシ Web アプリを追加できます。

Managed Browser アプリの構成を作成する手順に従い、以下のキーと値のペアを指定します。

|||
|-|-|
|キー|値|
|**com.microsoft.intune.mam.managedbrowser.bookmarks**|この構成の値は、ブックマークのリストです。 各ブックマークは、ブックマークのタイトルとブックマークの URL で構成されます。 タイトルおよび URL は、**&#124;** の文字で区切ります。<br><br>例: **Microsoft Bing&#124;https://www.bing.com**<br><br>複数のブックマークを構成するには、二重の文字 **&#124;&#124;** で各ペアを区切ります。<br><br>例: **Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com**|

## <a name="how-to-specify-allowed-and-blocked-urls-for-the-managed-browser"></a>Managed Browser で許可する URL とブロックする URL を指定する方法

Managed Browser アプリの構成を作成する手順に従い、以下のキーと値のペアを指定します。

|||
|-|-|
|キー|値|
|次の中から選択します。<br><br>- 許可された URL を指定する場合 (ここで指定した URL のみが許可され、他のサイトにはアクセスできない): **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br>- ブロックされた URL を指定する場合 (その他のすべてのサイトにアクセスできる): <br><br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**|キーに対応する値は URL のリストです。 パイプ文字 **&#124;** によって区切られた、1 つの値として許可またはブロックする必要がある、すべての URL を入力します。<br><br>例:<br><br>**URL1&#124;URL2&#124;URL3**<br>**http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com**|

>[!IMPORTANT]
>両方のキーを指定しないでください。 両方のキーが同じユーザーを対象とする場合、許可のキーが最も制限の厳しいオプションとして使用されます。
>また、会社の Web サイトなど、重要なページをブロックしないようにご注意ください。

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
|http://www.contoso.com:80|ポート番号を使用し、単一のページと一致する|http://www.contoso.com:80|
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

## <a name="how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios"></a>iOS で Managed Browser を使用し、管理対象アプリ ログにアクセスする方法

iOS デバイスに Managed Browser をインストールしているエンド ユーザーは、Microsoft が公開しているすべてのアプリの管理ステータスを表示できます。 管理対象 iOS アプリの問題を解決するためにログを送信できます。

1. iOS の **[設定]** を開きます。
2. **Managed Browser** のアプリケーション設定を選択します。
3. **[Intune 診断の有効化]** を切り替え、ブラウザーをトラブルシューティング モードに設定します。
4. **Managed Browser** を開きます。 **[Intune アプリの状態を表示]** をクリックし、個々のアプリケーション ポリシー設定を確認します。
5. **[開始]** と **[ログの共有]** または **[Microsoft にログを送信]** を押し、IT 管理者または Microsoft にトラブルシューティング ログを送信します。

アプリ内からブラウザーをトラブルシューティング モードで開くこともできます。

1. Managed Browser を開きます。
2. アドレス バー「`about:intunehelp`」と入力します。
ブラウザーがトラブルシューティング モードで起動します。

アプリ ログに格納されている設定の一覧については、「[Managed Browser 内のアプリの保護ログのレビュー](app-protection-policy-settings-log.md)」を参照してください。

## <a name="security-and-privacy-for-the-managed-browser"></a>Managed Browser のセキュリティとプライバシー

-   ユーザーが自分のデバイスの組み込みブラウザーに対して構成した設定は、Managed Browser では使用されません。 Managed Browser では、これらの設定にアクセスできません。

-   Managed Browser に関連付けられているアプリ保護ポリシーにオプション **[アクセスの際にシンプルな PIN を要求する]** または **[アクセスの際に会社の資格情報を要求する]** を設定した場合、およびユーザーが認証ページでヘルプのリンクを選択した場合は、ポリシーのブロック リストに追加されているかどうかにかかわらず、インターネット サイトを参照できます。

-   Managed Browser では、サイトへの直接のアクセスのみをブロックできます。 中間サービス (翻訳サービスなど) がサイトへのアクセスに使用される場合、そのアクセスはブロックされません。

-   認証を許可し、Intune ドキュメントにアクセスするために、**&#42;.microsoft.com** は許可またはブロック リスト設定の対象から除外されます。 常に許可されます。

### <a name="turn-off-usage-data"></a>使用状況データをオフにする
Microsoft は、Microsoft の製品やサービスを改善するために、Managed Browser のパフォーマンスおよび使用に関する匿名データを自動的に収集します。 ただし、ユーザーはデバイスの **[使用状況データ]** 設定を使用して、データの収集を無効にすることができます。 このデータの収集方法は制御できません。


-   iOS デバイスでは、証明書の有効期限が切れている Web サイトや証明書が信頼されていない Web サイトにユーザーがアクセスしても、開くことができません。
-   ユーザーが自分のデバイスの組み込みブラウザーに対して構成した設定は、Managed Browser では使用されません。 Managed Browser では、これらの設定にアクセスできません。

-   Managed Browser に関連付けられているアプリ保護ポリシーにオプション **[アクセスの際にシンプルな PIN を要求する]** または **[アクセスの際に会社の資格情報を要求する]** を設定した場合、およびユーザーが認証ページでヘルプのリンクを選択した場合は、ポリシーのブロック リストに追加されているかどうかにかかわらず、インターネット サイトを参照できます。

-   Managed Browser では、サイトへの直接のアクセスのみをブロックできます。 中間サービス (翻訳サービスなど) がサイトへのアクセスに使用される場合、そのアクセスはブロックされません。

-   認証を許可し、Intune ドキュメントにアクセスするために、**&#42;.microsoft.com** は許可またはブロック リスト設定の対象から除外されます。 常に許可されます。

### <a name="turn-off-usage-data"></a>使用状況データをオフにする
Microsoft は、Microsoft の製品やサービスを改善するために、Managed Browser のパフォーマンスおよび使用に関する匿名データを自動的に収集します。 ただし、ユーザーはデバイスの **[使用状況データ]** 設定を使用して、データの収集を無効にすることができます。 このデータの収集方法は制御できません。
