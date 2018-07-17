---
title: Microsoft Intune でカスタム デバイス設定を使用する - Azure | Microsoft Docs
description: Microsoft Intune を使用し、Windows、Android、iOS デバイスのカスタム設定を使用するプロファイルを追加または作成する
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d917d2449e75b89db00d453b72940a93efb03321
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905004"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Intune でカスタム設定を持つプロファイルを作成する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune には、必要な設定が用意されていない場合があります。 あるいは、他のデバイス プロファイルで利用できる設定が使用できれば便利な場合があります。 そのような設定を追加するには、デバイス プロファイルを作成し、カスタム デバイス設定でそのプロファイルを構成します。

この記事では、カスタム設定でプロファイルを作成する基本的な手順を紹介します。 さまざまなプラットフォームでカスタム設定を作成する方法を詳しく紹介するページのリンクも含まれています。

## <a name="custom-settings-on-different-platforms"></a>さまざまなプラットフォームでのカスタム設定
カスタム設定は、プラットフォームごとに構成が異なります。 たとえば、Android デバイスと Windows デバイスで機能を制御するには、Open Mobile Alliance Uniform Resource Identifier (OMA-URI) 値を入力できます。 Apple デバイスでは、[Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) で作成したファイルをインポートできます。

## <a name="create-the-profile"></a>プロファイルの作成

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択します。
4. カスタム プロファイルの**名前**と**説明**を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、カスタム設定を適用するデバイス プラットフォームを選択します。 次のいずれかのプラットフォームを選択できます。

    - **Android**
    - **Android エンタープライズ**
    - **Android**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 以降**
    - **Windows 10 以降**

6. **[プロファイルの種類]** ドロップダウン リストで、**[カスタム]** を選択します。
7. 選択したプラットフォームによって構成できる設定が異なります。 次のリンクからは、各プラットフォームのカスタム設定に関する詳細を確認できます。

    - [Android の設定](custom-settings-android.md)
    - [iOS の設定](custom-settings-ios.md)
    - [macOS の設定](custom-settings-macos.md)
    - [Windows Phone 8.1 の設定](custom-settings-windows-phone-8-1.md)
    - [Windows 10 の設定](custom-settings-windows-10.md)
    - [Windows Holographic for Business の設定](custom-settings-windows-holographic.md)
    - [Android 仕事用プロファイルの設定](custom-settings-android-for-work.md)

8. 完了したら、**[作成]** を選択します。

プロファイルが作成され、プロファイル一覧に表示されます。 このプロファイルをグループに割り当てるには、[デバイス プロファイルを割り当てる方法](device-profile-assign.md)に関する記事を参照してください。
