---
title: チュートリアル - Microsoft Endpoint Manager の Intune のチュートリアル
titleSuffix: Microsoft Intune
description: このチュートリアルでは、Microsoft Endpoint Manager 管理センターで Microsoft Intune のツアーを開始し、タスクを実行する方法について理解を深めます。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune from the Microsoft Endpoint Manager admin center.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d8950e57c2427c522d337807d315ed5c399c0d5
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514083"
---
# <a name="tutorial-walkthrough-intune-in-microsoft-endpoint-manager"></a>チュートリアル:Microsoft Endpoint Manager の Intune のチュートリアル

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) には、クラウド コンピューティングのさまざまなシナリオと可能性を支援する 100 を超えるサービスが含まれています。 Microsoft Intune は、Azure で利用できるサービスの 1 つです。 Intune を利用すると、会社のデバイス、アプリ、データが会社のセキュリティ要件を確実に満たすようにできます。 確認する必要がある要件や、それらの要件が満たされない場合の対応の設定を制御できます。 [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)には、Microsoft Intune サービス、およびその他のデバイス管理関連の設定があります。 Intune で使用できる機能を理解しておくと、モバイル デバイス管理 (MDM) とモバイル アプリケーション管理 (MAM) のさまざまなタスクを実行するときに役に立ちます。

> [!NOTE]
> Microsoft エンドポイント マネージャーは、すべてのエンドポイントを管理するための単一の統合エンドポイント管理プラットフォームです。 この Microsoft Endpoint Manager 管理センターでは、ConfigMgr と Microsoft Intune が統合されています。

このチュートリアルでは次のことを行います。
> [!div class="checklist"]
> * Microsoft Endpoint Manager 管理センターのツアーを開始する
> * Microsoft Endpoint Manager 管理センターの表示をカスタマイズする

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

## <a name="prerequisites"></a>[前提条件]
Microsoft Intune を設定する前に、次の要件を確認してください。

- [サポートされるオペレーティング システムとブラウザー](../supported-devices-browsers.md) 
- [ネットワーク構成の要件と帯域幅](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Microsoft Intune の無料試用版にサインアップ

Intune は 30 日間無料で試用できます。 既に職場または学校アカウントがある場合は、そのアカウントで**サインイン**し、Intune をサブスクリプションに追加します。 それ以外の場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)して、組織で Intune を使うことができます。

> [!IMPORTANT]
> 新しいアカウントにサインアップした後で、既存の職場または学校アカウントを組み合わせることはできません。

## <a name="tour-microsoft-intune-in-the-microsoft-endpoint-manager-admin-center"></a>Microsoft Endpoint Manager 管理センターで Microsoft Intune のツアーを開始する

Microsoft Endpoint Manager 管理センターの Intune について理解を深めるには、以下の手順に従います。 ツアーを終えると、Intune のいくつかの主要な領域について理解が深まります。

1. ブラウザーを開き、[Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。 Intune を初めて使う場合は、無料試用版サブスクリプションを使用します。

    ![Microsoft Endpoint Manager 管理センターの [ホーム ページ] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-01.png)

    Microsoft Endpoint Manager や他のサービスを Azure で開くと、ウィンドウにそのサービスが表示されます。 Intune で最初に使用する可能性のあるワークロードには、 **[デバイス]** 、 **[アプリ]** 、 **[ユーザー]** 、 **[グループ]** などが含まれます。 ワークロードは、サービスのサブ領域に過ぎません。 ワークロードを選択すると、そのウィンドウがページ全体に表示されます。 他のブレードは開くときにブレードの右側から引き出され、閉じると前のウィンドウが表示されます。 

    既定では、Microsoft Endpoint Manager を開くと、 **[ホーム ページ]** ウィンドウが表示されます。 このウィンドウでは、テナントの状態とコンプライアンスの状態の全体的なビジュアル スナップショットと、その他の便利な関連リンクが提供されます。

2. ナビゲーション ウィンドウから、 **[ダッシュボード]** を選択して、Intune テナント内のデバイスとクライアント アプリの全体的な詳細を表示します。 新しい Intune テナントを始めたばかりの場合は、まだ登録されているデバイスはありません。 

    ![Microsoft Endpoint Manager 管理センターの [ダッシュボード] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-02.png)
    
    Intune では、従業員のデバイスやアプリによる会社のデータへのアクセス方法などを管理できます。 このモバイル デバイス管理 (MDM) サービスを使用するには、最初にデバイスを Intune に登録する必要があります。 デバイスが登録されると、MDM 証明書が発行されます。 この証明書を使用して、Intune サービスと通信します。 

    従業員のデバイスを Intune に登録する方法は複数あります。 各方法は、デバイスの所有権 (個人または会社)、デバイスの種類 (iOS/iPadOS、Windows、Android)、管理要件 (リセット、アフィニティ、ロック) によって異なります。 ただし、デバイスを登録するには、その前に Intune インフラストラクチャを設定する必要があります。 特に、デバイスの登録には [MDM 機関を設定する](mdm-authority-set.md)必要があります。 Intune 環境 (テナント) の準備について詳しくは、「[Intune をセットアップする](setup-steps.md)」をご覧ください。 Intune テナントの準備が済むと、デバイスを登録できます。 デバイスの登録について詳しくは、「[デバイス登録とは](../enrollment/device-enrollment.md)」をご覧ください

3. ナビゲーション ウィンドウから、 **[デバイス]** を選択し、Intune テナント内の登録済みデバイスの詳細を表示します。 

    > [!TIP]
    > 以前に Azure portal で Intune を使用したことがある場合は、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[デバイス]** を選択することで、Azure portal に上記の詳細が表示されます。

    **[デバイス] - [概要]** ウィンドウには、次の状態とアラートの概要を表示できるタブがいくつかあります。
    - **登録の状態** - プラットフォーム別の Intune に登録されたデバイスと、登録エラーの詳細を確認します。
    - **登録のアラート** - プラットフォーム別の割り当てられていないデバイスについて、さらに詳しく確認します。 
    - **コンプライアンスの状態** - デバイス、ポリシー、設定、脅威、および保護に基づいて、コンプライアンスの状態を確認します。 また、このウィンドウでは、コンプライアンス ポリシーのないデバイスのリストが提供されます。
    - **構成の状態** - デバイス プロファイルの構成状態と、プロファイルの展開を確認します。 
    - **ソフトウェアの更新状態** - すべてのデバイスとすべてのユーザーに対する、展開の状態を視覚的に表示します。

    ![Microsoft Endpoint Manager 管理センターの [デバイス] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-03.png)

4. **[デバイス] - [概要]** ウィンドウから、 **[コンプライアンス ポリシー]** を選択し、Intune によって管理されているデバイスのコンプライアンスに関する詳細を表示します。 次の図のような詳細が表示されます。

    ![Microsoft Endpoint Manager 管理センターの [コンプライアンス ポリシー] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-04.png)
    
    > [!TIP]
    > 以前に Azure portal で Intune を使用したことがある場合は、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[デバイスのポリシー準拠]** を選択することで、Azure portal に上記の詳細が表示されます。

    コンプライアンス要件とは、基本的に、デバイスの PIN を必要とする、暗号化を必要とする、といった規則です。 デバイス コンプライアンス ポリシーでは、デバイスが準拠していると見なされるために従う必要のある規則および設定を定義します。 デバイスのコンプライアンスを使用するには、次のものが必要です。
    - Intune と Azure Active Directory (Azure AD) Premium のサブスクリプション
    - サポート対象のプラットフォームが実行されているデバイス
    - デバイスは Intune に登録されている必要があります
    - 1 人のユーザーに登録されているデバイス、またはプライマリ ユーザーに登録されていないデバイス。
    
    詳しくは、「[Intune のデバイス コンプライアンス ポリシーの概要](../protect/device-compliance-get-started.md)」をご覧ください。

5. **[デバイス] - [概要]** ウィンドウから、 **[条件付きアクセス]** を選択し、アクセス ポリシーに関する詳細を表示します。

    ![Microsoft Endpoint Manager 管理センターの [条件付きアクセス] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-05.png)

    > [!TIP]
    > 以前に Azure portal で Intune を使用したことがある場合は、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[条件付きアクセス]** を選択することで、Azure portal に上記の詳細が表示されます。

    条件付きアクセスとは、自分のメールや会社のリソースに接続することが許可されたデバイスやアプリを制御する手段です。 デバイス ベースやアプリ ベースの条件付きアクセスと、Intune で条件付きアクセスを利用する一般的なシナリオについては、[条件付きアクセス](../protect/conditional-access.md)に関するページをご覧ください。

6. ナビゲーション ウィンドウから、 **[デバイス]**  >  **[構成プロファイル]** の順に選択して、Intune のデバイス プロファイルに関する詳細を表示します。

    ![Microsoft Endpoint Manager 管理センターの [構成プロファイル] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-06.png)
    
    > [!TIP]
    > 以前に Azure portal で Intune を使用したことがある場合は、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[デバイス構成]** を選択することで、Azure portal に上記の詳細が表示されます。

    Intune には、組織内のさまざまなデバイスで有効または無効にできる設定と機能が含まれています。 これらの設定と機能は "構成プロファイル" に追加されます。 さまざまなデバイス、および iOS/iPadOS、Android、macOS、Windows などのさまざまなプラットフォームに対するプロファイルを作成することができます。 次に、Intune を使用して、組織内のデバイスにプロファイルを適用することができます。   

    デバイスの構成について詳しくは、「[Microsoft Intune でデバイス プロファイルを使用してデバイスに機能設定を適用する](../configuration/device-profiles.md)」をご覧ください。

7. ナビゲーション ウィンドウから、 **[デバイス]**  >  **[すべてのデバイス]** の順に選択し、Intune テナントの登録済みデバイスに関する詳細を表示します。 新しく Intune 登録を始める場合は、登録されているデバイスはまだありません。

    ![Microsoft Endpoint Manager 管理センターの [すべてのデバイス] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-07.png)

    このデバイスのリストには、コンプライアンス、OS のバージョン、および前回のチェックイン日に関する主要な詳細が表示されます。

    > [!TIP]
    > 以前に Azure portal で Intune を使用したことがある場合は、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[デバイス]**  >  **[すべてのデバイス]** の順に選択することで、Azure portal に上記の詳細が表示されます。
 
8. ナビゲーション ウィンドウから、 **[アプリ]** を選択して、アプリの状態の概要を表示します。 このウィンドウでは、次のタブに基づいて、アプリのインストール状態が提供されます。

    > [!TIP]
    > 以前に Azure portal で Intune を使用したことがある場合は、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[クライアント アプリ]** を選択することで、Azure portal に上記の詳細が表示されます。

    **[アプリ] - [概要]** ウィンドウには、次の状態の概要を表示できる 2 つのタブがあります。
    - **インストールの状態** - バイス別の上位のインストール エラーと、インストールに問題が生じているアプリを表示します。  
    - **アプリ保護ポリシーの状態** - アプリ保護ポリシーに割り当てられたユーザーと、フラグが設定されたユーザーの詳細を確認します。

    ![Microsoft Endpoint Manager 管理センターの [アプリ] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-08.png)

    Microsoft Intune を使用すれば、IT 管理者として、会社の従業員が使用するクライアント アプリを管理することができます。 この機能は、デバイス管理とデータ保護に加え用意されています。 管理者の優先事項の 1 つは、エンド ユーザーが仕事を行う上で必要なアプリに確実にアクセスできるようにすることです。 また、Intune に登録されていないデバイスでアプリの割り当てと管理が必要になる場合もあります。 Intune では、必要なデバイスで必要なアプリを利用できるように、さまざまな機能を提供しています。 

    > [!NOTE]
    > **[アプリ] - [概要]** ウィンドウでは、テナントの状態とアカウントの詳細も提供されます。

    アプリの追加と割り当てについて詳しくは、「[Microsoft Intune にアプリを追加する](../apps/apps-add.md)」および「[Microsoft Intune を使用してアプリをグループに割り当てる](../apps/apps-deploy.md)」をご覧ください。

9. **[アプリ] -[概要]** ウィンドウから、 **[すべてのアプリ]** を選択して、Intune に追加されたアプリのリストを表示します。

    > [!TIP]
    > 以前に Azure portal で Intune を使用したことがある場合は、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[クライアント アプリ]**  >  **[アプリ]** の順に選択することで、Azure portal に上記の詳細が表示されます。

    プラットフォームに基づいて、さまざまな種類のアプリを Intune に追加できます。 アプリが追加されたら、それをユーザーのグループに割り当てることができます。 

    ![Microsoft Endpoint Manager 管理センターの [すべてのアプリ] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-09.png)

    詳しくは、「[Microsoft Intune にアプリを追加する](~/apps/apps-add.md)」をご覧ください。 

10. ナビゲーション ウィンドウから、 **[ユーザー]** を選択し、Intune に含まれているユーザーに関する詳細を表示します。 これらのユーザーは、会社の従業員です。

    ![Microsoft Endpoint Manager 管理センターの [ユーザー] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-10.png)

    > [!TIP]
    > 以前に Azure portal で Intune を使用したことがある場合は、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[ユーザー]** を選択することで、Azure portal に上記の詳細が表示されます。

    ユーザーを Intune に直接追加することも、オンプレミスの Active Directory からユーザーを同期することもできます。 追加されたユーザーは、デバイスを登録し、会社のリソースにアクセスできます。 Intune にアクセスするための追加アクセス許可をユーザーに付与することもできます。 詳しくは、「[Intune にユーザーを追加して管理アクセス許可を付与する](users-add.md)」をご覧ください。

11. ナビゲーション ウィンドウから、 **[グループ]** を選択し、Intune に含まれる Azure Active Directory (Azure AD) グループに関する詳細を表示します。 Intune 管理者は、グループを使用してデバイスとユーザーを管理します。

    ![Microsoft Endpoint Manager 管理センターの [グループ] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-11.png)

    > [!TIP]
    > 以前に Azure portal で Intune を使用したことがある場合は、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[グループ]** を選択することで、Azure portal に上記の詳細が表示されます。

    組織のニーズに合うようにグループを設定できます。 地理的な場所、部門、ハードウェアの特性ごとにグループを作成して、ユーザーまたはデバイスを整理します。 大規模なタスクを管理するには、グループを使用します。 たとえば、多数のユーザーに対するポリシーを設定したり、デバイスのセットにアプリを展開したりできます。 グループについて詳しくは、「[ユーザーとデバイスを整理するためのグループを追加する](../groups-add.md)」をご覧ください。

12. ナビゲーション ウィンドウから、 **[テナント管理]** を選択し、Intune テナントの詳細を表示します。

    > [!TIP]
    > 以前に Azure portal で Intune を使用していた場合は、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[テナントの状態]** を選択することで、Azure portal に上記の詳細が表示されます。

    **[テナント管理者] - [テナントの状態]** ウィンドウには、 **[テナントの詳細]** 、 **[コネクタの状態]** 、および **[サービス正常性ダッシュボード]** の各タブが表示されます。 テナントまたは Intune 自体に問題がある場合は、このウィンドウで詳細を確認できます。 

    ![Microsoft Endpoint Manager 管理センターの [テナントの状態] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-12.png)

    詳しくは、「[Intune のテナントの状態ページ](../tenant-status.md)」をご覧ください。

13. ナビゲーション ウィンドウから、 **[トラブルシューティング + サポート]**  >  **[トラブルシューティング]** の順に選択して、特定のユーザーに関する状態の詳細を確認します。 

    > [!TIP]
    > 以前に Azure portal で Intune を使用したことがある場合は、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[トラブルシューティング]** を選択することで、Azure portal に上記の詳細が表示されます。

    **[割り当て]** ドロップダウン リストから、クライアント アプリ、ポリシー、更新リング、および登録制限の対象となる割り当てを表示するように選択できます。 さらに、このウィンドウでは、特定のユーザーに対するデバイスの詳細、アプリ保護の状態、および登録エラーが表示されます。

    ![Microsoft Endpoint Manager 管理センターの [トラブルシューティング] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-13.png)

    Intune 内でのトラブルシューティングについて詳しくは、「[トラブルシューティング ポータルを使用して社内のユーザーをサポートする](../help-desk-operators.md)」をご覧ください。

14. ナビゲーション ウィンドウから、 **[トラブルシューティング + サポート]**  >  **[ヘルプとサポート]** の順に選択してヘルプを要求します。 

    > [!TIP]
    > 以前に Azure portal で Intune を使用したことがある場合は、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[ヘルプとサポート]** を選択することで、Azure portal に上記の詳細が表示されます。

    IT 管理者は、 **[ヘルプとサポート]** オプションを使用して、解決策を検索して表示したり、Intune のオンライン サポート チケットを提出したりすることができます。 

    ![Microsoft Endpoint Manager 管理センターの [ヘルプとサポート] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-14.png)

    サポート チケットを作成するには、使用しているアカウントを Azure Active Directory の管理者ロールとして割り当てる必要があります。 管理者ロールには、**Intune 管理者**、**グローバル管理者**、および**サービス管理者**が含まれます。 

    詳細については、「[Microsoft Intune のサポートを受ける方法](../get-support.md)」を参照してください。

15. ナビゲーション ウィンドウから、 **[トラブルシューティング + サポート]**  >  **[ガイド付きのシナリオ]** の順に選択し、利用可能な Intune のガイド付きのシナリオを表示します。 

    ガイド付きシナリオは、1 つのエンドツーエンドのユースケースを中心にカスタマイズされた一連の手順です。 一般的なシナリオは、組織内で管理者、ユーザー、またはデバイスが果たす役割に基づいています。 これらの役割では通常、最適なユーザー エクスペリエンスとセキュリティを提供するために、慎重に調整されたプロファイル、設定、アプリケーション、セキュリティ制御のコレクションが必要です。

    特定の Intune シナリオを実装するために必要なすべての手順とリソースについて詳しく理解していない場合は、ガイド付きシナリオを出発点として使用することができます。 

    ![Microsoft Endpoint Manager 管理センターの [ガイド付きのシナリオ] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-15.png)

    ガイド付きのシナリオの詳細については、[ガイド付きのシナリオの概要](~/fundamentals/guided-scenarios-overview.md)に関するページを参照してください。

## <a name="configure-the-microsoft-endpoint-manager-admin-center"></a>Microsoft Endpoint Manager 管理センターを構成する

Azure では、ポータルの表示をカスタマイズおよび構成できます。

### <a name="change-the-dashboard"></a>[ダッシュボード] を変更する

Intune テナント内のデバイスとクライアント アプリに関する全体的な詳細を表示するための、 **[ダッシュボード]** があります。 ダッシュボードでは、Microsoft Endpoint Manager 管理センターで、対象が絞られ、整理されたビューを作成するための方法が提供されます。 ダッシュボードをワークスペースとして使用して、日常業務のタスクをすばやく起動し、リソースを監視することができます。 たとえば、プロジェクト、タスク、またはユーザー ロールに基づいて、カスタム ダッシュボードを構築します。 Microsoft Endpoint Manager 管理センターでは、既定のダッシュボードが開始点として提供されます。 既定のダッシュボードを編集したり、追加のダッシュボードを作成およびカスタマイズしたり、ダッシュボードを発行および共有して他のユーザーが使用できるようにしたりすることができます。 

   ![Microsoft Endpoint Manager 管理センターの [ダッシュボード] のスクリーンショット](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-16.png)

現在のダッシュボードを変更するには、 **[編集]** を選択します。 既定のダッシュボードを変更しなくても、**新しいダッシュボード**を作成できます。 新しいダッシュボードを作成すると、**タイル ギャラリー**がある空のプライベート ダッシュボードが与えられ、そこでタイルを追加したり再編成できます。 カテゴリまたはリソースの種類別にタイルを見つけることができます。 また、特定のタイルを検索することができます。 既存のカスタム ダッシュボードのいずれかを選ぶ場合は、 **[マイ ダッシュボード]** を選択します。

### <a name="change-the-portal-settings"></a>[ポータルの設定] を変更する

Microsoft Endpoint Manager 管理センターは、既定のビュー、テーマ、資格情報のタイムアウト期間、および言語と地域の設定を選択することでカスタマイズできます。

   <img alt="Screenshot of the Microsoft Endpoint Manager admin center - Portal settings" src="./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-17.png" width="250">

## <a name="next-steps"></a>次のステップ

Microsoft Intune を短時間で実行するには、Intune のクイック スタートの手順で Intune の無料アカウントを最初に設定します。

> [!div class="nextstepaction"]
> [クイック スタート: Microsoft Intune を無料で試す](free-trial-sign-up.md)
