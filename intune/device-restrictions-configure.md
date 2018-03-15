---
title: "Microsoft Intune デバイス制限設定の構成"
titleSuffix: 
description: "Microsoft Intune を使用して、管理対象デバイスの設定と機能を構成する方法について説明します。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c5ccb928b8ff3f9cebbd6f51d99cddd1f36fb074
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-configure-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune でデバイスの制限設定を構成する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

デバイスの制限では、次のような広範なカテゴリにわたって、管理対象のさまざまな設定と機能を制御できます。
- セキュリティ
- ブラウザー
- ハードウェア
- データ共有の設定

たとえば、iOS デバイスのユーザーがデバイスのカメラにアクセスできないようにするデバイスの制限プロファイルを作成できます。

デバイス制限プロファイルの基礎を学習します。その後、デバイスの詳細について、各プラットフォームの記事を参照してください。

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>デバイスの制限設定を含むデバイス プロファイルの作成

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ページで、**[デバイス構成]** を選択します。
2. **[デバイス構成]** ページの **[管理]** セクションで、**[プロファイル]** を選択します。
3. **[プロファイル]** ページで、**[プロファイルの作成]** を選択します。
4. **[プロファイルの作成]** ページで、デバイスの制限プロファイルの **[名前]** と **[説明]** を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、カスタム設定を適用するデバイス プラットフォームを選択します。 現時点では、デバイスの制限設定に対応している次のいずれかのプラットフォームを選択できます。
    - **Android**
    - **Android**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 以降**
    - **Windows 10 以降**
6. **[プロファイルの種類]** ドロップダウン リストで、**[デバイスの制限]** を選択します。 Surface Hub などの Windows 10 Team デバイス用のデバイスの制限プロファイルを作成する場合は、**[デバイスの制限 (Windows 10 Team)]** を選択します。
7. 選択したプラットフォームによって構成できる設定が異なります。 各プラットフォームの詳細な設定については、次のいずれかのトピックを参照してください。
    - [Android の設定](device-restrictions-android.md)
    - [iOS の設定](device-restrictions-ios.md)
    - [macOS の設定](device-restrictions-macos.md)
    - [Windows Phone 8.1 の設定](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Windows 10 の設定](device-restrictions-windows-10.md)
    - [Windows 10 Team の設定](device-restrictions-windows-10-teams.md)
    - [Windows Holographic for Business の設定](device-restrictions-windows-holographic.md)
    - [Android for Work の設定](device-restrictions-android-for-work.md)
8. 完了したら、**[プロファイルの作成]** ページに戻り、**[作成]** をクリックします。

プロファイルが作成され、プロファイルの一覧ページに表示されます。
このプロファイルをグループに割り当てる場合は、[デバイス プロファイルを割り当てる方法](device-profile-assign.md)に関する記事を参照してください。

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
