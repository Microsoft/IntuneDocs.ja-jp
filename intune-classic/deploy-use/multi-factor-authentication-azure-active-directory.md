---
title: Intune へのデバイスの登録での多要素認証
description: デバイス登録で Azure AD の多要素認証を要求する方法。
keywords: ''
author: dougeby
ms.author: angrobe
manager: angerobe
ms.date: 02/17/2017
ms.topic: article
ms.prod: ''
ms.service: ''
ms.technology: ''
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: e8572834aed14ee08b3ba3c74bc7504193397ef5
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="multi-factor-authentication-for-intune-device-enrollments"></a>Intune へのデバイスの登録での多要素認証

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune には、デバイス登録用に Azure AD の多要素認証 (MFA) 機能が統合されていて、会社のリソースのセキュリティ保護に利用できます。

MFA は、次の確認方法のうち 2 つ以上を必須にすることで機能します。 

- ユーザーが知っている情報 (通常はパスワードまたは PIN)。
- ユーザーの所持品 (電話など、容易には複製できない、信頼済みのデバイス)。
- ユーザー自身の特性 (生体認証)。

MFA は、iOS、Android、Windows 8.1 以上、または Windows Phone 8.1 以上のデバイスでサポートされています。

> [!NOTE]
> 以前のバージョンの Configuration Manager (リリース 1610 より前) では、Configuration Manager 管理コンソールに MFA の設定が表示されますが、 Configuration Manager 管理コンソールで MFA を構成しようとしないでください。MFA は機能しません。 MFA はこのトピックの説明に従って構成してください。

### <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>デバイス登録時に多要素認証を要求するように Intune を構成する
デバイスの登録時に MFA を要求するには、次の手順に従います。

1. 管理者資格情報で [Microsoft Azure ポータル](https://manage.windowsazure.com)にサインインします。
2. テナントを選択します。
2. **[アプリケーション]** タブを選択します。Azure AD のセキュリティ機能を構成できるサービスの一覧が表示されます。
3. **[Microsoft Intune enrollment (Microsoft Intune 登録)]** を選択します。
4. **[構成]** を選択します。 
5. **[多要素認証と場所ベースのアクセス規則]** では、次の操作をすることができます。
    
    -  アクセス規則の有効化
    -  すべてのユーザーまたは特定の Azure セキュリティ グループのどちらに規則を適用するか選択します。
    -  すべてのデバイスの登録では、多要素認証を要求します。
    -  デバイスが動作していないときの登録では、多要素認証を要求します。
    -  **[Block access to corporate resources (会社のリソースへのアクセスをブロックする)]** を選択して、デバイスが企業ネットワークに接続されていないときはデバイスを登録できないようにします。 
4. **社内ネットワークの場所の定義/編集**へのリンクをクリックして、デバイス登録のネットワーク接続要件を構成することもできます。

> [!IMPORTANT]
> 
> [Microsoft Intune enrollment (Microsoft Intune 登録)] の **[デバイス ベースのアクセス規則]** は構成しないでください。
