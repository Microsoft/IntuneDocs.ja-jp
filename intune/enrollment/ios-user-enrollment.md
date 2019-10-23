---
title: iOS デバイスの登録 - ユーザー登録
titleSuffix: Microsoft Intune
description: iOS と iPadOS のユーザー登録を設定する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f201cdac0f881ce03863704dd80d8635de52074a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505466"
---
# <a name="set-up-ios-and-ipados-user-enrollment-preview"></a>iOS と iPadOS のユーザー登録を設定する (プレビュー)

Apple のユーザー登録プロセスを使用して、iOS デバイスと iPadOS デバイスを登録するように Intune を設定できます。 ユーザー登録により、管理者は他の登録方法と比較して簡素化された一部の管理オプションを使用できるようになります。

ユーザー登録で使用できるオプションの詳細については、[ユーザー登録でサポートされるアクション、パスワードなどのオプション](ios-user-enrollment-supported-actions.md)に関する記事を参照してください。

> [!NOTE]
> Intune での Apple のユーザー登録のサポートは、現在プレビュー段階です。

## <a name="prerequisites"></a>必要条件
- [モバイル デバイス管理 (MDM) 機関](../fundamentals/mdm-authority-set.md)
- [Apple MDM プッシュ証明書](apple-mdm-push-certificate-get.md)
- [マネージド Apple ID](https://support.apple.com/guide/apple-business-manager/mdm1c9622977/web)。

## <a name="create-a-user-enrollment-profile-in-intune"></a>Intune でユーザー登録プロファイルを作成する

登録プロファイルで、デバイス グループに対して登録時に適用する設定を定義します。 

1. Intune ポータルで、 **[デバイスの登録]**  >  **[Apple の登録]**  >  **[Enrollment types (preview)]\(登録の種類 (プレビュー)\)**  >  **[プロファイルの作成]**  >  **[iOS]** を選択します。 このプロファイルでは、iOS および iPadOS のエンド ユーザーが、会社の Apple メソッドで登録されていないデバイスでどのような登録エクスペリエンスを利用できるかを指定します。 変更が必要な場合は、作成後にこのプロファイルを編集できます。

    ![Apple 登録プロファイルを作成する](./media/ios-user-enrollment/create-profile.png)

2. **[基本]** ページ上で、管理用にプロファイルの **[名前]** と **[説明]** を入力します。 ユーザーには、これらの詳細は表示されません。 この **[名前]** フィールドを使用して、Azure Active Directory で動的グループを作成できます。 この登録プロファイルに対応するデバイスを割り当てるために enrollmentProfileName パラメーターを定義する場合はプロファイル名を使用します。 Azure Active Directory の動的グループの詳細については[こちら](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices)を参照してください。

    ![[基本] ページ](./media/ios-user-enrollment/basics-page.png)


3. **[次へ]** を選択します。

4. **[設定]** ページで、使用する登録の種類をユーザーに選択させることができます。 または、管理者が既定値を設定することもできます。

    ![[設定] ページ](./media/ios-user-enrollment/settings-page.png)

    - このプロファイルのすべてのユーザーがユーザー登録を使用できるようにするには、次の手順を実行します。
        1. **[Require user to select device type]\(ユーザーがデバイスの種類を選択することを必須にする\)** について **[未構成]** を選択します。
        2. **[Default enrollment type]\(既定の登録の種類\)** について **[ユーザー登録]** を選択します。
    - このプロファイルのすべてのユーザーがデバイスの登録を使用できるようにするには、次の手順を実行します。
        1. **[Require user to select device type]\(ユーザーがデバイスの種類を選択することを必須にする\)** について **[未構成]** を選択します。
        2. **[Default enrollment type]\(既定の登録の種類\)** について **[デバイスの登録]** を選択します。
    - このグループのすべてのユーザーに、使用する登録の種類の選択を許可する場合は、 **[Require user to select device type]\(ユーザーがデバイスの種類を選択することを必須にする\)** について **[必須]** を選択します。 ユーザーが自分のデバイスを登録すると、 **[I own this device]\(このデバイスを所有している\)** と **[(Company) owns this device]\((会社が) このデバイスを所有している\)** から選択できるようになります。 前者を選択した場合、デバイスはユーザー登録を使用して登録されます。 後者を選択した場合は、デバイスの登録を使用してデバイスが登録されます。 ユーザーが **[I own this device]\(このデバイスを所有している\)** を選択した場合は、さらにデバイス全体をセキュリティで保護するか、職場関連のアプリとデータのみをセキュリティで保護するかを選択できます。 デバイスを所有するかどうかのエンド ユーザーによる選択でのみ、デバイスに実装されている登録の種類が決まります。 このユーザーの選択は、Intune の [デバイスの所有者] 属性には反映されません。 ユーザー エクスペリエンスの詳細については、「[iOS デバイスからの会社のリソースへのアクセスを設定する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)」を参照してください。
    
    > [!NOTE]
    > 次の通知は不正確であり、UI から削除される予定です。
    > "For Conditional Access to work on devices targeted with User Enrollment, you will need to push the Azure Authenticator app as a required app for this user group to enable Single Sign-On and Workplace Join" (ユーザー登録を対象とするデバイスで条件付きアクセスが機能するには、このユーザー グループに必要なアプリとして Azure Authenticator アプリをプッシュして、シングル サインオンと Workplace Join を有効にする必要があります)。
    > 管理者の場合、ユーザーに Authenticator アプリをプッシュするアクションを実行する必要はありません。 これらのシナリオが適切に機能するように、ユーザーには、ポータル サイト内で Authenticator アプリをインストールしてユーザー登録プロセスを完了するように指示されます。

5. **[次へ]** を選択します。

6. **[割り当て]** ページで、このプロファイルを割り当てるユーザーを含むユーザー グループを選択します。 すべてのユーザーまたは特定のグループにプロファイルを割り当てることができます。 選択したグループ内のすべてのユーザーが、上で選択した登録の種類を使用します。 デバイス グループは、デバイスではなくユーザー ID に基づいているため、ユーザー登録シナリオではサポートされません。 すべてのユーザーまたは特定のグループにプロファイルを割り当てることができます。

    ![[割り当て] ページ](./media/ios-user-enrollment/assignments-page.png)

7. **[次へ]** を選択します。

8. **[確認と作成]** ページで、選択内容を確認し、 **[作成]** を選択して、プロファイルをユーザーに割り当てます。

    ![[割り当て] ページ](./media/ios-user-enrollment/assignments-page.png)


## <a name="profile-priority"></a>プロファイルの優先順位

複数の登録の種類のプロファイルを作成した後は、適用される優先順位を変更できます。

1. Azure portal の Intune で、 **[デバイスの登録]**  >  **[Apple の登録]**  >  **[Enrollment types (preview)]\(登録の種類 (プレビュー)\)** を選択します。
2. 一覧のプロファイルを、適用する順序でドラッグ アンド ドロップします。

ユーザーのプロファイル間で競合が生じた場合は、優先順位の高いプロファイルがユーザーに適用されます。


