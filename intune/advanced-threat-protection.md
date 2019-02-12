---
title: Microsoft Intune - Azure で Windows Defender ATP を使用する | Microsoft Docs
description: Intune および Windows Defender Security Center (ATP ポータル) での ATP の有効化など、エンド ツー エンド シナリオで Windows Defender Advanced Threat Protection (ATP) を有効にする方法を確認します。さらに、ATP 構成プロファイルを使用するデバイスのオンボード、Intune デバイス コンプライアンス ポリシーの作成、Azure AD 条件付きアクセス ポリシーの作成、デバイス コンプライアンスの監視方法を確認します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 1/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: afa2ef4cf1199597f61af99d631243e2d3b51e64
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845178"
---
# <a name="enforce-compliance-for-windows-defender-atp-with-conditional-access-in-intune"></a>Intune で条件付きアクセスによる Windows Defender ATP の準拠を強制する

Windows Defender Advanced Threat Protection (ATP) と Microsoft Intune の連動により、セキュリティ違反を防ぎ、組織内の違反の影響を抑えることができます。

この機能は、以下に適用されます。Windows 10 デバイス

たとえば、誰かが組織内のユーザーに悪意のあるコードが埋め込まれた Word の添付ファイルを送信したとします。 そのユーザーは添付ファイルを開き、コンテンツを有効にします。 昇格された特権への攻撃が始まります。リモート コンピューターからの攻撃者は犠牲者のデバイスへの管理者権限を持ちます。 その後、攻撃者はそのユーザーの他のデバイスにリモートでアクセスします。

このセキュリティ違反が組織全体に影響する可能性があります。

Windows Defender ATP は、このシナリオのようなセキュリティ イベントを解決することができます。 Windows Defender セキュリティ センター (ATP コンソール) ではデバイスを "高リスク" として報告し、不審なアクティビティの詳細レポートに含めます。 この例では、Windows Defender ATP によって、デバイスで異常なコードが実行され、プロセス特権が昇格され、悪意のあるコードが挿入され、不審なリモート シェルが発行されたことが検出されます。 その後、Windows Defender ATP で脅威を緩和するためのオプションが示されます。

Intune を使用することで、リスクの許容レベルを決定するコンプライアンス ポリシーを作成できます。 デバイスがこのリスクを超えた場合、そのデバイスは非準拠となります。 Azure Active Directory (AD) の条件付きアクセスと組み合わせて使用する場合、ユーザーによる企業リソースからのアクセスがブロックされます。

この記事では、以下の方法を示します。

- ATP で Intune を有効にし、Intune で ATP を有効にする。 これらのタスクでは、Intune および Windows Defender ATP のサービス間の接続を作成します。 この接続では、Windows Defender ATP で Intune デバイスのコンピューター リスクを作成することができます。
- Intune でコンプライアンス ポリシーを作成する。
- 脅威レベルに基づいて、デバイス上の Azure Active Directory (AD) で条件付きアクセスを有効にする。

## <a name="prerequisites"></a>必要条件

Intune で ATP を使用する場合は、以下が構成済みであり、使用できる状態であることを確認してください。

- Enterprise Mobility + Security E3 および Windows E5 (または Microsoft 365 Enterprise E5) のライセンス済みテナント
- [Intune で管理されている](windows-enroll.md) Windows 10 デバイス (Azure AD にも参加している) を含む Microsoft Intune 環境
- [Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) および Windows Defender セキュリティ センター (ATP ポータル) へのアクセス

## <a name="enable-windows-defender-atp-in-intune"></a>Intune で Windows Defender ATP を有効にする

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイスのポリシー準拠]**、**[Windows Defender ATP]** > **[Windows Defender セキュリティ センターを開く]** の順に選択します。

    ![Windows Defender セキュリティ センターを選択して開く](./media/atp-device-compliance-open-windows-defender.png)

4. **Windows Defender セキュリティ センター**で、以下の操作を行います。
    1. **[設定]** > **[高度な機能]** の順に選択します。
    2. **Microsoft Intune の接続**については、次のように **[オン]** を選択します。

        ![Intune への接続を有効にする](./media/atp-security-center-intune-toggle.png)

    3. **[環境設定の保存]** を選択します。

5. Intune に戻り、**[デバイスのポリシー準拠]** > **[Windows Defender ATP]** の順に選択します。 **[Connect Windows devices version 10.0.15063 and above to Windows Defender ATP]\(Windows デバイス バージョン 10.0.15063 以上を Windows Defender ATP に接続する\)** を **[オン]** に設定します。
6. **[保存]** を選択します。

通常、このタスクは 1 回実行します。 したがって、Intune リソースで既に ATP が有効になっている場合は、再度実行する必要はありません。

## <a name="onboard-devices-using-a-configuration-profile"></a>構成プロファイルを使用してデバイスをオンボードする

エンドユーザーが Intune に登録すると、構成プロファイルを使用してデバイスにさまざまな設定をプッシュできます。 これは、Windows Defender ATP の場合もそうです。

Windows Defender には、[Windows Defender ATP サービス](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection)と通信してファイルをスキャンし、脅威を検出して、Windows Defender ATP にリスクを報告する、オンボード構成パッケージが含まれています。

オンボードされると、Intune は、Windows Defender ATP から自動生成された構成パッケージを取得します。 プロファイルがデバイスにプッシュされるか、展開されると、この構成パッケージもデバイスに自動的にプッシュされます。 これにより、Windows Defender ATP はデバイスへの脅威を監視するようになります。

構成パッケージを使用してデバイスをオンボードすれば、再度オンボードする必要はありません。 [グループ ポリシーまたは System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-windows-defender-advanced-threat-protection) を使用して、デバイスをオンボードすることもできます。

### <a name="create-the-configuration-profile"></a>構成プロファイルを作成する

1. **Azure Portal** で、[[すべてのサービス]](https://portal.azure.com) を選択し、**[Intune]** をフィルターとして適用して、**[Microsoft Intune]** を選びます。
2. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
3. **名前**と**説明**を入力します。
4. **[プラットフォーム]** では、**[Windows 10 以降]** を選択します。
5. **[プロファイルの種類]** では、**[Windows Defender ATP (Windows 10 デスクトップ)]** を選択します。
6. 次のように設定を構成します。

  - **[Windows Defender ATP client configuration package type]\(Windows Defender ATP クライアント構成パッケージの種類\)**:**[Onboard]\(オンボード\)** を選択し、プロファイルに構成パッケージを追加します。 **[Offboard]** \(オフボード\) を選択し、プロファイルから構成パッケージを削除します。
  
    > [!NOTE] 
    > Windows Defender ATP との接続を適切に確立している場合、Intune によって自動的に構成プロファイルが**オンボード**されるので、**[Windows Defender ATP client configuration package type]\(Windows Defender ATP クライアント構成パッケージの種類\)** の設定はできません。
  
  - **[すべてのファイルのサンプル共有]**:**[有効にする]** では、サンプルを収集し、Windows Defender ATP と共有できるようにします。 たとえば、疑わしいファイルがある場合、Windows Defender ATP に送信して詳しく分析できます。 **[構成されていません]** では、いかなるサンプルも Windows Defender ATP と共有されません。
  - **[テレメトリの報告頻度を早める]**:高リスクのデバイスがある場合は、この設定を**有効**にして、Windows Defender ATP サービスにより頻繁にテレメトリを報告することができます。

    これらの Windows Defender ATP の設定の詳細については、[System Center Configuration Manager を使用する Windows 10 コンピューターのオンボード](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-sccm-windows-defender-advanced-threat-protection)に関するページを参照してください。

7. **[OK]**、**[作成]** の順に選択して変更を保存します。これで、プロファイルが作成されます。

## <a name="create-the-compliance-policy"></a>コンプライアンス ポリシーを作成する
コンプライアンス ポリシーによって、デバイス上でのリスクの許容レベルが決まります。

1. **Azure Portal** で、[[すべてのサービス]](https://portal.azure.com) を選択し、**[Intune]** をフィルターとして適用して、**[Microsoft Intune]** を選びます。
2. **[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** の順に選択します。
3. **名前**と**説明**を入力します。
4. **[プラットフォーム]** で、**[Windows 10 以降]** を選択します。
5. **[Windows Defender ATP]** 設定で、**[Require the device to be at or under the machine risk score]\(デバイスは、コンピューターのリスク スコア以下であることが必要\)** を次の任意のレベルに設定します。

  - **[クリア]**:このレベルはセキュリティ上最も安全です。 デバイスに既存のいかなる脅威も存在できず、デバイスからは引き続き会社のリソースにアクセスできます。 いずれかの脅威が見つかった場合、デバイスは非準拠と評価されます。
  - **[低]**:低レベルの脅威が存在する場合にのみ、デバイスは準拠しています。 脅威レベルが中または高のデバイスは非準拠になります。
  - **[中]**:デバイスに存在する脅威が低または中の場合、デバイスは準拠しています。 高レベルの脅威が検出された場合は、デバイスは非準拠と判定されます。
  - **[高]**:最も安全性の低いレベルであり、すべての脅威レベルが許容されます。 したがって、脅威レベルが高、中または低のデバイスは準拠していると見なされます。

6. **[OK]**、**[作成]** の順に選択して、変更を保存 (およびポリシーを作成) します。

## <a name="assign-the-policy"></a>ポリシーを割り当てる

1. **Azure Portal** で、[[すべてのサービス]](https://portal.azure.com) を選択し、**[Intune]** をフィルターとして適用して、**[Microsoft Intune]** を選びます。
2. **[デバイスのポリシー準拠]** > **[ポリシー]** > Windows Defender ATP コンプライアンス ポリシーの順に選択します。
3. **[割り当て]** を選択します。
4. ポリシーの割り当て対象として Azure AD グループを含めるか除外します。
5. グループにポリシーを展開するには、**[保存]** を選択します。 ポリシーの対象となっているユーザー デバイスは、コンプライアンスが評価されます。

## <a name="create-an-azure-ad-conditional-access-policy"></a>Azure AD 条件付きアクセス ポリシーを作成する
デバイスが準拠していない*場合* は、条件付きアクセス ポリシーによって、リソースへのアクセスがブロックされます。 したがって、デバイスが脅威レベルを超えている場合は、SharePoint や Exchange Online などの企業リソースへのアクセスをブロックすることができます。

1. [Azure Portal](https://portal.azure.com) で、**[Azure Active Directory]** > **[条件付きアクセス]** > **[新しいポリシー]** の順に開きます。
2. ポリシーの**名前**を入力して、**[ユーザーとグループ]** を選択します。 含めるオプションまたは除外するオプションを使用して、ポリシーのグループを追加し、**[完了]** を選択します。
3. **[クラウド アプリ]** を選択し、保護するアプリを選びます。 たとえば、**[アプリを選択]** を選び、**[Office 365 SharePoint Online]** と **[Office 365 Exchange Online]** を選択します。

    **[完了]** を選択して変更を保存します。

4. **[条件]** > **[クライアント アプリ]** の順に選択して、アプリとブラウザーにポリシーを適用します。 たとえば、**[はい]** を選択し、**[ブラウザー]** と **[モバイル アプリとデスクトップ クライアント]** を有効にします。

    **[完了]** を選択して変更を保存します。

5. **[許可]** を選択し、デバイスのコンプライアンスに基づいて条件付きアクセスを適用します。 たとえば、**[アクセスの許可]** > **[デバイスは準拠しているとしてマーク済みである必要があります]** の順に選択します。

    **[選択]** を選んで変更を保存します。

6. **[ポリシーを有効にする]**、**[作成]** の順に選択して変更を保存します。

「[条件付きアクセスとは](conditional-access.md)」は適切なリソースです。

## <a name="monitor-device-compliance"></a>デバイス コンプライアンスを監視する
次に、Windows Defender ATP コンプライアンス ポリシーを持つデバイスの状態を監視します。

1. **Azure Portal** で、[[すべてのサービス]](https://portal.azure.com) を選択し、**[Intune]** をフィルターとして適用して、**[Microsoft Intune]** を選びます。
2. **[デバイスのポリシー準拠]** > **[ポリシーへの準拠]** の順に選択します。
3. 一覧で Windows Defender ATP ポリシーを見つけ、準拠しているデバイスまたは準拠していないデバイスを確認します。

## <a name="more-good-stuff"></a>関連トピック
[Windows Defender ATP の条件付きアクセス](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/conditional-access-windows-defender-advanced-threat-protection)  
[Windows Defender ATP のリスク ダッシュボード](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection)  
[デバイス コンプライアンス ポリシーの概要](device-compliance-get-started.md)  
[Azure AD の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
