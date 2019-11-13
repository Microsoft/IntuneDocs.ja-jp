---
title: チュートリアル - Azure portal での Intune のチュートリアル
titleSuffix: Microsoft Intune
description: このチュートリアルでは、Microsoft Intune でタスクを実行する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e892d8a3-7f74-498c-98d5-e968a8fbb049
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9197d4f96eae1041b00b07110ef421a12a4fe338
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712987"
---
# <a name="tutorial-walkthrough-of-microsoft-intune-in-the-azure-portal"></a>チュートリアル: Azure portal での Microsoft Intune のチュートリアル

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) には、クラウド コンピューティングのさまざまなシナリオと可能性を支援する 100 を超えるサービスが含まれています。 Microsoft Intune は、Azure で利用できるサービスの 1 つです。 Intune を利用すると、会社のデバイス、アプリ、データが会社のセキュリティ要件を確実に満たすようにできます。 確認する必要がある要件や、それらの要件が満たされない場合の対応の設定を制御できます。 [Azure Portal](https://portal.azure.com) は、Microsoft Intune サービスのある場所です。 Intune で使用できる機能を理解しておくと、モバイル デバイス管理 (MDM) とモバイル アプリケーション管理 (MAM) のさまざまなタスクを実行するときに役に立ちます。

このチュートリアルでは次のことを行います。
> [!div class="checklist"]
> * Microsoft Intune の概要を知る
> * Azure portal を構成する

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

## <a name="prerequisites"></a>必要条件
Microsoft Intune を設定する前に、次の要件を確認してください。

- [サポートされるオペレーティング システムとブラウザー](../supported-devices-browsers.md) 
- [ネットワーク構成の要件と帯域幅](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Microsoft Intune の無料試用版にサインアップ

Intune は 30 日間無料で試用できます。 既に職場または学校アカウントがある場合は、そのアカウントで**サインイン**し、Intune をサブスクリプションに追加します。 それ以外の場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)して、組織で Intune を使うことができます。

> [!IMPORTANT]
> 新しいアカウントにサインアップした後で、既存の職場または学校アカウントを組み合わせることはできません。

## <a name="tour-microsoft-intune"></a>Microsoft Intune の概要を知る

次の手順のようにすると、Azure portal での Intune についていっそうよく理解できます。 ツアーを終えると、Intune のいくつかの主要な領域について理解が深まります。

1. ブラウザーを開き、[Intune ポータル](https://aka.ms/intuneportal)にサインインします。 Intune を初めて使う場合は、無料試用版サブスクリプションを使用します。

    ![Microsoft Intune ポータルのスクリーンショット](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-01.png)

    Intune や他のサービスを Azure で開くと、ウィンドウにサービスが表示されます。 Intune で最初に使うワークロードは、 **[デバイス]** 、 **[クライアント アプリ]** 、 **[ユーザー]** 、 **[グループ]** などです。 ワークロードは、サービスのサブ領域に過ぎません。 ワークロードを選択すると、そのウィンドウがページ全体に表示されます。 他のブレードは開くときにブレードの右側から引き出され、閉じると前のウィンドウが表示されます。 ウィンドウはブレードとも呼ばれます。 

    既定では、Intune を開くと **[概要]** ウィンドウが表示されます。 このウィンドウでは、デバイスの割り当てとコンプライアンスの状態およびアプリのインストール状態の全体的なビジュアル スナップショットが提供されます。

2. [Intune](https://aka.ms/intuneportal) で **[デバイスの登録]** を選択すると、Intune テナントに登録されているデバイスの詳細情報が表示されます。 新しい Intune テナントを始めたばかりの場合は、まだ登録されているデバイスはありません。 

    ![[デバイス登録] ウィンドウのスクリーンショット](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-02.png)
    
    Intune では、従業員のデバイスやアプリによる会社のデータへのアクセス方法などを管理できます。 このモバイル デバイス管理 (MDM) サービスを使用するには、最初にデバイスを Intune に登録する必要があります。 デバイスが登録されると、MDM 証明書が発行されます。 この証明書を使用して、Intune サービスと通信します。 

    従業員のデバイスを Intune に登録する方法は複数あります。 各方法は、デバイスの所有権 (個人または会社)、デバイスの種類 (iOS、Windows、Android)、および管理要件 (リセット、アフィニティ、ロック) によって異なります。 ただし、デバイスを登録するには、その前に Intune インフラストラクチャを設定する必要があります。 特に、デバイスの登録には [MDM 機関を設定する](mdm-authority-set.md)必要があります。 Intune 環境 (テナント) の準備について詳しくは、「[Intune をセットアップする](setup-steps.md)」をご覧ください。 Intune テナントの準備が済むと、デバイスを登録できます。 デバイスの登録について詳しくは、「[デバイス登録とは](../enrollment/device-enrollment.md)」をご覧ください

3. [Intune](https://aka.ms/intuneportal) で **[デバイスのポリシー準拠]** を選択すると、Intune によって管理されているデバイスのコンプライアンスの詳細が表示されます。 次の図のような詳細が表示されます。

    ![[デバイスのポリシー準拠] ウィンドウのスクリーンショット](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-03.png)
    
    コンプライアンス要件とは、基本的に、デバイスの PIN を必要とする、暗号化を必要とする、といった規則です。 デバイス コンプライアンス ポリシーでは、デバイスが準拠していると見なされるために従う必要のある規則および設定を定義します。 デバイスのコンプライアンスを使用するには、次のものが必要です。
    - Intune と Azure Active Directory (Azure AD) Premium のサブスクリプション
    - サポート対象のプラットフォームが実行されているデバイス
    - デバイスは Intune に登録されている必要があります
    - 1 人のユーザーに登録されているデバイス、またはプライマリ ユーザーに登録されていないデバイス。
    
    詳しくは、「[Intune のデバイス コンプライアンス ポリシーの概要](../protect/device-compliance-get-started.md)」をご覧ください。

4. [Intune](https://aka.ms/intuneportal) で **[デバイス構成]** を選択すると、Intune でのデバイス プロファイルの詳細が表示されます。

    ![[デバイス構成] ウィンドウのスクリーンショット](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-04.png)
    
    Intune には、組織内のさまざまなデバイスで有効または無効にできる設定と機能が含まれています。 これらの設定と機能は "構成プロファイル" に追加されます。 異なるデバイスおよび iOS、Android、Windows などの異なるプラットフォームに対するプロファイルを作成することができます。 次に、Intune を使用して、組織内のデバイスにプロファイルを適用することができます。   

    デバイスの構成について詳しくは、「[Microsoft Intune でデバイス プロファイルを使用してデバイスに機能設定を適用する](../configuration/device-profiles.md)」をご覧ください。

5. [Intune](https://aka.ms/intuneportal) で **[デバイス]** を選択すると、Intune テナントの登録済みデバイスに関する詳細が表示されます。 新しく Intune 登録を始める場合は、登録されているデバイスはまだありません。

    ![[デバイス登録] ウィンドウのスクリーンショット](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-05.png)

    **[デバイス]** ウィンドウでは、テナントの登録済みデバイスに関する詳細が提供されます。 **[すべてのデバイス]** をクリックして、Intune テナントのデバイスの一覧を表示できます。

6. [Intune](https://aka.ms/intuneportal) で **[クライアント アプリ]** を選択すると、アプリのインストール状態が表示されます。

    ![[クライアント アプリ] ウィンドウのスクリーンショット](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-06.png)

    Microsoft Intune を使用すれば、IT 管理者として、会社の従業員が使用するクライアント アプリを管理することができます。 この機能は、デバイス管理とデータ保護に加え用意されています。 管理者の優先事項の 1 つは、エンド ユーザーが仕事を行う上で必要なアプリに確実にアクセスできるようにすることです。 また、Intune に登録されていないデバイスでアプリの割り当てと管理が必要になる場合もあります。 Intune では、必要なデバイスで必要なアプリを利用できるように、さまざまな機能を提供しています。 アプリの追加と割り当てについて詳しくは、「[Microsoft Intune にアプリを追加する](../apps/apps-add.md)」および「[Microsoft Intune を使用してアプリをグループに割り当てる](../apps/apps-deploy.md)」をご覧ください。

7. [Intune](https://aka.ms/intuneportal) で **[条件付きアクセス]** を選択すると、アクセス ポリシーに関する詳細が表示されます。

    ![[条件付きアクセス] ウィンドウのスクリーンショット](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-07.png)

    条件付きアクセスとは、自分のメールや会社のリソースに接続することが許可されたデバイスやアプリを制御する手段です。 デバイス ベースやアプリ ベースの条件付きアクセスと、Intune で条件付きアクセスを利用する一般的なシナリオについては、[条件付きアクセス](../protect/conditional-access.md)に関するページをご覧ください。

8. [Intune](https://aka.ms/intuneportal) で **[ユーザー]** を選択すると、Intune に含まれるユーザーに関する詳細が表示されます。 これらのユーザーは、会社の従業員です。

    ![[ユーザー] ウィンドウのスクリーンショット](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-08.png)

    ユーザーを Intune に直接追加することも、オンプレミスの Active Directory からユーザーを同期することもできます。 追加されたユーザーは、デバイスを登録し、会社のリソースにアクセスできます。 Intune にアクセスするための追加アクセス許可をユーザーに付与することもできます。 詳しくは、「[Intune にユーザーを追加して管理アクセス許可を付与する](users-add.md)」をご覧ください。

9. [Intune](https://aka.ms/intuneportal) で **[グループ]** を選択すると、Intune に含まれる Azure Active Directory (Azure AD) グループに関する詳細が表示されます。 Intune 管理者は、グループを使用してデバイスとユーザーを管理します。

    ![[グループ] ウィンドウのスクリーンショット](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-09.png)

    組織のニーズに合うようにグループを設定できます。 地理的な場所、部門、ハードウェアの特性ごとにグループを作成して、ユーザーまたはデバイスを整理します。 大規模なタスクを管理するには、グループを使用します。 たとえば、多数のユーザーに対するポリシーを設定したり、デバイスのセットにアプリを展開したりできます。 グループについて詳しくは、「[ユーザーとデバイスを整理するためのグループを追加する](../groups-add.md)」をご覧ください。

10. ヘルプを依頼するには、[Intune](https://aka.ms/intuneportal) で **[ヘルプとサポート]** を選択します。 IT 管理者は、 **[ヘルプとサポート]** オプションを使用して、解決策を検索して表示したり、Intune のオンライン サポート チケットを提出したりすることができます。 

    ![[ヘルプとサポート] ウィンドウのスクリーンショット](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-10.png)

    サポート チケットを作成するには、使用しているアカウントを Azure Active Directory の管理者ロールとして割り当てる必要があります。 管理者ロールには、**Intune 管理者**、**グローバル管理者**、および**サービス管理者**が含まれます。 詳細については、「[Microsoft Intune のサポートを受ける方法](../get-support.md)」を参照してください。

11. [Intune](https://aka.ms/intuneportal) で **[テナントの状態]** を選択すると、Intune テナントに関する詳細が表示されます。

    ![[テナントの状態] ウィンドウのスクリーンショット](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-11.png)

    テナントの状態の詳細には、コネクタの状態、Intune サービスの正常性、および Intune のニュースが含まれます。 テナントまたは Intune 自体に問題がある場合は、 **[テナントの状態]** ウィンドウで詳細を確認します。 詳しくは、「[Intune のテナントの状態ページ](../tenant-status.md)」をご覧ください。

12. [Intune](https://aka.ms/intuneportal) で **[トラブルシューティング]** を選択すると、トラブルシューティングのヒント、サポートの依頼、Intune の状態の確認に関するショートカットが表示されます。 この情報は、選択されている Intune ユーザーに固有のものです。

    ![[トラブルシューティング] ウィンドウのスクリーンショット](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-12.png)

Intune 内でのトラブルシューティングについて詳しくは、「[トラブルシューティング ポータルを使用して社内のユーザーをサポートする](../help-desk-operators.md)」をご覧ください。

## <a name="configure-the-azure-portal"></a>Azure portal を構成する

Azure では、ポータルの表示をカスタマイズおよび構成できます。

### <a name="change-the-sidebar"></a>サイドバーを変更する

Azure Portal の左側にある**サイドバー**には、利用できるすべての Azure サービスの一覧が表示されます。 この包括的な一覧は既定以外の表示に変更できます。自分にとって最も重要なサービスを常に表示しておくことができます。 次の情報では、サービスの例として Intune を利用し、一覧の一番上に追加します。

![あるユーザーが 'その他のサービス' 一覧で Microsoft Intune を探しています。](./media/tutorial-walkthrough-intune-portal/azure-add-intune1.png)

1. ページの左側にあるサイドバーから **[すべてのサービス]** を選択します。
2. フィルター ボックスで **Intune** を検索します。
3. **星**マークを選択し、お気に入りサービス一覧の一番下に Intune を追加します。
4. Intune サービスの上にカーソルを合わせます。 Intune を選択してドラッグします。サービス名の右側にある **3 つの垂直ドット**を利用します。

### <a name="change-the-dashboard"></a>ダッシュボードを変更する

既定のランディング ページは**ダッシュボード**です。 このページで、タイルをカスタマイズし、自分にとって最も重要な情報を表示します。

![一般的な新しいダッシュボードのイメージ。 すべてのサービスを含むサイドバーが左に、メインのダッシュボードが中央に表示されます。 ダッシュボードの変更ボタンは上にあります。タイルからすべてのリソース、クイックスタート チュートリアル、サービス正常性、Azure Marketplace にアクセスできます。](./media/tutorial-walkthrough-intune-portal/azure-default-dashboard.png)

現在のダッシュボードを変更するには、 **[ダッシュボードの編集]** ボタンを選択します。 既定のダッシュボードを変更しなくても、**新しいダッシュボード**を作成できます。 新しいダッシュボードを作成すると、**タイル ギャラリー**がある空のプライベート ダッシュボードが与えられ、そこでタイルを追加したり再編成できます。 **全般**カテゴリや**種類**に基づいて、あるいは**検索**、**リソース グループ**、**タグ**を利用してタイルを検索できます。

また、**省略記号**ボタンからダッシュボードに直接、タイルを追加できます。 **[ダッシュボードにピン留めする]** を選択します。

![Intune の [ユーザーとグループ - すべてのグループ] の拡大画面。グループの右端で "ダッシュボードにピン留めする" オプションを確認できます。](./media/tutorial-walkthrough-intune-portal/azure-pin-to-dashboard.png)

この機能は、Intune にグループやユーザーなどのコンテンツを追加した後に重要になります。

## <a name="next-steps"></a>次の手順

Microsoft Intune を短時間で実行するには、Intune のクイック スタートの手順で Intune の無料アカウントを最初に設定します。

> [!div class="nextstepaction"]
> [クイック スタート: Microsoft Intune を無料で試す](free-trial-sign-up.md)
