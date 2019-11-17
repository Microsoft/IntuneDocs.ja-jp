---
title: Microsoft Intune - Azure でのデバイス プロファイルの作成 | Microsoft Docs
description: Microsoft Intune でデバイス構成プロファイルを追加または構成します。 プラットフォームの種類を選択し、設定を構成し、スコープのタグを追加します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 51ec328a60ef2737c776bf6cf5d4b8dc1b32460c
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755317"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Microsoft Intune でのデバイス プロファイルの作成

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

デバイス プロファイルでは、設定を追加および構成してから、組織内のデバイスにこれらの設定をプッシュすることができます。 「[デバイス プロファイルを使用してデバイスに機能と設定を適用する](device-profiles.md)」では、可能な操作を含め、詳細について説明しています。

この記事の内容:

- プロファイルを作成する手順を示します。
- プロファイルを "フィルター処理" するためにスコープのタグを追加する方法を示します。
- Windows 10 デバイスに対する適用性ルールについて説明し、ルールを作成する方法を示します。
- デバイスでプロファイルおよびプロファイルの更新を受信した際のチェックインの更新サイクル時間を示します。

## <a name="create-the-profile"></a>プロファイルの作成

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[デバイス]** 、 **[構成プロファイル]** の順に選択します。 次のオプションがあります。

    - **概要**:プロファイルの状態を一覧表示し、ユーザーとデバイスに割り当てたプロファイルに関する追加の詳細を提供します。
    - **管理**:デバイス プロファイルを作成し、カスタムの [PowerShell スクリプト](../apps/intune-management-extension.md)をアップロードしてプロファイル内で実行し、[eSIM](esim-device-configuration.md) を使用してデバイスにデータ プランを追加します。
    - **監視**:プロファイルの状態が成功か失敗かを確認し、プロファイルのログも表示します。
    - **セットアップ**:SCEP または PFX 証明書機関を追加するか、プロファイルで[通信費管理サービス](telecom-expenses-monitor.md)を有効にします。

3. **[プロファイルの作成]** を選択します。 次のプロパティを入力します。

   - **名前**: プロファイルのわかりやすい名前を入力します。 後で簡単に識別できるよう、プロファイルに名前を付けます。 たとえば、適切なプロファイル名は、**会社全体の WP 電子メール プロファイル**などです。
   - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
   - **[プラットフォーム]** :デバイスのプラットフォームを選択します。 次のようなオプションがあります。  

       - **Android**
       - **Android エンタープライズ**
       - **iOS/iPadOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 以降**
       - **Windows 10 以降**

   - **[プロファイルの種類]** :作成する設定の種類を選択します。 表示される一覧は、選択した**プラットフォーム**によって異なります。
   - **設定**:次の記事では、ファイルの種類ごとの設定について説明します。

       - [管理用テンプレート](administrative-templates-windows.md)
       - [カスタム](../custom-settings-configure.md)
       - [配信の最適化](../delivery-optimization-windows.md)
       - [デバイスの機能](../device-features-configure.md)
       - [デバイスの制限](device-restrictions-configure.md)
       - [エディションのアップグレードとモードの切り替え](edition-upgrade-configure-windows-10.md)
       - [教育](education-settings-configure.md)
       - [電子メール](email-settings-configure.md)
       - [Endpoint Protection](../protect/endpoint-protection-configure.md)
       - [ID 保護](../protect/identity-protection-configure.md)  
       - [キオスク](kiosk-settings.md)
       - [PKCS 証明書](../protect/certficates-pfx-configure.md)
       - [PKCS のインポートされた証明書](../protect/certificates-imported-pfx-configure.md)
       - [SCEP 証明書](../protect/certificates-scep-configure.md)
       - [信頼された証明書](../protect/certificates-configure.md)
       - [更新ポリシー](../software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](../protect/advanced-threat-protection.md)
       - [Windows 情報保護](../protect/windows-information-protection-configure.md)

     たとえば、プラットフォームとして **iOS/iPadOS** を選択した場合、プロファイルの種類のオプションは次のプロファイルのようになります。

     ![Intune で iOS プロファイルを作成する](./media/device-profile-create/create-device-profile.png)

4. 完了したら、 **[OK]**  >  **[作成]** の順に選択して変更を保存します。 プロファイルが作成され、一覧に表示されます。

## <a name="scope-tags"></a>スコープのタグ

設定を追加したら、プロファイルにスコープのタグを追加することもできます。 スコープのタグを使用すると、人事や US-NC の全従業員など、特定のグループにポリシーを割り当てて、フィルター処理することができます。

スコープのタグと可能な操作の詳細については、[分散 IT での RBAC とスコープのタグの使用](../fundamentals/scope-tags.md)に関するページを参照してください。

### <a name="add-a-scope-tag"></a>スコープのタグを追加する

1. **[スコープ (タグ)]** を選択します。
2. **[追加]** を選択して、新しいスコープのタグを作成します。 または、一覧から既存のスコープのタグを選択します。
3. **[OK]** を選択して変更を保存します。

## <a name="applicability-rules"></a>適用性ルール

適用対象:

- Windows 10 以降

管理者は、適用性ルールを使用して、グループの特定の条件を満たすデバイスを対象にすることができます。 たとえば、**すべての Windows 10 デバイス** グループに適用されるデバイス制限プロファイルを作成します。 また、Windows 10 Enterprise を実行しているデバイスにのみプロファイルを割り当てことができます。

これを行うには、**適用性ルール**を作成します。 これらのルールは、次のシナリオに最適です。

- Windows 10 Education (EDU) を使用しています。 Bellows College では、RS3 から RS4 までのすべての Windows 10 EDU デバイスを対象にする必要があります。
- Contoso では、人事部のすべてのユーザーを対象にし、さらに Windows 10 Professional または Enterprise デバイスのみを対象にする必要があります。

これらのシナリオに取り組むには:

- Bellows College のすべてのデバイスを含むデバイス グループを作成します。 プロファイルに、OS の最小バージョンが `16299` であり、最大バージョンが `17134` である場合に適用される適用性ルールを追加します。 このプロファイルを Bellows College デバイス グループに割り当てます。

  割り当てられると、入力した最小バージョンから最大バージョンまでのデバイスに対してプロファイルが適用されます。 入力した最小バージョンから最大バージョンまでに含まれないデバイスの場合、その状態は **[適用なし]** と表示されます。

- Contoso の人事部 (HR) のすべてのユーザーを含むユーザー グループを作成します。 プロファイルに、Windows 10 Professional または Enterprise を実行しているデバイスに適用される適用性ルールを追加します。 このプロファイルを HR ユーザー グループに割り当てます。

  割り当てられると、Windows 10 Professional または Enterprise を実行しているデバイスに対してプロファイルが適用されます。 これらのエディションを実行していないデバイスの場合、その状態は **[適用なし]** と表示されます。

- まったく同じ設定のプロファイルが 2 つある場合は、適用性ルールが含まれていないプロファイルが適用されます。 

  たとえば、ProfileA では Windows 10 デバイス グループを対象とし、BitLocker が有効ですが、適用性ルールは含まれていません。 ProfileB では同じ Windows 10 デバイス グループを対象とし、BitLocker が有効であり、Windows 10 Enterprise にのみプロファイルを適用するという適用性ルールが含まれています。

  両方のプロファイルが割り当てられた場合、適用性ルールがないため、ProfileA が適用されます。 

プロファイルをグループに割り当てると、適用性ルールはフィルターとして機能し、条件を満たすデバイスのみが対象になります。

### <a name="add-a-rule"></a>ルールを追加する

1. **[適用性ルール]** を選択します。 **[ルール]** 、 **[プロパティ]** 、および **[OS のエディション]** を選択できます。

    ![Microsoft Intune でデバイス構成プロファイルに適用性ルールを追加する](./media/device-profile-create/applicability-rules.png)

2. **[ルール]** で、ユーザーまたはグループを含めるか除外するかを選択します。 次のようなオプションがあります。

    - **プロファイルを割り当てる条件**:入力した条件を満たすユーザーまたはグループを含めます。
    - **プロファイルを割り当てない条件**:入力した条件を満たすユーザーまたはグループを除外します。

3. **[プロパティ]** で、フィルターを選択します。 次のようなオプションがあります。 

    - **OS のエディション**:一覧で、ルールに含める (または除外する) Windows 10 のエディションをオンにします。
    - **OS のバージョン**:ルールに含める (または除外する) Windows 10 の**最小**および**最大**のバージョン番号を入力します。 両方の値が必要です。

      たとえば、最小バージョンには `10.0.16299.0` (RS3 または 1709) を、最大バージョンには `10.0.17134.0` (RS4 または 1803) を入力できます。 または、さらに細かい設定が可能であり、最小バージョンとして `10.0.16299.001` を、最大バージョンとして `10.0.17134.319` を入力できます。

4. **[追加]** を選択して変更を保存します。

## <a name="refresh-cycle-times"></a>サイクル時間の更新

Intune では、複数の更新サイクルを使用して、構成プロファイルへの更新が確認されます。 登録してすぐのデバイスでは、チェックインの実行頻度が高くなります。 「[ポリシーとプロファイルの更新サイクル](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)に、おおよその更新間隔が一覧表示されています。

ユーザーはいつでもポータル サイト アプリを起動し、デバイスを同期して、プロファイルの更新をすぐに確認できます。

## <a name="next-steps"></a>次の手順

[プロファイルを割り当て](../device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
