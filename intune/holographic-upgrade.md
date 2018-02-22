---
title: "Windows Holographic を Windows Holographic for Business にアップグレードする"
titleSuffix: Azure portal
description: "Windows Holographic を実行するデバイスを Windows Holographic for Business にアップグレードする方法について説明します"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/30/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c467d2d4e02785bfac48afe2b39c50300eb4be40
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Windows Holographic を実行するデバイスを Windows Holographic for Business にアップグレードする


Windows Holographic を実行するデバイスを Microsoft Intune で管理するには、エディションのアップグレード プロファイルを作成して、Windows Holographic から Windows Holographic for Business にデバイスをアップグレードする必要があります。 Microsoft HoloLens の場合、Commercial Suite を購入してアップグレードに必要なライセンスを入手できます。 詳細については、「[Windows Holographic for Business 機能のロック解除](https://docs.microsoft.com/en-us/hololens/hololens-upgrade-enterprise)」を参照してください。

## <a name="to-set-up-an-edition-upgrade-device-configuration-profile"></a>エディションのアップグレード デバイス構成プロファイルを設定するには

1. 管理者アカウントで [Azure Portal](https://portal.azure.com) にサインインします。


2.  **[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順にクリックします。

    ![プロファイルの作成](media/Holographic-create-profile.png)

3.  **[プロファイルの作成]** ブレードで、プロファイルの名前を入力し、プラットフォームとして **[Windows 10 以降]** を選び、プロファイルの種類として **[エディションのアップグレード]** を選びます。 **[設定] > [構成]** をクリックします。

5. **[エディションのアップグレード]** ブレードの **[アップグレードのターゲット エディション]** で、**[Windows 10 Holographic for Business]** を選びます。 **[ライセンス ファイル]** で、提供された XML ライセンス ファイルを参照して選びます。

    ![XML ファイルの名前を入力する](media/Holographic-edition-upgrade.png)
 
5.  **[OK]** をクリックし、**[作成]** をクリックしてプロファイルを作成します。


## <a name="deploy-the-edition-upgrade-policy"></a>エディションのアップグレード ポリシーを展開する

次に、エディションのアップグレード プロファイルを選んだグループまたはデバイスに割り当てます。

1. 前のステップで作成したプロファイルで、**[割り当て]** をクリックします。

2. **[割り当て]** ブレードのユーザー グループとデバイスで、ポリシーに含めるものとポリシーから除外するものを選びます。

![含めるグループと除外するグループ](media/Holographic-groups.PNG)

これらのユーザーまたはデバイスが Intune に登録されるとき、エディションのアップグレード プロファイルが適用されます。 

## <a name="next-steps"></a>次の手順

グループについては、「[グループの概要](get-started-groups.md)」を参照してください。


