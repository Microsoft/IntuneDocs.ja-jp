---
title: モバイル アプリ管理 (MAM)
titleSuffix: Microsoft Intune
description: Intune データ ウェアハウス API にあるエンティティ コレクションのモバイル アプリ管理カテゴリのための参照トピック。
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
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 456abbf849120675b6a7c108ca65c6f9967ae64a
ms.sourcegitcommit: 601327125ac8ae912d8159422de8aac7dbdc25f6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59429201"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>モバイル アプリ管理 (MAM) エンティティのリファレンス

**モバイル アプリ管理**カテゴリには、次のようなモバイル アプリのエンティティが含まれています。

  -  アプリ
  -  Instances
  -  チェックインの状態
  -  正常性の状態
  -  ポリシーの状態
  -  登録ステータス
  -  プラットフォームの種類

## <a name="mamapplication"></a>MamApplication

**MamApplication** エンティティは、企業内登録なしで、モバイル アプリケーション管理 (MAM) 経由で管理される基幹業務 (LOB) アプリを一覧表示します。

| プロパティ | 説明 | 例 |
|---------|------------|--------|
| mamApplicationKey |MAM アプリケーションの一意の識別子。 | 432 |
| mamApplicationName |MAM アプリケーションの名前。 |MAM アプリケーション名の例 |
| mamApplicationId |MAM アプリのアプリケーション ID。 | 123 |
| IsDeleted |この MAM アプリ レコードが更新されているかどうかを示します。 <br>True - MAM アプリには新しいレコードがあり、そのフィールドはこのテーブルで更新されています。 <br>False - この MAM アプリの最新のレコード。 |真/偽 |
| StartDateInclusiveUTC |この MAM アプリがデータ ウェアハウスで作成されたときの UTC 日時。 |11/23/2016 12:00:00 AM |
| DeletedDateUTC |IsDeleted が True に変更されたときの UTC 日時。 |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |この MAM アプリがデータ ウェアハウスで最後に変更されたときの UTC 日時。 |11/23/2016 12:00:00 AM |


## <a name="mamapplicationinstance"></a>MamApplicationInstance

**MamApplicationInstance** エンティティは、デバイス別ユーザー別の単一インスタンスとして、管理されているモバイル アプリケーション管理 (MAM) アプリを一覧表示します。 エンティティ内に一覧表示されているユーザーとデバイスはすべて、少なくとも 1 つの MAM ポリシーが割り当てられ、保護されます。


|          プロパティ          |                                                                                                  説明                                                                                                  |               例                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   ApplicationInstanceKey   |                                                               データ ウェアハウスにおける MAM アプリ インスタンスを示す一意識別子 - 代理キー。                                                                |                 123                  |
|           UserId           |                                                                              この MAM アプリをインストールしたユーザーのユーザー ID。                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   ApplicationInstanceId    |                                              MAM アプリ インスタンスを示す一意識別子 - ApplicationInstanceKey に似ていますが、識別子はナチュラル キーです。                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | この Mam アプリケーション インスタンスが作成された Mam アプリケーションのアプリケーション Id。   | 11/23/2016 12:00:00 AM   |
|     ApplicationVersion     |                                                                                     この MAM アプリのアプリケーション バージョン。                                                                                      |                  2                   |
|        CreatedDate         |                                                                 MAM アプリ インスタンスのこのレコードが作成された日付 値は null を取ることができます。                                                                 |        11/23/2016 12:00:00 AM        |
|          プラットフォーム          |                                                                          この MAM アプリがインストールされているデバイスのプラットフォーム。                                                                           |                  2                   |
|      PlatformVersion       |                                                                      この MAM アプリがインストールされているデバイスのプラットフォーム バージョン。                                                                       |                 2.2                  |
|         SdkVersion         |                                                                            この MAM アプリをラップした MAM SDK バージョン。                                                                            |                 3.2                  |
| mamDeviceId | 使用する MAM アプリケーション インスタンスが関連付けられているデバイスのデバイス Id。   | 11/23/2016 12:00:00 AM   |
| mamDeviceType | 使用する MAM アプリケーション インスタンスが関連付けられているデバイスのデバイスの種類。   | 11/23/2016 12:00:00 AM   |
| mamDeviceName | 使用する MAM アプリケーション インスタンスが関連付けられているデバイスのデバイス名。   | 11/23/2016 12:00:00 AM   |
|         IsDeleted          | この MAM アプリ インスタンス レコードが更新されているかどうかを示します。 <br>True - この MAM アプリ インスタンスには新しいレコードがあり、そのフィールドはこのテーブルで更新されています。 <br>False - この MAM アプリ インスタンスの最新のレコード。 |              真/偽              |
|   StartDateInclusiveUtc    |                                                              この MAM アプリ インスタンスがデータ ウェアハウスで作成されたときの UTC 日時。                                                               |        11/23/2016 12:00:00 AM        |
|       DeletedDateUtc       |                                                                             IsDeleted が True に変更されたときの UTC 日時。                                                                              |        11/23/2016 12:00:00 AM        |
| RowLastModifiedDateTimeUtc |                                                           この MAM アプリ インスタンスがデータ ウェアハウスで最後に変更されたときの UTC 日時。                                                            |        11/23/2016 12:00:00 AM        |


## <a name="mamcheckin"></a>MamCheckin

**MamCheckin** エンティティは、モバイル アプリケーション管理 (MAM) アプリ インスタンスが Intune サービスでチェックインしたときに集められたデータを表します。 

> [!Note]  
> アプリ インスタンスが一日に複数回チェックインするとき、データ ウェアハウスは単一チェックインとしてそれを保存します。

| プロパティ | 説明 | 例 |
|---------|------------|--------|
| DateKey |MAM アプリ チェックインがデータ ウェアハウスに記録されたときの日付キー。 | 20160703 |
| ApplicationInstanceKey |この MAM アプリ チェックインに関連付けられているアプリ インスタンスのキー。 | 123 |
| UserKey |この MAM アプリ チェックインに関連付けられているユーザーのキー。 | 4323 |
| mamApplicationKey |アプリケーション キーの関連付けられているアプリケーションでの MAM アプリケーションのチェック。 | 432 |
| DeviceHealthKey |この MAM アプリ チェックインに関連付けられている DeviceHealth のキー。 | 321 |
| PlatformKey |この MAM アプリ チェックインに関連付けられているデバイスのプラットフォームを表します。 |123 |
| EffectiveAppliedPolicyKey |チェックインした MAM アプリに関連付けられているポリシーが適用されていることを表します。 特定のアプリとユーザーに関連するポリシーがすべて結合された結果、ポリシー適用は有効となります。 | 322 |
| LastCheckInDate |この MAM アプリが最後にチェックインした日時 値は null を取ることができます。 |11/23/2016 12:00:00 AM |


## <a name="mamdevicehealth"></a>MamDeviceHealth

**MamDeviceHealth** エンティティは、モバイル アプリケーション管理 (MAM) ポリシーが展開されているデバイスを表します。脱獄されているものも含まれます。

| プロパティ | 説明 | 例 |
|---------|------------|--------|
| DeviceHealthKey |データ ウェアハウスにおけるデバイスとそれに関連付けられている正常性を示す一意識別子 - 代理キー。 |123 |
| DeviceHealth |デバイスとそれに関連付けられている正常性を示す一意識別子 - DeviceHealthKey に似ていますが、この識別子はナチュラル キーです。 |b66bc706-ffff-7777-0340-032819502773 |
| DeviceHealthName |デバイスの状態を表します。 <br>利用不可 - このデバイスの情報はありません。 <br>正常 - デバイスは脱獄されていません。 <br>異常 - デバイスは脱獄されています。 |利用不可、正常、異常 |
| RowLastModifiedDateTimeUtc |この特定の MAM デバイス正常性がデータ ウェアハウスで最後に変更されたときの UTC 日時。 |11/23/2016 12:00:00 AM |

## <a name="mameffectivepolicy"></a>MamEffectivePolicy

**MamEffectivePolicy** エンティティは、組織で適用されている有効なモバイル アプリケーション管理 (MAM) ポリシーをすべて一覧表示します。 特定のアプリとユーザーに関連するポリシーがすべて結合された結果、ポリシー適用は有効となります。

| プロパティ | 説明 | 例 |
|---------|------------|--------|
| EffectivePolicyKey |データ ウェアハウスにおける有効な MAM ポリシーを示す一意識別子。 |2 |
| RealPolicyKey |IT プロフェッショナルが作成した MAM ポリシーを示す一意識別子。 |1 |
| RowCreatedDateTimeUtc |この有効な MAM ポリシーがデータ ウェアハウスで作成されたときの UTC 日時。 |11/23/2016 12:00:00 AM |

## <a name="mamglobalapplication"></a>MamGlobalApplication

**MamGlobalApplication** エンティティは、企業内登録なしで、モバイル アプリケーション管理 (MAM) 経由で管理されるストア アプリを一覧表示します。


|          プロパティ          |                                               説明                                               |           例            |
|----------------------------|---------------------------------------------------------------------------------------------------------|------------------------------|
|       ApplicationKey       |          データ ウェアハウスにおけるストア アプリを示す一意識別子で代理キー。          |             123              |
|       ApplicationId        | ストア アプリを示す一意識別子。 この識別子は ApplicationKey に似ていますが、ナチュラル キーです。  | com.microsoft.skydrive.<ios> |
|      ApplicationName       |                                      MAM グローバル アプリケーション名。                                       |           Skydrive           |
| RowLastModifiedDateTimeUtc | この特定の MAM グローバル アプリケーションがデータ ウェアハウスで最後に変更されたときの UTC 日時。 |    11/23/2016 12:00:00 AM    |

## <a name="mamplatform"></a>MamPlatform

**MamPlatform** エンティティは、モバイル アプリケーション管理 (MAM) アプリがインストールされたプラットフォームの名前と種類を一覧表示します。


|          プロパティ          |                                    説明                                    |                         例                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        PlatformKey         |     データ ウェアハウスにおけるプラットフォームを示す一意識別子 - 代理キー。      |                           123                           |
|          プラットフォーム          | プラットフォームを示す一意識別子 - PlatformKey に似ていますが、ナチュラル キーです。 |                           123                           |
|        PlatformName        |                                   プラットフォームの名前                                   | 利用不可 <br>なし <br>Windows <br>iOS <br>Android。 |
| RowLastModifiedDateTimeUtc | このプラットフォームがデータ ウェアハウスで最後に変更されたときの UTC 日時。  |                 11/23/2016 12:00:00 AM                  |

