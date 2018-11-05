---
title: アプリ保護ポリシーを作成して展開する
titleSuffix: Microsoft Intune
description: Microsoft Intune アプリ保護ポリシーを作成して割り当てる方法について説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d7dbb0214bb80fa0f72808c15eacc6799c0807cc
ms.sourcegitcommit: 46f6f3d4e1c7c0a5a716503f759ea5cf03c1a02b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2018
ms.locfileid: "50136949"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>アプリ保護ポリシーを作成して割り当てる方法

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune アプリ保護ポリシーを作成してユーザーに割り当てる方法について説明します。 このトピックでは、既存のポリシーを変更する方法についても説明します。

## <a name="before-you-begin"></a>始める前に

アプリ保護ポリシーは、場合によっては Intune で管理できないデバイスで実行されているアプリに適用できます。 アプリ保護ポリシーのしくみと Intune のアプリ保護ポリシーでサポートされるシナリオの詳細については、[Microsoft Intune のアプリ保護ポリシー](app-protection-policy.md)に関するページを参照してください。

MAM でサポートされるアプリの一覧については、[MAM アプリの一覧](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)に関するページをご覧ください。

組織の基幹業務 (LOB) アプリを Microsoft Intune に追加してアプリ保護ポリシーを準備する方法について詳しくは、「[Microsoft Intune にアプリを追加する](apps-add.md)」をご覧ください。

##  <a name="create-an-app-protection-policy"></a>アプリ保護ポリシーを作成する
1. **クライアント アプリ** ワークロードで、**[管理]** セクションから **[アプリ保護ポリシー]** を選択します。 この選択により、**[アプリ保護ポリシー]** の詳細が開き、ここで新しいポリシーを作成したり、既存のポリシーを編集したりできます。
2. **[ポリシーの追加]** を選択します。

   ![[ポリシーの追加] ブレードのスクリーンショット](./media/app-protection-add-policy.png)

3. ポリシーの名前を入力して簡単な説明を追加し、ポリシーのプラットフォームの種類を選択します。 必要に応じて、プラットフォームごとに複数のポリシーを作成できます。

4. **[アプリ]** を選択して **[アプリ]** ブレードを開くと、使用可能なアプリの一覧が表示されます。 一覧から、作成するポリシーに関連付けるアプリを 1 つまたは複数選択します。
5. アプリを選択したら、**[選択]** を選び、選択内容を保存します。

    > [!IMPORTANT]
    > ポリシーを作成するには、少なくとも 1 つのアプリを選択する必要があります。

6. **[ポリシーの追加]** ブレードで、**[必要な設定の構成]** を選択し、**[設定]** を開きます。

   ポリシー設定には、**[データ再配置]** と **[アクセス]** の 2 つのカテゴリがあります。  データ再配置ポリシーは、アプリ間のデータの移動に適用できます。 アクセス ポリシーは、エンド ユーザーが仕事関連でアプリにアクセスする方法を決定します。
   ユーザーが開始できるように、ポリシー設定には既定値が入力されています。 既定値が要件を満たす場合は、変更を加える必要はありません。

   > [!TIP]
   > これらのポリシー設定は、作業コンテキストでアプリを使用する場合にのみ適用されます。 エンド ユーザーが、個人のタスクを実行するためにアプリを使用する場合、これらのポリシーによる影響を受けることはありません。 作成した新しいファイルは、個人用ファイルだと見なされることに注意してください。 

7. **[OK]** を選択して、この構成を保存します。 これにより、**[ポリシーの追加]** ブレードに戻ります。
8. **[作成]** を選択してポリシーを作成し、設定を保存します。

前の手順の説明に従ってポリシーの作成が完了した時点では、ポリシーはユーザーに展開されません。 ポリシーを展開するには、「[ユーザーへのポリシーの展開](app-protection-policies.md#deploy-a-policy-to-users)」を参照してください。

## <a name="deploy-a-policy-to-users"></a>ユーザーへのポリシーの展開

1. **[アプリ保護ポリシー]** ウィンドウでポリシーを選択します。

2. **[ポリシー]** ウィンドウで、**[割り当て]** を選択して、**[Intune App Protection - 割り当て]** ウィンドウを開きます。 **[割り当て]** ウィンドウで **[含めるグループを選択]** を選択し、**[含めるグループを選択]** ウィンドウを開きます。

   ![[含めるグループを選択] メニュー オプションが強調表示された [割り当て] ウィンドウのスクリーンショット](./media/app-protection-policy-add-users.png)

3.  ユーザー グループの一覧が、 **[ユーザー グループの追加]** ウィンドウに表示されます。 この一覧には、**Azure Active Directory** 内にあるすべてのセキュリティ グループが表示されます。 このポリシーを適用するユーザー グループを選択し、**[選択]** を選択します。 **[選択]** を選択すると、ポリシーがユーザーに展開されます。

    ![Azure Active Directory ユーザーの一覧を示している [ユーザー グループの追加] ウィンドウのスクリーンショット](./media/azure-ad-user-group-list.png)

これで、作成したポリシーはユーザーに展開されました。

Microsoft Intune ライセンスが割り当てられているユーザーのみが、このポリシーの影響を受けます。 Intune ライセンスが割り当てられていない、選択したセキュリティ グループ内のユーザーは、影響を受けません。

>[!IMPORTANT]
> Intune を使用し、Configuration Manager によってデバイスを管理する場合、このポリシーは、選択したグループ直下のユーザーにのみ適用されます。 選択したグループ内で入れ子になっている子グループのメンバーは、影響を受けません。

エンド ユーザーは App Store または Google Play からアプリをダウンロードできます。 詳細については、次をご覧ください。
* [アプリ保護ポリシーを使用して Android アプリを管理するときの注意点](app-protection-enabled-apps-android.md)
* [アプリ保護ポリシーを使用して iOS アプリを管理するときの注意点](app-protection-enabled-apps-ios.md)

##  <a name="change-existing-policies"></a>既存のポリシーの変更
既存のポリシーを編集して、対象ユーザーに適用できます。 ただし、既存のポリシーを変更する場合、アプリに既にサインインしているユーザーには、8 時間にわたって変更が表示されません。

変更の効果をすぐに確認するには、エンド ユーザーはアプリをログアウトし、もう一度サインインする必要があります。

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>ポリシーに関連付けられているアプリの一覧を変更するには

1.  **[アプリ保護ポリシー]** ウィンドウで、変更するポリシーを選択して、その選択したポリシーに固有のウィンドウを開きます。

2.  ポリシー ウィンドウで **[対象アプリ]** を選択し、アプリの一覧を開きます。

3.  一覧からアプリを削除または追加し、**[保存]** アイコンを選択して変更内容を保存します。

### <a name="to-change-the-list-of-user-groups"></a>ユーザー グループの一覧を変更するには


1.  **[アプリ保護ポリシー]** ウィンドウで、変更するポリシーを選択して、その選択したポリシーに固有のウィンドウを開きます。

2.  ポリシー ウィンドウで、**[割り当て]** を選択して **[Intune App Protection - 割り当て]** ウィンドウを開きます。このウィンドウには、このポリシーを持つ現在のユーザー グループの一覧が表示されます。

3.  ポリシーに新しいユーザー グループを追加するには、**[含める]** タブで **[含めるグループを選択]** を選択し、ユーザー グループを選択します。 **[選択]** を選択して、選択したグループにポリシーを展開します。

4.  ユーザー グループを削除するには、**[除外]** タブで **[含めないグループを選択]** を選択し、ユーザー グループを選択します。 **[選択]** を選択してユーザー グループを削除します。

### <a name="to-change-policy-settings"></a>ポリシー設定を変更するには

1.  **[アプリ保護ポリシー]** ウィンドウで、変更するポリシーを選択して、その選択したポリシーに固有のウィンドウを開きます。

2.  **[ポリシー設定]** を選択して **[ポリシー設定]** ウィンドウを開きます。

3.  設定を変更し、**[保存]** アイコンを選択して変更内容を保存します。

## <a name="target-app-protection-policies-based-on-device-management-state"></a>デバイス管理状態に基づくアプリ保護ポリシーの対象指定
多くの組織では、企業所有デバイスなどの Intune モバイル デバイス管理 (MDM) マネージド デバイスと、BYO デバイスなどの Intune アプリ保護ポリシーでのみ保護されるアンマネージド デバイスの両方をエンド ユーザーが使用できるようにするのが一般的です。

Intune アプリ保護ポリシーの対象はユーザーの ID であるため、ユーザーの保護設定は従来、登録されている (MDM 管理対象) デバイスと登録されていないデバイス (MDM なし) の両方に適用されます。 したがって、Intune に登録されている、または登録されていない iOS および Android デバイスを Intune アプリ保護ポリシーの対象にすることができます。 厳格なデータ損失防止 (DLP) 制御が行われている、アンマネージド デバイスに対して 1 つの保護ポリシーを適用し、MDM マネージド デバイスに対して別の保護ポリシーを適用することができます。この場合、DLP 制御が少し緩和される可能性があります。 

これらのポリシーを作成するには、Intune コンソールで **[クライアント アプリ]** > **[アプリ保護ポリシー]** を参照し、**[ポリシーの追加]** をクリックします。 既存のアプリ保護ポリシーを編集することもできます。 マネージド デバイスとアンマネージド デバイスの両方にアプリ保護ポリシーを適用する場合は、**[Target to all app types]\(すべてのアプリの種類を対象とする\)** が **[はい]** (既定値) に設定されていることを確認してください。 管理状態に基づいて細かく割り当てる場合は、**[Target to all app types]\(すべてのアプリの種類を対象とする\)** オプションを **[いいえ]** に設定します。 

![[Target to all app types]\(すべてのアプリの種類を対象とする\) が選択された [Add an policy]\(ポリシーの追加\) ブレードのスクリーン ショット](./media/app-protection-policies-target-all.png)

iOS の場合、Intune に登録されているデバイスのアプリに APP 設定を行うには、さらにアプリを構成設定する必要があります。
- **IntuneMAMUPN** を、MDM で管理されているすべてのアプリケーションに構成する必要があります。  詳細については、「[Microsoft Intune で iOS アプリ間のデータ転送を管理する方法](https://docs.microsoft.com/intune/data-transfer-between-apps-manage-ios#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm)」を参照してください。
- **IntuneMAMDeviceID** を、すべてのサードパーティ製アプリケーションおよび LOB MDM マネージド アプリケーションに構成する必要があります。 **IntuneMAMDeviceID** を、デバイスの ID トークンに構成する必要があります。 たとえば、`key=IntuneMAMDeviceID, value={{deviceID}}` のように指定します。 詳細については、「[管理対象の iOS デバイス用アプリ構成ポリシーを追加する](https://docs.microsoft.com/intune/app-configuration-policies-use-ios)」を参照してください。
- **IntuneMAMDeviceID** のみが構成されている場合、Intune APP はデバイスが管理対象であると見なしません。  

> [!NOTE]
> デバイス管理状態に基づくアプリ保護ポリシーに関する特定の iOS サポート情報については、[管理の状態に基づいて対象とされる MAM 保護ポリシー](whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state-)に関するページを参照してください。

## <a name="policy-settings"></a>ポリシー設定
iOS と Android 用のポリシー設定の完全な一覧を表示するには、次のいずれかのリンクを選択します。

- [iOS ポリシー](app-protection-policy-settings-ios.md)
- [Android ポリシー](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>次の手順
[コンプライアンスとユーザーの状態を監視する](app-protection-policies-monitor.md)

### <a name="see-also"></a>関連項目
* [アプリ保護ポリシーを使用して Android アプリを管理するときの注意点](app-protection-enabled-apps-android.md)
* [アプリ保護ポリシーを使用して iOS アプリを管理するときの注意点](app-protection-enabled-apps-ios.md)
