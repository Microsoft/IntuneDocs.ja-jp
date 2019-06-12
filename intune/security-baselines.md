---
title: Microsoft Intune でセキュリティのベースラインを使用する - Azure | Microsoft Docs
description: モバイル デバイス管理に Microsoft Intune を使用して、デバイス上のユーザーとデータを保護するために推奨されるグループ セキュリティ設定を追加または構成します。 BitLocker の有効化、Microsoft Defender Advanced Threat Protection の構成、Internet Explorer の制御、SmartScreen の使用、ローカル セキュリティ ポリシーの設定、パスワードの要求、インターネット ダウンロードのブロックなどを行います。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e4d5c23d598641256c196cd7217797f87f99d1c
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66374128"
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

この記事では、セキュリティ ベースラインを使用してプロファイルを作成し、プロファイルを割り当て、プロファイルを監視する方法を説明します。

「[Windows セキュリティ基本計画](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines)」は、この機能の詳細を学ぶ際に役立つリソースです。 「[Mobile device management (モバイル デバイス管理)](https://docs.microsoft.com/windows/client-management/mdm/)」(MDM) は、MDM と、Windows デバイス上で実行できることに関する優れたリソースです。

## <a name="available-security-baselines"></a>使用可能なセキュリティ ベースライン  

Intune では、次のセキュリティ ベースラインを使用できます。
- **プレビュー:2018 年 10 月の MDM セキュリティ ベースライン**  
  [設定を表示する](security-baseline-settings-windows.md)

- **プレビュー:Windows Defender ATP ベースライン**  
  [設定を表示する](security-baseline-settings-defender-atp.md)  
  " *(ご使用の環境が [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites) を使用するための前提条件を満たしている場合は、このベースラインを使用できます)* "。


## <a name="prerequisites"></a>必要条件
Intune でベースラインを管理するには、アカウントに [[Policy and Profile Manager]\(ポリシーとプロファイル マネージャー\)](role-based-access-control.md#built-in-roles) 組み込みロールが必要です。


## <a name="co-managed-devices"></a>共同管理デバイス

Intune マネージド デバイスに関するセキュリティのベースラインは、Configuration Manager との共同マネージド デバイスと似ています。 共同マネージド デバイスでは、System Center Configuration Manager と Microsoft Intune を使用して Windows 10 デバイスを同時に管理します。 これにより、既存の Configuration Manager への投資を Intune のメリットへとクラウドで結び付けることができます。 Configuration Manager を使用していて、クラウドのメリットも必要な場合、[共同管理の概要](https://docs.microsoft.com/sccm/comanage/overview)に関するページは優れたリソースです。

共同マネージド デバイスを使用する場合は、 **[デバイス構成]** ワークロード (その設定) を Intune に切り替える必要があります。 詳細については、[デバイス構成ワークロード](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration)に関するセクションを参照してください。

## <a name="create-the-profile"></a>プロファイルの作成

1. [[Intune]](https://go.microsoft.com/fwlink/?linkid=20909) にサインインして、 **[デバイスのセキュリティ]**  >  **[セキュリティのベースライン (プレビュー)]** を選択します。 使用できるベースラインの一覧が表示されます。 

    ![構成するセキュリティ ベースラインを選択する](./media/security-baselines/available-baselines.png)

   >[!TIP]  
   > ご使用の環境が [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites) を使用するための前提条件を満たしている場合は、Windows Defender ATP ベースラインを使用できます。
2. 使用するベースラインを選択して、 **[プロファイルの作成]** を選択します。  

3. **[基本]** タブ上で、次のプロパティを指定します。

    - **名前**: セキュリティのベースライン プロファイルの名前を入力します。 たとえば、「*Standard profile for Defender ATP*」(Defender ATP 用の標準プロファイル) と入力します
    - **説明**:このベースラインの実行内容を説明するテキストを入力します。 この説明には、任意のテキストを入力できます。 省略可能ですが、強く推奨されます。

4. **[構成]** タブを選択して、このベースラインで利用可能な **[設定]** のグループを表示します。 グループを選択して展開し、含まれている個々の設定を表示します。 設定には、セキュリティ ベースラインに対する既定の構成があります。 ビジネス ニーズに合うように、既定の設定を再構成します。  

    ![グループを展開してそのグループに対する設定を表示する](./media/security-baselines/sample-list-of-settings.png)

5. **[割り当て]** タブを選択して、ベースラインをグループに割り当てます。 既存のグループにベースラインを割り当てるか、または Intune コンソール内の標準プロセスを使用して新しいグループを作成し、構成を完了します。  

   ![プロファイルを割り当てる](./media/security-baselines/assignments.png)
  
6. ベースラインをデプロイする準備が整ったら、 **[Review + create]\(確認と作成\)** タブを選択して、ベースラインの詳細を確認します。 その後、 **[プロファイルの保存]** を選択して、プロファイルを保存してデプロイします。 

   ![ベースラインを確認する](./media/security-baselines/review.png) 

   保存するとすぐに、デバイスの Intune へのチェックイン時にプロファイルがデバイスにプッシュされるようになります。 そのため、この処理はすぐに実行されます。

   > [!TIP]  
   > プロファイルは、最初にグループに割り当てなくても、保存することができます。 後からプロファイルを編集して、グループに追加できます。 

7. プロファイルを作成した後に、 **[デバイス セキュリティ]**  >  **[Security baselines]\(セキュリティ ベースライン\)** の順に移動して編集を行い、構成したベースラインを選択して、 **[プロファイル]** を選択します。  プロファイルを選択してから、 **[プロパティ]** を選択して設定を編集し、 **[割り当て]** を選択してこのベースラインを受信するグループを編集します。 

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
