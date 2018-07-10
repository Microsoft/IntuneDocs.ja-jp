---
title: Microsoft Intune での Windows 10 デバイス向けのカスタム設定 - Azure | Microsoft Docs
description: Microsoft Intune でカスタム プロファイルを使用して、Windows 10 を実行しているデバイスに OMA-URI カスタム設定を構成します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bdbb6643a4ee8aace0db22cd7f9189f7ac6445f0
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36232828"
---
# <a name="custom-oma-uri-settings-for-windows-10-devices---intune"></a>Windows 10 デバイスのカスタム OMA-URI 設定 - Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows 10 と Windows 10 Mobile 用の Microsoft Intune **カスタム** プロファイルを使用して、OMA-URI (Open Mobile Alliance Uniform Resource Identifier) 設定を展開します。 これらの設定は、デバイスの機能を制御するために使用されます。 Windows 10 では、[ポリシー構成サービス プロバイダー (ポリシー CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers) など、多くの構成サービス プロバイダー (CSP) 設定を使用できます。

特定の設定を探しているのであれば、[Windows 10 デバイス制限プロファイル](device-restrictions-windows-10.md)には Intune に組み込まれているさまざまな設定があり、カスタム値は必須ではない点に注意してください。

## <a name="configure-custom-settings"></a>カスタム設定を構成する

1. **カスタム** プロファイルの種類を使用して新しい構成プロファイルを作成します。 手順については、[カスタム デバイス設定の構成する方法](custom-settings-configure.md)に関するページを参照してください。
2. **[OMA-URI のカスタム設定]** で **[追加]** を選択し、新しい設定を作成します。 **[エクスポート]** をクリックして、コンマ区切り値 (.csv) ファイルで構成した値の一覧を作成することもできます。
3. 各 OMA-URI 設定を追加するには、次の情報を入力します。

- **名前**: OMA-URI 設定の一意の名前を入力すると、設定リスト内で容易に識別できます。
- **説明**: 必要に応じて、設定の説明を入力します。
- **OMA-URI (大文字と小文字を区別)**: 設定対象の OMA-URI を入力します。
- **データ型**: 以下から選択します。
  - **文字列**
  - **文字列型 (XML)**
  - **日付と時刻**
  - **整数型**
  - **浮動小数点**
  - **ブール型**
  - **Base64**
- **値**: 入力した OMA-URI に関連付ける値またはファイルを入力します。

4. 完了したら、**[OK]** を選択します。 **[プロファイルの作成]** で **[作成]** を選択します。 プロファイルが作成され、プロファイル一覧に表示されます。

## <a name="example"></a>例
次の例では、**Connectivity/AllowVPNOverCellular** 設定が有効です。 この設定により、移動体通信ネットワーク上の Windows 10 デバイスで VPN 接続が利用できるようになります。

![VPN 設定を含むカスタム ポリシーの例](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>構成できるポリシーを見つける

「[Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)」(構成サービス プロバイダー リファレンス) には、Windows 10 でサポートされているすべての構成サービス プロバイダー (CSP) の詳細な一覧が掲載されています。

Windows 10 のバージョンによっては、一部の設定に互換性がありません。 各 CSP でサポートされるバージョンについては、「[Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)」(構成サービス プロバイダー リファレンス) を参照してください。

また、掲載されている設定の一部は Intune でサポートされていません。 Intune で必要な設定がサポートされているかどうかを確認するには、その設定の記事を開きます。 各設定ページには、サポートされている操作が示されます。 Intune で利用するには、その設定で**追加**操作または**置換**操作がサポートされている必要があります。
