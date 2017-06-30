---
title: "Android デバイス向けの Intune カスタム設定"
titleSuffix: Intune on Azure
description: "Android カスタム プロファイルで使用できる設定について説明します。&quot;"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 014e59c017eac0d54a632e545692e1a1a8053164
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="custom-settings-for-android-devices-in-microsoft-intune"></a>Microsoft Intune での Android デバイス向けのカスタム設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune Android **カスタム** プロファイルを使用して、Android デバイスで各機能の制御に使用できる OMA-URI 設定を割り当てます。 これらの設定は、多くのデバイス製造元がデバイスの機能を制御するために使用する標準の設定です。

この機能は、Intune ポリシーで構成できない Android 設定を割り当てられるようにするためのものです。

## <a name="custom-profile-settings-for-android-devices"></a>Android デバイス向けのカスタム プロファイル設定

1. 「[How to configure custom device settings in Microsoft Intune (Microsoft Intune でカスタム デバイス設定を構成する方法)](custom-settings-configure.md)」の手順に従って開始します。
2. **[プロファイルを作成します]** ブレードで **[設定]** を選択し、1 つまたは複数の OMA-URI 設定を追加します。
3. **[行の編集]** ブレードで、設定ごとに次の値を構成します。
    - **[名前]** - OMA-URI 設定の一意の名前を入力すると、設定リスト内で容易に識別できます。
    - **[説明]** - 設定の概要と、それを特定するために役立つその他の関連情報についての説明を入力します。
    - **[データ型]** - この OMA-URI 設定を指定するデータ型を選択します。 **[文字列]**、**[文字列 (XML)]**、**[日付と時刻]**、**[整数]**、**[浮動小数点]**、または **[ブール値]** から選択します。
    - **[OMA-URI]** - 設定対象の OMA-URI を指定します。
    - **[値]** - 入力した OMA-URI に関連付ける値を入力します。
4. 完了したら **[OK]** をクリックし、必要に応じて引き続き他の設定を追加します。

