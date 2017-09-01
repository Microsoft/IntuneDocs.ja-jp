---
title: "デバイスの登録 - デバイス登録マネージャー"
titleSuffix: Intune on Azure
description: "デバイス登録マネージャー アカウントを使用してデバイスを Intune に登録します。 \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 204df4648f1d79167e8eb5941d91b48d65b90704
ms.sourcegitcommit: 4dc5bed94cc965a54eacac2d87fb2d49c9300c3a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2017
---
# <a name="enroll-devices-using-device-enrollment-manager"></a>デバイス登録マネージャーを使用してデバイスを登録する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

組織は Intune を使用して、単一のユーザー アカウントで多数のモバイル デバイスを管理することができます。 *デバイス登録マネージャー (DEM)* アカウントは、最大で 1,000 台のデバイスを登録できる特別なユーザー アカウントです。 既存のユーザーを DEM アカウントに追加し、特別な DEM 機能を与えます。 登録される各デバイスは 1 つのライセンスを使用します。 このアカウントで登録したデバイスは、個人用 ("BYOD") デバイスではなく共有デバイスとして使用することをお勧めします。  

ユーザーをデバイス登録マネージャーとして追加するには、そのユーザーが Azure Portal に存在する必要があります。 最適なセキュリティのために、DEM ユーザーを Intune 管理にも指定することは避けてください。

>[!NOTE]
>DEM による登録方法は、[Apple Configurator とセットアップ アシスタント](apple-configurator-setup-assistant-enroll-ios.md)、[Apple Configurator と直接登録](apple-configurator-direct-enroll-ios.md)、[Apple School Manager (ASM)](apple-school-manager-set-up-ios.md)、または [Device Enrollment Program (DEP)](device-enrollment-program-enroll-ios.md) という他の登録方法と一緒に使用することはできません。

## <a name="example-of-a-device-enrollment-manager-scenario"></a>デバイス登録マネージャーのシナリオの例

あるレストランで、接客担当スタッフが販売時点管理に使い、調理担当スタッフがオーダーのモニターに使う POS タブレットが 50 台必要になりました。 従業員は、会社のデータにアクセスしたり、ユーザーとしてサインインしたりする必要はありません。 Intune 管理者はデバイス登録マネージャー アカウントを作成し、レストランの監督者を DEM アカウントに追加し、DEM の機能を与えます。 これで監督者は DEM の資格情報を利用し、50 台のタブレット デバイスを登録できます。

Intune コンソール内のユーザーのみがデバイス登録マネージャーになることができます。 デバイス登録マネージャーのユーザーを Intune 管理者にすることはできません。

DEM ユーザーができること:

-   Intune に最大 1,000 台のデバイスを登録する
-   ポータル サイトにサインインして会社のアプリを取得する
-   タブレットにロール固有のアプリを展開することで、会社データへのアクセスを構成する

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>DEM アカウントで登録されるデバイスの制限事項

デバイス登録マネージャー アカウントを使用して登録されているデバイスには、次の制限があります。

  - ユーザーごとのアクセスはできません。 デバイスには割り当てられたユーザーがないため、電子メールや会社のデータ アクセスがありません。 VPN 構成などを使用すれば、デバイス アプリがデータにアクセスすることはできます。
  - これらのシナリオはユーザーごとであるため、条件付きのアクセスはできません。
  - DEM ユーザーは、会社ポータルを使用して、デバイス自体で DEM 登録のデバイスを登録解除することはできません。 Intune 管理者はこれができますが、DEM ユーザーはできません。
  - ポータル サイト アプリまたは Web サイトには、ローカルのデバイスのみが表示されます。
  - アプリ管理のための Apple ID 要件がユーザー単位になるため、ユーザーは Apple Volume Purchase Program (VPP) アプリを利用できません。
  - (iOS のみ) DEM を利用して iOS デバイスを登録する場合は、Apple Configurator、Apple Device Enrollment Program (DEP)、または Apple School Manager (ASM) を利用してデバイスを登録することはできません。
  - 各デバイスには、デバイスのライセンスが必要です。 [ユーザーとデバイスのライセンス](licenses-assign.md#how-user-and-device-licenses-affect-access-to-services)の詳細についてはこちらです。


> [!NOTE]
> デバイス登録マネージャーで管理されているデバイスに会社のアプリを展開するには、ポータル サイト アプリを**必須のインストール**としてデバイス登録マネージャーのユーザー アカウントに展開します。
> パフォーマンスを改善するために、DEM デバイスでポータル サイト アプリを表示すると、ローカル デバイスのみが表示されます。 その他の DEM デバイスのリモート管理は、Intune 管理コンソールからのみ実行できます。


## <a name="add-a-device-enrollment-manager"></a>デバイス登録マネージャーの追加

1.  Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2.  [Intune] ブレードで **[デバイスの登録]** を選択し、**[デバイス登録マネージャー]** を選択します。

3.  **[追加]** を選択します。

4.  **[ユーザーの追加]** ブレードで、DEM ユーザーのユーザー プリンシパル名を入力し、**[追加]** を選択します。 DEM ユーザーが DEM ユーザーの一覧に追加されます。

## <a name="permissions-for-dem"></a>DEM のアクセス許可

DEM 登録タスクを実行するには、グローバル管理者または Intune サービス管理者の Azure AD ロールが必要です。 また、これらのロールは、カスタムのユーザー ロールに一覧表示され使用可能である RBAC のアクセス許可に関係なく、すべての DEM ユーザーを表示するのに必要です。 グローバル管理者または Intune サービス管理者のロールが割り当てられていないユーザーで、デバイス登録マネージャー ロールの読み取りアクセス許可を持つユーザーは、自分が作成した DEM ユーザーのみ表示できます。 これらの機能の RBAC ロールのサポートについては、今後発表される予定です。

ユーザーにグローバル管理者または Intune サービス管理者のロールが割り当てられていないが、デバイス登録マネージャー ロールが割り当てられていてその読み取りアクセス許可を持っているという場合は、そのユーザー自身が作成した DEM ユーザーのみ表示できます。

## <a name="remove-a-device-enrollment-manager"></a>デバイス登録マネージャーの削除

デバイス登録マネージャーを削除しても、登録済みのデバイスに影響はありません。 デバイス登録マネージャーを削除した場合は次のようになります。

-   登録済みデバイスは影響を受けず、引き続き完全に管理されます。
-   削除されたデバイス登録マネージャー アカウントの資格情報は有効なままです。
-   削除されたデバイス登録マネージャーでは、デバイスのワイプとインベントリからの削除を実行できません。
-   削除されたデバイス登録マネージャーは、Intune 管理者によって構成されたデバイスを、ユーザーあたりの上限数まで登録することのみできます。

**デバイス登録マネージャーを削除するには**

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
2. [Intune] ブレードで **[デバイスの登録]** を選択し、**[デバイス登録マネージャー]** を選択します。
3. **[デバイス登録マネージャー]** ブレードで、DEM ユーザーを右クリックし、**[削除]** を選択します。

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>デバイス登録マネージャーのプロパティの表示

1. Intune ポータルで **[デバイスの登録]** を選択し、**[デバイス登録マネージャー]** を選択します。
2. **[デバイス登録マネージャー]** ブレードで、DEM ユーザーを右クリックし、**[プロパティ]** を選択します。
