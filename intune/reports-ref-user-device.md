---
title: "ユーザー デバイスの関連付け - Intune データ ウェアハウス | Microsoft Docs"
description: "Intune のデータ ウェアハウス API の変更一覧。"
keywords: "Intune データ ウェアハウス"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4c47455b0139f7451796257a77859cbd9899a7dd
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2017
---
# <a name="user-device-association"></a>ユーザー デバイスの関連付け

**UserDeviceAssociation** エンティティには、組織内のユーザー デバイスの関連付けが含まれています。

| 名前               | 説明                                                                                      | 例                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | データ ウェアハウス内のユーザーを示す一意識別子 (代理キー)。                              | 123                    |
| DeviceKey          | データ ウェアハウス内のデバイスを示す一意識別子。                                            | 123                    |
| CreatedDateTimeUTC | ユーザー デバイスの関連付けが作成されたときの日時。 UTC 形式を使用します。                                | 11/23/2016 12:00:00 AM |
| IsDeleted          | ユーザーがそのデバイスを登録解除し、その関連付けが最新でなくなったことを示します。 | 真/偽             |
| EndedDateTimeUTC   | IsDeleted が **True** に変更されたときの日時 (UTC)。                                              | 06/23/2017 12:00:00 AM |
