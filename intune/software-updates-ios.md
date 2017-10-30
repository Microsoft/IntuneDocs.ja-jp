---
title: "iOS 更新ポリシーの構成"
titlesuffix: Azure portal
description: "監視対象の iOS デバイスに利用可能な最新のソフトウェア更新プログラムを強制的に自動インストールするために、更新ポリシーを構成します。"
keywords: 
author: dougeby
manager: dougeby
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6334421-85e1-4457-9c44-e5db8d4ee00e
ms.openlocfilehash: 199760a60ee2290560ebdf933192de0eaf569e9e
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2017
---
# <a name="configure-ios-update-policies"></a>iOS 更新ポリシーの構成
iOS を対象にした更新ポリシーにより、監視対象の iOS デバイスに利用可能な最新のソフトウェア更新プログラムを強制的に自動インストールします。 デバイスに更新プログラムをインストールできないようにする日や時間を構成することもできます。

## <a name="configure-the-ios-update-policy"></a>iOS 更新ポリシーの構成
1. コピー先 Azure Portal の [Intune] ブレードに移動します。
2. **[Intune]** ブレードで、**[ソフトウェア更新プログラム]** > **[iOS 更新ポリシー]** を選択します。
4. ポリシーのブレードで **[作成]** を選択し、ポリシーの名前と説明を入力します。
5. **[設定]** > **[構成]** を選択し、iOS デバイスに最新の更新プログラムを強制的にインストールしないときの詳細を入力します。
6. **[OK]** を選択して、この構成を保存します。 これにより、**[更新ポリシーを作成する]** ブレードに戻ります。 **[作成]** を選択してポリシーを作成し、設定を保存します。

プロファイルが作成され、iOS 更新ポリシーの一覧ブレードに表示されます。

## <a name="assign-an-ios-update-policy-to-users"></a>iOS 更新ポリシーをユーザーに割り当てる
iOS 更新ポリシーをユーザーに割り当てるには、構成したポリシーを選択します。 既存のポリシーは、**[ソフトウェア更新プログラム]** > **[iOS 更新プログラム]** ブレードに表示されます。
1. ユーザーに割り当てるポリシーを選択し、**[割り当て]** を選択します。 Azure Active Directory セキュリティ グループを選んでポリシーに割り当てることができるブレードが開きます。
2. **[グループの選択]** を選択すると、ブレードが開き、Azure AD セキュリティ グループが表示されます。 **[選択]** を選び、ユーザーにポリシーを展開します。

ポリシーがユーザーに適用されました。 ポリシーの対象となっているユーザーが使用しているデバイスは、Update Compliance で評価されます。

## <a name="change-the-restricted-days-for-the-policy"></a>ポリシーを制限する曜日の変更
1. **[ソフトウェア更新プログラム]** ブレードで、**[iOS 更新ポリシー]** を選択します。
2. 更新する iOS 更新ポリシーを選択します。
3. **[プロパティ]** を選択し、制限する曜日の情報を更新します。

## <a name="monitor-ios-devices-with-older-ios-versions"></a>古い iOS バージョンの iOS デバイスを監視する 
<!-- 1352223 -->
**[古い iOS デバイス]** レポートは、**[ソフトウェア更新プログラム]** > **[iOS 更新ポリシー]** ブレードから利用できます。 このレポートには、iOS 更新ポリシーの対象になっていて更新できなかった監視対象の iOS デバイスの一覧が表示されます。 デバイスごとに、デバイスが自動的に更新されない理由のステータスを確認できます。