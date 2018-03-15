---
title: "Windows 8.1 以降の Wi-Fi 設定のインポート"
titleSuffix: Microsoft Intune
description: "Wi-Fi 設定を Windows から Intune Wi-Fi プロファイルにインポートする方法。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0113703cbdc58172edc9552146c7634aa1058e3b
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
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

1. Azure Portal にサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ページで、**[デバイス構成]** を選択します。
2. **[デバイス構成]** ページで、**[管理]** > **[プロファイル]** の順に選択します。
3. [プロファイル] ページで、**[プロファイルの作成]** をクリックします。
4. **[プロファイルの作成]** ページで、デバイスの制限プロファイルの **[名前]** と **[説明]** を入力します。

   > [!WARNING]
   > 名前は、Wi-Fi プロファイルの xml の名前属性と同じにする**必要があります**。異なると失敗します。

5. **[プラットフォーム]** ドロップダウン リストで、**[Windows 8.1 以降]** を選択します。
6. **[プロファイルの種類]** ドロップダウン リストで、**[Wi-Fi インポート]** を選択します。
7. **[Wi-fi Basic]\(Wi-Fi 基本\)** ページで、以下の設定を構成します。
    - **[接続名]**: Wi-Fi 接続の名前を入力します。 この名前は、使用可能な Wi-Fi ネットワークを参照しているエンド ユーザーに表示されます。
    - **[プロファイル XML]**: 参照ボタンをクリックして、Intune にインポートする Wi-Fi プロファイル設定を含む XML ファイルを選択します。
    - **[ファイルの内容]**: 選択した構成プロファイルの XML コードが表示されます。
8. 完了したら、**[プロファイルの作成]** ページに戻り、**[作成]** をクリックします。

プロファイルが作成され、プロファイルの一覧ページに表示されます。
