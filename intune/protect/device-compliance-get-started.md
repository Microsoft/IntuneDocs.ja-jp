---
title: Microsoft Intune - Azure のデバイス コンプライアンス ポリシー | Microsoft Docs
description: デバイス コンプライアンス ポリシーの使用の開始、状態と重大度レベルの概要、InGracePeriod 状態の使用、条件付きアクセスの使用、割り当てポリシーなしのデバイスの処理。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/13/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b593cab8a9a89f895c668b2b49583b73cbfccffa
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515171"
---
# <a name="set-rules-on-devices-to-allow-access-to-resources-in-your-organization-using-intune"></a>Intune を使用して組織内のリソースへのアクセスを許可するように、デバイス上でルールを設定する

モバイル デバイス管理 (MDM) ソリューションの多くでは、組織のデータを保護するために、ユーザーやデバイスがいくつかの要件を満たすことを要求します。 Intune では、この機能は "コンプライアンス ポリシー" と呼ばれています。 コンプライアンス ポリシーでは、準拠ユーザーおよびデバイスであるために満たす必要があるルールや設定が定義されます。 条件付きアクセスと組み合わせた場合、管理者はルールを満たしていないユーザーとデバイスをブロックすることができます。

たとえば、Intune 管理者は次を要求できます。

- モバイル デバイス上の組織のデータにアクセスするために、エンド ユーザーがパスワードを使うこと
- デバイスが脱獄またはルート化されていないこと
- デバイスのオペレーティング システムの最小または最大バージョン
- デバイスが脅威レベル以下であること

また、この機能を使用して、組織のデバイス上のコンプライアンス状態を監視することもできます。

> [!IMPORTANT]
> Intune では、デバイス上のすべてのコンプライアンス評価をデバイスのチェックイン スケジュールに従って行います。 [ポリシーとプロファイルの更新サイクル](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)に関するページに、おおよその更新間隔が一覧表示されています。

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

- When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

- 3 days after initial noncompliance state, a follow up reminder is sent to the user.

- 5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

- 7 days after initial noncompliance state, access to company resources is blocked. This requires that you have Conditional Access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement Conditional Access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="device-compliance-policies-work-with-azure-ad"></a>デバイス コンプライアンス ポリシーと Azure AD の連携

Intune では、Azure Active Directory (AD) の[条件付きアクセス](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) (別のドキュメント Web サイトが開きます) を使用して、コンプライアンスが適用されます。 デバイスが Intune に登録されると、Azure AD の登録プロセスが開始され、デバイス情報が Azure AD で更新されます。 重要な情報の 1 つとして、デバイスのコンプライアンス状態があります。 このコンプライアンス状態は、電子メールと他の組織のリソースへのアクセスをブロックまたは許可するための条件付きアクセス ポリシーによって使用されます。

- 「[Azure Active Directory のデバイス管理とは](https://docs.microsoft.com/azure/active-directory/device-management-introduction)」は、デバイスが Azure AD に登録される理由と方法に最適なリソースです。

- [条件付きアクセス](conditional-access.md)に関するページと[条件付きアクセスの一般的な使用方法](conditional-access-intune-common-ways-use.md)に関するページでは、Intune に関連するこの機能について説明されています。

## <a name="ways-to-use-device-compliance-policies"></a>デバイス コンプライアンス ポリシーを使用する方法

### <a name="with-conditional-access"></a>条件付きアクセスあり

ポリシー規則に準拠しているデバイスには、電子メールやその他の組織のリソースへのアクセス許可を付与することができます。 デバイスがポリシー規則に準拠していない場合は、組織のリソースにアクセスすることはできません。 これが条件付きアクセスです。

### <a name="without-conditional-access"></a>条件付きアクセスなし

条件付きアクセスなしのデバイス コンプライアンス ポリシーを使用することもできます。 コンプライアンス ポリシーを単独で使用した場合、対象のデバイスが評価され、コンプライアンス ステータスを含めて報告されます。 たとえば、暗号化されていないデバイスの数や、脱獄またはルート化されたデバイスに関するレポートを取得できます。 条件付きアクセスなしでコンプライアンス ポリシーを使用する場合、組織のリソースに対するアクセス制限はありません。

## <a name="ways-to-deploy-device-compliance-policies"></a>デバイス コンプライアンス ポリシーを展開する方法

ユーザー グループ内のユーザー、またはデバイス グループ内のデバイスにコンプライアンス ポリシーを展開することができます。 コンプライアンス ポリシーがユーザーに展開されると、すべてのユーザーのデバイスのコンプライアンスがチェックされます。 Windows 10 バージョン 1803 以降のデバイスでは、プライマリ ユーザーがデバイスを登録しなかった*場合は*デバイス グループに展開することをお勧めします。 このシナリオでのデバイス グループの使用は、コンプライアンス レポートに役立ちます。

Intune には、組み込みのコンプライアンス ポリシー設定のセットも含まれています。 次の組み込みのポリシーは、Intune に登録されたすべてのデバイスで評価されます。

- **[Mark devices with no compliance policy assigned as]\(コンプライアンス ポリシーが割り当てられていないデバイスにマークを付ける\)** :このプロパティには次の 2 つの値があります。

  - **[準拠]** (*既定値*): セキュリティ機能が無効
  - **[非準拠]** : セキュリティ機能が有効

  デバイスにコンプライアンス ポリシーが割り当てられていない場合、そのデバイスは既定で準拠と見なされます。 コンプライアンス ポリシーで条件付きアクセスを使用する場合は、既定の設定を **[非準拠]** に変更することをお勧めします。 ポリシーが割り当てられていないためにエンド ユーザーが準拠していない場合、[ポータル サイト アプリ](../apps/company-portal-app.md)には `No compliance policies have been assigned` と表示されます。


> [!NOTE]
> iOS/iPadOS デバイスの脱獄の高度な検出は、Intune で一時的に無効にされています。

- **[脱獄の高度な検出]** :この設定が有効な場合、iOS/iPadOS デバイスは Intune によって、より頻繁にチェックインされます。 このプロパティを有効にすると、デバイスの位置情報サービスが使用され、バッテリの使用量に影響します。 ユーザーの場所データは Intune では保存されません。

  この設定を有効にするには、デバイスで以下の操作が必要です。
  - OS レベルで位置情報サービスを有効にする
  - ポータル サイトで位置情報サービスを使用できるようにする
  - 72 時間ごとに 1 回以上、脱獄状態を評価して Intune にレポートする それ以外の場合、デバイスは非準拠とマークされます。 ポータル サイト アプリを開くか、デバイスを 500 メートル以上物理的に移動すると、評価がトリガーされます。 デバイスが 72 時間以内に 500 メートルを移動しない場合は、脱獄評価を強化するために、ユーザーはポータル サイト アプリを開く必要があります。

- **[コンプライアンス状態の有効期間 (日)]** :デバイスが受け取ったすべてのコンプライアンス ポリシーの状態をレポートする期間を入力します。 この期間内に状態を返さないデバイスは非準拠として扱われます。 既定値は 30 日です。 最小値は 1 日です。

  この設定は、 **[アクティブ]** な既定のコンプライアンス ポリシーとして表示されます ( **[デバイス]**  >  **[監視]**  >  **[コンプライアンスの設定]** )。 このポリシーのバックグラウンド タスクは 1 日に 1 回実行されます。

これらの組み込みポリシーを使用して、これらの設定を監視できます。 Intune では、デバイス プラットフォームに応じて、さまざまな間隔で[更新プログラムの更新または確認](create-compliance-policy.md#refresh-cycle-times)も行われます。 「[Microsoft Intune でのデバイス プロファイルの一般的な問題と解決策](../configuration/device-profile-troubleshoot.md)」は、適切なリソースです。

コンプライアンス レポートは、デバイスの状態を確認する優れた方法です。 [コンプライアンス ポリシーの監視](compliance-policy-monitor.md)には、いくつかのガイダンスが含まれています。

## <a name="non-compliance-and-conditional-access-on-the-different-platforms"></a>さまざまなプラットフォームでのコンプライアンス違反と条件付きアクセス

次の表では、条件付きアクセス ポリシーとコンプライアンス ポリシーを使用する場合に非準拠設定をどのように管理するかについて説明しています。

---------------------------

|**ポリシー設定**| **プラットフォーム** |
| --- | ----|
| **PIN またはパスワードの構成** | - **Android 4.0 以降**: 検疫済み<br>- **Samsung KNOX Standard 4.0 以降**: 検疫済み<br>- **Android エンタープライズ**: 検疫済み  <br>  <br>- **iOS 8.0 以降**: 修復<br>- **macOS 10.11 以降**: 修復  <br>  <br>- **Windows 8.1 以降**: 修復<br>- **Windows Phone 8.1 以降**: 修復|
| **デバイスの暗号化** | - **Android 4.0 以降**: 検疫済み<br>- **Samsung KNOX Standard 4.0 以降**: 検疫済み<br>- **Android エンタープライズ**: 検疫済み<br><br>- **iOS 8.0 以降**: 修復 (PIN の設定による)<br>- **macOS 10.11 以降**: 修復 (PIN の設定による)<br><br>- **Windows 8.1 以降**: 適用できません<br>- **Windows Phone 8.1 以降**: 修復 |
| **脱獄またはルート化されたデバイス** | - **Android 4.0 以降**: 検疫済み (設定ではありません)<br>- **Samsung KNOX Standard 4.0 以降**: 検疫済み (設定ではありません)<br>- **Android エンタープライズ**: 検疫済み (設定ではありません)<br><br>- **iOS 8.0 以降**: 検疫済み (設定ではありません)<br>- **macOS 10.11 以降**: 適用できません<br><br>- **Windows 8.1 以降**: 適用できません<br>- **Windows Phone 8.1 以降**: 適用できません |
| **電子メールのプロファイル** | - **Android 4.0 以降**: 適用できません<br>- **Samsung KNOX Standard 4.0 以降**: 適用できません<br>- **Android エンタープライズ**: 適用できません<br><br>- **iOS 8.0 以降**: 検疫済み<br>- **macOS 10.11 以降**: 検疫済み<br><br>- **Windows 8.1 以降**: 適用できません<br>- **Windows Phone 8.1 以降**: 適用できません |
| **最小 OS バージョン** | - **Android 4.0 以降**: 検疫済み<br>- **Samsung KNOX Standard 4.0 以降**: 検疫済み<br>- **Android エンタープライズ**: 検疫済み<br><br>- **iOS 8.0 以降**: 検疫済み<br>- **macOS 10.11 以降**: 検疫済み<br><br>- **Windows 8.1 以降**: 検疫済み<br>- **Windows Phone 8.1 以降**: 検疫済み |
| **最大 OS バージョン** | - **Android 4.0 以降**: 検疫済み<br>- **Samsung KNOX Standard 4.0 以降**: 検疫済み<br>- **Android エンタープライズ**: 検疫済み<br><br>- **iOS 8.0 以降**: 検疫済み<br>- **macOS 10.11 以降**: 検疫済み<br><br>- **Windows 8.1 以降**: 検疫済み<br>- **Windows Phone 8.1 以降**: 検疫済み |
| **Windows 正常性構成証明書** | - **Android 4.0 以降**: 適用できません<br>- **Samsung KNOX Standard 4.0 以降**: 適用できません<br>- **Android エンタープライズ**: 適用できません<br><br>- **iOS 8.0 以降**: 適用できません<br>- **macOS 10.11 以降**: 適用できません<br><br>- **Windows 10 および Windows 10 Mobile**: 検疫済み<br>- **Windows 8.1 以降**: 検疫済み<br>- **Windows Phone 8.1 以降**: 適用できません |

---------------------------

**修復**: デバイス オペレーティング システムによってコンプライアンスが適用されます。 たとえば、ユーザーは PIN を設定するように強制されます。

**検疫済み**: デバイス オペレーティング システムによってコンプライアンスは適用されません。 たとえば、Android デバイスと Android エンタープライズ デバイスでは、ユーザーはデバイスの暗号化を強制されません。 デバイスが準拠していない場合、次のアクションが行われます。

- ユーザーに条件付きアクセス ポリシーを適用すると、デバイスがブロックされます。
- ポータル サイト アプリでは、コンプライアンスの問題についてユーザーに通知します。

## <a name="next-steps"></a>次のステップ

- [ポリシーを作成](create-compliance-policy.md)して、前提条件を表示します。
- さまざまなデバイス プラットフォームでのコンプライアンス設定を参照してください。

  - [Android](compliance-policy-create-android.md)
  - [Android エンタープライズ](compliance-policy-create-android-for-work.md)
  - [Android](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows Holographic for Business](compliance-policy-create-windows.md#windows-holographic-for-business)
  - [Windows Phone 8.1](compliance-policy-create-windows-8-1.md)
  - [Windows 8.1 以降](compliance-policy-create-windows-8-1.md)
  - [Windows 10 以降](compliance-policy-create-windows.md)

- 「[ポリシー エンティティのリファレンス](../reports-ref-policy.md)」には、Intune データ ウェアハウス ポリシー エンティティに関する情報が含まれます。
