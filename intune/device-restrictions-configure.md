---
title: Microsoft Intune - Azure でデバイスの制限設定を構成する | Microsoft Docs
description: デバイス プロファイルを追加して、Microsoft Intune で Android、macOS、iOS、Windows Phone、Windows 10 の各デバイスの機能を制限します
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9b84877d37d26dababda2987801fc7267cb3c2e6
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181209"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune でデバイスの制限設定を構成する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

デバイスの制限では、次のような広範なカテゴリにわたって、管理対象のさまざまな設定と機能を制御できます。
- セキュリティ
- ブラウザー
- ハードウェア
- データ共有の設定

たとえば、iOS デバイスのユーザーがデバイスのカメラにアクセスできないようにするデバイスの制限プロファイルを作成できます。

デバイス制限プロファイルの基礎を学習します。その後、デバイスの詳細について、各プラットフォームの記事を参照してください。

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>デバイスの制限設定を含むデバイス プロファイルの作成

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
4. デバイス制限プロファイルの **[名前]** と **[説明]** を入力します。
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
    - [Android 仕事用プロファイルの設定](device-restrictions-android-for-work.md)
8. 完了したら、**[プロファイルの作成]** ページに戻り、**[作成]** をクリックします。

プロファイルが作成され、プロファイルの一覧ページに表示されます。
このプロファイルをグループに割り当てる場合は、[デバイス プロファイルを割り当てる方法](device-profile-assign.md)に関する記事を参照してください。

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
