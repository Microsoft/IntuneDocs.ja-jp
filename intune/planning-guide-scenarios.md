---
title: ユース ケース シナリオを特定する
titleSuffix: Microsoft Intune
description: この記事は、Microsoft Intune クラウドのみの実装に関する Intune ユース ケース シナリオとサブ ユース ケース シナリオの特定について説明します。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69a4ee29a6d35623d6269a94a9c1b4fc7a1f956f
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567557"
---
# <a name="identify-mobile-device-management-use-case-scenarios"></a>モバイル デバイス管理のユース ケース シナリオを特定する

ユース ケース シナリオの特定は、正常な Intune 展開のための計画プロセスにおいて重要な部分です。 ユース ケース シナリオが役立つのは、ユーザーの種類またはロール、ユーザーのデバイス (たとえば、会社または個人) の所有権によって、ユーザーを管理しやすいグループに分割できるからです。

組織が Intune ユース ケース シナリオ、組織グループ、そして各ユース ケースに関連付けられるモバイル デバイス プラットフォームなどを特定するのに役立つ、いくつかの例について説明します。

## <a name="device-ownership"></a>デバイスの所有権
お客様の展開向けの主なユース ケース シナリオを特定するには、組織の Intune 展開の目標と目的を確認することから始めます。 Intune 展開計画の範囲内で、以下の質問にお答えください。

-   会社所有のデバイスをサポートする予定ですか。

-   個人所有のデバイス (BYOD) をサポートする予定ですか。

これらの質問はどちらか 1 つを選択する類のものではありません。 両方の形式のデバイス所有権をサポートして組織の目標を果たす必要があると気付く場合があります。 サブ ユース ケースは、異なるデバイス管理ポリシーを適用する場所を明らかにするのに役立ちます。

### <a name="user-type-or-device-role"></a>ユーザーの種類またはデバイスのロール

各ユース ケース シナリオにサブ ユース ケースが含まれるかどうかを判断します。 たとえば、組織が会社のユース ケース シナリオをサポートするための要件を特定していて、そのシナリオに、以下のようなユーザーの種類またはデバイスのロールに基づいた追加のサブ ユース ケースが含まれている場合があります。

-   インフォメーション ワーカー

-   役員

-   キオスク

ユース ケース シナリオとサブ ユース ケース シナリオのいくつかの例を次に示します。

| **ユース ケース** | **サブ ユース ケース** |
|:---:|:---:|
| 企業 | インフォメーション ワーカー |              
| 企業 | 役員 |           
| 企業 | キオスク |
| BYOD | インフォメーション ワーカー |           
| BYOD | 役員 |

[上記の表のテンプレートをダウンロード](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)して、お客様の組織のユース ケース シナリオとサブ ユース ケース シナリオを入力できます。

## <a name="organizational-groups-for-your-scenarios"></a>シナリオ用の組織のグループ

次に、各ユース ケースとサブ ユース ケース シナリオに関連付けられている組織グループを特定する必要があります。 次に例を示します。

| **ユース ケース** | **サブ ユース ケース** | **組織グループ** |
|:---:|:---:|:---:|
| 企業 | インフォメーション ワーカー | 人事、財務 |               
| 企業 | 役員 | 人事、財務 |            
| 企業 | キオスク | 小売 |
| BYOD | インフォメーション ワーカー | マーケティング、営業 |            
| BYOD | 役員 | マーケティング、営業 |


## <a name="mobile-device-platforms-for-your-scenarios"></a>シナリオに合ったモバイル デバイス プラットフォーム

次に、各ユース ケース シナリオに関連付けられているモバイル デバイス プラットフォームを特定します。 候補が複数存在する場合があります。

たとえば、会社のユース ケース シナリオでは、iOS と Android Samsung KNOX デバイスのプラットフォームをサポートする場合があります。 BYOD ポリシーに、Android (Samsung KNOX 以外) と Windows 10 Mobile のようなモバイル デバイス プラットフォームの追加に関するサポートが含まれる場合があります。 前述の例に基づき、モバイル デバイス プラットフォームと各ユース ケース シナリオを関連付けています。

| **ユース ケース** | **サブ ユース ケース** | **グループ** | **デバイス プラットフォーム** |   
|:---:|:---:|:---:|:---:|
| 企業 | インフォメーション ワーカー | 人事、財務 | iOS |                                                           
| 企業 | 役員 | 人事、財務 | iOS |                                                           
| 企業 | キオスク | 小売 | Android |
| BYOD | インフォメーション ワーカー | マーケティング、営業 | iOS |                                                           
| BYOD | 役員 | マーケティング、営業 | iOS |

## <a name="next-steps"></a>次の手順

次のセクションでは、[各ユース ケース シナリオの Intune 要件を特定する方法](planning-guide-requirements.md)についてのガイダンスを提供します。
