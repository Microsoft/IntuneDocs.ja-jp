---
title: Microsoft Intune での Windows 10 のコンプライアンス設定 - Azure | Microsoft Docs
description: Microsoft Intune で Windows 10、Windows Holographic、および Surface Hub の各デバイスにコンプライアンスを設定するときに使用できるすべての設定の一覧を表示します。 オペレーティング システムの最小バージョンと最大バージョンでコンプライアンスを確認する、パスワードの制限と長さを設定する、パートナーのウイル対策 (AV) ソリューションを確認する、データ ストレージで暗号化を有効にするなどを行います。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 484035603e4fb447b004aad6c6f85726034f3c23
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732829"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Intune を使用してデバイスを準拠または非準拠としてマークするための Windows 10 以降の設定

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

この記事では、Intune で Windows 10 以降のデバイスに構成できるさまざまなコンプライアンス設定の一覧を示して説明します。 モバイル デバイス管理 (MDM) ソリューションの一部として、これらの設定を使用して、BitLocker の要求、オペレーティング システムの最小バージョンと最大バージョンの設定、Microsoft Defender Advanced Threat Protection (ATP) を使用したリスク レベルの設定を行います。

この機能は、以下に適用されます。

- Windows 10 以降
- Windows Holographic for Business
- Surface Hub

Intune 管理者は、組織のリソースの保護に役立てるためにこれらのコンプライアンス設定を使用します。 コンプライアンス ポリシーの詳細およびその機能については、[デバイス コンプライアンスの概要](device-compliance-get-started.md)に関するページを参照してください。

## <a name="before-you-begin"></a>始める前に

[コンプライアンス ポリシーの作成](create-compliance-policy.md#create-the-policy)。 **[プラットフォーム]** には、 **[Windows 10 以降]** を選択します。

## <a name="device-health"></a>Device health

- **[BitLocker が必要]** : **[必須]** に設定すると、システムがオフになっているとき、または休止状態のときに、デバイスはドライブに格納されているデータを不正アクセスから保護できます。 Windows BitLocker ドライブ暗号化により、Windows オペレーティング システム ボリューム上に格納されているすべてのデータが暗号化されます。 BitLocker は TPM を使用して Windows オペレーティング システムとユーザー データを保護しています。 また、コンピューターのそばに人がいなかった場合や、コンピューターを紛失したり、盗難されたりした場合でも、改ざんされていないことを確認するためにも役立ちます。 コンピューターに互換性のある TPM が装備されている場合、BitLocker は TPM を使用してデータを保護する暗号化キーをロックします。 その結果、TPM がコンピューターの状態を確認するまで、キーはアクセスできません。

  **[未構成]** (既定値) に設定した場合、この設定に対して準拠であるか非準拠であるかの評価は行われません。

- **[Require Secure Boot to be enabled on the device]\(デバイス上でセキュア ブートを有効にする必要がある\)** : **[必須]** に設定すると、システムが工場出荷時の信頼できる状態で強制的に起動されます。 有効にする場合は、コンピューターを起動するために使用されるコア コンポーネントに、デバイスを製造した組織によって信頼されている正しい暗号署名が設定されている必要があります。 UEFI ファームウェアは、コンピューターを起動する前に署名を確認します。 ファイルが改ざんされ、その署名が破損している場合、システムは起動しません。

  **[未構成]** (既定値) に設定した場合、この設定に対して準拠であるか非準拠であるかの評価は行われません。

  > [!NOTE]
  > **[デバイス上でセキュア ブートの有効化が必要]** の設定は一部の TPM 1.2 および 2.0 デバイスでサポートされています。 TPM 2.0 以降をサポートしていないデバイスでは、Intune のポリシーの状態が **[非準拠]** と表示されます。 サポートされているバージョンの詳細については、[デバイス正常性構成証明](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation)に関するページを参照してください。

- **[コードの整合性が必要]:** コードの整合性は、ドライバーまたはシステム ファイルがメモリに読み込まれるたびに、その整合性を検証する機能です。 **[必須]** に設定すると、コードの整合性で、未署名のドライバーまたはシステム ファイルがカーネルに読み込まれているかどうかが検出されます。 また、管理者特権を持つユーザー アカウントが実行している悪意のあるソフトウェアによって、システム ファイルが変更されたかどうかも検出されます。

  **[未構成]** (既定値) に設定した場合、この設定に対して準拠であるか非準拠であるかの評価は行われません。

その他のリソース:

- HAS サービスのしくみについて詳しくは、[正常性構成証明 CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp) に関するページをご覧ください。
- [サポートのヒント: Intune コンプライアンス ポリシーの一部としてデバイス正常性構成証明書設定を使用する](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643)

## <a name="device-properties"></a>デバイスのプロパティ

- **最小 OS バージョン**: 許容される最小バージョンを **major.minor.build.CU の番号**形式で入力します。 正しい値を得るには、コマンド プロンプトを開き、「`ver`」と入力します。 `ver` コマンドは次の形式でバージョンを返します。

  `Microsoft Windows [Version 10.0.17134.1]`

  入力した OS バージョンよりデバイスのバージョンが低い場合、非準拠としてレポートされます。 アップグレード方法に関する情報のリンクが表示されます。 エンド ユーザーは、そのデバイスのアップグレードを行うことを選択できます。 アップグレード後は、会社のリソースにアクセスできます。

- **最大 OS バージョン**: 許容される最大バージョンを **major.minor.build.revision の番号**形式で入力します。 正しい値を得るには、コマンド プロンプトを開き、「`ver`」と入力します。 `ver` コマンドは次の形式でバージョンを返します。

  `Microsoft Windows [Version 10.0.17134.1]`

  入力したバージョンよりも新しいバージョンの OS がデバイスで使用されている場合、組織のリソースへのアクセスがブロックされます。 IT 管理者に問い合わせることをエンド ユーザーに促すメッセージが表示されます。 OS のバージョンを許可するようにルールが変更されるまでは、デバイスは組織のリソースにアクセスできません。

- **[Minimum OS required for mobile devices]\(モバイル デバイスに必要な最小 OS\)** : 許容される最小バージョンを major.minor.build の番号形式で入力します。

  入力した OS バージョンよりデバイスのバージョンが低い場合、非準拠としてレポートされます。 アップグレード方法に関する情報のリンクが表示されます。 エンド ユーザーは、そのデバイスのアップグレードを行うことを選択できます。 アップグレード後は、会社のリソースにアクセスできます。

- **[Maximum OS required for mobile devices]\(モバイル デバイスに必要な最大 OS\)** : 許容される最大バージョンを major.minor.build の番号で入力します。

  入力したバージョンよりも新しいバージョンの OS がデバイスで使用されている場合、組織のリソースへのアクセスがブロックされます。 IT 管理者に問い合わせることをエンド ユーザーに促すメッセージが表示されます。 OS のバージョンを許可するようにルールが変更されるまでは、デバイスは組織のリソースにアクセスできません。

- **[有効なオペレーティング システムのビルド]** : 最小バージョンと最大バージョンを含む、許容可能なオペレーティング システムのバージョンの範囲を入力します。 この許容可能な OS ビルド番号のコンマ区切り値 (CSV) ファイル リストを**エクスポート**することもできます。

## <a name="configuration-manager-compliance"></a>Configuration Manager のコンプライアンス

Windows 10 以降を実行している共同マネージド デバイスにのみ適用されます。 Intune 専用デバイスからは、利用不可の状態が返されます。

- **[System Center Configuration Manager からデバイス コンプライアンスが必要]** : System Center Configuration Manager のすべての設定 (構成項目) が準拠することを強制するには、 **[必須]** を選択します。 

  たとえば、すべてのソフトウェア更新プログラムをデバイスにインストールすることを要求します。 Configuration Manager では、この要求は "インストール済み" 状態となります。 デバイス上のいずれかのプログラムが不明な状態である場合、Intune ではデバイスが非準拠となります。
  
  **[未構成]** の場合、Intune では Configuration Manager 設定のすべてについて準拠しているかどうかが確認されません。

## <a name="system-security"></a>システム セキュリティ

### <a name="password"></a>パスワード

- **[モバイル デバイスのロック解除にパスワードを必要とする]** : デバイスにアクセスするユーザーにパスワードを入力するよう**求めます**。 構成されて**いない**場合、Intune はデバイスのコンプライアンス対応状態を評価しません。
- **[単純なパスワード]** : **[ブロック]** に設定すると、ユーザーは単純なパスワード (**1234**、**1111** など) を作成できません。 **[未構成]** に設定すると、ユーザーは **1234** や **1111** などのパスワードを作成できます。
- **[パスワードの種類]** : 必要なパスワードまたは PIN の種類を選択します。 次のようなオプションがあります。

  - **デバイスの既定**: パスワード、数字の pin、または英数字の pin が必要
  - **数値**: パスワードまたは数字の PIN が必要です
  - **英数字**: パスワードまたは英数字の PIN が必要です。 また、**パスワードの複雑さ**も選択します。 
    
    - **数字と小文字が必要**
    - **数字、小文字、および大文字を必要とする**
    - **[Require digits, lowercase letters, uppercase letters, and special characters]\(数字、小文字、大文字、特殊文字が必要\)**

    > [!TIP]
    > 英数字のパスワードポリシーは複雑になる場合があります。 詳細については、管理者が Csp を読むことをお勧めします。
    >
    > - [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [DeviceLock/MinDevicePasswordComplexCharacters CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **[パスワードの最小文字数]** : パスワードに必要な数字または文字の最小数を入力します。
- **[デバイスの画面がロックされるまでの非アクティブな最大分数]** : ユーザーがパスワードを再入力しなければならなくなるまでのアイドル時間を入力します。
- **[パスワードの有効期限 (日数)]** : 新しいパスワードの作成が必要となるまでのパスワードの有効日数 (1 日から 730 日) を入力します。
- **[再利用できないようにする前のパスワードの数]** : 何回前までのパスワードを使用できないようにするかを入力します。
- **[Require password]\(アイドル状態から戻るときにパスワードが必要\) (モバイルおよび Holographic)** : デバイスがアイドル状態から戻るたびにパスワードを入力することをユーザーに強制します。

  > [!IMPORTANT]
  > Windows デスクトップでパスワード要件が変更されると、デバイスがアイドルからアクティブに移行する次回のサインイン時にユーザーに影響します。 要件を満たすパスワードを持っているユーザーにも、パスワードの変更を求めるメッセージが表示されます。

### <a name="encryption"></a>暗号化

- **[Encryption of data storage on a device]\(デバイス上のデータ ストレージの暗号化\)** : **[必要]** を選択すると、デバイス上のデータ ストレージが暗号化されます。

  > [!NOTE]
  > **[Encryption of data storage on a device]\(デバイス上のデータ ストレージの暗号化\)** 設定では通常、デバイス上の暗号化の存在が確認されます。 より堅牢な暗号化設定が必要であれば、 **[BitLocker が必要]** の使用を検討してください。Windows デバイス ヘルス構成証明が活用され、TPM レベルで BitLocker の状態が検証されます。

### <a name="device-security"></a>［デバイス セキュリティ］

- **ファイアウォール**: Microsoft Defender ファイアウォールを有効にし、ユーザーが無効にすることを禁止する**ように設定**します。 **未構成**(既定) は Microsoft Defender ファイアウォールを制御せず、既存の設定を変更しません。

  [ファイアウォール CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

- **トラステッドプラットフォームモジュール (TPM)** : **[必須]** に設定されている場合、Intune はバージョンのコンプライアンスを確認します。 TPM チップのバージョンが 0 (ゼロ) より大きい場合、デバイスは準拠しています。 デバイスに TPM バージョンがない場合、デバイスは準拠していません。 構成されて**いない**場合、Intune はデバイスで TPM チップバージョンを確認しません。

  [DeviceStatus CSP-DeviceStatus/TPM/仕様バージョンノード](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **[ウイルス対策]** : **[必要]** に設定すると、[Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/) に登録されている Symantec や Microsoft Defender などのウイルス対策ソリューションを使って、コンプライアンスを確認できます。 **未構成**のときには、Intune は、デバイスにインストールされている AV ソリューションを確認しません。
- **[スパイウェア対策]** : **[必要]** に設定すると、[Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/) に登録されている Symantec や Microsoft Defender などのウイルス対策ソリューションを使って、コンプライアンスを確認できます。 **[未構成]** のときには、Intune は、デバイスにインストールされているスパイウェア対策ソリューションを確認しません。

### <a name="defender"></a>Defender

- **Microsoft Defender マルウェア対策**: microsoft defender マルウェア対策サービスを有効にし、ユーザーが**オフにでき**ないようにするには、を設定します。 **未構成**(既定) はサービスを制御せず、既存の設定を変更しません。
- **Microsoft Defender マルウェア対策の最小バージョン**: microsoft defender マルウェア対策サービスの許可されている最小バージョンを入力します。 たとえば、「`4.11.0.0`」と入力します。 空白のままにすると、Microsoft Defender マルウェア対策サービスのすべてのバージョンを使用できます。
- **Microsoft Defender マルウェア対策セキュリティインテリジェンス**の最新情報: デバイス上の Windows セキュリティウイルスおよび脅威保護の更新を制御します。 Microsoft Defender セキュリティインテリジェンスを強制的に最新の状態にする**必要が**あります。 **未構成**(既定) では、要件は適用されません。

  セキュリティインテリジェンスの詳細については、 [Microsoft Defender ウイルス対策およびその他の microsoft マルウェア対策のセキュリティインテリジェンスの更新](https://www.microsoft.com/en-us/wdsi/defenderupdates)に関する情報を参照してください。

- **リアルタイム保護**: **[必須]** は、マルウェア、スパイウェア、およびその他の望ましくないソフトウェアをスキャンするリアルタイム保護をオンにします。 **未構成**(既定) は、この機能を制御したり、既存の設定を変更したりしません。

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

- **[Require the device to be at or under the machine risk score]\(デバイスは、コンピューターのリスク スコア以下であることが必要\)** : この設定は、脅威防御サービスからのリスク評価をコンプライアンスの条件とする場合に使用します。 許容される脅威の最大レベルを選択します。

  - **[クリア]** : デバイスにはいかなる脅威も存在してはならないので、これはセキュリティ上最も安全なオプションです。 デバイスで何らかのレベルの脅威が検出された場合、非準拠と評価されます。
  - **[低]** : 存在する脅威が低レベルの場合のみ、デバイスは準拠として評価されます。 低レベルより高い脅威が存在する場合、デバイスは非準拠状態になります。
  - **[中]** : デバイスに存在する脅威が低レベルまたは中レベルの場合、デバイスは準拠として評価されます。 デバイスで高レベルの脅威が検出された場合は、非準拠と判定されます。
  - **[高]** : 最も安全性の低いオプションであり、すべての脅威レベルが許容されます。 このソリューションをレポート目的のみで使用した場合、役立つ場合があります。
  
  脅威対策サービスとして Microsoft Defender ATP (Advanced Threat Protection) を設定するには、[条件付きアクセスによる Microsoft Defender ATP の有効化](advanced-threat-protection.md)に関するページを参照してください。

**[OK]**  >  **[作成]** を選択して変更を保存します。

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business では、**Windows 10 以降**のプラットフォームが使用されます。 Windows Holographic for Business は、以下の設定をサポートします。

- **システム セキュリティ** > **暗号化** > **デバイス上のデータ ストレージの暗号化**。

Microsoft HoloLens でデバイスの暗号化を確認するには、「[デバイスの暗号化を確認する](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption)」を参照してください。

## <a name="surface-hub"></a>Surface Hub

Surface Hub では **Windows 10 以降**のプラットフォームが使用されます。 Surface Hub は、コンプライアンスと条件付きアクセスの両方でサポートされます。 Surface Hub 上でこれらの機能を有効にするには、Intune で [Windows 10 の自動登録を有効](../enrollment/windows-enroll.md)にし (Azure Active Directory (Azure AD) が必要)、デバイス グループとして Surface Hub デバイスを対象とすることをお勧めします。 Surface Hub は、コンプライアンスおよび条件付きアクセスが機能するように Azure AD に参加している必要があります。

ガイダンスについては、「[Windows デバイスの登録をセットアップする](../enrollment/windows-enroll.md)」を参照してください。

## <a name="next-steps"></a>次の手順

- [非準拠デバイスに対するアクションを追加](actions-for-noncompliance.md)し、[スコープのタグを使用してポリシーをフィルター処理する](../fundamentals/scope-tags.md)
- [コンプライアンス ポリシーを監視します](compliance-policy-monitor.md)。
- [Windows 8.1 デバイス向けのコンプライアンス ポリシー設定](compliance-policy-create-windows-8-1.md)を確認します。
