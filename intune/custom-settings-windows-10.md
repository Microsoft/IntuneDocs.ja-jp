---
title: Microsoft Intune で Windows 10 デバイス用のカスタム設定を追加する - Azure | Microsoft Docs
description: Microsoft Intune で Windows 10 を実行するデバイス用の OMA-URI 設定を使用するためのカスタム プロファイルを追加または作成します。 カスタム プロファイルを使用して、カスタム設定を追加します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9d07b2d46e5128d96a578e9a000e17c2aca7cec
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66373979"
---
# <a name="use-custom-settings-for-windows-10-devices-in-intune"></a>Intune で Windows 10 デバイス用のカスタム設定を使用する

Microsoft Intune では、"カスタム プロファイル" を使用して Windows 10 デバイス用のカスタム設定を追加または作成できます。 カスタム プロファイルは Intune の機能です。 Intune に組み込まれていないデバイスの設定と機能を追加するように設計されています。

Windows 10 のカスタム プロファイルでは、Open Mobile Alliance Uniform Resource Identifier (OMA-URI) の設定を使用してさまざまな機能を構成します。 通常、これらの設定は、デバイスの機能を制御するためにモバイル デバイスの製造元によって使われます。 

Windows 10 では、[ポリシー構成サービス プロバイダー (ポリシー CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers) など、多くの構成サービス プロバイダー (CSP) 設定を使用できます。

特定の設定を探している場合、[Windows 10 デバイス制限プロファイル](device-restrictions-windows-10.md)には多くの組み込み設定が含まれることに留意してください。 そのため、カスタム値の入力は必要ない場合があります。

この記事では、以下のことを示します。

- Windows 10 デバイス用のカスタム プロファイルを作成する方法
- 推奨される OMA-URI 設定の一覧が含まれます
- VPN 接続を開くカスタム プロファイルの例を提供します

## <a name="create-the-profile"></a>プロファイルの作成

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択します。
3. 次の設定を入力します。

    - **名前**: `windows 10 custom profile` のようにプロファイルの名前を入力します。
    - **説明**: プロファイルの説明を入力します
    - **[プラットフォーム]** : **[Windows 10 以降]** を選択します。
    - **プロファイルの種類**: **[カスタム]** を選択します。

4. **[OMA-URI のカスタム設定]** で、 **[追加]** を選択します。 次の設定を入力します。

    - **名前**: OMA-URI 設定の一意の名前を入力すると、設定リスト内で容易に識別できます。
    - **説明**: 設定の概要および他の重要な詳細がわかる説明を入力します。
    - **OMA-URI** (大文字と小文字を区別): 設定として使用する OMA-URI を入力します。
    - **データ型**: この OMA-URI の設定に使用するデータ型を選択します。 次のようなオプションがあります。

        - 文字列型
        - 文字列 (XML ファイル)
        - 日付と時刻
        - 整数型
        - 浮動小数点
        - ブール型
        - Base64 (ファイル)

    - **値**: 入力した OMA-URI に関連付けるデータ値を入力します。 値は、選択したデータ型に依存します。 たとえば、 **[日付と時刻]** を選択した場合は、日付の選択から値を選択します。

    設定を何か追加した後は、 **[エクスポート]** を選択できます。 **[エクスポート]** では、追加した値の一覧がコンマ区切り値 (.csv) ファイルで作成されます。

5. **[OK]** を選択して変更を保存します。 必要に応じて他の設定の追加を続けます。
6. 終わったら、 **[OK]**  >  **[作成]** を選択して Intune プロファイルを作成します。 完了すると、プロファイルが **[デバイス構成 - プロファイル]** の一覧に表示されます。

## <a name="example"></a>例

次の例では、**Connectivity/AllowVPNOverCellular** 設定が有効です。 この設定により、移動体通信ネットワーク上の Windows 10 デバイスで VPN 接続が利用できるようになります。

![VPN 設定を含むカスタム ポリシーの例](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>構成できるポリシーを見つける

「[Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)」(構成サービス プロバイダー リファレンス) には、Windows 10 でサポートされているすべての構成サービス プロバイダー (CSP) の詳細な一覧が記載されています。

Windows 10 のバージョンによっては、一部の設定に互換性がありません。 各 CSP でサポートされるバージョンについては、「[Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)」(構成サービス プロバイダー リファレンス) を参照してください。

また、「[Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)」(構成サービス プロバイダー リファレンス) に記載されているすべての設定が Intune でサポートされているわけではありません。 Intune で必要な設定がサポートされているかどうかを確認するには、その設定の記事を開きます。 各設定ページには、サポートされている操作が示されます。 Intune で利用するには、その設定で**追加**、**置換**、**取得**の操作がサポートされている必要があります。 **取得**の操作によって返された値が**追加**または**置換**の操作によって得た値と一致しない場合、Intune ではコンプライアンス エラーが報告されます。

## <a name="next-steps"></a>次の手順

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当てます](device-profile-assign.md)。
