---
title: "デバイスのポリシー準拠"
titleSuffix: Intune on Azure
description: "このトピックでは、Microsoft Intune でのデバイス コンプライアンスについて説明します&quot;"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a916fa0d-890d-4efb-941c-7c3c05f8fe7c
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: a747d577a28433635883ad6c4fe4c858e75902d0
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="what-is-device-compliance-in-intune"></a>Intune でのデバイス コンプライアンスとは

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune のデバイス コンプライアンス ポリシーは、デバイスが Intune および EMS 条件付きアクセス ポリシーによって "準拠している" と見なされるために遵守する必要がある規則および設定を定義します。 デバイス コンプライアンス ポリシーを使用して、デバイスのコンプライアンスに関する問題を監視および修復することもできます。 

この規則には次のようなものがあります。

- パスワードを使用したデバイスへのアクセス
- 暗号化
- デバイスが脱獄またはルート化されているかどうか
- 必要な最小 OS バージョン
- 許可される最大 OS バージョン
- デバイスが Mobile Threat Defense レベル以下であることが必要

<!---##  Concepts
Following are some terms and concepts that are useful to understanding how to use compliance policies.

### Device compliance requirements
Compliance requirements are essentially rules like requiring a device PIN or encryption that you can specify as required or not required for a compliance policy.

### Actions for noncompliance

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

##  <a name="how-should-i-use-a-device-compliance-policy"></a>デバイス コンプライアンス ポリシーの使用方法

### <a name="using-ems-conditional-access"></a>EMS 条件付きアクセスを使用
コンプライアンス ポリシーは、EMS 条件付きアクセスと一緒に使用することで、1 つ以上のデバイス コンプライアンス ポリシー ルールに準拠しているデバイスにのみ電子メールや他の企業リソースへのアクセスを許可することができます。

### <a name="not-using-ems-conditional-access"></a>EMS 条件付きアクセスを使用しない
また、EMS 条件付きアクセスと独立してデバイス コンプライアンス ポリシーを使用することもできます。
コンプライアンス ポリシーを単独で使用した場合、対象のデバイスが評価され、コンプライアンス ステータスを含めて報告されます。 たとえば、暗号化されていないデバイスの数や脱獄またはルート化されたデバイスに関するレポートを取得できます。 ただし、コンプライアンス ポリシーを単独で使用した場合、会社のリソースへのアクセス制限が設定されません。

コンプライアンス ポリシーはユーザーに展開して使用します。 コンプライアンス ポリシーがユーザーに展開されると、ユーザーのデバイスのコンプライアンスがチェックされます。 ポリシーの展開後にモバイル デバイスがポリシーを取得できるようになるまでにかかる時間については、デバイスでの設定と機能の管理に関するページを参照してください。

##  <a name="intune-classic-admin-console-vs-intune-on-the-azure-portal"></a>Intune クラシック 管理コンソール対Azure Portal での Intune

Intune クラシック管理コンソールを利用している場合は、以下の相違点について把握し、Azure Portal の新しいデバイス コンプライアンス ポリシー ワークフローへの移行に役立ててください。

-   Azure Portal では、コンプライアンス ポリシーがサポート対象のプラットフォームごとに個別に作成されます。 Intune 管理コンソールでは、すべてのサポート対象プラットフォームで 1 つのコンプライアンス ポリシーが共有されていました。

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migration-from-intune-classic-console-to-intune-on-the-azure-portal"></a>Intune クラシック コンソールから Azure Portal での Intune への移行

[Intune クラシック コンソール](https://manage.microsoft.com)で作成したデバイス コンプライアンス ポリシーは、新しい [Intune Azure Portal](https://portal.azure.com) で表示されません。 ただし、これらのポリシーは引き続きユーザーを対象とし、Intune クラシック コンソールで管理できます。

Intune Azure Portal のデバイス コンプライアンスに関連した新機能を活用するには、Intune Azure Portal で新しいデバイス コンプライアンス ポリシーを作成する必要があります。 Intune クラシック ポータルのデバイス コンプライアンス ポリシーが既に割り当てられているユーザーに Intune Azure Portal の新しいデバイス コンプライアンス ポリシーを割り当てると、Intune クラシック コンソールで作成されたポリシーよりも Intune Azure Portal のデバイス コンプライアンス ポリシーが優先されます。

##  <a name="next-steps"></a>次のステップ

[デバイス コンプライアンス ポリシーの概要](device-compliance-get-started.md)


<!---### See also

Conditional access--->

