---
title: Microsoft Intune での Windows 10 のコンプライアンス設定 - Azure | Microsoft Docs
description: Microsoft Intune で Windows 10、Windows Holographic、および Surface Hub の各デバイスにコンプライアンスを設定するときに使用できるすべての設定の一覧を表示します。 オペレーティング システムの最小バージョンと最大バージョンでコンプライアンスを確認する、パスワードの制限と長さを設定する、パートナーのウイル対策 (AV) ソリューションを確認する、データ ストレージで暗号化を有効にするなどを行います。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ca5d475f92cbe3298689273dcdf0da1644078b2
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547029"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Intune を使用してデバイスを準拠または非準拠としてマークするための Windows 10 以降の設定

この記事では、Intune で Windows 10 以降のデバイスに構成できるさまざまなコンプライアンス設定の一覧を示して説明します。 モバイル デバイス管理 (MDM) ソリューションの一部として、これらの設定を使用して、BitLocker の要求、オペレーティング システムの最小バージョンと最大バージョンの設定、Microsoft Defender Advanced Threat Protection (ATP) を使用したリスク レベルの設定を行います。

この機能は、以下に適用されます。

- Windows 10 以降
- Windows Holographic for Business
- Surface Hub

Intune サービス管理者は、組織のリソースの保護に役立てるために、これらのコンプライアンス設定を使用します。 コンプライアンス ポリシーの詳細およびその機能については、[デバイス コンプライアンスの概要](device-compliance-get-started.md)に関するページを参照してください。

## <a name="before-you-begin"></a>始める前に

[コンプライアンス ポリシーの作成](create-compliance-policy.md#create-the-policy)。 **[プラットフォーム]** には、 **[Windows 10 以降]** を選択します。

## <a name="device-health"></a>デバイスの正常性

### <a name="windows-health-attestation-service-evaluation-rules"></a>Windows 正常性構成証明サービスの評価ルール

- **[BitLocker が必要]** :  
   Windows BitLocker ドライブ暗号化により、Windows オペレーティング システム ボリューム上に格納されているすべてのデータが暗号化されます。 BitLocker は、トラステッドプラットフォームモジュール (TPM) を使用して、Windows オペレーティングシステムとユーザーデータを保護します。 また、コンピューターのそばに人がいなかった場合や、コンピューターを紛失したり、盗難されたりした場合でも、改ざんされていないことを確認するためにも役立ちます。 コンピューターに互換性のある TPM がインストールされている場合は、BitLocker は TPM を使用してデータを保護する暗号化キーをロックします。 その結果、TPM がコンピューターの状態を確認するまで、キーはアクセスできません。  

   - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。
   - **[必須]** - システムがオフになっているとき、または休止状態のときに、デバイスがドライブに格納されているデータを不正アクセスから保護できます。  


- **[デバイス上でセキュア ブートの有効化が必要]** :  
    - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。
    - **必須**-システムは、工場出荷時の信頼できる状態で強制的に起動されます。 コンピューターを起動するために使用されるコア コンポーネントに、デバイスを製造した組織によって信頼されている正しい暗号署名が設定されている必要があります。 UEFI ファームウェアは、コンピューターを起動する前に署名を確認します。 ファイルが改ざんされ、その署名が破損している場合、システムは起動しません。

  > [!NOTE]
  > **[デバイス上でセキュア ブートの有効化が必要]** の設定は一部の TPM 1.2 および 2.0 デバイスでサポートされています。 TPM 2.0 以降をサポートしていないデバイスでは、Intune のポリシーの状態が **[非準拠]** と表示されます。 サポートされているバージョンの詳細については、[デバイス正常性構成証明](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation)に関するページを参照してください。

- **[コードの整合性が必要]** :  
  コードの整合性は、ドライバーまたはシステム ファイルがメモリに読み込まれるたびに、その整合性を検証する機能です。
  - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。
  -  **[必須]** - コードの整合性が必要です。これにより、未署名のドライバーまたはシステム ファイルがカーネルに読み込まれているかどうかが検出されます。 また、システム ファイルが、悪意のあるソフトウェアによって変更されたかどうか、または管理者特権を持つユーザー アカウントによって実行されたかどうかも検出されます。

その他のリソース:

- 正常性構成証明書サービスの動作の詳細については、「[正常性構成証明書 CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp)」を参照してください。
- [サポートのヒント:Intune コンプライアンス ポリシーの一部としてデバイス正常性構成証明の設定を使用する](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643)。

## <a name="device-properties"></a>デバイスのプロパティ

### <a name="operating-system-version"></a>オペレーティング システムのバージョン

- **[最小 OS バージョン]** :  
  許容される最小バージョンを **major.minor.build.CU の番号**形式で入力します。 正しい値を得るには、コマンド プロンプトを開き、「`ver`」と入力します。 `ver` コマンドは次の形式でバージョンを返します。

  `Microsoft Windows [Version 10.0.17134.1]`

  入力した OS バージョンよりデバイスのバージョンが低い場合、非準拠としてレポートされます。 アップグレード方法に関する情報のリンクが表示されます。 エンド ユーザーは、そのデバイスのアップグレードを行うことを選択できます。 アップグレード後は、会社のリソースにアクセスできます。

- **[最大 OS バージョン]** :  
  許容される最大バージョンを **major.minor.build.revision の番号**形式で入力します。 正しい値を得るには、コマンド プロンプトを開き、「`ver`」と入力します。 `ver` コマンドは次の形式でバージョンを返します。

  `Microsoft Windows [Version 10.0.17134.1]`

  入力したバージョンよりも新しいバージョンの OS がデバイスで使用されている場合、組織のリソースへのアクセスがブロックされます。 IT 管理者に問い合わせることをエンド ユーザーに促すメッセージが表示されます。 OS のバージョンを許可するようにルールが変更されるまでは、デバイスは組織のリソースにアクセスできません。

- **[Minimum OS required for mobile devices]\(モバイル デバイスに必要な最小 OS\)** :  
  許容される最小バージョンを major.minor.build の番号形式で入力します。

  入力した OS バージョンよりデバイスのバージョンが低い場合、非準拠としてレポートされます。 アップグレード方法に関する情報のリンクが表示されます。 エンド ユーザーは、そのデバイスのアップグレードを行うことを選択できます。 アップグレード後は、会社のリソースにアクセスできます。

- **[Maximum OS required for mobile devices]\(モバイル デバイスに必要な最大 OS\)**  
  許容される最大バージョンを major.minor.build の番号で入力します。

  入力したバージョンよりも新しいバージョンの OS がデバイスで使用されている場合、組織のリソースへのアクセスがブロックされます。 IT 管理者に問い合わせることをエンド ユーザーに促すメッセージが表示されます。 OS のバージョンを許可するようにルールが変更されるまでは、デバイスは組織のリソースにアクセスできません。

- **[有効なオペレーティング システムのビルド]** :  
  最小バージョンと最大バージョンを含む、許容可能なオペレーティング システムのバージョンの範囲を入力します。 この許容可能な OS ビルド番号のコンマ区切り値 (CSV) ファイル リストを**エクスポート**することもできます。

## <a name="configuration-manager-compliance"></a>Configuration Manager のコンプライアンス

Windows 10 以降を実行している共同マネージド デバイスにのみ適用されます。 Intune 専用デバイスからは、利用不可の状態が返されます。

- **Configuration Manager からのデバイスコンプライアンスが必要**:  
  - **[未構成]** ("*規定値*") - Intune で、あらゆる Configuration Manager 設定についてコンプライアンスがチェックされません。
  - **[必須]** - Configuration Manager のすべての設定 (構成項目) が準拠している必要があります。  

    たとえば、すべてのソフトウェア更新プログラムをデバイスにインストールすることを要求します。 Configuration Manager では、この要求は "インストール済み" 状態となります。 デバイス上のいずれかのプログラムが不明な状態である場合、Intune ではデバイスが非準拠となります。

## <a name="system-security"></a>システム セキュリティ

### <a name="password"></a>パスワード

- **[モバイル デバイスのロック解除にパスワードを必要とする]** :  
  - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。
  - **[必須]** - デバイスにアクセスするユーザーにパスワードを入力するよう求めます。 

- **[単純なパスワード]** :  
  - **未構成**(*既定*)-ユーザーは、 **1234**や**1111**などの単純なパスワードを作成できます。
  - **[ブロック]** - ユーザーは単純なパスワード (**1234**、**1111** など) を作成できません。

- **パスワードの種類**:  
  必要なパスワードまたは PIN の種類を選択します。 次のようなオプションがあります。
  - **デバイスの既定**値 (*既定*)-パスワード、数字の pin、または英数字の pin が必要です
  - **数値**-パスワードまたは数字の PIN が必要です
  - **英数字**-パスワード、または英数字の PIN が必要です。  
  
  [*英数字*] に設定すると、次の設定を使用できます。  
  - **[パスワードの複雑さ]** :  
    次のようなオプションがあります。 
    - **数字と小文字を必要とする**(*既定*)
    - **数字、小文字、および大文字を必要とする**
    - **[Require digits, lowercase letters, uppercase letters, and special characters]\(数字、小文字、大文字、特殊文字が必要\)**

    > [!TIP]
    > 英数字のパスワードポリシーは複雑になる場合があります。 詳細については、管理者が Csp を読むことをお勧めします。
    >
    > - [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [DeviceLock/MinDevicePasswordComplexCharacters CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **[パスワードの最小文字数]** :  
  パスワードに必要な数字または文字の最小数を入力します。

- **[パスワードが要求されるまでの非アクティブの最長時間 (分)]** :  
  ユーザーがパスワードを再入力しなければならなくなるまでのアイドル時間を入力します。

- **[パスワードの有効期限 (日数)]** :  
  パスワードの有効期限が切れて、新しく作成することが必要になるまでの日数を、1-730 日の範囲で入力します。

- **[再使用を禁止するパスワード世代数]** :  
  何回前までのパスワードを使用できないようにするかを入力します。

- **[デバイスがアイドル状態から戻るときにパスワードを必須にする (Mobile および Holographic)]** :  
  - **[未構成]** ("*既定値*")
  - **[必須]** - デバイスがアイドル状態から戻るたびに、デバイスのユーザーにパスワードの入力を要求します。

  > [!IMPORTANT]
  > Windows デスクトップでパスワード要件が変更されると、デバイスがアイドルからアクティブに移行する次回のサインイン時にユーザーに影響します。 要件を満たすパスワードを持っているユーザーにも、パスワードの変更を求めるメッセージが表示されます。

### <a name="encryption"></a>暗号化

- **[デバイス上のデータ ストレージの暗号化]** :  
  この設定は、デバイス上のすべてのドライブに適用されます。
  - **[未構成]** ("*既定値*")
  - **[必須]** - デバイス上のデータ ストレージを暗号化するには、 *[必須]* を選択します。

  > [!NOTE]
  > **[Encryption of data storage on a device]\(デバイス上のデータ ストレージの暗号化\)** 設定では通常、デバイス上の暗号化の存在が確認されます。 より堅牢な暗号化設定が必要であれば、 **[BitLocker が必要]** の使用を検討してください。Windows デバイス ヘルス構成証明が活用され、TPM レベルで BitLocker の状態が検証されます。

### <a name="device-security"></a>デバイスのセキュリティ  

- **ファイアウォール**:  
  - **未構成**(*既定*)-Intune は Microsoft Defender ファイアウォールを制御せず、既存の設定を変更しません。
  - **[必須]** -Microsoft Defender ファイアウォールを有効にし、ユーザーが無効にできないようにします。  

  [ファイアウォール CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

  > [!NOTE]
  > 再起動後にデバイスが直ちに同期される場合、またはすぐにスリープからウェイクアップを同期する場合は、この設定が**エラー**として報告されることがあります。 このシナリオは、全体的なデバイスのコンプライアンス状態に影響しない場合があります。 コンプライアンス対応状態を再評価するには、デバイスを手動で[同期](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows)します。

- **トラステッド プラットフォーム モジュール (TPM)** :  
  - **未構成**(*既定*)-INTUNE はデバイスで TPM チップのバージョンを確認しません。
  - **必須**-Intune は、TPM チップバージョンのコンプライアンスを確認します。 TPM チップのバージョンが**0** (ゼロ) より大きい場合、デバイスは準拠しています。 デバイスに TPM バージョンがない場合、デバイスは準拠していません。  

  [DeviceStatus CSP-DeviceStatus/TPM/仕様バージョンノード](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **[ウイルス対策]** :  
  - **[未構成]** ("*規定値*") - Intune により、デバイスにインストールされているスパイウェア対策ソリューションが確認されません。 
  - **[必須]** - [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/) に登録されている Symantec や Microsoft Defender などのウイルス対策ソリューションを使って、コンプライアンスを確認します。

- **[スパイウェア対策]** :  
  - **[未構成]** ("*規定値*") - Intune により、デバイスにインストールされているスパイウェア対策ソリューションが確認されません。
  - **[必須]** - [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/) に登録されている Symantec や Microsoft Defender などのスパイウェア対策ソリューションを使って、コンプライアンスを確認します。  

### <a name="defender"></a>Defender

*Windows 10 Desktop では、次のコンプライアンス設定がサポートされています。*

- **Microsoft Defender マルウェア対策**:  
  - **未構成**(*既定*)-Intune はサービスを制御したり、既存の設定を変更したりしません。
  - **[必須]** -Microsoft Defender マルウェア対策サービスを有効にし、ユーザーが無効にできないようにします。

- **Microsoft Defender マルウェア対策の最小バージョン**:  
  Microsoft Defender マルウェア対策サービスの許可されている最小バージョンを入力してください。 たとえば、「`4.11.0.0`」と入力します。 空白のままにすると、Microsoft Defender マルウェア対策サービスのすべてのバージョンを使用できます。  

  *既定では、バージョンは構成されていません*。

- **Microsoft Defender マルウェア対策セキュリティインテリジェンスは最新**の状態です。  
  デバイス上の Windows セキュリティウイルスおよび脅威保護の更新を制御します。
  - **未構成**(*既定*)-Intune は要件を強制しません。
  - **必須**-Microsoft Defender セキュリティインテリジェンスを強制的に最新の状態にする。

  [Defender/Health/SignatureOutOfDate CSP](https://docs.microsoft.com/windows/client-management/mdm/defender-csp)
  
  詳細については、「 [Microsoft Defender ウイルス対策およびその他の microsoft マルウェア対策のセキュリティインテリジェンスの更新プログラム](https://www.microsoft.com/en-us/wdsi/defenderupdates)」を参照してください。

- **[リアルタイム保護]** :  
  - **未構成**(*既定*)-Intune はこの機能を制御したり、既存の設定を変更したりしません。
  - **[必須]** -マルウェア、スパイウェア、およびその他の望ましくないソフトウェアをスキャンするリアルタイム保護を有効にします。  

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

### <a name="microsoft-defender-advanced-threat-protection-rules"></a>Microsoft Defender Advanced Threat Protection のルール

- **[デバイスは、次のマシン リスク スコア以下であることが必要]** :  
  この設定は、脅威防御サービスからのリスク評価をコンプライアンスの条件とする場合に使用します。 許容される脅威の最大レベルを選択します。
  - **[未構成]** ("*既定値*")  
  - **[クリア]** - デバイスにはいかなる脅威も存在してはならないので、これはセキュリティ上最も安全なオプションです。 デバイスで何らかのレベルの脅威が検出された場合、非準拠と評価されます。
  - **[低]** - 存在する脅威が低レベルの場合のみ、デバイスは準拠として評価されます。 中レベル以上の脅威が存在する場合、デバイスは非準拠のステータスに分類されます。
  - **[中]** - デバイスに存在する脅威が低レベルまたは中レベルの場合、デバイスは準拠として評価されます。 デバイスで高レベルの脅威が検出された場合は、非準拠と判定されます。
  - **[高]** - 最も安全性の低いオプションであり、すべての脅威レベルが許容されます。 このソリューションをレポート目的のみで使用した場合、役立つ場合があります。
  
  脅威対策サービスとして Microsoft Defender ATP (Advanced Threat Protection) を設定するには、[条件付きアクセスによる Microsoft Defender ATP の有効化](advanced-threat-protection.md)に関するページを参照してください。


## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business では、**Windows 10 以降**のプラットフォームが使用されます。 Windows Holographic for Business は、以下の設定をサポートします。

- **システム セキュリティ** > **暗号化** > **デバイス上のデータ ストレージの暗号化**。

Microsoft HoloLens でデバイスの暗号化を確認するには、「[デバイスの暗号化を確認する](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption)」を参照してください。

## <a name="surface-hub"></a>Surface Hub

Surface Hub では **Windows 10 以降**のプラットフォームが使用されます。 Surface Hub は、コンプライアンスと条件付きアクセスの両方でサポートされます。 Surface Hub 上でこれらの機能を有効にするには、Intune で [Windows 10 の自動登録を有効](../enrollment/windows-enroll.md)にし (Azure Active Directory (Azure AD) が必要)、デバイス グループとして Surface Hub デバイスを対象とすることをお勧めします。 Surface Hub は、コンプライアンスおよび条件付きアクセスが機能するように Azure AD に参加している必要があります。

ガイダンスについては、「[Windows デバイスの登録をセットアップする](../enrollment/windows-enroll.md)」をご覧ください。

## <a name="next-steps"></a>次のステップ

- [非準拠デバイスに対するアクションを追加](actions-for-noncompliance.md)し、[スコープのタグを使用してポリシーをフィルター処理する](../fundamentals/scope-tags.md)
- [コンプライアンス ポリシーを監視する](compliance-policy-monitor.md)
- [Windows 8.1 デバイス向けのコンプライアンス ポリシー設定](compliance-policy-create-windows-8-1.md)を確認します。
