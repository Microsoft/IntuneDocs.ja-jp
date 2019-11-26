---
title: Microsoft Intune で Android エンタープライズ デバイスにカスタム設定を追加する - Azure | Microsoft Docs
description: Microsoft Intune で Android エンタープライズ デバイスを作成するためのカスタム プロファイルを追加または作成します
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bd2ab7ad8eb155719695bede1f539d5c264d455b
ms.sourcegitcommit: eb2e420b304c7da9d3be5ef49a676cba66766d2b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74319829"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Microsoft Intune で Android エンタープライズ デバイス用のカスタム設定を使用する

Microsoft Intune を使うと、"カスタム プロファイル" を使って、Android エンタープライズの仕事用プロファイルのデバイスのカスタム設定を追加または作成できます。 カスタム プロファイルは Intune の機能です。 Intune に組み込まれていないデバイスの設定と機能を追加するように設計されています。

Android エンタープライズのカスタム プロファイルでは、Open Mobile Alliance Uniform Resource Identifier (OMA-URI) 設定を使って、Android エンタープライズ デバイスの機能を制御します。 通常、これらの設定は、モバイル デバイスの製造元によってこれらの機能を制御するために使われます。

Intune でサポートされている Android Enterprise カスタムプロファイルの数は次のとおりです。

- ./Vendor/MSFT/WiFi/Profile/SSID/Settings:[事前共有キーを使用して wi-fi プロファイルを作成](wi-fi-profile-shared-key.md)する例がいくつかあります。
- ./Vendor/MSFT/VPN/Profile/Name/PackageList:[アプリごとの VPN プロファイルの作成](android-pulse-secure-per-app-vpn.md)にはいくつかの例があります。
- ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste: この記事の[例](#example)を参照してください。 この設定は、ユーザーインターフェイスでも使用できます。 詳細については、[機能を許可または制限する Android エンタープライズ デバイスの設定](device-restrictions-android-for-work.md)に関する記事をご覧ください。

追加の設定が必要な場合は、「 [Android Enterprise の Oemconfig](android-oem-configuration-overview.md)」を参照してください。

この記事では、Android エンタープライズ デバイス用のカスタム プロファイルを作成する方法を示します。 また、コピーと貼り付けをブロックするカスタム プロファイルの例も示します。

## <a name="create-the-profile"></a>プロファイルの作成

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択します。
3. 次の設定を入力します。

    - **名前**: `android enterprise custom profile` のようにプロファイルの名前を入力します
    - **説明**: プロファイルの説明を入力します
    - **プラットフォーム**: **[Android エンタープライズ]** を選択します
    - **プロファイルの種類**: **[カスタム]** を選択します

4. **[OMA-URI のカスタム設定]** で、 **[追加]** を選択します。 次の設定を入力します。

    - **名前**: 簡単に見つけられるように、OMA-URI 設定の一意の名前を入力します。
    - **説明**: 設定の概要および他の重要な詳細がわかる説明を入力します。
    - **OMA-URI**: 設定として使用する OMA-URI を入力します。
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

この例では、Android エンタープライズ デバイスで仕事用アプリと個人用アプリ間のコピーと貼り付け操作を制限するカスタム プロファイルを作成します。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択します。
3. 次の設定を入力します。

    - **名前**: `android ent block copy paste custom profile` のようにプロファイルの名前を入力します。
    - **説明**: プロファイルの説明を入力します
    - **プラットフォーム**: **[Android エンタープライズ]** を選択します。
    - **プロファイルの種類**: **[カスタム]** を選択します。

4. **[OMA-URI のカスタム設定]** で、 **[追加]** を選択します。 次の設定を入力します。

    - **名前**: `Block copy and paste` のような名前を入力します。
    - **説明**: `Blocks copy/paste between work and personal apps` のような説明を入力します。
    - **OMA-URI**: 「`./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`」と入力します。
    - **データ型**: この OMA-URI の値は **True** または **False** なので、 **[ブール値]** を選択します。
    - **値**: **[True]** を選択します。

5. 設定を入力した後、環境は次の画像のようになります。

    ![Android 仕事用プロファイルのコピーと貼り付けをブロックします。](./media/custom-settings-android-for-work/custom-policy-afw-copy-paste.png)

このプロファイルを管理対象の Android エンタープライズ デバイスに割り当てると、仕事用アプリと個人用アプリの間でのコピーと貼り付けはブロックされます。

## <a name="next-steps"></a>次の手順

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当てます](device-profile-assign.md)。

[Android デバイスでプロファイルを作成する](../custom-settings-android.md)方法を確認してください。
