---
title: "Microsoft Intune でカスタム VPN プロファイルを作成する方法"
titleSuffix: 
description: "Intune でカスタム構成を使用して VPN プロファイルを作成します。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ec9b959d086051985287a62f7d10fe8d4cbad7e9
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>Microsoft Intune でカスタム VPN プロファイルを作成する方法

Intune のカスタム構成ポリシーを使用して、次のプラットフォームの VPN プロファイルを作成できます。

* Android 4 以降
* Windows 8.1 以降を実行する登録済みのデバイス
* Windows Phone 8.1 以降
* Windows 10 デスクトップを実行する登録済みのデバイス 
* Windows 10 Mobile

この種のポリシーは、使用する設定が標準的な Intune VPN ポリシーに含まれていない場合に役立ちます。

## <a name="to-create-a-custom-configuration-policy"></a>カスタム構成ポリシーを作成するには:

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]**、**[Intune]** の順に選択します。 Intune は、**[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[デバイス構成]** を選択します。
2. **[デバイス構成]** ウィンドウの **[管理]** セクションで、**[プロファイル]** を選択します。
5. [プロファイル] ウィンドウで **[プロファイルの作成]** を選択します。
6. **[プロファイルを作成します]** ウィンドウで、VPN プロファイルの**名前**と**説明**を入力します。
7. **[プラットフォーム]** ドロップダウン リストで、VPN 設定を適用するデバイス プラットフォームを選択します。 現時点では、カスタム デバイス設定に対応している次のいずれかのプラットフォームを選択できます。
    - **Android**
    - **Android for Work**
    - **iOS** (Apple Configurator からエクスポートしたファイルを使用して構成済み)。
    - **macOS** (Apple Configurator からエクスポートしたファイルを使用して構成済み)。
    - **Windows Phone 8.1**
    - **Windows 8.1 以降**
    - **Windows 10 以降**
6. **[プロファイルの種類]** ドロップダウン リストで、**[カスタム]** を選択します。
7. **[OMA-URI のカスタム設定]** ウィンドウで、指定する URI 設定ごとに **[追加]** を選択し、必要な情報を入力して、**[OK]** を選択します。 次に例を示します。

   ![VPN プロファイルのカスタム構成ダイアログ ボックス](./media/Intune_Add_VPN_URI.png)

4.  必要な URI 設定をすべて入力したら **[OK]** を選択し、**[プロファイルを作成します]** ウィンドウで **[作成]** を選択します。

プロファイルが作成され、プロファイルの一覧ウィンドウに表示されます。
このプロファイルをグループに割り当てる場合は、[デバイス プロファイルを割り当てる方法](device-profile-assign.md)に関する記事を参照してください。




