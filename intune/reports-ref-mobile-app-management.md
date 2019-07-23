---
title: モバイル アプリ管理 (MAM)
titleSuffix: Microsoft Intune
description: Intune データ ウェアハウス API にあるエンティティ コレクションのモバイル アプリ管理カテゴリのための参照トピック。
keywords: Intune データ ウェアハウス
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c549a7063883f637ac7b5316e767b159d2328d0b
ms.sourcegitcommit: c3ac858bbadb63d248ed54069e48160d703bbaf2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313656"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>モバイル アプリ管理 (MAM) エンティティのリファレンス

**モバイル アプリ管理**カテゴリには、次のようなモバイル アプリのエンティティが含まれています。

- アプリ
- Instances
- チェックインの状態
- 正常性の状態
- ポリシーの状態
- 登録ステータス
- プラットフォームの種類

## <a name="mamapplications"></a>mamApplications

**mamApplication** エンティティには、企業に登録することなくモバイル アプリケーション管理 (MAM) 経由で管理される基幹業務 (LOB) アプリがリストされています。

| プロパティ | 説明 | 例 |
|---------|------------|--------|
| mamApplicationKey |MAM アプリケーションの一意識別子。 | 432 |
| mamApplicationName |MAM アプリケーションの名前。 |MAM Application Example Name |
| mamApplicationId |MAM アプリケーションのアプリケーション ID。 | 123 |
| isDeleted |この MAM アプリ レコードが更新されているかどうかを示します。 <br>True - MAM アプリには新しいレコードがあり、そのフィールドはこのテーブルで更新されています。 <br>False - この MAM アプリの最新のレコード。 |真/偽 |
| startDateInclusiveUTC |この MAM アプリがデータ ウェアハウスで作成されたときの UTC 日時。 |11/23/2016 12:00:00 AM |
| deletedDateUTC |IsDeleted が True に変更されたときの UTC 日時。 |11/23/2016 12:00:00 AM |
| rowLastModifiedDateTimeUTC |この MAM アプリがデータ ウェアハウスで最後に変更されたときの UTC 日時。 |11/23/2016 12:00:00 AM |


## <a name="mamapplicationinstances"></a>mamApplicationInstances

**mamApplicationInstance** エンティティには、モバイル アプリケーション管理 (MAM) のマネージド アプリが、デバイス別ユーザー別の単一インスタンスとしてリストされています。 エンティティ内に一覧表示されているユーザーとデバイスはすべて、少なくとも 1 つの MAM ポリシーが割り当てられ、保護されます。


|          プロパティ          |                                                                                                  説明                                                                                                  |               例                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   applicationInstanceKey   |                                                               データ ウェアハウスにおける MAM アプリ インスタンスを示す一意識別子 - 代理キー。                                                                |                 123                  |
|           userId           |                                                                              この MAM アプリをインストールしたユーザーのユーザー ID。                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   applicationInstanceId    |                                              MAM アプリ インスタンスを示す一意識別子 - ApplicationInstanceKey に似ていますが、識別子はナチュラル キーです。                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | この MAM アプリケーション インスタンスの作成に使用された MAM アプリケーションのアプリケーション ID。   | 11/23/2016 12:00:00 AM   |
|     applicationVersion     |                                                                                     この MAM アプリのアプリケーション バージョン。                                                                                      |                  2                   |
|        createdDate         |                                                                 MAM アプリ インスタンスのこのレコードが作成された日付 値は null を取ることができます。                                                                 |        11/23/2016 12:00:00 AM        |
|          プラットフォーム          |                                                                          この MAM アプリがインストールされているデバイスのプラットフォーム。                                                                           |                  2                   |
|      platformVersion       |                                                                      この MAM アプリがインストールされているデバイスのプラットフォーム バージョン。                                                                       |                 2.2                  |
|         sdkVersion         |                                                                            この MAM アプリをラップした MAM SDK バージョン。                                                                            |                 3.2                  |
| mamDeviceId | MAM アプリケーションのインスタンスが関連付けられているデバイスのデバイス ID。   | 11/23/2016 12:00:00 AM   |
| mamDeviceType | MAM アプリケーション インスタンスが関連付けられているデバイスのデバイスの種類。   | 11/23/2016 12:00:00 AM   |
| mamDeviceName | MAM アプリケーション インスタンスが関連付けられているデバイスのデバイス名。   | 11/23/2016 12:00:00 AM   |
|         isDeleted          | この MAM アプリ インスタンス レコードが更新されているかどうかを示します。 <br>True - この MAM アプリ インスタンスには新しいレコードがあり、そのフィールドはこのテーブルで更新されています。 <br>False - この MAM アプリ インスタンスの最新のレコード。 |              真/偽              |
|   startDateInclusiveUtc    |                                                              この MAM アプリ インスタンスがデータ ウェアハウスで作成されたときの UTC 日時。                                                               |        11/23/2016 12:00:00 AM        |
|       deletedDateUtc       |                                                                             IsDeleted が True に変更されたときの UTC 日時。                                                                              |        11/23/2016 12:00:00 AM        |
| rowLastModifiedDateTimeUtc |                                                           この MAM アプリ インスタンスがデータ ウェアハウスで最後に変更されたときの UTC 日時。                                                            |        11/23/2016 12:00:00 AM        |


## <a name="mamcheckins"></a>mamCheckins

**mamCheckin** エンティティは、モバイル アプリケーション管理 (MAM) アプリのインスタンスが Intune サービスでチェックインしたときに集められたデータを表します。 

> [!Note]  
> アプリ インスタンスが一日に複数回チェックインするとき、データ ウェアハウスは単一チェックインとしてそれを保存します。

| プロパティ | 説明 | 例 |
|---------|------------|--------|
| dateKey |MAM アプリ チェックインがデータ ウェアハウスに記録されたときの日付キー。 | 20160703 |
| applicationInstanceKey |この MAM アプリ チェックインに関連付けられているアプリ インスタンスのキー。 | 123 |
| userKey |この MAM アプリ チェックインに関連付けられているユーザーのキー。 | 4323 |
| mamApplicationKey |MAM アプリケーションのチェックインに関連付けられているアプリケーションのアプリケーション キー。 | 432 |
| deviceHealthKey |この MAM アプリ チェックインに関連付けられている DeviceHealth のキー。 | 321 |
| platformKey |この MAM アプリ チェックインに関連付けられているデバイスのプラットフォームを表します。 |123 |
| effectiveAppliedPolicyKey |チェックインした MAM アプリに関連付けられているポリシーが適用されていることを表します。 特定のアプリとユーザーに関連するポリシーがすべて結合された結果、ポリシー適用は有効となります。 | 322 |
| pastCheckInDate |この MAM アプリが最後にチェックインした日時 値は null を取ることができます。 |11/23/2016 12:00:00 AM |


## <a name="mamdevicehealth"></a>mamDeviceHealth

**mamDeviceHealth** エンティティは、モバイル アプリケーション管理 (MAM) ポリシーが展開されているデバイスを表します。脱獄されているものも含まれます。

| プロパティ | 説明 | 例 |
|---------|------------|--------|
| deviceHealthKey |データ ウェアハウスにおけるデバイスとそれに関連付けられている正常性を示す一意識別子 - 代理キー。 |123 |
| deviceHealth |デバイスとそれに関連付けられている正常性を示す一意識別子 - DeviceHealthKey に似ていますが、この識別子はナチュラル キーです。 |b66bc706-ffff-7777-0340-032819502773 |
| deviceHealthName |デバイスの状態を表します。 <br>利用不可 - このデバイスの情報はありません。 <br>正常 - デバイスは脱獄されていません。 <br>異常 - デバイスは脱獄されています。 |利用不可、正常、異常 |
| rowLastModifiedDateTimeUtc |この特定の MAM デバイス正常性がデータ ウェアハウスで最後に変更されたときの UTC 日時。 |11/23/2016 12:00:00 AM |

## <a name="mameffectivepolicies"></a>mamEffectivePolicies

**mamEffectivePolicy** エンティティには、組織で適用されている有効なモバイル アプリケーション管理 (MAM) ポリシーがすべてリストされています。 特定のアプリとユーザーに関連するポリシーがすべて結合された結果、ポリシー適用は有効となります。

| プロパティ | 説明 | 例 |
|---------|------------|--------|
| effectivePolicyKey |データ ウェアハウスにおける有効な MAM ポリシーを示す一意識別子。 |2 |
| realPolicyKey |IT プロフェッショナルが作成した MAM ポリシーを示す一意識別子。 |1 |
| rowCreatedDateTimeUtc |この有効な MAM ポリシーがデータ ウェアハウスで作成されたときの UTC 日時。 |11/23/2016 12:00:00 AM |

## <a name="mamplatforms"></a>mamPlatforms

**mamPlatform** エンティティには、モバイル アプリケーション管理 (MAM) アプリがインストールされたプラットフォームの名前と種類がリストされています。


|          プロパティ          |                                    説明                                    |                         例                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        platformKey         |     データ ウェアハウスにおけるプラットフォームを示す一意識別子 - 代理キー。      |                           123                           |
|          プラットフォーム          | プラットフォームを示す一意識別子 - PlatformKey に似ていますが、ナチュラル キーです。 |                           123                           |
|        platformName        |                                   プラットフォームの名前                                   | 利用不可 <br>なし <br>Windows <br>iOS <br>Android。 |
| rowLastModifiedDateTimeUtc | このプラットフォームがデータ ウェアハウスで最後に変更されたときの UTC 日時。  |                 11/23/2016 12:00:00 AM                  |

