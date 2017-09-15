---
title: "Azure Portal での Intune クラシック グループ"
titleSuffix: Azure portal
description: "Intune Azure Portal でのグループの新機能について説明します"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angerobe
ms.date: 01/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 323f384d-8a76-4adc-999b-e508d641bfa1
ms.custom: intune-azure
ms.openlocfilehash: 7ba5c3d0e6f241c5734d629a23f092ac007f8300
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="intune-classic-groups-in-the-azure-portal"></a>Azure Portal での Intune クラシック グループ

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

ユーザーからのフィードバックに対応して、Microsoft Intune でグループを操作する方法が変更されています。
Azure Portal から Intune を使用している場合、Intune グループが Azure Active Directory セキュリティ グループに移行されています。

お客様にとってのメリットは、すべての Enterprise Mobility + Security と Azure AD アプリで同じグループ エクスペリエンスを使えるようになったことです。 さらに、PowerShell と Graph API を使って、この新しい機能を拡張およびカスタマイズすることができます。

Azure AD セキュリティ グループは、ユーザーとデバイスの両方に対するあらゆる種類の Intune 展開をサポートします。 さらに、ユーザーが指定した属性に基づいて自動的に更新する Azure AD の動的グループを使用できます。 たとえば、iOS 9 搭載デバイスのグループを作成できます。 iOS 9 を実行しているデバイスを登録するたびに、デバイスに動的なグループが自動的に表示されます。

## <a name="what-is-not-available"></a>利用できない機能

以前に使用できた Intune グループの機能は一部 Azure AD では利用できません。

- Intune の**グループに属していないユーザー** グループと**グループに属していないデバイス** グループは利用できなくなります。
- グループから**特定のメンバーを除外**するオプションは、Azure Portal にはありません。 ただし、Azure AD セキュリティ グループと高度なルールを使用して、この動作を複製できます。 たとえば、肩書きに "Assistant" が付いているグループを除く、営業部内のすべてのユーザーをセキュリティ グループに含める高度なルールを作成する場合は、次の高度なルールを使用できます。

  `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`
- Intune クラシック コンソールの **Exchange ActiveSync で管理されているすべてのデバイス** グループは、Azure AD に移行されていません。 ただし、EAS で管理されたデバイスに関する情報には、Azure Portal から引き続きアクセスできます。

## <a name="how-to-get-started"></a>開始する方法

- Azure AD のセキュリティ グループとそのしくみの詳細については、次のトピックを参照してください。
    -  [Azure Active Directory グループを利用したリソースへのアクセス管理](https://azure.microsoft.com/documentation/articles/active-directory-manage-groups/)
    -  [Azure Active Directory でのグループの管理](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/)
    -  [属性を利用した高度なルールの作成](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)
-  グループを作成する必要がある管理者が、**Intune サービス管理者** Azure AD ロールに追加されていることを確認します。 Azure AD サービス管理者ロールには**グループの管理**アクセス許可がありません。
-  Intune グループで **[特定のメンバーを除外]** オプションを使用している場合は、除外を必要としないようにグループを再設計できるかどうか、またはビジネス ニーズを満たすために高度なルールが必要かどうかを判断してください。


## <a name="what-happened-to-intune-groups"></a>Intune グループに対する移行処理の内容
グループを Azure Portal から Azure Portal の Intune に移行すると、次のルールが適用されます。

| Intune のグループ|Azure AD でのグループ|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|静的なユーザー グループ|静的な Azure AD セキュリティ グループ|
|動的なユーザー グループ|Azure AD セキュリティ グループの階層構造を持つ静的な Azure AD セキュリティ グループ|
|静的なデバイス グループ|静的な Azure AD セキュリティ グループ|
|動的なデバイス グループ|静的な Azure AD セキュリティ グループ|
|"含める条件" 付きのグループ|Intune の "含める条件" のすべての静的メンバーまたは動的メンバーを含む静的な Azure AD セキュリティ グループ|
|"除外条件" 付きのグループ|移行されません|
|組み込みグループ:<br>- **すべてのユーザー**<br>- **グループに属していないユーザー**<br>- **すべてのデバイス**<br>- **グループに属していないデバイス**<br>- **すべてのコンピューター**<br>- **すべてのモバイル デバイス**<br>- **MDM で管理されているすべてのデバイス**<br>- **EAS で管理されているすべてのデバイス**|Azure AD セキュリティ グループ|

## <a name="group-hierarchy"></a>グループ階層

Intune コンソールでは、すべてのグループに親グループがありました。 グループには、親グループのメンバーのみを含めることができました。 Azure AD の子グループには、親グループに含まれないメンバーを含めることができます。

## <a name="group-attributes"></a>グループの属性
属性は、グループの定義時に使用できるデバイス プロパティです。 次の表では、条件を Azure AD セキュリティ グループに移行する方法について説明します。

| Intune での属性|Azure AD での属性|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|デバイス グループの組織単位 (OU) 属性|動的なグループの OU 属性。|
|デバイス グループのドメイン名属性|動的なグループのドメイン名属性。|
|ユーザー グループの属性としてセキュリティ グループ|Azure AD の動的クエリで属性を使用することはできません。 動的なグループには、ユーザーまたはデバイス固有の属性のみを含めることができます。|
|ユーザー グループに対するマネージャー属性|動的グループの *manager* 属性に対する高度なルール|
|親ユーザー グループのすべてのユーザー|そのグループをメンバーとして含む静的なグループ|
|親デバイス グループのすべてのモバイル デバイス|そのグループをメンバーとして含む静的なグループ|
|Intune によって管理されているすべてのモバイル デバイス|動的なグループの値として 'MDM' が使用される Management Type 属性|
|静的なグループ内で入れ子になったグループ |静的なグループ内で入れ子になったグループ|
|動的なグループ内で入れ子になったグループ|入れ子のレベルが 1 である動的なグループ|

## <a name="what-happens-to-policies-and-apps-you-previously-deployed"></a>以前に展開されているポリシーおよびアプリに対する処理

ポリシーとアプリは、移行前と同じように、引き続きグループに展開されます。 ただし、これらのグループの管理は、Intune コンソールではなく、Azure Portal から行うようになります。
