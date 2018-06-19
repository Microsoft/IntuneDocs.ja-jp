---
title: Windows 8.1 以降の Wi-Fi 設定のインポート
titleSuffix: Microsoft Intune
description: Wi-Fi 設定を Windows から Intune Wi-Fi プロファイルにインポートする方法。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 157416738e4607d5022f1c3c7ed8251a8e32fe3e
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31834018"
---
# <a name="import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>Microsoft Intune で Windows 8.1 以降のデバイス向け Wi-Fi 設定をインポートする

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows 8.1、Windows 10 デスクトップまたはモバイル、または Windows Holographic for Business を実行するデバイスの場合は、以前エクスポートされた Wi-Fi 構成プロファイルをファイルにインポートすることができます。

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Windows デバイスからの Wi-Fi 設定のエクスポート

Windows で、**netsh wlan** ユーティリティを使用して、既存の Wi-Fi プロファイルを Intune で読み取れる XML ファイルにエクスポートします。 プロファイルを正常に使用するには、キーをプレーン テキストでエクスポートする必要があります。

必要な Wi-Fi プロファイルが既にインストールされている Windows コンピューターでは、次の手順のようにします。

1. エクスポートされた Wi-Fi プロファイル用のローカル フォルダー (**c:\WiFi** など) を作成します。
2. コマンド プロンプトを管理者として開きます。
3. `netsh wlan show profiles` コマンドを実行し、エクスポートするプロファイルの名前をメモします。 この例では、プロファイル名は **WiFiName** です。
4. `netsh wlan export profile name="ProfileName" folder=c:\Wifi` コマンドを実行します。これにより、**Wi-Fi-WiFiName.xml** という名前の Wi-Fi プロファイル ファイルがターゲット フォルダーに作成されます。

## <a name="import-the-wi-fi-settings-into-intune"></a>Intune への Wi-Fi 設定のインポート

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
4. デバイス制限プロファイルの **[名前]** と **[説明]** を入力します。

    > [!IMPORTANT]
    > - 名前は、Wi-Fi プロファイルの xml の名前属性と同じにする**必要があります**。 異なると失敗します。
    > - 事前共有キーが含まれている Wi-Fi プロファイルをエクスポートする場合は、`key=clear` をコマンドに追加する**必要があります**。 たとえば、「`netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`」と入力します。
    > - Windows 10 で事前共有キーを使用すると、Intune に修復エラーが表示されます。 この場合は、Wi-Fi プロファイルがデバイスに正常に割り当てられ、プロファイルは想定どおりに動作します。
    > - 事前共有キーが含まれている Wi-Fi プロファイルをエクスポートする場合は、ファイルが保護されていることを確認します。 キーはプレーン テキスト形式であるため、ユーザーはキーを保護する必要があります。

5. **[プラットフォーム]** で、**[Windows 8.1 以降]** を選択します。
6. **[プロファイルの種類]** で、**[Wi-Fi インポート]** を選択します。
7. 次の設定を構成します。
  - **[接続名]**: Wi-Fi 接続の名前を入力します。 この名前は、使用可能な Wi-Fi ネットワークを参照しているエンド ユーザーに表示されます。
  - **[プロファイル XML]**: 参照ボタンを選択して、Intune にインポートする Wi-Fi プロファイル設定を含む XML ファイルを選びます。
  - **[ファイルの内容]**: 選択した構成プロファイルの XML コードが表示されます。
8. 完了したら **[OK]** を選択し、**[作成]** を選択してプロファイルを作成します。

プロファイルが作成され、プロファイルの一覧に表示されます。
