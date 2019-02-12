---
title: Intune を使用してデバイスをグループに分類する
titleSuffix: Microsoft Intune
description: 管理を容易にするためにデバイスをグループに分類する方法を説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a7bb551784af2f61b61cfc57b968e32ab4db2f7e
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848051"
---
# <a name="categorize-devices-into-groups"></a>デバイスをグループに分類する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

デバイス管理を容易にするために、Microsoft Intune デバイス カテゴリを使用し、定義したカテゴリに基づいてデバイスをグループに自動的に追加することができます。

デバイス カテゴリでは、次のワークフローを使用します。
1. ユーザーがデバイスを登録するときに選択できるカテゴリを作成します。
2. iOS デバイスと Android デバイスのユーザーがデバイスを登録する場合、構成されているカテゴリの一覧からカテゴリを選択する必要があります。 Windows デバイスにカテゴリを割り当てる場合、ユーザーはポータル Web サイトを使用する必要があります。
3. 次に、ポリシーとアプリをグループに展開します。

任意のデバイス カテゴリを作成できます。 次に例を示します。
- POS デバイス
- デモンストレーション デバイス
- 営業
- アカウンティング
- Manager

## <a name="how-to-configure-device-categories"></a>デバイス カテゴリを構成する方法

### <a name="step-1-create-device-categories-on-the-intune-blade-of-the-azure-portal"></a>手順 1.Azure portal の [Intune] ブレードでデバイス カテゴリを作成する
1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** を選択します。
2. **[デバイスの登録]** ブレードで、**[デバイス カテゴリ]** を選択します。
3. **[デバイス カテゴリ]** ページで、**[作成]** を選択して、新しいカテゴリを追加します。
4. **[デバイス カテゴリの作成]** ブレードで、新しいカテゴリの**名前**と省略可能な**説明**を入力します。
5. 完了したら、**[作成]** を選択します。 カテゴリの一覧に、この新しいカテゴリが表示されます。

デバイス カテゴリ名は、手順 2 で Azure Active Directory (Azure AD) セキュリティ グループを作成するときに使用します。

### <a name="step-2-create-azure-active-directory-security-groups"></a>手順 2: Azure Active Directory セキュリティ グループを作成する
この手順では、デバイス カテゴリとデバイス カテゴリ名に基づいて、Azure Portal で動的グループを作成します。

次に進む前に、Azure AD ドキュメントの「[属性を利用した高度なルールの作成](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects)」を参照してください。

このセクションの情報を参考にして、**deviceCategory** 属性を使用して高度なルールのデバイス グループを作成します。 例: **device.deviceCategory -eq** "*Azure Portal から取得したデバイス カテゴリ名*"。

デバイス グループを構成し、ユーザーがデバイスを登録すると、構成したカテゴリの一覧が表示されます。 ユーザーがカテゴリを選択して登録を完了すると、選択したカテゴリに対応する Active Directory セキュリティ グループにデバイスが追加されます。

### <a name="view-the-categories-of-devices-that-you-manage"></a>管理対象デバイスのカテゴリを表示する

1.  [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイス]** を選択します。

2.  **[管理]** で、**[すべてのデバイス]** を選択します。

3.  デバイスの一覧の **[デバイス カテゴリ]** 列を確認します。

**[デバイス カテゴリ]** 列が表示されていない場合は、**[列]** を選択します。 一覧から **[デバイス カテゴリ]** を選択します。次に、**[適用]** を選択します。

### <a name="change-the-category-of-a-device"></a>デバイスのカテゴリを変更する

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイス]** を選択します。
2. **[デバイス]** ブレードの **[管理]** セクションで、**[すべてのデバイス]** を選択します。
3. デバイスの一覧で、目的のデバイスを選択します。 次に、**[管理]** セクションの下のデバイス プロパティ ブレードで、**[プロパティ]** を選択します。
4. 次のブレードで、選択したデバイスの **[デバイス カテゴリ]** を、以前に構成したカテゴリ名のいずれかに変更できます。

## <a name="after-you-configure-device-groups"></a>デバイス グループの構成後

iOS デバイスと Android デバイスのユーザーがデバイスを登録する場合、構成されているカテゴリの一覧からカテゴリを選択する必要があります。 ユーザーがカテゴリを選択して登録を完了すると、選択したカテゴリに対応する Active Directory セキュリティ グループ、または Intune デバイス グループにデバイスが追加されます。

Windows ユーザーがカテゴリを選択するには、ポータル Web サイトを使用する必要があります。

プラットフォームにかかわらず、ユーザーはデバイスを登録した後いつでも portal.manage.microsoft.com にアクセスできます。 ポータル Web サイトにアクセスし、**[デバイス]** に移動します。 ページに一覧表示されている登録済みデバイスを選択し、次にカテゴリを選択します。

カテゴリを選択すると、作成済みの対応するグループにデバイスが自動的に追加されます。 カテゴリを構成する前にデバイスが既に登録されている場合、ユーザーにはポータル Web サイトのデバイスに関する通知が表示されます。 これで、次回 iOS または Android でポータル サイト アプリにアクセスするときに、ユーザーにカテゴリの選択について知らせることができます。

## <a name="further-information"></a>詳細情報
- Azure Portal でデバイス カテゴリを編集できますが、このカテゴリを参照するすべての Azure AD セキュリティ グループを手動で更新する必要があります。

- カテゴリを削除すると、そのカテゴリに割り当てられていたデバイスのカテゴリ名が "**未割り当て**" と表示されます。
