---
title: "Windows 8.1 以降の Wi-Fi 設定のインポート | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Windows から Intune Wi-Fi プロファイルに Wi-Fi 設定をインポートする方法。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c4e9b19-b268-4f6d-9663-7cdbe4e4a8dd
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 938129f210d1a4a6b4719deb63d1dc47dad21b29
ms.openlocfilehash: 132ce1c8e6ad69c5d8998f233c114f912cb4bf8b


---

# <a name="how-to-import-wi-fi-settings-for-windows-81-and-later-devices-in-intune-azure-preview"></a>Intune Azure プレビューで Windows 8.1 以降のデバイス向け Wi-Fi 設定をインポートする方法 | Microsoft Docs

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Windows 8.1 または Windows 10 デスクトップまたはモバイルを実行するデバイスの場合は、以前エクスポートされた Wi-Fi 構成プロファイルをファイルにインポートすることができます。

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Windows デバイスからの Wi-Fi 設定のエクスポート

Windows で、**netsh wlan** ユーティリティを使用して、既存の Wi-Fi プロファイルを Intune で読み取れる XML ファイルにエクスポートします。 必要な Wi-Fi プロファイルが既にインストールされている Windows コンピューターでは、次の手順に従います。
1. エクスポートされた Wi-Fi プロファイル用のローカル フォルダー (**c:\WiFi** など) を作成します。
1. コマンド プロンプトを管理者として開きます。
1. **netsh wlan show profiles** コマンドを実行し、エクスポートするプロファイルの名前をメモします。 この例では、プロファイル名は **WiFiName** です。
1. **netsh wlan export profile name="ProfileName" folder=c:\Wifi** コマンドを実行します。これにより、**Wi-Fi-WiFiName.xml** という名前の Wi-Fi プロファイル ファイルがターゲット フォルダーに作成されます。

## <a name="import-the-wi-fi-settings-into-intune"></a>Intune への Wi-Fi 設定のインポート

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[その他]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの構成]** を選択します。
2. **[デバイス構成]** ブレードで、**[管理]** > **[プロファイル]** の順に選択します。
3. [プロファイル] ブレードで、**[プロファイルを作成します]** をクリックします。
4. **[プロファイルを作成します]** ブレードで、デバイスの制限プロファイルの**名前**と**説明**を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、**[Windows 8.1 以降]** を選択します。
6. **[プロファイルの種類]** ドロップダウン リストで、**[Wi-Fi インポート]** を選択します。
7. **[Wi-fi Basic]** ブレードで、次を構成します。
    - **[接続名]**: Wi-Fi 接続の名前を入力します。 この名前は、使用可能な Wi-Fi ネットワークを参照しているエンド ユーザーに表示されます。
    - **[プロファイル XML]**: 参照ボタンをクリックして、Intune にインポートする Wi-Fi プロファイル設定を含む XML ファイルを選択します。
    - **[ファイルの内容]**: 選択した構成プロファイルの XML コードが表示されます。
8. 完了したら、**[プロファイルを作成します]** ブレードに戻り、**[作成]** をクリックします。

プロファイルが作成され、プロファイルの一覧ブレードに表示されます。



<!--HONumber=Feb17_HO1-->


