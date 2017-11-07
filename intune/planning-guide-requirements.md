---
title: "ユース ケース シナリオの要件の決定"
description: "この記事は、Microsoft Intune クラウドのみの実装に関する Intune ユース ケース シナリオとサブ ユース ケース シナリオの要件の決定について説明します。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 65a1fb8fb41fa8d9f3e707c73bf752a997a8a1a1
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2017
---
# <a name="determine-use-case-scenario-requirements"></a>ユース ケース シナリオの要件の決定

このセクションでは、各ユース ケース シナリオ内の組織グループごとに要件を決定します。 このプロセスは、アーキテクチャとデザイン、オンボード、ロールアウトなど、その他の Intune 展開の計画を準備するのに役立ちます。 また、Intune 展開プロジェクトに関連する潜在的なギャップと課題の特定にも役立ちます。

ユース ケースとサブ ユース ケースの各シナリオ、関連する組織グループとモバイル デバイス プラットフォームについて、異なる要件を持つことになる可能性があります。 たとえば、企業のユース ケース シナリオの要件では、6 文字の PIN や無効なクラウド バックアップといった、より制限の厳しいデバイス設定で Intune にデバイスを登録する必要がある場合があります。 "Bring Your Own Device"(BYOD) ユース ケース シナリオはより制限が少なく、4 文字の PIN とクラウド バックアップを許可する可能性があります。

また、企業のユース ケース シナリオが適した組織グループが複数あり、それぞれが異なる要件セット (たとえば、PIN 設定、Wi-Fi または VPN プロファイル、展開されるアプリ) を持つという場合もあります。 要件はまた、モバイル デバイス プラットフォームの機能 (たとえば、指紋認証、電子メール プロファイル) によって判断できる場合があります。

組織のユース ケースの要件の例を次に示します。ここでは、各ユース ケースとサブ ユース ケースのシナリオ、組織グループ、モバイル デバイス プラットフォームに対する異なる要件セットを示します。 次の表を使用して、組織のユース ケースの要件を入力することもできます。

| **ユース ケース** | **サブ ユース ケース** | **グループ** | **デバイス プラットフォーム** | **Requirements** |
|:---:|:---:|:---:|:---:|:---:|
| 企業 | インフォメーション ワーカー | 人事、財務 | iOS | 電子メールのセキュリティ保護、デバイスの設定、プロファイル、アプリ |                                                          
| 企業 | 役員 | 人事、財務 | iOS | 電子メールのセキュリティ保護、デバイスの設定、プロファイル、アプリ |                                                         
| 企業 | キオスク | 小売 | Android | デバイスの設定、プロファイル、アプリ |
| BYOD | インフォメーション ワーカー | マーケティング、営業 | iOS | 電子メールのセキュリティ保護、デバイスの設定、プロファイル、アプリ |                                                         
| BYOD | 役員 | マーケティング、営業 | iOS | 電子メールのセキュリティ保護、デバイスの設定、プロファイル、アプリ |

[上記の表のテンプレートをダウンロード](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)して、お客様の組織のユース ケースとサブ ユース ケースの要件を入力できます。


## <a name="examples-of-requirements"></a>要件の例

"要件" 列に使用できる追加の例を次に示します。

- **電子メールのセキュリティ保護**
    - Exchange Online / On-Premises の条件付きアクセス
    - Outlook アプリの保護ポリシー

- **デバイスの設定**
    - 4 桁、6 桁の PIN 設定
    - クラウド バックアップの制限

- **プロファイル**
    - Wi-Fi
    - VPN
    - 電子メール (Windows 10 Mobile)

- **アプリ**
    - アプリの保護ポリシー付きの Office 365
    - アプリの保護ポリシー付きの基幹業務 (LOB)

## <a name="next-steps"></a>次のステップ

次のセクションでは、[Intune ロールアウト計画を作成する方法](planning-guide-rollout-plan.md)についてのガイダンスを提供します。
