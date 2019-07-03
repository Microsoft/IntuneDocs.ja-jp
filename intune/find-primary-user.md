---
title: Microsoft Intune デバイスのプライマリ ユーザーを確認する。
titleSuffix: ''
description: Intune デバイスのプライマリ ユーザー (ユーザーとデバイスのアフィニティ) を確認します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b6a20ccec2ef0cbaba87637b3c44c2cc2be094ab
ms.sourcegitcommit: b3a1c5b0b24f0e52cf318defe10f3d27a2770009
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2019
ms.locfileid: "67325540"
---
# <a name="find-the-primary-user-of-an-intune-device"></a>Intune デバイスのプライマリ ユーザーを確認する

プライマリ ユーザーは、ユーザーとデバイスのアフィニティとも呼ばれ、各 Intune デバイスのプロパティです。 Intune デバイスには、0 人または 1 人のプライマリ ユーザーを割り当てることができます。 プライマリ ユーザーが割り当てられていない場合、そのデバイスは "共有デバイス" と呼ばれます。

## <a name="how-to-find-a-devices-primary-user"></a>デバイスのプライマリ ユーザーを確認する方法

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイス]** を選択し、デバイスを選択します。
3. **[概要]** ページで、 **[詳細]** を選択すると、プライマリ ユーザーが一覧表示されます。

## <a name="what-is-the-primary-user"></a>プライマリ ユーザーとは
プライマリ ユーザー プロパティは、ライセンスが付与された Intune ユーザーをデバイスにマップするために以下で使用されます。
- ポータル サイト アプリ
- エンドユーザー Web サイト
- Azure portal のトラブルシューティング ページなどの IT プロフェッショナルのエクスペリエンス。 これらのページでは、プライマリ ユーザーを使用してユーザー アカウントをデバイスにマップします。    

### <a name="company-portal-app"></a>ポータル サイト アプリ
ポータル サイト アプリは、ポータル サイトにサインインしたユーザー アカウントがそのデバイスのプライマリ ユーザーであることを想定します。 他のユーザーがプライマリ ユーザーとして割り当てられている場合は、ポータル サイトに次の警告が表示されます。

"This device is already assigned to someone in your organization. (このデバイスは組織内の他のユーザーに既に割り当てられています。) Contact company support about becoming the primary device user. (プライマリ デバイス ユーザーになるには、会社のサポートにお問い合わせください。) You can continue to use Company Portal but functionality will be limited. (ポータル サイトは引き続き使用できますが、機能は制限されます。)"

Intune デバイスにプライマリ ユーザーが割り当てられていない場合、ポータル サイト アプリでは共有デバイスとして検出されます。 共有デバイスは、デバイス タイルに表示される "共有" ラベルで視覚的に特定できます。 このモードでも、ポータル サイトを使用して、使用できるアプリを要求してインストールすることができます。 ただし、セルフサービスのアクション (リセット/名前変更/インベントリからの削除) は利用できません。  

共有デバイスのポータル サイトに表示するには、使用できるアプリをユーザー グループに割り当てる必要があります。 これらは、IT 管理者によるアプリの構成方法に応じて、システム コンテキストまたはユーザー コンテキストでインストールされます。 アプリ コンテキストの詳細については、「[Windows 10 デバイスでのアプリのインストール](apps-windows-10-app-deploy.md#installing-apps-on-windows-10-devices)」を参照してください。 この機能を使用するには、ポータル サイト バージョン 10.3.4651.0 以降が必要です。


## <a name="who-is-assigned-as-the-primary-user"></a>プライマリ ユーザーとして割り当てられるユーザー
Intune では、登録時または登録直後に、プライマリ ユーザーがデバイスに自動的に追加されます。 登録方法によって、プライマリ ユーザーがデバイスに追加されるタイミングが決まります。

| プラットフォーム | 登録方法 | 割り当てられるプライマリ ユーザー | プライマリ ユーザーが割り当てられる |
| ---- | ---- | ---- | ---- |
| Windows | 職場または学校を追加する (ユーザー主導) | 登録ユーザー | 登録時 |   
| Windows | モダン アプリのサインイン (ユーザー主導) | 登録ユーザー | 登録時 | 
| Windows | MDM のみへの登録 (ユーザー主導) | 登録ユーザー | 登録時 | 
| Windows | Azure AD 参加 (すぐに利用できるエクスペリエンス) | 登録ユーザー | 登録時 | 
| Windows | Azure AD の参加 (Autopilot のすぐに利用できるエクスペリエンス) | 登録ユーザー | 登録時 | 
| Windows | MDM のみへの登録 | 登録ユーザー | 登録時 | 
| Windows | ハイブリッド AADJ + 自動登録 GPO | サインインする最初のユーザー | 最初のユーザーがサインインするとき | 
| Windows | 共同管理 | サインインする最初のユーザー | 最初のユーザーがサインインするとき | 
| Windows | Azure AD 参加 (一括登録トークン) | なし | 適用できません | 
| Windows | Azure AD 参加 (Autopilot の自己展開モード) | なし | 適用できません | 
| クロスプラット フォーム | ポータル サイト アプリへのユーザー主導の登録 | 登録ユーザー | 登録時 |
| クロスプラット フォーム | デバイス登録マネージャー (DEM) | DEM ユーザーの登録 | 登録時 |
| iOS、macOS | Apple Automated Device Enrollment (ユーザー アフィニティありの DEP) | 登録ユーザー | 登録時 |
| iOS、macOS | Apple Automated Device Enrollment (ユーザー アフィニティなしの DEP) | なし | 適用できません |
| Android | 会社所有の専用の Android デバイス | なし | 適用できません |

## <a name="primary-user-and-azure-ad-device-owner"></a>プライマリ ユーザーと Azure AD デバイス所有者
場合によっては、Intune プライマリ ユーザーが Azure AD デバイスの **[所有者]** プロパティとは異なる場合があります ( **[デバイス]**  >  **[Azure AD デバイス]** で表示できます)。 Azure AD デバイスの所有者は、デバイスの Azure Active Directory への登録時に追加されます。

## <a name="next-steps"></a>次の手順
[Intune デバイスを管理します。](device-management.md)
