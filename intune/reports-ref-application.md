---
title: アプリケーション
titlesuffix: Microsoft Intune
description: Intune データ ウェアハウス API にあるエンティティ コレクションのアプリケーション カテゴリのための参照トピック。
keywords: Intune データ ウェアハウス
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 32f41e4f299af4802dd270ec4a46c0cf4d467bc9
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179135"
---
# <a name="reference-for-application-entities"></a>アプリケーション エンティティのリファレンス

**アプリケーション** カテゴリには、次のような情報を追跡記録するモバイル デバイスのエンティティが含まれています。

  -  アプリのバージョン
  -  アプリのインストール ソース
  -  アプリを作成した開発者の種類
  -  **sidecar** や **desktop** など、アプリの管理対象ソフトウェアの種類
  -  アプリのボリューム購入プログラム (VPP) 状態

## <a name="apprevision"></a>AppRevision

**AppRevision** エンティティは、アプリのバージョンをすべて一覧表示します。

| プロパティ  | 説明 | 例 |
|---------|------------|--------|
| AppKey |アプリを示す一意識別子。 |123 |
| ApplicationId |アプリを示す一意識別子 - AppKey に似ていますが、このキーはナチュラルです。 |b66bc706-ffff-7437-0340-032819502773 |
| リビジョン |バイナリのアップロード中に管理者が挙げたバージョン。 |2 |
| タイトル |アプリのタイトル。 |Excel |
| 発行者 |アプリの発行者。 |Microsoft |
| UploadState |アプリのアップロード状態。 |1 |
| AppTypeKey |AppType の参照 (次のセクションに説明あり) | |
| VppProgramTypeKey |VppProgramType の参照 (下に説明あり)。 | |
| CreationTime |このリビジョンが作成された時刻。 |11/23/2016 12:00:00 AM |
| ModifiedTime |このリビジョンに関連する事項が最後に変更された時刻。 |11/23/2016 12:00:00 AM |
| Size |バイナリのサイズ。 | |
| StartDateInclusiveUTC |このアプリ リビジョンがデータ ウェアハウスで作成されたときの UTC 日時。 |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |このアプリ リビジョンが推奨されなくなったときの UTC 日時。 |11/23/2016 12:00:00 AM |
| IsCurrent |データ ウェアハウスにおいて、このアプリ バージョンが現行のものであるかどうかを示します。 |真/偽 |
| RowLastModifiedDateTimeUTC |このアプリ バージョンがデータ ウェアハウスで最後に変更されたときの UTC 日時。 |11/23/2016 12:00:00 AM |

## <a name="apptypes"></a>AppTypes

**AppTypes** エンティティは、アプリのインストール ソースを一覧表示します。

| プロパティ  | 説明 |
|---------|------------|
| AppTypeID |種類の ID |
| AppTypeKey |キーの代理キー |
| AppTypeName |アプリの種類 |

### <a name="example"></a>例

| AppTypeID  | 名前 | 説明 |
|---------|------------|--------|
| 0 |Android ストア アプリ | Android ストア アプリ。 |
| 1 |Android LOB アプリ | Android の基幹業務アプリ。 |
| 2 |管理対象 Android ストア アプリ (MAM) | 管理を有効にしている Android ストア アプリ。 |
| 3 |iOS ストア アプリ | iOS ストア アプリ。 |
| 4 |iOS LOB アプリ | iOS の基幹業務アプリ。 |
| 5 |管理対象 iOS ストア アプリ (MAM) | 管理を有効にしている iOS ストア アプリ。 |
| 6 |O365 Pro Plus Suite | Office 365 Pro Plus Suite for Windows 10。 |
| 7 |Web アプリ | Web アプリ。 |
| 8 |Windows Phone 8.1 ストア アプリ | Windows Phone 8.1 ストア アプリ。 |
| 9 |Windows ストア アプリ | Windows ストア アプリ。 |
| 10 |Windows LOB アプリ | Windows AppX 基幹業務アプリ。 |
| 11 |Windows Mobile MSI | MSI の基幹業務アプリ。 |
| 12 |Windows Phone LOB アプリ | Windows Phone 基幹業務アプリ。 |


## <a name="vppprogramtypes"></a>VppProgramTypes

**VppProgramTypes** エンティティは、アプリの VPP プログラムの種類を一覧表示します。

| プロパティ  | 説明 |
|---------|------------|
| VppProgramTypeID | 種類の ID。 |
| VppProgramTypeKey | キーの代理キー。 |
| VppProgramTypeName | VPP プログラムの種類。 |

### <a name="example"></a>例

| VppProgramID  | 名前 | 説明 |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Microsoft の VPP プログラム。 |
| 00000000-0000-0000-0000-000000000000 | まだ利用できません | 既定値、VPP なし。 |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Apple の VPP プログラム。 |



## <a name="applicationinventory"></a>ApplicationInventory

**ApplicationInventory** エンティティには、インベントリ回収時にデバイスで検出されたアプリケーションが一覧表示されます。

| プロパティ  | 説明 |
|---------|------------|
| DeviceKey | これは、Intune デバイス ID が含まれるデバイス テーブルの参照です。 |
| DateKey | 日付テーブルの参照であり、インベントリの日を示します。 |
| ApplicationName | アプリケーション名。 |
| ApplicationVersion | アプリケーションのバージョン。 |
| BundleSize | アプリのサイズ (バイト単位)。 |

## <a name="mobileappinstallstate"></a>MobileAppInstallState

**MobileAppInstallState** エンティティは、デバイス、ユーザーまたはその両方を含むグループに割り当てられた後のモバイル アプリケーションのインストール状態を表します。

| プロパティ | 説明 |
|---|---|
| AppInstallStateKey | アカウントにおけるアプリのインストール状態の一意の ID。 |
| AppInstallState | アプリのインストール状態の列挙値。 |
| AppInstallStateName | アプリのインストール状態の名前。 |

## <a name="mobileappdeviceuserinstallstatus"></a>MobileAppDeviceUserInstallStatus

**MobileAppDeviceUserInstallStatus** は、特定のデバイスとユーザーのモバイル アプリのインストール状態を表します。


|      プロパティ      |                                                         説明                                                         |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------|
|      DateKey       |                                  アプリのインストール状態が記録されたときの日付のキー。                                  |
|       AppKey       |                             AppRevision のインスタンスの識別に使用する、モバイル アプリのキー。                              |
|     DeviceKey      |                              Device のインスタンスの識別に使用する、対象デバイスのキー。                               |
|      UserKey       |                                User のインスタンスの識別に使用する、対象ユーザーのキー。                                 |
| AppInstallStateKey |                     MobileAppInstallState のインスタンスの識別に使用する、アプリのインストール状態のキー。                     |
|     エラー コード      | アプリのインストーラー、モバイル プラットフォーム、またはアプリのインストールと関わりがあるサービスによって返されるエラー コード。 |

