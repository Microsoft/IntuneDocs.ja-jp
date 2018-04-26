---
title: iOS 用 Microsoft Intune 共有デバイス構成設定
titlesuffix: ''
description: iOS デバイスのロック画面に情報を表示するために使用できる Microsoft Intune 設定について説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7c735486ad93bd76350435861482505a1ab0d30a
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>iOS デバイスのロック画面にメッセージを表示するための共有デバイス構成設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事では、iOS デバイスのロック画面に情報を表示するために使用できる Microsoft Intune 設定について説明します。

共有デバイス構成設定では、ログイン ウィンドウやロック画面に表示する任意のテキストを指定できます。 たとえば、"忘れ物として見つけた場合の返却先" メッセージや資産タグなどを入力できます。 

>[!IMPORTANT]
> この機能は、iOS 9.3 以降を実行している監視対象デバイスでサポートされます。

## <a name="create-shared-device-settings"></a>共有デバイス設定を作成する

1. [Azure Portal の Intune](https://portal.azure.com) から[デバイス構成領域の **[デバイス機能]**](device-features-configure.md) に移動します。 
1. **[デバイス機能]** ウィンドウで、**[共有デバイスの構成 (監視のみ)]** を選びます。
2. **[共有デバイスの構成 (監視のみ)]** ウィンドウで、以下の設定を構成します。
    - **[資産タグ情報]** - デバイスの資産タグに関する情報を入力します。 例: **Contoso Corp によって所有されている**。入力した情報は、このプロファイルを割り当てるすべてのデバイスに適用されます。
    - **[ロック画面の脚注]** - デバイスの紛失または盗難時に、返却に役立つようなメモを入力します。 例: **拾った方はこの番号 (xxx-xxx-xxx) にご連絡ください**。
3. 完了したら、**[プロファイルの作成]** ウィンドウに戻るまで **[OK]** を選択し、戻ったら **[作成]** を選択します。 


## <a name="next-steps"></a>次の手順

選択したグループにデバイス プロファイルを割り当てることができます。 詳しくは、「[デバイス プロファイルを割り当てる方法](device-profile-assign.md)」をご覧ください。
