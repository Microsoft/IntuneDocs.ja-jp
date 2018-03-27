---
title: Microsoft Intune のデバイス コンプライアンス ポリシー
titleSuffix: ''
description: Microsoft Intune でのデバイス コンプライアンスについての説明
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fb3ec168844708d80c83909ab6c58a52ca62e53c
ms.sourcegitcommit: a22309174e617e59ab0cdd0a55abde38711a5f35
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="get-started-with-microsoft-intune-device-compliance-policies"></a>Microsoft Intune のデバイス コンプライアンス ポリシーの概要


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune のデバイス コンプライアンス ポリシーは、デバイスが Intune によって準拠していると見なされるために遵守する必要がある規則および設定を定義します。

この規則には次のようなものがあります。

- パスワードを使用したデバイスへのアクセス

- 暗号化

- デバイスが脱獄またはルート化されているかどうか

- 必要な最小 OS バージョン

- 許可される最大 OS バージョン

- デバイスが Mobile Threat Defense レベル以下であることが必要

デバイス コンプライアンス ポリシーを使用して、デバイス コンプライアンスの状態を監視することもできます。

## <a name="device-compliance-requirements"></a>デバイス コンプライアンスの要件

コンプライアンス要件とは、基本的にはデバイスの PIN または暗号化を要求するようなルールであり、コンプライアンス ポリシーに対して必要か不要かを指定できます。

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

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

- Intune

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

デバイスが Intune に登録されると、Azure AD の登録プロセスが発生し、デバイスの属性が Azure AD への詳細な情報で更新されます。 1 つのキーのデバイス情報は、デバイス コンプライアンスの状態で、電子メールと他の企業リソースへのアクセスをブロックまたは許可するための条件付きアクセス ポリシーによって使用されます。

- 詳細については、[Azure Active Directory の登録プロセス](https://docs.microsoft.com/en-us/azure/active-directory/device-management-introduction)に関するページを参照してください。

### <a name="assigning-a-resulting-device-configuration-profile-status"></a>デバイスの構成プロファイルの結果の状態を割り当てる

デバイスに複数の構成プロファイルが割り当てられていて、デバイスの 2 つ以上の割り当て済み構成プロファイルが異なるコンプライアンス状態になっている場合、1 つの結果のコンプライアンス状態を割り当てる必要があります。 この割り当ては、各コンプライアンス状態に割り当てられている概念的な重大度レベルを基にしています。 各コンプライアンス状態には、次の重大度レベルがあります。


|状態  |重大度  |
|---------|---------|
|Pending     |1|
|成功     |2|
|Failed     |3|
|エラー     |4|

2 つ以上の構成プロファイルの結果の状態は、デバイスに割り当てられているすべてのプロファイルの最大の重大度レベルを選択することで決定されます。

たとえば、デバイスに 3 つのプロファイルが割り当てられていて、1 つが保留中の状態 (重大度 = 1)、1 つが成功状態 (重大度 = 2)、1 つがエラー状態 (重大度 = 4) だとします。 エラー状態が最も重大度が高いので、この 3 つのプロファイルの結果のコンプライアンス状態としてエラー状態が割り当てられます。

### <a name="assigning-an-ingraceperiod-status-for-an-assigned-compliance-policy"></a>割り当て済みコンプライアンス ポリシーの InGracePeriod 状態を割り当てる

コンプライアンス ポリシーの InGracePeriod 状態は、デバイスの猶予期間と割り当てられているコンプライアンス ポリシーのデバイスの実際の状態の組み合わせを考慮して決定される値です。 

具体的には、デバイスに割り当てられているコンプライアンス ポリシーが NonCompliant 状態になっている場合、次のようになります。

- デバイスに猶予期間が割り当てられていない場合、コンプライアンス ポリシーの割り当て済みの値は NonCompliant です。
- デバイスに割り当てられている猶予期間が期限切れになっている場合、コンプライアンス ポリシーの割り当て済みの値は NonCompliant です。
- デバイスに将来の猶予期間が割り当てられている場合、コンプライアンス ポリシーの割り当て済みの値は InGracePeriod です。

次の表に、前の事項の概要を示します。


|実際のコンプライアンス状態|割り当てられた猶予期間の値|有効なコンプライアンス状態|
|---------|---------|---------|
|NonCompliant |猶予期間が割り当てられていない |NonCompliant |
|NonCompliant |昨日の日付|NonCompliant|
|NonCompliant |明日の日付|InGracePeriod|

デバイスのコンプライアンス ポリシーの監視の詳細については、「[Intune デバイス コンプライアンス対応ポリシーの監視](compliance-policy-monitor.md)」を参照してください。

### <a name="assigning-a-resulting-compliance-policy-status"></a>コンプライアンス ポリシーの結果の状態を割り当てる

デバイスに複数のコンプライアンス ポリシーが割り当てられていて、デバイスの 2 つ以上の割り当て済みコンプライアンス ポリシーが異なるコンプライアンス状態になっている場合、1 つの結果のコンプライアンス状態を割り当てる必要があります。 この割り当ては、各コンプライアンス状態に割り当てられている概念的な重大度レベルを基にしています。 各コンプライアンス状態には、次の重大度レベルがあります。 

|状態  |重大度  |
|---------|---------|
|Unknown     |1|
|NotApplicable     |2|
|準拠|3|
|InGracePeriod|4|
|NonCompliant|5|
|エラー|6|

2 つ以上のコンプライアンス ポリシーの結果の状態は、デバイスに割り当てられているすべてのプロファイルの最大の重大度レベルを選択することで決定されます。
 
たとえば、デバイスに 3 つのコンプライアンス ポリシーに割り当てられていて、1 つが不明状態 (重大度 = 1)、1 つが準拠状態 (重大度 = 3)、1 つが InGracePeriod 状態 (重要度 = 4) であるとします。 InGracePeriod 状態が最も重大度が高いので、この 3 つのプロファイルの結果のコンプライアンス状態として InGracePeriod 状態が割り当てられます。  

##  <a name="ways-to-use-device-compliance-policies"></a>デバイス コンプライアンス ポリシーを使用する方法

### <a name="with-conditional-access"></a>条件付きアクセスあり
コンプライアンス ポリシーは、条件付きアクセスと一緒に使用することで、1 つ以上のデバイス コンプライアンス ポリシー ルールに準拠しているデバイスにのみ電子メールや他の企業リソースへのアクセスを許可することができます。

### <a name="without-conditional-access"></a>条件付きアクセスなし
条件付きアクセスと独立してデバイス コンプライアンス ポリシーを使用することもできます。 コンプライアンス ポリシーを単独で使用した場合、対象のデバイスが評価され、コンプライアンス ステータスを含めて報告されます。 たとえば、暗号化されていないデバイスの数や脱獄またはルート化されたデバイスに関するレポートを取得できます。 ただし、コンプライアンス ポリシーを単独で使用した場合、会社のリソースへのアクセス制限が設定されません。

コンプライアンス ポリシーはユーザーに展開して使用します。 コンプライアンス ポリシーがユーザーに展開されると、ユーザーのデバイスのコンプライアンスがチェックされます。 ポリシーの展開後にモバイル デバイスがポリシーを取得できるようになるまでの時間については、「[Microsoft Intune のデバイス プロファイルに関するトラブルシューティング](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned)」を参照してください。

#### <a name="actions-for-non-compliance"></a>コンプライアンス非対応に対するアクション

コンプライアンス非対応に対するアクションでは、コンプライアンス ポリシーの条件を満たしていない、コンプライアンス非対応のデバイスに適用されるアクションを時刻順に構成できます。 詳細については、「[コンプライアンス非対応に対するアクションを自動化する](actions-for-noncompliance.md)」を参照してください。

##  <a name="using-device-compliance-policies-in-the-intune-classic-portal-vs-azure-portal"></a>Intune のクラシック ポータルとAzure Portal を比較してデバイス コンプライアンス ポリシーを使用する

Azure Portal での新しいデバイス コンプライアンス ポリシーのワーク フローへの移行に役立つ主な相違点に注意してください。

- Azure Portal では、コンプライアンス ポリシーがサポート対象のプラットフォームごとに個別に作成されます。
- Intune クラシック ポータルでは、すべてのサポート対象プラットフォームで 1 つのデバイス コンプライアンス ポリシーが共有されていました。

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migrate-device-compliance-policies-from-the-intune-classic-portal-to-the-azure-portal"></a>デバイス コンプライアンス ポリシーを Intune クラシック ポータルから Azure Portal に移行する

[Intune クラシック ポータル](https://manage.microsoft.com)で作成したデバイス コンプライアンス ポリシーは、新しい [Intune Azure Portal](https://portal.azure.com) では表示されません。 ただし、これらのポリシーは引き続きユーザーを対象とし、Intune クラシック ポータルで管理できます。

Azure Portal の新しいデバイス コンプライアンスに関連した機能を活用するには、Azure Portal で新しいデバイス コンプライアンス ポリシーを作成する必要があります。 Intune クラシック ポータルのデバイス コンプライアンス ポリシーが既に割り当てられているユーザーに Azure Portal の新しいデバイス コンプライアンス ポリシーを割り当てると、Intune クラシック ポータルで作成されたポリシーよりも Intune Azure Portal のデバイス コンプライアンス ポリシーが優先されます。

##  <a name="next-steps"></a>次の手順

- 以下のプラットフォームに対してデバイス コンプライアンス ポリシーを作成します。

   - [Android](compliance-policy-create-android.md)
   - [Android for Work](compliance-policy-create-android-for-work.md)
   - [Android](compliance-policy-create-ios.md)
   - [macOS](compliance-policy-create-mac-os.md)
   - [Windows](compliance-policy-create-windows.md)

- Intune データ ウェアハウス ポリシー エンティティの詳細については、「[ポリシーのエンティティのリファレンス](reports-ref-policy.md)」を参照してください。
