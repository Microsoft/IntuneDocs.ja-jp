---
title: "ユーザー デバイスの関連付け | Microsoft Docs"
description: "Intune データ ウェアハウス API のエンティティ コレクションのユーザー デバイスの関連付けカテゴリに関するリファレンス トピック。"
keywords: "Intune データ ウェアハウス"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 09/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: BCDBABCB-A7B1-42F2-BDD1-D055E33F2239
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 490e29f87c65875a385472e6abe9400363383f9b
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2017
---
# <a name="reference-for-user-device-association-entity"></a>ユーザー デバイスの関連付けエンティティのリファレンス

**ユーザー デバイスの関連付け**カテゴリには、組織でデバイスの関連付けを定義するために使用される**ユーザー デバイスの関連付け**エンティティが含まれています。

**ユーザー デバイスの関連付け**

**ユーザー デバイスの関連付け**エンティティは、組織でデバイスの関連付けの定義を表します。

| 名前               | 説明                                                                                      | 例                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | データ ウェアハウス内のユーザーを示す一意識別子 - 代理キー。                             | 123                    |
| DeviceKey          | データ ウェアハウス内のデバイスを示す一意識別子。                                           | 123                    |
| CreatedDateTimeUTC | ユーザー デバイスの関連付けが作成されたときの日時 (UTC)。                               | 11/23/2016 12:00:00 AM |
| IsDeleted          | ユーザーがそのデバイスを登録解除し、その関連付けが最新でなくなったことを示します。 | True                   |
| EndedDateTimeUTC   | IsDeleted が **True** に変更されたときの日時 (UTC)。                                         | 06/23/2017 12:00:00 AM |