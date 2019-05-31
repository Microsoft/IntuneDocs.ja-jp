---
title: Microsoft Intune - Azure でのデバイス プロファイルの作成 | Microsoft Docs
description: Microsoft Intune でデバイス構成プロファイルを追加または構成します。 プラットフォームの種類を選択し、設定を構成して、スコープのタグを追加します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08c6ece37a4ff6eceaa4df735f365453a4bc7d88
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570404"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Microsoft Intune でのデバイス プロファイルの作成

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

デバイス プロファイルでは、設定を追加および構成してから、組織内のデバイスにこれらの設定をプッシュすることができます。 「[デバイス プロファイルを使用してデバイスに機能と設定を適用する](device-profiles.md)」では、可能な操作を含め、詳細について説明しています。

この記事の内容:

- プロファイルを作成する手順を示します。
- プロファイルを "フィルター処理" するためにスコープのタグを追加する方法を示します。
- デバイスでプロファイルおよびプロファイルの更新を受信した際のチェックインの更新サイクル時間を示します。

## <a name="create-the-profile"></a>プロファイルの作成

1. [Azure portal](https://portal.azure.com) で、 **[すべてのサービス]** を選択し、**Intune** でフィルター処理して、 **[Intune]** を選択します。

2. **[デバイス構成]** を選択します。 次のオプションがあります。

    - **概要**:プロファイルの状態を一覧表示し、ユーザーとデバイスに割り当てたプロファイルに関する追加の詳細を提供します。
    - **管理**:デバイス プロファイルを作成し、カスタムの [PowerShell スクリプト](intune-management-extension.md)をアップロードしてプロファイル内で実行し、[eSIM](esim-device-configuration.md) を使用してデバイスにデータ プランを追加します。
    - **監視**:プロファイルの状態が成功か失敗かを確認し、プロファイルのログも表示します。
    - **セットアップ**:SCEP または PFX 証明書機関を追加するか、プロファイルで[通信費管理サービス](telecom-expenses-monitor.md)を有効にします。

3. **[プロファイル]**  >  **[プロファイルの作成]** の順に選択します。 次のプロパティを入力します。

   - **名前**: プロファイルのわかりやすい名前を入力します。 後で簡単に識別できるよう、プロファイルに名前を付けます。 たとえば、適切なプロファイル名は、**会社全体の WP 電子メール プロファイル**などです。
   - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
   - **[プラットフォーム]** :デバイスのプラットフォームを選択します。 次のようなオプションがあります。  

       - **Android**
       - **Android エンタープライズ**
       - **Android**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 以降**
       - **Windows 10 以降**

   - **[プロファイルの種類]** :作成する設定の種類を選択します。 表示される一覧は、選択した**プラットフォーム**によって異なります。
   - **設定**:次の記事では、ファイルの種類ごとの設定について説明します。

       - [管理用テンプレート](administrative-templates-windows.md)
       - [カスタム](custom-settings-configure.md)
       - [配信の最適化](delivery-optimization-windows.md)
       - [デバイスの機能](device-features-configure.md)
       - [デバイスの制限](device-restrictions-configure.md)
       - [エディションのアップグレードとモードの切り替え](edition-upgrade-configure-windows-10.md)
       - [教育](education-settings-configure.md)
       - [電子メール](email-settings-configure.md)
       - [Endpoint Protection](endpoint-protection-configure.md)
       - [ID 保護](identity-protection-configure.md)  
       - [キオスク](kiosk-settings.md)
       - [PKCS 証明書](certficates-pfx-configure.md)
       - [SCEP 証明書](certificates-scep-configure.md)
       - [信頼された証明書](certificates-configure.md)
       - [更新ポリシー](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](advanced-threat-protection.md)
       - [Windows 情報保護](windows-information-protection-configure.md)

     たとえば、プラットフォームとして **iOS** を選択した場合、プロファイルの種類のオプションは次のプロファイルのようになります。

     ![Intune で iOS プロファイルを作成する](./media/create-device-profile.png)

4. 完了したら、 **[OK]**  >  **[作成]** の順に選択して変更を保存します。 プロファイルが作成され、一覧に表示されます。

## <a name="scope-tags"></a>スコープのタグ

設定を追加したら、プロファイルにスコープのタグを追加することもできます。 スコープのタグを使用すると、人事や US-NC の全従業員など、特定のグループにポリシーを割り当てて、フィルター処理することができます。

スコープのタグと可能な操作の詳細については、[分散 IT での RBAC とスコープのタグの使用](scope-tags.md)に関するページを参照してください。

### <a name="add-a-scope-tag"></a>スコープのタグを追加する

1. **[スコープ (タグ)]** を選択します。
2. **[追加]** を選択して、新しいスコープのタグを作成します。 または、一覧から既存のスコープのタグを選択します。
3. **[OK]** を選択して変更を保存します。

## <a name="refresh-cycle-times"></a>サイクル時間の更新

Intune では、次の更新サイクルを使用して、構成プロファイルへの更新が確認されます。

| プラットフォーム | 更新サイクル|
| --- | --- |
| iOS | 6 時間ごと |
| macOS | 6 時間ごと |
| Android | 8 時間ごと |
| デバイスとして登録された Windows 10 PC | 8 時間ごと |
| Windows Phone | 8 時間ごと |
| Windows 8.1 | 8 時間ごと |

登録してすぐのデバイスでは、次のようにチェックインの実行頻度が高くなります。

| プラットフォーム | 頻度 |
| --- | --- |
| iOS | 6 時間まで 15 分ごと、その後 6 時間ごと |  
| macOS | 6 時間まで 15 分ごと、その後 6 時間ごと | 
| Android | 15 分まで 3 分ごと、その後の 2 時間は 15 分ごと、その後 8 時間ごと | 
| デバイスとして登録された Windows 10 PC | 30 分まで 3 分ごと、その後 8 時間ごと | 
| Windows Phone | 15 分まで 5 分ごと、その後の 2 時間は 15 分ごと、その後 8 時間ごと | 
| Windows 8.1 | 15 分まで 5 分ごと、その後の 2 時間は 15 分ごと、その後 8 時間ごと | 

ユーザーはいつでもポータル サイト アプリを起動し、デバイスを同期して、プロファイルの更新をすぐに確認できます。

## <a name="next-steps"></a>次の手順

[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
