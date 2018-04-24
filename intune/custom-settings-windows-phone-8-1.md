---
title: Windows Phone 8.1 を実行するデバイス向けの Microsoft Intune のカスタム設定
titleSuffix: ''
description: Windows Phone 8.1 カスタム プロファイルで使用できる Intune の設定について説明します。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 83c123f3752680dbc7faca76aa525a0f035831d7
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-phone-81"></a>Windows Phone 8.1 を実行するデバイス向けの Microsoft Intune のカスタム デバイス設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune Windows Phone 8.1 **カスタム** プロファイルを使用して、Windows Phone 8.1 デバイスで各機能の制御に使用できる OMA-URI 設定を割り当てます。 これらの設定は、多くのデバイス製造元がデバイスの機能を制御するために使用する標準の設定です。

この機能は、他の Intune ポリシーで構成できない設定を割り当てられるようにするためのものです。

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Windows Phone 8.1 デバイス向けのカスタム ポリシー設定

1. 「[How to configure custom device settings in Microsoft Intune (Microsoft Intune でカスタム デバイス設定を構成する方法)](custom-settings-configure.md)」の手順に従って開始します。
2. **[OMA-URI のカスタム設定]** ウィンドウで **[追加]** を選択し、1 つまたは複数の OMA-URI を追加します。
3. **[行の追加]** ウィンドウで、設定ごとに次の値を構成します。
    - **[名前]** - OMA-URI 設定の一意の名前を入力すると、設定リスト内で容易に識別できます。
    - **[説明]** - 設定の概要と、それを特定するために役立つその他の関連情報についての説明を入力します。
    - **[OMA-URI]** - 設定対象の OMA-URI を指定します。
    - **[データ型]** - この OMA-URI 設定を指定するデータ型を選択します。 **[文字列]**、**[文字列 (XML)]**、**[日付と時刻]**、**[整数]**、**[浮動小数点]**、**[ブール値]**、または **[Base64]** から選択します。
    - **[値]** - 入力した OMA-URI に関連付ける値またはファイルを入力します。

4. 完了したら **[OK]** をクリックし、必要に応じて引き続き他の設定を追加します。
