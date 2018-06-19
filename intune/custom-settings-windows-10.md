---
title: Windows 10 を実行するデバイス向けの Microsoft Intune のカスタム設定
titlesuffix: ''
description: Windows 10 カスタム プロファイルで構成できるカスタム設定について説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 36705c49a55c88c41470feaad14520e900dcb3dd
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31837015"
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-10"></a>Windows 10 を実行するデバイス向けの Microsoft Intune のカスタム デバイス設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 Windows 10 と Windows 10 Mobile 用の Microsoft Intune **カスタム** プロファイルを使用して、デバイスで各機能の制御に使用できる OMA-URI (Open Mobile Alliance Uniform Resource Identifier) 設定を展開します。 Windows 10 では、[ポリシー構成サービス プロバイダー (ポリシー CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers) など、多くの構成サービス プロバイダー (CSP) 設定を使用できます。
特定の設定を探しているのであれば、[Windows 10 デバイス制限プロファイル](device-restrictions-windows-10.md)には Intune に組み込まれているさまざまな設定があり、カスタム値の指定が要求されないことにご留意ください。

## <a name="configure-custom-settings"></a>カスタム設定を構成する

1. 「[How to configure custom device settings in Microsoft Intune (Microsoft Intune でカスタム デバイス設定を構成する方法)](custom-settings-configure.md)」の手順に従って開始します。
1. **[OMA-URI のカスタム設定]** ウィンドウで **[追加]** をクリックして、新しい値を追加します。 **[エクスポート]** をクリックして、コンマ区切り値 (.csv) ファイルで構成した値の一覧を作成することもできます。
1. 各 OMA-URI 設定を追加するには、次の情報を入力します。 この記事にあるリストを使用して、使用できる設定の詳細について説明します。
    - **[名前]** - OMA-URI 設定の一意の名前を入力すると、設定リスト内で容易に識別できます。
    - **説明** - 必要に応じて、設定の説明を入力します。
    - **OMA-URI (大文字と小文字を区別)** - 設定対象の OMA-URI を指定します。
    - **データ型** - 以下から選択します。
        - **文字列**
        - **文字列型 (XML)**
        - **日付と時刻**
        - **整数型**
        - **浮動小数点**
        - **ブール型**
        - **Base64**
    - **値** - 入力した OMA-URI に関連付ける値またはファイルを指定します。
1. 完了したら、**[OK]** を選択し、**[プロファイルの作成]** ウィンドウに戻り、**[作成]** を選択します。
プロファイルが作成され、プロファイルの一覧ウィンドウに表示されます。

## <a name="example"></a>例
以下のスクリーン ショットで、**Connectivity/AllowVPNOverCellular** 設定が有効になりました。 これにより、移動体通信ネットワーク上の Windows 10 デバイスで OpenVPN 接続を利用できます。

> ![VPN 設定を含むカスタム ポリシーの例](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>構成できるポリシーを見つける方法

Windows ドキュメント ライブラリの[構成サービス プロバイダー リファレンス](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)に、Windows 10 でサポートされているすべての構成サービス プロバイダー (CSP) の完全一覧があります。

Windows 10 のバージョンによっては、一部の設定に互換性がありません。 Windows 記事の表を見れば、各 CSP でサポートされているバージョンを確認できます。

また、記事の一覧にある設定の一部は Intune でサポートされていません。 Intune で必要な設定がサポートされているかどうかを確認するには、その設定の記事を開きます。 各設定ページには、サポートされている操作が示されます。 Intune で利用するには、その設定で**追加**操作または**置換**操作がサポートされている必要があります。
