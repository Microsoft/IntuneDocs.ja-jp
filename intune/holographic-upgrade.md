---
title: "Windows Holographic を Windows Holographic for Business にアップグレードする"
titleSuffix: Microsoft Intune
description: "Windows Holographic を実行するデバイスを Windows Holographic for Business にアップグレードする方法について説明します"
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
ms.openlocfilehash: e7c750b372c297637abcdb9e941dae17714d081b
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Windows Holographic を実行するデバイスを Windows Holographic for Business にアップグレードする


Windows Holographic を実行するデバイスを Microsoft Intune で管理するには、Windows Holographic から Windows Holographic for Business にデバイスをアップグレードする必要があります。 このアップグレードを行うために、エディション アップグレード プロファイルを作成できます。 Microsoft HoloLens の場合、Commercial Suite を購入してアップグレードに必要なライセンスを入手できます。 詳細については、「[Windows Holographic for Business 機能のロック解除](https://docs.microsoft.com/en-us/hololens/hololens-upgrade-enterprise)」を参照してください。

## <a name="to-set-up-an-edition-upgrade-device-configuration-profile"></a>エディションのアップグレード デバイス構成プロファイルを設定するには

1. 管理者アカウントで [Azure Portal](https://portal.azure.com) にサインインします。


2.  **[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順にクリックします。

    ![プロファイルの作成](media/Holographic-create-profile.png)

3.  **[プロファイルの作成]** ページで、プロファイルの名前を入力し、プラットフォームとして **[Windows 10 以降]** を選び、プロファイルの種類として **[エディションのアップグレード]** を選びます。 **[設定] > [構成]** をクリックします。

5. **[エディションのアップグレード]** ページの **[アップグレードのターゲット エディション]** で、**[Windows 10 Holographic for Business]** を選びます。 **[ライセンス ファイル]** で、提供された XML ライセンス ファイルを参照して選びます。

    ![XML ファイルの名前を入力する](media/Holographic-edition-upgrade.png)
 
5.  **[OK]** をクリックし、**[作成]** をクリックしてプロファイルを作成します。


## <a name="deploy-the-edition-upgrade-policy"></a>エディションのアップグレード ポリシーを展開する

次に、エディションのアップグレード プロファイルを選んだグループまたはデバイスに割り当てます。

1. 前のステップで作成したプロファイルで、**[割り当て]** をクリックします。

2. **[割り当て]** ページのユーザー グループとデバイスで、ポリシーに含めるものとポリシーから除外するものを選びます。

![含めるグループと除外するグループ](media/Holographic-groups.PNG)

これらのユーザーまたはデバイスが Intune に登録されるとき、エディションのアップグレード プロファイルが適用されます。 

## <a name="next-steps"></a>次の手順

グループについては、「[グループの概要](get-started-groups.md)」を参照してください。


