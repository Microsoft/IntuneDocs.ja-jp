---
title: "Intune で Mobile Threat Defense コネクタを有効にする"
titlesuffix: Azure portal
description: "Intune で Mobile Threat Defense コネクタを有効にします。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d818581ca74e64bf27c968b39969afd889b6fbda
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2017
---
# <a name="enable-mobile-threat-defense-in-intune"></a>Intune で Mobile Threat Defense を有効にする

> [!NOTE] 
> このトピックは、すべての Mobile Threat Defense パートナーに適用されます。

Intune で Mobile Threat Defense (MTD) 接続を有効にするには、MTD パートナー コンソールで Intune コネクタが構成済みである必要があります。

## <a name="to-enable-the-mtd-connector"></a>MTD コネクタを有効にするには

1. [Azure Portal](https://portal.azure.com) に移動し、Intune 資格情報でサインインします。 正常にサインインすると、**Azure ダッシュボード**が開きます。

2. **Azure ダッシュボード**で、左側のメニューから **[その他のサービス]** を選択し、テキスト ボックス フィルターに「**Intune**」と入力します。

3. **[Intune]** を選択すると、**Intune ダッシュボード**が開きます。

4. **Intune ダッシュ ボード**で、**[デバイスのポリシー準拠]** を選択し、**[セットアップ]** セクションで **[Mobile Threat Defense]** を選択します。

5. **[Mobile Threat Defense]** ブレードで、**[追加]** を選択します。

6. **[セットアップする Mobile Threat Defense コネクタ]** として、ドロップダウン リストから MTD ソリューションを選択します。

    ![Intune Azure Portal での MTD のセットアップ](./media/enable-mtd-connector-1.png)

7. 組織の要件に応じてトグルのオプションを有効にします。

## <a name="mtd-toggle-options"></a>MTD トグル オプション

組織の要件に従って、有効にすべき MTD トグル オプションを決定できます。 詳細を以下に示します。

- **[Connect Android 4.1+ devices to [MTD partner name] for Work MTD]\(Android 4.1+ デバイスを [MTD パートナー名] for Work MTD に接続する\)**: このオプションを有効にすると、Android 4.1+ デバイスはセキュリティ上のリスクを Intune に報告します。
    - **[データが受信されない場合、非準拠としてマークする]**: Intune がこのプラットフォーム上のデバイスに関するデータを MTD パートナーから受信しない場合は、そのデバイスを非準拠とみなします。
<br></br>
- **[Connect iOS 8.0+ devices to [MTD partner name] for Work MTD]\(iOS 8.0+ デバイスを [MTD パートナー名] for Work MTD に接続する\)**: このオプションを有効にすると、Android 4.1+ デバイスはセキュリティ上のリスクを Intune に報告します。
    - **[データが受信されない場合、非準拠としてマークする]**: Intune がこのプラットフォーム上のデバイスに関するデータを MTD パートナーから受信しない場合は、そのデバイスを非準拠とみなします。
<br></br>
- **[サポートされていない OS バージョンをブロックする]**: デバイスがサポートされる最低バージョン以前のオペレーティング システムを実行している場合は、ブロックします。

- **[パートナーが無応答になるまでの日数]**: 接続が失われたためにパートナーが応答していないと Intune が判断するまでの、非アクティブ状態の日数。 Intune は、応答しない MTD パートナーのコンプライアンス対応状態を無視します。

> [!IMPORTANT] 
> MTD アプリは、デバイス コンプライアンスと条件付きアクセス ポリシー ルールを作成する前に、追加して割り当てる必要があります。 これにより、MTD アプリはエンド ユーザーがインストールできる状態になり、アプリをインストールするとエンド ユーザーは電子メールや他の会社のリソースにアクセスできます。

> [!TIP]
> [Mobile Threat Defense] ブレードで、**[接続の状態]** や、Intune と MTD パートナー間の **[最終同期]** 時刻を確認できます。
