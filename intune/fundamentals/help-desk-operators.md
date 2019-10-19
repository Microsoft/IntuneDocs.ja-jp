---
title: ヘルプ デスクのトラブルシューティング ポータル
titleSuffix: Microsoft Intune
description: ヘルプ デスクのスタッフが、トラブルシューティング ポータルを使用して、ユーザーの技術的な問題を解決します。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/11/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0094cdd12b2594cb60260d768daec8c5bed04c9c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72510258"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>トラブルシューティング ポータルを使用して社内のユーザーをサポートする

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

トラブルシューティング ポータルでは、ヘルプ デスクのオペレーターや Intune の管理者が、ユーザーのヘルプ要求に対処するためにユーザー情報を表示することができます。 ヘルプ デスクが含まれる組織は、ユーザーのグループに**ヘルプ デスク オペレーター**を割り当てることができます。 ヘルプ デスク オペレーター ロールの場合、 **[トラブルシューティング]** ウィンドウを使用できます。

**[トラブルシューティング]** ウィンドウにもユーザー登録に関する問題が表示されます。 問題に関する詳細と推奨される修復手順は、管理者およびヘルプ デスクのオペレーターが問題をトラブルシューティングするのに役立ちます。 登録に関する特定の問題はキャプチャされず、一部のエラーには推奨される修復方法がない場合があります。

ヘルプ デスク オペレーター ロールを追加する手順については、「[Intune でのロール ベースの管理制御 (RBAC)](/intune/role-based-access-control)」を参照してください。

ユーザーが Intune で技術的な問題をサポートに連絡すると、ヘルプ デスク オペレーターがそのユーザーの名前を入力します。 Intune には、次のような階層 1 の多くの問題を解決するのに役立つデータが示されます。

- ユーザーの状態
- ［割り当て］
- ポリシー準拠の問題
- デバイスが応答しない
- デバイスが VPN または Wi-Fi の設定を取得できない
- アプリのインストールの失敗

## <a name="to-review-troubleshooting-details"></a>トラブルシューティングの詳細を確認するには

トラブルシューティング ウィンドウで、 **[ユーザーの選択]** を選択してユーザー情報を表示します。 ユーザー情報は、ユーザーと彼らのデバイスの現在の状態を理解するのに役立ちます。  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
3. **[Intune]** ウィンドウで、 **[トラブルシューティング]** を選択します。
4. **[選択]** をクリックして、トラブルシューティングを行うユーザーを選択します。
5. 名前または電子メール アドレスを入力して、ユーザーを選択します。 **[選択]** をクリックします。 ユーザーのトラブルシューティング情報が、トラブルシューティング ウィンドウに表示されます。 情報については、次の表で説明します。

> [!Note]  
> **[トラブルシューティング]** ウィンドウには、ブラウザーで [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) に移動してアクセスすることもできます。

## <a name="areas-of-troubleshooting-dashboard"></a>トラブルシューティング ダッシュボードの領域

**[トラブルシューティング]** ウィンドウを使用して、ユーザー情報を確認することができます。

![次の表で説明する番号付き領域を持つトラブルシューティングダッシュボード](./media/help-desk-operators/troubleshooting-dash.png)

| 領域 | 名前 | 説明 |
| ---  | ---  | ---         |
| 1.   | アカウントの状態  | 現在の Intune テナントの状態が**アクティブ**または**非アクティブ**として表示されます。       |
| 2.   | ユーザー選択  | 現在選択されているユーザーの名前。 **[ユーザーの変更]** をクリックして、新しいユーザーを選択します。       |
| 3.   | ユーザーの状態  | ユーザーの Intune ライセンスの状態、デバイスの数、各デバイスのコンプライアンス状態、アプリの数、およびアプリのコンプライアンス状態が表示されます。       |
| 4.   | ユーザー情報  | 一覧を使用して、ウィンドウで確認する詳細を選択します。 <br>以下を選択できます。 <ul><li>クライアント アプリ<li>Compliance ポリシー<li> 構成ポリシー<li>アプリ保護ポリシー <li>登録制限</ul>      |
| 5.   | グループのメンバーシップ  | 選択したユーザーがメンバーになっている現在のグループが表示されます。       |

<!-- this section needs to be updated

## Client apps reference

The apps that are running devices
- managed by Intune and Azure Active Directory (AD) 
- owned by users managed by Intune and Azure Active Directory (AD).

### Properties

The properties of client apps.

| Property      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name          | The name of the application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| OS            | The operating system installed on the device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Type          | You can choose an assignment type for each app.  <br> **Available** - Users install the app from the Company Portal app or website.  <br> **Not Applicable** - The app is not installed or shown in the Company Portal. <br> **Uninstall** - The app is uninstalled from devices in the selected groups.  <br> **Available with or without enrollment** - Assign this app to groups of users whose devices are not enrolled with Intune. |
| Last Modified | The name of the type of device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| App install | Denotes whether an app install failure or success has occurred on the individual device. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection status

An app protection policy is available to mobile apps that integrate with Enterprise Mobility Solution (EMS) technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## App protection policies reference

An app protection policy is available to mobile apps that integrate with EMS technologies.These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

### Properties

The table summarizes app protection policies status for devices managed by Intune.

| Property    | Description                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Name        | The name of the application.                                                                                                        |
| Deployed    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Platform    | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Enrollment  | The name of the type of device.                                                                                                     |
| Last Update | The timestamp the policy was modified.                                                                                              |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device Name        | The name of the type of device.                                                                                                     |
| Managed By         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last Check in      | The name of the type of device.                                                                                                     |

## Compliance policies reference

Makes sure that the devices used to access company apps and data, comply with certain rules like using a PIN to access the device, and encryption of data stored on the device.

### Properties

The properties of the compliance policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## Configuration policies reference

An app configuration policy is available to mobile apps with vendor-specific configuration. 

### Properties

The properties of the configuration policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |


### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

-->

## <a name="enrollment-failure-reference"></a>登録エラーのリファレンス

登録エラー テーブルには、失敗した登録の試行が一覧表示されます。 次のテーブルに一覧表示されているデバイスは、その後の別の試行中に正常に登録されている可能性があります。 失敗した試行の一部は、一覧表示されない場合があります。 すべてのエラーで軽減策の情報を利用できるわけではありません。

| テーブル列 | 説明 |
|-------------|----------|
| 登録の開始 | ユーザーが最初に登録を開始した時間。 |
| OS | デバイスのオペレーティング システム。 |
| OS のバージョン | デバイスのオペレーティング システムのバージョン。 |
| 失敗 | エラーの理由。 |

### <a name="failure-details"></a>エラーの詳細

エラー行を選択すると、さらに詳細が提供されます。

| セクション | 説明 |
|-------------|----------|
| エラーの詳細 | エラーのより詳細な説明。 |
| 考えられる修復 | エラーを解決するための推奨手順。 エラーの中には、修復できないものもあります。 |
| リソース (省略可能) | 参考資料やアクションを実行するためのポータルの領域へのリンク。 |

### <a name="enrollment-errors"></a>登録エラー

| エラー | 説明 |
|-------------|----------|
| iOS タイムアウトまたは障害 | ユーザーが登録を完了するのに時間がかかり過ぎたことによる、デバイスと Intune 間のタイムアウト。 |
| ユーザーが見つからないか、ライセンスを取得していません | ユーザーがライセンスを失っているか、サービスから削除されています。 |
| デバイスが既に登録されています | 別のユーザーによってまだ登録されているデバイスで、ユーザーがポータル サイトを使用してデバイスを登録しようとしています。 |
| Intune にオンボードされていません | Intune のモバイル デバイス管理 (MDM) 機関が構成されていないときに、登録が試行されました。 |
| 承認に失敗しました | 古いバージョンのポータル サイトを使用して、登録が試行されました。 |
| デバイスがサポートされていません | デバイスが Intune 登録のための最小要件を満たしていません。 |
| 登録制限が満たされていません | この登録は、管理者が構成した登録制限によりブロックされました。 |
| Device version too low (デバイス バージョンが古すぎます) | 管理者がより新しいデバイス バージョンを必要とする登録制限を構成しました。 |
| デバイスのバージョンが新しすぎます | 管理者がより古いデバイス バージョンを必要とする登録制限を構成しました。 |
| デバイスを個人用として登録することはできません | 管理者が個人の登録をブロックする登録制限を構成し、失敗したデバイスが会社として事前定義されていませんでした。 |
| デバイス プラットフォームがブロックされました | 管理者がこのデバイスのプラットフォームをブロックする登録制限を構成しました。 |
| Bulk token expired (バルク トークンが期限切れです) | プロビジョニング パッケージのバルク トークンが期限切れです。 |
| Autopilot デバイスまたは詳細が見つかりません | 登録しようとしたときに Autopilot デバイスが見つかりませんでした。 |
| Autopilot プロファイルが見つからないか、割り当てられていません | デバイスにアクティブな Autopilot プロファイルがありません。 |
| Autopilot 登録方法は予期されていませんでした | デバイスが、許可されていない方法を使用して登録しようとしました。 |
| Autopilot デバイスが削除されました | 登録しようとしているデバイスは、このアカウントの Autopilot から削除されました。 |
| デバイス キャップに達しました | この登録は、管理者が構成したデバイス数の制限によりブロックされました。 |
| Apple オンボーディング | Intune 内で Apple MDM プッシュ証明書が見つからないか有効期限切れのため、この時点ですべての iOS デバイスの登録がブロックされました。 |
| デバイスが事前登録されていません | デバイスが会社として事前登録されておらず、個人のすべての登録が管理者によってブロックされました。 |
| 機能がサポートされていません | ユーザーが Intune の構成と互換性のない方法で登録を試行した可能性があります。 |

## <a name="collect-available-data-from-mobile-device"></a>モバイル デバイスから使用可能なデータを収集する

ユーザーのデバイスの問題のトラブルシューティングを行うときに、以下のリソースを使用してデバイスのデータを収集します。
- [IT 管理者に iOS の登録に関するエラーを送信する](/intune-user-help/send-errors-to-your-it-admin-ios)
- [詳細ログ記録を使用して会社のサポートがデバイスの問題を解決できるようにする](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)
- [USB ケーブルを使用して Android のログを会社のサポートに送信する](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
- [メールを使用して Android の診断データのログを IT 管理者に送信する](/intune-user-help/send-logs-to-your-it-admin-by-email-android)
- [IT 管理者に Android の登録に関するエラーを送信する](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)

## <a name="next-steps"></a>次の手順

ロール ベースの管理制御 (RBAC) の詳細を学習し、組織デバイス、モバイル アプリケーション管理、データ保護タスクにおけるロールを定義することができます。 詳細については、「[Intune でのロール ベースの管理制御 (RBAC)](/intune/role-based-access-control)」を参照してください。

Microsoft Intune の既知の問題について学習します。 詳細については、「[Microsoft Intune の既知の問題](/intune/known-issues)」を参照してください。

サポート チケットを作成し、必要なときにヘルプを表示する方法を学習します。 「[Microsoft Intune のサポートを受ける方法](/intune/get-support)」を参照してください。
