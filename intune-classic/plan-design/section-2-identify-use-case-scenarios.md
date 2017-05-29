---
title: "Intune ユース ケース シナリオの特定 | Microsoft Docs"
description: "この記事は、Microsoft Intune クラウドのみの実装向けに Intune ユース ケース シナリオ、およびサブ ユース ケース シナリオを特定するために役立ちます。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 031820d505e0e9cb007e47a5397934d0e505aed4
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="identify-intune-use-case-scenarios"></a>Intune ユース ケース シナリオの特定

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

モバイル デバイス管理のユース ケース シナリオでは、ユーザーの種類またはロールおよびデバイスの所有権 (会社、個人など) について説明します。 ユーザー ケース シナリオは、ユーザーを管理しやすいグループに分割することができるため便利です。 ユース ケース シナリオを特定することは、正常な Intune 展開の計画プロセスの重要な部分です。

組織が Intune ユース ケース シナリオ、および組織グループ、各ユース ケースに関連付けられているモバイル デバイス プラットフォームを特定するために役立ついくつかの例について説明します。

## <a name="use-case-scenarios"></a>ユース ケース シナリオ

お客様の展開向けのメイン ユース ケース シナリオを特定するために役立てるには、組織の Intune 展開の目標と目的を参照することから始めることができます。 Intune 展開計画の範囲内で、次の質問に答える必要があります。

-   会社所有のデバイスをサポートする予定ですか。

-   個人所有のデバイス (BYOD) をサポートする予定ですか。

### <a name="sub-use-case-scenarios"></a>サブ ユース ケース シナリオ

メイン ユース ケース シナリオを特定した後に、各ユース ケース シナリオにサブ ユース ケースも含めるかどうかを判断する必要があります。 たとえば、組織は、追加のサブ ユース ケースを含む企業のユース ケース シナリオをサポートするための要件を特定している場合があります。

-   インフォメーション ワーカー

-   役員

-   キオスク

ユース ケース シナリオとサブ ユース ケース シナリオのいくつかの例を次に示します。 次の表を利用し、お客様の組織のユース ケース シナリオ、およびサブ ユース ケース シナリオを入力できます。

| **ユース ケース** | **サブ ユース ケース** |
|:---:|:---:|
| 企業 | インフォメーション ワーカー |              
| 企業 | 役員 |           
| 企業 | キオスク |
| BYOD | インフォメーション ワーカー |           
| BYOD | 役員 |

## <a name="identify-organizational-groups-associated-with-use-case-scenarios"></a>ユース ケース シナリオに関連付けられている組織グループを特定する

次に、各ユース ケースおよびサブ ユース ケース シナリオに関連付けられている組織グループを特定する必要があります。 組織の情報を入力するテンプレートとして使用できる、ユース ケース シナリオとサブ ユース ケース シナリオに関連付けられている組織グループのいくつかの例を次に示します。

| **ユース ケース** | **サブ ユース ケース** | **組織グループ** |
|:---:|:---:|:---:|
| 企業 | インフォメーション ワーカー | 人事、財務 |               
| 企業 | 役員 | 人事、財務 |            
| 企業 | キオスク | 小売 |
| BYOD | インフォメーション ワーカー | マーケティング、営業 |            
| BYOD | 役員 | マーケティング、営業 |

## <a name="identify-mobile-device-platforms-for-use-case-scenarios"></a>ユース ケース シナリオのモバイル デバイス プラットフォームを特定する

ここでは、各ユース ケース シナリオに関連付けられているモバイル デバイス プラットフォームを特定します。 たとえば、企業のユース ケース シナリオでは、iOS および Android Samsung KNOX デバイスのプラットフォームをサポートする可能性があり、BYOD ポリシーでは、Android (非 Samsung KNOX) および Windows 10 Mobile のような追加のモバイル デバイス プラットフォームのサポートを含める場合があります。 各ユース ケース シナリオに関連付けられているモバイル デバイス プラットフォームの例を次に示します。 次の表を使用して、ユース ケース シナリオに関連付けられている組織のデバイス プラットフォームを入力することができます。

| **ユース ケース** | **サブ ユース ケース** | **グループ** | **デバイス プラットフォーム** |   
|:---:|:---:|:---:|:---:|
| 企業 | インフォメーション ワーカー | 人事、財務 | iOS |                                                           
| 企業 | 役員 | 人事、財務 | iOS |                                                           
| 企業 | キオスク | 小売 | Android |
| BYOD | インフォメーション ワーカー | マーケティング、営業 | iOS |                                                           
| BYOD | 役員 | マーケティング、営業 | iOS |

## <a name="next-steps"></a>次のステップ

次のセクションでは、[各ユース ケース シナリオの Intune 要件を特定する方法](section-3-determine-use-case-requirements.md)についてのガイダンスを提供します。

