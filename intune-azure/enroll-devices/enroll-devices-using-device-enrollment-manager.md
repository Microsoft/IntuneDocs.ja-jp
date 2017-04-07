---
title: "デバイスの登録 - デバイス登録マネージャー"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: デバイス登録マネージャー アカウントを使用して Intune にデバイスを登録します。 "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: b4629d98f935ab2fac95144940e2a58a1b1e7c5c
ms.lasthandoff: 02/18/2017

---

# <a name="enroll-devices-using-device-enrollment-manager"></a>デバイス登録マネージャーを使用してデバイスを登録する

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

組織は Intune を使用して、単一のユーザー アカウントで多数のモバイル デバイスを管理することができます。 *デバイス登録マネージャー (DEM)* アカウントは、最大で 1,000 台のデバイスを登録できる特別なユーザー アカウントです。 既存のユーザーを DEM アカウントに追加し、特別な DEM 機能を与えます。 登録される各デバイスは&1; つのライセンスを使用します。 このアカウントで登録したデバイスは、個人用 ("BYOD") デバイスではなく共有デバイスとして使用することをお勧めします。  

ユーザーをデバイス登録マネージャーとして追加するには、そのユーザーが Azure Portal に存在する必要があります。 最適なセキュリティのために、DEM ユーザーを Intune 管理にも指定することは避けてください。

>[!NOTE]
>DEM による登録方法は、[Apple Configurator とセットアップ アシスタント](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)、[Apple Configurator と直接登録](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md)、または [Device Enrollment Program](enroll-ios-devices-using-device-enrollment-program.md) という他の登録方法と一緒に使用することはできません。 

## <a name="example-of-a-device-enrollment-manager-scenario"></a>デバイス登録マネージャーのシナリオの例

あるレストランで、接客担当スタッフが販売時点管理に使い、調理担当スタッフがオーダーのモニターに使う POS タブレットが 50 台必要になりました。 従業員は、会社のデータにアクセスしたり、ユーザーとしてサインインしたりする必要はありません。 Intune 管理者はデバイス登録マネージャー アカウントを作成し、レストランの監督者を DEM アカウントに追加し、DEM の機能を与えます。 これで監督者は DEM の資格情報を利用し、50 台のタブレット デバイスを登録できます。

Intune コンソール内のユーザーのみがデバイス登録マネージャーになることができます。 デバイス登録マネージャーのユーザーを Intune 管理者にすることはできません。

DEM ユーザーができること:

-   Intune に最大 1,000 台のデバイスを登録する。
-   ポータル サイトにサインインして会社のアプリを取得する。
-   タブレットにロール固有のアプリを展開することで、会社データへのアクセスを構成する。

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>DEM アカウントで登録されるデバイスの制限事項

デバイス登録マネージャー アカウントを使用して登録されているデバイスには、次の制限があります。

  - 具体的なデバイス "ユーザー" は存在しません。 そのため、電子メールや会社のデータへのアクセスがありません。 ただし、VPN などを使用してデバイス アプリからデータにアクセスすることはできます。

  - シナリオはユーザーごとになるため、条件付きアクセスはありません。

  - DEM ユーザーは、会社ポータルを使用して、デバイス自体で DEM 登録のデバイスを登録解除することはできません。 Intune 管理者にはこの機能が与えられますが、DEM ユーザーはこの機能を使用できません。

  - ポータル サイト アプリまたは Web サイトには、ローカルのデバイスのみが表示されます。
 
  - アプリ管理のための Apple ID 要件がユーザー単位になるため、ユーザーは Apple Volume Purchase Program (VPP) アプリを利用できません。
 
  - (iOS のみ) DEM を利用して iOS デバイスを登録する場合、Apple Configurator またはデバイス登録プログラム (DEP) を利用してデバイスを登録することはできません。


> [!NOTE]
> デバイス登録マネージャーで管理されているデバイスに会社のアプリを展開するには、ポータル サイト アプリを**必須のインストール**としてデバイス登録マネージャーのユーザー アカウントに展開します。
> パフォーマンスを改善するために、DEM デバイスでポータル サイト アプリを表示すると、ローカル デバイスのみが表示されます。 その他の DEM デバイスのリモート管理は、Intune 管理コンソールからのみ実行できます。


## <a name="add-a-device-enrollment-manager"></a>デバイス登録マネージャーの追加

1.  Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2.  [Intune] ブレードで **[デバイスの登録]** を選択し、**[デバイス登録マネージャー]** を選択します。

3.  **[追加]** を選択します。

4.  **[ユーザーの追加]** ブレードで、DEM ユーザーのユーザー プリンシパル名を入力し、**[追加]** を選択します。 DEM ユーザーが DEM ユーザーの一覧に追加されます。

## <a name="remove-a-device-enrollment-manager"></a>デバイス登録マネージャーの削除

デバイス登録マネージャーを削除しても、登録済みのデバイスに影響はありません。 デバイス登録マネージャーを削除した場合は次のようになります。

-   DEM ユーザーの一覧からユーザーを削除しても登録済みのデバイスには影響がなく、登録済みデバイスは引き続き完全に管理されます。

-   削除されたデバイス登録マネージャー アカウントの資格情報は有効なままです。

-   削除されたデバイス登録マネージャーでは、デバイスのワイプとインベントリからの削除を実行できません。

-   削除されたデバイス登録マネージャーは、追加のデバイスを登録できません。ただし、Intune 管理者によって構成されたデバイスごとの制限に達していない場合を除きます。

**デバイス登録マネージャーを削除するには**

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. [Intune] ブレードで **[デバイスの登録]** を選択し、**[デバイス登録マネージャー]** を選択します。

3. **[デバイス登録マネージャー]** ブレードで、DEM ユーザーを右クリックし、**[削除]** を選択します。

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>デバイス登録マネージャーのプロパティの表示

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. [Intune] ブレードで **[デバイスの登録]** を選択し、**[デバイス登録マネージャー]** を選択します。

3. **[デバイス登録マネージャー]** ブレードで、DEM ユーザーを右クリックし、**[プロパティ]** を選択します。

