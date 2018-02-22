---
title: "Windows Holographic for Business デバイス用の Intune のカスタム設定"
titlesuffix: Azure portal
description: "Windows Holographic for Business カスタム プロファイルで使用できる Intune の設定について説明します。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 1/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ae46aef10ca294637a4d433ce273d3c53e695d64
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="custom-device-settings-for-windows-holographic-for-business-devices-in-microsoft-intune"></a>Microsoft Intune での Windows Holographic for Business デバイス用のカスタム デバイス設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 デバイスで機能の制御に使用できる OMA-URI (Open Mobile Alliance Uniform Resource Identifier) の設定を展開するには、Windows Holographic for Business 用の Microsoft Intune **カスタム** プロファイルを使います。 Windows Holographic for Business では、構成サービス プロバイダー (CSP) の多くの設定を利用できます。 CSP の概要については、「[構成サービス プロバイダー (CSP) の概要 (IT 担当者向け)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)」をご覧ください。 Windows Holographic で特定の CSP がサポートされているかどうかについては、「[CSPs supported in Windows Holographic](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens)」(Windows Holographic でサポートされている CSP) をご覧ください。

特定の設定を探している場合、[Windows Holographic for Business デバイス制限プロファイル](device-restrictions-windows-holographic.md)には多くの組み込み設定が含まれ、カスタム値を指定する必要がないことに留意してください。

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
5. 完了したら、**[プロファイルの作成]** ブレードに戻り、**[作成]** をクリックします。
プロファイルが作成され、プロファイルの一覧ブレードに表示されます。

## <a name="supported-custom-settings"></a>サポートされているカスタム設定

Windows Holographic for Business は、以下のカスタム設定をサポートします。


|設定の名前|OMA-URI|［データの種類］  |
|---------|---------|---------|
|AllowFastReconnect     |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|整数 (0 - 非許可、1 - 許可)|
|AllowVPN     |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|整数 (0 - 非許可、1 - 許可)|



## <a name="how-to-find-the-policies-you-can-configure"></a>構成できるポリシーを見つける方法

「[CSPs supported in Windows Holographic](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens)」(Windows Holographic でサポートされている CSP) で、Windows Holographic によってサポートされているすべての構成サービス プロバイダー (CSP) の完全な一覧がわかります。 Windows Holographic のバージョンによっては、一部の設定に互換性がありません。 Windows トピックの表を見れば、各 CSP でサポートされているバージョンを確認できます。

また、トピックの一覧にある設定の一部は Intune でサポートされていません。 Intune で必要な設定がサポートされているかどうかを確認するには、その設定のトピックを開きます。 各設定ページには、サポートされている操作が示されます。 Intune で利用するには、その設定で**追加**操作または**置換**操作がサポートされている必要があります。


