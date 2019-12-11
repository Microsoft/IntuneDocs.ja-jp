---
title: アプリケーション エンティティのリファレンス
titleSuffix: Microsoft Intune
description: Intune データ ウェアハウス API にあるエンティティ コレクションのアプリケーション カテゴリのための参照トピック。
keywords: Intune データ ウェアハウス
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4a8fa34673340e4adca7b64707d8c79d4808460
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74290950"
---
# <a name="reference-for-application-entities"></a>アプリケーション エンティティのリファレンス

**アプリケーション** カテゴリには、次のような情報を追跡するデバイスのエンティティが含まれています。

- アプリのバージョン
- アプリのインストール ソース
- アプリを作成した開発者の種類
- **sidecar** や **desktop** など、アプリの管理対象ソフトウェアの種類
- アプリのボリューム購入プログラム (VPP) 状態

## <a name="apprevisions"></a>appRevisions

**appRevision** エンティティには、アプリのすべてのバージョンがリストされています。

| プロパティ  | 説明 | 例 |
|---------|------------|--------|
| appKey |アプリを示す一意識別子。 |123 |
| applicationId |アプリを示す一意識別子 - AppKey に似ていますが、このキーはナチュラルです。 |b66bc706-ffff-7437-0340-032819502773 |
| revision |バイナリのアップロード中に管理者が挙げたバージョン。 |2 |
| title |アプリのタイトル。 |Excel |
| publisher |アプリの発行者。 |Microsoft |
| uploadState |アプリのアップロード状態。 |1 |
| appTypeKey |AppType の参照 (次のセクションに説明あり) | |
| vppProgramTypeKey |VppProgramType の参照 (下に説明あり)。 | |
| creationTime |このリビジョンが作成された時刻。 |11/23/2016 12:00:00 AM |
| modifiedTime |このリビジョンに関連する事項が最後に変更された時刻。 |11/23/2016 12:00:00 AM |
| サイズ |バイナリのサイズ。 | |
| startDateInclusiveUTC |このアプリ リビジョンがデータ ウェアハウスで作成されたときの UTC 日時。 |11/23/2016 12:00:00 AM |
| endDateExclusiveUTC |このアプリ リビジョンが推奨されなくなったときの UTC 日時。 |11/23/2016 12:00:00 AM |
| isCurrent |データ ウェアハウスにおいて、このアプリ バージョンが現行のものであるかどうかを示します。 |真/偽 |
| rowLastModifiedDateTimeUTC |このアプリ バージョンがデータ ウェアハウスで最後に変更されたときの UTC 日時。 |11/23/2016 12:00:00 AM |

## <a name="apptypes"></a>appTypes

**appType** エンティティには、アプリのインストール ソースがリストされています。

| プロパティ  | 説明 |
|---------|------------|
| appTypeID |種類の ID |
| appTypeKey |キーの代理キー |
| appTypeName |アプリの種類 |

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


## <a name="vppprogramtypes"></a>vppProgramTypes

**vppProgramType** エンティティには、アプリの VPP プログラムの種類がリストされています。

| プロパティ  | 説明 |
|---------|------------|
| vppProgramTypeID | 種類の ID。 |
| vppProgramTypeKey | キーの代理キー。 |
| vppProgramTypeName | VPP プログラムの種類。 |

### <a name="example"></a>例

| VppProgramID  | 名前 | 説明 |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Microsoft の VPP プログラム。 |
| 00000000-0000-0000-0000-000000000000 | まだ利用できません | 既定値、VPP なし。 |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Apple の VPP プログラム。 |



## <a name="applicationinventories"></a>applicationInventories

**applicationInventory** エンティティには、インベントリ回収時にデバイスで検出されたアプリケーションがリストされています。

| プロパティ  | 説明 |
|---------|------------|
| deviceKey | これは、Intune デバイス ID が含まれるデバイス テーブルの参照です。 |
| dateKey | 日付テーブルの参照であり、インベントリの日を示します。 |
| applicationName | アプリケーション名。 |
| applicationVersion | アプリケーションのバージョン。 |
| bundleSize | アプリのサイズ (バイト単位)。 |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates

**mobileAppInstallState** エンティティは、デバイス、ユーザー、またはその両方を含むグループに割り当てられた後のモバイル アプリケーションのインストール状態を表します。

| プロパティ | 説明 |
|---|---|
| appInstallStateKey | アカウントにおけるアプリのインストール状態の一意の ID。 |
| appInstallState | アプリのインストール状態の列挙値。 |
| appInstallStateName | アプリのインストール状態の名前。 |



