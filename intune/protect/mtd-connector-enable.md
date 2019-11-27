---
title: Microsoft Intune で Mobile Threat Defense コネクタを有効にする
titleSuffix: Microsoft Intune
description: Mobile Threat Defense (MTD) パートナーと Microsoft Intune の間のコネクタを有効にします。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 38ddec9d76a51ca0afe7561c3616e3a97050ba02
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199221"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Intune で Mobile Threat Defense コネクタを有効にする

> [!NOTE] 
> このトピックは、すべての Mobile Threat Defense パートナーに適用されます。

Mobile Threat Defense (MTD) のセットアップ中、MTD パートナー コンソールで脅威を分類するためのポリシーを構成し、Intune でデバイスのコンプライアンス ポリシーを作成しました。 MTD パートナー コンソールで Intune コネクタを既に構成している場合、MTD パートナー アプリケーションに対して MTD 接続を有効にすることができます。

新しいアプリケーションを Intune Mobile Threat Defense に統合し、Intune への接続を有効にすると、Intune によって Azure Active Directory 内に従来の条件付きアクセス ポリシーが作成されます。 統合する各 MTD アプリ ([Defender ATP](advanced-threat-protection.md) や追加の [MTD パートナー](mobile-threat-defense.md#mobile-threat-defense-partners)など) によって、新しい従来の条件付きアクセス ポリシーが作成されます。 これらのポリシーは無視してもかまいませんが、編集、削除、または無効にすることはできません。

従来のポリシーを削除した場合は、その作成に使用された Intune への接続を削除してから、それを再設定する必要があります。 このプロセスにより、従来のポリシーが再作成されます。 MTD アプリ用の従来のポリシーを、条件付きアクセス用の新しいポリシーの種類に移行することは、サポートされていません。

MTD アプリ用の従来の条件付きアクセス ポリシーは: 

- デバイスが Azure AD に登録され、MTD パートナーと通信する前にデバイス ID を持っていることを要求するために、Intune MTD によって使用されます。 ID は、デバイスが Intune に正常に自身の状態を報告できるようにするために必要です。  
- 他のクラウド アプリやリソースには影響しません。  
- MTD の管理を支援するために作成する条件付きアクセス ポリシーとは異なります。
- 既定では、評価に使用する他の条件付きアクセス ポリシーとは対話しません。  

従来の条件付きアクセス ポリシーを表示するには、[Azure](https://portal.azure.com/#home) で **[Azure Active Directory]**  >  **[条件付きアクセス]**  >  **[クラシック ポリシー]** の順に移動します。


## <a name="to-enable-the-mobile-threat-defense-connector"></a>Mobile Threat Defense コネクタを有効にするには

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。

4. **Intune ダッシュ ボード**で、 **[デバイスのポリシー準拠]** を選択し、 **[セットアップ]** セクションで **[Mobile Threat Defense]** を選択します。

5. **[Mobile Threat Defense]** ウィンドウで、 **[追加]** を選択します。

6. **[セットアップする Mobile Threat Defense コネクタ]** として、ドロップダウン リストから MTD ソリューションを選択します。

    ![Intune Azure Portal での MTD のセットアップ](./media/mtd-connector-enable/enable-mtd-connector-1.png)

7. 組織の要件に応じてトグルのオプションを有効にします。 表示される切り替えオプションは、MTD パートナーによって異なります。

## <a name="mobile-threat-defense-toggle-options"></a>Mobile Threat Defense 切り替えオプション

どの Mobile Threat Defense 切り替えオプションを有効にする必要があるのかを、ご自身の組織の要件に応じて決定することができます。 詳細を次に示します。

**MDM コンプライアンス ポリシー設定**
- **[Android 4.1 以上のデバイスを \<_MTD パートナー名_> に接続する]** : このオプションを有効にすると、Android 4.1+ デバイスはセキュリティ上のリスクを Intune に報告します。
- **[iOS 8.0 以上のデバイスを \<_MTD パートナー名_> に接続する]** : このオプションを有効にすると、iOS 8.0 以降のデバイスはセキュリティ上のリスクを Intune に報告します。
- **[iOS デバイスのアプリの同期を有効にする]** :この Mobile Threat Defense パートナーに、Intune から iOS アプリケーションのメタデータを脅威分析用に要求することを許可します。
- **[サポートされていない OS バージョンをブロックする]** :デバイスがサポートされる最低バージョン以前のオペレーティング システムを実行している場合は、ブロックします。

**アプリ保護ポリシー設定**
- **[バージョン 4.1 以上の Android デバイスを *\<MTD パートナー名>* に接続し、アプリ保護ポリシーを評価する]** :このオプションを有効にすると、デバイスの脅威レベルの規則を使用したアプリ保護ポリシーによって、このコネクタのデータを含むデバイスが評価されます。
- **[バージョン 8.0 以上の iOS デバイスを *\<MTD パートナー名>* に接続し、アプリ保護ポリシーを評価する]** :このオプションを有効にすると、デバイスの脅威レベルの規則を使用したアプリ保護ポリシーによって、このコネクタのデータを含むデバイスが評価されます。

Intune アプリ保護ポリシーを評価するために Mobile Threat Defense コネクタを使用する方法について詳しくは、[登録されていないデバイスに対する Mobile Threat Defense の設定](~/protect/mtd-enable-unenrolled-devices.md)に関するページをご覧ください。

**共通の共有設定**
- **[パートナーが無応答になるまでの日数]** :接続が失われたためにパートナーが応答していないと Intune が判断するまでの、非アクティブ状態の日数。 Intune は、応答しない MTD パートナーのコンプライアンス対応状態を無視します。

> [!IMPORTANT] 
> 可能な場合には、デバイス コンプライアンスと条件付きアクセス ポリシー ルールを作成する前に、MTD アプリを追加して割り当てることをお勧めします。 これにより、MTD アプリはエンド ユーザーがインストールできる状態になり、アプリをインストールするとエンド ユーザーは電子メールや他の会社のリソースにアクセスできます。

> [!TIP]
> [Mobile Threat Defense] ウィンドウで、 **[接続の状態]** や、Intune と MTD パートナー間の **[最終同期]** 時刻を確認できます。
