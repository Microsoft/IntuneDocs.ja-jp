---
title: Intune で Mobile Threat Defense (MTD) アプリ保護ポリシーを作成する
titleSuffix: Microsoft Intune
description: Microsoft Intune で Mobile Threat Defense (MTD) アプリ保護ポリシーを作成する
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 15d986bc5017a44571c6194f9c6b53167b671349
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794421"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Intune で Mobile Threat Defense アプリ保護ポリシーを作成する

> [!NOTE] 
> この記事は、アプリ保護ポリシーをサポートするすべての Mobile Threat Defense (MTD) パートナーに適用されます。Better Mobile (Android)、Zimperium (iOS)、Lookout for Work (Android/iOS) です。

Intune で MTD を使用すると、モバイル デバイス上で脅威を検出し、リスクを評価できます。 リスクを評価し、デバイスが企業データへのアクセスを許可されているかどうかを判断する Intune アプリ保護ポリシーを作成できます。 

## <a name="before-you-begin"></a>始める前に

MTD の設定の一部として、MTD パートナー コンソールで、さまざまな脅威を高、中、低として分類するポリシーを作成しておきます。 これにより、Intune アプリ保護ポリシーに Mobile Threat Defense レベルを設定する必要があります。

MTD のアプリ保護ポリシーの前提条件:

- MTD と Intune の統合をセットアップします。 この統合がなければ、MTD アプリ保護ポリシーには効力がありません。

## <a name="to-create-an-mtd-app-protection-policy"></a>MTD アプリ保護ポリシーを作成するには

1. [Azure Portal](https://portal.azure.com/) に移動し、Intune 資格情報でサインインします。

2. **Azure ダッシュボード**で、左側のメニューから **[すべてのサービス]** を選択し、テキスト ボックス フィルターに「**Intune**」と入力します。

3. **[Intune]** を選択すると、**Intune ダッシュボード**が開きます。

4. **Intune ダッシュボード**で、 **[クライアント アプリ]** を選択し、 **[管理]** セクションの下で **[アプリ保護ポリシー]** を選択します。

5. **[ポリシーの作成]** を選択し、 **[名前]** と **[説明]** を入力し、 **[プラットフォーム]** を選択します。 

6. **[条件付き起動]** ウィンドウの **[デバイスの条件]** テーブルの下で、 **[Max allowed device threat level]\(許容される最大デバイス脅威レベル\)** の下にあるドロップダウン リストからモバイル脅威レベルを選択します。

    」を参照します。  **[セキュリティ保護]** :このレベルはセキュリティ上最も安全です。 デバイスにいかなる脅威も存在できず、デバイスからは引き続き会社のリソースにアクセスできます。 いずれかの脅威が見つかった場合、デバイスは非準拠と評価されます。

    b.  **[低]** :存在する脅威が低レベルの場合のみ、デバイスは準拠しています。 低レベルより高い脅威が存在する場合、デバイスは非準拠状態になります。

    c.  **[中]** :デバイスに存在する脅威が低レベルまたは中レベルの場合、デバイスは準拠しています。 高レベルの脅威が検出された場合は、デバイスは非準拠と判定されます。

    d.  **[高]** :このレベルは最も安全性の低い状態です。 この場合、すべての脅威レベルが許可され、レポート目的のみで Mobile Threat Defense が使用されます。 デバイスには、この設定でアクティブ化された MTD アプリが含まれている必要があります。

7. **[保存]** を 2 回クリックしてから、 **[作成]** を選択します。

## <a name="to-assign-an-mtd-app-protection-policy"></a>MTD アプリ保護ポリシーを割り当てるには

デバイス コンプライアンス ポリシーをユーザーに割り当てるには、前に構成したポリシーを選択します。 既存のポリシーは、 **[デバイスのポリシー準拠 - ポリシー]** ウィンドウで確認できます。

1. ユーザーに割り当てるポリシーを選択し、 **[割り当て]** を選択します。 この操作でウィンドウが表示され、 **[Azure Active Directory セキュリティ グループ]** を選択してポリシーに割り当てることができます。

2. **[Select groups to include]\(含めるグループの選択\)** を選択すると、Azure AD セキュリティ グループが表示されたウィンドウが開きます。 **[選択]** を選択すると、ポリシーがユーザーに展開されます。

> [!NOTE] 
> ポリシーがユーザーに適用されました。 Intune アプリ保護の対象アプリで企業データにアクセスすることについて、ポリシーの対象となるユーザーによって使用されているデバイスが評価されます。

## <a name="next-steps"></a>次の手順  

- Microsoft Intune の [Mobile Threat Defense](~/protect/mobile-threat-defense.md) について学習します。
