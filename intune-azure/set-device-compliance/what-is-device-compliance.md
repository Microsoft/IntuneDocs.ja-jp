---
title: "デバイス コンプライアンス | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: このトピックでは、Microsoft Intune でのデバイス コンプライアンスについて説明します。"
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
translationtype: Human Translation
ms.sourcegitcommit: 7693d49e2f0fa6e4aa40b6bb71433a7eaab8dd15
ms.openlocfilehash: a4254503e4e6b86079f862966dee2727934f1ee6


---

# <a name="what-is-device-compliance-in-intune-azure-preview"></a>Intune Azure プレビューでのデバイス コンプライアンスとは


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

会社のデータを容易に保護できるようにするには、会社のアプリとデータへのアクセスに使用されるデバイスが特定のルールに準拠していることを確認する必要があります。 これらのルールには、PIN を使用するデバイスへのアクセスと、デバイスに格納されているデータの暗号化に関するものが含まれる場合があります。 このような一連のルールは、**コンプライアンス ポリシー**と呼ばれます。

##  <a name="how-should-i-use-a-device-compliance-policy"></a>デバイス コンプライアンス ポリシーの使用方法
コンプライアンス ポリシーは、条件付きアクセスと一緒に使用することで、コンプライアンス ポリシー ルールに準拠しているデバイスにのみ電子メールや他のサービスへのアクセスを許可することができます。

また、条件付きアクセスと独立してコンプライアンス ポリシーを使用することもできます。
コンプライアンス ポリシーを単独で使用した場合、対象のデバイスが評価され、コンプライアンス ステータスを含めて報告されます。 たとえば、暗号化されていないデバイスの数や脱獄またはルート化されたデバイスに関するレポートを取得できます。 ただし、コンプライアンス ポリシーを単独で使用した場合、会社のリソースへのアクセス制限が設定されません。

コンプライアンス ポリシーはユーザーに展開して使用します。 コンプライアンス ポリシーがユーザーに展開されると、ユーザーのデバイスのコンプライアンスがチェックされます。 ポリシーの展開後にモバイル デバイスがポリシーを取得できるようになるまでにかかる時間については、デバイスでの設定と機能の管理に関するページを参照してください。

##  <a name="concepts"></a>概念
以下に、コンプライアンス ポリシーの使用方法を把握するうえで役立ついくつかの用語と概念を挙げます。

### <a name="compliance-requirements"></a>コンプライアンス要件
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

##  <a name="differences-between-the-classic-intune-admin-console-and-intune-in-the-azure-portal"></a>クラシック Intune 管理コンソールと Azure Portal の Intune の相違点


以前からクラシック Intune 管理コンソールを利用している場合は、以下の相違点について把握し、Azure Portal の新しいデバイス コンプライアンス ワークフローへの移行に役立ててください。


-   Azure Portal では、コンプライアンス ポリシーがサポート対象のプラットフォームごとに個別に作成されます。 Intune 管理コンソールでは、すべてのサポート対象プラットフォームで&1; つのコンプライアンス ポリシーが共有されていました。


<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="next-steps"></a>次のステップ

[コンプライアンス ポリシーの概要](get-started-with-device-compliance.md)


<!---### See also

Conditional access--->



<!--HONumber=Feb17_HO1-->


