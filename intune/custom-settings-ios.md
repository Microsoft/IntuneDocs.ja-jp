---
title: Microsoft Intune で iOS デバイスにカスタム設定を追加する - Azure | Microsoft Docs
titleSuffix: ''
description: Apple Configurator または Apple Profile Manager ツールから iOS の設定をエクスポートした後、Microsoft Intune にそれらの設定をインポートします。 これらの設定では、iOS デバイスでのカスタム設定と機能を作成、使用、制御できます。 このカスタム プロファイルを組織内の iOS デバイスに割り当てたり配布したりして、ベースラインまたは基準を作成できます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f75317678034a488e689461982550bbb0a8afad8
ms.sourcegitcommit: 7273100afc51fd808558dc05c651358145d4fa6b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68533159"
---
# <a name="use-custom-settings-for-ios-devices-in-microsoft-intune"></a>Microsoft Intune で iOS デバイス用のカスタム設定を使用する

Microsoft Intune では、"カスタム プロファイル" を使用して iOS デバイス用のカスタム設定を追加または作成できます。 カスタム プロファイルは Intune の機能です。 Intune に組み込まれていないデバイスの設定と機能を追加するように設計されています。

iOS デバイスを使用するとき、Intune にカスタム設定を取り込むには 2 つの方法があります。

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

これらのツールを使用して、設定を構成プロファイルにエクスポートすることができます。 Intune では、このファイルをインポートし、iOS のユーザーとデバイスにプロファイルを割り当てます。 割り当てが完了すると、設定が配布されます。 また、組織内の iOS のベースラインまたは標準も作成します。

この記事では、Apple Configurator と Apple Profile Manager の使用に関するガイダンスを提供し、構成できるプロパティについて説明します。

## <a name="before-you-begin"></a>始める前に

[プロファイルを作成します](device-profile-create.md)。

## <a name="what-you-need-to-know"></a>知っておく必要がある情報

- **Apple Configurator** を使用して構成プロファイルを作成するときは、エクスポートする設定が、デバイスの iOS バージョンと互換性があることを確認してください。 互換性のない設定の解決については、[Apple 開発者](https://developer.apple.com/) Web サイトで「**Configuration Profile Reference**」(構成プロファイル リファレンス) および「**Mobile Device Management Protocol Reference**」(モバイル デバイス管理プロトコル リファレンス) を検索してください。

- **Apple Profile Manager** を使用するときは、次のことを確認してください。

  - Profile Manager で[モバイル デバイス管理](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C)を有効にします。
  - Profile Manager で [iOS デバイス](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984)を追加します。
  - Profile Manager でデバイスを追加した後、 **[Under the Library]\(ライブラリの下\)**  >  **[Devices]\(デバイス\)** に移動し、デバイスを選択し、 **[Settings]\(設定\)** を選択します。 デバイスの全般設定を入力します。

    このファイルをダウンロードして保存します。 このファイルを Intune プロファイルに入力します。

  - Apple Profile Manager からエクスポートする設定が、デバイスの iOS バージョンと互換性があることを確認してください。 互換性のない設定の解決については、[Apple 開発者](https://developer.apple.com/) Web サイトで「**Configuration Profile Reference**」(構成プロファイル リファレンス) および「**Mobile Device Management Protocol Reference**」(モバイル デバイス管理プロトコル リファレンス) を検索してください。

## <a name="custom-configuration-profile-settings"></a>カスタム構成プロファイルの設定

- **カスタム構成プロファイル名**: ポリシーの名前を入力します。 この名前は、デバイス上と、Intune の状態に表示されます。
- **構成プロファイル ファイル**: Apple Configurator または Apple Profile Manager を使用して作成した構成プロファイルを指定します。 インポートしたファイルは、 **[ファイルの内容]** 領域に表示されます。

  カスタム構成ファイルにデバイストークンを追加することもできます。 デバイストークンは、デバイス固有の情報を追加するために使用されます。 たとえば、シリアル番号を表示するには、`{{serialnumber}}` と入力します。 デバイスでは、各デバイスに固有の`123456789ABC`と同様のテキストが表示されます。 変数を入力するときは、必ず中かっこ `{{ }}` を使用してください。 [アプリの構成トークン](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)に関する記事には、使用できる変数の一覧が掲載されています。 `deviceid` または他のデバイス固有の値を使用することもできます。

  > [!NOTE]
  > 変数は UI で検証されず、大文字と小文字が区別されます。 その結果、不適切な入力で保存されたプロファイルが表示される場合があります。 たとえば、`{{deviceid}}` の代わりに `{{DeviceID}}` を入力した場合、リテラル文字列がデバイスの一意の ID の代わりに表示されます。 正しい情報を入力してください。

**[OK]**  >  **[作成]** を選択して変更を保存します。 プロファイルが作成されて、プロファイル一覧に表示されます。

## <a name="next-steps"></a>次の手順

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当てます](device-profile-assign.md)。

[macOS デバイスでプロファイルを作成する](custom-settings-macos.md)方法を確認してください。 
