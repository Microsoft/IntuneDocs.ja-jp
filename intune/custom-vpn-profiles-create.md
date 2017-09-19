---
title: "Microsoft Intune でカスタム VPN プロファイルを作成する方法"
titleSuffix: Azure portal
description: "Intune でカスタム構成を使用して VPN プロファイルを作成します。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7a3ab162ee950527c8d78123b4fd0a44c8bd7f29
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>Microsoft Intune でカスタム VPN プロファイルを作成する方法

## <a name="create-a-custom-configuration"></a>カスタム構成を作成する
Intune のカスタム構成ポリシーを使用して、以下の VPN プロファイルを作成できます。

* Android 4 以降が実行されているデバイス
* Windows 8.1 以降を実行する登録済みのデバイス
* Windows Phone 8.1 以降が実行されているデバイス
* Windows 10 デスクトップを実行する登録済みのデバイス 
* Windows 10 Mobile を実行するデバイス

この種のポリシーは、標準的な Intune VPN ポリシーに、使用する設定が含まれていない場合に役立ちます。

## <a name="to-create-a-custom-configuration-policy"></a>カスタム構成ポリシーを作成するには:

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス構成]** を選択します。
4. **[デバイス構成]** ブレードで、**[管理]** > **[プロファイル]** の順に選択します。
5. [プロファイル] ブレードで、**[プロファイルを作成します]** を選択します。
6. **[プロファイルを作成します]** ブレードで、VPN プロファイルの**名前**と**説明**を入力します。
7. **[プラットフォーム]** ドロップダウン リストで、VPN 設定を適用するデバイス プラットフォームを選択します。 現時点では、カスタム デバイス設定に対応している次のいずれかのプラットフォームを選択できます。
    - **Android**
    - **iOS** (Apple Configurator からエクスポートしたファイルを使用して構成済み)。
    - **macOS** (Apple Configurator からエクスポートしたファイルを使用して構成済み)。
    - **Windows Phone 8.1**
    - **Windows 10 以降**
6. **[プロファイルの種類]** ドロップダウン リストで、**[カスタム]** を選択します。
7. **[OMA-URI のカスタム設定]** ブレードで、指定する URI 設定ごとに **[追加]** を選択し、必要な情報を入力して、**[OK]** を選択します。 次に例を示します。

   ![VPN プロファイルのカスタム構成ダイアログ ボックス](./media/Intune_Add_VPN_URI.png)

4.  必要な URI 設定をすべて入力したら **[OK]** を選択し、**[プロファイルを作成します]** ブレードで **[作成]** を選択します。

プロファイルが作成され、プロファイルの一覧ブレードに表示されます。
このプロファイルをグループに割り当てる場合は、[デバイス プロファイルを割り当てる方法](device-profile-assign.md)に関する記事を参照してください。




