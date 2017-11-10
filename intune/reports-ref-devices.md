---
title: "デバイス - Intune データ ウェアハウス | Microsoft Docs"
description: "Intune データ ウェアハウス API にあるエンティティ コレクションのデバイス カテゴリのための参照トピック。"
keywords: "Intune データ ウェアハウス"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b11994028a42b19aca3e78900886afbedc1ca1d5
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2017
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

## <a name="example"></a>例

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
| 15 |HoloLens |Holo Lens デバイス |
| 16 |SurfaceHub |Surface Hub デバイス |
| 17 |AndroidForWork |Android デバイス - Android for Work Profile Owner により管理 |
| 100 |Blackberry |Blackberry デバイス |
| 101 |Palm |Palm デバイス |
| 255 |不明 |デバイスの種類が不明 |

## <a name="clientregistrationstatetypes"></a>ClientRegistrationStateTypes

**ClientRegistrationStateTypes** エンティティは、他のデータ ウェアハウス テーブルにより参照される登録の種類を表します。

| プロパティ  | 説明 |
|---------|------------|
| clientRegisterationStateID |登録状況の一意識別子 |
| clientRegisterationStateKey |データ ウェアハウスにおける登録状況を示す一意識別子 - 代理キー |
| clientRegisterationStateName |登録状況 |

## <a name="example"></a>例

| ClientRegisterationStateID  | 名前 | 説明 |
|---------|------------|--------|
| 0 |NotRegistered |未登録 |
| 1 |SMSIDConflict |SMS ID 競合 |
| 2 |登録済み |登録済み |
| 3 |取り消し済み |状態は IT 管理者がクライアントをブロックしたことを意味します。クライアントのブロックを解除できます。 デバイスは、ワイプした後やインベントリから削除した後にも取り消し済み状態になります。 |
| 4 |KeyConflict |キー競合 |
| 5 |ApprovalPending |承認保留中 |
| 6 |ResetCert |証明書のリセット |
| 7 |NotRegisteredPendingEnrollment |未登録で登録保留中 |
| 8 |不明 |状態が不明 |

## <a name="enrollmenttypes"></a>EnrollmentTypes

**EnrollmentTypes** エンティティは、デバイスの登録方法を示します。 登録の種類により、登録の方法が保存されます。 例には、登録のさまざまな種類とその意味が一覧表示されています。

| プロパティ  | 説明 |
|---------|------------|
| managementStateID |管理状態を示す一意識別子 |
| managementStateKey |データ ウェアハウスにおける管理状態を示す一意識別子 - 代理キー |
| managementStateName |このデバイスに適用されるリモート アクションの状態を示します。 |

## <a name="example"></a>例

| enrollmentTypeID  | 名前 | 説明 |
|---------|------------|--------|
| 0 |不明 |登録の種類が収集されませんでした |
| 1 |UserEnrollment |ユーザーが開始した登録 |
| 2 |DeviceEnrollment |ユーザーなしのプロファイルによるデバイス登録 |
| 3 |DeviceEnrollmentWithUDA |UDA プロファイルによるデバイス登録 |
| 4 |AzureDomainJoined |ユーザーが Azure Active Directory を利用して開始したデバイス登録 |
| 5 |UserEnrollmentWithServiceAccount |ユーザーがサービス アカウントを利用して開始した登録 |
| 6 |DepDeviceEnrollment |ユーザーなしのプロファイルによる DEP デバイス登録 |
| 7 |DepDeviceEnrollmentWithUDA |UDA プロファイルによる DEP デバイス登録 |
| 8 |AutoEnrollment |BYOD シナリオのための DRS と MDM を組み合わせた登録 |

## <a name="ownertypes"></a>OwnerTypes

**EnrollmentTypes** エンティティは、デバイスの種類として企業所有、個人所有、不明のいずれかを示します。

| プロパティ  | 説明 | 例 |
|---------|------------|--------|
| ownerTypeID |所有者の種類を示す一意識別子。 | |
| ownerTypeKey |データ ウェアハウスにおける所有者の種類を示す一意識別子 - 代理キー。 | |
| ownerTypeName |デバイスの所有者の種類を表します。  <br>[会社] - 会社が所有するデバイスです。 <br>[個人] - 個人が所有するデバイスです (BYOD)。  <br>[不明] - このデバイスの情報はありません。 |会社、個人、不明 |

## <a name="mdmstatuses"></a>MdmStatuses

**MdmStatuses** エンティティは、デバイスのコンプライアンス対応状態を示します。

| プロパティ  | 説明 |
|---------|------------|
| MdmStatusID |コンプライアンスの状態を示す一意識別子 |
| MdmStatusKey |データ ウェアハウスにおけるコンプライアンス対応状態を示す一意識別子 - 代理キー | 
| ComplianceStatus |デバイスのコンプライアンスの状態。以下の表のいずれかの値が表示されます | 


## <a name="example"></a>例

| MdmStatusID  | ComplianceStatus | 説明 |
|---------|------------|--------|
| 0 |不明 |デバイスのコンプライアンスの状態は不明です。 |
| 1 |準拠 |デバイスは準拠しています。 |
| 2 |非準拠 |デバイスは準拠していません。 |
| 3 |競合 |デバイスのコンプライアンスで競合が発生しました。 |
| 4 |エラー |デバイスのコンプライアンスの状態の読み取りでエラーが発生しました。 |


## <a name="managementstates"></a>ManagementStates

**ManagementStates** エンティティは、デバイスの状態に関する詳細を提供します。 リモート アクションが適用され、デバイスが脱獄またはルート化されているとき、詳細が役立ちます。

| プロパティ  | 説明 |
|---------|------------|
| managementStateID | 管理状態を示す一意識別子 |
| managementStateKey | データ ウェアハウスにおける管理状態を示す一意識別子 - 代理キー |
| managementStateName | このデバイスに適用されるリモート アクションの状態を示します。 |

## <a name="example"></a>例

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

## <a name="workplacejoinstatetypes"></a>WorkPlaceJoinStateTypes

**WorkPlaceJoinStateTypes** エンティティは、デバイスの Azure Active Directory の社内参加の状況を表します。  登録ワークフローでは、検証または認証に 1 つまたは複数の証明書を利用できます。 デバイスをワークプレース登録するとき、証明書でデバイスとユーザーを検証します。 証明書は SCEP (Simple Certificate Enrollment Point) サーバーから発行されます。 エンティティの値は、デバイスがこのプロセスを通過するときのさまざまな状態を示します。 このような状態の中に、(SCEP サーバーから) 必要な証明書が発行されなかったため、社内参加ができなかったという状態があります。 デバイスがこのワークフローを通過しなかった場合、値は [不明] に設定されます。

| プロパティ  | 説明 |
|---------|------------|
| WorkPlaceJoinStateID | ワークプレース参加状態を示す一意識別子 |
| WorkPlaceJoinStateKey | データ ウェアハウスにおけるワークプレース参加状態を示す一意識別子 - 代理キー |
| WorkPlaceJoinStateName | ワークプレース参加状態 |

## <a name="example"></a>例

| workPlaceJoinStateID  | 名前 | 説明 |
|---------|------------|--------|
| 0 |不明 |デバイスが社内参加していない場合、状態は不明となります。 |
| 1 |成功 |社内参加に成功しました |
| 2 |FailureToGetScepMetadata |SCEP メタデータを取得できませんでした |
| 3 |FailureToGetScepChallenge |SCEP チャレンジを取得できませんでした |
| 4 |DeviceFailureToInstallScepCommand |デバイスに SCEP コマンドをインストールしようとしましたが失敗しました |
| 5 |DeviceFailureToGetCertificate |デバイスが SCEP 経由で証明書を取得しようとしましたが失敗しました |
| 6 |DeviceScepPending |保留状態であり、デバイスは SCEP を継続しています |
| 7 |DeviceScepFailed |デバイスが SCEP 経由で証明書をインストールしようとしましたが失敗しました |
| 8 |AADValidationFailed |AAD にデバイスが存在するか検証しようとしましたが失敗しました |

## <a name="managementagenttypes"></a>ManagementAgentTypes

**ManagementAgentTypes** エンティティは、デバイスの管理に使用されるエージェントを表します。

| プロパティ  | 説明 |
|---------|------------|
| ManagementAgentTypeID | 管理エージェントの種類を示す一意識別子。 |
| ManagementAgentTypeKey | データ ウェアハウスにおける管理エージェントの種類を示す一意識別子 - 代理キー。 |
| ManagementAgentTypeName |デバイスの管理に利用されているエージェントの種類を示します。 |

## <a name="example"></a>例

| ManagementAgentTypeID  | 名前 | 説明 |
|---------|------------|--------|
| 1 |EAS | デバイスが Exchange Active Sync で管理されます |
| 2 |MDM | デバイスが MDM エージェントで管理されます |
| 3 |EasMdm | デバイスが Exchange Active Sync と MDM エージェントの両方で管理されます |
| 4 |IntuneClient | デバイスが Intune PC エージェントで管理されます |
| 5 |EasIntuneClient | デバイスが Exchange Active Sync と Intune PC エージェントの両方で管理されます |
| 8 |ConfigManagerClient | デバイスが System Center Configuration Manager エージェントで管理されます |
| 16 |不明 | 管理エージェントの種類が不明です |

## <a name="devices"></a>[デバイス]

**Devices** エンティティには、管理中のすべての登録済みデバイスとそれに対応するプロパティが一覧表示されます。

| プロパティ  | 説明 |
|---------|------------|
| DeviceKey | データ ウェアハウスにおけるデバイスを示す一意識別子 - 代理キー。 |
| DeviceId | デバイスの一意識別子。 |
| DeviceName | デバイスに名前を付けられるプラットフォーム上にあるデバイスの名前。 その他のプラットフォームの場合、Intune がその他のプロパティから名前を作成します。 この属性は一部のデバイスで利用できません。 |
| DeviceTypeKey | このデバイスの種類属性のキー。 |
| ClientRegisterationStateKey | このデバイスのクライアント登録状態属性のキー。 |
| OwnerTypeKey | このデバイスの所有者の種類属性のキー (会社、個人、不明) |
| objectSourceKey | この列は無視してください。 |
| CreatedDate | デバイスが登録された日付。 |
| LastContact | Intune によるデバイス チェックインで最後に確認されているもの。 |
| LastContactNotification | Intune によるチェックインを Intune がデバイスに通知した最後の時刻。 |
| LastContactWorkplaceJoin | このデバイスの社内参加について最後に確認されている状態を示すタイムスタンプ |
| ManagementAgentKey | このデバイスに関連付けられている管理エージェントのキー |
| ManagementStateKey | このデバイスに関連付けられている管理状態を示すキーであり、リモート アクションの最新の状態を示すか、脱獄/ルート化状態を示します |
| ReferenceId | Azure Active Directory のデバイス ID。 |
| WorkPlaceJoinStateKey | このデバイスに関連付けられている社内参加の状態を示すキー |
| CategoryId | この列は無視してください。 |
| EnrollmentTypeKey | このデバイスに関連付けられている登録の種類を示すキーであり、登録の方法を示します |
| CertExpirationDate | MDM 管理証明書の有効期限日 |
| MdmStatusKey | MdmStatus キー。 |
| OSFamily | OS 製品群 (Windows、iOS、Android など) |
| OSVersion | OS のバージョン |
| OSMajorVersion | OS バージョンのメジャー バージョン コンポーネント (major.minor.build.revision)。 |
| OSMinorVersion | OS バージョンのマイナー バージョン コンポーネント (major.minor.build.revision)。 |
| OSBuildNumber | OS バージョンのビルド バージョン コンポーネント (major.minor.build.revision)。 |
| OSRevisionNumber | OS バージョンのリビジョン バージョン コンポーネント (major.minor.build.revision)。 |
| EasID | デバイスが Exchange Active Sync で管理されている場合、このデバイスの EAS ID |
| GraphDeviceIsManaged | Intune により Azure AD で最後に設定された管理状態。 |
| GraphDeviceIsCompliant | Intune により Azure AD で最後に設定されたコンプライアンス対応状態。 |
| SerialNumber | デバイスのシリアル番号 (使用可能な場合)。 |
| EnrolledByUser | このデバイスを登録したユーザーの ID であり、ユーザー テーブルの userId 列を参照します |
| RowLastModifiedDateTimeUTC | このレコードが変更された最後の時刻 |
| ProcessorArchitecture | プロセッサ アーキテクチャ。 |
| DeviceAction | 最後に発行されたデバイス アクション (今回は無視してください) |
| 製造元 | デバイスの製造元。 |
| モデル | デバイスのモデル。 |
| LastPolicyUpdateUtc | デバイスでポリシーが更新された最後の時刻。 |
| LastExchangeStatusUtc | デバイスと Exchange が同期を行った最後の時刻 |
| IsDeleted | Intune によるデバイスの管理が終了している場合、True に設定されます。 最後に確認されている状態が保存されます。 |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

**DevicePropertyHistory** エンティティには、デバイス テーブルと過去 90 日間の各デバイス レコードの日次スナップショットと同じプロパティが与えられます。 DateKey 列は、各行の日を示します。

| プロパティ  | 説明 |
|---------|------------|
| DateKey |日付テーブルの参照であり、日を示します。 |
| DeviceKey |データ ウェアハウスにおけるデバイスを示す一意識別子 - 代理キー。 これは、Intune デバイス ID が含まれるデバイス テーブルの参照です。 |
| DeviceName |デバイスに名前を付けられるプラットフォーム上にあるデバイスの名前。 その他のプラットフォームの場合、Intune がその他のプロパティから名前を作成します。 この属性は一部のデバイスで利用できません。 |
| DeviceTypeKey |このデバイスの種類属性のキー。 |
| ClientRegisterationStateKey |このデバイスのクライアント登録状態属性のキー。 |
| OwnerTypeKey |このデバイスの所有者の種類属性のキー (会社、個人、不明) |
| objectSourceKey |この列は無視してください。 |
| CreatedDate |デバイスが登録された日付。 |
| LastContact |Intune によるデバイス チェックインで最後に確認されているもの。 |
| LastContactNotification |Intune によるチェックインを Intune がデバイスに通知した最後の時刻。 |
| LastContactWorkplaceJoin |このデバイスの社内参加について最後に確認されている状態を示すタイムスタンプ |
| ManagementAgentKey |このデバイスに関連付けられている管理エージェントのキー |
| ManagementStateKey |このデバイスに関連付けられている管理状態を示すキーであり、リモート アクションの最新の状態を示すか、脱獄/ルート化状態を示します |
| ReferenceId |Azure Active Directory のデバイス ID。 |
| WorkPlaceJoinStateKey |このデバイスに関連付けられている社内参加の状態を示すキー |
| CategoryId |この列は無視してください。 |
| EnrollmentTypeKey |このデバイスに関連付けられている登録の種類を示すキーであり、登録の方法を示します |
| CertExpirationDate |MDM 管理証明書の有効期限日 |
| MdmStatusKey |MdmStatus キー。 |
| OSFamily |OS 製品群 (Windows、iOS、Android など) |
| OSVersion |OS のバージョン。 |
| OSMajorVersion |OS バージョンのメジャー バージョン コンポーネント (major.minor.build.revision)。 |
| OSMinorVersion |OS バージョンのマイナー バージョン コンポーネント (major.minor.build.revision)。 |
| OSBuildNumber |OS バージョンのビルド バージョン コンポーネント (major.minor.build.revision)。 |
| OSRevisionNumber |OS バージョンのリビジョン バージョン コンポーネント (major.minor.build.revision)。 |
| EasID |デバイスが Exchange Active Sync で管理されている場合、このデバイスの EAS ID |
| GraphDeviceIsManaged |Intune により Azure AD で最後に設定された管理状態。 |
| GraphDeviceIsCompliant |Intune により Azure AD で最後に設定されたコンプライアンス対応状態。 |
| SerialNumber |デバイスのシリアル番号 (使用可能な場合)。 |
| EnrolledByUser |このデバイスを登録したユーザーの ID であり、ユーザー テーブルの userId 列を参照します |
| RowLastModifiedDateTimeUTC |このレコードが変更された最後の時刻 |
| ProcessorArchitecture |プロセッサ アーキテクチャ。 |
| DeviceAction |最後に発行されたデバイス アクション (今回は無視してください) |
| 製造元 |デバイスの製造元。 |
| モデル |デバイスのモデル。 |
| LastPolicyUpdateUtc |デバイスでポリシーが更新された最後の時刻。 |
| LastExchangeStatusUtc |デバイスと Exchange が同期を行った最後の時刻 |

## <a name="mdmdeviceinventoryhistories"></a>MdmDeviceInventoryHistories

**MdmDeviceInventoryHistories** エンティティには、過去 90 日間、MDM で管理しているデバイスのインベントリ データを対象に毎日作成されたスナップショットが含まれています。 DateKey 列は行の日を示します。 デバイスによっては適用または入力されないプロパティがあります。詳しくは、このページを参照してください。 詳細については、「[Microsoft Intune でインベントリを使用してデバイスを把握する](https://docs.microsoft.com/Intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-Intune)」を参照してください。

| プロパティ  | 説明 |
|---------|------------|
| DateKey | 日付テーブルの参照であり、日を示します。 |
| DeviceKey |データ ウェアハウスにおけるデバイスを示す一意識別子 - 代理キー。 これは、Intune デバイス ID が含まれるデバイス テーブルの参照です。 |
| DeviceModel |デバイスのモデル。 |
| OS |デバイスの OS。 |
| DeviceName |デバイスに名前を付けられるプラットフォーム上にあるデバイスの名前。 その他のプラットフォームの場合、Intune がその他のプロパティから名前を作成します。 この属性は一部のデバイスで利用できません。 |
| SoftwareVersion |多くの場合、OS バージョンとは異なる Apple プラットフォームを除き、これは OS バージョンになります。 |
| Imei |IMEI 番号 |
| HardwareInventoryTimeUtc |このデバイスのインベントリが報告された最初の時刻 |
| InventoryModifiedTimeUtc |このスナップショットが作成されたときにインベントリが保存された最後の時刻。 |
| InventoryReportingTimeUtc |このデバイスのインベントリが回収された最後の時刻 |
| ExchangeActiveSyncId |Exchange ActiveSync デバイス ID。 |
| ComputerSystemDescription |システムの説明。 |
| ComputerSystemName |システム名。 |
| ComputerSystemManufacturer |システムの製造元。 |
| ComputerSystemModel |システムのモデル。 |
| UserName |ユーザー名。 |
| OSType |OS の種類。 |
| OSCaption |OS キャプション。 |
| OSName |OS の名前。 |
| OSManufacturer |OS の製造元。 |
| OSProductSuite |OS 製品スイート。 |
| OSProductType |OS 製品の種類。 |
| ロケール |OS ロケール。 |
| PhysicalMemoryCapacity |物理メモリ容量 (バイト単位)。 |
| PhysicalMemoryRemovable |物理リムーバブル メモリ (バイト単位)。 |
| SystemEnclosureChassisTypesInnerText |このデバイスのシステム シャーシの種類を定義します。 数字は次の値を示します。  <br>0 または空白 = 不明   <br>1 = デスクトップ   <br>2 = ノート PC  <br>3 = ワークステーション  <br>4 = エンタープライズ サーバー  <br>100 = 電話  <br>101 = タブレット  <br>102/103 = 別の不明な種類のモバイル デバイス |
| SystemEnclosureModel |システム格納装置のモデル。 |
| SystemEnclosureSerialNumber |システム格納装置のシリアル番号。 |
| NetworkAdapterConfigurationText |ネットワーク アダプターからの構成テキスト。 |
| MacAddress |MAC アドレス。 |
| SmsID |Intune デバイス ID。 |
| CertExpiry |MDM 管理証明書の有効期限日 |
| DeviceClientAgentVersion |クライアント エージェントのバージョン。 |
| DeviceClientID |デバイスのクライアント ID。 |
| SerialNumber |シリアル番号。 |
| DeviceManufacturer |デバイスの製造元。 |
| DMVersion |DM バージョン。 |
| FirmwareVersion |ファームウェアのバージョン。 |
| HardwareVersion |ハードウェアのバージョン。 |
| PlatformType |プラットフォームの種類。 |
| ProcessorLevel |プロセッサのレベル。 |
| ProcessorRevision |プロセッサのリビジョン。 |
| 製品 |製品。 |
| ProductVersion |製品のバージョン。 |
| OEM |相手先ブランド供給。 |
| DeviceBuildVersion |デバイスのビルド バージョン。 |
| Meid |モバイル機器の識別子 |
| PhoneNumber |電話番号。 |
| SubscriberCarrierNetwork |電話通信事業者のネットワーク名。 |
| CellularTechnology |電話通信事業者のネットワークの種類 (CDMA/GSM)。 |
| Imsi |IMSI 番号。 |
| JailBroken |デバイスが脱獄またはルート化されている場合は True |
| IsActivationLockEnabled |アクティベーション ロックが有効な場合は True |
| DeviceType |デバイスの種類 |
| IsSupervised |監督対象モードになっています |
| DeviceDisplayNumberOfColors |デバイスのディスプレイの色数 |
| HorizontalResolution |デバイスの水平画面解像度 |
| VerticalResolution |デバイスの垂直画面解像度 |
| StorageFree |記憶域の空き容量 (バイト単位) |
| StorageTotal |記憶域の合計容量 (バイト単位) |
| ProgramFree |プログラム実行用メモリの空き容量 (バイト単位) |
| ProgramTotal |プログラム実行用メモリの合計容量 (バイト単位) |
| RemovableStorageFree |リムーバブル記憶域の空き容量 (バイト単位) |
| RemovableStorageTotal |リムーバブル記憶域の合計容量 (バイト単位) |
| DeviceMemoryDeviceCapacity |デバイス メモリの容量 |
| DeviceMemoryAvailableDeviceCapacity |デバイス メモリの空き容量 |
| DeviceOSVersion |OS のバージョン |
| DeviceOSPlatform |OS のプラットフォーム |
| DeviceOSLanguage |OS の言語 |
| PasswordMaxAttemptsBeforeWipe |パスワードの最大試行回数であり、これを超えるとデバイスがワイプされます |
| PasswordMinComplexChars |パスワードに必要な複合文字の最小数 |
| PasswordMinLength |パスワードの必要な長さの最小値 |
| PasswordHistory |パスワードを記録し、過去に使った中で最も新しい n 個までのパスワードを使用禁止とするとき、その最小数をここで指定します |
| PasswordEnabled |パスワードが有効かどうか |
| PasswordExpiration |パスワード - 有効期限。 |
| AllowRecoveryPassword |パスワードの復元を許可する。 |
| PasswordAutoLockTimeout |パスワード - 自動ロック タイムアウト。 |
| PasswordType |パスワードの種類。 |
| BacklightACTimeout |電源利用時のバックライトのタイムアウト。 |
| BacklightBatTimeout |バッテリー利用時のバックライトのタイムアウト。 |
| PowerBackupPercent |電源バックアップ パーセント。 |
| BatteryPercent |残りのバッテリーのパーセント |
| PlatformID |プラットフォーム ID。 |
| ExchangeDeviceID |Exchange デバイス ID。 |
| SmsProcessorDescription |プロセッサの説明。 |
| OwnerEmailAddress |所有者の電子メール アドレス。 |
| DeviceOSName |OS の名前。 |
| WifiMac |WiFi Mac アドレス。 |
| EthernetMac |イーサネット MAC アドレス。 |
| RequireEncryption |デバイスが暗号化されているかどうかを示します |
| ActivationLockBypassCode |アクティベーション ロックのバイパス コード。 |

## <a name="applicationinventory"></a>ApplicationInventory

**ApplicationInventory** エンティティには、インベントリ回収時にデバイスで検出されたアプリが一覧表示されます。

| プロパティ  | 説明 |
|---------|------------|
| DeviceKey |デバイス テーブルの参照。 |
| ApplicationKey |? (ExchangeDeviceService\DeviceApplication からコピーされます)。 |
| ApplicationName |? (ExchangeDeviceService\DeviceApplication からコピーされます)。 |
| ApplicationVersion |? (ExchangeDeviceService\DeviceApplication からコピーされます)。 |
| BundleSize |? (ExchangeDeviceService\DeviceApplication からコピーされます)。 |
