---
title: Microsoft Intune でセキュリティのベースラインを使用する - Azure | Microsoft Docs
description: モバイル デバイス管理に Microsoft Intune を使用して、デバイス上のユーザーとデータを保護するために推奨されるグループ セキュリティ設定を追加または構成します。 BitLocker の有効化、Windows Defender Advanced Threat Protection の構成、Internet Explorer の制御、SmartScreen の使用、ローカル セキュリティ ポリシーの設定、パスワードの要求、インターネット ダウンロードのブロックなどを行います。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 70638228875f1fb063a2ea22dc424c00f3940a30
ms.sourcegitcommit: ef4bc7318449129af3dc8c0154e54a264b7bf4e5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65197622"
---
# <a name="create-a-windows-10-security-baseline-in-intune"></a>Intune で Windows 10 のセキュリティのベースラインを作成する

セキュリティのベースラインは、Windows 10 以降を実行しているデバイスで使用できるプレビュー段階の機能です。 この機能には、ユーザーとデバイスをセキュリティで保護するために使用できる、Intune によってサポートされる多数の設定が含まれています。 また、このような設定をセキュリティ チームの推奨値に自動的に設定します。 たとえば、ベースラインによって、BitLocker を自動的に有効にする、デバイスのロックを解除するためにパスワードを自動的に要求する、基本認証を自動的に無効にするなどの操作を実行できます。

この機能は、以下に適用されます。

- Windows 10 バージョン 1809 以降

> [!NOTE]
> セキュリティのベースラインはプレビュー段階ですが、Microsoft は運用環境でプロファイルを使用することをお勧めしません。プレビューの過程でベースラインが変更される可能性があるためです。 セキュリティ ベースラインが一般に使用できるようになったとき、既存のプロファイルがサポートされる最新のプロファイルに変換されることはありません。

セキュリティのベースラインを使用する目的は、Microsoft 365 を使用するときにエンドツーエンドのセキュリティで保護されたワークフローを提供することです。 次のような利点があります。

- セキュリティのベースラインには、セキュリティに影響を与える設定に関するベスト プラクティスと推奨事項が含まれています。 Intune は、グループ ポリシーのセキュリティのベースラインを作成する場合と同じ Windows セキュリティ チームとパートナー関係を結んでいます。 このような推奨事項はガイダンスと豊富な経験に基づいています。
- Intune の初心者で、どこから手を付けたらよいかわからない場合は、セキュリティのベースラインを使用すると便利です。 組織のリソースとデータの保護に役立つことがわかっているので、セキュリティで保護されたプロファイルをすばやく作成して展開できます。
- 現在グループ ポリシーを使用している場合は、このようなベースラインを使用すると、管理のために Intune に移行する作業がはるかに簡単になります。 このようなベースラインはネイティブで Intune に組み込まれており、最新の管理エクスペリエンスが含まれています。

セキュリティのベースラインによって、Intune に "構成プロファイル" が作成されます。 このプロファイルには、ベースラインのすべての設定が含まれています。 次に、このプロファイルをユーザー、グループ、およびデバイスに適用または割り当てます。

プロファイルが割り当てられたら、プロファイルを監視し、ベースラインを監視できます。 たとえば、ベースラインと一致するデバイスや、ベースラインと一致しないデバイスを確認できます。

この記事では、セキュリティのベースラインを使用してプロファイルを作成し、プロファイルを割り当て、プロファイルを監視する方法を説明します。

「[Windows セキュリティ基本計画](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines)」は、この機能の詳細を学ぶ際に役立つリソースです。 「[Mobile device management (モバイル デバイス管理)](https://docs.microsoft.com/windows/client-management/mdm/)」(MDM) は、MDM と、Windows デバイス上で実行できることに関する優れたリソースです。

## <a name="prerequisites"></a>必要条件
Intune でベースラインを管理するには、アカウントに [[Policy and Profile Manager]\(ポリシーとプロファイル マネージャー\)](role-based-access-control.md#built-in-roles) 組み込みロールが必要です。


## <a name="co-managed-devices"></a>共同管理デバイス

Intune マネージド デバイスに関するセキュリティのベースラインは、Configuration Manager との共同マネージド デバイスと似ています。 共同マネージド デバイスでは、System Center Configuration Manager と Microsoft Intune を使用して Windows 10 デバイスを同時に管理します。 これにより、既存の Configuration Manager への投資を Intune のメリットへとクラウドで結び付けることができます。 Configuration Manager を使用していて、クラウドのメリットも必要な場合、[共同管理の概要](https://docs.microsoft.com/sccm/comanage/overview)に関するページは優れたリソースです。

共同マネージド デバイスを使用する場合は、 **[デバイス構成]** ワークロード (その設定) を Intune に切り替える必要があります。 詳細については、[デバイス構成ワークロード](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration)に関するセクションを参照してください。

## <a name="create-the-profile"></a>プロファイルの作成

1. [Azure portal](https://portal.azure.com/) で、 **[すべてのサービス]** を選択し、**Intune** でフィルター処理して、 **[Intune]** を選択します。
2. **[デバイス セキュリティ]**  >  **[セキュリティのベースライン (プレビュー)]** を選択します。 使用できるベースラインの一覧が表示されます。 さらにベースラインが追加されると、次のように表示されます。

    ![現在使用できるセキュリティのベースラインの一覧を Intune で表示する](./media/security-baselines/available-baselines.png)

3. 使用するベースラインを選択し、 **[プロファイルの作成]** を選択します。
4. **[Basics]\(基本\)** で次のプロパティを入力します。

    - **名前**: セキュリティのベースライン プロファイルの名前を入力します。 たとえば、「`pilot Windows 10 MDM baseline - Oct 2018`」と入力します。
    - **説明**:このベースラインの実行内容を説明するテキストを入力します。 この説明には、任意のテキストを入力できます。 省略可能ですが、強く推奨されます。

5. **[設定]** を展開します。 一覧には、このセキュリティのベースラインのすべての設定と、その設定に自動的に設定されている実行内容が表示されます。 設定とその値は推奨値が指定されていますが、変更することができます。

    ![設定を展開すると、Intune のこのセキュリティのベースラインの設定がすべて表示されます。](./media/security-baselines/sample-list-of-settings.png)

    いくつかの設定を展開して値を確認してください。 たとえば、 **[Windows Defender]** を展開します。 いくつかの設定と、その設定されている実行内容を確認してください。

    ![Windows Defender 設定の一部に自動的に設定されている Intune の実行内容を表示する](./media/security-baselines/expand-windows-defender.png)

6. プロファイルを **[作成]** します。 
7. **[プロファイル]** を選択します。 プロファイルが作成され、一覧に表示されます。 ただし、まだ何も行われていません。 次に、プロファイルを割り当てます。

## <a name="assign-the-profile"></a>プロファイルを割り当てる

プロファイルが作成されたら、ユーザー、デバイス、グループに割り当てることができます。 割り当てると、プロファイルとその設定は、選択したユーザー、デバイス、グループに適用されます。

1. Intune で **[Security Baselines]\(セキュリティのベースライン\)** を選択し、ベースライン、 **[プロファイル]** の順に選択します。
2. プロファイル、 **[割り当て]** の順に選択します。

    ![Intune でセキュリティのベースライン プロファイルを選択し、プロファイルを展開する割り当てをクリックします](./media/security-baselines/assignments.png)

3. **[Intune]** タブで、このポリシーを適用するグループ、ユーザー、またはデバイスを追加します。

    > [!TIP]
    > グループを**除外**することもできる点に注意してください。 ポリシーを **[すべてのユーザー]** に適用する場合は、管理者グループを除外することを検討してください。 何かが起こった場合に、お客様とその管理者が締め出されないようにします。

4. 変更内容を**保存**します。

保存するとすぐに、デバイスの Intune へのチェックイン時にプロファイルがデバイスにプッシュされるようになります。 そのため、この処理はすぐに実行されます。

## <a name="available-security-baselines"></a>使用可能なセキュリティ ベースライン  

Intune では次のセキュリティ ベースラインを使用できます。
- **プレビュー:MDM セキュリティ ベースライン**
  - バージョン:[2018 年 10 月](security-baseline-settings-windows.md)

## <a name="q--a"></a>Q & A

#### <a name="why-these-settings"></a>これらの設定の理由を教えてください。

Microsoft セキュリティ チームは、これらの推奨事項を作成するために、Windows の開発者とセキュリティ コミュニティと長年にわたって直接協力してきました。 このベースラインの設定は、関連性の特に高いセキュリティ関連の構成オプションと考えられています。 Windows の新しいビルドごとに、チームは新しくリリースされた機能に基づいて推奨事項を調整しています。

#### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>Windows セキュリティのベースラインの推奨事項には、グループ ポリシーとIntune とで違いはありますか。

同じ Microsoft セキュリティ チームが、各ベースラインの設定を選択し、編成しています。 Intune には、Intune のセキュリティのベースラインに関連する設定がすべて含まれています。 グループ ポリシー ベースラインには、オンプレミス ドメイン コントローラーに固有の設定がいくつかあります。 このような設定は Intune の推奨事項から除外されています。 他の設定はすべて同じです。

#### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>Intune のセキュリティのベースラインは CIS または NSIT に準拠していますか。

厳密に言えば、"いいえ" です。 Microsoft セキュリティ チームは、CIS などの組織に、その推奨事項をまとめるように依頼しています。 ただし、"CIS 準拠" と Microsoft のベースラインは 1 対 1 で対応していません。

#### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Microsoft のセキュリティのベースラインにはどのような認定資格がありますか。 

- Microsoft は、グループ ポリシー (GPO) および [Security Compliance Toolkit](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10) 用のセキュリティのベースラインを長年にわたって公開し続けています。 これらのベースラインは多くの組織で使用されています。 これらのベースラインの推奨事項は、Microsoft セキュリティ チームと、米国国防総省 (DoD)、National Institute of Standards and Technology (NIST) などの企業のお客様および外部機関との関わりから得られたものです。 Microsoft の推奨事項とベースラインは、これらの組織と共有しています。 また、これらの組織には、Microsoft の推奨事項を厳密に反映した独自の推奨事項もあります。 モバイル デバイス管理 (MDM) がクラウドへと成長を続けた過程で、Microsoft はこのようなグループ ポリシーのベースラインと同等の MDM の推奨事項を作成しました。 このような追加のベースラインは Microsoft Intune に組み込まれており、ベースラインに準拠している (または準拠していない) ユーザー、グループ、およびデバイスに関するコンプライアンス レポートが含まれています。

- 多くのお客様は、Intune のベースラインの推奨事項を出発点として使用し、お客様の IT とセキュリティの要求を満たすようにカスタマイズしています。 Microsoft の Windows 10 RS5 **MDM のセキュリティのベースライン**が最初にリリースされました。 このベースラインは、CIS、NIST などの標準に基づいて、お客様が他のセキュリティのベースラインを最終的にインポートできるようにするための汎用のインフラストラクチャとして構築されています。 現在、これは Windows で利用できます。最終的には iOS と Android が含まれる予定です。

- Microsoft Intune と共に Azure Active Directory (AD) を使用して、オンプレミスの Active Directory グループ ポリシーから純粋なクラウド ソリューションに移行することは、1 つの旅です。 参考までに、ハイブリッド AD および Azure AD の参加デバイス向けに公開されているガイドの GPO があります。 このようなデバイスは、必要に応じてクラウド (Intune) から MDM 設定を取得し、オンプレミス ドメイン コントローラーからグループ ポリシー設定を取得できます。

## <a name="next-steps"></a>次の手順
- Intune でサポートされている [Windows セキュリティ ベースラインの設定](security-baseline-settings-windows.md)を確認します。  
- 状態を確認し、[ベースラインとプロファイル](security-baselines-monitor.md)を監視します。
