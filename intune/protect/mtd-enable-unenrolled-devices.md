---
title: 未登録デバイスに対して Mobile Threat Defense コネクタを有効にする
titleSuffix: Microsoft Intune
description: 未登録デバイスに対して Microsoft Intune で Mobile Threat Defense コネクタを有効にする
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
ms.openlocfilehash: 63079757ee3610d825601921da1d33aa94f851b6
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794408"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>未登録デバイスに対して Intune で Mobile Threat Defense コネクタを有効にする

Mobile Threat Defense (MTD) のセットアップ中、Mobile Threat Defense パートナー コンソールで脅威を分類するためのポリシーを構成し、Intune でアプリ保護ポリシーを作成しました。 MTD パートナー コンソールで Intune コネクタを既に構成している場合、MTD パートナー アプリケーションに対して MTD 接続を有効にすることができます。

> [!NOTE] 
> この記事は、アプリ保護ポリシーをサポートするすべての Mobile Threat Defense パートナーに適用されます。Better Mobile (Android)、Zimperium (iOS)、Lookout for Work (Android/iOS) です。

## <a name="to-enable-the-mtd-connector"></a>MTD コネクタを有効にするには

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。

2. **Intune ダッシュ ボード**で、 **[デバイスのポリシー準拠]** を選択し、 **[セットアップ]** セクションで **[Mobile Threat Defense]** を選択します。

3. **[Mobile Threat Defense]** ウィンドウで、 **[追加]** を選択します。

4. **[セットアップする Mobile Threat Defense コネクタ]** として、ドロップダウン リストから MTD ソリューションを選択します。

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. 組織の要件に応じてトグルのオプションを有効にします。 表示される切り替えオプションは、MTD パートナーによって異なります。

## <a name="mtd-toggle-options"></a>MTD トグル オプション

組織の要件に基づき、有効にする MTD 切り替えオプションを決定できます。 詳細を次に示します。

**アプリ保護ポリシー設定**
- **バージョン 4.1 以上の Android デバイスを *\<MTD パートナー名>* に接続し、アプリ保護ポリシーを評価する**:このオプションを有効にすると、デバイスの脅威レベルの規則を使用したアプリ保護ポリシーによって、このコネクタのデータを含むデバイスが評価されます。
- **バージョン 8.0 以上の iOS デバイスを *\<MTD パートナー名>* に接続し、アプリ保護ポリシーを評価する**:このオプションを有効にすると、デバイスの脅威レベルの規則を使用したアプリ保護ポリシーによって、このコネクタのデータを含むデバイスが評価されます。

**共通の共有設定**
- **[パートナーが無応答になるまでの日数]** :接続が失われたためにパートナーが応答していないと Intune が判断するまでの、非アクティブ状態の日数。 Intune は、応答しない MTD パートナーのコンプライアンス対応状態を無視します。

> [!TIP]
> [Mobile Threat Defense] ウィンドウで、 **[接続の状態]** や、Intune と MTD パートナー間の **[最終同期]** 時刻を確認できます。

> [!NOTE] 
> Mobile Threat Defense と Intune の接続を有効にすると、Intune によって Azure Active Directory 内に従来の条件付きアクセス ポリシーが作成されます。 統合する各 MTD アプリ ([Defender ATP](advanced-threat-protection.md) や追加の [MTD パートナー](mobile-threat-defense.md#mobile-threat-defense-partners)など) によって、新しい従来の条件付きアクセス ポリシーが作成されます。 **これらのポリシーは無視してもかまいませんが、編集、削除、または無効にすることはできません。**
> 
> MTD アプリ用の従来の条件付きアクセス ポリシーは: 
> - デバイスが Azure AD に登録され、MTD パートナーと通信する前にデバイス ID を持っていることを要求するために、Intune MTD によって使用されます。 ID は、デバイスが Intune に正常に自身の状態を報告できるようにするために必要です。  
> - 他のクラウド アプリやリソースには影響しません。  
> - MTD の管理を支援するために作成する条件付きアクセス ポリシーとは異なります、あるいは Require App Protection CA のため
> - 既定では、評価に使用する他の条件付きアクセス ポリシーとは対話しません。  
>
> 従来の条件付きアクセス ポリシーを表示するには、[Azure](https://portal.azure.com/#home) で **[Azure Active Directory]**  >  **[条件付きアクセス]**  >  **[クラシック ポリシー]** の順に移動します。

## <a name="next-steps"></a>次の手順

- [Intune で Mobile Threat Defense (MTD) アプリ保護ポリシーを作成します](~/protect/mtd-app-protection-policy.md)。