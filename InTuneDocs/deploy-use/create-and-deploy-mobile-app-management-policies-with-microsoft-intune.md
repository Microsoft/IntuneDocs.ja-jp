---
title: "MAM ポリシーの作成と展開 | Microsoft Intune"
description: "モバイル アプリ管理ポリシーを作成して展開するには、このトピックのステップ バイ ステップの指示に従ってください。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1b9a343-1737-4a65-a9c6-aca48acad11c
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 05b898ffdd0b76eb04d344adb3cfb20ec15aeb52


---

# <a name="create-and-deploy-mobile-app-management-policies-with-microsoft-intune"></a>Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開
モバイル アプリ管理 (MAM) ポリシーは、デバイスを Intune で管理できるかできないかに関係なく、デバイスで実行されるアプリに適用できます。 MAM ポリシーの動作方法と Intune MAM ポリシーがサポートするシナリオの詳細については、[モバイル アプリ管理ポリシーを使用するアプリ データの保護](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)に関するトピックを参照してください。

このトピックでは、**Azure ポータル**で MAM ポリシーを作成するプロセスについて説明します。 Azure Portal は MAM ポリシーを作成するための新しい管理コンソールです。このポータルを使用して、MAM ポリシーを作成することをお勧めします。 Azure ポータルでは、次の MAM シナリオをサポートします。
- Intune に登録されたデバイス
- サードパーティの MDM ソリューションで管理されるデバイス
- MDM ソリューション (BYOD) で管理されないデバイス

>[!IMPORTANT]
現在 **Intune 管理コンソール**を使用してデバイスを管理している場合は、次のことに注意してください。

> * [Intune 管理コンソール](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)を使用して Intune に登録したデバイスのアプリをサポートする MAM ポリシーを作成できます。
> * Intune 管理コンソールで作成した MAM ポリシーを Azure ポータルにインポートすることはできません。  Azure ポータルで MAM ポリシーを作成し直す必要があります。

> * Intune 管理コンソールでは、MAM ポリシー設定の一部が表示されない可能性があります。 Azure ポータルは MAM ポリシーを作成するための新しい管理コンソールです。

> * 管理対象アプリを展開するには、Intune 管理コンソールで MAM ポリシーを作成する必要があります。 この場合、Intune 管理コンソールと Azure Portal の両方で MAM ポリシーを作成できます。Intune 管理コンソールはユーザーが管理対象アプリを展開できることを確認します。Azure Portal はすべての MAM ポリシー設定を備えた新しい管理コンソールです。

> * Intune 管理コンソールと Azure ポータルの両方で MAM ポリシーを作成した場合は、Azure ポータルで作成されたポリシーがアプリに適用されます。

Android および iOS プラットフォームでサポートされているポリシー設定の一覧を表示するには、次のいずれかを選択します。

> [!div class="op_single_selector"]
- [iOS ポリシー](ios-mam-policy-settings.md)
- [Android ポリシー](android-mam-policy-settings.md)

##  <a name="create-a-mam-policy"></a>MAM ポリシーの作成
MAM ポリシーを作成する前に、[前提条件とサポート](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)情報を確認してください。
1.  **[Intune モバイル アプリケーション管理] &gt; [設定]** を選択して、**[設定]** ブレードを開きます。

    ![[Intune モバイル アプリケーション管理] ブレードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > 初めて Azure ポータルを使用する場合は、先に「[Azure ポータルの Microsoft Intune MAM ポリシー対応](azure-portal-for-microsoft-intune-mam-policies.md)」を参照して、ポータルについて理解しておきます。

2.  **[設定]** ブレードで、**[アプリ ポリシー]**をクリックします。 これにより、**[アプリ ポリシー]** ブレードが開き、ここで新しいポリシーを作成や、既存のポリシーの編集ができます。 **[ポリシーの追加]** を選択します。

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
> Intune 管理コンソールでアプリの MAM ポリシーを作成し、Azure ポリシーで MAM ポリシーを作成した場合は、Azure ポータルが優先します。 ただし、Intune または Configuration Manager のコンソールのレポート機能では、Intune 管理コンソールから作成されたポリシー設定がレポート対象となります。 たとえば、
>
> -   アプリからのコピーがブロックされている Intune 管理コンソールで MAM ポリシーを作成しました。
> -   アプリからのコピーが許可されている Azure コンソールで MAM ポリシーを作成しました。
> -   これら両方のポリシーを同じアプリに関連付けます。
> -   Azure コンソールから作成したポリシーが優先され、コピーが許可されることになります。
> -   ただし、Intune コンソールのステータスとレポートは、コピーがブロックされているという正しくない情報を示します。

## <a name="deploy-a-policy-to-users"></a>ユーザーへのポリシーの展開

1.  **[ポリシー]** ブレードで **[ユーザー グループ]** を選択して、**[ユーザー グループ]** ブレードを開きます。 **[ユーザー グループ]** ブレードで **[ユーザー グループの追加]** を選択して、**[ユーザー グループの追加]** ブレードを開きます。

    ![[ユーザー グループの追加] メニュー オプションが強調表示されている [ユーザー グループ] ブレードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_AddUserstoPolicy.png)

2.  ユーザー グループの一覧が、 **[ユーザー グループの追加]** ブレードに表示されます。 これは、 **Azure Active Directory**内にあるすべてのセキュリティ グループの一覧です。 このポリシーを適用するユーザー グループを選択し、**[選択]** を選択します。 **[選択]** を選択すると、ポリシーがユーザーに展開されます。

    ![Azure Active Directory ユーザーの一覧を示している [ユーザー グループの追加] ブレードのスクリーン ョット](../media/AppManagement/AzurePortal_MAM_SelectUserstoDeploy.png)

    これで、作成したポリシーはユーザーに展開されました。

[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ライセンスが割り当てられているユーザーのみが、このポリシーの影響を受けます。 選択したセキュリティ グループ内のユーザーのうち、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ライセンスが割り当てられていないユーザーは影響を受けません。

>[!IMPORTANT]
> Intune を使用し、Configuration Manager によって iOS デバイスと Android デバイスを管理する場合、このポリシーは、選択したグループ直下のユーザーにのみ適用されます。 選択したグループ内にネストされた子グループのメンバーは、影響を受けません。

エンド ユーザーは App Store または Google Play からアプリをダウンロードできます。 詳細については、次をご覧ください。
* [MAM ポリシーを使用して Android アプリを管理するときの注意点](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [MAM ポリシーを使用して iOS アプリを管理するときの注意点](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

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
* [MAM ポリシーを使用して Android アプリを管理するときの注意点](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [MAM ポリシーを使用して iOS アプリを管理するときの注意点](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


