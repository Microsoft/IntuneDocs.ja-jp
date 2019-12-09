---
title: Microsoft Intune で MTD デバイスのコンプライアンス ポリシーを作成する
titleSuffix: Microsoft Intune
description: モバイル デバイスが会社のリソースにアクセスできるかどうかを決定するために、MTD パートナー脅威レベルを使用する Intune デバイスのコンプライアンス ポリシーを作成します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 504c77fb56918cf97312e70f50b38356f9f7efef
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409698"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Intune で Mobile Threat Defense (MTD) デバイス コンプライアンス ポリシーを作成する

Intune で MTD を使用すると、モバイル デバイス上で脅威を検出し、リスクを評価できます。 リスクを評価する Intune デバイス コンプライアンス ポリシー ルールを作成すれば、デバイスがポリシーに準拠しているかどうかを判断できます。 さらに、[条件付きアクセス ポリシー](create-conditional-access-intune.md)を使用することで、デバイスのコンプライアンスに基づいて、サービスへのアクセスを禁止できます。

> [!NOTE]
> この情報は、すべての Mobile Threat Defense パートナーに適用されます。

## <a name="before-you-begin"></a>始める前に

MTD の設定の一部として、MTD パートナー コンソールで、さまざまな脅威を高、中、低として分類するポリシーを作成しておきます。 これにより、Intune デバイス コンプライアンス ポリシーに Mobile Threat Defense レベルを設定する必要があります。

MTD でのデバイス コンプライアンス ポリシーの前提条件:

- MTD と Intune の統合をセットアップする

## <a name="to-create-an-mtd-device-compliance-policy"></a>MTD デバイス コンプライアンス ポリシーを作成するには

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[デバイス]** 、 **[コンプライアンス ポリシー]** 、 **[ポリシーの作成]** の順に選択します。

3. デバイス コンプライアンス ポリシーの **[名前]** 、 **[説明]** を入力し、 **[プラットフォーム]** を選択してから **[設定]** セクションの **[構成]** を選択します。

4. **[コンプライアンス ポリシー]** ウィンドウで、 **[デバイスのヘルス]** を選択します。

5. **[デバイスのヘルス]** ウィンドウで、 **[デバイスは、デバイス脅威レベル以下であることが必要]** のドロップダウン リストからモバイル脅威レベルを選択します。

   - **[セキュリティ保護]** :このレベルはセキュリティ上最も安全です。 デバイスにいかなる脅威も存在できず、デバイスからは引き続き会社のリソースにアクセスできます。 いずれかの脅威が見つかった場合、デバイスは非準拠と評価されます。

   - **[低]** :存在する脅威が低レベルの場合のみ、デバイスは準拠しています。 低レベルより高い脅威が存在する場合、デバイスは非準拠状態になります。

   - **[中]** :デバイスに存在する脅威が低レベルまたは中レベルの場合、デバイスは準拠しています。 高レベルの脅威が検出された場合は、デバイスは非準拠と判定されます。

   - **[高]** :このレベルは最も安全性の低い状態です。 この場合、すべての脅威レベルが許可され、レポート目的のみで Mobile Threat Defense が使用されます。 デバイスには、この設定でアクティブ化された MTD アプリが含まれている必要があります。

6. **[OK]** を 2 回選択し、 **[作成]** を選択するとポリシーが作成されます。

> [!IMPORTANT]
> Office 365 またはその他のサービスに対する条件付きアクセス ポリシーを作成すると、デバイス コンプライアンス評価が適用され、非準拠デバイスはデバイスで脅威が解決されるまで会社のリソースへのアクセスは禁止されます。

## <a name="to-assign-an-mtd-device-compliance-policy"></a>MTD デバイス コンプライアンス ポリシーを割り当てるには

デバイス コンプライアンス ポリシーをユーザーに割り当てるには:

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[デバイス]** 、 **[コンプライアンス ポリシー]** の順に選択します。

3. ユーザーに割り当てるポリシーを選択し、 **[割り当て]** を選択します。 使用可能なオプションを使用し、このポリシーを受け取るグループを*含める*か、*除外*します。  

4. [保存] を選択して割り当てを完了します。 割り当てを保存すると、ポリシーが選択したユーザーに展開され、デバイスのコンプライアンスが評価されます。

## <a name="next-steps"></a>次の手順

[Intune で MTD を有効にする](mtd-connector-enable.md)
