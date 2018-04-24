---
title: MAM ポリシーでアプリ データを保護する
description: このトピックでは、モバイル アプリケーション管理ポリシーが、会社データの保護、データ損失の防止、および個人用情報と作業情報の個別管理に役立つしくみについて説明します。
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: dcdee874e42aa9511c09fda43a8cc662afaea38a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="protect-app-data-using-app-protection-policies-with-microsoft-intune"></a>Microsoft Intune でアプリ保護ポリシーを使用してアプリ データを保護する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="how-you-can-protect-app-data"></a>アプリ データを保護する方法
従業員は個人のタスクと仕事のタスクの両方にモバイル デバイスを使用しています。 従業員の生産性を維持したまま、意図的なデータ損失や意図しないデータ損失が起こらないようにする必要があります。  さらに、会社が管理していないデバイスを使用して従業員がアクセスする会社のデータを保護できるようにします。

Intune のアプリ保護ポリシーを使用すれば、会社のデータを保護できます。 Intune のアプリ保護ポリシーは**どのモバイル デバイス管理 (MDM) ソリューションからも独立して**利用できるため、デバイスをデバイス管理ソリューションに登録しているかどうかにかかわらず、MAM を利用して会社のデータを保護することができます。 **アプリレベル ポリシー**を実装するだけで、会社のリソースへのアクセスを制限し、データを IT 部門の管理範囲内に保つことができます。

次のようなデバイスで実行されているアプリに対して、アプリ保護ポリシーを構成することができます。

-   **Microsoft Intune に登録されているデバイス:** このカテゴリに属するデバイスは、通常、企業所有デバイスです。

-   **サードパーティの MDM ソリューションに登録されているデバイス:** このカテゴリに属するデバイスは、通常、企業所有デバイスです。

    > [!NOTE]
    > サードパーティのモバイル アプリケーション管理ソリューションやセキュア コンテナー ソリューションでアプリ保護ポリシーを使用することはお勧めしません。

-   **いずれの MDM ソリューションにも登録されていないデバイス:** このカテゴリに属するデバイスは、通常、Intune またはその他の MDM ソリューションで管理も登録もされていない社員所有のデバイスです。

> [!IMPORTANT]
> Office 365 サービスに接続する Office モバイル アプリ向けのアプリ保護ポリシーを作成することができます。 アプリ保護ポリシーは、オンプレミスの Exchange サービスや Skype for Business サービス、SharePoint サービスに接続するアプリ向けにはサポートされていません。

## <a name="benefits-of-using-app-protection-policies"></a>アプリ保護ポリシーを利用した場合のメリット

-   **アプリ レベルでの会社データの保護に役立ちます。** モバイル アプリケーション管理にはデバイス管理が必要ないため、管理対象のデバイスと管理対象ではないデバイスの両方で会社データを保護することができます。 管理の中心がユーザー ID になり、デバイスを管理する必要がなくなります。

-   **ユーザーの生産性に影響を与えることがなく、個人のコンテキストでアプリが使用される場合にはポリシーは適用されません。** ポリシーは仕事のコンテキストでのみ適用されるため、個人データに影響を与えることなく会社データを保護することが可能になります。

MDM をアプリ保護ポリシーと共に使用することには付加的なメリットがあります。会社は MAM を MDM ありと MDM なしの両方で同時に使用できます。 たとえば、従業員は、会社が支給する電話に加えて個人のタブレットを使用する場合があります。 この場合、会社の電話は MDM に登録されたうえでアプリ保護ポリシーによって保護されますが、個人のデバイスはアプリ保護ポリシーのみで保護されます。

- **MDM によりデバイスの保護を実現できます。** たとえば、デバイスへのアクセスに PIN を要求したり、デバイスに管理対象のアプリを展開したりすることができます。 また、MDM ソリューションを介してデバイスにアプリを展開することにより、アプリ管理をより制御できるようになります。

- **アプリ保護ポリシーによりアプリ層の保護を実現できます**。 たとえば、仕事のコンテキストでアプリを開くために PIN を要求したり、アプリ間でのデータの共有を禁止したり、会社のアプリ データを個人の記憶域に保存できないようにしたりするポリシーを作成できます。

## <a name="devices-that-support-mam"></a>MAM をサポートするデバイス
Intune アプリの保護ポリシーのプラットフォーム サポートは、Office アプリケーションのプラットフォーム サポートと連携しています。 詳細については、「[Office のシステム要件](https://products.office.com/en-US/office-system-requirements)」を参照してください。

>[!NOTE]
>Windows デバイスに登録シナリオがなく、MAM でサポートされていません。 ただし、Intune で Windows 10 デバイスを登録すると、同様の機能を提供する Windows 情報保護を使用できます。 詳細については、「[Protect your enterprise data using Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)」 (Windows 情報保護 (WIP) を使用してエンタープライズ データを保護する) を参照してください。


##  <a name="how-app-protection-policies-protect-app-data"></a>アプリ保護ポリシーでアプリのデータを保護するしくみ

###  <a name="apps-without-app-protection-policies"></a>アプリ保護ポリシーのないアプリ

![アプリ保護ポリシーが配備されていない場合にデータがアプリ間をどのようにして自由に移動できるかを示すイメージ](../media/Apps_without_MAM_policies.png)

アプリを制限なしで使用すると、会社データと個人データが混在する可能性があります。 会社データが個人の記憶域に保存されたり、管理範囲外のアプリに転送されたりして、データが損失することがあります。 図の矢印はアプリ (会社と個人) と記憶域の間の制限されたデータ移動を示しています。

### <a name="data-protection-with-app-protection-policies"></a>アプリ保護ポリシーによるデータ保護

![アプリ保護ポリシーが適用されている場合に会社のデータがどのように保護されるかを示すイメージ](../media/Apps_with_mobile_app_policies.png)

アプリ保護ポリシーを使用すれば、会社のデータがデバイスのローカル ストレージに保存されるのを防止し、アプリ保護ポリシーで保護されていない他のアプリへのデータの移動を制限することができます。 アプリ保護ポリシー設定には以下のようなものがあります。
- **[名前を付けて保存] を禁止する**、**切り取り、コピー、貼り付けを制限する** のようなデータ再配置ポリシー。
- **アクセスの際にシンプルな PIN を要求する**、**脱獄されたデバイスまたは root 化されたデバイスで管理対象アプリが実行されることを禁止する**のようなアクセス ポリシー設定。

### <a name="data-protection-with-app-protection-on-devices-that-are-managed-by-a-mdm-solution"></a>MDM ソリューションで管理されるデバイスのアプリ保護ポリシーによるデータ保護

![Bring Your Own Devices (BYOD) デバイスでアプリ保護ポリシーが機能するしくみを示すイメージ](../media/MAM_BYOD_November.png)

**MDM ソリューションに登録されているデバイスの場合**: 前の図は、MDM とアプリ保護ポリシーによって提供される保護の各層を示しています。

MDM ソリューション:

-   デバイスを登録します。

-   アプリをデバイスに展開します。

-   継続的なデバイスのポリシー準拠と管理を提供します。

**アプリ保護ポリシーが価値を高める理由:**

-   コンシューマー アプリやサービスに会社データがリークしないように支援します。

-   モバイル アプリに制限を適用します (名前を付けて保存、クリップボード、PIN など)。

-   デバイスからアプリを削除しないで、アプリから会社データをワイプします。


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>登録されていないデバイスでのアプリ保護ポリシーによるデータ保護

![管理対象デバイスでアプリ保護ポリシーが機能するしくみを示すイメージ](../media/MAM_ManagedDevices_November.png)

上の図は、MDM がない場合にアプリ レベルでデータ保護ポリシーが機能するしくみを示しています。

MDM ソリューションに登録されていない BYOD デバイスでは、アプリ保護ポリシーによってアプリ レベルで会社のデータを保護できます。

ただし、次のようないくつかの制約があることに注意してください。

-   アプリをデバイスに展開することはできません。 アプリはユーザーがストアから入手する必要があります。

-   これらのデバイスで証明書プロファイルをプロビジョニングすることはできません。

-   会社が Wi-Fi や VPN の設定をこれらのデバイスにセットアップすることはできません。


## <a name="multi-identity"></a>複数の ID

複数の ID をサポートするアプリの場合、アプリが作業コンテキストで利用されているときにアプリ保護ポリシーが適用されていれば、仕事用や個人用など、複数のアカウントを利用して同じアプリにアクセスできます。  

たとえば、ユーザーが仕事用のアカウントを使用して OneDrive アプリを開始した場合、個人のストレージにファイルを移動できません。 ただし、ユーザーが個人のアカウントで OneDrive を使用する場合、個人の OneDrive から制限なしでデータをコピーしたり、移動したりできます。  

- Intune で [MAM と複数の ID](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) をサポートするアプリについての詳細を参照してください。

##  <a name="next-steps"></a>次の手順
- [アプリ保護ポリシーを構成する準備をする](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

- [Microsoft Intune でのアプリ保護ポリシーの作成と展開](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)
