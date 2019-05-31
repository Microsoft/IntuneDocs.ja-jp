---
title: Intune で Android Enterprise 仕事用プロファイル デバイスを登録する
titleSuffix: Microsoft Intune
description: Intune で Android Enterprise 仕事用プロファイル デバイスを登録する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66574fe66f90b73d8ebf5835c5b16e93276579e4
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568220"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Android Enterprise 仕事用プロファイル デバイスの登録を設定する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune を使用すると、アプリと設定を Android Enterprise 仕事用プロファイル デバイスに展開し、仕事の情報と個人の情報を分けることができます。 Android Enterprise に関する特定の詳細については、「[Android Enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)」 (Android Enterprise の要件) を参照してください。

Android Enterprise 仕事用プロファイル管理を設定するには、次の手順を行います。

1. [Android Enterprise アカウントに Intune テナント アカウントを接続します](connect-intune-android-enterprise.md)。
2. Android Enterprise 仕事用プロファイルの登録設定を指定します。 Android Enterprise 仕事用プロファイルは、[特定の Android デバイスでのみサポートされています](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22)。 Android Enterprise 仕事用プロファイルをサポートするすべてのデバイスでは、従来の Android 管理もサポートされます。 Intune では、Android Enterprise 仕事用プロファイルをサポートするデバイスを[登録制限](enrollment-restrictions-set.md)内から管理する方法を指定できます。
    - **ブロック (既定で設定)** :Android Enterprise 仕事用プロファイルをサポートするデバイスを含め、すべての Android デバイスが従来の Android デバイスとして登録されます。
    - **[許可]** :Android Enterprise 仕事用プロファイルをサポートするすべてのデバイスが Android 仕事用プロファイル デバイスとして登録されます。 Android Enterprise 仕事用プロファイルをサポートしないすべての Android デバイスは、従来の Android デバイスとして登録されます。
3. [デバイスを登録する方法をユーザーに知らせます](/intune-user-help/enroll-your-device-in-intune-android)。


以前は通常の Android デバイスとして登録されていたデバイスを Android Enterprise 仕事用プロファイルを使用して登録するには、まずデバイスの登録を解除してから再登録する必要があります。

[デバイス登録マネージャー](device-enrollment-manager-enroll.md) アカウントを使用して Android Enterprise 仕事用プロファイル デバイスを登録する場合、アカウントあたりの登録可能なデバイスは 10 台に制限されます。

詳細については、「[Intune から Google に送られるデータ](data-intune-sends-to-google.md)」を参照してください。

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>managed Google Play ストアで Intune ポータル サイト アプリを承認する

常にユーザーが Intune ポータル サイト アプリの最新バージョンにアクセスするように、managed Google Play ストアで Android 用 Intune ポータル サイト アプリを承認する必要があります。 承認すると、各ユーザーが自動更新を受け取るようにすることができます。 アプリを承認しないと、ポータル サイトはいずれ使われていない状態になってしまい、Microsoft からリリースされた重要なバグ修正プログラムや新しい機能を受け取らなくなることがあります。

Intune ポータル サイトを承認するには、次の手順のようにします。

1.  [managed Google Play ストア](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal)で Intune ポータル サイト アプリを参照します。
2.  Android エンタープライズのバインディングを構成するときに使ったものと同じ Google アカウントで、managed Google Play ストアにサインインします。
3.  **[承認]** をクリックすると、新しいダイアログが開きます。
4.  このダイアログでアクセス許可を確認し、 **[承認]** をクリックします。 ポータル サイト アプリがデバイスの仕事用プロファイルを管理できるようにするには、これらのアクセス許可を許可する必要があります。
5.  **[Keep approved when app requests new permissions]\(アプリが新しいアクセス許可を要求したときに承認済みのままにする\)** を選び、 **[保存]** をクリックします。

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Android Enterprise 仕事用プロファイルの次の手順
- [Android Enterprise 仕事用プロファイル アプリを展開する](apps-add-android-for-work.md)
- [Android Enterprise 仕事用プロファイル構成ポリシーを追加する](device-profiles.md)
