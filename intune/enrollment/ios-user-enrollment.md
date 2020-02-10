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
ms.openlocfilehash: 0872eef38e3ea5a70ebb64d3ae3c62069045fa97
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754630"
---
# <a name="set-up-ios-and-ipados-user-enrollment-preview"></a>iOS と iPadOS のユーザー登録を設定する (プレビュー)

Apple のユーザー登録プロセスを使用して、iOS デバイスと iPadOS デバイスを登録するように Intune を設定できます。 ユーザー登録により、管理者は他の登録方法と比較して簡素化された一部の管理オプションを使用できるようになります。

ユーザー登録で使用できるオプションの詳細については、[ユーザー登録でサポートされるアクション、パスワードなどのオプション](ios-user-enrollment-supported-actions.md)に関する記事を参照してください。

> [!NOTE]
> Intune での Apple のユーザー登録のサポートは、現在プレビュー段階です。

## <a name="prerequisites"></a>[前提条件]
- [モバイル デバイス管理 (MDM) 機関](../fundamentals/mdm-authority-set.md)
- [Apple MDM プッシュ証明書](apple-mdm-push-certificate-get.md)
- [マネージド Apple ID](https://support.apple.com/guide/apple-business-manager/mdm1c9622977/web)。

## <a name="create-a-user-enrollment-profile-in-intune"></a>Intune でユーザー登録プロファイルを作成する

登録プロファイルで、デバイス グループに対して登録時に適用する設定を定義します。 

1. [Microsoft Endpoint Manage 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[iOS]**  >  **[iOS の登録]**  >  **[登録の種類 (プレビュー)]**  >  **[プロファイルの作成]**  >  **[iOS/iPadOS]** を選択します。 このプロファイルでは、iOS および iPadOS のエンド ユーザーが、会社の Apple メソッドで登録されていないデバイスでどのような登録エクスペリエンスを利用できるかを指定します。 変更が必要な場合は、作成後にこのプロファイルを編集できます。

    ![Apple 登録プロファイルを作成する](./media/ios-user-enrollment/create-profile.png)

2. **[基本]** ページ上で、管理用にプロファイルの **[名前]** と **[説明]** を入力します。 ユーザーには、これらの詳細は表示されません。 この **[名前]** フィールドを使用して、Azure Active Directory で動的グループを作成できます。 この登録プロファイルに対応するデバイスを割り当てるために enrollmentProfileName パラメーターを定義する場合はプロファイル名を使用します。 Azure Active Directory の動的グループの詳細については[こちら](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices)を参照してください。

    ![[基本] ページ](./media/ios-user-enrollment/basics-page.png)


3. **[次へ]** を選択します。

4. **[設定]** ページで、 **[登録の種類]** に対して次のいずれかのオプションを選択します。

    ![[設定] ページ](./media/ios-user-enrollment/settings-page.png)

    - **デバイスの登録**:このプロファイル内のすべてのユーザーは、[デバイスの登録] を使用します。
    - **ユーザー登録**:このプロファイル内のすべてのユーザーは、[ユーザー登録] を使用します。
    - **Determine based on user choice (ユーザーの選択に基づいて決定する)** :このグループのすべてのユーザーには、使用する登録の種類の選択肢が表示されます。 ユーザーが自分のデバイスを登録すると、 **[I own this device]\(このデバイスを所有している\)** と **[(Company) owns this device]\((会社が) このデバイスを所有している\)** から選択できるようになります。 後者を選択した場合は、デバイスの登録を使用してデバイスが登録されます。 ユーザーが **[I own this device]\(このデバイスを所有している\)** を選択した場合は、さらにデバイス全体をセキュリティで保護するか、職場関連のアプリとデータのみをセキュリティで保護するかを選択できます。 デバイスを所有するかどうかのエンド ユーザーによる選択で、デバイスに実装されている登録の種類が決まります。 このユーザーの選択は、Intune の [デバイスの所有者] 属性にも反映されます。 ユーザー エクスペリエンスの詳細については、「[iOS デバイスからの会社のリソースへのアクセスを設定する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)」を参照してください。
    
5. **[次へ]** を選択します。

6. **[割り当て]** ページで、このプロファイルを割り当てるユーザーを含むユーザー グループを選択します。 すべてのユーザーまたは特定のグループにプロファイルを割り当てることができます。 選択したグループ内のすべてのユーザーが、上で選択した登録の種類を使用します。 デバイス グループは、デバイスではなくユーザー ID に基づいているため、ユーザー登録シナリオではサポートされません。 すべてのユーザーまたは特定のグループにプロファイルを割り当てることができます。

    ![[割り当て] ページ](./media/ios-user-enrollment/assignments-page.png)

7. **[次へ]** を選択します。

8. **[確認と作成]** ページで、選択内容を確認し、 **[作成]** を選択して、プロファイルをユーザーに割り当てます。

    ![[割り当て] ページ](./media/ios-user-enrollment/assignments-page.png)


## <a name="profile-priority"></a>プロファイルの優先順位

複数の登録の種類のプロファイルを作成した後は、適用される優先順位を変更できます。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[iOS]**  >  **[iOS の登録]**  >  **[登録の種類 (プレビュー)]** を選択します。
2. 一覧のプロファイルを、適用する順序でドラッグ アンド ドロップします。

ユーザーのプロファイル間で競合が生じた場合は、優先順位の高いプロファイルがユーザーに適用されます。


