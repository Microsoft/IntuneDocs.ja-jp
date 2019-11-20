---
title: Android 用のアプリごとのカスタム VPN プロファイル
titleSuffix: Microsoft Intune
description: Microsoft Intune で管理する Android デバイス用にアプリごとの VPN プロファイルを作成する方法について説明します。
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
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3683d2aeada791c6ec827e915e02365a336e6045
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059671"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Microsoft Intune のカスタム プロファイルを使って、Android デバイス用にアプリごとの VPN プロファイルを作成する

[!INCLUDE[azure_portal](../includes/azure_portal.md)]

Intune で管理する、アプリごとの VPN プロファイルを Android 5.0 以降のデバイスに作成できます。 まず、Pulse Secure または Citrix 接続の種類を使用する VPN プロファイルを作成します。 次に、特定のアプリと VPN プロファイルを関連付けるカスタム構成ポリシーを作成します。

Android デバイスまたはユーザー グループにポリシーが割り当てられた後、ユーザーは Pulse Secure または Citrix VPN クライアントを開始する必要があります。 その後、VPN クライアントは、指定されたアプリからのトラフィックのみに OpenVPN 接続の使用を許可します。

> [!NOTE]
>
> このプロファイルに対しては Pulse Secure 接続タイプと Citrix 接続タイプのみがサポートされます。

## <a name="step-1-create-a-vpn-profile"></a>手順 1.VPN プロファイルの作成

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **名前**: プロファイルのわかりやすい名前を入力します。 後で簡単に識別できるよう、プロファイルに名前を付けます。 たとえば、「**会社全体の Android アプリ別 VPN プロファイル**」は適切なプロファイル名です。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]** : **[Android]** を選択します。
    - **[プロファイルの種類]** : **[VPN]** を選択します。

4. **[設定]**  >  **[構成]** の順に選択し、[VPN 設定を構成する方法](vpn-settings-configure.md)に関する記事および [Android デバイス用の Intune VPN 設定](vpn-settings-android.md)に関する記事の設定に従って VPN プロファイルを構成します。

VPN プロファイルの作成時に指定した**接続名**の値を書き留めてください。 この名前は次の手順で必要になります。 たとえば、**MyAppVpnProfile** です。

## <a name="step-2-create-a-custom-configuration-policy"></a>手順 2: カスタム構成ポリシーを作成する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **名前**: カスタム プロファイルのわかりやすい名前を入力します。 後で簡単に識別できるよう、プロファイルに名前を付けます。 たとえば、「**会社全体のカスタム OMA-URI Android VPN プロファイル**」は適切なプロファイル名です。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]** : **[Android]** を選択します。
    - **[プロファイルの種類]** : **[カスタム]** を選択します。

4. **[設定]**  >  **[構成]** の順に選択します。
5. **[OMA-URI のカスタム設定]** ウィンドウで、 **[追加]** を選択します。
    - **名前**: 設定の名前を入力します。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **OMA-URI**:「`./Vendor/MSFT/VPN/Profile/*Name*/PackageList`」と入力します。ここで *[名前]* は手順 1 でメモした接続名です。 この例では、文字列は `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList` です。
    - **[データ型]** :「**String**」と入力します。
    - **値**: プロファイルと関連付けるセミコロンで区切られたパッケージの一覧を入力します。 たとえば、Excel と Google Chrome ブラウザーで VPN 接続を使用するには、「`com.microsoft.office.excel;com.android.chrome`」と入力します。

![Android のアプリごとの VPN カスタム ポリシーの例](./media/android-pulse-secure-per-app-vpn/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>アプリの一覧をブラックリストまたはホワイトリストとして設定する (省略可能)

**BLACKLIST** 値を使用すると、VPN 接続を使用*できない*アプリの一覧を入力できます。 その他のすべてのアプリは、VPN 経由で接続します。 または、**WHITELIST** 値を使用し、VPN 接続を使用*できる*アプリの一覧を入力できます。 一覧に含まれないアプリは、VPN 経由で接続しません。

1. **[OMA-URI のカスタム設定]** ウィンドウで、 **[追加]** を選択します。
2. 設定の名前を入力します。
3. **OMA-URI** に「`./Vendor/MSFT/VPN/Profile/*Name*/Mode`」と入力します。 *[名前]* は手順 1 でメモした VPN プロファイル名です。 今回の例では、文字列は `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode` です。
4. **[データ型]** に「**String**」と入力します。
5. **[値]** に **[BLACKLIST]** または **[WHITELIST]** と入力します。

## <a name="step-3-assign-both-policies"></a>手順 3: 両方のポリシーを割り当てる

必要なユーザーまたはデバイスに[両方のデバイス プロファイルを割り当てます](device-profile-assign.md)。
