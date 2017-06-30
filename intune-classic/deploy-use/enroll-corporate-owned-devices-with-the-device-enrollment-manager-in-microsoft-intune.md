---
title: "デバイス登録マネージャーを使用して登録する"
description: "デバイス登録マネージャー (DEM) アカウントでは、1 つのユーザー アカウントで企業所有の多数の共有モバイル デバイスを管理できます。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 095b89d1428d6b8f06143043d8bb6ed37fd8fa5b
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---


# <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune"></a>Microsoft Intune のデバイス登録マネージャーを使用した企業所有デバイスの登録

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

組織は Intune を使用して、単一のユーザー アカウントで多数のモバイル デバイスを管理することができます。 *デバイス登録マネージャー (DEM)* アカウントは、最大で 1,000 台のデバイスを登録できる特別なユーザー アカウントです。 既存のユーザーを DEM アカウントに追加し、特別な DEM 機能を与えます。 登録される各デバイスは 1 つのライセンスを使用します。 このアカウントで登録したデバイスは、個人用 ("BYOD") デバイスではなく共有デバイス (つまり、ユーザー アフィニティなし) として使用することをお勧めします。  

ユーザーをデバイス登録マネージャーとして追加するには、そのユーザーが Azure Portal に存在する必要があります。 最適なセキュリティのために、DEM ユーザーを Intune 管理にも指定することは避けてください。

>[!NOTE]
>DEM の登録方法は、[Apple Configurator セットアップ アシスタント](ios-setup-assistant-enrollment-in-microsoft-intune.md)、[直接登録](ios-direct-enrollment-in-microsoft-intune.md)、または [DEP の登録方法](ios-device-enrollment-program-in-microsoft-intune.md)と同時に使用することはできません。

## <a name="example-of-a-device-enrollment-manager-scenario"></a>デバイス登録マネージャーのシナリオの例

あるレストランで、接客担当スタッフが販売時点管理に使い、調理担当スタッフがオーダーのモニターに使う POS タブレットが 50 台必要になりました。 従業員は、会社のデータにアクセスしたり、ユーザーとしてサインインしたりする必要はありません。 Intune 管理者はデバイス登録マネージャー アカウントを作成し、レストランの監督者を DEM アカウントに追加し、DEM の機能を与えます。 これで監督者は DEM の資格情報を利用し、50 台のタブレット デバイスを登録できます。

Intune コンソール内のユーザーのみがデバイス登録マネージャーになることができます。 デバイス登録マネージャーのユーザーを Intune 管理者にすることはできません。

DEM ユーザーができること:

-   Intune に最大 1,000 台のデバイスを登録する
-   会社のポータル アプリを使用して会社のアプリを取得する
-   タブレットにロール固有のアプリを展開することで、会社データへのアクセスを構成する

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

1.  DEM アカウントに追加するユーザーが既に存在することを確認します。 ユーザーを追加する必要がある場合、[Office 365 ポータル](https://go.microsoft.com/fwlink/p/?LinkId=698854)にサインインし、「[Office 365 にユーザーを個別に、またはまとめて追加する - 管理者向けヘルプ](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec)」の手順を実行します。

2.  管理者の資格情報を使用して、[Microsoft Intune 管理コンソール](https://manage.microsoft.com) にサインインします。

3.  ナビゲーション ウィンドウで、**[管理]**、**[管理者の管理]** の順に選択し、**[デバイス登録マネージャー]** を選択します。 **[デバイス登録マネージャー]** ページが表示されます。

4.  **[追加]** を選択します。 **[デバイス登録マネージャーの追加]** ダイアログ ボックスが表示されます。

5.  Intune アカウントを **[ユーザー ID]** に入力し、**[OK]** を選択します。

    これで、DEM ユーザーが、BYOD シナリオの場合にエンド ユーザーがポータル サイトで実行する際と同じ手順で、モバイル デバイスを登録できるようになりました。 マネージャーであるエンド ユーザーは、ポータル サイト アプリをインストールし、DEM の資格情報を使用して最大 1,000 台のデバイスを登録することができます。 プラットフォーム別のエンドユーザー登録手順については、次を参照してください。

  - [Intune に iOS デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)
  - [Intune に macOS デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)
  - [Intune に Android デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)
  - [Intune に Windows デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)

## <a name="delete-a-device-enrollment-manager-from-intune"></a>Intune からのデバイス登録マネージャーの削除

1.  管理者の資格情報を使用して、[Microsoft Intune 管理ポータル](https://manage.microsoft.com)にサインインします。

2.  ナビゲーション ウィンドウで、**[管理]**、**[管理者の管理]** の順に選択し、**[デバイス登録マネージャー]** を選択します。 **[デバイス登録マネージャー]** ページが表示されます。

3.  削除するデバイス登録マネージャーの **[ユーザー]** を選択し、**[削除]** を選択します。 このユーザーは Intune から削除されません。このユーザーが管理するデバイスは Intune で登録されたままになります。 デバイス登録マネージャーを削除することにより、Intune でユーザーがデバイスをそれ以上追加できないようにします。

4.  **[はい]** を選択して、デバイス登録マネージャーを削除することを確認します。

デバイス登録マネージャーを削除していも、登録済みのデバイスに影響はありません。 デバイス登録マネージャーを削除した場合:

-   登録済みデバイスに影響はありません。

-   登録済みデバイスは引き続き完全に管理されます。

-   削除されたデバイス登録マネージャー アカウントの資格情報は有効なままなので、ポータル サイトにサインインしてアプリにアクセスできます。

-   削除されたデバイス登録マネージャー アカウントの資格情報では、デバイスのワイプとインベントリからの削除を実行できません。

-   削除されたデバイス登録マネージャー アカウントと登録済みデバイスの関係は残りますが、追加のデバイスは登録できません。

