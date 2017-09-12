---
title: "iOS 用のコンプライアンス ポリシーの作成方法"
titleSuffix: Azure portal
description: "iOS デバイス用のコンプライアンス ポリシーの作成方法について説明します。\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3b0fdb06b072c325d30b3e5ee72f1982c5f61849
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-create-a-device-compliance-policy-for-ios-devices-in-intune"></a>Intune で iOS デバイス用のデバイス コンプライアンス ポリシーを作成する方法


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

コンプライアンス ポリシーは、プラットフォームごとに作成されます。  また、Azure Portal でコンプライアンス ポリシーを作成できます。 コンプライアンス ポリシーの詳細については、[デバイスのコンプライアンス](device-compliance.md)に関するトピックを参照してください。 コンプライアンス ポリシーを作成する前に対応する必要がある前提条件については、[デバイス コンプライアンスの概要](device-compliance-get-started.md)に関するトピックを参照してください。

次の表では、条件付きアクセス ポリシーとコンプライアンス ポリシーを使用する場合に非準拠設定をどのように管理するかについて説明しています。

-------------------------------


| **ポリシー設定** | **iOS 8.0 以降** |
| --- | --- |
| **PIN またはパスワードの構成** | 修復 |   
| **デバイスの暗号化** | 修復 (PIN の設定による) |
| **脱獄またはルート化されたデバイス** | 検疫済み (設定ではありません)
| **電子メールのプロファイル** | 検疫済み |
|**最小 OS バージョン** | 検疫済み |
| **最大 OS バージョン** | 検疫済み |  
| **Windows 正常性構成証明書** | 該当なし |  
----------------------------


**修復** = デバイス オペレーティング システムによって準拠が強制されます  (たとえば、ユーザーは PIN を設定するように強制されます)。

**検疫済み** = デバイス オペレーティング システムによって準拠が強制されません  (たとえば、Android デバイスでは、ユーザーはデバイスの暗号化を強制されません)。デバイスが準拠していない場合、次のアクションが行われます。

- ユーザーに条件付きアクセス ポリシーを適用すると、デバイスがブロックされます。
- ポータル サイトは、コンプライアンスの問題をユーザーに通知します。

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Azure Portal でコンプライアンス ポリシーを作成する

1. **[Intune]** ブレードで、**[デバイス コンプライアンスの設定]** を選択します。 **[管理]** で **[All device compliance policies (すべてのデバイス コンプライアンス ポリシー)]**、**[作成]** の順に選択します。
2. 名前と説明を入力し、このポリシーを適用するプラットフォームを選択します。
3. **[コンプライアンス要件]** を選択し、ここで **[セキュリティ]**、**[デバイスのヘルス]**、**[デバイスのプロパティ]** の設定を指定します。終了したら、**[OK]** を選択します。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>ユーザー グループを割り当てる

コンプライアンス ポリシーをユーザーに割り当てるには、構成したポリシーを選択します。 既存のポリシーは、**[コンプライアンス ポリシー]** ブレードで確認できます。

1. ユーザーに割り当てるポリシーを選択し、**[割り当て]** を選択します。 これにより表示されたブレードで、**[Azure Active Directory セキュリティ グループ]** を選択し、ポリシーに割り当てることができます。
2. **[グループの選択]** を選択すると、ブレードが開き、Azure AD セキュリティ グループが表示されます。  **[選択]** を選択すると、ポリシーがユーザーに展開されます。

ポリシーがユーザーに適用されました。  ポリシーの対象となっているユーザーが使用しているデバイスは、コンプライアンスについて評価されます。

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>システム セキュリティ設定

### <a name="password"></a>パスワード

- **[モバイル デバイスのロック解除にパスワードを必要とする]**: デバイスにアクセスするユーザーにパスワードを入力するよう求める場合は、**[はい]** に設定します。 パスワードを使用する iOS デバイスは暗号化されます。
- **[単純なパスワードを許可する]**: これを **[はい]** に設定すると、ユーザーは単純なパスワード (**1234**、**1111** など) を作成できます。
- **[パスワードの最小文字数]**: パスワードに必要な数字または文字の最小数を指定します。
- **[必要なパスワードの種類]**: ユーザーが **[英数字]** パスワードまたは **[数字]** パスワードのどちらを作成する必要があるかを指定します。
- **[文字セットの最小数]**: **[必要なパスワードの種類]** を **[英数字]** に設定した場合、この設定を使用して、パスワードに含める必要がある文字セットの最小数を指定します。 次の 4 つの文字セットがあります。
  - 小文字
  - 大文字
  - 記号
  - 数字

大きな数値を設定すると、ユーザーはより複雑なパスワードを作成する必要があります。

iOS デバイスの場合、この設定はパスワードに含める必要がある特殊文字 (たとえば、**!** 、**#**、**&amp;**) の数を示します。

- **[デバイスの画面がロックされるまでの非アクティブな時間 (分)]**: ユーザーがパスワードを再入力しなければならなくなるまでのアイドル時間を指定します。
- **[パスワードの有効期限 (日数)]**: 新しいパスワードの作成が必要となるまでのパスワードの有効日数を選択します。
- **[パスワードの履歴を記憶する]**: この設定を **[前のパスワードの再利用を防止]** と組み合わせて使用することで、以前使用されていたパスワードをユーザーが作成することを制限します。
- **[前のパスワードの再利用を防止]**: **[パスワードの履歴を保存する]** が選択されている場合は、再利用できない、以前に使用されていたパスワードの数を指定します。
- **[デバイスがアイドル状態から戻るときにパスワードを必須とする]**: この設定は、**[デバイスの画面がロックされるまでの非アクティブな時間 (分)]** 設定と組み合わせて使用します。 ユーザーは、**[デバイスの画面がロックされるまでの非アクティブな時間 (分)]** 設定で指定された時間非アクティブの状態が続いたデバイスにアクセスしようとすると、パスワードを入力するように求められます。

### <a name="email-profile"></a>電子メールのプロファイル

- **[電子メール アカウントを Intune で管理する]**: このオプションを **[はい]** に設定すると、デバイスは、デバイスに展開された電子メール プロファイルを使用する必要があります。 デバイスは、次の状況で非準拠とみなされます。
  - 電子メール プロファイルが、コンプライアンス ポリシーの対象となるユーザー グループ以外のユーザー グループに展開されている。
  - デバイスに展開された Intune 電子メール プロファイルと一致するメール アカウントが、ユーザーによってデバイスに既にセットアップされている。 Intune では、ユーザーがプロビジョニングしたプロファイルを上書きできないので、結果としてそのプロファイルを管理できません。 コンプライアンスを確保するには、ユーザーが既存の電子メール設定を削除する必要があります。 これにより、Intune は管理対象の電子メール プロファイルをインストールできるようになります。
- **[Intune によって管理される必要のある電子メール プロファイルを選択する]**: **[電子メールアカウントは Intune によって管理される必要がある]** が設定されている場合は、**[選択]** を選択して Intune 電子メール プロファイルを指定します。 電子メール プロファイルは、デバイス上に存在する必要があります。

電子メール プロファイルの詳細については、「[Microsoft Intune で電子メール プロファイルを使用して会社の電子メールへのアクセスを構成する](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)」を参照してください。

## <a name="device-health-settings"></a>デバイスのヘルスの設定

- **[デバイスの脱獄または root 化を認めない]**: この設定を有効にした場合、脱獄デバイスは準拠しません。

## <a name="device-properties"></a>デバイスのプロパティ

- **[必要な最小 OS バージョン]**: デバイスが最小 OS バージョンの要件を満たしていない場合、非準拠として報告されます。 アップグレード方法に関する情報のリンクが表示されます。 ユーザーは、そのデバイスのアップグレードを行うことを選択できます。 その後、会社のリソースにアクセスできます。
- **[許可される最大 OS バージョン]**: ルールに指定された OS バージョンより新しいバージョンの OS がデバイスで使用されている場合、会社のリソースへのアクセスがブロックされ、IT 管理者に問い合わせることをユーザーに促すメッセージが表示されます。対象の OS バージョンを許可するようにルールが変更されるまで、このデバイスを使用して会社のリソースへのアクセスすることはできません。

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
