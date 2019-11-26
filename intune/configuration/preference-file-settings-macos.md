---
title: Microsoft Intune で macOS デバイスに設定ファイルの設定を追加する - Azure | Microsoft Docs
titleSuffix: ''
description: アプリに関する重要な情報を含む xml ファイルまたは plist ファイルを追加します。 基本設定ファイルのデバイス構成プロファイルを使用して、プロパティリストファイル内のキー情報を変更し、macOS デバイスに割り当てます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9acad2e8539da7210c349ffb254af62f370af5f6
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74391499"
---
# <a name="add-a-property-list-file-to-macos-devices-using-microsoft-intune"></a>Microsoft Intune を使用して macOS デバイスにプロパティリストファイルを追加する

Microsoft Intune を使用すると、macOS デバイスのプロパティリストファイル (plist)、または macOS デバイス上のアプリを追加できます。

この機能は、以下に適用されます。

- 10.7 以降を実行している macOS デバイス

プロパティリストファイルには、通常、macOS アプリケーションに関する情報が含まれています。 詳細については、「[情報プロパティリストファイル](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html)(Apple の web サイト)」および「[カスタムペイロード設定](https://support.apple.com/guide/mdm/custom-mdm9abbdbe7/1/web/1)」を参照してください。

この記事では、macOS デバイスに追加できるプロパティ一覧ファイルのさまざまな設定について説明します。 モバイルデバイス管理 (MDM) ソリューションの一部として、これらの設定を使用して、アプリバンドル ID (`com.company.application`) を追加し、その plist ファイルを追加します。

これらの設定は、Intune でデバイスの構成プロファイルに追加した後、ご使用の macOS デバイスに割り当てたり展開したりします。

## <a name="before-you-begin"></a>始める前に

[プロファイルを作成します](device-profile-create.md)。

## <a name="what-you-need-to-know"></a>知っておく必要がある情報

- これらの設定は検証されません。 プロファイルをデバイスに割り当てる前に、変更をテストしてください。
- アプリキーを入力する方法がわからない場合は、アプリ内の設定を変更します。 次に、 [Xcode](https://developer.apple.com/xcode/)を使用してアプリの基本設定ファイルを確認し、設定がどのように構成されているかを確認します。 Apple では、ファイルをインポートする前に、Xcode を使用して管理できない設定を削除することをお勧めします。
- 一部のアプリのみが管理対象の設定で動作し、すべての設定を管理することはできません。
- ユーザーチャネル設定ではなく、デバイスチャネル設定をターゲットにするプロパティリストファイルを必ずアップロードしてください。 プロパティリストファイルは、デバイス全体を対象とします。

## <a name="preference-file"></a>基本設定ファイル

- **基本設定ドメイン名**: プロパティリストファイルは、通常、web ブラウザー (microsoft Edge)、 [Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)、およびカスタムアプリに使用されます。 基本設定ドメインを作成すると、バンドル ID も作成されます。 バンドル ID (`com.company.application`など) を入力します。 たとえば、「`com.Contoso.applicationName`」、「`com.Microsoft.Edge`」、または「`com.microsoft.wdav`」と入力します。
- **プロパティリストファイル**: アプリに関連付けられているプロパティリストファイルを選択します。 `.plist` または `.xml` ファイルであることを確認してください。 たとえば、`YourApp-Manifest.plist` ファイルまたは `YourApp-Manifest.xml` ファイルをアップロードします。
- **ファイルの内容**: プロパティリストファイル内のキー情報が表示されます。 キー情報を変更する必要がある場合は、別のエディターでリストファイルを開き、Intune でファイルを再度アップロードします。

**[OK]**  >  **[作成]** を選択して変更を保存します。 プロファイルが作成されて、プロファイル一覧に表示されます。

## <a name="next-steps"></a>次の手順

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
