---
title: "Intune でデバイス カテゴリを使用する方法"
titleSuffix: Azure portal
description: "Intune でデバイスを登録するときにユーザーが選択できるデバイス カテゴリを使用する方法について説明します。\""
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e1200ce4ab5d24f8c9212c064961a167e0ec6c42
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="map-device-groups"></a>デバイス グループをマップする

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune のデバイス カテゴリを使用して、ユーザー定義のカテゴリに基づいてデバイスを自動的にグループに追加することで、デバイスの管理が容易になります。

デバイス カテゴリでは、次のワークフローを使用します。
1. ユーザーがデバイスを登録する際に選択肢として表示するカテゴリを作成します。
2. iOS デバイスと Android デバイスのエンド ユーザーがデバイスを登録する場合、構成されているカテゴリの一覧からカテゴリを選択する必要があります。 Windows デバイスにカテゴリを割り当てるには、エンド ユーザーはポータル サイトを使用する必要があります (詳細については、この記事の「**デバイス グループの構成後**」をご覧ください)。
3. 次に、ポリシーとアプリをグループに展開します。

次のように、任意のデバイス カテゴリを作成できます。
- 販売時点管理デバイス
- デモンストレーション デバイス
- 営業
- アカウンティング
- Manager

## <a name="how-to-configure-device-categories"></a>デバイス カテゴリを構成する方法

### <a name="step-1---create-device-categories-in-the-intune-blade-of-the-azure-portal"></a>手順 1 - Azure Portal の [Intune] ブレードでデバイス カテゴリを作成する
1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの登録]** を選択します。
3. **[デバイスの登録]** ブレードで、**[デバイス カテゴリ]** を選択します。
4. **[デバイス カテゴリ]** ページで、**[作成]** を選択して、新しいカテゴリを追加します。
5. 次のブレードで、新しいカテゴリの**名前**と省略可能な**説明**を入力します。
6. 完了したら **[作成]** をクリックします。 カテゴリの一覧に、この新しいカテゴリが表示されます。

デバイス カテゴリ名は、手順 2 で Azure Active Directory セキュリティ グループを作成するときに使用します。

### <a name="step-2---create-azure-active-directory-security-groups"></a>手順 2 - Azure Active Directory セキュリティ グループを作成する
この手順では、デバイス カテゴリとデバイス カテゴリ名に基づいて、Azure ポータルで動的グループを作成します。

次に進む前に、Azure Active Directory ドキュメントの記事「[属性を利用した高度なルールの作成](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects)」をご覧ください。

このセクションの情報を参考にして、**deviceCategory** 属性を使用して高度なルールのデバイス グループを作成します。 例: (**device.deviceCategory -eq** "*<the device category name you got from the Azure portal>*")

デバイス グループを構成し、ユーザーがデバイスを登録すると、構成したカテゴリの一覧が表示されます。 ユーザーがカテゴリを選択して登録を完了すると、選択したカテゴリに対応する Active Directory セキュリティ グループにデバイスが追加されます。

### <a name="how-to-view-the-categories-of-devices-you-manage"></a>管理対象デバイスのカテゴリを表示する方法

1.  Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. Azure Portal の [Intune] ブレードで、**[デバイスとグループ]** を選択します。

3.  **[管理]** の **[すべてのデバイス]** をクリックします。

4.  デバイスの一覧の **[カテゴリ]** 列を確認します。

**[カテゴリ]** 列が表示されていない場合は、**[列]** をクリックし、一覧から**[カテゴリ]** を選択して、**[適用]** をクリックします。

### <a name="to-change-the-category-of-a-device"></a>デバイスのカテゴリを変更するには

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスとグループ]** を選択します。
4. **[デバイスとグループ]** ブレードで、**[管理]** > **[すべてのデバイス]** の順に選択します。
5. デバイスの一覧で目的のデバイスを選択し、デバイスのプロパティ ブレードで、**[管理]** > **[プロパティ]** の順に選択します。
6. 次のブレードで、選択したデバイスの **[デバイス カテゴリ]** を、以前に構成したカテゴリ名のいずれかに変更できます。

## <a name="after-you-configure-device-groups"></a>デバイス グループの構成後

iOS デバイスと Android デバイスのエンド ユーザーがデバイスを登録する場合、構成されているカテゴリの一覧からカテゴリを選択する必要があります。 ユーザーがカテゴリを選択して登録を完了すると、選択したカテゴリに対応する Intune デバイス グループまたは Active Directory セキュリティ グループにデバイスが追加されます。

プラットフォームにかかわらず、エンド ユーザーはデバイスを登録した後いつでも portal.manage.microsoft.com にアクセスできます。 ポータル サイト Web サイトにアクセスし、**[デバイス]** に移動します。 ページに表示されている登録済みデバイスを選び、次にカテゴリを選びます。

カテゴリを選択すると、作成済みの対応するグループにデバイスが自動的に追加されます。 カテゴリを構成する前にデバイスが既に登録されている場合は、エンド ユーザーにはデバイスに関する通知がポータル サイトに表示され、次回ユーザーが iOS または Android でポータル サイト アプリにアクセスするときに、カテゴリの選択を求められます。

## <a name="further-information"></a>詳細情報
- Azure Portal でデバイス カテゴリを編集できますが、そのカテゴリを参照するすべての Azure Active Directory セキュリティ グループを手動で更新する必要があります。

- カテゴリを削除すると、そのカテゴリに割り当てられていたデバイスのカテゴリ名が "**未割り当て**" と表示されます。
