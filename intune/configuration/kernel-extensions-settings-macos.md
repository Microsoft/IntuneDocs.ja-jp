---
title: Microsoft Intune の macOS カーネル拡張機能の設定-Azure |Microsoft Docs
titleSuffix: ''
description: MacOS デバイスでカーネル拡張機能を使用する設定を追加、構成、または作成します。 また、承認された拡張機能のオーバーライド、チーム識別子からのすべての拡張の許可、または Microsoft Intune での特定の拡張機能またはアプリの許可をユーザーに許可します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8632f5b8df0f483de3bb4d06a6823639ba52c604
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506704"
---
# <a name="macos-device-settings-to-configure-and-use-kernel-extensions-in-intune"></a>Intune でカーネル拡張機能を構成して使用するための macOS デバイス設定

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

この記事では、macOS デバイスで制御できるさまざまなカーネル拡張機能の設定の一覧を示して説明します。 モバイルデバイス管理 (MDM) ソリューションの一部として、これらの設定を使用して、デバイスにカーネル拡張機能を追加し、管理します。

Intune のカーネル拡張機能と前提条件の詳細については、 [macOS カーネル拡張機能の追加](../kernel-extensions-overview-macos.md)に関するページを参照してください。

これらの設定は、Intune でデバイスの構成プロファイルに追加した後、ご使用の macOS デバイスに割り当てたり展開したりします。

## <a name="before-you-begin"></a>始める前に

[デバイスカーネル拡張機能の構成プロファイルを作成](../kernel-extensions-overview-macos.md)します。

> [!NOTE]
> これらの設定は、さまざまな登録の種類に適用されます。 さまざまな登録の種類の詳細については、「 [macOS の登録](../macos-enroll.md)」を参照してください。

## <a name="kernel-extensions"></a>カーネル拡張機能

### <a name="settings-apply-to-user-approved-automated-device-enrollment"></a>設定の適用対象: ユーザーの承認済み、自動デバイス登録

- **ユーザー**による上書きを許可する: **[許可]** に設定すると、ユーザーは、構成プロファイルに含まれていないカーネル拡張機能を承認できます。 **未構成**(既定) では、ユーザーは構成プロファイルに含まれていない拡張機能を許可できません。 つまり、構成プロファイルに含まれている拡張機能のみが許可されます。

  この機能の詳細については[、「ユーザーが承認したカーネル拡張](https://developer.apple.com/library/archive/technotes/tn2459/_index.html)機能の読み込み (Apple の web サイトを開く)」を参照してください。

- **許可されるチーム識別子**: この設定を使用して、1つまたは複数のチーム id を許可します。 入力したチーム Id で署名されたカーネル拡張機能は、許可され、信頼されています。 言い換えると、このオプションを使用すると、同じチーム ID 内のすべてのカーネル拡張が許可されます。これは、特定の開発者またはパートナーである可能性があります。

  読み込む有効なカーネル拡張機能のチーム識別子を**追加**します。 複数のチーム識別子を追加できます。 チーム識別子は英数字 (文字と数字) で、10文字である必要があります。 たとえば、「`ABCDE12345`」と入力します。

  チーム識別子を追加した後は、削除することもできます。

  [チーム ID を探し](https://help.apple.com/developer-account/#/dev55c3c710c)ます (Apple の web サイトを開きます)。詳細については、こちらを参照してください。

- **許可されるカーネル拡張機能**: 特定のカーネル拡張機能を許可するには、この設定を使用します。 入力したカーネル拡張子のみが許可または信頼されます。 

  読み込むカーネル拡張機能のバンドル識別子とチーム識別子を**追加**します。 未署名のレガシカーネル拡張機能の場合は、空のチーム識別子を使用します。 複数のカーネル拡張機能を追加できます。 チーム識別子は英数字 (文字と数字) で、10文字である必要があります。 たとえば、 **[バンドル ID]** に「`com.contoso.appname.macos`」と入力し、**チーム識別子**に `ABCDE12345` を入力します。

  > [!TIP]
  > MacOS デバイスでカーネル拡張機能 (Kext) のバンドル ID を取得するには、次のようにします。
  >
  > 1. ターミナルで `kextstat | grep -v com.apple`を実行し、出力を確認します。 必要なソフトウェアまたは Kext をインストールします。 `kextstat | grep -v com.apple` をもう一度実行し、変更を探します。
  >
  >    ターミナルでは、`kextstat` OS のすべてのカーネル拡張機能が一覧表示されます。 
  >
  > 2. デバイスで、Kext の情報プロパティリストファイル (情報 plist) を開きます。 バンドル ID が表示されます。 各 Kext には、の内部に格納されている情報 plist ファイルがあります。 

> [!NOTE]
> チーム識別子とカーネル拡張機能を追加する必要はありません。 どちらか一方を構成できます。

## <a name="next-steps"></a>次の手順

[プロファイルを割り当て](../device-profile-assign.md)、[その状態を監視](../device-profile-monitor.md)します。
