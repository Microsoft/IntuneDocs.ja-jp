---
title: "Windows 10 デバイス向けの Intune カスタム設定"
titlesuffix: Azure portal
description: "Windows 10 カスタム プロファイルで使用できる設定について説明します。\""
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7bcea136-7260-4042-b21b-c7dab86b380d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7101c489c0418b98be3224888a8473a77192ce0f
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="custom-device-settings-for-windows-10-devices-in-microsoft-intune"></a>Microsoft Intune での Windows 10 デバイス向けのカスタム デバイス設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Windows 10 と Windows 10 Mobile 用の Microsoft Intune **カスタム** プロファイルを使用して、デバイスで各機能の制御に使用できる OMA-URI (Open Mobile Alliance Uniform Resource Identifier) 設定を展開します。 Windows 10 では、[Policy Configuration Service プロバイダー (Policy CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers) など、多くの CSP 設定を使用できます。
特定の設定を探しているのであれば、[Windows 10 デバイス制限プロファイル](device-restrictions-windows-10.md)には Intune に組み込まれているさまざまな設定があり、カスタム値の指定が要求されないことにご留意ください。

1. 「[How to configure custom device settings in Microsoft Intune (Microsoft Intune でカスタム デバイス設定を構成する方法)](custom-settings-configure.md)」の手順に従って開始します。
2. **[プロファイルを作成します]** ブレードで **[設定]** を選択し、1 つまたは複数の OMA-URI 設定を追加します。
3. **[OMA-URI のカスタム設定]** ブレードで **[追加]** をクリックして、新しい値を追加します。 **[エクスポート]** をクリックして、コンマ区切り値 (.csv) ファイルで構成した値の一覧を作成することもできます。
4. 各 OMA-URI 設定を追加するには、次の情報を入力します。 このトピックにあるリストを使用して、使用できる設定の詳細について説明します。
    - **設定名** - OMA-URI 設定の一意の名前を入力すると、設定リスト内で容易に識別できます。
    - **設定の説明** - 必要に応じて、設定の説明を入力します。
    - **データ型** - 以下から選択します。
        - **文字列**
        - **文字列型 (XML)**
        - **日付と時刻**
        - **整数型**
        - **浮動小数点**
        - **ブール型**
    - **OMA-URI (大文字と小文字を区別)** - 設定対象の OMA-URI を指定します。
    - **値** - 入力した OMA-URI に関連付ける値を指定します。
5. 完了したら、**[プロファイルを作成します]** ブレードに戻り、**[作成]** をクリックします。
プロファイルが作成され、プロファイルの一覧ブレードに表示されます。

## <a name="example"></a>例
以下のスクリーン ショットで、**Connectivity/AllowVPNOverCellular** 設定が有効になりました。 これにより、移動体通信ネットワーク上の Windows 10 デバイスで OpenVPN 接続を利用できます。

> ![VPN 設定を含むカスタム ポリシーの例](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>構成できるポリシーを見つける方法

Windows ドキュメント ライブラリの[構成サービス プロバイダー リファレンス](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)に、Windows 10 でサポートされているすべての構成サービス プロバイダー (CSP) の完全一覧があります。

Windows 10 のバージョンによっては、一部の設定に互換性がありません。 Windows トピックの表を見れば、各 CSP でサポートされているバージョンを確認できます。

また、トピックの一覧にある設定の一部は Intune でサポートされていません。 Intune で必要な設定がサポートされているかどうかを確認するには、その設定のトピックを開きます。 各設定ページには、サポートされている操作が示されます。 Intune で利用するには、その設定で**追加**操作または**置換**操作がサポートされている必要があります。


