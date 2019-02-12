---
title: アプリ保護ポリシーとは
titleSuffix: Microsoft Intune
description: Microsoft Intune のアプリ保護ポリシーが、どのように会社のデータを保護し、データ損失の防止に役立つか説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbb6a8f159aebe837fabf671a84dd96223298227
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836355"
---
# <a name="what-are-app-protection-policies"></a>アプリ保護ポリシーとは


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune のアプリ保護ポリシーは、会社のデータを保護し、データ損失を防ぐために役立ちます。

## <a name="how-you-can-protect-app-data"></a>アプリ データを保護する方法
従業員は個人のタスクと仕事のタスクの両方にモバイル デバイスを使用しています。 従業員の生産性を維持したまま、意図的なデータ損失や意図しないデータ損失が起こらないようにする必要があります。 自分が管理していないデバイスからアクセスされる会社のデータを保護する必要もあります。

Intune のアプリ保護ポリシーは**あらゆるモバイル デバイス管理 (MDM) ソリューションとの依存関係なしで**使用できます。 この独立性により、デバイス管理ソリューションにデバイスを登録しても登録しなくても会社のデータを保護できます。 **アプリレベル ポリシー**を実装するだけで、会社のリソースへのアクセスを制限し、データを IT 部門の管理範囲内に保つことができます。

アプリ保護ポリシーは、次のようなデバイスで実行されているアプリ向けに構成できます。

- **Microsoft Intune に登録されているデバイス:** このようなデバイスは通常、企業所有です。

- **サード パーティ製のモバイル デバイス管理 (MDM) ソリューションに登録されているデバイス:** このようなデバイスは通常、企業所有です。

  > [!NOTE]
  > モバイル アプリ管理ポリシーを、サード パーティのモバイル アプリ管理ソリューションやセキュア コンテナー ソリューションとともに使用しないでください。

- **いずれのモバイル デバイス管理ソリューションにも登録されていないデバイス:** このようなデバイスは、通常、Intune またはその他の MDM ソリューションで管理も登録もされていない社員所有のデバイスです。

> [!IMPORTANT]
> Office 365 サービスに接続する Office モバイル アプリ向けのモバイル アプリ管理ポリシーを作成することができます。 ハイブリッドの最新認証に対応する iOS および Android 用の Outlook のために Intune アプリ保護ポリシーを作成することで、Exchange オンプレミス メールボックスへのアクセスも保護できます。 この機能を使用する前に、[iOS および Android 用 Outlook の要件](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx)を満たしていることを確認します。 アプリ保護ポリシーは、オンプレミス Exchange サービスや SharePoint サービスに接続する他のアプリではサポートされていません。

**アプリ保護ポリシーを利用した場合の主なメリットとしては、以下のようなものがあります。**

-   アプリ レベルで、会社データを保護します。 モバイル アプリ管理にはデバイス管理が必要ないため、マネージド デバイスとアンマネージド デバイスの両方で会社データを保護することができます。 管理の中心がユーザー ID になり、デバイスを管理する必要がなくなります。

-   エンド ユーザーの生産性に影響を与えることがなく、個人のコンテキストでアプリが使用される場合にはポリシーは適用されません。 ポリシーは仕事のコンテキストでのみ適用されるため、個人データに影響を与えることなく会社データを保護することが可能になります。

MDM をアプリ保護ポリシーと共に使用することで、MDM ありのアプリ保護ポリシーと MDM なしのアプリ保護ポリシーを社内で同時に使用できるという、新たなメリットが得られます。 たとえば、会社で支給されたスマートフォンと自分のタブレットの両方を使用する社員がいるとします。 会社のスマートフォンは MDM に登録されたうえでアプリ保護ポリシーによって保護されますが、個人のデバイスはアプリ保護ポリシーのみで保護されます。

- **MDM によりデバイスの保護を実現できる**。 たとえば、デバイスへのアクセスに PIN を要求したり、デバイスに管理対象のアプリを展開したりすることができます。 また、MDM ソリューションを介してデバイスにアプリを展開することにより、アプリ管理をより制御できるようになります。

- **アプリ保護ポリシーによりアプリ層の保護を実現できる**。 たとえば、次のように操作できます。
  - 仕事ではアプリを開くとき、PIN を要求する 
  - アプリ間のデータ共有を制御する 
  - 会社アプリのデータを個人ストレージの場所に保存することを禁止する


### <a name="supported-platforms-for-app-protection-policies"></a>アプリ保護ポリシーでサポートされているプラットフォーム
Intune アプリの保護ポリシーのプラットフォーム サポートは、Android および iOS デバイス向けの Office モバイル アプリケーションのプラットフォーム サポートと連携しています。 詳細については、[Office システム要件](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg)の「**モバイル アプリ**」セクションを参照してください。

Windows デバイスは現在サポートされていません。 ただし、同様の機能を提供する Windows 情報保護を使用できます。 詳細については、「[Protect your enterprise data using Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)」 (Windows 情報保護 (WIP) を使用してエンタープライズ データを保護する) を参照してください。


## <a name="how-app-protection-policies-protect-app-data"></a>アプリ保護ポリシーでアプリのデータを保護するしくみ

#### <a name="apps-without-app-protection-policies"></a>アプリ保護ポリシーのないアプリ

![ポリシーが定められていないアプリ間のデータ移動の概念図](./media/apps-without-protection-policies.png)

アプリが制限なしで使用されている場合、会社データと個人データが混在する可能性があります。 会社データが個人の記憶域に保存されたり、管理範囲外のアプリに転送されたりして、データ損失を招くことがあります。 先の図の矢印は企業アプリと個人アプリの間のデータ移動やストレージの場所へのデータ移動を示しており、データ移動は制限されています。


### <a name="data-protection-with-app-protection-policies"></a>アプリ保護ポリシーによるデータ保護

![ポリシーによって保護されている会社のデータを示す概念図](./media/apps-with-protection-policies.png)


アプリ保護ポリシーを使用し、デバイスのローカル ストレージに会社のデータが保存されることを禁止できます。 また、アプリ保護ポリシーで保護されていない他のアプリへのデータ移動を制限できます。 アプリ保護ポリシー設定には以下のようなものがあります。
- **[名前を付けて保存] を禁止する**、**切り取り、コピー、貼り付けを制限する**など、データ再配置ポリシー。
- **アクセスの際にシンプルな PIN を要求する**、**脱獄されたデバイスまたは root 化されたデバイスで管理対象アプリが実行されることを禁止する**など、アクセス ポリシー設定。

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mobile-device-management-solution"></a>モバイル デバイス管理ソリューションで管理されているデバイスでのアプリ保護ポリシーによるデータ保護

![BYOD デバイスでアプリ保護ポリシーが機能するしくみを示す画像](./media/app-protection-policies-with-mdm.png)

**MDM ソリューションに登録されているデバイスの場合**-

先の図は、MDM とアプリ保護ポリシーの連携によって提供される保護層を示しています。

MDM ソリューション:

-   デバイスを登録する

-   アプリをデバイスに展開する

-   継続的なデバイスのポリシー準拠と管理を提供する

**アプリ保護ポリシーによる追加機能:**

-   コンシューマー アプリやサービスに会社データがリークしないように支援する

-   *名前を付けて保存*、*クリップボード*、*PIN* などの制限をクライアント アプリに適用する

-   アプリから会社データをワイプし、その際にデバイスからそのアプリを削除しない


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>未登録デバイスでのアプリ保護ポリシーによるデータ保護

![マネージド デバイスでアプリ保護ポリシーが機能するしくみを示す画像](./media/app-protection-policies-without-mdm.png)

上の図は、MDM がない場合にアプリ レベルでデータ保護ポリシーが機能するしくみを示しています。

MDM ソリューションに登録されていない BYOD デバイスでは、アプリ保護ポリシーによってアプリ レベルで会社のデータを保護できます。
ただし、次のようないくつかの制約があることに注意してください。

-   アプリをデバイスに展開することはできません。 アプリはエンドユーザーがストアから入手する必要があります。

-   これらのデバイスで証明書プロファイルをプロビジョニングすることはできません。

-   会社が Wi-Fi や VPN の設定をこれらのデバイスにプロビジョニングすることはできません。

## <a name="app-protection-global-policy"></a>アプリ保護グローバル ポリシー

OneDrive 管理者が **admin.office.com** にアクセスし、**[デバイス]** アクセスを選択するとき、クライアント アプリの OneDrive と SharePoint に**モバイル アプリケーション管理**コントロールを設定できます。 

OneDrive 管理コンソールで利用可能になった設定により、**グローバル** ポリシーという名称の特別な Intune アプリ保護ポリシーが構成されます。 このグローバル ポリシーはテナント内のすべてのユーザーに適用され、ポリシーの対象を制御する手段はありません。 

iOS 向けと Android 向けの OneDrive アプリと SharePoint アプリを有効にすると、既定で、選択した設定でそのアプリが保護されます。 IT の専門家は Intune コンソールでこのポリシーを編集し、対象をもっと絞り込んだ上でアプリを追加したり、ポリシー設定を変更したりできます。 

既定では、**グローバル** ポリシーはテナントごとに 1 つだけとなります。 ただし、推奨されませんが、[Intune Graph API](intune-graph-apis.md) を使用し、テナントごとにグローバル ポリシーを追加で作成することは可能です。 グローバル ポリシーを追加で作成することが推奨されないのは、そのようなポリシーを実装するとトラブルシューティングが複雑になる可能性があるためです。

**グローバル** ポリシーはテナントのすべてのユーザーに適用されますが、標準 Intune アプリ保護ポリシーによってオーバーライドされます。


## <a name="multi-identity"></a>複数の ID

複数の ID をサポートするアプリの場合、仕事用や個人用など、複数のアカウントを利用して同じアプリにアクセスできます。アプリが仕事で利用されているときにのみ、アプリ保護ポリシーが適用されます。

個人のコンテキストの例としては、Word で新しいドキュメントの作成を開始するユーザーがいるとします。これは個人のコンテキストと見なされるため、Intune App Protection ポリシーは適用されません。 ドキュメントが企業の OneDrive アカウントに保存された後は、企業のコンテキストと見なされ、Intune App Protection ポリシーが適用されます。

仕事のコンテキストの例としては、仕事用アカウントを利用して OneDrive アプリを起動する人がいるとします。 仕事のうちに入る場合、個人ストレージの場所にファイルを移動することができません。 後で、個人のアカウントで OneDrive を使用するとき、個人の OneDrive から制限なしでデータをコピーしたり、移動したりできます。

- Intune で [MAM と複数の ID](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) をサポートするアプリについての詳細を参照してください。

## <a name="next-steps"></a>次の手順

[Microsoft Intune でアプリ保護ポリシーを作成および展開する方法](app-protection-policies.md)

## <a name="see-also"></a>関連項目
Salesforce モバイル アプリなどのサード パーティ製アプリは特別な方法で Intune と連携して企業データを保護します。 Salesforce アプリが特に Intune と連携する方法の詳細 (MDM アプリ構成の設定を含む) については、「[Salesforce App and Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf)」 (Salesforce アプリと Microsoft Intune) を参照してください。
