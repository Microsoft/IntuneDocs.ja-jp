---
title: "Android for Work 用のコンプライアンス ポリシーの作成"
titleSuffix: Azure portal
description: "Android for Work デバイス用のコンプライアンス ポリシーの作成方法について説明します。\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d9a01b88708dd077f15b6e23536667f7ee752e67
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-create-a-device-compliance-policy-for-android-for-work-devices-in-intune"></a>Intune で Android for Work デバイス用のデバイス コンプライアンス ポリシーを作成する方法


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

コンプライアンス ポリシーは、プラットフォームごとに作成されます。  また、Azure Portal でコンプライアンス ポリシーを作成できます。 コンプライアンス ポリシーの詳細については、[デバイスのコンプライアンス](device-compliance.md)に関するトピックを参照してください。 コンプライアンス ポリシーを作成する前に対応する必要がある前提条件については、[デバイス コンプライアンスの概要](device-compliance-get-started.md)に関するトピックを参照してください。

次の表では、条件付きアクセス ポリシーとコンプライアンス ポリシーを使用する場合に非準拠設定をどのように管理するかについて説明しています。

--------------------------

|**ポリシー設定**| **Android for Work** |
| --- | --- |
| **PIN またはパスワードの構成** |  検疫済み |
| **デバイスの暗号化** |  検疫済み |
| **脱獄またはルート化されたデバイス** | 検疫済み (設定ではありません) |
| **電子メールのプロファイル** | 該当なし |
| **最小 OS バージョン** | 検疫済み |
| **最大 OS バージョン** | 検疫済み |
| **Windows 正常性構成証明書** |該当なし |

**修復** = デバイス オペレーティング システムによって準拠が強制されます  (たとえば、ユーザーは PIN を設定するように強制されます)。+

**検疫済み** = デバイス オペレーティング システムによって準拠が強制されません  (たとえば、Android デバイスでは、ユーザーはデバイスの暗号化を強制されません)。デバイスが準拠していない場合、次のアクションが行われます。

- ユーザーに条件付きアクセス ポリシーを適用すると、デバイスがブロックされます。
- ポータル サイトは、コンプライアンスの問題をユーザーに通知します。

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Azure Portal でコンプライアンス ポリシーを作成する

1. **[Intune]** ブレードで、**[デバイス コンプライアンスの設定]** を選択します。 **[管理]** で **[All device compliance policies (すべてのデバイス コンプライアンス ポリシー)]**、**[作成]** の順に選択します。
2. 名前と説明を入力し、このポリシーを適用するプラットフォームを選択します。
3. **[コンプライアンス要件]** を選択し、ここで **[セキュリティ]**、**[デバイスのヘルス]**、**[デバイスのプロパティ]** の設定を指定します。終了したら、**[OK]** を選択します。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>ユーザー グループを割り当てる

コンプライアンス ポリシーをユーザーに割り当てるには、構成したポリシーを選択します。 既存のポリシーは、**[コンプライアンス ポリシー]** ブレードで確認できます。

1. ユーザーに割り当てるポリシーを選択し、**[割り当て]** を選択します。 これにより表示されたブレードで、**[Azure Active Directory セキュリティ グループ]** を選択し、ポリシーに割り当てることができます。
2. **[グループの選択]** を選択すると、ブレードが開き、Azure AD セキュリティ グループが表示されます。  **[選択]** を選択すると、ポリシーがユーザーに展開されます。

ポリシーがユーザーに適用されました。  ポリシーの対象となっているユーザーが使用しているデバイスは、コンプライアンスについて評価されます。

<!--- ##  Compliance policy settings--->

## <a name="system-security-settings"></a>システム セキュリティ設定

### <a name="password"></a>パスワード

- **モバイル デバイスのロック解除にパスワードを必要とする:** デバイスにアクセスするユーザーにパスワードを入力するよう求める場合は、**[はい]** に設定します。
- **[パスワードの最小文字数]:** パスワードに含まれている必要がある数字または文字の最小数を指定します。
- **パスワードの品質:** 指定したパスワード要件が、デバイスに構成されているかどうかをこの設定で検出します。 この設定を有効にすると、Android デバイスで特定のパスワード要件を構成することが必須になります。 次の中から選択します。
  - **低レベルのバイオメトリック セキュリティ**
  - **必須**
  - **最小数の数字**
  - **最小数の英字**
  - **最小数の英数字**
  - **英数字と記号**
- **[デバイスの画面がロックされるまでの非アクティブな時間 (分)]:** ユーザーがパスワードを再入力しなければならなくなるまでのアイドル時間を指定します。
- **[パスワードの有効期限 (日数)]:** 新しいパスワードの作成が必要となるまでのユーザーのパスワードの有効日数を選択します。
- **パスワードの履歴を記憶する:** この設定を **[前のパスワードの再利用を防止]** と組み合わせて使用することで、以前使用されていたパスワードをユーザーが作成することを制限します。
- **前のパスワードの再利用を防止:** **[パスワードの履歴を保存する]** が選択されている場合は、再利用できない、以前に使用されていたパスワードの数を指定します。
- **デバイスがアイドル状態から戻るときにパスワードを必須とする:** この設定は、**[デバイスの画面がロックされるまでの非アクティブな時間 (分)]** 設定と組み合わせて使用する必要があります。 エンドユーザーは、**[デバイスの画面がロックされるまでの非アクティブな時間 (分)]** 設定で指定された時間非アクティブの状態が続いたデバイスにアクセスしようとすると、パスワードを入力するように求められます。


### <a name="encryption"></a>暗号化

- **モバイル デバイスで暗号化を必要とする:** Android for Work デバイスは暗号化が適用されるので、この設定を構成する必要はありません。


## <a name="device-health-and-security-settings"></a>デバイスの正常性とセキュリティ設定

- **デバイスの脱獄または root 化を認めない:** この設定を有効にした場合、脱獄デバイスは非準拠として評価されます。
- **デバイスで提供元不明のアプリのインストールを禁止することを必須にする:** Android for Work デバイスでは、不明なソースからのインストールが常に制限されるので、この設定を構成する必要はありません。 。
- **[USB デバッグの無効化を必須にする]**: Android for Work デバイスでは、USB デバッグは無効にされているので、この設定を構成する必要はありません。
- **最低限の Android セキュリティ パッチ レベル**: この設定を使用して、Android の修正プログラムの最小レベルを指定します。 修正プログラムがこのレベルに達していないデバイスは非対応になります。 日付は YYYY-MM-DD の形式で指定する必要があります。
- **[デバイス脅威保護を有効にすることを必須とする]**: この設定は、Lookout MTP ソリューションからのリスク評価をコンプライアンスの条件とする場合に使用します。 最大許容脅威レベルとして次のいずれかを選択します。
  - **[なし (セキュリティ保護)]**: これはセキュリティ上最も安全です。 デバイスにはいかなる脅威も存在できないことを意味します。 デバイスで何らかのレベルの脅威が検出された場合、非準拠と評価されます。
  - **[低]**: 存在する脅威が低レベルの場合のみ、デバイスは準拠として評価されます。 低レベルより高い脅威が存在する場合、デバイスは非準拠状態になります。
  - **[中]**: デバイスに存在する脅威が低レベルまたは中レベルの場合、デバイスは準拠として評価されます。 デバイスで高レベルの脅威が検出された場合は、非準拠と判定されます。
  - **[高]**: 最も安全性の低い状態です。 基本的にすべての脅威レベルが許容されるため、通常、このソリューションはレポートを目的とした場合にのみ役に立ちます。

詳細については、「[コンプライアンス ポリシーでデバイスの脅威防御ルールを有効にする](https://docs.microsoft.com/intune-classic/deploy-use/enable-device-threat-protection-rule-in-compliance-policy)」を参照してください。

## <a name="device-property-settings"></a>デバイスのプロパティの設定

- **必要な最小 OS バージョン:** デバイスが最小 OS バージョンの要件を満たしていない場合、非準拠として報告されます。 アップグレード方法に関する情報のリンクが表示されます。 エンド ユーザーは、デバイスのアップグレードを行うことを選択できます。アップグレード後は、会社のリソースにアクセスできます。
- **許可される最大 OS バージョン:** ルールに指定された OS バージョンより新しいバージョンの OS がデバイスで使用されている場合、会社のリソースへのアクセスがブロックされ、IT 管理者に問い合わせることをユーザーに促すメッセージが表示されます。対象の OS バージョンを許可するようにルールが変更されるまで、このデバイスを使用して会社のリソースへのアクセスすることはできません。

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
