---
title: デバイス - Intune データ ウェアハウス
titleSuffix: Microsoft Intune
description: Intune データ ウェアハウス API にあるエンティティ コレクションのデバイス カテゴリのための参照トピック。
keywords: Intune データ ウェアハウス
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c361c6054cf52c802155587084eaea76e024f78c
ms.sourcegitcommit: 601327125ac8ae912d8159422de8aac7dbdc25f6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59429184"
---
# <a name="reference-for-devices-entities"></a>デバイス エンティティの参照

**デバイス** カテゴリには、次のような情報を追跡記録するモバイル デバイスのエンティティが含まれています。

  -  デバイスの種類
  -  デバイスの登録と登録状況
  -  デバイスの所有権
  -  デバイスの管理状態
  -  デバイスの Azure AD メンバーシップ状況
  -  登録ステータス
  -  デバイスに関する過去の情報
  -  デバイス上のアプリ目録

## <a name="devicetypes"></a>DeviceTypes

**DeviceTypes** エンティティは、他のデータ ウェアハウス エンティティによって参照されるデバイスの種類を表します。 デバイスの種類により、一般的に、デバイスのモデル、メーカー、あるいは両方の組み合わせが説明されます。

| プロパティ  | 説明 |
|---------|------------|
| DeviceTypeID |デバイスの種類を示す一意識別子 |
| DeviceTypeKey |データ ウェアハウスにおけるデバイスの種類を示す一意識別子 - 代理キー |
| DeviceTypeName |デバイスの種類 |

### <a name="example"></a>例

| deviceTypeID  | 名前 | 説明 |
|---------|------------|--------|
| 0 |デスクトップ |Windows デスクトップ デバイス |
| 1 |Windows RT |WindowsRT デバイス |
| 2 |WinMO6 |Windows Mobile 6.0 デバイス |
| 3 |Nokia |Nokia デバイス |
| 4 |WindowsPhone |Windows Phone デバイス |
| 5 |Mac |Mac デバイス |
| 6 |WinCE |Windows CE デバイス |
| 7 |WinEmbedded |Windows Embedded デバイス |
| 8 |IPhone |iPhone デバイス |
| 9 |IPad |iPad デバイス |
| 10 |IPod |iPod デバイス |
| 11 |Android |Android デバイス - デバイス管理者により管理 |
| 12 |ISocConsumer |iSoc Consumer デバイス |
| 14 |MacMDM |Mac OS X デバイス - 組み込み MDM エージェントにより管理 |
| 15 |HoloLens |HoloLens デバイス |
| 16 |SurfaceHub |Surface Hub デバイス |
| 17 |AndroidForWork |Android デバイス - Android Profile Owner により管理 |
| 100 |Blackberry |Blackberry デバイス |
| 101 |Palm |Palm デバイス |
| 255 |Unknown |デバイスの種類が不明 |

## <a name="enrollmentactivities"></a>enrollmentActivities 
**EnrollmentActivity** エンティティは、デバイス登録のアクティビティを示します。

| プロパティ                      | 説明                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | この登録アクティビティが記録された日付のキー。               |
| deviceEnrollmentTypeKey       | 登録の種類のキー。                                        |
| deviceTypeKey                 | デバイスの種類のキー。                                                |
| enrollmentEventStatusKey      | 登録の成功または失敗を示す状態のキー。    |
| enrollmentFailureCategoryKey  | 登録エラー カテゴリのキー (登録が失敗した場合)。        |
| enrollmentFailureReasonKey    | 登録エラーの理由のキー (登録が失敗した場合)。          |
| osVersion                     | デバイスのオペレーティング システムのバージョン。                               |
| count                         | 上記の分類に一致する登録アクティビティの合計数。  |

## <a name="enrollmenteventstatuses"></a>enrollmentEventStatuses 
**EnrollmentEventStatus** エンティティは、デバイス登録の結果を示します。

| プロパティ                   | 説明                                                                       |
|----------------------------|-----------------------------------------------------------------------------------|
| enrollmentEventStatusKey   | データ ウェアハウスでの登録状態の一意識別子 (代理キー)  |
| enrollmentEventStatusName  | 登録状態の名前。 以下の例を参照してください。                            |

### <a name="example"></a>例

| enrollmentEventStatusName  | 説明                            |
|----------------------------|----------------------------------------|
| 成功                    | 成功したデバイスの登録         |
| Failed                     | 失敗したデバイスの登録             |
| 利用不可              | 登録状態は利用できません。  |

## <a name="enrollmentfailurecategories"></a>enrollmentFailureCategories 
**EnrollmentFailureCategory** エンティティは、デバイスの登録が失敗した理由を示します。 

| プロパティ                       | 説明                                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------------|
| enrollmentFailureCategoryKey   | データ ウェアハウスでの登録の失敗カテゴリの一意識別子 (代理キー)  |
| enrollmentFailureCategoryName  | 登録エラーのカテゴリの名前。 以下の例を参照してください。                            |

### <a name="example"></a>例

| enrollmentFailureCategoryName   | 説明                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| 適用しない                  | 登録エラーのカテゴリは適用されません。                                                            |
| 利用不可                   | 登録エラーのカテゴリは利用できません。                                                             |
| Unknown                         | 不明なエラー。                                                                                                |
| 認証                  | 認証に失敗しました。                                                                                        |
| 承認                   | 呼び出しは認証されましたが、登録する権限がありません。                                                         |
| AccountValidation               | 登録用のアカウントの検証に失敗しました  (アカウントはブロックされ、登録は有効になっていません)。                      |
| UserValidation                  | ユーザーを検証できませんでした  (ユーザーが存在しておらず、ライセンスが欠落しています)。                                           |
| DeviceNotSupported              | デバイスがモバイル デバイス管理でサポートされていません。                                                         |
| InMaintenance                   | アカウントがメンテナンス中です。                                                                                    |
| BadRequest                      | クライアントによって、サービスで認識/サポートされていない要求が送信されました。                                        |
| FeatureNotSupported             | この登録で使用される機能が、このアカウントでサポートされていません。                                        |
| EnrollmentRestrictionsEnforced  | 管理者が構成した登録制限によって、この登録がブロックされました。                                          |
| ClientDisconnected              | クライアントがタイムアウトになったか、エンドユーザーによって登録が中断されました。                                                        |
| UserAbandonment                 | エンドユーザーによって登録が中止されました。 (エンドユーザーはオンボードを開始しましたが、適切なタイミングでそれを完了できませんでした)  |

## <a name="enrollmentfailurereasons"></a>enrollmentFailureReasons  
**EnrollmentFailureReason** エンティティは、特定のエラー カテゴリ内のデバイス登録エラーのより詳細な理由を示します。  

| プロパティ                     | 説明                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------|
| enrollmentFailureReasonKey   | データ ウェアハウスでの登録エラーの理由の一意識別子 (代理キー)  |
| enrollmentFailureReasonName  | 登録エラーの理由の名前。 以下の例を参照してください。                            |

### <a name="example"></a>例

| enrollmentFailureReasonName      | 説明                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 適用しない                   | 登録エラーの理由は適用されません。                                                                                                                                                       |
| 利用不可                    | 登録エラーの理由は利用できません。                                                                                                                                                        |
| Unknown                          | 不明なエラー。                                                                                                                                                                                         |
| UserNotLicensed                  | ユーザーが Intune で見つからなかったか、有効なライセンスを持っていません。                                                                                                                                     |
| UserUnknown                      | ユーザーが Intune に認識されていません。                                                                                                                                                                           |
| BulkAlreadyEnrolledDevice        | デバイスを登録できるのは 1 人のユーザーのみです。 このデバイスは以前に別のユーザーによって登録されています。                                                                                                                |
| EnrollmentOnboardingIssue        | Intune モバイル デバイス管理 (MDM) 機関がまだ構成されていません。                                                                                                                                 |
| AppleChallengeIssue              | iOS 管理プロファイルのインストールに遅延が生じたか、失敗しました。                                                                                                                                         |
| AppleOnboardingIssue             | Intune に登録するには、Apple MDM プッシュ証明書が必要です。                                                                                                                                       |
| DeviceCap                        | ユーザーが、最大許容数を超えるデバイスを登録しようとしました。                                                                                                                                        |
| AuthenticationRequirementNotMet  | Intune 登録サービスでこの要求を承認できませんでした。                                                                                                                                            |
| UnsupportedDeviceType            | このデバイスは Intune 登録のための最小要件を満たしていません。                                                                                                                                  |
| EnrollmentCriteriaNotMet         | 構成された登録制限規則により、このデバイスの登録に失敗しました。                                                                                                                          |
| BulkDeviceNotPreregistered       | このデバイスの International Mobile Equipment Identifier (IMEI) またはシリアル番号が見つかりませんでした。  この識別子がない場合、デバイスは、現在ブロックされている個人所有デバイスとして認識されます。  |
| FeatureNotSupported              | ユーザーが、すべての顧客に対してまだリリースされていないか、Intune 構成と互換性のない機能にアクセスしようとしました。                                                            |
| UserAbandonment                  | エンドユーザーによって登録が中止されました。 (エンドユーザーはオンボードを開始しましたが、適切なタイミングでそれを完了できませんでした)                                                                                           |
| APNSCertificateExpired           | 期限切れの Apple MDM プッシュ証明書では、Apple デバイスを管理できません。                                                                                                                            |
## <a name="ownertypes"></a>OwnerTypes

**EnrollmentTypes** エンティティは、デバイスの種類として企業所有、個人所有、不明のいずれかを示します。

| プロパティ  | 説明 | 例 |
|---------|------------|--------|
| ownerTypeID |所有者の種類を示す一意識別子。 | |
| ownerTypeKey |データ ウェアハウスにおける所有者の種類を示す一意識別子 - 代理キー。 | |
| ownerTypeName |デバイスの所有者の種類を表します。  <br>[会社] - 会社が所有するデバイスです。 <br>[個人] - 個人が所有するデバイスです (BYOD)。  <br>[不明] - このデバイスの情報はありません。 |会社、個人、不明 |

> [!Note]  
> デバイスに対して動的グループを作成する場合の AzureAD の `ownerTypeName` では、フィルター値 `deviceOwnership` を `Company` として設定する必要があります。 詳細については、「[デバイスのルール](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices)」を参照してください。 

## <a name="managementstates"></a>ManagementStates

**ManagementStates** エンティティは、デバイスの状態に関する詳細を提供します。 リモート アクションが適用され、デバイスが脱獄またはルート化されているとき、詳細が役立ちます。

| プロパティ  | 説明 |
|---------|------------|
| managementStateID | 管理状態を示す一意識別子 |
| managementStateKey | データ ウェアハウスにおける管理状態を示す一意識別子 - 代理キー |
| managementStateName | このデバイスに適用されるリモート アクションの状態を示します。 |

### <a name="example"></a>例

| managementStateID  | 名前 | 説明 |
|---------|------------|--------|
| 0 |管理対象 | 保留なしのリモート アクションにより管理 |
| 1 |RetirePending | インベントリから削除するコマンドがデバイスに対して保留になっています。 |
| 2 |RetireFailed | インベントリから削除するコマンドをデバイスに実行したところ、失敗しました。 |
| 3 |WipePending | ワイプ コマンドがデバイスに対して保留になっています。 |
| 4 |WipeFailed | ワイプ コマンドをデバイスに実行したところ、失敗しました。 |
| 5 |Unhealthy | 正常ではない状態。 |
| 6 |DeletePending | 削除コマンドがデバイスに対して保留になっています。 |
| 7 |RetireIssued | インベントリから削除するコマンドがデバイスに発行されています。 |
| 8 |WipeIssued | ワイプ コマンドが発行されています。 |
| 9 |WipeCanceled | ワイプ コマンドが取り消されています。 |
| 10 |RetireCanceled | インベントリから削除するコマンドが取り消されています。 |
| 11 |Discovered | Intune がデバイスを新たに検出しました。最初のチェックイン後、状態が [Managed] に変更されます。 |

## <a name="managementagenttypes"></a>ManagementAgentTypes

**ManagementAgentTypes** エンティティは、デバイスの管理に使用されるエージェントを表します。

| プロパティ  | 説明 |
|---------|------------|
| ManagementAgentTypeID | 管理エージェントの種類を示す一意識別子。 |
| ManagementAgentTypeKey | データ ウェアハウスにおける管理エージェントの種類を示す一意識別子 - 代理キー。 |
| ManagementAgentTypeName |デバイスの管理に利用されているエージェントの種類を示します。 |

### <a name="example"></a>例

| ManagementAgentTypeID  | 名前 | 説明 |
|---------|------------|--------|
| 1 |EAS | デバイスが Exchange Active Sync で管理されます |
| 2 |MDM | デバイスが MDM エージェントで管理されます |
| 3 |EasMdm | デバイスが Exchange Active Sync と MDM エージェントの両方で管理されます |
| 4 |IntuneClient | デバイスが Intune PC エージェントで管理されます |
| 5 |EasIntuneClient | デバイスが Exchange Active Sync と Intune PC エージェントの両方で管理されます |
| 8 |ConfigManagerClient | デバイスが System Center Configuration Manager エージェントで管理されます |
| 16 |Unknown | 管理エージェントの種類が不明です |

## <a name="devices"></a>[デバイス]

**Devices** エンティティには、管理中のすべての登録済みデバイスとそれに対応するプロパティが一覧表示されます。

|          プロパティ          |                                                                                       説明                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DeviceKey                  | データ ウェアハウスにおけるデバイスを示す一意識別子 - 代理キー。                                                                                                               |
| DeviceId                   | デバイスの一意識別子。                                                                                                                                                     |
| DeviceName                 | デバイスに名前を付けられるプラットフォーム上にあるデバイスの名前。 その他のプラットフォームの場合、Intune がその他のプロパティから名前を作成します。 この属性は一部のデバイスで利用できません。 |
| DeviceTypeKey              | このデバイスの種類属性のキー。                                                                                                                                    |
| DeviceRegistrationState    | このデバイスのクライアント登録状態属性のキー。                                                                                                                      |
| OwnerTypeKey               | このデバイスの所有者の種類属性のキー: 会社、個人、不明。                                                                                                    |
| EnrolledDateTime           | このデバイスが登録された日時。                                                                                                                                         |
| LastSyncDateTime           | Intune によるデバイス チェックインで最後に確認されているもの。                                                                                                                                              |
| ManagementAgentKey         | このデバイスに関連付けられている管理エージェントのキー。                                                                                                                             |
| ManagementStateKey         | このデバイスに関連付けられている管理状態を示すキーであり、リモート アクションの最新の状態を示すか、脱獄/ルート化状態を示します。                                                |
| AzureADDeviceId            | このデバイスの Azure deviceID。                                                                                                                                                  |
| AzureADRegistered          | デバイスが Azure Active Directory に登録されているかどうか。                                                                                                                             |
| DeviceCategoryKey          | このデバイスに関連付けられているカテゴリのキー。                                                                                                                                     |
| DeviceEnrollmentType       | このデバイスに関連付けられている登録の種類を示すキーであり、登録の方法を示します。                                                                                             |
| ComplianceStateKey         | このデバイスに関連付けられているコンプライアンスの状態のキー。                                                                                                                             |
| OSVersion                  | デバイスのオペレーティング システムのバージョン。                                                                                                                                                |
| EasDeviceId                | デバイスの Exchange ActiveSync ID。                                                                                                                                                  |
| SerialNumber               | SerialNumber                                                                                                                                                                           |
| UserId                     | デバイスに関連付けられているユーザーの一意識別子。                                                                                                                           |
| RowLastModifiedDateTimeUTC | このデバイスがデータ ウェアハウスで最後に変更されたときの UTC 日時。                                                                                                       |
| 製造元               | デバイスの製造元                                                                                                                                                             |
| モデル                      | デバイスのモデル                                                                                                                                                                    |
| OperatingSystem            | デバイスのオペレーティング システム。 Windows、iOS など。                                                                                                                                   |
| IsDeleted                  | デバイスを削除されているかどうかを示すバイナリ。                                                                                                                                 |
| AndroidSecurityPatchLevel  | Android セキュリティ パッチ レベル                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| isSupervised               | デバイスの監視状態                                                                                                                                                               |
| FreeStorageSpaceInBytes    | ストレージの空き容量 (バイト単位)。                                                                                                                                                                 |
| TotalStorageSpaceInBytes   | ストレージの合計容量 (バイト単位)。                                                                                                                                                                |
| EncryptionState            | デバイスの暗号化の状態。                                                                                                                                                      |
| SubscriberCarrier          | デバイスの通信事業者                                                                                                                                                       |
| PhoneNumber                | デバイスの電話番号                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| CellularTechnology         | デバイスの携帯電話テクノロジ                                                                                                                                                    |
| WiFiMacAddress             | Wi-Fi MAC                                                                                                                                                                              |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

**DevicePropertyHistory** エンティティには、デバイス テーブルと過去 90 日間の各デバイス レコードの日次スナップショットと同じプロパティが与えられます。 DateKey 列は、各行の日を示します。

|          プロパティ          |                                                                                      説明                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DateKey                    | 日付テーブルの参照であり、日を示します。                                                                                                                                          |
| DeviceKey                  | データ ウェアハウスでのデバイスの一意識別子 - 代理キー。 これは、Intune デバイス ID が含まれるデバイス テーブルの参照です。                               |
| DeviceName                 | デバイスに名前を付けられるプラットフォーム上にあるデバイスの名前。 その他のプラットフォームの場合、Intune がその他のプロパティから名前を作成します。 この属性は一部のデバイスでは利用できません。 |
| DeviceRegistrationStateKey | このデバイスのデバイス登録状態属性のキー。                                                                                                                    |
| OwnerTypeKey               | このデバイスの所有者の種類属性のキー: 会社、個人、不明                                                                                                  |
| ManagementStateKey         | このデバイスに関連付けられている管理状態を示すキーであり、リモート アクションの最新の状態を示すか、脱獄/ルート化状態を示します。                                                |
| AzureADRegistered          | デバイスが Azure Active Directory に登録されているかどうか。                                                                                                                             |
| ComplianceStateKey         | ComplianceState へのキー。                                                                                                                                                            |
| OSVersion                  | OS のバージョン。                                                                                                                                                                          |
| JailBroken                 | デバイスが脱獄またはルート化されているかどうか。                                                                                                                                         |
| DeviceCategoryKey          | このデバイスのデバイス カテゴリ属性のキー。 

## <a name="applicationinventory"></a>ApplicationInventory

**ApplicationInventory** エンティティには、インベントリ回収時にデバイスで検出されたアプリが一覧表示されます。


|      プロパティ      |                       説明                        |
|--------------------|----------------------------------------------------------|
|     DeviceKey      |              デバイス テーブルの参照。               |
|   ApplicationKey   | ? (ExchangeDeviceService\DeviceApplication からコピーされます)。 |
|  ApplicationName   | ? (ExchangeDeviceService\DeviceApplication からコピーされます)。 |
| ApplicationVersion | ? (ExchangeDeviceService\DeviceApplication からコピーされます)。 |
|     BundleSize     | ? (ExchangeDeviceService\DeviceApplication からコピーされます)。 |

