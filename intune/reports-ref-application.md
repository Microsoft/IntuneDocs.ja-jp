---
title: "アプリケーション | Microsoft Docs"
description: "Intune データ ウェアハウス API にあるエンティティ コレクションのアプリケーション カテゴリのための参照トピック。"
keywords: "Intune データ ウェアハウス"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2e12792445b36ba6657cbe6b2f6c924f6d97fe3c
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2017
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
| AppKey |アプリを示す一意識別子 |123 |
| ApplicationId |アプリを示す一意識別子 - AppKey に似ていますが、このキーはナチュラルです。 |b66bc706-ffff-7437-0340-032819502773 |
| リビジョン |バイナリのアップロード中に管理者が挙げたバージョン |2 |
| タイトル |アプリのタイトル |Excel |
| 発行者 |アプリの発行者 |Microsoft |
| UploadState |アプリのアップロード状態 |1 |
| AppTypeKey |AppType の参照 (次のセクションに説明あり) | |
| VppProgramTypeKey |VppProgramType の参照 (下に説明あり) | |
| CreationTime |このリビジョンが作成された時刻 |11/23/2016 12:00:00 AM |
| ModifiedTime |このリビジョンに関連する事項が最後に変更された時刻 |11/23/2016 12:00:00 AM |
| Size |バイナリのサイズ | |
| StartDateInclusiveUTC |このアプリ リビジョンがデータ ウェアハウスで作成されたときの UTC 日時 |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |このアプリ リビジョンが推奨されなくなったときの UTC 日時 |11/23/2016 12:00:00 AM |
| IsCurrent |データ ウェアハウスにおいて、このアプリ バージョンが現行のものであるかどうかを示します |真/偽 |
| RowLastModifiedDateTimeUTC |このアプリ バージョンがデータ ウェアハウスで最後に変更されたときの UTC 日時 |11/23/2016 12:00:00 AM |

## <a name="appinstallertypes"></a>AppInstallerTypes

**AppInstallerTypes** エンティティは、アプリのインストール ソースを一覧表示します。

| プロパティ  | 説明 |
|---------|------------|
| AppTypeID |種類の ID |
| AppTypeKey |キーの代理キー |
| AppTypeName |アプリの種類 |

## <a name="example"></a>例

| AppTypeID  | 名前 | 説明 |
|---------|------------|--------|
| 0 |Android ストア アプリ |Android ストア アプリ |
| 1 |Android LOB アプリ |Android の基幹業務アプリ |
| 2 |管理対象 Android ストア アプリ (MAM) |管理を有効にしている Android ストア アプリ |
| 3 |iOS ストア アプリ |iOS ストア アプリ |
| 4 |iOS LOB アプリ |iOS の基幹業務アプリ |
| 5 |管理対象 iOS ストア アプリ (MAM) |管理を有効にしている iOS ストア アプリ |
| 6 |O365 Pro Plus Suite |Office 365 Pro Plus Suite for Windows 10 |
| 7 |Web アプリ |Web アプリ |
| 8 |Windows Phone 8.1 ストア アプリ |Windows Phone 8.1 ストア アプリ |
| 9 |Windows ストア アプリ |Windows ストア アプリ |
| 10 |Windows LOB アプリ |Windows AppX 基幹業務アプリ |
| 11 |Windows Mobile MSI |MSI の基幹業務アプリ |
| 12 |Windows Phone LOB アプリ |Windows Phone 基幹業務アプリ |

## <a name="applicationtypes"></a>ApplicationTypes

**ApplicationTypes** エンティティは、アプリの種類を一覧表示します。

| プロパティ  | 説明 |
|---------|------------|
| ApplicationTypeID |種類の ID |
| ApplicationTypeKey |キーの代理キー |
| ApplicationTypeName |アプリの種類 |

## <a name="example"></a>例

| ApplicationTypeID  | 名前 | 説明 |
|---------|------------|--------|
| 0 |InHouse |社内で開発されたアプリ |
| 1 |DeepLink |アプリ ストアのアプリへのリンク |
| 2 |WebLink |Web アプリへのリンク |

## <a name="managedsoftwaretypes"></a>ManagedSoftwareTypes

**ManagedSoftwareTypes** エンティティは、アプリの管理対象ソフトウェアの種類を一覧表示します。

| プロパティ  | 説明 |
|---------|------------|
| SoftwareTypeID |種類の ID |
| SoftwareTypeKey |キーの代理キー |
| SoftwareTypeName |ソフトウェアの種類 |

## <a name="example"></a>例

| SoftwareTypeID  | 名前 | 説明 |
|---------|------------|--------|
| 0 |デスクトップ |デスクトップ アプリ |
| 2 |更新プログラム、更新 |ウィンドウの更新 |
| 5 |SideCarAgent | |
| 1 |モバイル |モバイル アプリ |
| 3 |WebLink |Web リンク |
| 4 |VppDeepLink |アプリストアのアプリで、VPP (ボリューム購入プログラム) に含まれるアプリのリンク |

## <a name="vppprogramtypes"></a>VppProgramTypes

**VppProgramTypes** エンティティは、アプリの VPP プログラムの種類を一覧表示します。

| プロパティ  | 説明 |
|---------|------------|
| VppProgramTypeID |種類の ID |
| VppProgramTypeKey |キーの代理キー |
| VppProgramTypeName |VPP プログラムの種類 |

## <a name="example"></a>例

| VppProgramID  | 名前 | 説明 |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 |Microsoft |Microsoft の VPP プログラム |
| 00000000-0000-0000-0000-000000000000 |まだ利用できません |既定値、VPP なし |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B |Apple |Apple の VPP プログラム |
