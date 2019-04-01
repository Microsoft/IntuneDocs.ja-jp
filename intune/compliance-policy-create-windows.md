---
title: Microsoft Intune で Windows デバイスに関するコンプライアンスを確認する - Azure | Microsoft Docs
description: Windows Phone 8.1 のデバイス、Windows 8.1 以降のデバイス、および Windows 10 以降のデバイス用の Microsoft Intune デバイス コンプライアンス ポリシーを作成または構成します。 最小および最大のオペレーティング システムでのコンプライアンスを確認し、パスワードの制限と長さを設定し、Bitlocker を要求し、サードパーティ AV ソリューションを確認し、許容可能な脅威レベルを設定し、データ ストレージでの暗号化を有効にします (Surface Hub や Windows Holographic for Business を含む)。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6e82e24f051e64d07487d915ac6fd0848727ecf
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566813"
---
# <a name="add-a-device-compliance-policy-for-windows-devices-in-intune"></a>Intune で Windows デバイス用のデバイス コンプライアンス ポリシーを追加する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune デバイス コンプライアンス ポリシーには、準拠しているものと見なされるためにデバイスが満たす必要のあるルールと設定が含まれています。 このようなポリシーを条件付きアクセスと共に使用することで、組織のリソースへのアクセスを許可または阻止することができます。 コンプライアンス違反に対して、デバイス レポートを取得したり、是正措置を取ったりすることもできます。

コンプライアンス ポリシーの詳細については、[デバイス コンプライアンスの概要](device-compliance-get-started.md)に関するページを参照してください。

次の表では、条件付きアクセス ポリシーとコンプライアンス ポリシーを使用する場合に非準拠設定をどのように管理するかについて説明しています。

---------------------------

| **ポリシー設定** | **Windows 8.1 以降** | **Windows Phone 8.1 以降** |
|----| ----| --- |
| **PIN またはパスワードの構成** | 修復 | 修復 |   
| **デバイスの暗号化** | 該当なし | 修復 |   
| **脱獄またはルート化されたデバイス** | 適用できません | 適用できません |  
| **電子メールのプロファイル** | 適用できません | 適用できません |   
| **最小 OS バージョン** | 検疫済み | 検疫済み |   
| **最大 OS バージョン** | 検疫済み | 検疫済み |   
| **Windows 正常性構成証明書** | 検疫済み: Windows 10 および Windows 10 Mobile|該当なし: Windows 8.1 |

-------------------------------

**修復** = デバイス オペレーティング システムによって準拠が強制されます  (たとえば、ユーザーは PIN を設定するように強制されます)。

**検疫済み** = デバイス オペレーティング システムによって準拠が強制されません  (たとえば、Android デバイスでは、ユーザーはデバイスの暗号化を強制されません)。デバイスが準拠していない場合、次のアクションが行われます。

- ユーザーに条件付きアクセス ポリシーを適用すると、デバイスがブロックされます。
- ポータル サイトは、コンプライアンスの問題をユーザーに通知します。

## <a name="create-a-device-compliance-policy"></a>デバイス コンプライアンス ポリシーの作成

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. **[プラットフォーム]** で、**[Windows Phone 8.1]**、**[Windows 8.1 以降]**、または **[Windows 10 以降]** を選択します。
6. **[設定]** を選択し、**[デバイスのヘルス]**、**[デバイス プロパティ]**、および **[システム セキュリティ]** の設定を入力します。 完了したら、**[OK]**、**[作成]** の順に選択します。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="windows-81-devices-policy-settings"></a>Windows 8.1 デバイス ポリシーの設定

これらのポリシー設定は、次のプラットフォームを実行しているデバイスに適用されます。

- Windows Phone 8。1
- Windows 8.1 以降

### <a name="device-properties"></a>デバイスのプロパティ

- **[必要な最小 OS バージョン]**: デバイスが最小 OS バージョンの要件を満たしていない場合、非準拠として報告されます。 アップグレード方法に関する情報のリンクが表示されます。 エンド ユーザーは、デバイスのアップグレードを行うことを選択できます。アップグレード後は、会社のリソースにアクセスできます。
- **[許可される最大 OS バージョン]**: ルールに入力された OS バージョンより新しいバージョンの OS がデバイスで使用されている場合、会社のリソースへのアクセスがブロックされます。 IT 管理者に問い合わせることをユーザーに促すメッセージが表示されます。OS バージョンを許可するようにルールを変更するまで、デバイスは組織のリソースにアクセスできません。

Windows 8.1 PC の場合、バージョン **3** が返されます。 Windows に関して OS バージョンのルールを Windows 8.1 に設定した場合、デバイスに Windows 8.1 がインストールされていても、そのデバイスは非準拠として報告されます。

### <a name="system-security"></a>システム セキュリティ

#### <a name="password"></a>パスワード

- **[モバイル デバイスのロック解除にパスワードを必要とする]**: デバイスにアクセスするユーザーにパスワードを入力するよう**求めます**。
- **[単純なパスワード]**: **[ブロック]** に設定すると、ユーザーは単純なパスワード (**1234**、**1111** など) を作成できません。 **[未構成]** に設定すると、ユーザーは **1234** や **1111** などのパスワードを作成できます。
- **[パスワードの最小文字数]**: パスワードに必要な数字または文字の最小数を入力します。

  Windows を実行していて Microsoft アカウントでアクセスされるデバイスについては、次の場合にコンプライアンス ポリシーが正常に評価されません。
  - パスワードの長さが 8 文字を超える場合
  - または、文字セットの最小数が 2 より大きい場合

- **[パスワードの種類]**: パスワードの内容を**数字**のみにするかどうか、あるいは数字とその他の文字との組み合わせ (**英数字**) にするかどうかを選択します。
  
  - **[パスワードに使用する英数字以外の文字数]:** **[必要なパスワードの種類]** が **[英数字]** に設定されている場合、この設定ではパスワードに含める必要がある、文字セットの最小数を指定します。 次の 4 つの文字セットがあります。
    - 小文字
    - 大文字
    - 記号
    - 数字

    大きな数値を設定すると、ユーザーはより複雑なパスワードを作成する必要があります。 Microsoft アカウントでアクセスされるデバイスについては、次の場合にコンプライアンス ポリシーが正常に評価されません。

    - パスワードの長さが 8 文字を超える場合
    - または、文字セットの最小数が 2 より大きい場合

- **[デバイスの画面がロックされるまでの非アクティブな最大分数]**: ユーザーがパスワードを再入力しなければならなくなるまでのアイドル時間を入力します。
- **[パスワードの有効期限 (日数)]**: 新しいパスワードの作成が必要となるまでのパスワードの有効日数を選択します。
- **[再利用できないようにする前のパスワードの数]**: 何回前までのパスワードを使用できないようにするかを入力します。

#### <a name="encryption"></a>暗号化

- **[モバイル デバイスで暗号化を必要とする]**: データ ストレージ リソースに接続するにはデバイスの暗号化が**必須**です。

## <a name="windows-10-and-later-policy-settings"></a>Windows 10 以降のポリシー設定

### <a name="device-health"></a>Device health

- **[BitLocker が必要]**: Bitlocker がオンである場合は、システムがオフになっているとき、または休止状態になるときに、デバイスはドライブに格納されているデータを不正アクセスから保護できます。 Windows BitLocker ドライブ暗号化により、Windows オペレーティング システム ボリューム上に格納されているすべてのデータが暗号化されます。 BitLocker は TPM を使用して Windows オペレーティング システムとユーザー データを保護しています。 また、コンピューターのそばに人がいなかった場合や、コンピューターを紛失したり、盗難されたりした場合でも、改ざんされていないことを確認するためにも役立ちます。 コンピューターに互換性のある TPM が装備されている場合、BitLocker は TPM を使用してデータを保護する暗号化キーをロックします。 その結果、TPM がコンピューターの状態を確認するまで、キーはアクセスできません。
- **[Require Secure Boot to be enabled on the device]\(デバイス上でセキュア ブートを有効にする必要がある\)**: セキュア ブートを有効にすると、システムが工場出荷時の信頼できる状態で強制的に起動されます。 また、セキュア ブートを有効にするときは、コンピューターを起動するために使用されるコア コンポーネントに、デバイスを製造した組織によって信頼されている正しい暗号署名が設定されている必要があります。 UEFI ファームウェアは、コンピューターを起動する前に署名を確認します。 ファイルが改ざんされ、その署名が破損している場合、システムは起動しません。

  > [!NOTE]
  > **[デバイス上でセキュア ブートの有効化が必要]** の設定は一部の TPM 1.2 および 2.0 デバイスでサポートされています。 TPM 2.0 以降をサポートしていないデバイスでは、Intune のポリシーの状態が **[非準拠]** と表示されます。 サポートされているバージョンの詳細については、次を参照してください。[デバイス正常性構成証明](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation)します。

- **[コードの整合性が必要]:** コードの整合性は、ドライバーまたはシステム ファイルがメモリに読み込まれるたびに、その整合性を検証する機能です。 コードの整合性で、未署名のドライバーまたはシステム ファイルがカーネルに読み込まれているかどうかが検出されます。 また、管理者特権を持つユーザー アカウントが実行している悪意のあるソフトウェアによって、システム ファイルが変更されたかどうかも検出されます。

HAS サービスのしくみの詳細については、「[HealthAttestation CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp)」をご覧ください。

### <a name="device-properties"></a>デバイスのプロパティ

- **最小 OS バージョン**: 許容される最小バージョンを **major.minor.build.CU の番号**形式で入力します。 正しい値を得るには、コマンド プロンプトを開き、「`ver`」と入力します。 `ver` コマンドは次の形式でバージョンを返します。

  `Microsoft Windows [Version 10.0.17134.1]`

  入力した OS バージョンよりデバイスのバージョンが低い場合、非準拠としてレポートされます。 アップグレード方法に関する情報のリンクが表示されます。 エンド ユーザーは、そのデバイスのアップグレードを行うことを選択できます。 アップグレード後は、会社のリソースにアクセスできます。

- **最大 OS バージョン**: 許容される最大バージョンを **major.minor.build.revision の番号**形式で入力します。 正しい値を得るには、コマンド プロンプトを開き、「`ver`」と入力します。 `ver` コマンドは次の形式でバージョンを返します。

  `Microsoft Windows [Version 10.0.17134.1]`

  ルールに入力した OS バージョンより新しいバージョンの OS がデバイスで使用されている場合、会社のリソースへのアクセスがブロックされ、IT 管理者に問い合わせることをユーザーに促すメッセージが表示されます。OS のバージョンを許可するようにルールが変更されるまでは、デバイスは会社のリソースにアクセスできません。

- **[Minimum OS required for mobile devices]\(モバイル デバイスに必要な最小 OS\)**: 許容される最小バージョンを major.minor.build の番号形式で入力します。

  入力した OS バージョンよりデバイスのバージョンが低い場合、非準拠としてレポートされます。 アップグレード方法に関する情報のリンクが表示されます。 エンド ユーザーは、そのデバイスのアップグレードを行うことを選択できます。 アップグレード後は、会社のリソースにアクセスできます。

- **[Maximum OS required for mobile devices]\(モバイル デバイスに必要な最大 OS\)**: 許容される最大バージョンを major.minor.build の番号で入力します。

  入力した OS バージョンより新しいバージョンの OS がデバイスで使用されている場合、会社のリソースへのアクセスがブロックされ、IT 管理者に問い合わせることをユーザーに促すメッセージが表示されます。OS のバージョンを許可するようにルールが変更されるまでは、デバイスは会社のリソースにアクセスできません。

- **[有効なオペレーティング システムのビルド]**: 最小バージョンと最大バージョンを含む、許容可能なオペレーティング システムのバージョンの範囲を入力します。 この許容可能な OS ビルド番号のコンマ区切り値 (CSV) ファイル リストを**エクスポート**することもできます。

### <a name="configuration-manager-compliance"></a>Configuration Manager のコンプライアンス

Windows 10 以降を実行している共同マネージド デバイスにのみ適用されます。 Intune 専用デバイスからは、利用不可の状態が返されます。

- **System Center Configuration Manager からのデバイス コンプライアンスが必要**: 選択**必要**System Center Configuration Manager で準拠しているすべての設定 (構成項目) を強制します。 

  たとえば、すべてのソフトウェア更新プログラムをデバイスにインストールすることを要求します。 Configuration Manager では、この要求は "インストール済み" 状態となります。 デバイス上のいずれかのプログラムが不明な状態である場合、Intune ではデバイスが非準拠となります。
  
  **[未構成]** の場合、Intune では Configuration Manager 設定のすべてについて準拠しているかどうかが確認されません。

### <a name="system-security-settings"></a>システム セキュリティ設定

#### <a name="password"></a>パスワード

- **[モバイル デバイスのロック解除にパスワードを必要とする]**: デバイスにアクセスするユーザーにパスワードを入力するよう**求めます**。
- **[単純なパスワード]**: **[ブロック]** に設定すると、ユーザーは単純なパスワード (**1234**、**1111** など) を作成できません。 **[未構成]** に設定すると、ユーザーは **1234** や **1111** などのパスワードを作成できます。
- **[パスワードの種類]**: パスワードの内容を**数字**のみにするかどうか、あるいは数字とその他の文字との組み合わせ (**英数字**) にするかどうかを選択します。

  - **[パスワードに使用する英数字以外の文字数]:** **[必要なパスワードの種類]** が **[英数字]** に設定されている場合、この設定ではパスワードに含める必要がある、文字セットの最小数を指定します。 次の 4 つの文字セットがあります。
    - 小文字
    - 大文字
    - 記号
    - 数字

    大きな数値を設定すると、ユーザーはより複雑なパスワードを作成する必要があります。

- **[パスワードの最小文字数]**: パスワードに必要な数字または文字の最小数を入力します。
- **[デバイスの画面がロックされるまでの非アクティブな最大分数]**: ユーザーがパスワードを再入力しなければならなくなるまでのアイドル時間を入力します。
- **[パスワードの有効期限 (日数)]**: 新しいパスワードの作成が必要となるまでのパスワードの有効日数を選択します。
- **[再利用できないようにする前のパスワードの数]**: 何回前までのパスワードを使用できないようにするかを入力します。
- **[Require password]\(アイドル状態から戻るときにパスワードが必要\) (モバイルおよび Holographic)**: デバイスがアイドル状態から戻るたびにパスワードを入力することをユーザーに強制します。

#### <a name="encryption"></a>暗号化

- **[Encryption of data storage on a device]\(デバイス上のデータ ストレージの暗号化\)**: **[必要]** を選択すると、デバイス上のデータ ストレージが暗号化されます。

  > [!NOTE]
  > **[Encryption of data storage on a device]\(デバイス上のデータ ストレージの暗号化\)** 設定では通常、デバイス上の暗号化の存在が確認されます。 より堅牢な暗号化設定が必要であれば、**[BitLocker が必要]** の使用を検討してください。Windows デバイス ヘルス構成証明が活用され、TPM レベルで BitLocker の状態が検証されます。

#### <a name="device-security"></a>［デバイス セキュリティ］

- **[ウイルス対策]**: **[必要]** に設定すると、[Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/) に登録されている Symantec や Windows Defender などのウイルス対策ソリューションを使って、コンプライアンスを確認できます。 **未構成**のときには、Intune は、デバイスにインストールされている AV ソリューションを確認しません。
- **[スパイウェア対策]**: **[必要]** に設定すると、[Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/) に登録されている Symantec や Windows Defender などのスパイウェア対策ソリューションを使って、コンプライアンスを確認できます。 **[未構成]** のときには、Intune は、デバイスにインストールされているスパイウェア対策ソリューションを確認しません。

### <a name="windows-defender-atp"></a>Windows Defender ATP

- **[Require the device to be at or under the machine risk score]\(デバイスは、コンピューターのリスク スコア以下であることが必要\)**: この設定は、脅威防御サービスからのリスク評価をコンプライアンスの条件とする場合に使用します。 許容される脅威の最大レベルを選択します。
  - **[クリア]**: デバイスにはいかなる脅威も存在してはならないので、これはセキュリティ上最も安全なオプションです。 デバイスで何らかのレベルの脅威が検出された場合、非準拠と評価されます。
  - **[低]**: 存在する脅威が低レベルの場合のみ、デバイスは準拠として評価されます。 低レベルより高い脅威が存在する場合、デバイスは非準拠状態になります。
  - **[中]**: デバイスに存在する脅威が低レベルまたは中レベルの場合、デバイスは準拠として評価されます。 デバイスで高レベルの脅威が検出された場合は、非準拠と判定されます。
  - **[高]**: 最も安全性の低いオプションであり、すべての脅威レベルが許容されます。 このソリューションをレポート目的のみで使用した場合、役立つ場合があります。
  
  脅威対策サービスとしての Windows Defender ATP (Advanced Threat Protection) を設定するには、「[Intune で条件付きアクセスによる Windows Defender ATP を有効にする](advanced-threat-protection.md)」を参照してください。

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business では、**Windows 10 以降**のプラットフォームが使用されます。 Windows Holographic for Business は、以下の設定をサポートします。

- **システム セキュリティ** > **暗号化** > **デバイス上のデータ ストレージの暗号化**。

Microsoft HoloLens でデバイスの暗号化を確認するには、「[デバイスの暗号化を確認する](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption)」を参照してください。

## <a name="surface-hub"></a>Surface Hub
Surface Hub では **Windows 10 以降**のプラットフォームが使用されます。 Surface Hub は、コンプライアンスと条件付きアクセスの両方でサポートされます。 Surface Hub 上でこれらの機能を有効にするには、Intune で [Windows 10 の自動登録を有効](windows-enroll.md)にし (Azure Active Directory (Azure AD) も必要)、デバイス グループとして Surface Hub デバイスを対象とすることをお勧めします。 Surface Hub は、コンプライアンスおよび条件付きアクセスが機能するように Azure AD に参加している必要があります。

ガイダンスについては、「[Windows デバイスの登録をセットアップする](windows-enroll.md)」を参照してください。

## <a name="assign-user-or-device-groups"></a>ユーザーまたはデバイス グループを割り当てる

1. 構成済みのポリシーを選択します。 既存のポリシーは、**[デバイスのポリシー準拠]** > **[ポリシー]** で確認できます。
2. ポリシーを選択し、**[割り当て]** を選択します。 Azure AD のセキュリティ グループは、含めることも除外することもできます。
3. **[選択したグループ]** を選択すると、Azure AD セキュリティ グループが表示されます。 このポリシーで適用するユーザー グループまたはデバイス グループを選択し、**[保存]** を選択してポリシーを展開します。

ポリシーが適用されました。 ポリシーの対象となっているユーザーが使用しているデバイスに対して、コンプライアンスに関する評価が行われます。

## <a name="next-steps"></a>次の手順
[非準拠デバイスに対する自動メール送信とアクションの追加](actions-for-noncompliance.md)  
[Intune デバイスのコンプライアンス対応ポリシーの監視](compliance-policy-monitor.md)
