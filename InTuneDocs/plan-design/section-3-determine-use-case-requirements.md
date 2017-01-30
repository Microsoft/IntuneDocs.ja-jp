---
title: "Intune ユース ケース シナリオの要件を決定する | Microsoft Docs"
description: "この記事は、Microsoft Intune のクラウドのみの実装に対する Intune ユース ケース シナリオ、およびサブ ユース ケース シナリオの要件を決定するために役立ちます。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f807d6e4b20b98ecf622d1ebdd9db33b132a2e6a
ms.openlocfilehash: 91b25fe35c6a1f8a554d543ca005cc3b482f22d7


---

# <a name="determine-intune-use-case-scenario-requirements"></a>Intune ユース ケース シナリオの要件を決定する

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

このセクションでは、各ユース ケース シナリオ内の組織グループごとに要件を決定します。 このプロセスを行うと、アーキテクチャとデザイン、オンボード、およびロールアウトなど、その他の Intune 展開の計画領域をしっかりと準備するのに役立ちます。 また、潜在的なギャップ、および Intune 展開プロジェクトに関連する課題の特定にも役立ちます。

各ユース ケース/サブ ユース ケースのシナリオ、および関連する組織グループとモバイル デバイス プラットフォームに対して、異なる要件のセットがある場合があります。 たとえば、企業のユース ケース シナリオの要件では、制限の少ない設定 (PIN 4 桁、クラウド バックアップの許可など) を必要とする "Bring your own device" (BYOD) のユース ケース シナリオに比べ、制限の厳しいデバイス設定のセット (PIN 6 桁、クラウド バックアップの無効化など) を使用してデバイスを Intune に登録する必要がある場合があります。

また、異なる要件のセット (PIN の設定、Wi-Fi または VPN プロファイル、展開されたアプリなど) がある企業のユース ケース シナリオ向けの組織グループがある場合もあります。 さらに、お客様の要件は、モバイル デバイス プラットフォームの機能 (指紋認証、電子メール プロファイルなど) によって判断できる場合があります。

組織のユース ケースの要件の例を次に示します。ここでは、各ユース ケース/サブ ユース ケースのシナリオ、組織グループおよびモバイル デバイス プラットフォームに対する異なる要件のセットを示します。 次の表を使用して、組織のユース ケースの要件を入力することもできます。

| **ユース ケース** | **サブ ユース ケース** | **グループ** | **デバイス OS プラットフォーム** | **Requirements** |
|:---:|:---:|:---:|:---:|:---:|
| 企業 | インフォメーション ワーカー | 人事、財務 | iOS | 電子メールのセキュリティ保護、デバイスの設定、プロファイル、アプリ |                                                          
| 企業 | 役員 | 人事、財務 | iOS | 電子メールのセキュリティ保護、デバイスの設定、プロファイル、アプリ |                                                         
| 企業 | キオスク | 小売 | Android | デバイスの設定、プロファイル、アプリ |
| BYOD | インフォメーション ワーカー | マーケティング、営業 | iOS | 電子メールのセキュリティ保護、デバイスの設定、プロファイル、アプリ |                                                         
| BYOD | 役員 | マーケティング、営業 | iOS | 電子メールのセキュリティ保護、デバイスの設定、プロファイル、アプリ |

## <a name="examples-of-requirements"></a>要件の例

上記の表で参照される"要件" 列に使用できる追加の例を次に示します。

- **電子メールのセキュリティ保護**
    - Exchange Online / On-Premises の条件付きアクセス
    - Outlook アプリの保護ポリシー
<br></br>
- **デバイスの設定**
    - 4 桁、6 桁の PIN 設定
    - クラウド バックアップの制限
<br></br>
- **プロファイル**
    - Wi-Fi
    - VPN
    - 電子メール (Windows 10 Mobile)
<br></br>
- **アプリ**
    - アプリの保護ポリシー付きの Office 365
    - アプリの保護ポリシー付きの基幹業務 (LOB)

## <a name="next-section"></a>次のセクション

次のセクションでは、[Intune ロールアウト計画を作成する方法](section-4-develop-a-rollout-plan.md)についてのガイダンスを提供します。



<!--HONumber=Dec16_HO5-->


