---
title: Microsoft Intune で Windows Phone 8.1 デバイスにカスタム設定を追加する - Azure | Microsoft Docs
titleSuffix: ''
description: Microsoft Intune で Windows Phone 8.1 を実行するデバイス用の OMA-URI 設定を使用するためのカスタム プロファイルを追加または作成します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 97d656db3e828ef3377b927395a283fe995bb8a4
ms.sourcegitcommit: a63b9eaa59867ab2b0a6aa415c19d9fff4fda874
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389298"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>Intune で Windows Phone 8.1 デバイス用のカスタム設定を使用する

Microsoft Intune では、"カスタム プロファイル" を使用して Windows Phone 8.1 デバイス用のカスタム設定を追加または作成できます。 カスタム プロファイルは Intune の機能です。 Intune に組み込まれていないデバイスの設定と機能を追加するように設計されています。

Windows Phone 8.1 のカスタム プロファイルでは、Open Mobile Alliance Uniform Resource Identifier (OMA-URI) の設定を使用してさまざまな機能を構成します。 通常、これらの設定は、デバイスの機能を制御するためにモバイル デバイスの製造元によって使われます。 [Windows Phone 8.1 の MDM プロトコルのドキュメント](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-phone/dn499787(v=technet.10))設定を示しています。

この記事では、Windows Phone 8.1 デバイス用のカスタム プロファイルを作成する方法を示します。 

## <a name="create-the-profile"></a>プロファイルの作成

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択します。
3. 次の設定を入力します。

    - **名前**: `windows phone custom profile` のようにプロファイルの名前を入力します。
    - **説明**: プロファイルの説明を入力します
    - **プラットフォーム**: **Windows Phone 8.1** を選択します。
    - **プロファイルの種類**: **[カスタム]** を選択します。

4. **[OMA-URI のカスタム設定]** で、 **[追加]** を選択します。 次の設定を入力します。

    - **名前**: OMA-URI 設定の一意の名前を入力すると、設定リスト内で容易に識別できます。
    - **説明**: 設定の概要と、プロファイルを特定するために役立つその他の関連情報についての説明を入力します。
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

次の例では、Windows 8.1 phone のデバイスはから通信事業者のカバレッジ領域の外側に旅行するときに、移動体通信ネットワークを変更できません。

- **名前**: 携帯電話データ ローミングを許可します。
- **説明**: 許可または携帯電話データのローミングを禁止します。
- **OMA-URI** (大文字小文字を区別): ./Vendor/MSFT/PolicyManager/My/Connectivity/AllowCellularDataRoaming
- **データ型**: 整数
- **値**:0

## <a name="next-steps"></a>次の手順

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当てます](device-profile-assign.md)。

[Windows 10 デバイス](custom-settings-windows-10.md)でのカスタム プロファイルの作成方法を確認してください。
