---
title: "デバイスの登録を可能にする"
description: "MDM 機関を設定し、iOS、Windows、Android、および Mac の各デバイスの登録を有効にします。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 64c6eb58246ac3ad232c1b8ee89d12a83e7e1784
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="enable-enrollment-for-mobile-devices"></a>モバイル デバイスの登録を有効にする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

このトピックでは、Intune 管理者がモバイル デバイスの登録を有効にする方法について説明します。 電話で Intune の使用する際のヘルプについては、[管理デバイスを使用した作業の完了](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions)に関するページを参照してください。

Intune でモバイル デバイス管理をセットアップするには、まず、*モバイル デバイス管理機関*を設定する必要があります。この機関は、アカウントに関連付けられているデバイスを管理できるサービスを特定します。 このガイダンスでは、System Center Configuration Manager ではなく、Intune サービスを使用することを想定します。 MDM 機関を設定したら、デバイス プラットフォームの管理を有効にし、デバイスをポータル サイト アプリに登録できます。

## <a name="enable-device-enrollment"></a>デバイスの登録を可能にする

1. **Intune をモバイル デバイス管理機関にする**
    [Intune 管理コンソール](https://manage.microsoft.com/)で、**[管理者]** > **[モバイル デバイス管理]** の順に選択し、**[タスク]** で **[MDM 機関の設定]** を選択します。  

2. MDM 機関ダイアログ ボックスで **[はい]** をクリックします。

    ![管理コンソール。 MDM を Intune に設定](../media/intune-mdm-authority.png)

## <a name="choose-how-to-enroll-devices"></a>デバイスの登録方法の選択

Intune では、会社の要件に応じて、さまざまな方法でデバイスを管理できます。 使用できる登録シナリオは "Bring Your Own Device" (BYOD)、企業所有デバイス、"Choose Your Own Device" (CYOD)、およびキオスク モード デバイスです。

以下の手順に従って、[デバイスの登録方法を選択](choose-how-to-enroll-devices1.md)します。

## <a name="enable-mdm-for-your-device-platform"></a>デバイス プラットフォームの MDM を有効にする
プラットフォーム プロバイダーと Intune テナント間の関係を確立して、iOS、Mac、および Android for Work デバイスの登録を有効にする必要があります。 Windows および Android デバイスには追加の手順は必要ありませんが、Windows デバイスの場合、特別な DNS レジストリ エントリを作成して、ユーザーのデバイス登録を簡略化することができます。

管理対象のデバイス プラットフォームに対してデバイス管理を有効にします。 要件はプラットフォームによって異なります。

- [iOS と macOS](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
- [Windows 10 および Windows Phone](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune)
- [Window PC](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) (Intune ソフトウェア クライアント)
- [Android for Work](/intune-classic/deploy-use/set-up-android-for-work)

登録が有効になったら、ユーザーは自分のデバイスにポータル サイト アプリをダウンロードして、デバイス登録プロセスを完了できます。

### <a name="enable-company-owned-device-enrollment"></a>会社所有のデバイス登録を有効にする
次のような、[会社所有のデバイス登録](/intune-classic/deploy-use/manage-corporate-owned-devices)シナリオを有効にすることもできます。
- [Apple Device Enrollment Program](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
- [Apple Configurator セットアップ アシスタントでの登録](/intune-classic/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
- [Apple Configurator の直接登録](/intune-classic/deploy-use/ios-direct-enrollment-in-microsoft-intune)
- [デバイス登録マネージャー](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

### <a name="next-steps"></a>次のステップ
これで終了です。 *Intune のクイック スタート ガイド*の最後の手順が完了しました。 これで初期構成が完了したので、追加の MDM 機能の有効化を検討できます。

>[!div class="step-by-step"]
>[&larr; **デバイスを登録する**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)     [**構成後のタスク** &rarr;](.\post-configuration-tasks.md)  

