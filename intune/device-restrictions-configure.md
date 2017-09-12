---
title: "Intune デバイス制限設定の構成"
titleSuffix: Azure portal
description: "Intune を使用して、管理対象デバイスの設定と機能を構成する方法について説明します。\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fc818d1fa1d72165a8d456718d506c7e18c944ba
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-configure-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune でデバイスの制限設定を構成する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

デバイスの制限では、セキュリティ、ブラウザー、ハードウェア、データ共有設定を含む広範なカテゴリにわたって、管理対象のさまざまな設定と機能を制御できます。 たとえば、iOS デバイスのユーザーがデバイスのカメラにアクセスできないようにするデバイスの制限プロファイルを作成できます。

このトピックでは、デバイスの制限プロファイルを構成する基本的な方法について説明します。その後、デバイスごとの詳細については、各プラットフォームのトピックを参照してください。

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>デバイスの制限設定を含むデバイス プロファイルの作成

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの構成]** を選択します。
2. **[デバイス構成]** ブレードで、**[管理]** > **[プロファイル]** の順に選択します。
3. [プロファイル] ブレードで、**[プロファイルを作成します]** を選択します。
4. **[プロファイルを作成します]** ブレードで、デバイスの制限プロファイルの**名前**と**説明**を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、カスタム設定を適用するデバイス プラットフォームを選択します。 現時点では、デバイスの制限設定に対応している次のいずれかのプラットフォームを選択できます。
    - **Android**
    - **iOS**
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
    - [Android for Work の設定](device-restrictions-android-for-work.md)
8. 完了したら、**[プロファイルを作成します]** ブレードに戻り、**[作成]** をクリックします。

プロファイルが作成され、プロファイルの一覧ブレードに表示されます。
このプロファイルをグループに割り当てる場合は、[デバイス プロファイルを割り当てる方法](device-profile-assign.md)に関する記事を参照してください。

## <a name="example-of-device-restriction-settings"></a>デバイスの制限設定の例

この概要レベルの例では、Android デバイスに組み込まれているカメラ アプリの使用をブロックするデバイスの制限ポリシーを作成します。

![Android デバイスのカメラを無効にする方法](./media/disable-android-camera.png)

