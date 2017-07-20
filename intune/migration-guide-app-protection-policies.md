---
title: "Intune 移行中にアプリ保護ポリシーを構成する"
description: "この記事では、Intune 移行中にアプリ保護ポリシーを設定するために必要な手順について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: c58ce51731b476cfca71851430297aff3edc5cd6
ms.sourcegitcommit: 388c5f59bc992375ac63968fd7330af5d84a1348
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2017
---
# <a name="configure-app-protection-policies-optional"></a>アプリ保護ポリシーを構成する (省略可能)


アプリ保護ポリシーでは次のことができます。
* アプリの暗号化
* アプリにアクセスするときの PIN の定義
* 脱獄またはルート化されたデバイスでのアプリの実行のブロック、および他の多くの保護

携帯電話を紛失したり盗難に遭ったりした場合は、個人データは保持したまま会社のデータに対して選択的にリモート ワイプを実行することができます。

アプリ保護ポリシーではアプリ レベルでセキュリティを適用し、デバイスの登録を必要としません。 Intune 登録の有無に関係なく、アプリ保護ポリシーをデバイスで使用できます。 また、サードパーティの MDM プロバイダーに登録されたデバイスにも適用できます。

## <a name="app-protection-policies-with-lob-apps"></a>LOB アプリでのアプリ保護ポリシー

[IOS](https://www.microsoft.com/download/details.aspx?id=45218&751be11f-ede8-5a0c-058c-2ee190a24fa6=True) および [Android](https://www.microsoft.com/download/details.aspx?id=47267) プラットフォーム用の [Microsoft Intune App SDK](app-sdk-get-started.md) や Microsoft Intune アプリ ラッピング ツールを利用して、基幹業務 (LOB) アプリに対してモバイル アプリ保護ポリシーを拡張することもできます。

## <a name="how-do-app-protection-policies-help-during-migration"></a>アプリ保護ポリシーは移行中にどのように役立つか

移行では、デバイスを以前の MDM プロバイダーから削除して、Intune に登録する必要があります。 この計画を立てて、エンド ユーザーに以前の MDM プロバイダーの利用をやめて、速やかに Intune に登録するよう働きかけます。 移行中は一部のユーザーの登録プロセスの完了が遅れて、デバイスがどちらの MDM プロバイダーでも管理されないことがあります。

この期間に会社のリソースへのアクセスを引き続き許可すると、デバイスの盗難や会社のデータの損失に対する脆弱性が高まります。 また、会社のリソースへのアクセスをブロックすると、ユーザーの生産性が低下する可能性があります。

Intune では移行中の企業データの保護が提供されるため、デバイス レベルの管理が行われない期間も、引き続き会社のデータをセキュリティで保護することができます。

以前の MDM プロバイダーで条件付きアクセスを無効にしても、Intune に登録すればユーザーの生産性を維持することができます。

## <a name="task-list-for-app-protection-policies"></a>アプリ保護ポリシーのタスク一覧

1. [アプリ保護ポリシーを作成する](app-protection-policies.md#create-an-app-protection-policy)
2. [ポリシーの展開](app-protection-policies.md#deploy-a-policy-to-users)


## <a name="next-steps"></a>次のステップ

[特殊な移行に関する考慮事項](migration-guide-considerations.md)
