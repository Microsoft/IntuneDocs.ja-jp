---
title: "モバイル デバイスの登録方法の選択 | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 06/06/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466
translationtype: Human Translation
ms.sourcegitcommit: f1dc713099c982d6e32c87b814dd3f55b1656eda
ms.openlocfilehash: 5668a4d8a6cce15446201926b03d71ede174a299


---

# モバイル デバイスの登録方法の選択

モバイル デバイス登録は、スマートフォン、タブレット、PC を Microsoft Intune で管理できるようにするためのプロセスです。 管理者は、デバイスの最適な登録方法を次の基準で決定する必要があります。

 -  所有権 (個人所有と 会社所有)
 -  使用方法 (共有と 個人使用)
 -  プラットフォーム (iOS、Android、Windows Phone、Windows PC、Mac PC) - 登録方法に基づいて選択

次の質問に答えることで、管理するデバイスの最適な登録方法が決まります。

## **社員が自分のデバイスを持ち込みますか。それとも、会社が提供しますか。**

  "Bring your own device" (BYOD) とも呼ばれる**、ユーザーが所有するデバイス**の登録の場合、デバイスを登録することで、ユーザーの電子メール、会社のアプリ、会社のデータ、サポートなどの会社のリソースにアクセスできるようになります。 **会社所有のデバイス** (COD) は、ビジネス ニーズに対処するために会社から社員に対して提供されます。
  > [!div class="button"]
  [BYOD 登録 >](#byod-device-enrollment)   [COD 登録 >](#cod-device-enrollment)

### BYOD デバイスの登録

BYOD 登録の場合、ユーザーは自分のデバイスに Intune ポータル サイト アプリをインストールする必要があります。 その後、アプリを起動し、職場や学校の資格情報を入力して登録します。 Intune でこれらの資格情報のライセンスが検出されると、デバイスが Intune 管理コンソールに追加され、Intune からポリシーを受け取り、会社のリソースにアクセスできるようになります。

**デバイスの種類を選択する:**
> [!div class="button"]
[Android](..deploy-use/set-up-android-management-with-microsoft-intune) [iOS と Mac](..deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 Mobile と Window Phone](..deploy-use/set-up-windows-phone-management-with-microsoft-intune) [Windows PC](..deploy-use/set-up-windows-device-management-with-microsoft-intune)


### COD デバイスの登録

会社所有のデバイス (COD) を登録すると、特定のユーザー専用にしたり、複数のユーザー間で共有したりできます。  **共有デバイス**は、利用者が 1 名ではなく、通常、電子メールにアクセスできるように設定されません。 たとえば、キオスク デバイスやタスク指向デバイスなどがあります。利用者が必要に応じてプールから取り出し、利用後に返却します。 推奨される登録方法は、デバイスのプラットフォームにより異なります。 **専用デバイス**は、ユーザーごとに支給される会社所有デバイスは会社の資産として追跡記録する必要があります。利用者は個人のデバイスとして電子メールやデータにアクセスできます。 推奨される登録方法は、デバイスのプラットフォームにより異なります。 [次の質問...](Are your company-owned devices shared or do they have dedicated users?)

## **会社所有デバイスを共有しますか。デバイスごとに専用の利用者が登録されますか。**

> [!div class="button"]
[共有 >](#Shared-company-owned-devices)   [専用 >](..deploy-use/get-ready-to-enroll-devices-in-microsoft-intune)


### 会社所有の共有デバイス

これらのデバイスは、利用者が 1 名ではなく、通常、電子メールにアクセスできるように設定されていません。 たとえば、キオスク デバイスやタスク指向デバイスなどがあります。利用者が必要に応じてプールから取り出し、利用後に返却します。 推奨される登録方法は、デバイスのプラットフォームにより異なります。

  - **Windows デバイスと Android デバイス** - *デバイス登録マネージャー*は、ポータル サイト アプリによるさまざまな共有デバイスの登録に利用できる Intune アカウントです。
  > [!div class="button"]
  [Windows >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#shared-ios-device-enrollment)

### 共有 iOS デバイスの登録

会社所有の共有 iOS デバイスの登録に推奨される方法は、デバイスの購入方法や管理方法によって異なります。

  - **Apple のデバイス登録プログラム (DEP)** - DEP で購入し、管理している iOS デバイスが対象となります。登録プロファイルが利用されます。 利用者がデバイスの電源を初めて入れると、デバイスが DEP プロファイルをダウンロードし、プロファイル DEP で登録します。
  - **Mac の Apple Configurator (Mac)** - Apple Configurator は Mac PC で実行される Apple アプリケーションです。 USB ケーブルで iOS デバイスを Mac に接続し、デバイスに登録プロファイルをインストールできます。 デバイスを工場出荷時にリセットして登録できる場合、セットアップ アシスタント登録を使用します。 デバイスを工場出荷時にリセットしない場合、直接登録を使用します。
  - **上記のいずれにも該当しない** - Apple の DEP も Apple Configurator も登録方法として利用できない、または利用が好ましくない場合、Intune のデバイス登録マネージャーを利用します。

  **選択:**
    > [!div class="button"]
     [DEP 登録 >](../deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Mac >](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [直接登録 >](../deploy-use/ios-direct-enrollment-in-microsoft-intune)  

  > [!div class="button"]
    [DEM 登録 >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

**個別ユーザー** - ユーザーごとに支給される会社所有デバイスは会社の資産として追跡記録する必要があります。利用者は個人のデバイスとして電子メールやデータにアクセスできます。 推奨される登録方法は、デバイスのプラットフォームにより異なります。

  - **Windows デバイスと Android デバイス** - 会社所有デバイスの IMEI (携帯機器の国際的な識別番号) をインポートすることで、Intune でデバイスに会社所有のタグを付けることができます。 その後、ポータル サイトをインストールし、デバイスを個人デバイスとして登録し、電子メール、アプリ、データなど、会社のリソースにアクセスできます。
  > [!div class="button"]
  [IMEI によるタグ付け >](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  - **iOS デバイス** - 共有する iOS デバイスを 3 通りの方法で管理できます。  **共有 iOS デバイスはどのような方法で登録しますか。**

    - **Apple のデバイス登録プログラム (DEP)** - DEP で購入し、管理している iOS デバイスが対象となります。登録プロファイルが利用されます。 利用者がデバイスの電源を初めて入れると、デバイスが DEP プロファイルをダウンロードし、プロファイルに基づいて登録されます。
    > [!div class="button"]
    [DEP 登録](../deploy-use/ios-device-enrollment-program-in-microsoft-intune)

    - **Mac の Apple Configurator** - Apple Configurator は Mac PC で実行される Apple アプリケーションです。 USB ケーブルで iOS デバイスを Mac に接続し、デバイスに登録プロファイルをインストールできます。 デバイスを工場出荷時にリセットして登録できる場合、セットアップ アシスタント登録を使用します。

    デバイスを工場出荷時にリセットしない場合、直接登録を使用します。
    デバイスを工場出荷時にリセットして登録できる場合、セットアップ アシスタント登録を使用します。
    > [!div class="button"][iOS Setup Assistant enrollment](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [!div class="button"][iOS direct enrollment](../deploy-use/ios-direct-enrollment-in-microsoft-intune).

    - **上記のいずれも** - Apple の DEP も Apple Configurator も登録方法として利用できない、または利用が好ましくない場合、会社所有デバイスの IMEI (携帯機器の国際的な識別番号) をインポートすることで、Intune でデバイスに会社所有のタグを付けることができます。 その後、ポータル サイトをインストールし、デバイスを個人デバイスとして登録し、電子メール、アプリ、データなど、会社のリソースにアクセスできます。
    > [!div class="button"][Tag devices with IMEI numbers](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)



<!--HONumber=Jun16_HO5-->


