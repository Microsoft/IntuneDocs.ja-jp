---
title: Microsoft Intune で Android 仕事用プロファイルのコンプライアンス ポリシーを作成する - Azure | Microsoft Docs
description: Android 仕事用プロファイル デバイス用の Microsoft Intune デバイス コンプライアンス ポリシーを作成または構成します。 脱獄されたデバイスを許可し、許容可能な脅威レベルを設定し、Google Play を確認し、オペレーティング システムの最小および最大バージョンを入力し、パスワードの要件を選択し、サイドローディング アプリケーションを許可します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0c7f1c7c47f2fa4c950cbffeaf8fe274fe239a63
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828161"
---
# <a name="add-a-device-compliance-policy-for-android-work-profile-devices-in-intune"></a>Intune で Android 仕事用プロファイル デバイス用のデバイス コンプライアンス ポリシーを追加する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android 仕事用プロファイル デバイスの Intune デバイス コンプライアンス ポリシーでは、準拠していると見なされるためにこれらのデバイスが満たす必要のあるルールと設定が指定されます。 このようなポリシーを条件付きアクセスと一緒に使用することにより、会社のリソースへのアクセスを許可または阻止することができます。 コンプライアンス違反に対して、デバイス レポートを取得したり、是正措置を取ったりすることもできます。 デバイス コンプライアンス ポリシーは、Intune Azure Portal で各種のプラットフォームに対して作成します。 コンプライアンス ポリシーの詳細については、[デバイス コンプライアンスの概要](device-compliance-get-started.md)に関するページを参照してください。

次の表では、条件付きアクセス ポリシーとコンプライアンス ポリシーを使用する場合に非準拠設定をどのように管理するかについて説明しています。

--------------------------

|**ポリシー設定**| **Android 仕事用プロファイル** |
| --- | --- |
| **PIN またはパスワードの構成** |  検疫済み |
| **デバイスの暗号化** |  検疫済み |
| **脱獄またはルート化されたデバイス** | 検疫済み (設定ではありません) |
| **電子メールのプロファイル** | 適用できません |
| **最小 OS バージョン** | 検疫済み |
| **最大 OS バージョン** | 検疫済み |
| **Windows 正常性構成証明書** |適用できません |

**修復** = デバイス オペレーティング システムによって準拠が強制されます  (たとえば、ユーザーは PIN を設定するように強制されます)。+

**検疫済み** = デバイス オペレーティング システムによって準拠が強制されません  (たとえば、Android デバイスでは、ユーザーはデバイスの暗号化を強制されません)。デバイスが準拠していない場合、次のアクションが行われます。

- ユーザーに条件付きアクセス ポリシーを適用すると、デバイスがブロックされます。
- ポータル サイトは、コンプライアンスの問題をユーザーに通知します。

## <a name="create-a-device-compliance-policy"></a>デバイス コンプライアンス ポリシーの作成

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. **[プラットフォーム]** で、**[Android エンタープライズ]** を選択します。 **[設定]** を選択し、**[デバイスのヘルス]**、**[デバイス プロパティ]**、および **[システム セキュリティ]** の設定を入力します。 終了したら、**[OK]**、**[作成]** の順に選択します。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="device-health"></a>Device health

- **[ルート化されたデバイス]**: この設定を有効にすると、脱獄されたデバイスは非準拠として評価されます。
- **[デバイスは、デバイス脅威レベル以下であることが必要]**: この設定は、Lookout MTP ソリューションからのリスク評価をコンプライアンスの条件とする場合に使用します。 許容される脅威の最大レベルを選択します。
  - **[セキュリティ保護]**: これはセキュリティ上最も安全なオプションであり、デバイスにはいかなる脅威も存在してはならないことを意味します。 デバイスで何らかのレベルの脅威が検出された場合、非準拠と評価されます。
  - **[低]**: 存在する脅威が低レベルの場合のみ、デバイスは準拠として評価されます。 低レベルより高い脅威が存在する場合、デバイスは非準拠状態になります。
  - **[中]**: デバイスに存在する脅威が低レベルまたは中レベルの場合、デバイスは準拠として評価されます。 デバイスで高レベルの脅威が検出された場合は、非準拠と判定されます。
  - **[高]**: すべての脅威レベルが許容されるため、最も安全性の低いオプションとなります。 このソリューションをレポート目的のみで使用した場合、役立つ場合があります。
- **[Google Play サービスが構成されています]**: Google Play 開発者サービス アプリがインストールされ、有効になっている必要があります。 Google Play 開発者サービスはセキュリティ更新プログラムを許可し、Google の認定デバイスの多くのセキュリティ機能に対してベースレベルの依存関係となっています。
- **[最新のセキュリティ プロバイダー]**: 最新のセキュリティ プロバイダーが既知の脆弱性からデバイスを保護できるようになっている必要があります。
- **[SafetyNet デバイス構成証明]**: 満たす必要がある [SafetyNet デバイス構成証明](https://developer.android.com/training/safetynet/attestation.html)のレベルを入力します。 次のようなオプションがあります。
  - **未構成**
  - **基本的な整合性のチェック**
  - **基本的な整合性と認定デバイスのチェック**

#### <a name="threat-scan-on-apps"></a>アプリの脅威のスキャン

Android 仕事用プロファイルがあるデバイスでは、**[アプリの脅威のスキャン]** 設定は構成ポリシー設定として存在しています。 管理者はデバイスの設定を有効にすることができます。

企業で、Android 作業プロファイルを使用する場合は、登録されているデバイスに対して **[アプリの脅威のスキャン]** を有効にできます。 デバイス プロファイルを作成し、システム セキュリティ設定を要求します。 詳細については、「[Intune での Work デバイスの制限設定](device-restrictions-android-for-work.md)」をご覧ください。

## <a name="device-property-settings"></a>デバイスのプロパティの設定

- **[最小 OS バージョン]**: デバイスが最小 OS バージョンの要件を満たしていない場合、非準拠として報告されます。 アップグレード方法に関する情報のリンクが表示されます。 エンド ユーザーは、デバイスのアップグレードを行うことを選択できます。アップグレード後は、会社のリソースにアクセスできます。
- **[最大 OS バージョン]**: ルールに指定された OS バージョンより新しいバージョンの OS がデバイスで使用されている場合、会社のリソースへのアクセスがブロックされます。 さらに、IT 管理者に問い合わせることをユーザーに促すメッセージが表示されます。対象の OS バージョンを許可するようにルールが変更されるまで、このデバイスを使用して会社のリソースにアクセスすることはできません。

## <a name="system-security-settings"></a>システム セキュリティ設定

### <a name="password"></a>パスワード

- **[モバイル デバイスのロック解除にパスワードを必要とする]**: デバイスにアクセスするユーザーにパスワードを入力するよう**求めます**。
- **[パスワードの最小文字数]**: ユーザーのパスワードに必要な数字または文字の最小数を入力します。
- **[必要なパスワードの種類]**: パスワードの内容を数字のみにするか、または数字と他の文字の組み合わせにするかを選択します。 次の中から選択します。
  - **デバイスの既定値**
  - **低レベルのバイオメトリック セキュリティ**
  - **最小数の数字**
  - **数値複素数**
  - **最小数の英字**
  - **最小数の英数字**
  - **英数字と記号を使用する**
- **[デバイスの画面がロックされるまでの非アクティブな最大分数]**: ユーザーがパスワードを再入力しなければならなくなるまでのアイドル時間を入力します。
- **[パスワードの有効期限 (日数)]**: 新しいパスワードの作成が必要となるまでのパスワードの有効日数を選択します。
- **[再使用を禁止するパスワード世代数]**: 再使用できないパスワードの世代数を入力します。 この設定を使用して、以前に使用されたことのあるパスワードの作成を制限するかどうかを指定します。

### <a name="encryption"></a>暗号化

- **モバイル デバイスで暗号化を必要とする:** Android 仕事用プロファイル デバイスは暗号化が適用されるので、この設定を構成する必要はありません。

### <a name="device-security"></a>［デバイス セキュリティ］

- **[提供元不明のアプリをブロックする]**: Android 仕事用プロファイル デバイスでは、提供元不明のアプリのインストールは常に制限されるため、この設定を構成する必要はありません。
- **[ポータル サイト アプリのランタイム整合性]**: ポータル サイト アプリの既定のランタイム環境がインストールされているかどうか、ポータル サイト アプリが適切に署名されているかどうか、デバッグ モードになっていないかどうか、既知の提供元からインストールされているかどうかを確認します。
- **[デバイスでの USB デバッグをブロックする]**: USB デバッグは Android 仕事用プロファイル デバイスでは既に無効になっているため、この設定を構成する必要はありません。
- **[最低限のセキュリティ パッチ レベル]**: デバイスに含めることができる最も古いセキュリティ パッチ レベルを選択します。 修正プログラムがこのレベルに達していないデバイスは非準拠になります。 日付は *YYYY-MM-DD* 形式で入力する必要があります。
- **[制限付きアプリ]**: バンドル ID をポリシーに追加することでアプリを制限できます。 その後、あるデバイスにそのアプリがインストールされた場合、そのデバイスは非準拠となります。 
   - **[アプリ名]**: バンドル ID の識別を容易にするわかりやすい名前を入力します。 
   - **[アプリ バンドル ID]**: アプリ プロバイダーの一意のバンドル ID を入力します。 Android の場合、アプリ バンドル ID は、アプリのストア URL から取得されます。 たとえば、ストアでのアプリの URL が *https://play.google.com/store/apps/details?id=com.Slack* の場合、アプリ バンドル ID は *com.Slack* になります。


## <a name="assign-user-groups"></a>ユーザー グループを割り当てる

1. 構成済みのポリシーを選択します。 既存のポリシーは、**[デバイスのポリシー準拠]** > **[ポリシー]** で確認できます。
2. ポリシーを選択し、**[割り当て]** を選択します。 Azure Active Directory (AD) のセキュリティ グループは、含めることも除外することもできます。
3. **[選択したグループ]** を選択すると、Azure AD セキュリティ グループが表示されます。 このポリシーで適用するユーザー グループを選択し、**[保存]** を選択してユーザーにポリシーを展開します。

ポリシーがユーザーに適用されました。 ポリシーの対象となっているユーザーが使用しているデバイスは、コンプライアンスが評価されます。

## <a name="next-steps"></a>次の手順
[非準拠デバイスに対する自動メール送信とアクションの追加](actions-for-noncompliance.md)  
[Intune デバイスのコンプライアンス対応ポリシーの監視](compliance-policy-monitor.md)
