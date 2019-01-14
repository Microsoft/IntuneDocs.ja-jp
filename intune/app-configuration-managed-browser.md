---
title: ポリシーで保護されたブラウザーを使用して Web アクセスを管理する
titlesuffix: Microsoft Intune
description: ポリシーで保護されたブラウザーを使用して、Web の閲覧や Web データ転送を制限します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 65f3598282bd46d422f8748d2653dbf8e18cf9b7
ms.sourcegitcommit: 874d9a00cc4666920069d54f99c6c2e687fa34a6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53324975"
---
# <a name="manage-internet-access-using-a-microsoft-intune-policy-protected-browser"></a>Microsoft Intune のポリシーで保護されたブラウザーを使用してインターネット アクセスを管理する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune ポリシーで保護されているブラウザー (Microsoft Edge または Intune Managed Browser) を使用して、企業の Web サイトが常にインプレースの保護付きでアクセスされるようにすることができます。  Intune を使用して構成されている場合、保護ブラウザーでは以下を利用します。

- アプリケーション保護ポリシー。
- 条件付きアクセス。
- シングル サインオン。
- アプリケーション構成設定。
- Azure アプリケーション プロキシの統合。

## <a name="getting-started"></a>はじめに

Microsoft Edge および Intune Managed Browser は、公開アプリ ストアからダウンロードできる、組織内で使用するための Web ブラウザー アプリです。 

ブラウザー ポリシーに対するオペレーティング システムの要件:
- Android 4 以降、または
- iOS 8.0 以降。

以前のバージョンの Android および iOS は、Managed Browser の使用を続けることができますが、新しいバージョンのアプリをインストールすることはできません。また、アプリのすべての機能にアクセスできるとは限りません。 サポートされるオペレーティング システム バージョンにこれらのデバイスを更新することをお勧めします。

>[!NOTE]
>Managed Browser では、Secure Sockets Layer バージョン 3 (SSLv3) 暗号化プロトコルをサポートしません。


## <a name="application-protection-policies-for-protected-browsers"></a>保護ブラウザーのアプリケーション保護ポリシー

Microsoft Edge および Managed Browser は Intune SDK と統合されているため、次のようなアプリ保護ポリシーを適用することもできます。
- 切り取り、コピー、貼り付けの使用をコントロールする。
- 画面の取り込みを禁止する。
- 企業リンクがマネージド アプリとブラウザー内でのみ開くようにする。

詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」を参照してください。

これらの設定は以下のものに適用できます。

- Intune に登録されたデバイス
- 別の MDM 製品に登録されたデバイス
- 管理されていないデバイス

>[!NOTE]
>ユーザーがアプリ ストアから Managed Browser をインストールし、それを Intune で管理していない場合は、Microsoft MyApps サイトを通したシングル サインオンをサポートする通常の Web ブラウザーとして使用できます。 ユーザーは直接 MyApps サイトにアクセスし、プロビジョニングされた SaaS アプリケーションのすべてを表示できます。
Managed Browser または Microsoft Edge が Intune で管理されていない場合、Intune で管理されている他のアプリケーションからデータにアクセスすることはできません。 


## <a name="conditional-access-for-protected-browsers"></a>保護ブラウザーの条件付きアクセス

Managed Browser は、条件付きアクセスの承認済みクライアント アプリになりました。 つまり、Safari や Chrome など、その他のすべての保護されていないブラウザーからのアクセスをブロックして、モバイル ブラウザー アクセスを、ユーザーが Managed Browser しか使用できない Azure AD に接続された Web アプリに制限することができます。 この保護は、Exchange Online や SharePoint Online などの Azure リソース、Office ポータル、および [Azure AD アプリケーション プロキシ](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)を介して外部ユーザーに公開しているオンプレミス サイトにも適用できます。 

Azure AD に接続された Web アプリをモバイル プラットフォームでの Intune Managed Browser の使用に制限するために、承認済みのクライアント アプリケーションを必要とする Azure AD の条件付きアクセス ポリシーを作成することができます。 

1. Azure Portal で **[Azure Active Directory]** > **[エンタープライズ アプリケーション]** > **[条件付きアクセス]** > **[新しいポリシー]** の順に選択します。 
2. 次に、ブレードの **[アクセス制御]** セクションから **[許可]** を選びます。 
3. **[承認されたクライアント アプリが必要です]** をクリックします。 
4. **[許可]** ブレードで **[選択]** をクリックします。 このポリシーは、Intune Managed Browser アプリにのみアクセス可能にするクラウド アプリに割り当てる必要があります。

    ![Azure AD - Managed Browser の条件付きアクセス ポリシー](./media/managed-browser-conditional-access-01.png)

5. **[割り当て]** セクションで、**[条件]** > **[クライアント アプリ]** の順に選択します。 **[クライアント アプリ]** ブレードが表示されます。
6. **[構成]** の下で **[はい]** をクリックして、特定のクライアント アプリにポリシーを適用します。
7. **[ブラウザー]** がクライアント アプリとして選択されていることを確認します。

    ![Azure AD - Managed Browser - クライアント アプリの選択](./media/managed-browser-conditional-access-02.png)

    > [!NOTE]
    > これらのクラウド アプリケーションにアクセスできるネイティブ アプリ (ブラウザー ベースではないアプリ) を制限する場合は、**[モバイル アプリとデスクトップ クライアント]** を選択することもできます。

8. **[割り当て]** セクションで、**[ユーザーとグループ]** を選択し、このポリシーを割り当てるユーザーまたはグループを選択します。 

    > [!NOTE]
    > アプリ構成ポリシーを受信するには、Intune App Protection ポリシーもターゲットとする必要があります。 Intune アプリ保護ポリシーの作成の詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」をご覧ください。

9. **[割り当て]** セクションで、**[クラウド アプリ]** を選択して、このポリシーで保護するアプリを選択します。

上記のポリシーが構成されると、ユーザーは強制的に Intune Managed Browser を使用して、このポリシーで保護している Azure AD に接続されている Web アプリにアクセスします。 ユーザーが、このシナリオで管理されていないブラウザーを使用しようとすると、Intune Managed Browser を代わりに使用する必要があることが通知されます。

Managed Browser では、従来の条件付きアクセス ポリシーはサポートされていません。 詳細については、「[Azure Portal でクラシック ポリシーを移行する](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration)」をご覧ください。

##  <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>ポリシーで保護されたブラウザー内での Azure AD に接続されている Web アプリへのシングル サインオン

iOS および Android 上の Microsoft Edge および Intune Managed Browser アプリケーションで、Azure AD に接続されているすべての Web アプリ (SaaS およびオンプレミス) への SSO を利用できます。 Microsoft Authenticator アプリが iOS 上または Android の Intune ポータル サイト アプリ上に存在する場合、ポリシーで保護されたブラウザーのユーザーは自分の資格情報を再入力しなくても Azure AD に接続されている Web アプリにアクセスできるようになります。

SSO では、iOS 上の Microsoft Authenticator アプリまたは Android 上の Intune ポータル サイトによって、お使いのデバイスが登録されている必要があります。 Authenticator アプリまたは Intune ポータル サイトを持っているユーザーは、デバイスが別のアプリケーションによってまだ登録されていない場合、ポリシーで保護されたブラウザー内で Azure AD に接続されている Web アプリに移動したときに、デバイスを登録することを求められます。 Intune で管理されているアカウントを使用してデバイスを登録すると、そのアカウントは Azure AD に接続されている Web アプリに対する SSO が有効になります。 

> [!NOTE]
> デバイスの登録は、Azure AD サービスによる単純なチェックインです。 完全なデバイスの登録は必要ありません。また、デバイスに対する追加の権限を IT に与えることもありません。

## <a name="create-a-protected-browser-app-configuration"></a>保護ブラウザー アプリの構成を作成する

>[!IMPORTANT]
>適用するアプリの構成については、ユーザーの保護されたブラウザーまたはデバイス上の別のアプリが既に [Intune App Protection ポリシー]( app-protection-policy.md)で管理されている必要があります

1. [Azure ポータル](https://portal.azure.com) にサインインします。
2. **すべてのサービス** > **Intune** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3.  [管理] リストの **[クライアント アプリ]** ブレードで、**[アプリ構成ポリシー]** を選択します。
4.  **[アプリ構成ポリシー]** ブレードで、**[追加]** を選択します。
5.  **[構成ポリシーの追加]** ブレードで **[名前]** を入力し、必要に応じてアプリ構成設定の **[説明]** を入力します。
6.  **[デバイス登録の種類]** には、**[管理対象アプリ]** を選択します。
7.  **[必要なアプリの選択]** を選択して、**[対象アプリ]** ブレードで、iOS、Android、またはその両方向けの **[Managed Browser]** または **[Microsoft Edge]**(あるいは両方) を選択します。
8.  **[OK]** を選択して **[構成ポリシーの追加]** ブレードに戻ります。
9.  **[構成設定]** を選択します。 **[構成]** ブレードで、Managed Browser の構成を指定するキーと値のペアを定義します。 定義できる別のキーと値のペアについては、この記事の後半のセクションで説明します。
10. 終了したら、**[OK]** を選択します。
11. **[構成ポリシーの追加]** ブレードで、**[追加]** を選択します。
12. 新しい構成が作成され、**[アプリの構成]** ブレードに表示されます。


## <a name="assign-the-configuration-settings-you-created"></a>作成した構成設定を割り当てる

設定をユーザーの Azure AD グループに割り当てます。 ユーザーが対象の保護ブラウザー アプリをインストールしている場合、そのアプリは指定された設定で管理されます。

1. Intune モバイル アプリケーション管理ダッシュボードの **[クライアント アプリ]** ブレードで、**[アプリ構成ポリシー]** を選択します。
2. アプリの構成の一覧から、割り当てる構成を選択します。
3. 次のブレードで、**[割り当て]** を選択します。
4. **[割り当て]** ブレードで、アプリの構成を割り当てる Azure AD グループを選択し、**[OK]** を選択します。


## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>保護ブラウザーのアプリケーション プロキシ設定を構成する方法

Microsoft Edge および Intune Managed Browser と [Azure AD アプリケーション プロキシ]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)は、iOS および Android デバイスのユーザーに対して、次のシナリオをサポートするために一緒に使用することができます。

- ユーザーがダウンロードして、Microsoft Outlook アプリにサインインします。 Intune アプリの保護ポリシーが自動的に適用されます。 保護ポリシーでは、保存されたデータを暗号化し、ユーザーが企業ファイルを管理されていないアプリまたはデバイス上の場所に転送できないようにします。 ユーザーが Outlook 内のイントラネット サイトへのリンクをクリックすると、そのリンクを別のブラウザーではなく、保護ブラウザー アプリ内で開くように指定することができます。 保護ブラウザーは、このイントラネット サイトがアプリケーション プロキシを使用してユーザーに公開されていることを認識します。 ユーザーは、適用される多要素認証で認証するためにアプリケーション プロキシを使い、イントラネット サイトに到達する前に条件付きアクセスを使って自動的にルーティングされます。 このサイトは、ユーザーがリモートにいるときに、以前は見つけることができませんでしたが、アクセスできるようになり、Outlook のリンクが期待どおりに動作するようになりました。
- リモート ユーザーが保護ブラウザー アプリケーションを開き、内部 URL を使用してイントラネット サイトに移動します。 保護ブラウザーは、このイントラネット サイトがアプリケーション プロキシを使用してユーザーに公開されていることを認識します。 ユーザーは、適用される多要素認証で認証するためにアプリケーション プロキシを使い、イントラネット サイトに到達する前に条件付きアクセスを使って自動的にルーティングされます。 このサイトは、ユーザーがリモートにいるときに、以前は見つけることができませんでしたが、アクセスできるようになりました。

### <a name="before-you-start"></a>開始する前に

- Azure AD アプリケーション プロキシ経由の内部アプリケーションをセットアップします。
    - アプリケーション プロキシを構成し、アプリケーションを公開するには、[セットアップに関するドキュメント](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started#get-started)を参照してください。 
- Managed Browser アプリの最小バージョン 1.2.0 を使用する必要があります。
- Managed Browser または Microsoft Edge アプリのユーザーは、[Intune アプリの保護ポリシー]( app-protection-policy.md)をアプリに割り当てています。

    > [!NOTE]
    > 更新されたアプリケーション プロキシのリダイレクト データが、Managed Browser や Microsoft Edge で有効になるまでには、最大で 24 時間かかる場合があります。


#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>手順 1.Outlook から保護ブラウザーへの自動リダイレクトを有効にする
Outlook は、アプリ保護ポリシーの [**Managed Browser に表示する Web コンテンツを制限する**] 設定を有効にして構成される必要があります。

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-protected-browser"></a>手順 2: 保護ブラウザーに割り当てられたアプリ構成ポリシーを割り当てる
この手順では、アプリ プロキシのリダイレクトを使用するように、Managed Browser または Microsoft Edge アプリを構成します。 Microsoft Edge または Managed Browser アプリの構成を作成する手順に従い、以下のキーと値のペアを指定します。

| キー                                                             | 値    |
|-----------------------------------------------------------------|----------|
| **com.microsoft.intune.mam.managedbrowser.AppProxyRedirection** | **true** |

オンプレミスの Web アプリへのシームレスな (保護された) アクセスのために、Managed Browser、Microsoft Edge、Azure AD アプリケーション プロキシを並行使用できる方法の詳細については、Enterprise Mobility + Security のブログ記事「[Better together: Intune and Azure Active Directory team up to improve user access (最適な組み合わせ: ユーザーのアクセスを向上するための Intune と Azure Active Directory の連携)](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access)」を参照してください。

> [!NOTE]
> Microsoft Edge は、Managed Browser と同じキーと値のペアを使用します。 

## <a name="how-to-configure-the-homepage-for-a-protected-browser"></a>保護ブラウザーのホームページを構成する方法

この設定では、ユーザーが保護ブラウザーを開始するか、新しいタブを作成したときに表示するホームページを構成することができます。 
- この設定によって、Managed Browser に Web ページが表示されます。  Microsoft Edge では,ホーム ページのショートカットが代わりに表示されます。
- ホーム ページ ショートカット アイコンが、検索コントロールの下にアイコンとして表示されます。  編集または削除することはできません。
- ホーム ページ ショートカットには、区別のために組織の名前が表示されます。  これは常に最初のアイコンとして表示されます。

Microsoft Edge または Managed Browser アプリの構成を作成する手順に従い、以下のキーと値のペアを指定します。

|                                キー                                |                                                           値                                                            |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.homepage</strong> | 有効な URL を指定します。 セキュリティ対策のため、誤った URL はブロックされます。<br>例: `<https://www.bing.com>` |

## <a name="how-to-configure-bookmarks-for-a-protected-browser"></a>保護ブラウザーのブックマークを構成する方法

この設定では、Microsoft Edge または Managed Browser のユーザーが使用できるブックマークのセットを構成できます。

- これらのブックマークは、ユーザーが削除または変更することはできません。
- これらのブックマークは、リストの上部に表示されます。 ユーザーが作成したブックマークは、これらのブックマークの下に表示されます。
- アプリ プロキシのリダイレクトを有効にした場合は、内部 URL または外部 URL を使用してアプリ プロキシ Web アプリを追加できます。

Microsoft Edge または Managed Browser アプリの構成を作成する手順に従い、以下のキーと値のペアを指定します。

|                                キー                                 |                                                                                                                                                                                                                                                         値                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.bookmarks</strong> | この構成の値は、ブックマークのリストです。 各ブックマークは、ブックマークのタイトルとブックマークの URL で構成されます。 タイトルおよび URL は、<strong>&#124;</strong> の文字で区切ります。<br><br>例:<br> <code>Microsoft Bing&#124;https://www.bing.com</code><br><br>複数のブックマークを構成するには、二重の文字 <strong>&#124;&#124;</strong> で各ペアを区切ります。<br><br>例:<br> <code>Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com</code> |

## <a name="how-to-specify-allowed-and-blocked-urls-for-a-protected-browser"></a>保護ブラウザーで許可する URL とブロックする URL を指定する方法

Microsoft Edge または Managed Browser アプリの構成を作成する手順に従い、以下のキーと値のペアを指定します。

|キー|値|
|-|-|
|次の中から選択します。<br><ul><li>許可された URL を指定する場合 (これらの URL のみが許可され、その他のサイトにはアクセスできない):<br> **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br></li><li>ブロックされた URL を指定する場合 (その他のすべてのサイトにアクセスできる):<br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**</li></ul>|キーに対応する値は URL のリストです。 パイプ文字 **&#124;** によって区切られた、1 つの値として許可またはブロックする必要がある、すべての URL を入力します。<br><br>例:<br><br><code>URL1&#124;URL2&#124;URL3</code><br><code>http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com</code>|

>[!IMPORTANT]
>両方のキーを指定しないでください。 両方のキーが同じユーザーを対象とする場合、許可のキーが最も制限の厳しいオプションとして使用されます。
>また、会社の Web サイトなど、重要なページをブロックしないようにご注意ください。

### <a name="url-format-for-allowed-and-blocked-urls"></a>許可される URL とブロックされる URL の形式
許可リストとブロック リストで URL を指定するときに使用できる形式とワイルドカードについて説明します。

- ワイルドカード記号 (**&#42;**) は、以下の許可されているパターン リストの規則に従って使用できます。

- リストに入力するときは、すべての URL の先頭に必ず **http** または **https** を付けてください。

- アドレスにはポート番号を指定できます。 ポート番号を指定しない場合は、次の値が使用されます。

  -   http の場合はポート 80

  -   https の場合はポート 443

  ポート番号にワイルドカードを使用することはできません。 たとえば、 `http://www.contoso.com:;` と `http://www.contoso.com: /;` はサポートされていません。

- URL を指定するときに使用できるパターンの詳細については、次の表を参照してください。

|                  [URL]                  |                     説明                      |                                                ［一致する］                                                |                                ［次の値に一致しない］                                 |
|---------------------------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|        `http://www.contoso.com`         |              単一のページと一致する               |                                            `www.contoso.com`                                            |  `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`contoso.com`/   |
|          `http://contoso.com`           |              単一のページと一致する               |                                             `contoso.com/`                                              | `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com` |
|    `http://www.contoso.com/&#42;`     | `www.contoso.com` で始まるすべての URL と一致する |      `www.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com/videos/tvshows`      |              `host.contoso.com`<br /><br />`host.contoso.com/images`              |
|    `http://*.contoso.com/*`     |     contoso.com の下のすべてのサブドメインに一致する     | `developer.contoso.com/resources`<br /><br />`news.contoso.com/images`<br /><br />`news.contoso.com/videos` |                               `contoso.host.com`                                |
|     `http://www.contoso.com/images`     |             単一のフォルダーと一致する              |                                        `www.contoso.com/images`                                         |                          `www.contoso.com/images/dogs`                          |
|       `http://www.contoso.com:80`       |  ポート番号を使用し、単一のページと一致する   |                                       `http://www.contoso.com:80`                                       |                                                                               |
|        `https://www.contoso.com`        |          セキュリティで保護された単一のページと一致する           |                                        `https://www.contoso.com`                                        |                            `http://www.contoso.com`                             |
| `http://www.contoso.com/images/&#42;` |    1 つのフォルダーおよびすべてのサブフォルダーと一致する    |                  `www.contoso.com/images/dogs`<br /><br />`www.contoso.com/images/cats`                   |                            `www.contoso.com/videos`                             |

- 指定することができない入力例を次に示します。

  - `*.com`

  - `*.contoso/*`

  - `www.contoso.com/*images`

  - `www.contoso.com/*images*pigs`

  - `www.contoso.com/page*`

  - IP アドレス

  - `https://*`

  - `http://*`

  - `http://www.contoso.com:*`

  - `http://www.contoso.com: /*`
## <a name="opening-links-within-the-intune-managed-browser-vs-microsoft-edge"></a>Intune Managed Browser または Microsoft Edge 内でリンクを開くMicrosoft Edge 

Intune Managed Browser および Microsoft Edge は現在、両方ともポリシーで管理されているブラウザー/保護されているブラウザーと見なされています。 今日、既存のアプリ保護ポリシーは Intune マネージド アプリからの Web リンクになっており、使用するシナリオおよびプラットフォームに応じて特定のブラウザーで開きます。 

Android 上の場合:  
* ポリシー マネージド ブラウザーが必須になっているすべての Intune マネージド アプリにおいて、アプリ構成の設定 "com.microsoft.intune.useEdge" が "true" に設定されていない限り、MB および Edge の両方がデバイス上にある場合は Managed Browser。  
* Microsoft Edge のみがデバイス上にあり、ポリシーの対象になっている場合は、Microsoft Edge。
* Managed Browser のみがデバイス上にあり、ポリシーの対象になっている場合は、Managed Browser。 

iOS 上で、iOS または 9.0.9+ 用の Intune SDK を統合したアプリ向けの場合:  
* すべての Intune マネージド アプリにおいて、アプリ構成の設定 "com.microsoft.intune.useEdge" が "true" に設定されていない限り、MB および Edge の両方がデバイス上にある場合は、Managed Browser。**または**、Microsoft Edge がインストールされており、ポリシーが受信済みの場合は、Microsoft Edge。 
* Microsoft Edge のみがデバイス上にあり、ポリシーで対象になっており、かつ、ポリシーが受信済みの場合は、Microsoft Edge。 
* Managed Browser のみがデバイス上にあり、ポリシーの対象になっており、かつ、ポリシーが受信済みの場合は、Managed Browser。

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

-   Managed Browser に関連付けられているアプリ保護ポリシーにオプション [**アクセスの際にシンプルな PIN を要求する**] または [**アクセスの際に会社の資格情報を要求する**] を設定した場合、およびユーザーが認証ページでヘルプのリンクを選択した場合は、ポリシーのブロック リストに追加されているかどうかにかかわらず、インターネット サイトを参照できます。

-   Managed Browser では、サイトへの直接のアクセスのみをブロックできます。 中間サービス (翻訳サービスなど) がサイトへのアクセスに使用される場合、そのアクセスはブロックされません。

-   認証を許可し、Intune ドキュメントにアクセスするために、**&#42;.microsoft.com** は許可またはブロック リスト設定の対象から除外されます。 常に許可されます。

### <a name="turn-off-usage-data"></a>使用状況データをオフにする
Microsoft は、Microsoft の製品やサービスを改善するために、Managed Browser のパフォーマンスおよび使用に関する匿名データを自動的に収集します。 ただし、ユーザーはデバイスの **[使用状況データ]** 設定を使用して、データの収集を無効にすることができます。 このデータの収集方法は制御できません。

-   iOS デバイスでは、証明書の有効期限が切れている Web サイトや証明書が信頼されていない Web サイトにユーザーがアクセスしても、開くことができません。

## <a name="next-steps"></a>次の手順

- [アプリ保護ポリシーとは](app-protection-policy.md) 
