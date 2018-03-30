---
title: Microsoft Intune - Azure でのデバイス プロファイルの作成 | Microsoft Docs
description: Microsoft Intune でデバイス プロファイルを追加または構成する場合、プラットフォームの種類の選択および Azure Portal 内での設定の構成も行います。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e5070052c0d4cce3cfd81a7bae259bc7dfb22e7f
ms.sourcegitcommit: e6319ff186d969da34bd19c9730ba003d6cce353
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2018
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Microsoft Intune でのデバイス プロファイルの作成

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>プロファイルの作成
1. [Azure Portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Microsoft Intune** を検索します。

2. **Microsoft Intune** で、**[デバイス構成]** を選択し、**[プロファイル]** を選択します。 次に、**[プロファイルの作成]** を選択します。

3. 次のプロパティを入力します。

    - **名前**: 新しいプロファイルのわかりやすい名前を入力します。
    - **説明**: プロファイルの説明を入力します  (これは省略可能ですが、入力することをお勧めします)。
    - **[プラットフォーム]**: プラットフォームの種類を選択します。  

        - **Android**
        - **Android for Work**
        - **iOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 以降**
        - **Windows 10 以降**

    - **[プロファイルの種類]**: 作成する種類を選択します。 リストは、選択したプラットフォームによって異なります。
    - **[設定]**: プロファイルの種類ごとの設定に関する説明については、次のトピックを参照してください。

        -  [デバイス機能設定](device-features-configure.md)
        -  [デバイスの制限設定](device-restrictions-configure.md)
        -  [電子メールの設定](email-settings-configure.md)
        -  [VPN 設定](vpn-settings-configure.md)
        -  [Wi-Fi 設定](wi-fi-settings-configure.md)
        -  [Windows 10 エディションのアップグレード設定](edition-upgrade-configure-windows-10.md)
        -  [証明書の設定](certificates-configure.md)
        -  [Windows 情報保護の設定](windows-information-protection-configure.md)
        -  [教育設定](education-settings-configure.md)
        -  [カスタム設定](custom-settings-configure.md)

    ![[プロファイルの作成] のスクリーンショット](./media/create-device-profile.png)

4. 完了したら、**[作成]** を選択します。

プロファイルが作成され、リストに表示されます。


## <a name="next-steps"></a>次の手順
デバイス プロファイルを割り当てるには、[Microsoft Intune でデバイス プロファイルを割り当てる方法](device-profile-assign.md)に関するページを参照してください。
