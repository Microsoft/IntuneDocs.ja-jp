---
title: "Windows 8.1 以降の Wi-Fi 設定のインポート"
titleSuffix: Microsoft Intune
description: "Wi-Fi 設定を Windows から Intune Wi-Fi プロファイルにインポートする方法。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 890a10ecf4212656c189adaf46bb2839898758c1
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>Microsoft Intune で Windows 8.1 以降のデバイス向け Wi-Fi 設定をインポートする

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Windows 8.1、Windows 10 デスクトップまたはモバイル、または Windows Holographic for Business を実行するデバイスの場合は、以前エクスポートされた Wi-Fi 構成プロファイルをファイルにインポートすることができます。

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Windows デバイスからの Wi-Fi 設定のエクスポート

Windows で、**netsh wlan** ユーティリティを使用して、既存の Wi-Fi プロファイルを Intune で読み取れる XML ファイルにエクスポートします。 必要な Wi-Fi プロファイルが既にインストールされている Windows コンピューターでは、次の手順に従います。
1. エクスポートされた Wi-Fi プロファイル用のローカル フォルダー (**c:\WiFi** など) を作成します。
1. コマンド プロンプトを管理者として開きます。
1. **netsh wlan show profiles** コマンドを実行し、エクスポートするプロファイルの名前をメモします。 この例では、プロファイル名は **WiFiName** です。
1. **netsh wlan export profile name="ProfileName" folder=c:\Wifi** コマンドを実行します。これにより、**Wi-Fi-WiFiName.xml** という名前の Wi-Fi プロファイル ファイルがターゲット フォルダーに作成されます。

## <a name="import-the-wi-fi-settings-into-intune"></a>Intune への Wi-Fi 設定のインポート

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[デバイス構成]** を選択します。
4. **[デバイス構成]** ウィンドウの **[管理]** セクションで、**[プロファイル]** を選択します。
5. [プロファイル] ウィンドウで、**[プロファイルの作成]** をクリックします。
6. **[プロファイルの作成]** ウィンドウで、デバイスの制限プロファイルの **[名前]** と **[説明]** を入力します。


   > [!WARNING]
   > 名前は、Wi-Fi プロファイルの xml の名前属性と同じにする**必要があります**。異なると失敗します。

7. **[プラットフォーム]** ドロップダウン リストで、**[Windows 8.1 以降]** を選択します。
8. **[プロファイルの種類]** ドロップダウン リストで、**[Wi-Fi インポート]** を選択します。
9. **[Wi-Fi]** ウィンドウで、以下の設定を構成します。
    - **[接続名]**: Wi-Fi 接続の名前を入力します。 この名前は、使用可能な Wi-Fi ネットワークを参照しているエンド ユーザーに表示されます。
    - **[プロファイル XML]**: 参照ボタンをクリックして、Intune にインポートする Wi-Fi プロファイル設定を含む XML ファイルを選択します。
    - **[ファイルの内容]**: 選択した構成プロファイルの XML コードが表示されます。
10. 完了したら、**[OK]** を選択し、**[プロファイルの作成]** ウィンドウに戻り、**[作成]** を選択します。

プロファイルが作成され、プロファイルの一覧ウィンドウに表示されます。
