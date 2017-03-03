---
title: "Windows Phone 8.1 デバイス向けの Intune カスタム設定 | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Windows 8.1 カスタム プロファイルで使用できる設定について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 21c55041-3821-4a62-9f85-855b97dba269
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: ab1ad9852b8f9145f405bb71cf52bfcb00e078f6
ms.lasthandoff: 02/16/2017


---

# <a name="custom-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>Microsoft Intune での Windows Phone 8.1 デバイス向けのカスタム設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Microsoft Intune Windows Phone 8.1 **カスタム** プロファイルを使用して、Windows Phone 8.1 デバイスで各機能の制御に使用できる OMA-URI 設定を展開します。 これらの設定は、多くのデバイス製造元がデバイスの機能を制御するために使用する標準の設定です。

この機能は、他の Intune ポリシーで構成できない設定を展開できるようにするためのものです。

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Windows Phone 8.1 デバイス向けのカスタム ポリシー設定

1. 「[How to configure custom device settings in Microsoft Intune (Microsoft Intune でカスタム デバイス設定を構成する方法)](how-to-configure-custom-settings.md)」の手順に従って開始します。
2. **[プロファイルを作成します]** ブレードで **[設定]** を選択し、1 つまたは複数の OMA-URI 設定を追加します。
3. **[行の追加]** ブレードで、設定ごとに次の値を構成します。
    - **[名前]** - OMA-URI 設定の一意の名前を入力すると、設定リスト内で容易に識別できます。
    - **[説明]** - 設定の概要と、それを特定するために役立つその他の関連情報についての説明を入力します。
    - **[OMA-URI]** - 設定対象の OMA-URI を指定します。
    - **[データ型]** - この OMA-URI 設定を指定するデータ型を選択します。 **[文字列]**、**[日付と時刻]**、**[整数]**、**[浮動小数点]**、または **[ブール値]** から選択します。
    - **[値]** - 入力した OMA-URI に関連付ける値を入力します。

4. 完了したら **[OK]** をクリックし、必要に応じて引き続き他の設定を追加します。

