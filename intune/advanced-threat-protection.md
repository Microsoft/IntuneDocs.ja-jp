---
title: Microsoft Intune で Microsoft Defender ATP を使用する - Azure | Microsoft Docs
description: エンド ツー エンド シナリオでの Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) の有効化 (Intune および Microsoft Defender セキュリティ センターでの Microsoft Defender ATP の有効化など)、Microsoft Defender ATP 構成プロファイルを使用するデバイスのオンボード、Intune デバイス コンプライアンス ポリシーの作成、Azure AD 条件付きアクセス ポリシーの作成、デバイス コンプライアンスの監視を行う方法を確認します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af27a9b07434346a5425d0539759cb90ebf1ee6f
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68427084"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>Intune で条件付きアクセスによる Microsoft Defender ATP のコンプライアンスを強制する  

Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) と Microsoft Intune の連動により、セキュリティ違反を防ぎ、組織内での違反の影響を抑えることができます。

この機能は、以下に適用されます。Windows 10 デバイス

たとえば、誰かが組織内のユーザーに悪意のあるコードが埋め込まれた Word の添付ファイルを送信したとします。 そのユーザーは添付ファイルを開き、コンテンツを有効にします。 昇格された特権への攻撃が始まります。リモート コンピューターからの攻撃者は犠牲者のデバイスへの管理者権限を持ちます。 その後、攻撃者はそのユーザーの他のデバイスにリモートでアクセスします。

このセキュリティ違反が組織全体に影響する可能性があります。

Microsoft Defender ATP により、このシナリオのようなセキュリティ イベントを解決することができます。 Microsoft Defender セキュリティ センターにより、このデバイスは "高リスク" として報告され、不審なアクティビティに関する詳細なレポートが追加されます。 この例では、Microsoft Defender ATP によって、デバイスで異常なコードが実行され、プロセスの特権エスカレーションが発生し、悪意のあるコードが挿入され、不審なリモート シェルが発行されたことが検出されます。 その後、Microsoft Defender ATP によって脅威を緩和するためのオプションが提供されます。

Intune を使用することで、リスクの許容レベルを決定するコンプライアンス ポリシーを作成できます。 デバイスがこのリスクを超えた場合、そのデバイスは非準拠となります。 Azure Active Directory (AD) の条件付きアクセスと組み合わせて使用する場合、ユーザーによる企業リソースからのアクセスがブロックされます。

この記事では、以下の方法を示します。

- Microsoft Defender セキュリティ センターで Intune を有効にし、Intune で Microsoft Defender ATP を有効にする。 これらのタスクでは、Intune と Microsoft Defender ATP 間でサービス間の接続を作成します。 この接続により、Microsoft Defender ATP で Intune デバイスに対するマシン リスクを記述することができます。
- Intune でコンプライアンス ポリシーを作成する。
- 脅威レベルに基づいて、デバイス上の Azure Active Directory (AD) で条件付きアクセスを有効にする。

## <a name="prerequisites"></a>必要条件

Intune で Microsoft Defender ATP を使用する場合は、以下が構成済みであり、使用できる状態であることを確認してください。

- Enterprise Mobility + Security E3 および Windows E5 (または Microsoft 365 Enterprise E5) のライセンス済みテナント
- [Intune で管理されている](windows-enroll.md) Windows 10 デバイス (Azure AD にも参加している) を含む Microsoft Intune 環境
- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) および Microsoft Defender セキュリティ センター (ATP ポータル) へのアクセス

## <a name="enable-microsoft-defender-atp-in-intune"></a>Intune で Microsoft Defender ATP を有効にする

新しいアプリケーションを Intune Mobile Threat Defense に統合し、接続を有効にすると、Intune によって Azure Active Directory 内に従来の条件付きアクセス ポリシーが作成されます。 統合する各 MTD アプリ ([Defender ATP](advanced-threat-protection.md) や追加の [MTD パートナー](mobile-threat-defense.md#mobile-threat-defense-partners)など) によって、新しい従来の条件付きアクセス ポリシーが作成されます。  これらのポリシーは無視してもかまいませんが、編集、削除、または無効にすることはできません。

MTD アプリ用の従来の条件付きアクセス ポリシーは: 

- デバイスがデバイス ID を持つように Azure AD に登録されていることを必要とする Intune MTD によって使用されます。 ID は、デバイスが Intune に正常に自身の状態を報告できるようにするために必要です。  
- MTD の管理を支援するために作成する条件付きアクセス ポリシーとは異なります。
- 既定では、評価に使用する他の条件付きアクセス ポリシーとは対話しません。  

従来の条件付きアクセス ポリシーを表示するには、[Azure](https://portal.azure.com/#home) で **[Azure Active Directory]**  >  **[条件付きアクセス]**  >  **[クラシック ポリシー]** の順に移動します。

### <a name="to-enable-defender-atp"></a>Defender ATP を有効にするには
1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイスのポリシー準拠]**  >  **[Microsoft Defender ATP]** の順に選択してから、 *[コネクタの設定]* の下で **[Microsoft Defender セキュリティ センターを開く]** を選択します。

    ![選択して Microsoft Defender セキュリティ センターを開く](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. **Microsoft Defender セキュリティ センター**で次の操作を行います。
    1. **[設定]**  >  **[高度な機能]** の順に選択します。
    2. **Microsoft Intune の接続**については、次のように **[オン]** を選択します。

        ![Intune への接続を有効にする](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. **[環境設定の保存]** を選択します。

4. Intune に戻り、 **[デバイスのポリシー準拠]**  >  **[Microsoft Defender ATP]** の順に選択します。 **[Connect Windows devices version 10.0.15063 and above to Microsoft Defender ATP]\(Windows デバイス バージョン 10.0.15063 以上を Microsoft Defender ATP に接続する\)** を **[オン]** に設定します。
5. **[保存]** を選択します。

通常、このタスクは 1 回実行します。 そのため、Intune リソースで Microsoft Defender ATP が既に有効になっている場合は、もう一度実行する必要はありません。

## <a name="onboard-devices-using-a-configuration-profile"></a>構成プロファイルを使用してデバイスをオンボードする

エンドユーザーが Intune に登録すると、構成プロファイルを使用してデバイスにさまざまな設定をプッシュできます。 これは Microsoft Defender ATP にも適用されます。

Microsoft Defender ATP には、[Microsoft Defender ATP サービス](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)と通信してファイルをスキャンし、脅威を検出して、そのリスクを Microsoft Defender ATP に報告する、オンボード構成パッケージが含まれています。

オンボードすると、Intune により、Microsoft Defender ATP から自動生成された構成パッケージが取得されます。 Intune では、デバイスに構成プロファイルを送信するときに、そのデバイスに構成パッケージがプッシュされます。これにより、Microsoft Defender ATP でデバイスの脅威を監視できるようになります。

構成パッケージを使用してデバイスをオンボードすれば、再度オンボードする必要はありません。 [グループ ポリシーまたは System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) を使用して、デバイスをオンボードすることもできます。

### <a name="create-the-configuration-profile"></a>構成プロファイルを作成する

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択します。
3. **名前**と**説明**を入力します。
4. **[プラットフォーム]** では、 **[Windows 10 以降]** を選択します。
5. **[プロファイルの種類]** では、 **[Microsoft Defender ATP (Windows 10 デスクトップ)]** を選択します。
6. 次のように設定を構成します。

    - **[Microsoft Defender ATP クライアント構成パッケージの種類]** : **[Onboard]\(オンボード\)** を選択し、プロファイルに構成パッケージを追加します。 **[Offboard]** \(オフボード\) を選択し、プロファイルから構成パッケージを削除します。
  
    > [!NOTE]  
    > Microsoft Defender ATP との接続を適切に確立している場合、Intune によって自動的に構成プロファイルが**オンボード**され、 **[Microsoft Defender ATP クライアント構成パッケージの種類]** 設定は使用できなくなります。
  
    - **[すべてのファイルのサンプル共有]** : **[有効にする]** では、サンプルを収集し、Microsoft Defender ATP と共有できるようになります。 たとえば、疑わしいファイルがある場合、それを Microsoft Defender ATP に送信して詳しく分析できます。 **[未構成]** では、いかなるサンプルも Microsoft Defender ATP と共有されません。
    - **[テレメトリの報告頻度を早める]** :高リスクのデバイスがある場合は、この設定を **[有効にする]** を選択し、Microsoft Defender ATP サービスに対してより頻繁にテレメトリを報告させることができます。

    これらの Microsoft Defender ATP の設定について詳しくは、「[System Center Configuration Manager を使用する Windows 10 コンピューターのオンボード](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm)」をご覧ください。

7. **[OK]** 、 **[作成]** の順に選択して変更を保存します。これで、プロファイルが作成されます。

## <a name="create-the-compliance-policy"></a>コンプライアンス ポリシーを作成する
コンプライアンス ポリシーによって、デバイス上でのリスクの許容レベルが決まります。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイスのポリシー準拠]**  >  **[ポリシー]**  >  **[ポリシーの作成]** の順に選択します。
3. **名前**と**説明**を入力します。
4. **[プラットフォーム]** で、 **[Windows 10 以降]** を選択します。
5. **[Microsoft Defender ATP]** 設定で、 **[デバイスは、次のマシン リスク スコア以下であることが必要]** を使用したいレベルに設定します。 脅威レベルの分類は、[Microsoft Defender ATP によって決定されます](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue)。

   - **[クリア]** :このレベルはセキュリティ上最も安全です。 デバイスには既存のいかなる脅威も存在できず、引き続き会社のリソースにアクセスできます。 いずれかの脅威が見つかった場合、デバイスは非準拠と評価されます。 (Microsoft Defender ATP ユーザーの値は *[セキュア]* です。)
   - **[低]** :低レベルの脅威が存在する場合にのみ、デバイスは準拠しています。 脅威レベルが中または高のデバイスは非準拠になります。
   - **[中]** :デバイスに存在する脅威が低または中の場合、デバイスは準拠しています。 高レベルの脅威が検出された場合は、デバイスは非準拠と判定されます。
   - **[高]** :最も安全性の低いレベルであり、すべての脅威レベルが許容されます。 したがって、脅威レベルが高、中または低のデバイスは準拠していると見なされます。

6. **[OK]** 、 **[作成]** の順に選択して、変更を保存 (およびポリシーを作成) します。

## <a name="assign-the-policy"></a>ポリシーを割り当てる

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイスのポリシー準拠]**  >  **[ポリシー]** の順に選択し、使用する Microsoft Defender ATP コンプライアンス ポリシーを選択します。
3. **[割り当て]** を選択します。
4. ポリシーの割り当て対象として Azure AD グループを含めるか除外します。
5. グループにポリシーを展開するには、 **[保存]** を選択します。 ポリシーの対象となっているユーザー デバイスは、コンプライアンスが評価されます。

## <a name="create-a-conditional-access-policy"></a>条件付きアクセス ポリシーを作成する
デバイスが準拠していない "*場合*" は、条件付きアクセス ポリシーによって、リソースへのアクセスがブロックされます。 したがって、デバイスが脅威レベルを超えている場合は、SharePoint や Exchange Online などの企業リソースへのアクセスをブロックすることができます。  

> [!TIP]  
> 条件付きアクセスは、Azure Active Directory (Azure AD) テクノロジです。 *Intune* からアクセスされる条件付きアクセス ノードは、*Azure AD* からアクセスされるノードと同じです。  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[条件付きアクセス]**  >  **[新しいポリシー]** の順に選択します。
2. ポリシーの**名前**を入力して、 **[ユーザーとグループ]** を選択します。 含めるオプションまたは除外するオプションを使用して、ポリシーのグループを追加し、 **[完了]** を選択します。
3. **[クラウド アプリ]** を選択し、保護するアプリを選びます。 たとえば、 **[アプリを選択]** を選び、 **[Office 365 SharePoint Online]** と **[Office 365 Exchange Online]** を選択します。

    **[完了]** を選択して変更を保存します。

4. **[条件]**  >  **[クライアント アプリ]** の順に選択して、アプリとブラウザーにポリシーを適用します。 たとえば、 **[はい]** を選択し、 **[ブラウザー]** と **[モバイル アプリとデスクトップ クライアント]** を有効にします。

    **[完了]** を選択して変更を保存します。

5. **[許可]** を選択し、デバイスのコンプライアンスに基づいて条件付きアクセスを適用します。 たとえば、 **[アクセスの許可]**  >  **[デバイスは準拠しているとしてマーク済みである必要があります]** の順に選択します。

    **[選択]** を選んで変更を保存します。

6. **[ポリシーを有効にする]** 、 **[作成]** の順に選択して変更を保存します。

「[条件付きアクセスとは](conditional-access.md)」はお勧めのリソースです。

## <a name="monitor-device-compliance"></a>デバイス コンプライアンスを監視する
次に、Microsoft Defender ATP コンプライアンス ポリシーを持つデバイスの状態を監視します。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイスのポリシー準拠]**  >  **[ポリシーへの準拠]** の順に選択します。
3. 一覧から Microsoft Defender ATP ポリシーを探し、どのデバイスが準拠または非準拠なのかを確認します。

## <a name="more-good-stuff"></a>関連トピック
[Microsoft Defender ATP の条件付きアクセス](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)  
[Microsoft Defender ATP のリスク ダッシュボード](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)  

[デバイス コンプライアンス ポリシーの概要](device-compliance-get-started.md)  
[Azure AD の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)