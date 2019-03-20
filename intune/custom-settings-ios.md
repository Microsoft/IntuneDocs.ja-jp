---
title: Microsoft Intune で iOS デバイスにカスタム設定を追加する - Azure | Microsoft Docs
titleSuffix: ''
description: Apple Configurator または Apple Profile Manager ツールから iOS の設定をエクスポートした後、Microsoft Intune にそれらの設定をインポートします。 これらの設定では、iOS デバイスでのカスタム設定と機能を作成、使用、制御できます。 このカスタム プロファイルを組織内の iOS デバイスに割り当てたり配布したりして、ベースラインまたは基準を作成できます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8e1edae77144b85d100bf590716768792afd8470
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565539"
---
# <a name="use-custom-settings-for-ios-devices-in-microsoft-intune"></a>Microsoft Intune で iOS デバイス用のカスタム設定を使用する

Microsoft Intune では、"カスタム プロファイル" を使用して iOS デバイス用のカスタム設定を追加または作成できます。 カスタム プロファイルは Intune の機能です。 Intune に組み込まれていないデバイスの設定と機能を追加するように設計されています。

iOS デバイスを使用するとき、Intune にカスタム設定を取り込むには 2 つの方法があります。

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

これらのツールを使用して、設定を構成プロファイルにエクスポートすることができます。 Intune では、このファイルをインポートし、iOS のユーザーとデバイスにプロファイルを割り当てます。 割り当てられた設定は配布され、組織内の iOS に対するベースラインまたは基準も作成します。

この記事では、iOS デバイス用のカスタム プロファイルを作成する方法を示します。 また、Apple Configurator と Apple Profile Manager の使用に関するガイダンスも提供します。

## <a name="before-you-begin"></a>始める前に

- **Apple Configurator** を使用して構成プロファイルを作成するときは、エクスポートする設定が、使用しているデバイスの iOS バージョンと互換性があることを確認してください。 互換性のない設定の解決については、[Apple 開発者](https://developer.apple.com/) Web サイトで「**Configuration Profile Reference**」(構成プロファイル リファレンス) および「**Mobile Device Management Protocol Reference**」(モバイル デバイス管理プロトコル リファレンス) を検索してください。

- **Apple Profile Manager** を使用するときは、次のことを確認してください。

  - Profile Manager で[モバイル デバイス管理](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C)を有効にします。
  - Profile Manager で [iOS デバイス](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984)を追加します。
  - Profile Manager でデバイスを追加した後、**[Under the Library]\(ライブラリの下\)** > **[Devices]\(デバイス\)** に移動し、デバイスを選択し、**[Settings]\(設定\)** を選択します。 デバイスの全般設定を入力します。

    このファイルをダウンロードして保存します。 このファイルを Intune プロファイルに入力します。

  - Apple Profile Manager からエクスポートする設定が、使用しているデバイスの iOS のバージョンと互換性があることを確認します。 互換性のない設定の解決については、[Apple 開発者](https://developer.apple.com/) Web サイトで「**Configuration Profile Reference**」(構成プロファイル リファレンス) および「**Mobile Device Management Protocol Reference**」(モバイル デバイス管理プロトコル リファレンス) を検索してください。

## <a name="create-the-profile"></a>プロファイルの作成

1. **Azure Portal** で、[[すべてのサービス]](https://portal.azure.com) を選択し、**[Intune]** をフィルターとして適用して、**[Microsoft Intune]** を選びます。
2. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
3. 次の設定を入力します。

    - **名前**: `ios custom profile` のようにプロファイルの名前を入力します。
    - **説明**: プロファイルの説明を入力します 
    - **[プラットフォーム]**: **[iOS]** を選びます。
    - **プロファイルの種類**: **[カスタム]** を選択します。

4. **[カスタムの構成]** には、次の設定を入力します。

    - **カスタム構成プロファイル名**: ポリシーの名前を入力します。 この名前は、デバイス上と、Intune の状態に表示されます。
    - **構成プロファイル ファイル**: Apple Configurator または Apple Profile Manager を使用して作成した構成プロファイルを指定します。 インポートしたファイルは、**[ファイルの内容]** 領域に表示されます。

5. **[OK]** > **[作成]** を選択して、Intune プロファイルを作成します。 完了すると、プロファイルが **[デバイス構成 - プロファイル]** の一覧に表示されます。

## <a name="next-steps"></a>次の手順

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当てます](device-profile-assign.md)。

[macOS デバイスでプロファイルを作成する](custom-settings-macos.md)方法を確認してください。 
