---
title: "Intune カスタム デバイス設定を構成する方法"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Intune を使用して、管理対象デバイスのカスタム設定を構成する方法について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: ca4f1adc5704ecd66d2af7823f95ca63ec20469e
ms.openlocfilehash: 029b5c4c011ddf3ff7dbb06c55b48ef0c18c725e
ms.lasthandoff: 03/17/2017


---

# <a name="how-to-configure-custom-device-settings-in-microsoft-intune"></a>Microsoft Intune でカスタム デバイス設定を構成する方法

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="when-to-use-custom-settings"></a>カスタム設定を使用する状況

カスタム デバイス設定は、構成する設定が Intune に組み込まれていない場合に便利で、他のデバイス プロファイルから利用できます。
カスタム設定は、プラットフォームごとに構成が異なります。 たとえば、Android および Windows デバイスでは、デバイスの機能を制御する Open Mobile Alliance Uniform Resource Identifier (OMA-URI) 値を指定できます。 Apple デバイスでは、[Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) で作成したファイルをインポートできます。

このトピックでは、カスタム設定を含むプロファイルを構成する基本的な方法について説明します。その後、デバイスごとの詳細については、各プラットフォームのトピックを参照してください。

## <a name="create-a-device-profile-containing-custom-settings"></a>カスタム設定を含むデバイス プロファイルの作成

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[その他]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス構成]** を選択します。
2. **[デバイス構成]** ブレードで、**[管理]** > **[プロファイル]** の順に選択します。
3. [プロファイル] ブレードで、**[プロファイルを作成します]** を選択します。
4. **[プロファイルを作成します]** ブレードで、カスタム プロファイルの**名前**と**説明**を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、カスタム設定を適用するデバイス プラットフォームを選択します。 現時点では、カスタム デバイス設定に対応している次のいずれかのプラットフォームを選択できます。
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 10 以降**
6. **[プロファイルの種類]** ドロップダウン リストで、**[カスタム]** を選択します。
7. 選択したプラットフォームによって構成できる設定が異なります。 各プラットフォームの詳細な設定については、次のいずれかのトピックを参照してください。
    - [Android の設定](custom-for-android.md)
    - [iOS の設定](custom-for-ios.md)
    - [macOS の設定](custom-for-macos.md)
    - [Windows Phone 8.1 の設定](custom-for-windows-phone-8-1.md)
    - [Windows 10 の設定](custom-for-windows-10.md)
8. 完了したら、**[プロファイルを作成します]** ブレードに戻り、**[作成]** をクリックします。

プロファイルが作成され、プロファイルの一覧ブレードに表示されます。
このプロファイルをグループに割り当てる場合は、[デバイス プロファイルを割り当てる方法](how-to-assign-device-profiles.md)に関する記事を参照してください。


