---
title: Microsoft Intune - Azure で iOS デバイスのコンプライアンス ポリシーを作成する | Microsoft Docs
description: iOS デバイスの Microsoft Intune のデバイス コンプライアンス ポリシーを作成して、電子メール アカウントの入力、脱獄されたデバイスの確認、最小および最大のオペレーティング システムの確認、およびパスワードの長さと非アクティブの状態のデバイスを含む、パスワードの制限の設定を行います。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 887f45cdc79aa5e45de3e8a1df5d12665d2ed8ab
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>Intune で iOS デバイス用のデバイス コンプライアンス ポリシーの追加

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune iOS デバイス コンプライアンス ポリシーでは、iOS デバイスが準拠する必要のあるルールと設定を定義します。 デバイスのコンプライアンス ポリシーと共に条件付きアクセスを使用すると、会社のリソースへのアクセスを許可したり、ブロックしたりできます。 コンプライアンス違反に対して、デバイス レポートを取得したり、是正措置を取ったりすることもできます。 デバイス コンプライアンス ポリシーは、Intune Azure Portal でプラットフォームごとに作成できます。 コンプライアンス ポリシーと、コンプライアンス ポリシーを作成する前に必要な前提条件については、「[Intune のデバイス コンプライアンス ポリシーの概要](device-compliance-get-started.md)」をご覧ください。

次の表では、条件付きアクセス ポリシーとコンプライアンス ポリシーを使用する場合に非準拠設定をどのように管理するかについて説明しています。

| **ポリシー設定** | **iOS 8.0 以降** |
| --- | --- |
| **PIN またはパスワードの構成** | 修復 |
| **デバイスの暗号化** | 修復 (PIN の設定による) |
| **脱獄またはルート化されたデバイス** | 検疫済み (設定ではありません)
| **電子メールのプロファイル** | 検疫済み |
|**最小 OS バージョン** | 検疫済み |
| **最大 OS バージョン** | 検疫済み |
| **Windows 正常性構成証明書** | 適用できません |

**修復** = デバイス オペレーティング システムによって準拠が強制されます  (たとえば、ユーザーは PIN を設定するように強制されます)。

**検疫済み** = デバイス オペレーティング システムによって準拠が強制されません  (たとえば、Android デバイスでは、ユーザーはデバイスの暗号化を強制されません)。デバイスが準拠していない場合、次のアクションが行われます。

- ユーザーに条件付きアクセス ポリシーを適用すると、デバイスがブロックされます。
- ポータル サイトは、コンプライアンスの問題をユーザーに通知します。

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Azure Portal でコンプライアンス ポリシーを作成する

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** の順に選択します。
4. 名前と説明を入力し、このポリシーを適用するプラットフォームを選択します。
5. **[設定]** を選択し、**[電子メール]**、**[デバイスのヘルス]**、**[デバイス プロパティ]**、および **[システム セキュリティ]** の設定を入力します。 終了したら、**[OK]** を選択します。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>ユーザー グループを割り当てる

コンプライアンス ポリシーをユーザーに割り当てるには、構成したポリシーを選択します。 既存のポリシーは、**[デバイスのポリシー準拠 - ポリシー]** ウィンドウで確認できます。

1. ユーザーに割り当てるポリシーを選択し、**[割り当て]** を選択します。 ウィンドウが開くので、**Azure Active Directory セキュリティ グループ**を選択してポリシーに割り当てることができます。
2. **[選択したグループ]** を選択すると、ウィンドウが開いて Azure AD セキュリティ グループが表示されます。  **[保存]** を選択すると、ポリシーがユーザーに展開されます。

ポリシーがユーザーに適用されました。  ポリシーの対象となっているユーザーが使用しているデバイスは、コンプライアンスが評価されます。

<!---## Compliance policy settings--->

## <a name="email"></a>電子メール

- **電子メール アカウントを Intune で管理する**: このオプションを **[はい]** に設定すると、デバイスは、デバイスに展開された電子メール プロファイルを使用する必要があります。 デバイスは、次の状況で非準拠とみなされます。
  - 電子メール プロファイルが、コンプライアンス ポリシーの対象となるユーザー グループ以外のユーザー グループに展開されている。
  - デバイスに展開された Intune 電子メール プロファイルと一致するメール アカウントが、ユーザーによってデバイスに既にセットアップされている。 Intune では、ユーザーがプロビジョニングしたプロファイルを上書きできないので、結果としてそのプロファイルを管理できません。 コンプライアンスを確保するには、ユーザーが既存の電子メール設定を削除する必要があります。 これにより、Intune は管理対象の電子メール プロファイルをインストールできるようになります。
- **Intune によって管理される必要のある電子メール プロファイルを選択する**: **[電子メールアカウントは Intune によって管理される必要がある]** が設定されている場合は、**[選択]** を選択して Intune 電子メール プロファイルを指定します。 電子メール プロファイルは、デバイス上に存在する必要があります。

電子メール プロファイルの詳細については、「[Microsoft Intune で電子メール プロファイルを使用して会社の電子メールへのアクセスを構成する](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)」を参照してください。

## <a name="device-health"></a>Device health

- **脱獄されたデバイス**: この設定を有効にすると、脱獄されたデバイスは非準拠になります。
- **デバイスは、デバイス脅威レベル以下であることが必要**: 非準拠としてデバイスをマークする最大脅威レベルを選択します。 たとえば、脅威レベルを **[中]** に設定すると、中、低、または安全な状態のデバイスが準拠になります。 脅威レベルが高いデバイスは非準拠になります。

## <a name="device-properties"></a>デバイスのプロパティ

- **必要な最小 OS バージョン**: デバイスが最小 OS バージョンの要件を満たしていない場合、非準拠として報告されます。 アップグレード方法に関する情報のリンクが表示されます。 ユーザーは、そのデバイスのアップグレードを行うことを選択できます。 その後、会社のリソースにアクセスできます。
- **許可される最大 OS バージョン**: ルールに指定された OS バージョンより新しいバージョンの OS がデバイスで使用されている場合、会社のリソースへのアクセスがブロックされます。 そして、IT 管理者に問い合わせることをユーザーに促すメッセージが表示されます。対象の OS バージョンを許可するようにルールが変更されるまで、このデバイスを使用して会社のリソースにアクセスすることはできません。

## <a name="system-security"></a>システム セキュリティ

### <a name="password"></a>パスワード

> [!NOTE]
> iOS デバイスにコンプライアンスまたは構成ポリシーが適用されると、ユーザーは 15 分ごとにパスコードを設定するように求められます。 パスコードを設定するまで継続してユーザーは入力を求められます。

- **[モバイル デバイスのロック解除にパスワードを必要とする]**: デバイスにアクセスするユーザーにパスワードを入力するよう求める場合は、これを **[はい]** に設定します。 パスワードを使用する iOS デバイスは暗号化されます。
- **[単純なパスワード]**: **[はい]** に設定すると、ユーザーは **1234** や **1111** のようなパスワードを作成できます。
- **[パスワードの最小文字数]**: パスワードに必要な数字または文字の最小数を入力します。
- **[必要なパスワードの種類]**: ユーザーが **[英数字]** パスワードまたは **[数字]** パスワードのどちらを作成する必要があるかを入力します。
- **[パスワードに使用する英数字以外の文字数]**: パスワードに含める必要がある特殊文字 (&、#、%、! など) の最小数を指定します。

    大きな数値を設定すると、ユーザーはより複雑なパスワードを作成する必要があります。

- **[デバイスの画面がロックされるまでの非アクティブな最大分数]**: ユーザーがパスワードを再入力しなければならなくなるまでのアイドル時間を入力します。
- **[パスワードの有効期限 (日数)]**: 新しいパスワードの作成が必要となるまでのパスワードの有効日数を選択します。
- **[再利用できないようにする前のパスワードの数]**: 何回前までのパスワードを使用できないようにするかを入力します。

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
