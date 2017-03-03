---
title: "Intune デバイス構成プロファイルを作成する | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Intune デバイス構成プロファイルを作成する方法について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 908169c47d9eaa583c775c8ed06acea233040e50
ms.lasthandoff: 02/16/2017


---

# <a name="how-to-create-device-configuration-profiles-in-microsoft-intune"></a>Microsoft Intune でデバイス構成プロファイルを作成する方法

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの構成]** を選択します。
2. **[デバイス構成]** ブレードで、**[管理]** > **[プロファイル]** の順に選択します。
2. プロファイルの一覧が表示されているブレードで、**[プロファイルを作成します]** を選択します。
3. **[プロファイルを作成します]** ブレードで、次を指定します。
    - **[名前]** - 新しいプロファイルのわかりやすい名前を入力します。
    - **[説明]** - プロファイルの説明を入力します (省略可能)。
    - **[プラットフォーム]** - 作成するプロファイルのプラットフォームの種類を選択します。
    - **[プロファイルの種類]** - 作成するプロファイルの種類を選択します。 選択可能な種類の一覧は、選択したプラットフォームによって異なります。
    - **[設定]** - プロファイルの種類ごとの設定に関する情報については、次のトピックを参照してください。
        -  [デバイスの制限設定](/intune-azure/configure-devices/how-to-configure-device-restrictions)
        -  [電子メールの設定](/intune-azure/configure-devices/how-to-configure-email-settings)
        -  [VPN 設定](/intune-azure/configure-devices/how-to-configure-vpn-settings)
        -  [Wi-Fi 設定](/intune-azure/configure-devices/how-to-configure-wi-fi-settings)
        -  [Windows 10 エディションのアップグレード設定](/intune-azure/configure-devices/how-to-configure-windows-10-edition-upgrade)
        -  [証明書の設定](/intune-azure/configure-devices/how-to-configure-certificates)
        -  [Windows 情報保護の設定](/intune-azure/configure-devices/how-to-configure-windows-information-protection)
        -  [教育設定](/intune-azure/configure-devices/education-settings-for-ios.md)
        -  [カスタム設定](/intune-azure/configure-devices/how-to-configure-custom-settings)

    ![デバイス プロファイルの作成](./media/create-device-profile.png)
4. 設定の構成が完了したら、**[プロファイルを作成します]** ブレードで、**[作成]** を選択します。

プロファイルが作成され、プロファイルの一覧ブレードに表示されます。
このプロファイルをグループに割り当てる場合は、[デバイス プロファイルを割り当てる方法](how-to-assign-device-profiles.md)に関する記事を参照してください。


### <a name="next-steps"></a>次のステップ
デバイス プロファイルを割り当てる方法については、[Microsoft Intune でデバイス プロファイルを割り当てる方法](/intune-azure/configure-devices/how-to-assign-device-profiles)に関する記事を参照してください。

