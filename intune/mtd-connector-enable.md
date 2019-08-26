---
title: Microsoft Intune で Mobile Threat Defense コネクタを有効にする
titleSuffix: Microsoft Intune
description: Mobile Threat Defense (MTD) パートナーと Microsoft Intune の間のコネクタを有効にします。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7272ddb502075f071b03925c47993c97e447bce
ms.sourcegitcommit: ec22a186a9cfa489a8490698e387624e480892d8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68960677"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Intune で Mobile Threat Defense コネクタを有効にする

> [!NOTE] 
> このトピックは、すべての Mobile Threat Defense パートナーに適用されます。

Mobile Threat Defense (MTD) のセットアップ中、MTD パートナー コンソールで脅威を分類するためのポリシーを構成し、Intune でデバイスのコンプライアンス ポリシーを作成しました。 MTD パートナー コンソールで Intune コネクタを既に構成している場合、MTD パートナー アプリケーションに対して MTD 接続を有効にすることができます。

新しいアプリケーションを Intune Mobile Threat Defense に統合し、Intune への接続を有効にすると、Intune によって Azure Active Directory 内に従来の条件付きアクセス ポリシーが作成されます。 統合する各 MTD アプリ ([Defender ATP](advanced-threat-protection.md) や追加の [MTD パートナー](mobile-threat-defense.md#mobile-threat-defense-partners)など) によって、新しい従来の条件付きアクセス ポリシーが作成されます。 これらのポリシーは無視してもかまいませんが、編集、削除、または無効にすることはできません。

MTD アプリ用の従来の条件付きアクセス ポリシーは: 

- デバイスが Azure AD に登録され、MTD パートナーと通信する前にデバイス ID を持っていることを要求するために、Intune MTD によって使用されます。 ID は、デバイスが Intune に正常に自身の状態を報告できるようにするために必要です。  
- 他のクラウド アプリやリソースには影響しません。  
- MTD の管理を支援するために作成する条件付きアクセス ポリシーとは異なります。
- 既定では、評価に使用する他の条件付きアクセス ポリシーとは対話しません。  

従来の条件付きアクセス ポリシーを表示するには、[Azure](https://portal.azure.com/#home) で **[Azure Active Directory]** > **[条件付きアクセス]** > **[クラシック ポリシー]** の順に移動します。


## <a name="to-enable-the-mtd-connector"></a>MTD コネクタを有効にするには

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。

4. **Intune ダッシュ ボード**で、**[デバイスのポリシー準拠]** を選択し、**[セットアップ]** セクションで **[Mobile Threat Defense]** を選択します。

5. **[Mobile Threat Defense]** ウィンドウで、**[追加]** を選択します。

6. **[セットアップする Mobile Threat Defense コネクタ]** として、ドロップダウン リストから MTD ソリューションを選択します。

    ![Intune Azure Portal での MTD のセットアップ](./media/enable-mtd-connector-1.png)

7. 組織の要件に応じてトグルのオプションを有効にします。 表示される切り替えオプションは、MTD パートナーによって異なります。

## <a name="mtd-toggle-options"></a>MTD トグル オプション

組織の要件に基づき、有効にする MTD 切り替えオプションを決定できます。 詳細を次に示します。

- **[Connect Android 4.1+ devices to [MTD partner name] for Work MTD]\(Android 4.1+ デバイスを [MTD パートナー名] for Work MTD に接続する\)**:このオプションを有効にすると、Android 4.1+ デバイスはセキュリティ上のリスクを Intune に報告します。
  - **[データが受信されない場合、非準拠としてマークする]**:Intune がこのプラットフォーム上のデバイスに関するデータを MTD パートナーから受信しない場合は、そのデバイスを非準拠と見なします。
<br></br>
- **[Connect iOS 8.0+ devices to [MTD partner name] for Work MTD]\(iOS 8.0+ デバイスを [MTD パートナー名] for Work MTD に接続する\)**:このオプションを有効にすると、iOS 8.0 以降のデバイスはセキュリティ上のリスクを Intune に報告します。
  - **[データが受信されない場合、非準拠としてマークする]**:Intune がこのプラットフォーム上のデバイスに関するデータを MTD パートナーから受信しない場合は、そのデバイスを非準拠と見なします。
<br></br>
- **[iOS デバイスのアプリの同期を有効にする]**:この Mobile Threat Defense パートナーに、Intune から iOS アプリケーションのメタデータを脅威分析用に要求することを許可します。

- **[サポートされていない OS バージョンをブロックする]**:デバイスがサポートされる最低バージョン以前のオペレーティング システムを実行している場合は、ブロックします。

- **[パートナーが無応答になるまでの日数]**:接続が失われたためにパートナーが応答していないと Intune が判断するまでの、非アクティブ状態の日数。 Intune は、応答しない MTD パートナーのコンプライアンス対応状態を無視します。

> [!IMPORTANT] 
> 可能な場合には、デバイス コンプライアンスと条件付きアクセス ポリシー ルールを作成する前に、MTD アプリを追加して割り当てることをお勧めします。 これにより、MTD アプリはエンド ユーザーがインストールできる状態になり、アプリをインストールするとエンド ユーザーは電子メールや他の会社のリソースにアクセスできます。

> [!TIP]
> [Mobile Threat Defense] ウィンドウで、**[接続の状態]** や、Intune と MTD パートナー間の **[最終同期]** 時刻を確認できます。
