---
title: "MAM ポリシーの作成と展開 | Microsoft Docs"
description: "モバイル アプリ管理ポリシーを作成して展開するには、このトピックのステップ バイ ステップの指示に従ってください。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1b9a343-1737-4a65-a9c6-aca48acad11c
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 33febef8787887401960592d95356347f6917681
ms.openlocfilehash: a7d38caac1cfd035c66d02579766d60d4394dd5e
ms.contentlocale: ja-jp
ms.lasthandoff: 05/04/2017


---

# <a name="create-and-deploy-app-protection-policies-with-microsoft-intune"></a>Microsoft Intune でのアプリ保護ポリシーの作成とデプロイ

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

このトピックでは、**Azure ポータル**でアプリ保護ポリシーを作成するプロセスについて説明します。 Azure ポータルはアプリ保護ポリシーを作成するための新しい管理コンソールです。このポータルを使用して、アプリ保護ポリシーを作成することをお勧めします。 Azure ポータルでは、次の MAM シナリオをサポートします。

- Intune に登録されたデバイス
- サードパーティの MDM ソリューションで管理されるデバイス
- MDM ソリューション (BYOD) で管理されないデバイス

>[!IMPORTANT]
デバイスの管理に **Intune 管理コンソール**を使用してしている場合は、次のことに注意してください。

> * [Intune 管理コンソール](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)を使用して Intune に登録したデバイスのアプリをサポートするアプリ保護ポリシーを作成できます。
> * Intune 管理コンソールで作成したアプリ保護ポリシーを Azure ポータルにインポートすることはできません。  Azure ポータルでアプリ保護ポリシーを作成し直す必要があります。

> * Intune 管理コンソールでは、アプリ保護ポリシー設定の一部が表示されない可能性があります。 Azure ポータルはアプリ保護ポリシーを作成するための新しい管理コンソールです。

> * 管理対象アプリをデプロイするには、Intune 管理コンソールでアプリ保護ポリシーを作成する必要があります。 この場合、Intune 管理コンソールと Azure ポータルの両方でアプリ保護ポリシーを作成できます。Intune 管理コンソールはユーザーが管理対象アプリをデプロイできることを確認します。Azure ポータルはすべてのアプリ保護ポリシー設定を備えた新しい管理コンソールです。

> * Intune 管理コンソールと Azure ポータルの両方でアプリ保護ポリシーを作成した場合は、Azure ポータルで作成されたポリシーがアプリに適用されます。

Android および iOS プラットフォームでサポートされているポリシー設定の一覧を表示するには、次のいずれかを選択します。

> [!div class="op_single_selector"]
- [iOS ポリシー](ios-mam-policy-settings.md)
- [Android ポリシー](android-mam-policy-settings.md)

- アプリ保護ポリシーのしくみと Intune のアプリ保護ポリシーでサポートされるシナリオについて詳しくは、[アプリ保護ポリシーを使用したアプリ データの保護](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)に関するページをご覧ください。

##  <a name="create-an-app-protection-policy"></a>アプリ保護ポリシーを作成する
アプリ保護ポリシーは、Azure ポータルで作成されます。 初めて Azure ポータルを使用する場合は、先に [Azure ポータルの Microsoft Intune アプリ保護ポリシー対応](azure-portal-for-microsoft-intune-mam-policies.md)に関する記事を参照して、Azure ポータルについて理解しておきます。 アプリ保護ポリシーを作成する前に、[前提条件とサポート](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)情報をご確認ください。

アプリ保護ポリシーを作成するには、次の手順に従います。

1. [Azure Portal](https://portal.azure.com) に移動し、資格情報を入力します。

2. **[その他のサービス]** を選択し、"Intune" と入力します。

3. **[Intune アプリ保護]** を選択します。

4. **[Intune モバイル アプリケーション管理] &gt; [設定]** を選択して、**[すべての設定]** ブレードを開きます。

    ![[Intune モバイル アプリケーション管理] ブレードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_Mainblade-2.png)

2.  **[すべての設定]** ブレードで、**[アプリ ポリシー]** をクリックします。 これにより、**[アプリ ポリシー]** ブレードが開き、ここで新しいポリシーを作成や、既存のポリシーの編集ができます。 **[ポリシーの追加]** を選択します。

    ![[ポリシーの追加] メニュー オプションが強調表示されている [ポリシーの追加] ブレードのスクリーンショット ](../media/AppManagement/AzurePortal_MAM_AddPolicy.png)

3.  ポリシーの名前を入力して簡単な説明を追加し、iOS または Android 用のポリシーを作成するプラットフォームの種類を選択します。 プラットフォームごとに複数のポリシーを作成できます。

    ![[ポリシーの追加] ブレードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_AddPolicy_only.png)

4.  **[アプリ]** を選択して **[アプリ] ブレード** を開くと、使用可能なアプリの一覧が表示されます。 一覧から、作成するポリシーに関連付けるアプリを 1 つまたは複数選択します。 アプリを選択したら、**[アプリ]** ブレードの下部にある **[選択]** を選択して、選択内容を保存します。

    > [!IMPORTANT]
    > ポリシーを作成するには、少なくとも 1 つのアプリを選択する必要があります。

5.  **[ポリシーの追加] ブレード**で、**[必要な設定の構成]** を選択し、[ポリシー設定] ブレードを開きます。

    ポリシー設定には、**[データ再配置]** と **[アクセス]** の 2 つのカテゴリがあります。  データ再配置ポリシーは、アプリとの間のデータ移動に適用可能ですが、作業コンテキストでエンド ユーザーがアプリにアクセスする方法は、アクセス ポリシーによって決まります。
    ユーザーが開始できるように、ポリシー設定には既定値が入力されています。 既定値が要件を満たす場合は、変更を加える必要はありません。

    > [!TIP]
    > これらのポリシー設定は、作業コンテキストでアプリを使用する場合にのみ適用されます。  エンド ユーザーが、個人のタスクを実行するためにアプリを使用する場合、これらのポリシーによって設定が影響を受けることはありません。

    ![[ポリシーの追加] ブレードと [設定] ブレードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_PolicySettings.png)

6.  **[OK]** を選択して、この構成を保存します。 これにより、 **[ポリシーの追加]** ブレードに戻ります。 **[作成]** を選択してポリシーを作成し、設定を保存します。

    ![アプリと設定が構成されていることを示す [ポリシーの追加] ブレードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_CreatePolicy.png)

前の手順の説明に従ってポリシーの作成が完了した時点では、ポリシーはユーザーに展開されません。 ポリシーを展開するには、次のセクションの「ユーザーへのポリシーの展開」を参照してください。

> [!IMPORTANT]
> Intune 管理コンソールでアプリのアプリ保護ポリシーを作成し、Azure ポータルでアプリ保護ポリシーを作成した場合は、Azure ポータルで作成したポリシーが優先されます。 ただし、Intune または Configuration Manager のコンソールのレポート機能では、Intune 管理コンソールから作成されたポリシー設定がレポート対象となります。 たとえば、
>
> -   アプリからのコピーがブロックされている Intune 管理コンソールでアプリ保護ポリシーを作成しました。
> -   アプリからのコピーが許可されている Azure コンソールでアプリ保護ポリシーを作成しました。
> -   これら両方のポリシーを同じアプリに関連付けます。
> -   Azure コンソールから作成したポリシーが優先され、コピーが許可されることになります。
> -   ただし、Intune コンソールのステータスとレポートは、コピーがブロックされているという正しくない情報を示します。

## <a name="line-of-business-lob-apps-optional"></a>基幹業務 (LOB) アプリ (オプション)

Intune 1703 バージョン以降では、新しいアプリ保護ポリシーを作成するときに、LOB アプリを Intune に一般的に追加するオプションがあります。 この方法では、完全なアプリ展開アクセス許可がなくても、MAM SDK を使って LOB アプリ用のアプリ保護ポリシーを定義できます。

> [!TIP]
> [Intune アプリ SDK](https://docs.microsoft.com/intune/develop/intune-app-sdk-get-started) ワークフローの過程で Intune に LOB アプリを追加することもできます。

> [!IMPORTANT]
> ユーザーが MAM アプリ展開用のアクセス許可しか持たず、任意のアプリを Intune に展開できる完全なアプリ展開アクセス許可がない場合は、Intune SDK ワークフローを実行することはできませんが、その場合でも MAM アプリ保護ポリシー作成ワークフローを使って LOB アプリを追加できます。

### <a name="to-add-lob-apps-ios-and-android"></a>LOB アプリを追加するには (iOS と Android)

1.  [ポリシーの追加] ブレードで **[アプリ]** の構成を選んで、[アプリ] ブレードを開きます。

    ![MAM の [ポリシーの追加] ブレード](../media/AppManagement/mam-lob-apps-1.png)

2.  **[その他のアプリ]** をクリックし、**[バンドル ID]** (iOS の場合) または **[パッケージ ID]** (Android の場合) を入力した後、[選択] をクリックして LOB アプリを追加します。

    ![MAM の [その他のアプリ] ブレード](../media/AppManagement/mam-lob-apps-2.png)

### <a name="to-add-lob-apps-windows"></a>LOB アプリを追加するには (Windows)

> [!IMPORTANT]
> 新しいアプリ保護ポリシーを作成するときは、[プラットフォーム] ドロップダウン リストから [Windows 10] を選ぶ必要があります。

1.  [ポリシーの追加] ブレードで、**[許可されたアプリ]** または **[適用から除外されるアプリ]** を選んで、許可するアプリまたは除外するアプリのブレードを開きます。

    > [!NOTE]
    >
    - **[許可されたアプリ]**: このポリシーに準拠する必要があるアプリです。
    - **[適用から除外されるアプリ]**: これらのアプリはこのポリシーから除外され、制限なしに企業データにアクセスできます。
<br></br>
2. 許可するアプリまたは除外するアプリのブレードで、**[アプリの追加]** をクリックします。 推奨される Microsoft アプリ、ストア アプリ、またはデスクトップ アプリを追加できます。

    a.  **[おすすめのアプリ]:** 管理者がポリシーに簡単にインポートできるようにあらかじめ設定されている (ほとんどは Office) アプリの一覧です。

    b.  **[ストア アプリ]:** 管理者は、Windows ストアからポリシーに任意のアプリを追加できます。

    c.  **[Windows desktop apps (Windows デスクトップ アプリ)]:** 管理者は従来の Windows デスクトップ アプリをポリシーに追加できます (exe、dll など)。

## <a name="deploy-a-policy-to-users"></a>ユーザーへのポリシーの展開

1.  **[ポリシー]** ブレードで **[ユーザー グループ]** を選択して、**[ユーザー グループ]** ブレードを開きます。 **[ユーザー グループ]** ブレードで **[ユーザー グループの追加]** を選択して、**[ユーザー グループの追加]** ブレードを開きます。

    ![[ユーザー グループの追加] メニュー オプションが強調表示されている [ユーザー グループ] ブレードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_AddUserstoPolicy.png)

2.  ユーザー グループの一覧が、 **[ユーザー グループの追加]** ブレードに表示されます。 これは、 **Azure Active Directory**内にあるすべてのセキュリティ グループの一覧です。 このポリシーを適用するユーザー グループを選択し、**[選択]** を選択します。 **[選択]** を選択すると、ポリシーがユーザーに展開されます。

    ![Azure Active Directory ユーザーの一覧を示している [ユーザー グループの追加] ブレードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_SelectUserstoDeploy.png)

    これで、作成したポリシーはユーザーに展開されました。

Intune ライセンスが割り当てられているユーザーのみが、このポリシーの影響を受けます。 選択したセキュリティ グループ内のユーザーのうち、Intune ライセンスが割り当てられていないユーザーは影響を受けません。

>[!IMPORTANT]
> Intune を使用し、Configuration Manager によって iOS デバイスと Android デバイスを管理する場合、このポリシーは、選択したグループ直下のユーザーにのみ適用されます。 選択したグループ内にネストされた子グループのメンバーは、影響を受けません。

エンド ユーザーは App Store または Google Play からアプリをダウンロードできます。 詳細については、次をご覧ください。
* [アプリ保護ポリシーを使用して Android アプリを管理するときの注意点](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [アプリ保護ポリシーを使用して iOS アプリを管理するときの注意点](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

##  <a name="change-existing-policies"></a>既存のポリシーの変更
既存のポリシーを編集して、対象ユーザーに適用できます。 ただし、既存のポリシーを変更する場合、アプリに既にサインインしているユーザーには、8 時間にわたって変更が表示されません。

変更の効果をすぐに確認するには、エンド ユーザーはアプリをログアウトし、もう一度サインインする必要があります。

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>ポリシーに関連付けられているアプリの一覧を変更するには

1.  **[アプリ ポリシー]** ブレードで、変更するポリシーを選択します。 これにより、選択したポリシーに固有のブレードが開きます。

    ![別のブレードで開かれている既存のポリシーのスクリーン ショット](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  ポリシー ブレードで **[対象アプリ]** をクリックし、アプリの一覧を開きます。

3.  一覧からアプリを削除または追加し、**[保存]** アイコンを選択して変更内容を保存します。

### <a name="to-change-the-list-of-user-groups"></a>ユーザー グループの一覧を変更するには

1.  **[アプリ ポリシー]** ブレードで、変更するポリシーを選択します。 これにより、選択したポリシーに固有のブレードが開きます。

2.  ポリシー ブレードで **[ユーザー グループ]** をクリックして **[ユーザー グループ]** ブレードを開きます。このブレードには、このポリシーが設定された現在のユーザー グループの一覧が表示されます。

3.  ポリシーに新しいユーザー グループを追加するには、**[ユーザー グループの追加]** を選択し、ユーザー グループを選択します。 **[選択]** を選択して、選択したグループにポリシーを展開します。

    ![2 人のユーザー グループが選択されている [ユーザー グループの追加] ブレードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_ChangePolicy_SelectUser.png)

4.  ユーザー グループを削除するには、削除するユーザー グループを選択します。 省略記号 (...) を選択し、**[削除]** を選択してユーザー グループを削除します。

    ![[削除] オプションが表示されたスクリーンショット ](../media/AppManagement/AzurePortal_MAM_ChangePolicy_DeleteUser.png)

### <a name="to-change-policy-settings"></a>ポリシー設定を変更するには

1.  **[アプリ ポリシー]** ブレードで、変更するポリシーを選択します。 これにより、選択したポリシーに固有のブレードが開きます。

    ![別のブレードで開かれている既存のポリシーのスクリーンショット ](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  **[ポリシー設定]** をクリックして **[ポリシー設定]** ブレードを開きます。

3.  設定を変更し、**[保存]** アイコンを選択して変更内容を保存します。

    ![上部に [保存] オプションが表示された [ポリシー設定] ブレードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_ChangePolicy_ChangeSettings.png)

## <a name="policy-settings"></a>ポリシー設定
iOS と Android 用のポリシー設定の完全な一覧を表示するには、次のいずれかを選択します。

> [!div class="op_single_selector"]
- [iOS ポリシー](ios-mam-policy-settings.md)
- [Android ポリシー](android-mam-policy-settings.md)

## <a name="next-steps"></a>次のステップ
[コンプライアンスとユーザーの状態を監視する](monitor-mobile-app-management-policies-with-microsoft-intune.md)

### <a name="see-also"></a>関連項目
* [アプリ保護ポリシーを使用して Android アプリを管理するときの注意点](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [アプリ保護ポリシーを使用して iOS アプリを管理するときの注意点](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

