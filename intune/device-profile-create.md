---
title: Microsoft Intune - Azure でのデバイス プロファイルの作成 | Microsoft Docs
description: Microsoft Intune でデバイス プロファイルを追加または構成する場合、プラットフォームの種類の選択および Azure Portal 内での設定の構成も行います。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cb6e3f0a9f62348d55b5dc2284c1007ea7faf088
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203214"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Microsoft Intune でのデバイス プロファイルの作成

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>プロファイルの作成

1. [Azure portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**[Intune]** を選択します。

2. **[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択します。

3. 次のプロパティを入力します。

   - **[名前]**:新しいプロファイルのわかりやすい名前を入力します。
   - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
   - **[プラットフォーム]**:プラットフォームの種類を選択します。  

       - **Android**
       - **Android エンタープライズ**
       - **Android**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 以降**
       - **Windows 10 以降**

   - **[プロファイルの種類]**:作成する種類を選択します。 リストは、選択したプラットフォームによって異なります。
   - **設定**:次の記事では、ファイルの種類ごとの設定について説明します。

       -  [デバイスの機能](device-features-configure.md)
       -  [デバイスの制限](device-restrictions-configure.md)
       -  [Endpoint Protection](endpoint-protection-configure.md)
       -  [ID 保護](identity-protection-configure.md)  
       -  [キオスク](kiosk-settings.md)
       -  [電子メール](email-settings-configure.md)
       -  [VPN](vpn-settings-configure.md)
       -  [Wi-Fi](wi-fi-settings-configure.md)
       -  [Windows 10](education-settings-configure.md) と [iOS](wi-fi-settings-ios.md) 向けの教育
       -  [Windows 10 エディションのアップグレード](edition-upgrade-configure-windows-10.md)
       -  [iOS 更新ポリシー](software-updates-ios.md)
       -  [証明書](certificates-configure.md)
       -  [Windows 情報保護](windows-information-protection-configure.md)
       -  [カスタム](custom-settings-configure.md)

     ![[プロファイルの作成] のスクリーンショット](./media/create-device-profile.png)

4. 完了したら、**[作成]** を選択します。

プロファイルが作成され、リストに表示されます。

## <a name="next-steps"></a>次の手順
[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
