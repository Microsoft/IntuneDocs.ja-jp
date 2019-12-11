---
title: IntuneManagementExtension エンティティ
titleSuffix: Microsoft Intune
description: Intune データ ウェアハウス API にあるエンティティ コレクションの IntuneManagementExtension エンティティ カテゴリのための参照トピック。
keywords: Intune データ ウェアハウス
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: ae99e747f9c0540418c15f24fbe0c27c585f869c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72490307"
---
# <a name="reference-for-intune-management-extensions"></a>Intune の管理拡張のリファレンス

**intuneManagementExtensions** カテゴリには、次のような情報を追跡するモバイル デバイスのエンティティが含まれています。

- IntuneManagementExtension のバージョン
- IntuneManagementExtension のインストール状態

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions

**intuneManagementExtensionVersion** エンティティには、intuneManagementExtensions で使用されるすべてのバージョンがリストされています。

| プロパティ  | 説明 | 例 |
|---------|------------|--------|
| extensionVersionKey |intuneManagementExtensions バージョンの一意識別子。 | 1 |
| extensionVersion |4 桁のバージョン番号。 |1.0.2.0 |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates

**intuneManagementExtensionHealthState** には、intuneManagementExtensions が取り得るすべての正常性状態がリストされています。

| プロパティ  | 説明 | 例 |
|---------|------------|--------|
| extensionStateKey |ヘルス状態の一意識別子。 | 2 |
| extensionState |IntuneManagementExtension のヘルス状態。 | Healthy |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions

**intuneManagementExtension** には、1 日あたりの各 Windows 10 デバイスでの IntuneManagementExtensions の正常性がリストされています。
過去 60 日間のデータが保持されます。 


|      プロパティ       |                         説明                         | 例 |
|---------------------|-------------------------------------------------------------|---------|
|       dateKey       |               日付の一意識別子。                |   123   |
|      tenantKey      |              テナントの一意識別子。               |   456   |
|      deviceKey      |              デバイスの一意識別子。               |   789   |
| extensionVersionKey | intuneManagementExtension バージョンの一意識別子。 |    1    |
|  extensionStateKey  |             ヘルス状態の一意識別子。              |    2    |

