---
title: Microsoft Intune - Azure で iOS デバイスのコンプライアンス ポリシーを作成する | Microsoft Docs
description: iOS デバイスの Microsoft Intune のデバイス コンプライアンス ポリシーを作成または構成して、電子メール アカウントの入力、脱獄されたデバイスの確認、最小および最大のオペレーティング システムの確認、およびパスワードの長さと非アクティブの状態のデバイスを含む、パスワードの制限の設定を行います。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6f711a6bec9be0ac1fd94183931070f9988d49e3
ms.sourcegitcommit: 2773f388f50654366197a95a6838306f70fc18b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>Intune で iOS デバイス用のデバイス コンプライアンス ポリシーの追加

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune iOS デバイス コンプライアンス ポリシーでは、iOS デバイスが準拠する必要のあるルールと設定を定義します。 デバイスのコンプライアンス ポリシーと共に条件付きアクセスを使用すると、会社のリソースへのアクセスを許可したり、ブロックしたりできます。 コンプライアンス違反に対して、デバイス レポートを取得したり、是正措置を取ったりすることもできます。 デバイス コンプライアンス ポリシーは、Intune Azure Portal でプラットフォームごとに作成できます。 コンプライアンス ポリシーの詳細については、[デバイス コンプライアンスの概要](device-compliance-get-started.md)に関するページを参照してください。

次の表では、条件付きアクセス ポリシーとコンプライアンス ポリシーを使用する場合に非準拠設定をどのように管理するかについて説明しています。

---------------------------

| **ポリシー設定** | **iOS 8.0 以降** |
| --- | --- |
| **PIN またはパスワードの構成** | 修復 |
| **デバイスの暗号化** | 修復 (PIN の設定による) |
| **脱獄またはルート化されたデバイス** | 検疫済み (設定ではありません)
| **電子メールのプロファイル** | 検疫済み |
|**最小 OS バージョン** | 検疫済み |
| **最大 OS バージョン** | 検疫済み |
| **Windows 正常性構成証明書** | 適用できません |

---------------------------

**修復** = デバイス オペレーティング システムによって準拠が強制されます  (たとえば、ユーザーは PIN を設定するように強制されます)。

**検疫済み** = デバイス オペレーティング システムによって準拠が強制されません  (たとえば、Android デバイスでは、ユーザーはデバイスの暗号化を強制されません)。デバイスが準拠していない場合、次のアクションが行われます。

- ユーザーに条件付きアクセス ポリシーを適用すると、デバイスがブロックされます。
- ポータル サイトは、コンプライアンスの問題をユーザーに通知します。

## <a name="create-a-device-compliance-policy"></a>デバイス コンプライアンス ポリシーの作成

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. **[プラットフォーム]** で **[iOS]** を選択します。 **[設定]** を選択し、**[電子メール]**、**[デバイスのヘルス]**、**[デバイス プロパティ]**、および **[システム セキュリティ]** の設定を入力します。 完了したら、**[OK]**、**[作成]** の順に選択します。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="email"></a>電子メール

- **[モバイル デバイスは管理されているメール プロファイルを持つことが必要]**: これを [必須] に設定すると、電子メール プロファイルが Intune で管理されていないデバイスは非準拠と見なされます。 デバイスが誤って対象とされている場合、またはユーザーがデバイス上で電子メール アカウントを手動で設定した場合、デバイスには管理されたメール プロファイルが存在しない場合があります。

  デバイスは、次の状況で非準拠とみなされます。
  - 電子メール プロファイルが、コンプライアンス ポリシーの対象となるユーザー グループ以外のユーザー グループに展開されている。
  - デバイスに展開された Intune 電子メール プロファイルと一致するメール アカウントが、ユーザーによってデバイスに既にセットアップされている。 Intune では、ユーザーがプロビジョニングしたプロファイルを上書きできないので、結果としてそのプロファイルを管理できません。 コンプライアンスを確保するには、ユーザーが既存の電子メール設定を削除する必要があります。 これにより、Intune は管理対象の電子メール プロファイルをインストールできるようになります。

- **Intune によって管理される必要のある電子メール プロファイルを選択する**: **[電子メールアカウントは Intune によって管理される必要がある]** が設定されている場合は、**[選択]** を選択して Intune 電子メール プロファイルを指定します。 電子メール プロファイルは、デバイス上に存在する必要があります。

電子メール プロファイルの詳細については、「[Microsoft Intune で電子メール プロファイルを使用して会社の電子メールへのアクセスを構成する](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)」を参照してください。

## <a name="device-health"></a>Device health

- **脱獄されたデバイス**: この設定を有効にすると、脱獄されたデバイスは非準拠になります。
- **[デバイスは、デバイス脅威レベル以下であることが必要]** (iOS 8.0 以降): 非準拠としてデバイスをマークする最大脅威レベルを選択します。 この脅威レベルを超えるデバイスは非準拠としてマークされます。
  - **[セキュリティ保護]**: デバイスにはいかなる脅威も存在してはならないので、これはセキュリティ上最も安全なオプションです。 デバイスで何らかのレベルの脅威が検出された場合、非準拠と評価されます。
  - **[低]**: 存在する脅威が低レベルの場合のみ、デバイスは準拠として評価されます。 低レベルより高い脅威が存在する場合、デバイスは非準拠状態になります。
  - **[中]**: デバイスに存在する脅威が低レベルまたは中レベルの場合、デバイスは準拠として評価されます。 デバイスで高レベルの脅威が検出された場合は、非準拠と判定されます。
  - **[高]**: 最も安全性の低いオプションであり、すべての脅威レベルが許容されます。 このソリューションをレポート目的のみで使用した場合、役立つ場合があります。

## <a name="device-properties"></a>デバイスのプロパティ

- **必要な最小 OS バージョン**: デバイスが最小 OS バージョンの要件を満たしていない場合、非準拠として報告されます。 アップグレード方法に関する情報のリンクが表示されます。 ユーザーは、そのデバイスのアップグレードを行うことを選択できます。 その後、会社のリソースにアクセスできます。
- **許可される最大 OS バージョン**: ルールに指定された OS バージョンより新しいバージョンの OS がデバイスで使用されている場合、会社のリソースへのアクセスがブロックされます。 そして、IT 管理者に問い合わせることをユーザーに促すメッセージが表示されます。対象の OS バージョンを許可するようにルールが変更されるまで、このデバイスを使用して会社のリソースにアクセスすることはできません。

## <a name="system-security"></a>システム セキュリティ

### <a name="password"></a>パスワード

> [!NOTE]
> iOS デバイスにコンプライアンスまたは構成ポリシーが適用されると、ユーザーは 15 分ごとにパスコードを設定するように求められます。 パスコードを設定するまで継続してユーザーは入力を求められます。

- **[モバイル デバイスのロック解除にパスワードを必要とする]**: デバイスにアクセスするユーザーにパスワードを入力するよう**求めます**。 パスワードを使用する iOS デバイスは暗号化されます。
- **[単純なパスワード]**: **[ブロック]** に設定すると、ユーザーは単純なパスワード (**1234**、**1111** など) を作成できません。 **[未構成]** に設定すると、ユーザーは **1234** や **1111** などのパスワードを作成できます。
- **[パスワードの最小文字数]**: パスワードに必要な数字または文字の最小数を入力します。
- **[必要なパスワードの種類]**: パスワードの内容を**数字**のみにするかどうか、あるいは数字とその他の文字との組み合わせ (**英数字**) にするかどうかを選択します。
- **[パスワードに使用する英数字以外の文字数]**: パスワードに含める必要がある特殊文字 (&、#、%、! など) の最小数を指定します。

    大きな数値を設定すると、ユーザーはより複雑なパスワードを作成する必要があります。

- **[デバイスの画面がロックされるまでの非アクティブな最大分数]**: ユーザーがパスワードを再入力しなければならなくなるまでのアイドル時間を入力します。
- **[パスワードの有効期限 (日数)]**: 新しいパスワードの作成が必要となるまでのパスワードの有効日数を選択します。
- **[再利用できないようにする前のパスワードの数]**: 何回前までのパスワードを使用できないようにするかを入力します。

## <a name="assign-user-groups"></a>ユーザー グループを割り当てる

1. 構成済みのポリシーを選択します。 既存のポリシーは、**[デバイスのポリシー準拠]** > **[ポリシー]** で確認できます。
2. ポリシーを選択し、**[割り当て]** を選択します。 Azure Active Directory (AD) のセキュリティ グループは、含めることも除外することもできます。
3. **[選択したグループ]** を選択すると、Azure AD セキュリティ グループが表示されます。 このポリシーで適用するユーザー グループを選択し、**[保存]** を選択してユーザーにポリシーを展開します。

ポリシーがユーザーに適用されました。 ポリシーの対象となっているユーザーが使用しているデバイスは、コンプライアンスが評価されます。

## <a name="next-steps"></a>次の手順
[非準拠デバイスに対する自動メール送信とアクションの追加](actions-for-noncompliance.md)  
[Intune デバイスのコンプライアンス対応ポリシーの監視](compliance-policy-monitor.md)