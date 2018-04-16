---
title: "SharePoint Online を保護する"
description: "条件付きアクセスを使って、SharePoint Online の会社データへのアクセスを保護および制御します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2b7285c272efac8eab406393b0b896795fa5d8ed
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="protect-access-to-sharepoint-online-with-microsoft-intune"></a>Microsoft Intune で SharePoint Online へのアクセスを保護する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune の条件付きアクセスを使って、SharePoint Online 上にあるファイルへのアクセスを制御します。
条件付きアクセスには、2 つのコンポーネントがあります。
- デバイス コンプライアンス ポリシー。準拠したデバイスと見なされるには、このポリシーに準拠している必要があります。
- 条件付きアクセス ポリシー。デバイスがサービスにアクセスするために満たす必要のある条件を指定します。
条件付きアクセスの動作の詳細については、[電子メール、O365、およびその他のサービスへのアクセスを保護する](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)に関するトピックをご覧ください。

コンプライアンス ポリシーと条件付きアクセス ポリシーを、ユーザーに対して展開します。 ユーザーがサービスへのアクセスに使うすべてのデバイスは、ポリシーによってコンプライアンスをチェックされます。

ユーザーが、デバイスで OneDrive などのサポートされているアプリを使ってファイルに接続しようとすると、次の評価が行われます。

![デバイスに SharePoint へのアクセスを許可するかブロックするかを判断する決定ポイントを示す図](../media/ConditionalAccess8-6.png)


SharePoint Online の条件付きアクセス ポリシーを構成する**前に**、次のことを行う必要があります。
- **SharePoint Online サブスクリプション**を取得します。ユーザーには SharePoint Online のライセンスが必要です。
- **Enterprise Mobility + Security (EMS) サブスクリプション**または **Azure Active Directory (Azure AD) Premium サブスクリプション**を取得します。ユーザーに EMS または Azure AD のライセンスが付与される必要があります。 詳細については、「[Enterprise Mobility pricing page](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing)」 (Enterprise Mobility の価格) ページまたは「[Azure Active Directory の価格](https://azure.microsoft.com/pricing/details/active-directory/)」ページを参照してください。


  必要なファイルに接続するには、デバイスが次の条件を満たしている必要があります。
-   Intune に**登録**されているか、ドメインに参加する PC である。

-   Azure Active Directory に**登録**されている (デバイスが Intune に登録されている場合は、自動的に登録されます)。


-   展開されているすべての Intune コンプライアンス ポリシーに**準拠**している。

デバイスの状態は、Azure Active Directory に格納され、指定した条件に基づいて、ファイルへのアクセスが許可されたりブロックされたりします。

条件が満たされない場合、ユーザーにはサインイン時に以下のうちのいずれかのメッセージが表示されます。

-   デバイスが Intune に登録されていない、または Azure Active Directory に登録されていない場合は、メッセージが表示され、ポータル サイト アプリのインストールと登録の手順が示されます。

-   デバイスがポリシーに準拠していない場合は、ユーザーを Intune ポータル サイト Web サイトに導くメッセージが表示されます。このポータルで、問題とその修復方法に関する情報を確認することができます。

**条件付きアクセスは外部共有に適用されません**。 テナントまたはサイト コレクションで外部共有を使用しない方法については、「[SharePoint Online 環境の外部共有を管理する](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)」をご覧ください。

>[!NOTE]
>SharePoint Online で条件付きアクセスを有効にする場合は、[Remove-SPOTenantSyncClientRestriction](https://technet.microsoft.com/library/dn917451.aspx) のトピックの説明に従って、一覧にあるドメインを無効にすることをお勧めします。  

## <a name="support-for-mobile-devices"></a>モバイル デバイスのサポート
次のものがサポートされています。
- iOS 8.0 以降
- Android 4.0 以降、Samsung Knox Standard 4.0 以降
- Windows Phone 8.1 以降

**iOS** デバイスや **Android** デバイスがブラウザーからアクセスした場合、SharePoint Online へのアクセスを保護することができます。 準拠デバイスでサポートされているブラウザーからのアクセスのみが許可されます。
* Safari (iOS)
* Chrome (Android)
* Intune Managed Browser (iOS および Android 5.0 以降)

**サポートされていないブラウザーはブロックされます**。

## <a name="support-for-pcs"></a>PC のサポート
次のものがサポートされています。
- Windows 8.1 以降 (PC が Intune に登録されている場合)
- Windows 7.0、Windows 8.1、または Windows 10 (PC がドメインに参加している場合)
  > [!NOTE]
  >Windows 10 を搭載した PC で条件付きアクセスを使用するには、Windows 10 Anniversary Update で PC を更新する必要があります。

  - ドメインに参加している PC の場合、Azure Active Directory に[自動的に登録](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/)するように設定する必要があります。 Azure AD Device Registration サービスは、Intune や Office 365 のお客様に対して自動的にアクティブ化されます。 ADFS Device Registration Service をデプロイ済みのお客様には、オンプレミスの Active Directory で登録されたデバイスは表示されません。

  - ドメインへの参加を要求するようにポリシーを設定していて、PC がドメインに参加していない場合は、IT 管理者に連絡するようにメッセージが表示されます。

  - ドメインへの参加または準拠を要求するようにポリシーを設定していて、PC がいずれかの要件を満たしていない場合は、ポータル サイト アプリをインストールして登録する方法についての手順が示されたメッセージが表示されます。
    >[!NOTE]
    >Intune コンピューター クライアントを実行する PC では、条件付きアクセスはサポートされていません。

[Office 365 の先進認証が有効化](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)されていて、最新の Office 更新プログラムがすべて適用されていること。

先進認証により、Active Directory Authentication Library (ADAL) に基づくサインインが Office 2013 Windows クライアントに導入され、**多要素認証**や**証明書ベースの認証**などのより強力なセキュリティを使用できるようになります。


## <a name="configure-conditional-access-for-sharepoint-online"></a>SharePoint Online の条件付きアクセスの構成

### <a name="step-1-configure-active-directory-security-groups"></a>手順 1. Active Directory セキュリティ グループを構成する
開始する前に、条件付きアクセス ポリシーの Azure Active Directory セキュリティ グループを構成します。 これらのグループは、**Office 365 管理センター**または **Intune アカウント ポータル**で構成できます。 これらのグループは、ユーザーをポリシーの対象とするか、または除外するために使用されます。 ユーザーがポリシーの対象となる場合、ユーザーに使用される各デバイスがリソースにアクセスするには、ポリシーを遵守している必要があります。

SharePoint Online ポリシーには、次の 2 つのグループの種類を指定できます。

-   **対象グループ**: ポリシーを適用するユーザーのグループが含まれます。

-   **例外グループ**: ポリシーから除外されるユーザーのグループが含まれます。

ユーザーが両方のグループに含まれている場合は、ポリシーから除外されます。

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>手順 2. コンプライアンス ポリシーを構成し、展開する
まだ行っていない場合は、コンプライアンス ポリシーを作成し、SharePoint Online ポリシーの対象となるユーザーに展開します。

> [!NOTE]
> コンプライアンス ポリシーは Intune グループに展開されますが、条件付きアクセス ポリシーは、Azure Active Directory セキュリティ グループを対象とします。

コンプライアンス ポリシーを構成する方法の詳細については、「[コンプライアンス ポリシーの作成](create-a-device-compliance-policy-in-microsoft-intune.md)」をご覧ください。

> [!IMPORTANT]
> コンプライアンス ポリシーを展開していない場合は、デバイスがポリシーに準拠しているものと見なされます。

準備ができたら、**手順 3** に進みます。

### <a name="step-3-configure-the-sharepoint-online-policy"></a>手順 3. SharePoint Online ポリシーを構成する
次に、管理デバイスおよび準拠デバイスのみが SharePoint Online にアクセスできるように要求するポリシーを構成します。 このポリシーは、Azure Active Directory に格納されます。

#### <a name="bkmk_spopolicy"></a>

>[!NOTE]
> Azure AD 管理コンソールで、Intune デバイスの条件付きアクセス ポリシーを作成することもできます (このようなポリシーは、Azure AD の**デバイス ベースの条件付きアクセス ポリシー**と呼ばれます)。 さらに、多要素認証のような他の条件付きアクセス ポリシーを作成することもできます。 Azure AD がサポートするサード パーティ製の Enterprise アプリ (Salesforce や Box など) に条件付きアクセス ポリシーを設定することもできます。 詳細については、「[Azure Active Directory に接続されたアプリケーションのアクセスを制御する Azure Active Directory デバイス ベースの条件付きアクセス ポリシーを設定する方法](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-policy-connected-applications/)」を参照してください。


1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** > **[条件付きアクセス]** > **[SharePoint Online ポリシー]** の順に選択します。
   ![SharePoint Online ポリシー ページのスクリーンショット](../media/mdm-ca-spo-policy-configuration.png)

2. **[SharePoint Online の条件付きアクセス ポリシーを有効にする]** をオンにします。

3. **[アプリケーション アクセス]** で、条件付きアクセス ポリシーを適用する対象を次のように選ぶことができます。

   - **すべてのプラットフォーム**

     **SharePoint Online** にアクセスするために使用するデバイスはすべて、Intune に登録され、またポリシーに準拠している必要があります。 **先進認証**を使っているすべてのクライアント アプリケーションに、条件付きアクセス ポリシーが適用されます。 プラットフォームが現在 Intune でサポートされていない場合、**SharePoint Online** へのアクセスはブロックされます。

     **[すべてのプラットフォーム]** オプションを選択することは、クライアント アプリケーションから報告されたプラットフォームでない限り、Azure Active Directory がすべての認証要求にこのポリシーを適用することを意味します。 次の場合を除いて、すべてのプラットフォームが登録されて準拠している必要があります。
     *   Windows デバイスが登録されて準拠している必要があるか、またはオンプレミスの Active Directory でドメインに参加している (一方または両方)
     * Mac などのサポートされていないプラットフォーム ただし、これらのプラットフォームからの最新の認証を使用しているアプリは、それでもブロックされます。

   - **特定のプラットフォーム**

      指定したプラットフォームで先進認証を使用しているすべてのクライアント アプリに条件付きアクセス ポリシーが適用されます。

     Windows PC の場合は、ドメインに参加しているか、または Intune に登録されてポリシーに準拠している必要があります。 以下の要件を設定できます。

     -   **デバイスはドメインに参加しているか準拠デバイスである必要があります。** PC に、ドメインに参加しているか、Intune で設定されたポリシーに準拠していることを求める場合は、このオプションを選択します。 PC がどちらの要件も満たさない場合、ユーザーはデバイスを Intune に登録するように求められます。

     -   **デバイスは準拠デバイスである必要があります** このオプションを選択した場合、PC は Intune に登録され、ポリシーに準拠している必要があります。 PC を登録していない場合は、登録する方法についての手順を示したメッセージが表示されます。

4. SharePoint Online と OneDrive for Business への **[ブラウザー アクセス]** では、サポートされているブラウザー (Safari (iOS)、Chrome (Android)) を通じてのみ、Exchange Online へのアクセスを許可することを選択できます。 その他のブラウザーからのアクセスはブロックされます。 OneDrive のアプリケーションのアクセス用に選択した同じプラットフォームの制限が、ここにも適用されます。

   **Android** デバイスで、ユーザーはブラウザー アクセスを有効にする必要があります。 この操作を行うには、次のようにユーザーが、登録されるデバイスで **[ブラウザー アクセスを有効にする]** オプションを選択する必要があります。
   1.    **ポータル サイト** アプリを開きます。
   2.    省略記号 [...] またはハードウェアのメニュー ボタンから、**[設定]** ページに移動します。
   3.    **[ブラウザー アクセスを有効にする]** ボタンを押します。
   4.    Chrome ブラウザーで Office 365 からサインアウトして、Chrome を再起動します。

   **iOS** および **Android** プラットフォームでは、サービスにアクセスするために使用するデバイスを識別するために、Azure Active Directory はデバイスにトランスポート層セキュリティ (TLS) 証明書を発行します。 デバイスには、次のスクリーン ショットに示すように、証明書を選択するユーザーに対してプロンプトで証明書が表示されます。 ユーザーは、ブラウザーを使用するには、まずこの証明書を選択する必要があります。

   **Android**

   ![iPad での証明書プロンプトのスクリーンショット](../media/mdm-browser-ca-ios-cert-prompt.png)

   **Android**

   ![Android デバイス上の証明書プロンプトのスクリーンショット](../media/mdm-browser-ca-android-cert-prompt.png)
5. **[対象グループ]**で、**[変更]** を選択して、ポリシーを適用する Azure Active Directory セキュリティ グループを選択します。 すべてのユーザーを対象にすることも、選んだユーザーのグループのみを対象にすることもできます。

6. **[例外グループ]**で、必要に応じて **[変更]** を選択して、このポリシーから除外する Azure Active Directory セキュリティ グループを選択します。

7. 終了したら、**[保存]** を選択します。

条件付きアクセス ポリシーを展開する必要はありません。直ちに有効になります。

### <a name="step-4-monitor-the-compliance-and-conditional-access-policies"></a>手順 4. コンプライアンスと条件付きアクセス ポリシーを監視する
**[グループ]** ワークスペースで、デバイスの状態を表示できます。

任意のモバイル デバイス グループを選択します。 次に、**[デバイス]** タブで、次のいずれかの **[フィルター]** を選択します。

-   **AAD に登録されていないデバイス**。 これらのデバイスは SharePoint Online からブロックされます。

-   **準拠していないデバイス**。 これらのデバイスは SharePoint Online からブロックされます。

-   **AAD に登録され、準拠しているデバイス**。 これらのデバイスは SharePoint Online にアクセスできます。

### <a name="see-also"></a>関連項目
[Microsoft Intune を使用して電子メールおよび O365 サービスへのアクセスを保護する](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
