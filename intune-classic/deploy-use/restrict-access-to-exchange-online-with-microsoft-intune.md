---
title: "Exchange Online への電子メールを保護する"
description: "条件付きアクセスで Exchange Online の会社電子メールへのアクセスを保護および制御します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 09c82f5d-531c-474d-add6-784c83f96d93
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5ea0e0c31dc3b24c0093d6e3b73d38f2bee50bd7
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="protect-email-access-to-exchange-online-and-new-exchange-online-dedicated-with-intune"></a>Intune で Exchange Online と新しい Exchange Online Dedicated への電子メール アクセスを保護する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune を使用して、Exchange Online または Exchange Online Dedicated の条件付きアクセスを構成できます。 条件付きアクセスの動作の詳細については、[電子メール、O365、およびその他のサービスへのアクセスを保護する](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)に関する記事をご覧ください。

> [!NOTE]
>Exchange Online Dedicated 環境を使用していて、それが新しい構成であるか既存の構成であるかを確認する必要がある場合は、アカウント マネージャーに問い合わせてください。

## <a name="before-you-begin"></a>始める前に

条件付きアクセスを構成するには

-   **Exchange Online を含む Office 365 サブスクリプション (E3 など)** を取得します。ユーザーには Exchange Online のライセンスが必要です。

- **Enterprise Mobility + Security (EMS) サブスクリプション**または **Azure Active Directory (Azure AD) Premium サブスクリプション**を取得します。ユーザーに EMS または Azure AD のライセンスが付与される必要があります。 詳細については、「[Enterprise Mobility pricing page](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing)」 (Enterprise Mobility の価格) ページまたは「[Azure Active Directory の価格](https://azure.microsoft.com/pricing/details/active-directory/)」ページを参照してください。

-  オプションの **Intune Service to Service Connector** の構成を検討します。これによって Intune が Exchange Online に接続され、Intune コンソールを使ってデバイス情報を管理できるようになります。 コンプライアンス ポリシーまたは条件付きアクセス ポリシーを使用するうえでコネクタを使用する必要はありませんが、条件付きアクセスの影響を評価するためのレポートの実行に必要です。
    -  詳細については、[Intune Service to Service Connector](intune-service-to-service-exchange-connector.md) に関するページを参照してください。

   > [!NOTE]
   > Exchange Online と Exchange On-Premises の両方で条件付きアクセスを使用する場合は、Intune Service to Service Connector を構成しないでください。

### <a name="device-compliance-requirements"></a>デバイス コンプライアンスの要件

条件付きアクセス ポリシーを構成してユーザーに適用すると、ユーザーが電子メールに接続するには、使用する**デバイス**が以下の条件を満たさなくてはならなくなります。

- ドメインに参加している PC であるか、または Intune に**登録**されていること。

- **Azure Active Directory に登録されている**。 この登録は、デバイスが Intune に登録されると自動的に行われます。 また、クライアントの Exchange ActiveSync ID を Azure Active Directory に登録する必要があります。

  Azure Active Directory Device Registration サービスは、Intune や Office 365 のお客様に対して自動的にアクティブ化されます。 ADFS Device Registration Service をデプロイ済みのお客様には、オンプレミスの Active Directory で登録されたデバイスは表示されません。

- そのデバイス、またはオンプレミス ドメインに参加しているドメインに展開された Intune コンプライアンス ポリシーに**準拠**していること。

### <a name="when-the-device-is-not-compliant"></a>デバイスが準拠していない場合

条件付きアクセス ポリシーが満たされない場合、デバイスはすぐに検疫され、ユーザーは電子メールを受信し、サインイン時に次のいずれかの検疫通知が表示されます。

- デバイスが Intune に登録されていない、または Azure Active Directory に登録されていない場合は、メッセージが表示され、ポータル サイト アプリのインストール、デバイスの登録、および電子メールのアクティブ化の手順が示されます。 また、このプロセスによって、デバイスの Exchange ActiveSync ID が Azure Active Directory のレコードに関連付けられます。

-   デバイスがコンプライアンス ポリシーのルールに準拠していないと評価された場合は、ユーザーを Intune ポータル サイト Web サイトまたはポータル サイト アプリに導くメッセージが表示されます。このポータルで、問題とその修復方法に関する情報を確認することができます。

### <a name="how-conditional-access-works-with-exchange-online"></a>Exchange Online での条件付きアクセスのしくみ

次の図は、Exchange Online の条件付きアクセス ポリシーで使用されるフローを示します。

![デバイスのアクセスを許可するかブロックするかを判断する決定ポイントを示す図](../media/ConditionalAccess8-1.png)

## <a name="support-for-mobile-devices"></a>モバイル デバイスのサポート
**Outlook** およびその他の**先進認証を使用するアプリ**から Exchange Online の電子メールへのアクセスを保護できます。 次のものがサポートされています。

- Android 4.0 以降、Samsung KNOX Standard 4.0 以降、Android for Work
- iOS 8.0 以降

**先進認証**では、Active Directory Authentication Library (ADAL) ベースのサインインが Microsoft Office クライアントに導入されます。

-   ADAL ベースの認証を使用すると、Office クライアントでブラウザー ベースの認証 (パッシブ認証とも呼ばれます) を利用できます。 認証するときに、ユーザーはサインイン Web ページに転送されます。
-   この新しいサインイン方法によって、**多要素認証**や**証明書ベースの認証**などのより強力なセキュリティを使用できるようになります。 詳細については、「[How modern authentication works](https://support.office.com/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517)」 (先進認証の動作) を参照してください。 最新ではない認証プロトコルをブロックするように ADFS 要求規則を設定できます。 詳しい手順は、[シナリオ 3: ブラウザー ベースのアプリケーションを除く Office 365 への外部アクセスをすべてブロックする方法](https://technet.microsoft.com/library/dn592182.aspx)に関するページを参照してください。

**iOS** と **Android** デバイス上のブラウザーからユーザーがアクセスした場合、Exchange Online の **Outlook Web Access (OWA)** へのアクセスを保護することができます。 準拠デバイスでサポートされているブラウザーからのアクセスのみが許可されます。

* Safari (iOS)
* Chrome (Android)
* Intune Managed Browser (iOS、Android 5.0 以降)

   > [!IMPORTANT]
   > **サポートされていないブラウザーはブロックされます**。

**iOS 用と Android 用 OWA アプリケーションでは、最新の認証がサポートされていないため、最新の認証を使用しないように変更することができます。OWA アプリケーションからのアクセスは、ADFS 要求規則を使用してブロックする必要があります。**


以下のプラットフォームの組み込み **Exchange ActiveSync 電子メール クライアント**による Exchange 電子メールへのアクセスを保護できます。

- Android 4.0 以降、Samsung Knox Standard 4.0 以降

- iOS 8.0 以降

- Windows Phone 8.1 以降

## <a name="support-for-pcs"></a>PC のサポート

PC が Office デスクトップ アプリケーションを実行して **Exchange Online** と **SharePoint Online** にアクセスする場合、次の要件を満たす PC に対して条件付きアクセスをセットアップできます。

- Windows 7.0、Windows 8.1、または Windows 10 を実行している PC であること。

  >[!NOTE]
  > Windows 10 を搭載した PC で条件付きアクセスを使用するには、Windows 10 Anniversary Update で PC を更新する必要があります。

  ドメインに参加しているか、コンプライアンス ポリシーのルールに準拠している PC であること。

  準拠していると見なされるためには、PC が Intune に登録済みで、ポリシーに準拠している必要があります。

  ドメインに参加する PC の場合、Azure Active Directory に[デバイスを自動的に登録](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/)するための条件付きアクセスを設定する必要があります。

  >[!NOTE]
  >Intune コンピューター クライアントを実行する PC では、条件付きアクセスはサポートされていません。

- [Office 365 の先進認証が有効化](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)されていて、最新の Office 更新プログラムがすべて適用されていること。

  先進認証では、Active Directory Authentication Library (ADAL) ベースのサインインが Office 2013/Windows クライアントに導入されます。 この方法によって、**多要素認証**や**証明書ベースの認証**などのより強力なセキュリティを使用できるようになります。

- 最新ではない認証プロトコルをブロックするように ADFS 要求規則が設定されます。 詳しい手順は、[シナリオ 3: ブラウザー ベースのアプリケーションを除く Office 365 への外部アクセスをすべてブロックする方法](https://technet.microsoft.com/library/dn592182.aspx)に関するページを参照してください。

## <a name="configure-conditional-access"></a>条件付きアクセスの構成
### <a name="step-1-configure-and-deploy-a-compliance-policy"></a>手順 1: コンプライアンス ポリシーを構成し、展開する
条件付きアクセス ポリシーを適用するユーザー グループに対しては、コンプライアンス ポリシーも[作成](create-a-device-compliance-policy-in-microsoft-intune.md)して[展開](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)する必要があります。


> [!IMPORTANT]
> コンプライアンス ポリシーを展開していない場合、デバイスはポリシーに準拠していると見なされ、Exchange へのアクセスが許可されます。

### <a name="step-2-evaluate-the-effect-of-the-conditional-access-policy"></a>手順 2: 条件付きアクセス ポリシーの効果を評価する
**モバイル デバイスのインベントリ レポート**を使用して、条件付きアクセス ポリシーを構成した後に Exchange へのアクセスがブロックされるデバイスを特定できます。

これを行うには、[Microsoft Intune Service to Service Connector](intune-service-to-service-exchange-connector.md) を使って、Intune と Exchange の間の接続を構成します。
1.  **[レポート]**、**[モバイル デバイスのインベントリ レポート]** に移動します。
![[モバイル デバイスのインベントリ レポート] ページのスクリーンショット](../media/IntuneSA2bMobileDeviceInventoryReport.png)

2.  レポート パラメーターで、評価する Intune グループを選択し、必要に応じて、ポリシーを適用するデバイス プラットフォームを選択します。
3.  組織のニーズを満たす条件を選択したら、**[レポートの表示]** を選択します。
レポート ビューアが新しいウィンドウで開きます。
![モバイル デバイスのインベントリ レポートのサンプルのスクリーンショット](../media/IntuneSA2cViewReport.PNG)

レポートを実行した後、ユーザーをブロックするかどうかを判断するために、次の 4 つの列を調べます。

-   **[管理チャネル]**: デバイスが Intune、Exchange ActiveSync、またはその両方のいずれによって管理されているかを示します。

-   **[AAD に登録済み]**: デバイスが Azure Active Directory に登録されているかどうかを示します (社内参加と呼ばれます)。

-   **[準拠]**: デバイスが、展開したコンプライアンス ポリシーに準拠しているかどうかを示します。

-   **[Exchange ActiveSync ID]**: iOS および Android デバイスで、Exchange ActiveSync ID が Azure Active Directory のデバイス登録レコードに関連付けられている必要があります。 これは、ユーザーが検疫メールで **[電子メールのアクティブ化]** のリンクを選択したときに実行されます。

    > [!NOTE]
    > Windows Phone デバイスは、常にこの列の値を表示します。

対象グループの一部であるデバイスは、列の値が以下の表に示されている値と一致しない限り、Exchange にアクセスできないようにブロックされます。

--------------------------

|                          管理チャネル                          | AAD に登録済み | 準拠 | Exchange ActiveSync ID |    結果の動作     |
|----------------------------------------------------------------------|----------------|-----------|------------------------|-------------------------|
| <strong>Microsoft Intune および Exchange ActiveSync による管理の対象</strong> |      はい       |    はい    |  値が表示される  | 電子メール アクセスが許可される |
|                           その他の値                            |       [いいえ]       |    [いいえ]     | 値が表示されない  | 電子メール アクセスがブロックされる |

----------------------
レポートの内容をエクスポートし、**[メール アドレス]** 列を使って、ブロックされることをユーザーに通知できます。

### <a name="step-3-configure-user-groups-for-the-conditional-access-policy"></a>手順 3: 条件付きアクセス ポリシーのユーザー グループを構成する
条件付きアクセス ポリシーは、さまざまな Azure Active Directory セキュリティ グループのユーザーに適用されます。 また、条件付きアクセス ポリシーから特定のユーザー グループを除外することもできます。 ユーザーがポリシーの対象となる場合、ユーザーに使用される各デバイスが電子メールにアクセスするには、ポリシーを遵守している必要があります。

これらのグループは、**Office 365 管理センター**または **Intune アカウント ポータル**で構成できます。

各ポリシーには、次の 2 つのグループの種類を指定できます。

-   **対象グループ**: ポリシーが適用されるユーザー グループ

-   **例外グループ**: ポリシーから除外されるユーザー グループ (省略可能)

ユーザーが両方のグループに含まれている場合は、ポリシーから除外されます。

条件付きアクセス ポリシーの対象となるグループだけが評価されます。

### <a name="step-4-configure-the-conditional-access-policy"></a>手順 4: 条件付きアクセス ポリシーを構成する

> [!NOTE]
> Azure AD 管理コンソールでは、条件付きアクセス ポリシーを作成することもできます。 Azure AD 管理コンソールを使用すると、Intune デバイスの条件付きアクセス ポリシー (Azure AD では**デバイスベースの条件付きアクセス ポリシー**と呼ばれている) に加えて、多要素認証など、他の条件付きアクセス ポリシーを作成することもできます。
> 
> Azure AD がサポートするサード パーティ製の Enterprise アプリ (Salesforce や Box など) に条件付きアクセス ポリシーを設定することもできます。 詳細については、「[Azure Active Directory に接続されたアプリケーションのアクセスを制御する Azure Active Directory デバイス ベースの条件付きアクセス ポリシーを設定する方法](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-policy-connected-applications/)」を参照してください。


1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** > **[条件付きアクセス]** > **[Exchange Online ポリシー]** の順に選択します。

2. **[Exchange Online ポリシー]** ページで、**[Exchange Online の条件付きアクセス ポリシーを有効にする]** を選択します。

   > [!NOTE]
   > コンプライアンス ポリシーを展開していない場合は、デバイスがポリシーに準拠しているものと見なされます。
   >
   > コンプライアンスの状態に関係なく、ポリシーの対象となっているすべてのユーザーがデバイスを Intune に登録する必要があります。

3. **[アプリケーション アクセス]** では、先進認証を使用するアプリに対して、ポリシーを適用するプラットフォームを選択する方法が 2 つあります。 サポートされているプラットフォームは、Android、iOS、Windows、および Windows Phone です。

   -   **すべてのプラットフォーム**

       **Exchange Online** にアクセスするために使用するデバイスはすべて、Intune に登録され、またポリシーに準拠している必要があります。 **先進認証**を使っているすべてのクライアント アプリケーションに、条件付きアクセス ポリシーが適用されます。 プラットフォームが現在 Intune でサポートされていない場合、**Exchange Online** へのアクセスはブロックされます。

       **[すべてのプラットフォーム]** オプションを選択することは、クライアント アプリケーションから報告されたプラットフォームでない限り、Azure Active Directory がすべての認証要求にこのポリシーを適用することを意味します。 次の場合を除いて、すべてのプラットフォームが登録されて準拠している必要があります。
       *   Windows デバイスが登録されて準拠している必要があるか、またはオンプレミスの Active Directory でドメインに参加している (一方または両方)
       * Mac OS などのサポートされていないプラットフォーム ただし、これらのプラットフォームからの最新の認証を使用しているアプリは、それでもブロックされます。

   -   **特定のプラットフォーム**

        指定したデバイス プラットフォームで**先進認証**を使用しているすべてのクライアント アプリに条件付きアクセス ポリシーが適用されます。

4. **Outlook Web Access (OWA)** で、サポートされているブラウザー (Safari (iOS)、Chrome (Android)) を通じてのみ、Exchange Online へのアクセスを許可することを選択できます。 その他のブラウザーからのアクセスはブロックされます。 Outlook のアプリケーションのアクセス用に選択した同じプラットフォームの制限も、ここに適用されます。

   **Android** デバイスで、ユーザーはブラウザー アクセスを有効にする必要があります。 この操作を行うには、次のようにエンドユーザーが、登録されるデバイスで **ブラウザー アクセスを有効にする** オプションを有効にする必要があります。
   1.    **ポータル サイト** アプリを開きます。
   2.    省略記号 [...] またはハードウェアのメニュー ボタンから、**[設定]** ページに移動します。
   3.    **[ブラウザー アクセスを有効にする]** ボタンを押します。
   4.    Chrome ブラウザーで Office 365 からサインアウトして、Chrome を再起動します。

   **iOS** および **Android** プラットフォームでは、サービスにアクセスするために使用するデバイスを識別するために、Azure Active Directory はデバイスにトランスポート層セキュリティ (TLS) 証明書を発行します。 デバイスには、次のスクリーン ショットに示すように、証明書を選択するユーザーに対してプロンプトで証明書が表示されます。 ユーザーは、ブラウザーを使用し続けるには、まずこの証明書を選択する必要があります。

   **Android**

   ![iPad での証明書プロンプトのスクリーンショット](../media/mdm-browser-ca-ios-cert-prompt.png)

   **Android**

   ![Android デバイス上の証明書プロンプトのスクリーンショット](../media/mdm-browser-ca-android-cert-prompt.png)

5. **[Exchange ActiveSync アプリ]** では、非準拠のデバイスから Exchange Online へのアクセスをブロックするよう選択できます。 また、サポートされているプラットフォームを実行していないデバイスに対して、電子メールへのアクセスを許可するかブロックするかを選択することもできます。 サポートされているプラットフォームは、Android、iOS、Windows、および Windows Phone です。

   **Android for Work** デバイスの Exchange Active Sync アプリ:
   -  Android for Work デバイスでは、**仕事用プロファイル**の **Gmail** アプリと **Nine Work** アプリのみがサポートされています。 条件付きアクセスが Android for Work デバイスで動作するには、Gmail アプリまたは Nine Work アプリ用の電子メール プロファイルを展開する必要があります。また、**必要な**インストールとして展開する必要があります。

6. **[対象グループ]** で、ポリシーを適用するユーザーの Active Directory セキュリティ グループを選択します。 すべてのユーザーと、ユーザー グループの選択した一覧のどちらを対象にするかを選択できます。
   ![対象グループと例外グループのオプションを表示した Exchange Online の条件付きアクセス ポリシー ページのスクリーンショット](../media/IntuneSA5eTargetedExemptedGroups.PNG)
   > [!NOTE]
   > **対象グループ**に含まれているユーザーについては、Exchange のルールとポリシーが Intune のポリシーに置き換えられます。
   >
   > 次の場合にのみ、Exchange の許可、ブロック、検疫のルールと、Exchange のポリシーが適用されます。
   >
   > -   ユーザーが Intune のライセンスを取得していない。
   > -   ユーザーが Intune のライセンスを取得しているが、条件付きアクセス ポリシーの対象となるどのセキュリティ グループにも属していない。

7. **[例外グループ]** で、このポリシーから除外するユーザーの Active Directory セキュリティ グループを選択します。 ユーザーが対象グループと例外グループの両方に属している場合、ユーザーはポリシーから除外されます。

8. 終了したら、**[保存]** を選択します。

-   条件付きアクセス ポリシーを展開する必要はありません。直ちに有効になります。

-   ユーザーが電子メール アカウントを作成すると、デバイスはすぐにブロックされます。

-   ブロックされたユーザーがデバイスを Intune に登録し、非準拠の問題を修正すると、メールのアクセスは 2 分以内でブロック解除されます。

-   ユーザーがデバイスの登録を解除した場合、メールは約 6 時間後にブロックされます。

**デバイスのアクセスを保護する条件付きアクセス ポリシーの構成方法を示したシナリオの例**を見るには、[電子メール アクセスの保護のシナリオ例](restrict-email-access-example-scenarios.md)をご覧ください。

## <a name="monitor-the-compliance-and-conditional-access-policies"></a>コンプライアンスと条件付きアクセス ポリシーを監視する

#### <a name="to-view-devices-that-are-blocked-from-exchange"></a>Exchange からブロックされているデバイスを表示するには

Intune ダッシュボードで、**[Exchange からブロックされているデバイス]** タイルを選択します。ブロックされているデバイスの数と詳細情報へのリンクが表示されます。
![Exchange へのアクセスがブロックされているデバイスの数を表示した Intune ダッシュボードのスクリーンショット](../media/IntuneSA6BlockedDevices.PNG)

## <a name="next-steps"></a>次の手順
- [SharePoint Online へのアクセスを保護する](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

- [Skype for Business Online へのアクセスを保護する](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
