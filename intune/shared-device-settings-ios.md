---
title: Microsoft Intune を使用して iOS デバイスのロック画面をカスタマイズする - Azure | Microsoft Docs
titlesuffix: ''
description: iOS の共有デバイス構成設定を使用して、iOS デバイスのロック画面に情報を表示するために使用できる Microsoft Intune 設定について説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9f4d75d795421c761398f349c324b498fd21ca01
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203078"
---
# <a name="add-custom-messages-to-lock-screen-and-login-window-on-ios-devices-using-microsoft-intune"></a>Microsoft Intune を使用して iOS デバイスのロック画面とログイン ウィンドウにカスタム メッセージを追加する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事では、iOS デバイスのロック画面とログイン ウィンドウに情報を表示するために使用できる Microsoft Intune 設定について説明します。 

これらの設定を使用して、ログイン ウィンドウとロック画面にカスタム メッセージまたはテキストを表示します。 たとえば、"忘れ物として見つけた場合の返却先" メッセージや資産タグ情報などを入力できます。

これらの設定は、iOS 9.3 以降を実行している監視対象のデバイスをサポートします。

## <a name="create-the-profile"></a>プロファイルの作成

1. [Azure portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**[Intune]** を選択します。
2. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
3. プロファイルの **[名前]** と **[説明]** を入力します。
4. **[プラットフォーム]** で **[iOS]** を選択します。 **[プロファイルの種類]** で **[デバイス機能]** を選択します。
5. **[設定]** で **[ロック画面のメッセージ (監視モードのみ)]** を選択します。 次の設定を構成します。

    - **資産タグ情報**:デバイスの資産タグに関する情報を入力します。 たとえば、「`123xyz`」と入力します。

        入力したテキストは、デバイスのログイン ウィンドウとロック画面に表示されます。

    - **ロック画面の脚注**:デバイスの紛失または盗難時に、返却に役立つようなメモを入力します。 このフィールドには任意のテキストを入力できます。 たとえば、`If found, call Contoso at ...` のようなものを入力します。

    デバイス トークンを使用して、このようなフィールドにデバイス固有の情報を追加することもできます。 たとえば、シリアル番号を表示するには、`Serial Number: {{serialnumber}}` と入力します。 ロック画面には、`Serial Number 123456789ABC` のようにテキストが表示されます。 変数を入力するときは、必ず中かっこ `{{ }}` を使用してください。 [アプリの構成トークン](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)に関する記事には、使用できる変数の一覧が掲載されています。 `deviceName` または他のデバイス固有の値を使用することもできます。

6. 完了したら **[OK]** > **[OK]** > **[作成]** の順に選択します。 一覧にプロファイルが表示されます。

## <a name="next-steps"></a>次の手順

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
