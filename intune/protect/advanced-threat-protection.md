---
title: Microsoft Intune で Microsoft Defender ATP を使用する - Azure | Microsoft Docs
description: Intune で Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) を使用して (設定と構成も含みます)、Intune デバイスを ATP にオンボードしてから、Intune デバイス コンプライアンスを使用したデバイスの ATP リスク評価と、条件付きアクセス ポリシーを使用して、ネットワーク リソースを保護します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6026cf3ef8d044c92680cf4c4c88ba55c9777e0
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713250"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>Intune で条件付きアクセスによる Microsoft Defender ATP のコンプライアンスを強制する

Mobile Threat Defense ソリューションとして Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) を Microsoft Intune と統合できます。 統合することで、セキュリティ侵害を防止し、組織内での侵害の影響を抑えることができます。 Microsoft Defender ATP は、Windows 10 以降を稼働しているデバイスで動作します。

正しく設定するには、以下の構成を同時に使用します。

- **Intune と Microsoft Defender ATP の間にサービス間接続を確立する**。 この接続により、Microsoft Defender ATP が Intune で管理する Windows 10 デバイスからコンピューターのリスクに関するデータを収集できるようになります。
- **デバイス構成プロファイルを使用して、デバイスを Microsoft Defender ATP にオンボードする**。 デバイスをオンボードして、Microsoft Defender ATP と通信を行い、そのリスク レベルを評価するのに役立つデータを提供するようにそれらを構成します。
- **デバイス コンプライアンス ポリシーを使用して、許可するリスクのレベルを設定する**。 リスク レベルは Microsoft Defender ATP によって報告されます。  許可したリスク レベルを超えているデバイスは、非準拠として識別されます。
- **条件付きアクセス ポリシーを使用**して、ユーザーが非準拠のデバイスから企業リソースにアクセスできないようにします。

Intune を Microsoft Defender ATP と統合する場合、ATP の脅威と脆弱性の管理 (TVM) を利用し、[Intune を使って TVM によって検出されたエンドポイントの脆弱性を修復](atp-manage-vulnerabilities.md)できます。

## <a name="example-of-using-microsoft-defender-atp-with-intune"></a>Intune で Microsoft Defender ATP を使用する例

以下の例は、これらのソリューションを連携させて組織を保護するしくみを説明するのに役立ちます。 この例では、Microsoft Defender ATP と Intune は既に統合されています。

誰かが、組織内のユーザーに、悪意のあるコードが埋め込まれた Word の添付ファイルを送信する、というイベントを考えてみましょう。

- そのユーザーは添付ファイルを開き、コンテンツを有効にします。
- 昇格された特権への攻撃が始まります。リモート コンピューターからの攻撃者は犠牲者のデバイスへの管理者権限を持ちます。
- その後、攻撃者はそのユーザーの他のデバイスにリモートでアクセスします。 このセキュリティ違反が組織全体に影響する可能性があります。

Microsoft Defender ATP は、このシナリオのようなセキュリティ イベントを解決するのに役立ちます。

- この例では、Microsoft Defender ATP によって、デバイスで異常なコードが実行され、プロセスの特権エスカレーションが発生し、悪意のあるコードが挿入され、不審なリモート シェルが発行されたことが検出されます。
- デバイスからのこのようなアクションに基づいて、Microsoft Defender ATP により[そのデバイスは危険度が高いと分類され](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue#severity)、Microsoft Defender セキュリティ センターのポータルに疑わしいアクティビティに関する詳細なレポートが追加されます。

リスク レベルが "*中*" または "*高*" であるデバイスを非準拠として分類する Intune デバイス コンプライアンス ポリシーを使用しているため、侵害されたデバイスは非準拠として分類されます。 この分類により、条件付きアクセス ポリシーが適用されて、そのデバイスから企業リソースへのアクセスがブロックされます。

## <a name="prerequisites"></a>必要条件

Intune で Microsoft Defender ATP を使用する場合は、以下が構成済みであり、使用できる状態であることを確認してください。

- Enterprise Mobility + Security E3 および Windows E5 (または Microsoft 365 Enterprise E5) のライセンス済みテナント
- [Intune で管理されている](../enrollment/windows-enroll.md) Windows 10 デバイス (Azure AD にも参加している) を含む Microsoft Intune 環境
- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) および Microsoft Defender セキュリティ センター (ATP ポータル) へのアクセス

> [!NOTE]
> Microsoft Defender ATP は、Intune アプリ保護ポリシーではサポートされていません。

## <a name="enable-microsoft-defender-atp-in-intune"></a>Intune で Microsoft Defender ATP を有効にする

実行する最初の手順は、Intune と Microsoft Defender ATP の間にサービス間接続を設定することです。 これには、Microsoft Defender セキュリティ センターと Intune の両方に対する管理アクセス権が必要です。

### <a name="to-enable-defender-atp"></a>Defender ATP を有効にするには

Defender ATP を有効にする必要があるのは、テナントごとに 1 回だけです。 

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[エンドポイント セキュリティ]** 、 **[Microsoft Defender ATP]** の順に選択し、 **[Microsoft Defender セキュリティ センターを開く]** を選択します。

   ![選択して Microsoft Defender セキュリティ センターを開く](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. **Microsoft Defender セキュリティ センター**で次の操作を行います。
    1. **[設定]**  >  **[高度な機能]** の順に選択します。
    2. **Microsoft Intune の接続**については、次のように **[オン]** を選択します。

        ![Intune への接続を有効にする](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. **[環境設定の保存]** を選択します。

4. Microsoft Endpoint Manager 管理センターで **Microsoft Defender ATP** に戻ります。 **[MDM コンプライアンス ポリシー設定]** の下で **[Connect Windows devices version 10.0.15063 and above to Microsoft Defender ATP]\(Windows デバイス バージョン 10.0.15063 以上を Microsoft Defender ATP に接続する\)** を **[オン]** に設定します。

5. **[保存]** を選択します。

> [!TIP]
> 新しいアプリケーションを Intune Mobile Threat Defense に統合し、Intune への接続を有効にすると、Intune によって Azure Active Directory 内に従来の条件付きアクセス ポリシーが作成されます。 統合する各 MTD アプリ ([Defender ATP](advanced-threat-protection.md) や追加の [MTD パートナー](mobile-threat-defense.md#mobile-threat-defense-partners)など) によって、新しい従来の条件付きアクセス ポリシーが作成されます。 これらのポリシーは無視してもかまいませんが、編集、削除、または無効にすることはできません。
>
> MTD アプリ用の従来の条件付きアクセス ポリシーは:
>
> - デバイスが Azure AD に登録され、MTD パートナーと通信する前にデバイス ID を持っていることを要求するために、Intune MTD によって使用されます。 ID は、デバイスが Intune に正常に自身の状態を報告できるようにするために必要です。
> - 他のクラウド アプリやリソースには影響しません。
> - MTD の管理を支援するために作成する条件付きアクセス ポリシーとは異なります。
> - 既定では、評価に使用する他の条件付きアクセス ポリシーとは対話しません。
>
> 従来の条件付きアクセス ポリシーを表示するには、[Azure](https://portal.azure.com/#home) で **[Azure Active Directory]**  >  **[条件付きアクセス]**  >  **[クラシック ポリシー]** の順に移動します。

## <a name="onboard-devices-by-using-a-configuration-profile"></a>構成プロファイルを使用してデバイスをオンボードする

Intune と Microsoft Defender ATP の間にサービス間接続を確立したら、Intune の管理対象デバイスを ATP にオンボードして、そのリスク レベルに関するデータを収集して使用できるようにします。 デバイスをオンボードするには、Microsoft Defender ATP のデバイス構成プロファイルを使用します。

Microsoft Defender ATP への接続を確立したときに、Intune は Microsoft Defender ATP から Microsoft Defender ATP のオンボード構成パッケージを受け取りました。 このパッケージは、デバイス構成プロファイルを使用してデバイスに展開されます。 この構成パッケージによってデバイスが構成され、[Microsoft Defender ATP サービス](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)と通信し、ファイルのスキャン、脅威の検出、Microsoft Defender ATP へのリスクの報告が行われるようになります。

構成パッケージを使用してデバイスをオンボードした後は、再度これを行う必要はありません。 [グループ ポリシーまたは System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) を使用して、デバイスをオンボードすることもできます。

### <a name="create-the-device-configuration-profile"></a>デバイス構成プロファイルの作成

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。
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
8. Microsoft Defender ATP を使用して評価するデバイスに[デバイス構成プロファイルを割り当てます](../configuration/device-profile-assign.md)。  

## <a name="create-and-assign-the-compliance-policy"></a>コンプライアンス ポリシーを作成して割り当てる

コンプライアンス ポリシーによって、デバイスに対して許容可能と見なすリスク レベルが決まります。

### <a name="create-the-compliance-policy"></a>コンプライアンス ポリシーを作成する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** 、 **[コンプライアンス ポリシー]** 、 **[ポリシーの作成]** の順に選択します。
3. **名前**と**説明**を入力します。
4. **[プラットフォーム]** で、 **[Windows 10 以降]** を選択します。
5. **[設定]** で、 **[Microsoft Defender ATP]** を選択します。
6. **[デバイスは、次のマシン リスク スコア以下であることが必要]** を目的のレベルに設定します。

   脅威レベルの分類は、[Microsoft Defender ATP によって決定されます](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue)。

   - **[クリア]** :このレベルはセキュリティ上最も安全です。 デバイスには既存のいかなる脅威も存在できず、引き続き会社のリソースにアクセスできます。 いずれかの脅威が見つかった場合、デバイスは非準拠と評価されます。 (Microsoft Defender ATP ユーザーの値は *[セキュア]* です。)
   - **[低]** :低レベルの脅威が存在する場合にのみ、デバイスは準拠しています。 脅威レベルが中または高のデバイスは非準拠になります。
   - **[中]** :デバイスに存在する脅威が低または中の場合、デバイスは準拠しています。 高レベルの脅威が検出された場合は、デバイスは非準拠と判定されます。
   - **[高]** :最も安全性の低いレベルであり、すべての脅威レベルが許容されます。 したがって、脅威レベルが高、中または低のデバイスは準拠していると見なされます。

7. **[OK]** 、 **[作成]** の順に選択して、変更を保存 (およびポリシーを作成) します。
8. 該当するグループに[デバイス コンプライアンス ポリシーを割り当てます](create-compliance-policy.md#assign-the-policy)。

## <a name="create-a-conditional-access-policy"></a>条件付きアクセス ポリシーを作成する

条件付きアクセス ポリシーによって、コンプライアンス ポリシーで設定した脅威レベルを超えたデバイスによるリソースへのアクセスがブロックされます。 デバイスから企業リソース (SharePoint や Exchange Online など) へのアクセスをブロックできます。

> [!TIP]
> 条件付きアクセスは、Azure Active Directory (Azure AD) テクノロジです。 Microsoft Endpoint Manager 管理センターからアクセスされる条件付きアクセス ノードは、*Azure AD* からアクセスされるものと同じノードです。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[エンドポイント セキュリティ]** 、 **[条件付きアクセス]** 、 **[新しいポリシー]** の順に選択します。

3. ポリシーの**名前**を入力して、 **[ユーザーとグループ]** を選択します。 含めるオプションまたは除外するオプションを使用して、ポリシーのグループを追加し、 **[完了]** を選択します。

4. **[クラウド アプリ]** を選択し、保護するアプリを選びます。 たとえば、 **[アプリを選択]** を選び、 **[Office 365 SharePoint Online]** と **[Office 365 Exchange Online]** を選択します。

   **[完了]** を選択して変更を保存します。

5. **[条件]**  >  **[クライアント アプリ]** の順に選択して、アプリとブラウザーにポリシーを適用します。 たとえば、 **[はい]** を選択し、 **[ブラウザー]** と **[モバイル アプリとデスクトップ クライアント]** を有効にします。

   **[完了]** を選択して変更を保存します。

6. **[許可]** を選択し、デバイスのコンプライアンスに基づいて条件付きアクセスを適用します。 たとえば、 **[アクセスの許可]**  >  **[デバイスは準拠しているとしてマーク済みである必要があります]** の順に選択します。

    **[選択]** を選んで変更を保存します。

7. **[ポリシーを有効にする]** 、 **[作成]** の順に選択して変更を保存します。

## <a name="monitor-device-compliance"></a>デバイス コンプライアンスを監視する

次に、Microsoft Defender ATP コンプライアンス ポリシーを持つデバイスの状態を監視します。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[デバイス]** 、 **[モニター]** 、 **[ポリシー コンプライアンス]** の順に選択します。

3. 一覧から Microsoft Defender ATP ポリシーを探し、どのデバイスが準拠または非準拠なのかを確認します。

## <a name="view-onboarding-status"></a>オンボードの状態を表示する

Intune で管理されているすべての Windows 10 デバイスのオンボードの状態を確認するには、 **[デバイスのポリシー準拠]**  >  **[Microsoft Defender ATP]** に移動します。 このページから、さらに多くのデバイスを Microsoft Defender ATP にオンボードするためのデバイス構成プロファイルの作成を開始することもできます。

## <a name="next-steps"></a>次の手順

[Microsoft Defender ATP の条件付きアクセス](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)

[Microsoft Defender ATP のリスク ダッシュボード](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)

[ATP の脆弱性の管理を使用したセキュリティ タスクを使用して、デバイスの問題を修復する](atp-manage-vulnerabilities.md)。

[デバイス コンプライアンス ポリシーの概要](device-compliance-get-started.md)
