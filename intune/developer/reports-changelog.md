---
title: Intune データ ウェアハウスの変更ログ
titleSuffix: Microsoft Intune
description: このトピックには、Microsoft Intune データ ウェアハウス API の変更の一覧が記載されています。
keywords: Intune データ ウェアハウス
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9740eed3ab727d76a9af4e46642d8279b310fd9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490526"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Intune データ ウェアハウス API の変更ログ

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

常に Intune データ ウェアハウスの最新の更新プログラムをインストールしてください。

## <a name="1903-part-2"></a>1903 (パート 2)
_リリース日: 2019 年 4 月_

### <a name="beta-changes"></a>ベータ版の変更

次の表には、Intune データ ウェアハウス内で最近削除されたコレクションと置換のコレクションが一覧表示されています。

|    コレクション                          |    変更     |    追加情報                                                                                                                                                                                                                                                                                                                                                                 |
|----------------------------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    mobileAppDeviceUserInstallStatus    |    削除済み    |    代わりに [mobileAppInstallStatusCounts](intune-data-warehouse-collections.md#mobileappinstallstatuscounts) を使用します。                                                                                                                                                                                                                                                                     |
|    enrollmentTypes                     |    削除済み    |    代わりに [deviceEnrollmentTypes](intune-data-warehouse-collections.md#deviceenrollmenttypes) を使用します。                                                                                                                                                                                                                                                                                      |
|    mdmStatuses                         |    削除済み    |    代わりに [complianceStates](intune-data-warehouse-collections.md#compliancestates) を使用します。                                                                                                                                                                                                                                                                                               |
|    workPlaceJoinStateTypes             |    削除済み    |    代わりに [devices](intune-data-warehouse-collections.md#devices) と [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) コレクションの `azureAdRegistered` プロパティを使用します。                                                                                                                                                                                                             |
|    clientRegistrationStateTypes        |    削除済み    |    代わりに [deviceRegistrationStates](intune-data-warehouse-collections.md#deviceregistrationstates) を使用します。                                                                                                                                                                                                                                                                             |
|    currentUser                         |    削除済み    |    代わりに [users](intune-data-warehouse-collections.md#users) コレクションを使用します。                                                                                                                                                                                                                                                                                                      |
|    mdmDeviceInventoryHistories         |    削除済み    |    多くのプロパティは冗長であったか、[devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) または [devices](intune-data-warehouse-collections.md#devices) コレクションで見つけることができるようになりました。 これらの 2 つのプロパティと共に、まだ一覧にない任意の **mdmDeviceInventoryHistories** プロパティは、利用できなくなりました。 以下の詳細を参照してください。    |

次の表では、以前に **mdmDeviceInventoryHistories** コレクションで見つかった古いプロパティと変更/置換を一覧表示しています。 **mdmDeviceInventoryHistories** にあったプロパティで、以下に一覧にないプロパティは削除されました。

|    古いプロパティ                |    変更/置換                                                           |
|--------------------------------|---------------------------------------------------------------------------------|
|    cellularTechnology          |    devices コレクションの cellularTechnology                                     |
|    deviceClientId              |    devices コレクションの deviceId                                               |
|    deviceManufacturer          |    devices コレクションの manufacturer                                           |
|    deviceModel                 |    devices コレクションの model                                                  |
|    deviceName                  |    devices コレクションの deviceName                                             |
|    deviceOsPlatform            |    devices コレクションの deviceTypeKey                                          |
|    deviceOsVersion             |    devicePropertyHistories コレクションの osVersion                              |
|    deviceType                  |    devices コレクションの deviceTypeKey、deviceTypes コレクションを参照    |
|    encryptionState             |    devices コレクションの encryptionState プロパティ                           |
|    exchangeActiveSyncId        |    devices コレクションの easDeviceId プロパティ                               |
|    exchangeDeviceId            |    devices コレクションの easDeviceId                                            |
|    imei                        |    devices コレクションの imei                                                   |
|    isSupervised                |    devices コレクションの isSupervised プロパティ                              |
|    jailBroken                  |    devicePropertyHistories コレクションの jailBroken                             |
|    meid                        |    devices コレクションの meid プロパティ                                      |
|    oem                         |    devices コレクションの manufacturer                                           |
|    osName                      |    devices コレクションの deviceTypeKey、deviceTypes コレクションを参照    |
|    phoneNumber                 |    devices コレクションの phoneNumber                                            |
|    platformType                |    devices コレクションの model                                                  |
|    product                     |    devices コレクションの deviceTypeKey                                          |
|    productVersion              |    devicePropertyHistories コレクションの osVersion                              |
|    serialNumber                |    devices コレクションの serialNumber                                           |
|    storageFree                 |    devices コレクションの freeStorageSpaceInBytes プロパティ                   |
|    storageTotal                |    devices コレクションの totalStorageSpaceInBytes プロパティ                |
|    subscriberCarrierNetwork    |    devices コレクションの subscriberCarrier プロパティ                         |
|    wifimac                     |    devices コレクションの wiFiMacAddress                                         |

次の表には、[devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) コレクションで見つかるプロパティへの変更が一覧表示されています。 

|    古いプロパティ                  |    変更/置換                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey、deviceCategories コレクションを参照       |
|    certExpirationDate            |    削除済み                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    devices コレクションの enrolledDateTime                           |
|    deviceTypeKey                 |    devices コレクションの deviceTypeKey                              |
|    easID                         |    devices コレクションの easDeviceId                                |
|    enrolledByUser                |    devices コレクションの userId                                     |
|    enrollmentTypeKey             |    devices コレクションの deviceEnrollmentTypeKey                    |
|    graphDeviceIsCompliant        |    削除済み                                                          |
|    graphDeviceIsManaged          |    削除済み                                                          |
|    lastContact                   |    devices コレクションの lastSyncDateTime                           |
|    lastContactNotification       |    削除済み                                                          |
|    lastContactWorkplaceJoin      |    削除済み                                                          |
|    lastExchangeStatusUtc         |    削除済み                                                          |
|    lastModifiedDateTimeUTC       |    削除済み                                                          |
|    lastPolicyUpdateUtc           |    削除済み                                                          |
|    managementAgentKey            |    managementStateKey                                               |
|    manufacturer                  |    devices コレクションの manufacturer                               |
|    mdmStatusKey                  |    complianceStateKey、complianceStates コレクションを参照    |
|    対象となるのは、モデル                         |    devices コレクションの model                                      |
|    osFamily                      |    devices コレクションの operatingSystem                            |
|    osRevisionNumber              |    devices コレクションの osVersion                                  |
|    processorArchitecture         |    削除済み                                                          |
|    referenceId                   |    devices コレクションの azureAdDeviceId                            |
|    serialNumber                  |    devices コレクションの serialNumber                               |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

次の表には、[devices](intune-data-warehouse-collections.md#devices) コレクションで見つかるプロパティへの変更が一覧表示されています。 

|    古いプロパティ                  |    変更/置換                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey、deviceCategories コレクションを参照       |
|    certExpirationDate            |    削除済み                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    enrolledDateTime                                                 |
|    easId                         |    easDeviceId                                                      |
|    enrolledByUser                |    userId                                                           |
|    enrollmentTypeKey             |    deviceEnrollmentTypeKey                                          |
|    graphDeviceIsCompliant        |    削除済み                                                          |
|    graphDeviceIsManaged          |    削除済み                                                          |
|    lastContact                   |    lastSyncDateTime                                                 |
|    lastContactNotification       |    削除済み                                                          |
|    lastContactWorkplaceJoin      |    削除済み                                                          |
|    lastExchangeStatusUtc         |    削除済み                                                          |
|    lastPolicyUpdateUtc           |    削除済み                                                          |
|    mdmStatusKey                  |    complianceStateKey、complianceStates コレクションを参照    |
|    osFamily                      |    operatingSystem                                                  |
|    processorArchitecture         |    削除済み                                                          |
|    referenceId                   |    azureAdDeviceId                                                  |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

次の表には、[enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities) コレクションで見つかるプロパティへの変更が一覧表示されています。 

|    古いプロパティ         |    変更/置換         |
|-------------------------|-------------------------------|
|    enrollmentTypeKey    |    deviceEnrollmentTypeKey    |

次の表には、[mamApplications](intune-data-warehouse-collections.md#mamapplications) コレクションで見つかるプロパティへの変更が一覧表示されています。 

|    古いプロパティ       |    変更/置換    |
|-----------------------|--------------------------|
|    applicationKey     |    mamApplicationKey     |
|    applicationName    |    mamApplicationName    |
|    applicationId      |    mamApplicationId      |

次の表には、[mamApplicationInstances](intune-data-warehouse-collections.md#mamapplicationinstances) コレクションで見つかるプロパティへの変更が一覧表示されています。 

|    古いプロパティ     |    変更/置換    |
|---------------------|--------------------------|
|    applicationId    |    mamApplicationId      |
|    deviceId         |    mamDeviceId           |
|    deviceType       |    mamDeviceType         |
|    deviceName       |    mamDeviceName         |

次の表には、[mamCheckins](intune-data-warehouse-collections.md#mamcheckins) コレクションで見つかるプロパティへの変更が一覧表示されています。 

|    古いプロパティ      |    変更/置換    |
|----------------------|--------------------------|
|    applicationKey    |    mamApplicationKey     |

次の表には、[users](intune-data-warehouse-collections.md#users) コレクションで見つかるプロパティへの変更が一覧表示されています。 

|    古いプロパティ             |    変更/置換    |
|-----------------------------|--------------------------|
|    startDateInclusiveUtc    |    削除済み               |
|    endDateInclusiveUtc      |    削除済み               |
|    isCurrent                |    削除済み               |

## <a name="1903"></a>1903
"_リリース日: 2019 年 3 月_"

### <a name="v10-changes-reflecting-back-to-beta"></a>ベータに反映された V1.0 の変更
V1.0 が 1808 で初めて導入されたとき、ベータ API とはいくつかの重要な点で異なっていました。 1903 では、それらの変更がベータ API バージョンに反映されます。 ベータ API バージョンを使用する重要なレポートがある場合は、破壊的な変更を回避するためにそれらのレポートを V1.0 に切り替えることを強くお勧めします。 データ ウェアハウスの API バージョンと下位互換性の詳細については、[API のバージョン情報](../reports-api-url.md)に関するページを参照してください。 

## <a name="1902"></a>1902 
_リリース日: 2019 年 2 月_

### <a name="power-bi-compliance-app"></a>Power BI コンプライアンス アプリ 

[Intune コンプライアンス (データ ウェアハウス)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) アプリを使用して、Power BI Online 内の Intune データ ウェアハウスにアクセスします。 この Power BI アプリを使用すると、設定を行うことも、Web ブラウザーを離れることもなく、事前に作成されたレポートにアクセスし、共有することができます。 

> [!NOTE]
> Intune コンプライアンス アプリに適用できる追加のフィルターが 2 つあります。

#### <a name="add-additional-filters-to-the-intune-compliance-app"></a>Intune コンプライアンス アプリに追加のフィルターを追加する
1. ご利用の Web ブラウザーで [Intune コンプライアンス (データ ウェアハウス)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) アプリを開きます。
2. **[Non-Compliant Devices]\(非準拠デバイス\)** をクリックして、**complianceStatus** フィルターで **[非準拠]** を選択します。 
3. **[Unknown Devices]\(不明なデバイス\)** をクリックして、**complianceStatus** フィルターで **[まだ使用できません]** を選択します。 

## <a name="1812"></a>1812 
_2018 年 12 月リリース_

### <a name="enrollment-activities-collection-released-to-v10"></a>v1.0 にリリースされた登録アクティビティ コレクション 

v1.0 で登録アクティビティ コレクションが利用できるようになりました。 このコレクションを使用して、環境内での登録エラーのボリュームと傾向を把握できます。 詳細については、「[enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities)」、「[enrollmentEventStatuses](intune-data-warehouse-collections.md#enrollmenteventstatuses)」、「[enrollmentFailureCategories](intune-data-warehouse-collections.md#enrollmentfailurecategories)」、および「[enrollmentFailureReasons](intune-data-warehouse-collections.md#enrollmentfailurereasons)」を参照してください。

## <a name="1808"></a>1808
_リリース日: 2018 年 8 月_

### <a name="v10-collections"></a>v1.0 コレクション  

クエリ パラメーター `api-version=v1.0` を設定することにより、Intune データ ウェアハウスの v1.0 バージョンを使用できるようになりました。 Data Warehouse 内のコレクションに対する更新は本質的に追加であり、既存のシナリオが使用できなくなることはありません。

### <a name="enrollment-activities-collection-released-to-beta"></a>ベータ版にリリースされた登録アクティビティ コレクション

新しい `Enrollment Activities` コレクションが、ベータ版にリリースされました。 このコレクションを使用して、最も一般的なエラーを表示することにより、登録の進行状況がわかります。 


## <a name="1805"></a>1805
_2018 年 5 月リリース_

### <a name="correction-to-device-count-in-devices-collection"></a>**Devices** コレクションのデバイス数の修正 

**Devices** コレクションが修正されました。この修正により、`isDeleted` 属性でフィルター処理される合計デバイス数が少なくなることがあります この減少は修正の結果であり、エラーではありません。 **Devices** コレクションの詳細については、「[デバイス エンティティの参照](reports-ref-devices.md)」を参照してください。 


## <a name="1801"></a>1801
_2018 年 1 月リリース_

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>Intune データ ウェアハウス アプリケーションのみの認証 <!-- 1867540 -->

Azure Active Directory (Azure AD) を使用してアプリケーションを設定し、Intune データ ウェアハウスに対する認証を実行できます。 詳細については、「[Intune データ ウェアハウス アプリケーションのみの認証](data-warehouse-app-only-auth.md)」を参照してください。

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Azure AD と Intune の資格情報の要件 <!-- 2077525 -->

- Intune データ ウェアハウス (API を含む) にアクセスするときに、Intune ライセンスをユーザーに割り当てる必要がなくなりました。
- Intune のロール名は**レポート**から **Intune データ ウェアハウス**に変更されました。 

    詳細については、「[Azure AD と Intune の資格情報の要件](reports-api-url.md#azure-ad-and-intune-credential-requirements)」を参照してください。

### <a name="odata-query-options----2077711---"></a>OData クエリのオプション <!-- 2077711 -->

OData クエリ パラメーターとして <code>$select</code> を使用できます。 現在のバージョンは、OData クエリ パラメーター <code>$filter</code>、<code>$orderby</code>、<code>$select</code>、<code>$skip</code>、および <code>$top</code> をサポートしています。 詳細については、「[OData クエリのオプション](reports-api-url.md#odata-query-options)」を参照してください。

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>データ ウェアハウス データ モデルの新しいエンティティ <!-- 2077804 -->

- エンティティ [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md) が追加されました。 **MobileAppDeviceUserInstallStatus** は、特定のデバイスとユーザーのモバイル アプリのインストール状態を表します。
- エンティティ [**MobileAppInstallState**](reports-ref-application.md#mobileappinstallstates) が追加されました。 **MobileAppInstallState** エンティティは、デバイス、ユーザー、またはその両方を含むグループに割り当てられた後のモバイル アプリケーションのインストール状態を表します。 

## <a name="1710"></a>1710
_リリース日: 2017 年 11 月_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>現在のユーザーという名前の新しいエンティティ コレクションは、現在アクティブなユーザー データに限られています <!-- 1544273 -->

**ユーザー** エンティティ コレクションには、社内のすべての Azure Active Directory (Azure AD) ユーザーと割り当てられているライセンスが表示されます。 これらのレコードには、ユーザーが削除されている場合でも、データ コレクション期間中のユーザーの状態が含まれます。 たとえば、ユーザーが Intune に追加され、過去 1 か月の過程で削除されたとします。 このユーザーがレポートの時点では存在しない一方で、ユーザーと状態はデータに存在します。 データ内のユーザーの履歴における存在の期間を示すレポートを作成できます。

これに対し、新しい**現在のユーザー** エンティティ コレクションには、削除されていないユーザーのみが含まれています。 **現在のユーザー** エンティティ コレクションには、現在アクティブなユーザーのみが含まれています。 **現在のユーザー** エンティティ コレクションの詳細については、「[現在のユーザー エンティティのリファレンス](../reports-ref-current-user.md)」をご覧ください。

## <a name="1709"></a>1709
_リリース日: 2017 年 10 月_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Intune データ ウェアハウスのデータ モデルに追加されたユーザー デバイス関連付けエンティティ コレクション <!-- 1187917 -->

ユーザーとデバイスのエンティティ コレクションを関連付けるユーザー デバイス関連付け情報を使って、レポートやデータの視覚エフェクトを作成できるようになりました。 このデータ モデルは、OData エンドポイントを使うか、カスタム クライアントを開発すると、[Data Warehouse Intune]\(データ ウェアハウス Intune\) ページから取得した Power BI ファイル (PBIX) を使ってアクセスできます。 詳細については、「[ユーザー デバイスの関連付け](reports-ref-user-device.md)」をご覧ください。

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>データ ウェアハウス データ モデルの新しいエンティティ <!-- 1479526 --><!-- -->

- [**UserDeviceAssociation**](reports-ref-user-device.md) というエンティティが追加されました。 **UserDeviceAssociation** には、組織内のユーザー デバイスの関連付けが含まれています。 ユーザーとデバイスのエンティティ コレクションを関連付けるユーザー デバイス関連付け情報を使って、レポートやデータの視覚エフェクトを作成できるようになりました。  
- [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md) というエンティティが追加されました。 **IntuneManagementExtension** には、バージョンやインストール状態などの情報を追跡するモバイル デバイスのエンティティが含まれます。

## <a name="next-steps"></a>次の手順
- [週ごとにまとめた Intune の新機能](../fundamentals/whats-new.md)を参照してください。 今後の変更、サービスに関する重要なお知らせ、過去のリリースに関する情報も確認できます。
- [Microsoft Intune のブログ](https://go.microsoft.com/fwlink/?LinkID=273882)を参照してください。
