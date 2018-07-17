---
title: Android 仕事用プロファイル用の Intune カスタム プロファイル設定
titlesuffix: Microsoft Intune
description: Android 仕事用プロファイル用の Microsoft Intune カスタム プロファイル設定を作成する方法について説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/12/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 109c50acf194598017aa507a0979ad3b9298de9e
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905293"
---
# <a name="create-intune-custom-profile-settings-for-android-work-profile-devices"></a>Android 仕事用プロファイル デバイス用の Intune カスタム プロファイル設定を作成する

Intune Android 仕事用プロファイル カスタム構成ポリシーを使用して、Android 仕事用プロファイル デバイスでの各機能の制御に使用できる OMA-URI 設定を割り当てます。 これらの設定は、多くのデバイス製造元がデバイスの機能を制御するために使用する標準の設定です。

この機能は、Intune ポリシーで構成できない Android 設定を割り当てられるようにするためのものです。 現時点では、Intune でサポートされる Android カスタム ポリシーの数は限られています。 構成できるポリシーを見つける場合は、この記事の例を参照してください。

## <a name="create-a-custom-profile"></a>カスタム プロファイルの作成

1. 「[Microsoft Intune でカスタム デバイス設定を構成する方法](custom-settings-configure.md)」の手順に従って開始します。 **[プラットフォーム]** には **[Android エンタープライズ]** を選択し、**[プロファイルの種類]** には **[カスタム]** を選択します。
2. **[OMA-URI のカスタム設定]** ブレードで **[追加]** を選択して、新しい設定を追加します。
3. **[行の追加]** ブレードで、以下を構成します。
    - **[名前]** - Android 仕事用プロファイル カスタム設定の一意の名前を入力すると、Azure portal 内で容易に識別できます。
    - **[説明]** - Android カスタム ポリシーの概要や、ポリシーを特定するのに役立つその他の関連情報についての説明を入力します。
    - **[OMA-URI]** - 設定対象の OMA-URI を入力します。
    - **[データ型]** - この OMA-URI 設定を指定するデータ型を選択します。 **[文字列]**、**[文字列 (XML ファイル)]**、**[日付と時刻]**、**[整数]**、**[浮動小数点]**、**[ブール値]**、または **[Base64 (ファイル)]** から選択します。
    - **[値]** - 以前に指定した OMA-URI に関連付ける値を指定します。 この値の指定に使用する方法は、選択したデータ型によって異なります。 たとえば、**[日付と時刻]** を選択した場合は、[日付の選択] から値を選択します。
4. 完了したら、[OK] を選択して **[OMA-URI のカスタム設定]** に戻り、他の設定を追加するか、**[作成]** を選択してカスタム プロファイルを作成します。


## <a name="example"></a>例

この例では、Android 仕事用プロファイル デバイスで、仕事用アプリと個人用アプリ間のコピーと貼り付け操作を許可するかどうかの制限に使用できるカスタム プロファイルを作成します。

1. この記事の手順に従い、次の値を使用して Android 仕事用プロファイル デバイス用のカスタム プロファイルを作成します。
    - **[名前]** - 「コピーと貼り付けをブロック」または独自のテキストを入力します。
    - **[説明]** - 「仕事用アプリと個人用アプリの間でのコピーや貼り付けをブロック」または独自のテキストを入力します。
    - **[OMA-URI]** - 「**./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste**」を入力します。
    - **[データ型]** - **[ブール]** を選択して、この OMA-URI の値が **True** または **False** のいずれかであるかを示します。
    - **[値]** - **True** を選択します。
2. 最終的に、この画像のような設定になります。
![Android 仕事用プロファイルのコピーと貼り付けをブロックします。](./media/custom-policy-afw-copy-paste.png)
3. これで、このカスタム プロファイルを管理対象の Android 仕事用プロファイル デバイスに割り当てると、仕事用アプリと個人用アプリの間でのコピーと貼り付けはブロックされます。