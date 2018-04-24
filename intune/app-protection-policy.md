---
title: アプリ保護ポリシーとは
titleSuffix: Microsoft Intune
description: Microsoft Intune のアプリ保護ポリシーが、どのように会社のデータを保護し、データ損失の防止に役立つか説明します。
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 01/19/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c4483baa68267b7a7218a4e78fe5275d1ea8d330
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="what-are-app-protection-policies"></a>アプリ保護ポリシーとは


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune のアプリ保護ポリシーは、会社のデータを保護し、データ損失を防ぐために役立ちます。

## <a name="how-you-can-protect-app-data"></a>アプリ データを保護する方法
従業員は個人のタスクと仕事のタスクの両方にモバイル デバイスを使用しています。  従業員の生産性を維持したまま、意図的なデータ損失や意図しないデータ損失が起こらないようにする必要があります。  また、デバイスを自分で管理していない場合でも、そのデバイスでアクセスされる会社のデータを保護する機能があれば便利です。

Intune のアプリ保護ポリシーを使用すれば、会社のデータを保護できます。 Intune のアプリ保護ポリシーは**どのモバイル デバイス管理 (MDM) ソリューションからも独立して**利用できるため、デバイスをデバイス管理ソリューションに登録しているかどうかにかかわらず、これを利用して会社のデータを保護することができます。 **アプリレベル ポリシー**を実装するだけで、会社のリソースへのアクセスを制限し、データを IT 部門の管理範囲内に保つことができます。

アプリ保護ポリシーは、次のようなデバイスで実行されているアプリ向けに構成できます。

- **Microsoft Intune に登録されているデバイス:** このカテゴリに属するデバイスは、通常、企業所有デバイスです。

- **サード パーティ製のモバイル デバイス管理 (MDM) ソリューションに登録されているデバイス:** このカテゴリに属するデバイスは、通常、企業所有デバイスです。

  > [!NOTE]
  > モバイル アプリ管理ポリシーを、サード パーティのモバイル アプリ管理ソリューションやセキュア コンテナー ソリューションとともに使用しないでください。

- **いずれのモバイル デバイス管理ソリューションにも登録されていないデバイス:** このカテゴリに属するデバイスは、通常、Intune またはその他の MDM ソリューションで管理も登録もされていない社員所有のデバイスです。

> [!IMPORTANT]
> Office 365 サービスに接続する Office モバイル アプリ向けのモバイル アプリ管理ポリシーを作成することができます。 アプリ保護ポリシーは、オンプレミス Exchange サービスや SharePoint サービスに接続するアプリではサポートされていません。

**アプリ保護ポリシーを利用した場合の主なメリットとしては、以下のようなものがあります。**

-   アプリ レベルで、会社データを保護します。  モバイル アプリ管理にはデバイス管理が必要ないため、管理対象のデバイスと管理対象ではないデバイスの両方で会社データを保護することができます。 管理の中心がユーザー ID になり、デバイスを管理する必要がなくなります。

-   エンド ユーザーの生産性に影響を与えることがなく、個人のコンテキストでアプリが使用される場合にはポリシーは適用されません。  ポリシーは仕事のコンテキストでのみ適用されるため、個人データに影響を与えることなく会社データを保護することが可能になります。

MDM をアプリ保護ポリシーと共に使用することで、MDM ありのアプリ保護ポリシーと MDM なしのアプリ保護ポリシーを社内で両方同時に使用できるという、新たなメリットが得られます。 たとえば、従業員は、会社が支給する電話に加えて個人のタブレットを使用する場合があります。  この場合、会社の電話は MDM に登録されたうえでアプリ保護ポリシーによって保護されますが、個人のデバイスはアプリ保護ポリシーのみで保護されます。

- **MDM によりデバイスの保護を実現できる**。  たとえば、デバイスへのアクセスに PIN を要求したり、デバイスに管理対象のアプリを展開したりすることができます。 また、MDM ソリューションを介してデバイスにアプリを展開することにより、アプリ管理をより制御できるようになります。

- **アプリ保護ポリシーによりアプリ層の保護を実現できる**。 たとえば、仕事のコンテキストでアプリを開くために PIN を要求したり、アプリ間でデータを共有できるかどうかを決めたり、会社のアプリ データを個人の記憶域に保存できないようにしたりできます。


### <a name="supported-platforms-for-app-protection-polices"></a>アプリ保護ポリシーでサポートされているプラットフォーム
Intune アプリの保護ポリシーのプラットフォーム サポートは、Office アプリケーションのプラットフォーム サポートと連携しています。 詳細については、「[Office のシステム要件](https://products.office.com/en-US/office-system-requirements)」を参照してください。

Windows デバイスは現在サポートされていません。 ただし、Intune で Windows 10 デバイスを登録すると、同様の機能を提供する Windows 情報保護を使用できます。 詳細については、「[Protect your enterprise data using Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)」 (Windows 情報保護 (WIP) を使用してエンタープライズ データを保護する) を参照してください。
##  <a name="how-app-protection-policies-protect-app-data"></a>アプリ保護ポリシーでアプリのデータを保護するしくみ

####  <a name="apps-without-app-protection-policies"></a>アプリ保護ポリシーのないアプリ

![アプリ保護ポリシーが配備されていない場合にデータがアプリ間を自由に移動できることを示す画像](./media/apps-without-protection-policies.png)

アプリが制限なしで使用されている場合、会社データと個人データが混在する可能性があります。  会社データが個人の記憶域に保存されたり、管理範囲外のアプリに転送されたりして、データが損失することがあります。 図の矢印はアプリ (会社と個人) と記憶域の間の制限されたデータ移動を示しています。


### <a name="data-protection-with-app-protection-policies"></a>アプリ保護ポリシーによるデータ保護

![アプリ保護ポリシーが適用されている場合に会社のデータがどのように保護されるかを示す画像 ](./media/apps-with-protection-policies.png)


アプリ保護ポリシーを使用すれば、会社のデータがデバイスのローカル ストレージに保存されるのを防止し、アプリ保護ポリシーで保護されていない他のアプリへのデータの移動を制限することができます。 アプリ保護ポリシー設定には以下のようなものがあります。
- **[名前を付けて保存] を禁止する**、**切り取り、コピー、貼り付けを制限する** のようなデータ再配置ポリシー。
- **アクセスの際にシンプルな PIN を要求する**、**脱獄されたデバイスまたは root 化されたデバイスで管理対象アプリが実行されることを禁止する**のようなアクセス ポリシー設定。

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mdm-solution"></a>MDM ソリューションで管理されているデバイスでのアプリ保護ポリシーによるデータ保護

![BYOD デバイスでアプリ保護ポリシーが機能するしくみを示す画像](./media/app-protection-policies-with-mdm.png)

**MDM ソリューションに登録されているデバイスの場合**-

上の図は、MDM とアプリ保護ポリシーの連携によって提供される保護層を示しています。

MDM ソリューション:

-   デバイスを登録する

-   アプリをデバイスに展開する

-   継続的なデバイスのポリシー準拠と管理を提供する

**アプリ保護ポリシーによる追加機能:**

-   コンシューマー アプリやサービスに会社データがリークしないように支援する

-   モバイル アプリへの制限の適用 (名前を付けて保存、クリップボード、PIN など)

-   アプリから会社データをワイプし、その際にデバイスからそのアプリを削除しない


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>未登録デバイスでのアプリ保護ポリシーによるデータ保護

![管理対象デバイスでアプリ保護ポリシーが機能するしくみを示す画像](./media/app-protection-policies-without-mdm.png)

上の図は、MDM がない場合にアプリ レベルでデータ保護ポリシーが機能するしくみを示しています。

MDM ソリューションに登録されていない BYOD デバイスでは、アプリ保護ポリシーによってアプリ レベルで会社のデータを保護できます。
ただし、次のようないくつかの制約があることに注意してください。

-   アプリをデバイスに展開することはできません。  アプリはエンドユーザーがストアから入手する必要があります。

-   これらのデバイスで証明書プロファイルをプロビジョニングすることはできません。

-   会社が Wi-Fi や VPN の設定をこれらのデバイスにプロビジョニングすることはできません。


## <a name="multi-identity"></a>複数の ID

複数の ID をサポートするアプリの場合、アプリが作業コンテキストで利用されているときにアプリ保護ポリシーが適用されていれば、仕事用や個人用など、複数のアカウントを利用して同じアプリにアクセスできます。

たとえば、ユーザーが仕事用のアカウントを使用して OneDrive アプリを開始した場合、個人のストレージにファイルを移動できません。 ただし、ユーザーが個人のアカウントで OneDrive を使用する場合、個人の OneDrive から制限なしでデータをコピーしたり、移動したりできます。

- Intune で [MAM と複数の ID](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) をサポートするアプリについての詳細を参照してください。

##  <a name="next-steps"></a>次の手順

[Microsoft Intune でアプリ保護ポリシーを作成および展開する方法](app-protection-policies.md)

## <a name="see-also"></a>関連項目
Salesforce モバイル アプリなどのサード パーティ製アプリは特定の方法で Intune と連携して企業データを保護します。 Salesforce アプリが特に Intune と連携する方法の詳細 (MDM アプリ構成の設定を含む) については、「[Salesforce App and Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf)」 (Salesforce アプリと Microsoft Intune) を参照してください。
