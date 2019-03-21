---
title: Microsoft Intune で Windows デバイス向けの Wi-Fi 設定をインポートする - Azure | Microsoft Docs
description: netsh wlan を使用して、Windows デバイスから Wi-Fi 設定を XML ファイル形式でエクスポートします。 次に、Intune でこのファイルをインポートして、Windows 8.1、Windows 10、Windows Holographic for Business を実行するデバイス用の Wi-Fi プロファイルを作成します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/18/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3452eb832f31377ddc9c55c5008405cb2235569b
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57564841"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Intune で Windows デバイス用の Wi-Fi 設定をインポートする

Windows を実行するデバイスの場合は、以前エクスポートされた Wi-Fi 構成プロファイルをファイルにインポートすることができます。 **Windows 10 以降のデバイスでは、Intune で直接 [Wi-Fi プロファイルを作成する](wi-fi-settings-windows.md)こともできます**。

適用先:  
- Windows 8.1 以降
- Windows 10 以降
- Windows 10 デスクトップまたは Windows 10 Mobile
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Windows デバイスからの Wi-Fi 設定のエクスポート

Windows で、`netsh wlan` を使用して、既存の Wi-Fi プロファイルを Intune で読み取れる XML ファイルにエクスポートします。 プロファイルを正常に使用するには、キーをプレーン テキストでエクスポートする必要があります。

必要な Wi-Fi プロファイルが既にインストールされている Windows コンピューターでは、次の手順のようにします。

1. エクスポートされた Wi-Fi プロファイル用のローカル フォルダー (**c:\WiFi** など) を作成します。
2. コマンド プロンプトを管理者として開きます。
3. `netsh wlan show profiles` コマンドを実行し、エクスポートするプロファイルの名前をメモします。 この例では、プロファイル名は **WiFiName** です。
4. `netsh wlan export profile name="ProfileName" folder=c:\Wifi` コマンドを実行します。 このコマンドにより、**Wi-Fi-WiFiName.xml** という名前の Wi-Fi プロファイル ファイルがターゲット フォルダーに作成されます。

## <a name="import-the-wi-fi-settings-into-intune"></a>Intune への Wi-Fi 設定のインポート

1. **Azure Portal** で、[[すべてのサービス]](https://portal.azure.com) を選択し、**[Intune]** をフィルターとして適用して、**[Microsoft Intune]** を選びます。
2. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
3. デバイス制限プロファイルの **[名前]** と **[説明]** を入力します。

    > [!IMPORTANT]
    > - 名前は、Wi-Fi プロファイルの xml の名前属性と同じにする**必要があります**。 異なると失敗します。
    > - 事前共有キーが含まれている Wi-Fi プロファイルをエクスポートする場合は、`key=clear` をコマンドに追加する**必要があります**。 たとえば、「`netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`」と入力します。
    > - Windows 10 で事前共有キーを使用すると、Intune に修復エラーが表示されます。 この場合は、Wi-Fi プロファイルがデバイスに正常に割り当てられ、プロファイルは想定どおりに動作します。
    > - 事前共有キーが含まれている Wi-Fi プロファイルをエクスポートする場合は、ファイルが保護されていることを確認します。 キーはプレーン テキスト形式であるため、ユーザーはキーを保護する必要があります。

4. **[プラットフォーム]** で、**[Windows 8.1 以降]** を選択します。
5. **[プロファイルの種類]** で、**[Wi-Fi インポート]** を選択します。
6. 次の設定を構成します。
    - **[接続名]**: Wi-Fi 接続の名前を入力します。 この名前は、使用可能な Wi-Fi ネットワークを参照しているエンド ユーザーに表示されます。
    - **[プロファイル XML]**: 参照ボタンを選択し、インポートする Wi-Fi プロファイル設定を含む XML ファイルを選択します。
    - **[ファイルの内容]**: 選択した構成プロファイルの XML コードが表示されます。
7. 完了したら、**[OK]** > **[作成]** を選択して変更を保存します。 プロファイルが作成され、プロファイル一覧に表示されます。

## <a name="next-steps"></a>次の手順

プロファイルは作成されますが、何も実行されません。 次に、[このプロファイルを割り当て](device-profile-assign.md)ます。

## <a name="more-resources"></a>その他のリソース

使用可能な他のプラットフォームなど、[Wi-Fi 設定の概要](wi-fi-settings-configure.md)に関する記事。
