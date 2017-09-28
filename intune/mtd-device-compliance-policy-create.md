---
title: "Intune で Mobile Threat Defense デバイス コンプライアンス ポリシーを作成する"
titlesuffix: Azure portal
description: "Intune で Mobile Threat Defense デバイス コンプライアンス ポリシーを作成する"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2e9b1a3dc42a9c18d61fc9b55d5a7b71f00c3e29
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2017
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Intune で Mobile Threat Defense (MTD) デバイス コンプライアンス ポリシーを作成する

> [!NOTE] 
> このトピックは、すべての Mobile Threat Defense パートナーに適用されます。

Intune で MTD を使用すると、モバイル デバイス上で脅威を検出し、リスクを評価できます。 リスクを評価する Intune デバイス コンプライアンス ポリシー ルールを作成すれば、デバイスがポリシーに準拠しているかどうかを判断できます。 さらに、条件付きアクセス ポリシーを使用することで、デバイスのコンプライアンスに基づいて、サービスへのアクセスを禁止できます。

## <a name="before-you-begin"></a>始める前に

MTD の設定の一部として、MTD パートナー コンソールで、さまざまな脅威を高、中、低として分類するポリシーを作成しておきます。 これにより、Intune デバイス コンプライアンス ポリシーに Mobile Threat Defense レベルを設定する必要があります。

MTD でのデバイス コンプライアンス ポリシーの前提条件:

-   MTD と Intune の統合をセットアップする

## <a name="to-create-a-mtd-device-compliance-policy"></a>MTD デバイス コンプライアンス ポリシーを作成するには

1.  [Azure Portal](https://portal.azure.com/) に移動し、Intune 資格情報でサインインします。

2.  **Azure ダッシュボード**で、左側のメニューから **[その他のサービス]** を選択し、テキスト ボックス フィルターに「**Intune**」と入力します。

3.  **[Intune]** を選択すると、**Intune ダッシュボード**が開きます。

4. **Intune ダッシュ ボード**で、**[デバイスのポリシー準拠]** を選択し、**[管理]** セクションで **[ポリシー]** を選択します。

5.  **[Create policy]\(ポリシーの作成\)** を選択し、デバイス コンプライアンスの **[名前]**、**[説明]** を入力し、 **[プラットフォーム]** を選択してから **[設定]** セクションの **[構成]** を選択します。

6.  **[コンプライアンス ポリシー]** ブレードで、**[Device Health]\(デバイスの正常性\)** を選択します。

7.  **[Device Health]\(デバイスの正常性\)** ブレードの、**[Require the device to be at or under the Mobile threat Defense Level]\(デバイスが Mobile Threat Defense レベル以下であることが必要)** の下で Mobile Threat レベルをドロップダウン リストから選択します。

    a.  **[セキュリティ保護]**: これはセキュリティ上最も安全です。 デバイスにいかなる脅威も存在できず、デバイスからは引き続き会社のリソースにアクセスできます。 いずれかの脅威が見つかった場合、デバイスは非準拠と評価されます。

    b.  **[低]**: 存在する脅威が低レベルの場合のみ、デバイスは準拠しています。 低レベルより高い脅威が存在する場合、デバイスは非準拠状態になります。

    c.  **[中]**: デバイスに存在する脅威が低レベルまたは中レベルの場合、デバイスは準拠しています。 高レベルの脅威が検出された場合は、デバイスは非準拠と判定されます。

    d.  **[High]** (高): 最も安全性の低い状態です。 この場合、すべての脅威レベルが許可され、レポート目的のみで Mobile Threat Defense が使用されます。 デバイスには、この設定でアクティブ化された MTD アプリが含まれている必要があります。

8.  **[OK]** を 2 回クリックしてから、**[作成]** を選択します。

> [!IMPORTANT]
> Office 365 またはその他のサービスに対する条件付きアクセス ポリシーを作成すると、デバイス コンプライアンス評価が適用され、非準拠デバイスはデバイスで脅威が解決されるまで会社のリソースへのアクセスは禁止されます。

## <a name="to-assign-a-mtd-device-compliance-policy"></a>MTD デバイス コンプライアンス ポリシーを割り当てるには

デバイス コンプライアンス ポリシーをユーザーに割り当てるには、前に構成したポリシーを選択します。 既存のポリシーは、**[デバイス コンプライアンス ポリシー]** ブレードで確認できます。

1. ユーザーに割り当てるポリシーを選択し、**[割り当て]** を選択します。 これにより表示されたブレードで、**[Azure Active Directory セキュリティ グループ]** を選択し、ポリシーに割り当てることができます。

2. **[グループの選択]** を選択すると、ブレードが開き、Azure AD セキュリティ グループが表示されます。  **[選択]** を選択すると、ポリシーがユーザーに展開されます。

    > [!NOTE] 
    > ポリシーがユーザーに適用されました。 ポリシーの対象となっているユーザーが使用しているデバイスは、コンプライアンスについて評価されます。

## <a name="next-steps"></a>次のステップ

- [Intune で MTD を有効にする](mtd-connector-enable.md)