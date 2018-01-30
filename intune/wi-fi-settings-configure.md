---
title: "Intune Wi-Fi 設定を構成する方法"
titleSuffix: Azure portal
description: "Intune を使用して、管理対象デバイスの Wi-Fi 接続を構成する方法について説明します。\""
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1fadb488-9c6c-43c1-ba23-8c69db633b96
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 161b0de7d697a4ed2d8f80dffdef71296eb6ced2
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>Microsoft Intune で Wi-Fi の設定を構成する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune の Wi-Fi プロファイルを使用して、ワイヤレス ネットワーク設定を組織のユーザーとデバイスに割り当てます。 Wi-Fi プロファイルを割り当てた場合、ユーザーはプロファイルを構成することなく、会社の Wi-Fi ネットワークにアクセスできます。

たとえば、Contoso Wi-Fi という名前の新しい Wi-Fi ネットワークをインストールし、すべての iOS デバイスがこのネットワークに接続するように設定するとします。 その手順は次のとおりです。

1. Contoso Wi-Fi ワイヤレス ネットワークへの接続に必要な設定が含まれている Wi-Fi プロファイルを作成します。
2. iOS デバイスのすべてのユーザーを含むグループにそのプロファイルを割り当てます。
3. ユーザーは、自分のデバイスでワイヤレス ネットワークの一覧にある新しい Contoso Wi-Fi ネットワークを見つけ、このネットワークに簡単に接続できるようになります。

Wi-Fi プロファイルでは次のデバイス プラットフォームをサポートしています。

- Android 4 以降
- Android for Work
- iOS 8.0 以降
- macOS (Mac OS X 10.9 以降)

Windows 8.1、Windows 10、および Windows 10 Mobile を実行しているデバイスの場合は、以前に別のデバイスからエクスポートした Wi-Fi 構成をインポートできます。

このトピックでは、Wi-Fi プロファイルを構成する基本的な方法について説明します。その後、デバイスごとの詳細については、各プラットフォームのトピックを参照してください。

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>Wi-Fi 設定を含むデバイス プロファイルの作成

1. Azure Portal にサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス構成]** を選択します。
2. **[デバイス構成]** ブレードで、**[管理]** > **[プロファイル]** の順に選択します。
3. [プロファイル] ブレードで、**[プロファイルを作成します]** を選択します。
4. **[プロファイルを作成します]** ブレードで、Wi-Fi プロファイルの**名前**と**説明**を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、Wi-Fi 設定を適用するデバイス プラットフォームを選択します。 現時点では、Wi-Fi 設定に対応している次のいずれかのプラットフォームを選択できます。
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows 8.1 以降 (プロファイルのインポート)**
6. **[プロファイルの種類]** ドロップダウン リストで、**[Wi-Fi Basic]** または **[Wi-Fi Enterprise]** を選択します。 **[Wi-Fi Basic]** を使用し、ネットワーク名や SSID などの基本的な機能を指定できます。 **[Wi-Fi Enterprise]** を使用すると、詳細情報 (たとえば、Wi-Fi ネットワークで拡張認証プロトコル (EAP) を使用している場合は EPA) を指定できます。 **[Wi-Fi インポート]** (Windows 8.1 および Windows 10) を使用すると、以前に別のデバイスからエクスポートした Wi-Fi 設定を XML ファイルとしてインポートすることができます。
7. 選択したプラットフォームによって構成できる設定が異なります。 各プラットフォームの詳細な設定については、次のいずれかのトピックを参照してください。
    - [Android と Android for Work の設定](wi-fi-settings-android.md)
    - [iOS の設定](wi-fi-settings-ios.md)
    - [macOS の設定](wi-fi-settings-macos.md)
    - [Windows Phone 8.1 の設定](wi-fi-settings-import-windows-8-1.md)
8. 完了したら、**[プロファイルを作成します]** ブレードに戻り、**[作成]** をクリックします。

プロファイルが作成され、プロファイルの一覧ブレードに表示されます。
このプロファイルをグループに割り当てる場合は、[デバイス プロファイルを割り当てる方法](device-profile-assign.md)に関する記事を参照してください。
