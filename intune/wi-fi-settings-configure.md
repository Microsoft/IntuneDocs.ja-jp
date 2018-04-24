---
title: Intune Wi-Fi 設定を構成する方法
titleSuffix: Microsoft Intune
description: Microsoft Intune を使用して、管理対象デバイスの Wi-Fi 接続を構成する方法について説明します。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9a550e2963fa60a91db3ef63f7771bc4ca352d98
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>Microsoft Intune で Wi-Fi の設定を構成する方法

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune の Wi-Fi プロファイルを使用して、ワイヤレス ネットワーク設定を組織のユーザーとデバイスに割り当てます。 Wi-Fi プロファイルを割り当てた場合、ユーザーはプロファイルを構成することなく、会社の Wi-Fi ネットワークにアクセスできます。

たとえば、Contoso Wi-Fi という名前の新しい Wi-Fi ネットワークをインストールし、すべての iOS デバイスがこのネットワークに接続するように設定するとします。 その手順は次のとおりです。

1. Contoso Wi-Fi ワイヤレス ネットワークへの接続に必要な設定が含まれている Wi-Fi プロファイルを作成します。
2. iOS デバイスのすべてのユーザーを含むグループにそのプロファイルを割り当てます。
3. ユーザーは、自分のデバイスでワイヤレス ネットワークの一覧にある新しい Contoso Wi-Fi ネットワークを見つけ、このネットワークに簡単に接続できるようになります。

## <a name="supported-device-platforms"></a>サポートされるデバイス プラットフォーム

Wi-Fi プロファイルでは次のデバイス プラットフォームをサポートしています。

- Android 4 以降
- Android for Work
- iOS 8.0 以降
- macOS (Mac OS X 10.9 以降)

Windows 8.1、Windows 10、Windows 10 Mobile、Windows Holographic for Business を実行しているデバイスの場合は、以前に別のデバイスからエクスポートした Wi-Fi 構成をインポートできます。

このトピックでは、Wi-Fi プロファイルを構成する基本的な方法について説明します。その後、デバイスごとの詳細については、各プラットフォームのトピックを参照してください。

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>Wi-Fi 設定を含むデバイス プロファイルの作成

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]**、**[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[デバイス構成]** を選択します。
2. **[デバイス構成]** ウィンドウの **[管理]** セクションで、**[プロファイル]** を選択します。
3. [プロファイル] ウィンドウで **[プロファイルの作成]** を選択します。
4. **[プロファイルの作成]** ウィンドウで、Wi-Fi プロファイルの **[名前]** と **[説明]** を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、Wi-Fi 設定を適用するデバイス プラットフォームを選択します。 現時点では、Wi-Fi 設定に対応している次のいずれかのプラットフォームを選択できます。
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 以降**
    - **Windows 10 以降**

   > [!IMPORTANT]
   > Windows 10 を実行するデバイス用のプロファイルを作成する場合は (Windows Holographic for Business など)、**Windows 8.1 以降の**プラットフォームを選ぶ必要があります。 **Windows 10 以降**のプラットフォームには、Wi-Fi プロファイルの種類は含まれません。 

6. Apple デバイスまたは Android デバイスの場合、**[WiFi の種類]** ドロップダウン リストで、**[Basic]** または **[Enterprise]** を選びます。 **[Basic]** を使うと、ネットワーク名や SSID などの基本的な機能を指定できます。 **[Enterprise]** を使用すると、詳細情報 (たとえば、Wi-Fi ネットワークで拡張認証プロトコル (EAP) を使用している場合は EPA) を指定できます。 

   **[Wi-Fi インポート]** プロファイル (Windows 8.1 以降の場合) を使うと、以前に別のデバイスからエクスポートした Wi-Fi 設定を XML ファイルとしてインポートすることができます。
1. 選択したプラットフォームによって構成できる設定が異なります。 各プラットフォームの詳細な設定については、次のいずれかのトピックを参照してください。
    - [Android と Android for Work の設定](wi-fi-settings-android.md)
    - [iOS の設定](wi-fi-settings-ios.md)
    - [macOS の設定](wi-fi-settings-macos.md)
    - [Windows 8.1 以降の設定](wi-fi-settings-import-windows-8-1.md) (Windows Holographic for Business を含む)
1. 完了したら、**[プロファイルの作成]** ウィンドウに戻り、**[作成]** をクリックします。

プロファイルが作成され、プロファイルの一覧ウィンドウに表示されます。

## <a name="next-steps"></a>次の手順

このプロファイルをグループに割り当てる場合は、[デバイス プロファイルを割り当てる方法](device-profile-assign.md)に関する記事を参照してください。
