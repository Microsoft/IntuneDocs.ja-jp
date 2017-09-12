---
title: "Intune のデバイス コンプライアンス ポリシー"
titleSuffix: Azure portal
description: "このトピックでは、Microsoft Intune でのデバイス コンプライアンスについて説明します\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a916fa0d-890d-4efb-941c-7c3c05f8fe7c
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: aa78383233950e342c5ab0f83095bba3c8fda1f9
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="get-started-with-intune-device-compliance-policies"></a>Intune のデバイス コンプライアンス ポリシーの概要

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="what-is-device-compliance-in-intune"></a>Intune でのデバイス コンプライアンスとは

Intune のデバイス コンプライアンス ポリシーは、デバイスが Intune によって "準拠している" と見なされるために遵守する必要がある規則および設定を定義します。

この規則には次のようなものがあります。

- パスワードを使用したデバイスへのアクセス

- 暗号化

- デバイスが脱獄またはルート化されているかどうか

- 必要な最小 OS バージョン

- 許可される最大 OS バージョン

- デバイスが Mobile Threat Defense レベル以下であることが必要

デバイス コンプライアンス ポリシーを使用して、デバイス コンプライアンスの状態を監視することもできます。

### <a name="device-compliance-requirements"></a>デバイス コンプライアンスの要件

コンプライアンス要件とは、基本的にはデバイスの PIN または暗号化を要求するようなルールであり、コンプライアンス ポリシーに対して必要か不要かを指定できます。

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be non-compliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

##  <a name="pre-requisites"></a>前提条件

Intune でデバイス コンプライアンス ポリシーを使用するには、次のサブスクリプションが必要です。

- Intune EMS

- Azure AD プレミアム

###  <a name="supported-platforms"></a>サポートされているプラットフォーム:

-   Android

-   iOS

-   macOS (プレビュー)

-   Windows 8.1

-   Windows Phone 8。1

-   Windows 10

> [!IMPORTANT]
> デバイス コンプライアンスの状態をレポートするには、Intune にデバイスを登録する必要があります。

## <a name="how-intune-device-compliance-policies-work-with-azure-ad"></a>Azure AD で Intune のデバイス コンプライアンス ポリシーを操作する方法

デバイスが Intune に登録されると、Azure AD の登録プロセスが発生し、デバイスの属性が Azure AD への詳細な情報で更新されます。 キーのデバイス情報の 1 つは、デバイス コンプライアンスの状態で、電子メールと他の企業リソースへのアクセスをブロックまたは許可するための条件付きアクセス ポリシーによって使用されます。

- 詳細については、[Azure Active Directory の登録プロセス](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-overview)に関するページを参照してください。

##  <a name="ways-to-use-device-compliance-policies"></a>デバイス コンプライアンス ポリシーを使用する方法

### <a name="with-conditional-access"></a>条件付きアクセスあり
コンプライアンス ポリシーは、条件付きアクセスと一緒に使用することで、1 つ以上のデバイス コンプライアンス ポリシー ルールに準拠しているデバイスにのみ電子メールや他の企業リソースへのアクセスを許可することができます。

### <a name="without-conditional-access"></a>条件付きアクセスなし
条件付きアクセスと独立してデバイス コンプライアンス ポリシーを使用することもできます。 コンプライアンス ポリシーを単独で使用した場合、対象のデバイスが評価され、コンプライアンス ステータスを含めて報告されます。 たとえば、暗号化されていないデバイスの数や脱獄またはルート化されたデバイスに関するレポートを取得できます。 ただし、コンプライアンス ポリシーを単独で使用した場合、会社のリソースへのアクセス制限が設定されません。

コンプライアンス ポリシーはユーザーに展開して使用します。 コンプライアンス ポリシーがユーザーに展開されると、ユーザーのデバイスのコンプライアンスがチェックされます。 ポリシーの展開後にモバイル デバイスがポリシーを取得できるようになるまでにかかる時間については、デバイスでの設定と機能の管理に関するページを参照してください。

##  <a name="using-device-compliance-policies-in-the-intune-classic-portal-vs-azure-portal"></a>Intune のクラシック ポータルとAzure Portal を比較してデバイス コンプライアンス ポリシーを使用する

Azure Portal での新しいデバイス コンプライアンス ポリシーのワーク フローへの移行に役立つ主な相違点に注意してください。

- Azure Portal では、コンプライアンス ポリシーがサポート対象のプラットフォームごとに個別に作成されます。
- Intune クラシック ポータルでは、すべてのサポート対象プラットフォームで 1 つのデバイス コンプライアンス ポリシーが共有されていました。

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migrate-device-compliance-policies-from-the-intune-classic-portal-to-the-azure-portal"></a>デバイス コンプライアンス ポリシーを Intune クラシック ポータルから Azure Portal に移行する

[Intune クラシック ポータル](https://manage.microsoft.com)で作成したデバイス コンプライアンス ポリシーは、新しい [Intune Azure Portal](https://portal.azure.com) では表示されません。 ただし、これらのポリシーは引き続きユーザーを対象とし、Intune クラシック ポータルで管理できます。

Azure Portal の新しいデバイス コンプライアンスに関連した機能を活用するには、Azure Portal で新しいデバイス コンプライアンス ポリシーを作成する必要があります。 Intune クラシック ポータルのデバイス コンプライアンス ポリシーが既に割り当てられているユーザーに Azure Portal の新しいデバイス コンプライアンス ポリシーを割り当てると、Intune クラシック ポータルで作成されたポリシーよりも Intune Azure Portal のデバイス コンプライアンス ポリシーが優先されます。

##  <a name="next-steps"></a>次のステップ

以下のプラットフォームに対してデバイス コンプライアンス ポリシーを作成します。

- [Android](compliance-policy-create-android.md)
- [Android for Work](compliance-policy-create-android-for-work.md)
- [iOS](compliance-policy-create-ios.md)
- [macOS](compliance-policy-create-mac-os.md)
- [Windows](compliance-policy-create-windows.md)
