---
title: Microsoft Intune にサインアップまたはサインインする
description: Microsoft Intune サブスクリプションにサインアップする方法、またはサブスクリプションを使用してサインインする方法。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f3ce07a-b718-42a9-bace-f99a8b8abd94
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 22e5c38be9dc5a8a09888651e471f64bf6739c72
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "71238906"
---
# <a name="sign-up-or-sign-in-to-microsoft-intune"></a>Microsoft Intune にサインアップまたはサインインする

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

このトピックでは、システム管理者が Intune アカウントにサインアップする方法を説明します。

Intune にサインアップする前に、Microsoft Online Services アカウント、Enterprise Agreement、または同等のボリューム ライセンス契約が既にあるかどうかを確認してください。 Microsoft ボリューム ライセンス契約や、Office 365 などの他の Microsoft クラウド サービス サブスクリプションには、通常、職場または学校アカウントが含まれます。

既に職場または学校アカウントがある場合は、そのアカウントで**サインイン**し、Intune をサブスクリプションに追加します。 それ以外の場合は、新しいアカウントに**サインアップ**して、組織で Intune を使うことができます。

>[!WARNING]
>新しいアカウントにサインアップした後で、既存の職場または学校アカウントを組み合わせることはできません。

## <a name="how-to-sign-up-for-intune"></a>Intune にサインアップする方法

1. [Intune のサインアップ ページ](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)にアクセスします。

   ![Microsoft Intune 試用版アカウントのサインアップ Web ページのスクリーンショット](./media/account-sign-up-site.png)

2. サインアップ ページで、Intune の新しいサブスクリプションを管理するために、サインアップまたはサインインします。

## <a name="post-sign-up-considerations"></a>サインアップ後の考慮事項
新しいサブスクリプションにサインアップした後、アカウント情報の記載されたメール メッセージが、サインアップ過程で登録したメール アドレスに送信されます。 このメールで、サブスクリプションがアクティブになったことが確認されます。

サインアップ プロセスが完了すると、ユーザーの追加とライセンスの割り当てに使われる Microsoft 365 管理センターが表示されます。 既定の onmicrosoft.com ドメイン名を使ったクラウドベースのアカウントだけがある場合は、この時点でユーザーを追加し、ライセンスを割り当てることができます。 一方、組織の[カスタム ドメイン名](custom-domain-name-configure.md)を使う場合や、オンプレミスの Active Directory から[ユーザー アカウント情報を同期する](users-add.md#sync-active-directory-and-add-users-to-intune)場合は、そのブラウザー ウィンドウを閉じてかまいません。

## <a name="sign-in-to-microsoft-intune"></a>Microsoft Intune にサインインする
Intune にサインアップしたら、[サポートされているブラウザー](supported-devices-browsers.md#intune-supported-web-browsers)がインストールされている任意のデバイスを使用して、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、サービスを管理できます。

既定では、アカウントに Azure AD の次のいずれかのアクセス許可が必要です。
- グローバル管理者
- Intune サービス管理者 (Intune 管理者 とも呼ばれます)

他のアクセス許可を持つユーザーに対してサービスを管理するためのアクセス権を付与するには、[ロールベースのアクセス制御](role-based-access-control.md)に関する記事をご覧ください

### <a name="intune-admin-portal-url"></a>Intune 管理ポータルの URL

Microsoft 365 管理センター: https://devicemanagement.microsoft.com

Intune Azure portal: https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade

Intune for Education: https://intuneeducation.portal.azure.com

Intune クラシック ポータル: https://manage.microsoft.com Intune クラシック ポータルは、Intune PC ソフトウェア クライアントで登録されたデバイスの管理にのみ使用されます

### <a name="urls-for-intune-services-provided-by-office-365"></a>Office 365 によって提供される Intune サービスの URL

Microsoft 365 Business: https://portal.microsoft.com/adminportal

Office 365 モバイル デバイス管理: https://portal.office.com/adminportal/home#/MifoDevices

## <a name="see-also"></a>関連項目
[Office 365、Azure、または Intune にサインインできない](https://support.microsoft.com/help/2412085)
