---
title: Intune で Android Enterprise 仕事用プロファイル デバイスを登録する
titleSuffix: Microsoft Intune
description: Intune で Android Enterprise 仕事用プロファイル デバイスを登録する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c447b6b21021573d95a5ece3297e548f216b7a0
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723529"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Android Enterprise 仕事用プロファイル デバイスの登録を設定する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune を使用すると、アプリと設定を Android Enterprise 仕事用プロファイル デバイスに展開し、仕事の情報と個人の情報を分けることができます。 Android Enterprise に関する特定の詳細については、「[Android Enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)」 (Android Enterprise の要件) を参照してください。

Android Enterprise 仕事用プロファイル管理を設定するには、次の手順を行います。

1. [Android Enterprise アカウントに Intune テナント アカウントを接続します](connect-intune-android-enterprise.md)。
2. Android Enterprise 仕事用プロファイルの登録設定を指定します。 Android Enterprise 仕事用プロファイルは、[特定の Android デバイスでのみサポートされています](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22)。 Android Enterprise 仕事用プロファイルをサポートするすべてのデバイスでは、Android デバイス管理者の管理もサポートされます。 Intune では、Android Enterprise 仕事用プロファイルをサポートするデバイスを[登録制限](enrollment-restrictions-set.md)内から管理する方法を指定できます。
    - **[ブロック]** :Android デバイス管理者登録もブロックされていない限り、Android Enterprise 仕事用プロファイルをサポートするデバイスを含め、すべての Android デバイスが Android デバイス管理者デバイスとして登録されます。 
    - **許可 (既定で設定)** :Android Enterprise 仕事用プロファイルをサポートするすべてのデバイスが Android 仕事用プロファイル デバイスとして登録されます。 Android デバイス管理者登録がブロックされていない限り、Android Enterprise 仕事用プロファイルをサポートしていないすべての Android デバイスが Android デバイス管理者デバイスとして登録されます。 
> [!NOTE]
> 2019 年 7 月以降の新しいテナントでは、既定で **[許可]** に設定されます。 以前のすべてのテナントでは、登録制限に対する変更は発生せず、登録制限に設定されているすべてのポリシーが表示されます。 登録制限の変更が行われていない以前のテナントでは、Android Enterprise 仕事用プロファイルの既定値は **[ブロック]** のままです。

3. [デバイスを登録する方法をユーザーに知らせます](/intune-user-help/create-a-work-profile-and-enroll-your-device-in-intune-android)。  

以前は Android デバイス管理者によって登録されていたデバイスを Android Enterprise 仕事用プロファイルを使用して登録するには、デバイスの登録を解除してから再登録する必要があります。
> [!NOTE]
> 管理者として **[削除]** 機能を使用して、リモートでこれを実行できます。 この機能は、 **[すべてのデバイス]** ブレードからデバイスを選択した後、[アクション] メニューで見つけることができます。

[デバイス登録マネージャー](device-enrollment-manager-enroll.md) アカウントを使用して Android Enterprise 仕事用プロファイル デバイスを登録する場合、アカウントあたりの登録可能なデバイスは 10 台に制限されます。

詳細については、「[Intune から Google に送られるデータ](../protect/data-intune-sends-to-google.md)」を参照してください。

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Android Enterprise 仕事用プロファイルの次の手順
- [Android Enterprise 仕事用プロファイル アプリを展開する](../apps/apps-add-android-for-work.md)
- [Android Enterprise 仕事用プロファイル構成ポリシーを追加する](../configuration/device-profiles.md)

## <a name="see-also"></a>関連項目

[Microsoft Intune での Android Enterprise デバイスの構成とトラブルシューティング](https://support.microsoft.com/help/4476974)
