---
title: Microsoft Intune - Azure での iOS または macOS デバイス プロファイルの作成 | Microsoft Docs
description: Microsoft Intune で iOS または macOS デバイス プロファイルを追加または作成し、AirPrint、ホーム画面のレイアウト、アプリの通知、共有デバイス、シングル サインイン、Web コンテンツ フィルター設定を構成します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4542a65afa87668702620a1b50443c9844692a87
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831277"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Intune での iOS または macOS デバイスの機能設定の追加

Intune には、管理者が iOS および macOS デバイスを制御するために役立つ多くの機能と設定が含まれています。 たとえば、管理者には次の機能があります。

- ネットワーク内の AirPrint プリンターへのアクセスをユーザーに許可する
- 新しいページの追加を含め、アプリとフォルダーをホーム画面に追加する
- アプリの通知を表示する場合と方法を選択する
- 特に共有デバイスに対して、メッセージまたは資産タグを表示するようにロック画面を構成する
- アプリ間で資格情報を共有するためのセキュリティで保護されたシングル サインオン エクスペリエンスをユーザーに提供する
- 成人向けの言葉を使用している Web サイトをフィルター処理し、特定の Web サイトを許可またはブロックする

これらの機能は Intune で使用できます。また、管理者が構成できます。 Intune では、"構成プロファイル" を使用して、お客様の組織のニーズに合わせてこのような設定を作成およびカスタマイズします。 これらの機能をプロファイルに追加した後は、そのプロファイルをお客様の組織内の iOS および macOS デバイスにプッシュまたは展開できます。

この記事では、デバイス構成プロファイルを作成する方法について説明します。 また、[iOS](ios-device-features-settings.md) および [macOS](macos-device-features-settings.md) デバイスで使用できるすべての設定を確認することもできます。

## <a name="create-a-device-profile"></a>デバイス プロファイルの作成

1. [Azure portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**[Intune]** を選択します。
2. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **[名前]**:新しいプロファイルのわかりやすい名前を入力します。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]**:プラットフォームを選択します。
        - **Android**
        - **macOS**
    - **[プロファイルの種類]**:**[デバイスの機能]** を選択します。
    - **設定**:構成が必要な設定を入力します。 すべての設定の一覧とその実行内容については、以下を参照してください。

        - [Android](ios-device-features-settings.md)
        - [macOS](macos-device-features-settings.md)

4. 完了したら、**[OK]** を選択し、**[作成]** を選択して変更を保存します。

プロファイルが作成され、一覧に表示されます。 必ず[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)してください。

## <a name="next-steps"></a>次の手順

プロファイルが作成されると、割り当てることができます。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

[iOS](ios-device-features-settings.md) および [macOS](macos-device-features-settings.md) デバイスのすべてのデバイス機能設定を表示します。