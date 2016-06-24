---
# required metadata

title: Exchange Online と新しい Exchange Online Dedicated への電子メール アクセスを制限する | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 09c82f5d-531c-474d-add6-784c83f96d93

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Intune で Exchange Online と新しい Exchange Online Dedicated への電子メール アクセスを制限する

Exchange Online Dedicated 環境を使用していて、それが新しい構成であるか既存の構成であるかを確認する必要がある場合は、アカウント マネージャーに問い合わせてください。

Exchange Online または新しい Exchange Online Dedicated 環境への電子メール アクセスを制御するには、Intune で Exchange Online の条件付きアクセスを構成します。
条件付きアクセスの動作の詳細については、[電子メールと O365 サービスへのアクセスの制限](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)に関する記事を参照してください。

>[!IMPORTANT]
>先進認証を使用したアプリでの PC および Windows 10 Mobile デバイスに対する条件付きアクセスは、現在、Intune の一部のお客様だけが使用できます。 これらの機能を既に使用している場合は、何も行う必要はありません。 機能を引き続き使用できます。

>先進認証を使用したアプリでの PC および Windows 10 Mobile に対する条件付きアクセス ポリシーをまだ作成しておらず、これから作成する予定である場合は、要求を送信する必要があります。  既知の問題およびこの機能へのアクセス方法の詳細については、[Microsoft Connect サイト](http://go.microsoft.com/fwlink/?LinkId=761472)を参照してください。

条件付きアクセスを構成する**前に**、次のことを行う必要があります。

-   **Exchange Online を含む Office 365 サブスクリプション (E3 など)** を取得します。ユーザーには Exchange Online のライセンスが必要です。

-  オプションの **Microsoft Intune Service to Service Connector** の構成を検討します。これによって [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] が Microsoft Exchange Online に接続され、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] コンソールを使用してデバイス情報を管理できるようになります。 コンプライアンス ポリシーまたは条件付きアクセス ポリシーを使用するうえでコネクタを使用する必要はありませんが、条件付きアクセスの影響を評価するためのレポートの実行に必要です。

   > [!NOTE] Exchange Online と Exchange On-Premises の両方で条件付きアクセスを使用する場合は、Service to Service Connector を構成しないでください。

   コネクタを構成する手順については、[Intune Service to Service Connector](intune-service-to-service-exchange-connector.md) に関するページを参照してください。

条件付きアクセス ポリシーを構成してユーザーに適用すると、ユーザーが電子メールに接続するには、使用する**デバイス**が以下の条件を満たさなくてはならなくなります。

-   [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] に**登録**されているか、ドメインに参加している PC である。

-  **Azure Active Directory に登録されている**。 この登録は、デバイスが [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] に登録されると自動的に行われます。 また、クライアントの Exchange ActiveSync ID を Azure Active Directory に登録する必要があります。

  AAD DRS は、Intune や Office 365 のお客様に対して自動的にアクティブ化されます。 ADFS Device Registration Service をデプロイ済みのお客様には、オンプレミスの Active Directory で登録されたデバイスは表示されません。

-   そのデバイス、またはオンプレミス ドメインに参加しているドメインに展開された [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] コンプライアンス ポリシーに**準拠**している。

条件付きアクセス ポリシーが満たされない場合、ユーザーにはログイン時に次のいずれかのメッセージが表示されます。

- デバイスが [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] に登録されていない、または Azure Active Directory に登録されていない場合は、メッセージが表示され、ポータル サイト アプリのインストール、デバイスの登録、および電子メールのアクティブ化の手順が示されます。 また、このプロセスによって、デバイスの Exchange ActiveSync ID が Azure Active Directory のレコードに関連付けられます。

-   デバイスがコンプライアンス ポリシーのルールに準拠していないと評価された場合は、エンド ユーザーを [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ポータル サイト Web サイトまたはポータル サイト アプリに導くメッセージが表示されます。このポータルで、問題とその修復方法に関する情報を確認することができます。


次の図は、Exchange Online の条件付きアクセス ポリシーで使用されるフローを示します。

![デバイスのアクセスを許可するかブロックするかを判断する決定ポイントを示す図](../media/ConditionalAccess8-1.png)

## モバイル デバイスのサポート
**Outlook** およびその他の**先進認証を使用するアプリ**から Exchange Online の電子メールへのアクセスを制限できます。

- Android 4.0 以降、Samsung Knox Standard 4.0 以降
- iOS 7.1 以降
- Windows Phone 8.1 以降

 **先進認証**では、Active Directory Authentication Library (ADAL) ベースのサインインが Microsoft Office クライアントに導入されます。

> -   ADAL ベースの認証を使用すると、Office クライアントでブラウザー ベースの認証 (パッシブ認証とも呼ばれます) を利用できます。  認証する際に、ユーザーはサインイン Web ページに転送されます。 この新しいサインイン方法によって、**多要素認証**や**証明書ベースの認証**などのより強力なセキュリティを使用できるようになります。先進認証の動作の詳細については、[この記事](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517)を参照してください。


以下のプラットフォームの組み込み **Exchange ActiveSync 電子メール クライアント**による Exchange 電子メールへのアクセスを制限できます。

- Android 4.0 以降、Samsung Knox Standard 4.0 以降

- iOS 7.1 以降

- Windows Phone 8.1 以降

## PC のサポート

PC が Office デスクトップ アプリケーションを実行して **Exchange Online** と **SharePoint Online** にアクセスする場合、次の要件を満たす PC に対して条件付きアクセスをセットアップできます。

-   Windows 7.0 または Windows 8.1 を実行している PC であること。

-   ドメインに参加しているか、コンプライアンス ポリシーのルールに準拠している PC であること。

    準拠していると見なされるためには、PC が [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] に登録済みで、ポリシーに準拠している必要があります。

    ドメインに参加する PC の場合、[デバイスを Azure Active Directory に自動的に登録](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/)するように設定する必要があります。

-   [Office 365 の先進認証が有効化](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)されていて、最新の Office 更新プログラムがすべて適用されていること。

    先進認証により、Active Directory Authentication Library (ADAL) ベースのサインインが Office 2013 Windows クライアントに導入され、**多要素認証**や**証明書ベースの認証**などのより強力なセキュリティを使用できるようになります。

-   最新ではない認証プロトコルをブロックするように ADFS 要求規則を設定します。 詳しい手順は、シナリオ 3 の[ブラウザー ベースのアプリケーションを除く Office 365 への外部アクセスをすべてブロックする](https://technet.microsoft.com/library/dn592182.aspx)、に関するページを参照してください。

## 条件付きアクセスの構成
### 手順 1: コンプライアンス ポリシーを構成し、展開する
条件付きアクセス ポリシーを適用するユーザー グループに対しては、コンプライアンス ポリシーも[作成](create-a-device-compliance-policy-in-microsoft-intune.md)して[展開](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)する必要があります。


> [!IMPORTANT] コンプライアンス ポリシーを展開していない場合、デバイスはポリシーに準拠していると見なされ、Exchange へのアクセスが許可されます。

### 手順 2: 条件付きアクセス ポリシーの効果を評価する
**モバイル デバイスのインベントリ レポート**を使用して、条件付きアクセス ポリシーを構成した後に Exchange へのアクセスがブロックされるデバイスを特定できます。

これを行うには、[Microsoft Intune Service to Service Connector](intune-service-to-service-exchange-connector.md) を使用して、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] と Exchange の間の接続を構成します。
1.  **[レポート] > [モバイル デバイスのインベントリ レポート]** に移動します。
![[モバイル デバイスのインベントリ レポート] ページのスクリーンショット](../media/IntuneSA2bMobileDeviceInventoryReport.png)

2.  レポート パラメーターで、評価する [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] グループを選択し、必要に応じて、ポリシーを適用するデバイス プラットフォームを選択します。
3.  組織のニーズを満たす条件を選択したら、**[レポートの表示]** を選択します。
レポート ビューアが新しいウィンドウで開きます。
![モバイル デバイスのインベントリ レポートのサンプルのスクリーンショット](../media/IntuneSA2cViewReport.PNG)

レポートを実行した後、ユーザーをブロックするかどうかを判断するために、次の 4 つの列を調べます。

-   **[管理チャネル]** - デバイスが Intune、Exchange ActiveSync、またはその両方のいずれによって管理されているかを示します。

-   **[AAD に登録済み]** - デバイスが Azure Active Directory に登録されているかどうかを示します (社内参加と呼ばれます)。

-   **[準拠]** - デバイスが、展開したコンプライアンス ポリシーに準拠しているかどうかを示します。

-   **[Exchange ActiveSync ID]** - iOS および Android デバイスで、Exchange ActiveSync ID が Azure Active Directory のデバイス登録レコードに関連付けられている必要があります。 これは、ユーザーが検疫メールで **[電子メールのアクティブ化]** のリンクを選択したときに実行されます。

    > [!NOTE] Windows Phone デバイスは、常にこの列の値を表示します。

対象グループの一部であるデバイスは、列の値が以下の表に示されている値と一致しない限り、Exchange にアクセスできないようにブロックされます。

--------------------------
|管理チャネル|AAD に登録済み|準拠|Exchange ActiveSync ID|結果の動作|
|----------------------|------------------|-------------|--------------------------|--------------------|
|**Microsoft Intune および Exchange ActiveSync による管理の対象**|○|○|値が表示される|電子メール アクセスが許可される|
|その他の値|×|×|値が表示されない|電子メール アクセスがブロックされる|
----------------------
レポートの内容をエクスポートし、**[メール アドレス]** 列を使って、ブロックされることをユーザーに通知できます。

### 手順 3: 条件付きアクセス ポリシーのユーザー グループを構成する
条件付きアクセス ポリシーは、さまざまな Azure Active Directory セキュリティ グループのユーザーに適用されます。 また、このポリシーから特定のユーザー グループを除外することもできます。  ユーザーがポリシーの対象となる場合、ユーザーに使用される各デバイスが電子メールにアクセスするには、ポリシーを遵守している必要があります。

これらのグループは、 **Office 365 管理センター**または **Intune アカウント ポータル**で構成できます。

各ポリシーには、次の 2 つのグループの種類を指定できます。

-   **対象グループ** - ポリシーが適用されるユーザー グループ

-   **例外グループ** - ポリシーから除外されるユーザー グループ (省略可能)

ユーザーが両方のグループに含まれている場合は、ポリシーから除外されます。

条件付きアクセス ポリシーの対象となるグループだけが評価されます。

### 手順 4: 条件付きアクセス ポリシーを構成する

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]**、**[条件付きアクセス]** > **[Exchange Online ポリシー]** の順に選択します。
![Exchange Online の条件付きアクセス ポリシー ページのスクリーンショット](../media/IntuneSA5dExchangeOnlinePolicy.png)

2.  **[Exchange Online ポリシー]** ページで、**[Exchange Online の条件付きアクセス ポリシーを有効にする]** を選択します。

    > [!NOTE] コンプライアンス ポリシーを展開していない場合は、デバイスがポリシーに準拠しているものと見なされます。
    >
    > コンプライアンスの状態に関係なく、ポリシーの対象となっているすべてのユーザーがデバイスを [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] に登録する必要があります。

3.  **[アプリケーション アクセス]** では、先進認証を使用するアプリに対して、ポリシーを適用するプラットフォームを選択する方法が 2 つあります。 サポートされているプラットフォームは、Android、iOS、Windows、および Windows Phone です。

    -   **すべてのプラットフォーム**

        **Exchange Online** にアクセスするために使用するデバイスはすべて、Intune に登録され、またポリシーに準拠している必要があります。  **先進認証**を使用しているクライアント アプリケーションはすべて、条件付きアクセス ポリシーに従います。プラットフォームが現在 Intune でサポートされていない場合、**Exchange Online** へのアクセスはブロックされます。
        >[!TIP]
           PC に対して条件付きアクセスを使用していないと、このオプションは表示されない場合があります。  その場合は、代わりに **[特定のプラットフォーム]** を使用してください。 PC の条件付きアクセスは、現在、Intune の一部のお客様だけが使用できます。   既知の問題およびこの機能へのアクセス方法の詳細については、[Microsoft Connect サイト](http://go.microsoft.com/fwlink/?LinkId=761472)を参照してください。

    -   **特定のプラットフォーム**

         指定したデバイス プラットフォームで**先進認証**を使用しているすべてのクライアント アプリに条件付きアクセス ポリシーが適用されます。

4.  **[Exchange ActiveSync アプリ]** では、非準拠のデバイスから Exchange Online へのアクセスをブロックするよう選択できます。 また、サポートされているプラットフォームを実行していないデバイスに対して、電子メールへのアクセスを許可するかブロックするかを選択することもできます。 サポートされているプラットフォームは、Android、iOS、Windows、および Windows Phone です。


5.  **[対象グループ]** で、ポリシーを適用するユーザーの Active Directory セキュリティ グループを選択します。 すべてのユーザーと、ユーザー グループの選択した一覧のどちらを対象にするかを選択できます。
![対象グループと例外グループのオプションを表示した Exchange Online の条件付きアクセス ポリシー ページのスクリーンショット](../media/IntuneSA5eTargetedExemptedGroups.PNG)
    > [!NOTE] **対象グループ**に含まれているユーザーについては、Exchange のルールとポリシーが Intune のポリシーに置き換えられます。
    >
    > 次の場合にのみ、Exchange の許可、ブロック、検疫のルールと、Exchange のポリシーが適用されます。
    >
    > -   ユーザーが Intune のライセンスを取得していない。
    > -   ユーザーが Intune のライセンスを取得しているが、条件付きアクセス ポリシーの対象となるどのセキュリティ グループにも属していない。

6.  **[例外グループ]** で、このポリシーから除外するユーザーの Active Directory セキュリティ グループを選択します。 ユーザーが対象グループと例外グループの両方に属している場合、ユーザーはポリシーから除外されます。

7.  終了したら、**[保存]** を選択します。

-   条件付きアクセス ポリシーを展開する必要はありません。直ちに有効になります。

-   ユーザーが電子メール アカウントを作成すると、デバイスはすぐにブロックされます。

-   ブロックされたユーザーがデバイスを [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] に登録し、非準拠の問題を修正すると、メールのアクセスは 2 分以内でブロック解除されます。

-   ユーザーがデバイスの登録を解除した場合、メールは約 6 時間後にブロックされます。

**デバイスのアクセスを制限する条件付きアクセス ポリシーの構成方法を示したシナリオの例を見るには、[電子メール アクセスの制限のシナリオ例](restrict-email-access-example-scenarios.md)を参照してください。**

## コンプライアンスと条件付きアクセス ポリシーを監視する

#### Exchange からブロックされているデバイスを表示するには

[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ダッシュボードで、**[Exchange からブロックされているデバイス]** タイルを選択します。ブロックされているデバイスの数と詳細情報へのリンクが表示されます。
![Exchange へのアクセスがブロックされているデバイスの数を表示した Intune ダッシュボードのスクリーンショット](../media/IntuneSA6BlockedDevices.PNG)

## 次のステップ
[SharePoint Online へのアクセスを制限する](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

[Skype for Business Online へのアクセスを制限する](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


