---
title: Microsoft Intune - Azure のデバイス コンプライアンス ポリシー | Microsoft Docs
description: デバイス コンプライアンス ポリシーを使用する場合の要件、状態と重大度レベルの概要、InGracePeriod 状態の使用、条件付きアクセスの使用、割り当てポリシーなしのデバイスの処理、Microsoft Intune の Azure Portal とクラシック ポータルのコンプライアンスの違い
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3326ecccd0d20602d6a9445b62c39f582354f238
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="get-started-with-device-compliance-policies-in-intune"></a>Intune のデバイス コンプライアンス ポリシーの概要

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

コンプライアンス要件は、基本的にはデバイス PIN を必要とするや、暗号化を必要とするなどのの規則です。 デバイス コンプライアンス ポリシーは、デバイスが準拠していると見なされるために従う必要のある規則および設定を定義します。 次のような規則があります。

- パスワードを使用したデバイスへのアクセス

- 暗号化

- デバイスが脱獄またはルート化されているかどうか

- 必要な最小 OS バージョン

- 許可される最大 OS バージョン

- デバイスが Mobile Threat Defense レベル以下であることが必要

デバイス コンプライアンス ポリシーを使用して、デバイス コンプライアンスの状態を監視することもできます。

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

## <a name="prerequisites"></a>必要条件
デバイス コンプライアンス ポリシーを使用するには、以下が必要です。

- 以下のサブスクリプションを使用します。

  - Intune
  - Azure Active Directory (AD) Premium

- サポートされているプラットフォームを使用します。

  - Android
  - iOS
  - macOS (プレビュー)
  - Windows 8.1
  - Windows Phone 8。1
  - Windows 10

- コンプライアンスの状態をレポートするには、Intune にデバイスを登録する必要があります。

## <a name="how-intune-device-compliance-policies-work-with-azure-ad"></a>Azure AD で Intune のデバイス コンプライアンス ポリシーを操作する方法

デバイスが Intune に登録されると、Azure AD の登録プロセスが開始され、デバイス属性が Azure AD に更新されます。 重要な情報の 1 つとして、デバイスのコンプライアンス状態があります。 このコンプライアンス状態は、電子メールと他の企業リソースへのアクセスをブロックまたは許可するための条件付きアクセス ポリシーによって使用されます。

[Azure AD の登録プロセス](https://docs.microsoft.com/en-us/azure/active-directory/device-management-introduction)に関するページで詳しく説明します。

### <a name="assign-a-resulting-device-configuration-profile-status"></a>デバイスの構成プロファイルの結果の状態を割り当てる

デバイスに複数の構成プロファイルがあり、デバイスの 2 つ以上の割り当て済み構成プロファイルが異なるコンプライアンス状態になっている場合、1 つの結果のコンプライアンス状態が割り当てられます。 この割り当ては、各コンプライアンス状態に割り当てられている概念的な重大度レベルを基にしています。 各コンプライアンス状態には、次の重大度レベルがあります。

|状態  |重大度  |
|---------|---------|
|Pending     |1|
|成功     |2|
|Failed     |3|
|エラー     |4|

デバイスに複数の構成プロファイルがある場合、すべてのプロファイルの最も高い重大度レベルがそのデバイスに割り当てられます。

たとえば、デバイスに 3 つのプロファイルが割り当てられていて、1 つが保留中の状態 (重大度 = 1)、1 つが成功状態 (重大度 = 2)、1 つがエラー状態 (重大度 = 4) だとします。 エラー状態の重大度レベルが最も高いので、3 つすべてのプロファイルのコンプライアンス状態はエラーとなります。

### <a name="assign-an-ingraceperiod-status"></a>InGracePeriod 状態を割り当てる

コンプライアンス ポリシーの InGracePeriod 状態は値の 1 つです。 この値は、デバイスの猶予期間、およびそのコンプライアンス ポリシーのデバイスの実際の状態の組み合わせによって決まります。

具体的には、デバイスに割り当てられているコンプライアンス ポリシーが NonCompliant 状態になっている場合、次のようになります。

- デバイスに猶予期間が割り当てられていない場合、コンプライアンス ポリシーの割り当て済みの値は NonCompliant です。
- デバイスに割り当てられている猶予期間が期限切れになっている場合、コンプライアンス ポリシーの割り当て済みの値は NonCompliant です。
- デバイスに将来の猶予期間が割り当てられている場合、コンプライアンス ポリシーの割り当て済みの値は InGracePeriod です。

次の表はこれらの点をまとめたものです。

|実際のコンプライアンス状態|割り当てられた猶予期間の値|有効なコンプライアンス状態|
|---------|---------|---------|
|NonCompliant |猶予期間が割り当てられていない |NonCompliant |
|NonCompliant |昨日の日付|NonCompliant|
|NonCompliant |明日の日付|InGracePeriod|

デバイスのコンプライアンス ポリシーの監視の詳細については、「[Intune デバイス コンプライアンス対応ポリシーの監視](compliance-policy-monitor.md)」を参照してください。

### <a name="assign-a-resulting-compliance-policy-status"></a>コンプライアンス ポリシーの結果の状態を割り当てる

デバイスに複数のコンプライアンス ポリシーがあり、デバイスの 2 つ以上の割り当て済みコンプライアンス ポリシーが異なるコンプライアンス状態になっている場合、1 つの結果のコンプライアンス状態が割り当てられます。 この割り当ては、各コンプライアンス状態に割り当てられている概念的な重大度レベルを基にしています。 各コンプライアンス状態には、次の重大度レベルがあります。

|状態  |重大度  |
|---------|---------|
|Unknown     |1|
|NotApplicable     |2|
|準拠|3|
|InGracePeriod|4|
|NonCompliant|5|
|エラー|6|

デバイスに複数のコンプライアンス ポリシーがある場合、すべてのポリシーの最も高い重大度がそのデバイスに割り当てられます。

たとえば、デバイスに 3 つのコンプライアンス ポリシーに割り当てられていて、1 つが不明状態 (重大度 = 1)、1 つが準拠状態 (重大度 = 3)、1 つが InGracePeriod 状態 (重要度 = 4) であるとします。 InGracePeriod 状態の重大度レベルが最も高いので、3 つすべてのポリシーのコンプライアンス状態は InGracePeriod になります。

## <a name="ways-to-use-device-compliance-policies"></a>デバイス コンプライアンス ポリシーを使用する方法

#### <a name="with-conditional-access"></a>条件付きアクセスあり
ポリシー規則に準拠しているデバイスには、電子メールやその他の企業リソースへのアクセス許可を付与することができます。 ポリシー規則に準拠していないデバイスは、企業リソースにアクセスすることはできません。 これが条件付きアクセスです。

#### <a name="without-conditional-access"></a>条件付きアクセスなし
条件付きアクセスなしのデバイス コンプライアンス ポリシーを使用することもできます。 コンプライアンス ポリシーを単独で使用した場合、対象のデバイスが評価され、コンプライアンス ステータスを含めて報告されます。 たとえば、暗号化されていないデバイスの数や脱獄またはルート化されたデバイスに関するレポートを取得できます。 条件付きアクセスなしのコンプライアンス ポリシーを使用する場合、会社のリソースへのアクセス制限はありません。

## <a name="ways-to-deploy-device-compliance-policies"></a>デバイス コンプライアンス ポリシーを展開する方法
ユーザー グループ内のユーザー、またはデバイス グループ内のデバイスにコンプライアンス ポリシーを展開することができます。 コンプライアンス ポリシーがユーザーに展開されると、ユーザーのデバイスのコンプライアンスがチェックされます。

デバイス グループ内のデバイスの場合、**[コンプライアンス ポリシー設定]** ([Azure Portal] > [デバイスのポリシー準拠]) には以下が含まれます。

- **[Mark devices with no compliance policy assigned as]\(コンプライアンス ポリシーが割り当てられていないデバイスにマークを付ける\)**: このプロパティには次の 2 つの値があります。

  - **[準拠]**: セキュリティ機能が無効
  - **[非準拠]** (既定値): セキュリティ機能が有効

  デバイスにコンプライアンス ポリシーが割り当てられていない場合、そのデバイスは非準拠と見なされます。 既定では、デバイスは **[非準拠]** としてマークされます。 条件付きアクセスを使用する場合は、既定の設定の **[非準拠]** のままにしておくことをお勧めします。 ポリシーが割り当てられていないためにエンド ユーザーが非準拠である場合、ポータル サイトには `No compliance policies have been assigned` とリストされます。

- **[脱獄の高度な検出]**: この設定が有効な場合、iOS デバイスは Intune によって、より頻繁にチェックインされます。 このプロパティを有効にすると、デバイスの位置情報サービスが使用され、バッテリの使用量に影響します。 ユーザーの場所データは Intune では保存されません。

  この設定を有効にするには、デバイスで以下の操作が必要です。
  - OS レベルで位置情報サービスを有効にする
  - ポータル サイトで位置情報サービスを使用できるようにする
  - 72 時間ごとに 1 回以上、脱獄状態を評価して Intune にレポートする それ以外の場合、デバイスは非準拠とマークされます。

- **[コンプライアンス状態の有効期間 (日)]**: デバイスが受け取ったすべてのコンプライアンス ポリシーの状態をレポートする期間を入力します。 この期間内に状態を返さないデバイスは非準拠として扱われます。 既定値は 30 日です。

すべてのデバイスに**既定のデバイス コンプライアンス ポリシー** ([Azure Portal] > [デバイス コンプライアンス] > [ポリシー コンプライアンス]) があります。 この既定のポリシーを使用して、これらの設定を監視します。

ポリシーの展開後にモバイル デバイスがポリシーを取得できるようになるまでの時間については、[デバイス プロファイルのトラブルシューティング](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned)に関するページを参照してください。

コンプライアンス レポートは、デバイスの状態を確認する優れた方法です。 ガイダンスについては、[コンプライアンス ポリシーの監視](compliance-policy-monitor.md)に関するページを参照してください。

### <a name="actions-for-noncompliance"></a>コンプライアンス非対応に対するアクション
コンプライアンス ポリシーの条件を満たしていないデバイスに適用されるアクションを時刻順に構成することができます。 コンプライアンス非対応に対するこれらのアクションを自動化することができます (「[コンプライアンス非対応に対するアクションを自動化する](actions-for-noncompliance.md)」を参照)。

## <a name="azure-classic-portal-vs-azure-portal"></a>Azure クラシック ポータルと Azure Portal

Azure ポータルでデバイス コンプライアンス ポリシーを使用する場合の主な違い:

- Azure Portal では、コンプライアンス ポリシーがサポート対象のプラットフォームごとに個別に作成されます。
- Azure クラシック ポータルでは、すべてのサポート対象プラットフォームで 1 つのデバイス コンプライアンス ポリシーが共有されます。

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

## <a name="device-compliance-policies-in-the-classic-portal-and-azure-portal"></a>クラシック ポータルと Azure Portal のデバイス コンプライアンス ポリシー

[クラシック ポータル](https://manage.microsoft.com)で作成されたデバイス コンプライアンス ポリシーは、[Azure Portal](https://portal.azure.com) には表示されません。 ただし、これらのポリシーは引き続きユーザーを対象とし、クラシック ポータルを使用して管理できます。

Azure Portal でデバイス コンプライアンスに関連した機能を使用するには、Azure Portal で新しいデバイス コンプライアンス ポリシーを作成する必要があります。 クラシック ポータルのデバイス コンプライアンス ポリシーが既に割り当てられているユーザーに Azure Portal のデバイス コンプライアンス ポリシーを割り当てると、クラシック ポータルで作成されたポリシーよりも Azure Portal のデバイス コンプライアンス ポリシーが優先されます。

## <a name="next-steps"></a>次の手順

- 以下のプラットフォームに対してデバイス コンプライアンス ポリシーを作成します。

  - [Android](compliance-policy-create-android.md)
  - [Android for Work](compliance-policy-create-android-for-work.md)
  - [Android](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Intune データ ウェアハウス ポリシー エンティティの詳細については、「[ポリシーのエンティティのリファレンス](reports-ref-policy.md)」を参照してください。
