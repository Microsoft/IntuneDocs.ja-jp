---
title: Microsoft Intune - Azure でデバイスの制限設定を構成する | Microsoft Docs
description: デバイス プロファイルを追加して、Microsoft Intune で Android、macOS、iOS、Windows Phone、Windows 10 の各デバイスの機能を制限します
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e040743975a482c702e0c0168a4fd6315a2dac8
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61505745"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune でデバイスの制限設定を構成する

デバイスの制限では、次のような広範なカテゴリにわたって、管理対象のさまざまな設定と機能を制御できます。
- セキュリティ
- ブラウザー
- ハードウェア
- データ共有の設定

たとえば、iOS デバイスのユーザーがデバイスのカメラにアクセスできないようにするデバイスの制限プロファイルを作成できます。

デバイス制限プロファイルの基礎を学習します。その後、デバイスの詳細について、各プラットフォームの記事を参照してください。

## <a name="create-the-profile"></a>プロファイルの作成

1. [Azure portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**Intune** を選択します。
2. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
3. デバイス制限プロファイルの **[名前]** と **[説明]** を入力します。
4. **[プラットフォーム]** ドロップダウン リストで、カスタム設定を適用するデバイス プラットフォームを選択します。 現時点では、デバイスの制限設定に対応している次のいずれかのプラットフォームを選択できます。

    - **Android**
    - **Android エンタープライズ**
    - **Android**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 以降**
    - **Windows 10 以降**

5. **[プロファイルの種類]** ドロップダウン リストで、**[デバイスの制限]** を選択します。 Surface Hub などの Windows 10 Team デバイス用のデバイスの制限プロファイルを作成するには、**[デバイスの制限 (Windows 10 Team)]** を選択します。
6. 選択したプラットフォームによって構成できる設定が異なります。 詳細な設定については、お使いのプラットフォームを選択してください。

    - [Android の設定](device-restrictions-android.md)
    - [Android エンタープライズの設定](device-restrictions-android-for-work.md)
    - [iOS の設定](device-restrictions-ios.md)
    - [macOS の設定](device-restrictions-macos.md)
    - [Windows Phone 8.1 の設定](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Windows 10 の設定](device-restrictions-windows-10.md)
    - [Windows 10 Team の設定](device-restrictions-windows-10-teams.md)
    - [Windows Holographic for Business の設定](device-restrictions-windows-holographic.md)

7. 完了したら、**[OK]** > **[作成]** を選択して変更を保存します。

プロファイルが作成され、プロファイル一覧に表示されます。

## <a name="next-steps"></a>次の手順

プロファイルが作成されると、割り当てることができます。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
