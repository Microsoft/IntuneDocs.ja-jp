---
title: アプリ保護ポリシーの概要
titleSuffix: Microsoft Intune
description: Microsoft Intune のアプリ保護ポリシーが、どのように会社のデータを保護し、データ損失の防止に役立つか説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, get-started, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 31bb0e2ff4379c55829afc65fb99b768c9099a47
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72498954"
---
# <a name="app-protection-policies-overview"></a>アプリ保護ポリシーの概要

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

アプリ保護ポリシー (APP) は、組織のデータが安全な状態にあるか、またはマネージド アプリ内に格納されることを保証するルールです。 ポリシーの例としては、ユーザーが "企業" データへのアクセスまたは移動を試みた場合や、アプリ内で禁止または監視されている一連の操作を試みた場合に適用されるルールがあります。 管理対象アプリは、アプリ保護ポリシーが適用されたアプリであり、Intune で管理できます。

モバイル アプリケーション管理 (MAM) のアプリ保護ポリシーを使用すると、アプリケーション内の組織のデータを管理して保護することができます。 **登録を必要としない MAM** (MAM-WE) を使用すれば、機密データが含まれる職場または学校関連のアプリを、**Bring Your Own Device** (BYOD) シナリオにおける個人所有デバイスを含むほぼすべての[デバイス](app-management.md#app-management-capabilities-by-platform)で管理できます。 Microsoft Office アプリなどの多くの仕事効率化アプリを、Intune MAM で管理することができます。 一般使用が可能な [Microsoft Intune の保護されたアプリ](apps-supported-intune-apps.md)の公式一覧を参照してください。

## <a name="how-you-can-protect-app-data"></a>アプリ データを保護する方法
従業員は個人のタスクと仕事のタスクの両方にモバイル デバイスを使用しています。 従業員の生産性を維持したまま、意図的なデータ損失や意図しないデータ損失が起こらないようにする必要があります。 自分が管理していないデバイスからアクセスされる会社のデータを保護する必要もあります。

Intune のアプリ保護ポリシーは**あらゆるモバイル デバイス管理 (MDM) ソリューションとの依存関係なしで**使用できます。 この独立性により、デバイス管理ソリューションにデバイスを登録しても登録しなくても会社のデータを保護できます。 **アプリレベル ポリシー**を実装するだけで、会社のリソースへのアクセスを制限し、データを IT 部門の管理範囲内に保つことができます。

### <a name="app-protection-policies-on-devices"></a>デバイスでのアプリ保護ポリシー

アプリ保護ポリシーは、次のようなデバイスで実行されているアプリ向けに構成できます。

- **Microsoft Intune に登録されているデバイス:** このようなデバイスは通常、企業所有です。

- **サード パーティ製のモバイル デバイス管理 (MDM) ソリューションに登録されているデバイス:** このようなデバイスは通常、企業所有です。

  > [!NOTE]
  > モバイル アプリ管理ポリシーを、サード パーティのモバイル アプリ管理ソリューションやセキュア コンテナー ソリューションとともに使用しないでください。

- **いずれのモバイル デバイス管理ソリューションにも登録されていないデバイス:** これらのデバイスは通常、Intune またはその他の MDM ソリューションにおいて管理や登録が行われていない従業員所有のデバイスです。

> [!IMPORTANT]
> Office 365 サービスに接続する Office モバイル アプリ向けのモバイル アプリ管理ポリシーを作成することができます。 ハイブリッドの最新認証に対応する iOS および Android 用の Outlook のために Intune アプリ保護ポリシーを作成することで、Exchange オンプレミス メールボックスへのアクセスも保護できます。 この機能を使用する前に、[iOS および Android 用 Outlook の要件](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx)を満たしていることを確認します。 アプリ保護ポリシーは、オンプレミス Exchange サービスや SharePoint サービスに接続する他のアプリではサポートされていません。

## <a name="benefits-of-using-app-protection-policies"></a>アプリ保護ポリシーを利用した場合のメリット

アプリ保護ポリシーを利用した場合の重要なメリットとして、以下が挙げられます。

- **会社データをアプリ レベルで保護します。** モバイル アプリ管理にはデバイス管理が必要ないため、マネージド デバイスとアンマネージド デバイスの両方で会社データを保護することができます。 管理の中心がユーザー ID になり、デバイスを管理する必要がなくなります。

- **エンド ユーザーの生産性に影響を与えることがなく、個人のコンテキストでアプリが使用される場合にはポリシーは適用されません。** ポリシーは仕事のコンテキストでのみ適用されるため、個人データに影響を与えることなく会社データを保護することが可能になります。

- **アプリ保護ポリシーによって、アプリ層の保護を確実に行うことができます。** たとえば、次のように操作できます。
  - 仕事ではアプリを開くとき、PIN を要求する 
  - アプリ間のデータ共有を制御する 
  - 会社アプリのデータを個人ストレージの場所に保存することを禁止する

- **MAM だけでなく MDM を使用することで、確実にデバイスを保護できます**。 たとえば、デバイスへのアクセスに PIN を要求したり、デバイスに管理対象のアプリを展開したりすることができます。 また、MDM ソリューションを介してデバイスにアプリを展開することにより、アプリ管理をより制御できるようになります。

MDM をアプリ保護ポリシーと共に使用することで、MDM ありのアプリ保護ポリシーと MDM なしのアプリ保護ポリシーを社内で同時に使用できるという、新たなメリットが得られます。 たとえば、会社で支給されたスマートフォンと自分のタブレットの両方を使用する社員がいるとします。 会社のスマートフォンは MDM に登録されたうえでアプリ保護ポリシーによって保護されますが、個人のデバイスはアプリ保護ポリシーのみで保護されます。

デバイスの状態を設定せず、ユーザーに MAM ポリシーを適用する場合、ユーザーは、BYOD デバイスと Intune マネージド デバイスの両方で MAM ポリシーを取得します。 管理されている状態に基づいて、MAM ポリシーを適用することもできます。 したがって、アプリ保護ポリシーを作成する場合、**[すべてのアプリの種類を対象にする]** の横の **[いいえ]** を選択します。 次に以下のいずれかを実行します。
- Intune マネージド デバイスに制限が緩い MAM ポリシーを適用し、MDM が登録されていないデバイスにより制限の厳しい MAM ポリシーを適用します。
- 登録解除されたデバイスのみに MAM ポリシーを適用します。

## <a name="supported-platforms-for-app-protection-policies"></a>アプリ保護ポリシーでサポートされているプラットフォーム

Intune では、アプリを実行するデバイス上で必要なアプリを取得するのに役立つさまざまな機能を提供しています。 詳細については、「[App management capabilities by platform (プラットフォーム別のアプリ管理機能)](app-management.md#app-management-capabilities-by-platform)」を参照してください。

Intune アプリの保護ポリシーのプラットフォーム サポートは、Android および iOS デバイス向けの Office モバイル アプリケーションのプラットフォーム サポートと連携しています。 詳細については、[Office システム要件](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg)の「**モバイル アプリ**」セクションを参照してください。

> [!IMPORTANT]
> Android デバイスでアプリ保護ポリシーを受信するには、デバイスに Intune ポータル サイトが必要です。 詳細については、[Intune ポータル サイト アクセス アプリの要件](../fundamentals/end-user-mam-apps-android.md#access-apps)に関するページを参照してください。

## <a name="how-app-protection-policies-protect-app-data"></a>アプリ保護ポリシーでアプリのデータを保護するしくみ

### <a name="apps-without-app-protection-policies"></a>アプリ保護ポリシーのないアプリ

アプリが制限なしで使用されている場合、会社データと個人データが混在する可能性があります。 会社データが個人の記憶域に保存されたり、管理範囲外のアプリに転送されたりして、データ損失を招くことがあります。 次の図の矢印は企業アプリと個人アプリの間のデータ移動やストレージの場所へのデータ移動を示しており、データ移動は制限されていません。

![ポリシーが定められていないアプリ間のデータ移動の概念図](./media/app-protection-policy/apps-without-protection-policies.png)

### <a name="data-protection-with-app-protection-policies-app"></a>アプリ保護ポリシー (APP) によるデータ保護

アプリ保護ポリシーを使用して、デバイスのローカル ストレージに会社のデータが保存されることを禁止できます (下の画像を参照)。 また、アプリ保護ポリシーで保護されていない他のアプリへのデータ移動を制限できます。 アプリ保護ポリシー設定には以下のようなものがあります。
- **[名前を付けて保存] を禁止する**、**切り取り、コピー、貼り付けを制限する**などの、データ再配置ポリシー。
- **アクセスの際にシンプルな PIN を要求する**、**脱獄されたデバイスまたは root 化されたデバイスで管理対象アプリが実行されることを禁止する**など、アクセス ポリシー設定。

![ポリシーによって保護されている会社のデータを示す概念図](./media/app-protection-policy/apps-with-protection-policies.png)

### <a name="data-protection-with-app-on-devices-managed-by-an-mdm-solution"></a>MDM ソリューションによって管理されるデバイス上での APP によるデータ保護

下の図は、MDM とアプリ保護ポリシーの連携によって提供される保護層を示しています。

![BYOD デバイスでアプリ保護ポリシーが機能するしくみを示す画像](./media/app-protection-policy/app-protection-policies-with-mdm.png)

MDM ソリューションでは、次のことを行うと値が追加されます。

- デバイスを登録する
- アプリをデバイスに展開する
- 継続的なデバイスのポリシー準拠と管理を提供する

アプリ保護ポリシーでは、次のことを行うと値が追加されます。

- コンシューマー アプリやサービスに会社データがリークしないように保護を支援する
- "*名前を付けて保存*"、"*クリップボード*"、*PIN* などの制限をクライアント アプリに適用する
- デバイスからアプリを削除せずに、必要時にアプリから会社データをワイプする

### <a name="data-protection-with-app-for-devices-without-enrollment"></a>登録のないデバイスに対する APP によるデータ保護

以下の図は、MDM がない場合にアプリ レベルでデータ保護ポリシーが機能するしくみを示しています。

![登録のないデバイス (非マネージド デバイス) 上でアプリ保護ポリシーが機能するしくみを示した画像](./media/app-protection-policy/app-protection-policies-without-mdm.png)

MDM ソリューションに登録されていない BYOD デバイスでは、アプリ保護ポリシーによってアプリ レベルで会社のデータを保護できます。
ただし、次のようないくつかの制約があることに注意してください。

- アプリをデバイスに展開することはできません。 アプリはエンドユーザーがストアから入手する必要があります。
- これらのデバイスで証明書プロファイルをプロビジョニングすることはできません。
- 会社が Wi-Fi や VPN の設定をこれらのデバイスにプロビジョニングすることはできません。

## <a name="apps-you-can-manage-with-app-protection-policies"></a>アプリ保護ポリシーで管理できるアプリ

Intune アプリ保護ポリシーでは、[Intune アプリ SDK](../developer/app-sdk.md) に統合されたアプリや [Intune アプリ ラッピング ツール](../developer/apps-prepare-mobile-application-management.md) によってラップされたアプリを管理できます。 これらのツールを使用して構築されている一般使用が可能な [Microsoft Intune による保護アプリ](apps-supported-intune-apps.md)の公式一覧を参照してください。

Intune SDK の開発チームは、ネイティブの Android、iOS (Obj-C、Swift)、Xamarin、Xamarin.Forms、および Cordova プラットフォームを使ってビルドされたアプリに対するサポートを、積極的にテストして管理しています。 一部のお客様は、Intune SDK とその他のプラットフォーム (React Native や NativeScript など) の統合に成功されていますが、Microsoft では、サポートされているプラットフォーム以外を使うアプリ開発者に向けた明示的なガイダンスやプラグインは提供されません。

[Intune App SDK](../developer/app-sdk.md) では、ファースト パーティおよびサード パーティ両方のバージョンの SDK に対して、[Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL) による最新の高度な認証機能がいくつか利用されています。 そのため、[Microsoft Authentication Library](https://docs.microsoft.com/azure/active-directory/develop/reference-v2-libraries) (MSAL) は、Intune App Protection サービスへの認証や条件付き起動などの主要なシナリオの多くで、正常に機能しません。 すべての Microsoft Office アプリに対して MSAL に切り替えることが Microsoft の ID チームからの包括的なガイダンスであり、最終的には [Intune App SDK](../developer/app-sdk.md) でサポートされる必要がありますが、今のところ計画はありません。

## <a name="end-user-requirements-to-use-app-protection-policies"></a>アプリ保護ポリシーを使用するためのエンドユーザーの要件

次の一覧に、Intune マネージド アプリ上でアプリ保護ポリシーを使用するためのエンドユーザーの要件を示します。

- エンドユーザーに、Azure Active Directory (AAD) アカウントが必要です。 Azure Active Directory で Intune ユーザーを作成する方法については、「[Intune にユーザーを追加して管理権限を付与する](../fundamentals/users-add.md)」を参照してください。

- エンドユーザーに、Azure Active Directory アカウントに割り当てられた Microsoft Intune のライセンスが必要です。 Intune ライセンスをエンドユーザーに割り当てる方法については、「[Intune のライセンスを管理する](../fundamentals/licenses-assign.md)」を参照してください。

- エンドユーザーは、アプリ保護ポリシーの対象となるセキュリティ グループに属している必要があります。 同一のアプリ保護ポリシーでは、使用中の特定のアプリを対象とする必要があります。 アプリ保護ポリシーは、[Azure Portal](https://portal.azure.com) の Intune コンソールで作成して展開できます。 セキュリティ グループは現在のところ、[Microsoft 365 管理センター](https://admin.microsoft.com)で作成できます。

- エンドユーザーは、AAD アカウントを使用してアプリにサインインする必要があります。

## <a name="app-protection-policies-for-microsoft-office-apps"></a>Microsoft Office アプリに対するアプリ保護ポリシー

Microsoft Office アプリにアプリ保護ポリシーを利用する場合は、いくつかの追加要件に注意してください。

### <a name="outlook-mobile-app"></a>Outlook モバイル アプリ
[Outlook モバイル アプリ](https://products.office.com/outlook)を使用するための追加要件には、以下が含まれます。

- エンドユーザーが、Outlook モバイル アプリをデバイスにインストールしている必要があります。
- エンド ユーザーに、[Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) メールボックスと Azure Active Directory アカウントにリンクされたライセンスが必要です。

  >[!NOTE]
  > 現段階では、Outlook モバイル アプリは Microsoft Exchange Online と[ハイブリッド先進認証を使用する Exchange Server](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) のみをサポートし、Office 365 専用の Exchange はサポートされていません。

### <a name="word-excel-and-powerpoint"></a>Word、Excel、PowerPoint
[Word、Excel、PowerPoint](https://products.office.com/business/office) アプリを使用するための追加要件には、以下が含まれます。

- エンドユーザーに、Azure Active Directory アカウントにリンクされた [Office 365 Business または Office 365 Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) のライセンスが必要です。 サブスクリプションには、モバイル デバイスの Office アプリが含まれている必要があります。また、[OneDrive for Business](https://onedrive.live.com/about/business/) のクラウド ストレージ アカウントを含めることも可能です。 Office 365 ライセンスは、[Microsoft 365 管理センター](https://admin.microsoft.com)で割り当てることができます。[こちら](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)の手順に従ってください。

- エンド ユーザーは、[名前を付けて保存することを禁止] アプリケーション保護ポリシー設定の機能として、詳細保存を使用して管理対象の場所を構成しておく必要があります。 たとえば、管理対象の場所が OneDrive の場合、[OneDrive](https://onedrive.live.com/about/) アプリは、エンド ユーザーの Word アプリ、Excel アプリ、または PowerPoint アプリ内で構成される必要があります。

- 管理対象の場所が OneDrive の場合、アプリは、エンド ユーザーに展開されているアプリの保護ポリシーの対象となる必要があります。

  >[!NOTE]
  > 現段階では、Office モバイル アプリは SharePoint Online のみをサポートし、オンプレミスの SharePoint はサポートされていません。

### <a name="managed-location-needed-for-office"></a>Office に必要な管理される場所
Office には、管理される場所 (OneDrive など) が必要です。 Intune では、アプリ内のすべてのデータが "企業" または "個人用" のいずれかとしてマークされます。 勤務地から送信されたデータは "企業" データと見なされます。 Office アプリについては、Intune では電子メール (Exchange) またはクラウド ストレージ (OneDrive for Business アカウントを使用した OneDrive アプリ) が勤務地と見なされます。

### <a name="skype-for-business"></a>Skype for Business
Skype for Business を使用するためには、追加要件があります。 [Skype for Business](https://products.office.com/skype-for-business/it-pros) のライセンス要件を参照してください。 Skype for Business (SfB) のハイブリッド構成とオンプレミス構成の場合は、「[Hybrid Modern Auth for SfB and Exchange goes GA](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756)」(SfB と Exchange のハイブリッドな最新認証が一般公開) と「[Modern Auth for SfB OnPrem with AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910)」(AAD による SfB オンプレミスの最新認証) をそれぞれ参照してください。

## <a name="app-protection-global-policy"></a>アプリ保護グローバル ポリシー

OneDrive 管理者が **admin.office.com** にアクセスし、**[デバイス]** アクセスを選択するとき、クライアント アプリの OneDrive と SharePoint に**モバイル アプリケーション管理**コントロールを設定できます。 

OneDrive 管理コンソールで利用可能になった設定により、**グローバル** ポリシーという名称の特別な Intune アプリ保護ポリシーが構成されます。 このグローバル ポリシーはテナント内のすべてのユーザーに適用され、ポリシーの対象を制御する手段はありません。 

iOS 向けと Android 向けの OneDrive アプリと SharePoint アプリを有効にすると、既定で、選択した設定でそのアプリが保護されます。 IT の専門家は Intune コンソールでこのポリシーを編集し、対象をもっと絞り込んだ上でアプリを追加したり、ポリシー設定を変更したりできます。 

既定では、**グローバル** ポリシーはテナントごとに 1 つだけとなります。 ただし、推奨されませんが、[Intune Graph API](../developer/intune-graph-apis.md) を使用し、テナントごとにグローバル ポリシーを追加で作成することは可能です。 グローバル ポリシーを追加で作成することが推奨されないのは、そのようなポリシーを実装するとトラブルシューティングが複雑になる可能性があるためです。

**グローバル** ポリシーはテナントのすべてのユーザーに適用されますが、標準 Intune アプリ保護ポリシーによってオーバーライドされます。

## <a name="app-protection-features"></a>アプリ保護機能

### <a name="multi-identity"></a>複数の ID

複数 ID のサポートを利用すると、アプリでは複数の対象ユーザーをサポートできます。 これらの対象ユーザーは、"企業" ユーザーと "個人" ユーザーの両方です。 職場および学校のアカウントは "企業" の対象ユーザーによって使用されるのに対して、個人用アカウントは Microsoft Office ユーザーなどのコンシューマーの対象ユーザーに使用されます。 複数 ID をサポートするアプリは、一般向けにリリースすることができます。その際、アプリ保護ポリシーは、アプリが職場および学校 ("企業") のコンテキストで使用されている場合にのみ適用されます。 複数 ID をサポートする場合、[Intune App SDK](../developer/app-sdk.md) を利用して、アプリにサインインしている職場または学校のアカウントにのみアプリ保護ポリシーが適用されます。 個人用アカウントでアプリにサインインした場合、データは管理されません。

"個人" のコンテキストの例としては、Word で新規ドキュメントに着手するユーザーがいるとした場合、これは個人のコンテキストと見なされるため、Intune App Protection ポリシーは適用されません。 ドキュメントが "企業" の OneDrive アカウントに保存されると、以降は "企業" のコンテキストと見なされ、Intune App Protection ポリシーが適用されます。

仕事または "企業" のコンテキストの例としては、職場のアカウントを利用して OneDrive アプリを起動するユーザーが考えられます。 仕事のコンテキストである場合、個人ストレージの場所にファイルを移動することができません。 後で、個人のアカウントで OneDrive を使用するとき、個人の OneDrive から制限なしでデータをコピーしたり、移動したりできます。

Outlook では、"個人" と "企業" 両方の電子メールが組み合わさった電子メール表示になっています。 この場合、Outlook アプリでは、起動時に Intune PIN の入力が求められます。

Intune での複数 ID の詳細については、[MAM および複数 ID](apps-supported-intune-apps.md) に関する記事を参照してください。

### <a name="intune-app-pin"></a>Intune アプリの PIN

暗証番号 (PIN) は、アプリケーションで適切なユーザーが組織のデータにアクセスしていることを確認するために使用されるパスコードです。

**PIN の入力要求**<br>
Intune では、ユーザーが "企業" データにアクセスしようとした場合にアプリの PIN が要求されます。 Word、Excel、PowerPoint などの複数 ID アプリでは、"企業" のドキュメントやファイルを開こうとすると、ユーザーは PIN の入力を求められます。 [Intune アプリ ラッピング ツール](../developer/apps-prepare-mobile-application-management.md)を使用して管理されている基幹業務アプリなど、単一 ID のアプリでは、[Intune アプリ SDK](../developer/app-sdk.md) によってアプリでのユーザーのエクスペリエンスが常に "企業" であることが把握されるため、起動時に PIN の入力が要求されます。

**PIN の入力要求の頻度**<br>
IT 管理者は、Intune 管理コンソール上で、**[(分数) 後にアクセス要件を再確認する]** という Intune アプリ保護ポリシーの設定を定義できます。 この設定では、デバイスで、アクセス要件がチェックされ、アプリケーションの PIN 画面が再度表示されるまでの時間を指定します。 ただし、PIN に関する以下の内容は重要であり、ユーザーが入力を求められる頻度に影響を与えます。

- **使いやすさの向上のために、同じ公開元のアプリで PIN が共有されます:**<br> iOS 上では、アプリの PIN は、**同じ公開元の**すべてのアプリ間で共有されます。 Android では、アプリの PIN はすべてのアプリで共有されます。
  - **デバイス再起動後の *[(分数) 後に、アクセス要件を再確認する]* の動作:**<br> "PIN タイマー" が非アクティブな時間の分数を追跡し、Intune アプリの PIN を次に表示するタイミングを決定します。 iOS では、PIN タイマーはデバイスの再起動の影響を受けません。 そのため、デバイスの再起動は、Intune PIN ポリシーを使用する iOS アプリからの、ユーザーが非アクティブになっている時間の分数に影響しません。 Android では、PIN タイマーはデバイスの再起動時にリセットされます。 そのため、Intune PIN ポリシーを使用する Android アプリは、[(分数) 後に、アクセス要件を再確認する] の設定値に関係なく、**デバイスの再起動後に**アプリの PIN を要求する場合があります。  
  - **PIN に関連付けられたタイマーのローリングという性質:**<br> PIN を入力してアプリ (アプリ A) にアクセスし、その後、そのアプリがデバイス上のフォアグラウンド (メイン入力フォーカス) を離れると、その PIN の PIN タイマーがリセットされます。 タイマーがリセットされるため、この PIN を共有するアプリ (アプリ B) では、PIN の入力は求められません。 "(分数) 後にアクセス要件を再確認する" の値がもう一度満たされると、再度プロンプトが表示されます。

iOS デバイスの場合、発行元が異なるアプリ間で PIN を共有する場合でも、メイン入力フォーカスではないアプリに対して再度、**[(分数) 後にアクセス要件を再確認する]** 値が満たされると、プロンプトが再表示されます。 そこで、たとえば、ユーザーに発行元 _X_ からのアプリ _A_ と発行元 _Y_ からのアプリ _B_ があるとき、それら 2 つのアプリで同じ PIN が共有されているとします。 ユーザーのフォーカスがアプリ _A_ (前景) にあり、アプリ _B_ は最小化されています。 **[(分数) 後にアクセス要件を再確認する]** 値が満たされ、ユーザーがアプリ _B_ に切り替えると、PIN が必要になります。

  >[!NOTE]
  > ユーザーのアクセス要件の確認頻度をあげるために (PIN のプロンプト)、特に頻繁に使用するアプリにおいて、"(分数) 後にアクセス要件を再確認する" の設定値を下げることをお勧めします。

**Outlook および OneDrive 用の組み込みアプリの PIN**<br>
Intune PIN は、非アクティブ状態をベースとするタイマー (**[(分数) 後に、アクセス要件を再確認する]** の値) を基にして機能します。 そのため、Intune PIN プロンプトは、既定でアプリの起動に関連付けられていることが多い Outlook および OneDrive 用の組み込みのアプリ PIN プロンプトとは独立して表示されます。 ユーザーに両方の PIN プロンプトが同時に表示される場合、Intune PIN が優先される動作が予想されます。

**Intune PIN のセキュリティ**<br>
PIN は、アプリで適切なユーザーのみが組織のデータにアクセスできるようにするためのものです。 そのため、エンドユーザーが Intune アプリの PIN を設定またはリセットするには、職場または学校のアカウントを使用してサインインする必要があります。 この認証は Azure Active Directory によってセキュリティ トークンの交換を通じて処理され、[Intune アプリ SDK ](../developer/app-sdk.md)に対して透過的ではありません。 セキュリティの観点からは、職場または学校のデータを保護する最も効果的な方法は暗号化です。 暗号化はアプリの PIN とは関係しませんが、独自のアプリ保護ポリシーと関係があります。

**Intune PIN - ブルート フォース攻撃からの保護**<br>
IT 管理者は、アプリの PIN ポリシーの一環として、アプリがロックされるまでにユーザーが PIN の認証を試みることのできる最大回数を設定できます。 試行回数に達すると、[Intune アプリ SDK](../developer/app-sdk.md) によってアプリ内の "企業" データをワイプできます。
  
**同じ発行元のアプリ上で PIN を 2 回設定するか**<br>
MAM (iOS 上) では現在、英数字と特殊文字による ("パスコード" と呼ばれる) アプリケーションレベルの PIN が許可されていますが、[iOS 用の Intune アプリ SDK](../developer/app-sdk-ios.md) を統合するには、アプリケーション (WXP、Outlook、Managed Browser、Yammer) の参加が必要です。 これを行わないと、パスコードの設定が対象のアプリケーションに正しく適用されません。 これは iOS 用 Intune SDK の、 バージョン 7.1.12 でリリースされた機能です。

この機能をサポートし、iOS 用 Intune SDK の以前のバージョンとの下位互換性を保証するために、7.1.12 以降の PIN は (数値のものもパスコードも) すべて、以前のバージョンの SDK で使用された数値からなる PIN とは別に扱われます。 そのため公開元が同じで、7.1.12 よりも前のバージョンと後のバージョンの iOS 用 Intune SDK を使用するアプリケーションが、1 つのデバイス上に "両方とも" ある場合、PIN を 2 つ設定する必要があります。 (各アプリの) 2 つの PIN には、いかなる関連性もありません (つまり、アプリに適用されるアプリ保護ポリシーに従う必要があるということです)。 そのため、アプリ A と B に対して、(PIN に関して) 同じポリシーを適用できる場合に "*のみ*"、ユーザーは同じ PIN を 2 回設定できます。 

これは Intune Mobile App Management が有効になっている iOS アプリケーション上の PIN に固有の動作です。 時間の経過とともに、新しいバージョンの iOS 用 Intune SDK が採用されていくと、同じ公開元のアプリに 1 つの PIN を 2 回設定しなくてはならないという問題は減っていきます。 例については、以下の注記をご覧ください。

  >[!NOTE]
  > たとえば、アプリの公開元が同じで、アプリ A が 7.1.12 よりも前のバージョンでビルドされ、アプリ B が 7.1.12 以上のバージョンでビルドされている場合、エンド ユーザーは A と B の両方に別の PIN を設定する必要があります (両方が 1 つの iOS デバイスにインストールされている場合)。
  > SDK バージョン 7.1.9 があるアプリ C がデバイスにインストールされている場合、アプリ A と同じ PIN が共有されます。7.1.14 に組み込まれたアプリ D では、アプリ B と同じ PIN が共有されます。  
  > 1 つのデバイスに アプリ A とアプリ C だけがインストールされている場合、設定する必要がある PIN は 1 つです。 1 つのデバイスに アプリ B とアプリ D だけがインストールされている場合も同様です。

### <a name="app-data-encryption"></a>アプリ データの暗号化
IT 管理者は、アプリ データの暗号化を必須にするアプリ保護ポリシーを展開できます。 ポリシーの一環として、IT 管理者はコンテンツがいつ暗号化されるかを指定することもできます。

**Intune データ暗号化の処理方法**<br> 暗号化のアプリ保護ポリシー設定の詳細については、[Android アプリ保護ポリシーの設定](app-protection-policy-settings-android.md)と [iOS アプリ保護ポリシーの設定](app-protection-policy-settings-ios.md)に関する各記事を参照してください。

**暗号化されたデータ**<br>
IT 管理者のアプリ保護ポリシーに従い、"企業" データとしてマークされたデータのみが暗号化されます。 勤務地から送信されたデータは "企業" データと見なされます。 Office アプリの場合、Intune では、以下をビジネスの場所と見なします。

- 電子メール (Exchange) 
- クラウド ストレージ (OneDrive for Business アカウントを利用する OneDrive アプリ)

[Intune アプリ ラッピング ツール](../developer/apps-prepare-mobile-application-management.md)によって管理された基幹業務アプリでは、すべてのアプリ データが "企業" と見なされます。

**リモートでデータをワイプする**<br>

Intune では、3 つの異なる方法でアプリ データをワイプできます。 
- 完全なデバイスのワイプ
- MDM の選択的なワイプ 
- MAM の選択的なワイプ

MDM のリモート ワイプの詳細については、[ワイプまたはインベントリからの削除を使用してデバイスを削除する方法](../remote-actions/devices-wipe.md)に関するページを参照してください。 MAM を使用した選択的なワイプの詳細については、[インベントリからの削除アクション](../remote-actions/devices-wipe.md#retire)に関するページと[アプリから会社のデータのみをワイプする方法](apps-selective-wipe.md)に関するページを参照してください。

[ワイプ](../remote-actions/devices-wipe.md)では、デバイスを出荷時の既定の設定に戻すことにより、すべてのユーザー データと設定が**デバイス**から削除されます。 デバイスは Intune から削除されません。

  >[!NOTE]
  > ワイプは、Intune モバイル デバイス管理 (MDM) に登録済みのデバイスでのみ行うことができます。

**MDM の選択的なワイプ**<br>
会社データの削除については、[デバイスの削除 - インベントリからの削除](../remote-actions/devices-wipe.md#retire)に関するページを参照してください。

**MAM の選択的なワイプ**<br>
MAM の選択的ワイプは、単にアプリから業務用アプリのデータを削除します。 要求は、Intune Azure Portal を使用して開始されます。 ワイプ要求を開始する方法については、[アプリから企業データのみをワイプする方法](apps-selective-wipe.md)に関するページを参照してください。

選択的なワイプが開始された時点でユーザーがアプリを使用している場合は、[Intune アプリ SDK](../developer/app-sdk.md) によって Intune MAM サービスからの選択的ワイプの要求が 30 分ごとにチェックされます。 ユーザーがアプリを初めて起動し職場または学校のアカウントを使ってサインインした場合も、選択的ワイプがチェックされます。

**オンプレミス (on-prem) サービスが Intune の保護対象アプリと連携しない場合**<br>
Intune アプリ保護は、アプリケーションと [Intune App SDK](../developer/app-sdk.md) の間で一貫性を保つためにユーザーの ID に依存しています。 これを保証する唯一の方法は、最新の認証を使用することです。 アプリをオンプレミス構成と連携させるシナリオはありますが、一貫性がなく保証されていません。

**マネージド アプリから Web リンクを開く安全な方法**<br>
IT 管理者は、Microsoft Intune によって開発された、Intune で簡単に管理可能な Web ブラウザーである [Intune Managed Browser アプリ](app-configuration-managed-browser.md) のアプリ保護ポリシーを展開および設定することができます。 IT 管理者は、Intune 管理対象アプリ内のすべての Web リンクが Managed Browser アプリで開かれるように指定することができます。

## <a name="examples-of-app-protection-policies"></a>アプリ保護ポリシーの例

アプリ保護ポリシーの例を詳しく把握し、各アプリ保護ポリシー設定に関する詳細情報を確認するには、[Android アプリ保護ポリシーの設定](app-protection-policy-settings-android.md)と [iOS アプリ保護ポリシーの設定](app-protection-policy-settings-ios.md)に関する各記事を参照してください。

## <a name="app-protection-experience-for-ios-devices"></a>iOS デバイスでのアプリ保護のエクスペリエンス

### <a name="device-fingerprint-or-face-ids"></a>デバイスの指紋 ID または Face ID 
Intune アプリ保護ポリシーでは、アプリへのアクセスを制御して、Intune のライセンスがあるユーザーのみを許可することができます。 アプリへのアクセスを制御する方法の 1 つは、Apple の Touch ID または Face ID のいずれかをサポートされているデバイス上で要求することです。 Intune は、デバイスの生体認証データベースに何らかの変更が加えられると、次に非アクティブ状態のタイムアウト値に達したときにユーザーに PIN の入力を求めるように実装されています。 フィンガープリントや顔の追加や削除も、生体認証データの変更に含まれます。 Intune ユーザーが PIN を設定していない場合は、Intune PIN を設定するよう求められます。
 
このプロセスの目的は、アプリ内にある組織のデータを、アプリ レベルで安全に保護し続けることです。 この機能は iOS でのみ使用可能で、iOS 向け Intune App SDK のバージョン 9.0.1 以降を統合するアプリケーションの参加が必要です。 SDK の統合は、対象のアプリケーション上で動作を適用するために必要です。 この統合は、ローリング方式で行われ、特定のアプリケーション チームに依存します。 参加するアプリケーションには、WXP、Outlook、Managed Browser、Yammer などが含まれます。
  
### <a name="ios-share-extension"></a>iOS 共有拡張機能
データ転送ポリシーが "**マネージド アプリのみ**" または "**アプリなし**" に設定されている場合であっても、iOS 共有拡張機能を使用すると、アンマネージド アプリ内の職場または学校のデータを開くことができます。 Intune アプリ保護ポリシーは、デバイスを管理しないで iOS 共有拡張機能を制御することはできません。 したがって、Intune は _**"企業" データがアプリの外部で共有される前に、データを暗号化します**_。 マネージド アプリの外部で "企業" ファイルを開いてみると、この暗号化の動作を確認できます。 ファイルは暗号化されていて、管理対象アプリの外部では開くことができないはずです。

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>同じアプリとユーザーのセットに対する複数の Intune アプリ保護アクセスの設定
エンドユーザー デバイスが会社のアカウントから対象のアプリにアクセスしようとすると、アクセスに関する Intune アプリ保護ポリシーが所定の順序で適用されます。 通常、優先順位は、ワイプ、ブロック、無視できる警告となります。 たとえば、特定のユーザー/アプリに適用可能な場合、ユーザーのアクセスをブロックする最小の iOS オペレーティング システム設定の後、iOS バージョンを更新するようユーザーに警告する最小の iOS オペレーティング システム設定が適用されます。 したがって、IT 管理者が最小の iOS オペレーティング システムを 11.0.0.0 に構成し、最小の iOS オペレーティング システム (警告のみ) を 11.1.0.0 に構成した状態で、アプリにアクセスしようとしているデバイスが iOS 10 にあった場合、エンド ユーザーは最小の iOS オペレーティング システム バージョンに対するより制限の厳しい設定に基づいてブロックされ、その結果、アクセスがブロックされます。

さまざまな種類の設定を扱う場合、優先順位は、Intune App SDK のバージョン要件、アプリのバージョン要件、iOS オペレーティング システムのバージョン要件となります。 その後、同じ順序ですべての種類の設定の警告が確認されます。 ブロックが重要である場合は、Intune 製品チームのガイダンスのみに従って、Intune App SDK のバージョン要件を構成することをお勧めします。

## <a name="app-protection-experience-for-android-devices"></a>Android デバイスでのアプリ保護のエクスペリエンス

### <a name="company-portal-app-and-intune-app-protection"></a>ポータル サイト アプリと Intune アプリの保護
アプリ保護機能の多くはポータル サイト アプリに組み込まれています。 デバイスの登録が_不要_な場合でも、ポータル サイト アプリは常に必要です。 登録のないモバイル アプリケーション管理 (MAM-WE) の場合、エンド ユーザーはデバイスにポータル サイト アプリをインストールするだけでかまいません。

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>同じアプリとユーザーのセットに対する複数の Intune アプリ保護アクセスの設定
エンドユーザー デバイスが会社のアカウントから対象のアプリにアクセスしようとすると、アクセスに関する Intune アプリ保護ポリシーが所定の順序で適用されます。 通常、優先順位は、ブロック、無視できる警告となります。 たとえば、特定のユーザー/アプリに適用可能な場合、ユーザーのアクセスをブロックする最小の Android パッチ バージョン設定の後、パッチ アップグレードを実行するようユーザーに警告する最小の Android パッチ バージョン設定が適用されます。 したがって、IT 管理者が最小の Android パッチ バージョンを 2018-03-01 に構成し、最小の Android パッチ バージョン (警告のみ) を 2018-02-01 に構成した状態で、アプリにアクセスしようとしているデバイスがパッチ バージョン 2018-01-01 にあった場合、エンド ユーザーは最小の Android パッチ バージョンに対するより制限の厳しい設定に基づいてブロックされ、その結果、アクセスがブロックされます。 

さまざまな種類の設定を扱う場合、優先順位は、アプリのバージョン要件、Android オペレーティング システムのバージョン要件、Android パッチのバージョン要件となります。 その後、同じ順序ですべての種類の設定の警告が確認されます。

### <a name="intune-app-protection-policies-and-googles-safetynet-attestation-for-android-devices"></a>Android デバイスでの Intune アプリ保護ポリシーと Google の SafetyNet 構成証明 
Intune アプリ保護ポリシーでは、Google の Android デバイス向け SafetyNet 構成証明に合格することをエンドユーザー デバイスに要求する機能を管理者に提供しています。 Google Play サービスに関する新しい決定は、Intune サービスによって決められた間隔で IT 管理者に報告されます。 サービス呼び出しの頻度は負荷に基づいて調整されます。そのため、この値は内部で保守管理され、構成できません。 Google SafetyNet 構成証明設定に対して IT 管理者が構成したアクションは、条件付き起動時に、Intune サービスに最後に報告された結果に基づいて行われます。 データがない場合、他の条件付き起動チェックで不合格にならなければアクセスが許可されます。構成証明結果を決定するための Google Play Service の "ラウンドトリップ" がバックエンドで開始し、デバイスが不合格の場合、ユーザーに非同期で指示が求められます。 データが古い場合、最後に報告された結果に基づいてアクセスが拒否または許可されます。同様に、構成証明結果を決定するための Google Play Service の "ラウンドトリップ" が開始し、デバイスが不合格の場合、ユーザーに非同期で指示が求められます。

### <a name="intune-app-protection-policies-and-googles-verify-apps-api-for-android-devices"></a>Android デバイス対応の Intune アプリ保護ポリシーと Google のアプリの確認 API
Intune App Protection ポリシーでは、Google の Android デバイス向けアプリの確認 API 経由で信号を送信することをエンドユーザー デバイスに要求する機能を管理者に提供しています。 この方法はデバイスごとに若干異なります。 一般的なプロセスでは、Google Play Store に移動し、**[My apps & games]\(アプリとゲーム\)** をアクセスし、最後のアプリ スキャンの結果をクリックします。クリックすると、Play Protect メニューが表示されます。 **[Scan device for security threats]\(端末をスキャンしてセキュリティ上の脅威を確認\)** のトグルが確実にオンになっているようにします。

### <a name="googles-safetynet-attestation-api"></a>Google の SafetyNet 構成証明 API 
Intune は未登録のデバイスに対する既存のルート検出チェックに追加する目的で Google Play Protect SafetyNet API を活用します。 Google は、ルート化されたデバイスでアプリを実行させない場合に採用するよう、Android アプリ向けにこの API セットを開発し、保守管理しています。 Android Pay アプリなどでこれを組み込んでいます。 Google は行われるルート検出チェックの全体を公表しませんが、デバイスをルート化しているユーザーを検出することがこのような API に期待されます。 そのようなユーザーのアクセスをブロックしたり、ポリシーが有効になっているアプリからそのようなユーザーの企業アカウントを消去したりできます。 **基本的な整合性のチェック**では、デバイスの全体的な整合性がわかります。 ルート化されたデバイス、エミュレーター、仮想デバイス、改ざんの兆候があるデバイスは基本的な整合性のチェックで不合格になります。 **基本的な整合性と認定デバイスのチェック**では、デバイスと Google のサービスとの互換性がわかります。 Google に認められた、改造されていないデバイスのみがこのチェックに合格します。 不合格になるデバイス:

- 基本的な整合性のチェックで不合格になるデバイス
- ブートローダーがロックされていないデバイス
- カスタム システム イメージ/ROM が含まれるデバイス
- メーカーが Google 認定に申し込まなかった、あるいは合格しなかったデバイス
- Android オープン ソース プログラムのソース ファイルから直接構築されたシステム イメージを含むデバイス
- ベータ版/開発者プレビューのシステム イメージを含むデバイス

技術的な詳細については、「[Google's documentation on the SafetyNet Attestation](https://developer.android.com/training/safetynet/attestation)」 (SafetyNet 構成証明に関する Google の文書) を参照してください。

### <a name="safetynet-device-attestation-setting-and-the-jailbrokenrooted-devices-setting"></a>SafetyNet デバイスの構成証明設定と "脱獄またはルート化されたデバイス" の設定
Google Play Protect の SafetyNet API チェックでは、エンド ユーザーがオンラインになっていることが要求されます。少なくとも構成証明結果を決定するための "ラウンドトリップ" の実行中はオンラインになっている必要があります。 エンド ユーザーがオフラインになっている場合でも、IT 管理者は引き続き **[脱獄またはルート化されたデバイス]** 設定からの結果の適用を期待できます。 しかし、エンド ユーザーがオフラインになっている時間が長すぎると、**[オフラインの猶予期間]** の値が作動し、タイマー値に到達すると、ネットワーク アクセスが利用できるようになるまで、職場または学校のデータへのアクセスがすべて遮断されます。 両方の設定をオンにすると、階層的な手法でエンド ユーザー デバイスの正常性が維持されます。これは、エンドユーザーがモバイル端末上で職場または学校のデータにアクセスする場合に重要です。

### <a name="google-play-protect-apis-and-google-play-services"></a>Google Play プロテクト API と Google Play 開発者サービス
Google Play プロテクトの API を活用するアプリ保護ポリシー設定を利用するには、Google Play 開発者サービスが機能する必要があります。 **[SafetyNet デバイスの構成証明]** と **[アプリの脅威のスキャン]** 設定の両方において、Google によって決められたバージョンの Google Play 開発者サービスが正しく機能する必要があります。 これらはセキュリティの領域に属する設定であるため、エンド ユーザーはこれらの設定の対象となっているとき、Google Play 開発者サービスのバージョンが適切でない、あるいは Google Play 開発者サービスにアクセスできない場合はブロックされます。

## <a name="next-steps"></a>次の手順

[Microsoft Intune でアプリ保護ポリシーを作成および展開する方法](app-protection-policies.md)

## <a name="see-also"></a>関連項目
Salesforce モバイル アプリなどのサード パーティ製アプリは特別な方法で Intune と連携して企業データを保護します。 Salesforce アプリが特に Intune と連携する方法の詳細 (MDM アプリ構成の設定を含む) については、「[Salesforce App and Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf)」 (Salesforce アプリと Microsoft Intune) を参照してください。
