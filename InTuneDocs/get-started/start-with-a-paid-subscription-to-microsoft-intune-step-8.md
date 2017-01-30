---
title: "デバイス登録を有効にする | Microsoft Docs"
description: "MDM 機関を設定し、iOS、Windows、Android、および Mac の各デバイスの登録を有効にします。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 654c5b65a9fde6742f3682b1fd5ba6c056d0d45b


---

# <a name="enroll-mobile-devices-and-install-an-app"></a>モバイル デバイスを登録してアプリをインストールする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune でモバイル デバイス管理をセットアップするには、まず、*モバイル デバイス管理機関*を設定する必要があります。この機関は、アカウントに関連付けられているデバイスを管理できるサービスを特定します。 このガイダンスでは、System Center Configuration Manager ではなく、Intune サービスを使用することを想定します。 MDM 機関を設定したら、デバイス プラットフォームの管理を有効にし、デバイスをポータル サイト アプリに登録できます。

## <a name="enable-device-enrollment"></a>デバイスの登録を可能にする

1. **Intune をモバイル デバイス管理機関にする**
    [Intune 管理コンソール](https://manage.microsoft.com/)で、**[管理者]** > **[モバイル デバイス管理]** の順に選択し、**[タスク]** で **[MDM 機関の設定]** を選択します。  

2. MDM 機関ダイアログ ボックスで **[はい]** をクリックします。

    ![管理コンソール。 MDM を Intune に設定](./media/mdmAuthority.png)

## <a name="choose-how-to-enroll-devices"></a>デバイスの登録方法の選択

Intune では、会社の要件に応じて、さまざまな方法でデバイスを管理できます。 使用できる登録シナリオは "Bring Your Own Device" (BYOD)、企業所有デバイス、"Choose Your Own Device" (CYOD)、およびキオスク モード デバイスです。

以下の手順に従って、[デバイスの登録方法を選択](choose-how-to-enroll-devices1.md)します。

## <a name="enable-mdm-for-your-device-platform"></a>デバイス プラットフォームの MDM を有効にする
プラットフォーム プロバイダーと Intune テナント間の関係を確立して、iOS、Mac、および Android for Work デバイスの登録を有効にする必要があります。 Windows および Android デバイスには追加の手順は必要ありませんが、Windows デバイスの場合、特別な DNS レジストリ エントリを作成して、ユーザーのデバイス登録を簡略化することができます。

管理対象のデバイス プラットフォームに対してデバイス管理を有効にします。 要件はプラットフォームによって異なります。

-  [iOS と macOS](https://docs.microsoft.com/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune.md)
-  [Windows PC](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)
-  [Windows 10 Mobile と Windows Phone](https://docs.microsoft.com/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune)
- [Android for Work](https://docs.microsoft.com/intune/deploy-use/set-up-android-for-work)

登録が有効になったら、ユーザーは自分のデバイスにポータル サイト アプリをダウンロードして、デバイス登録プロセスを完了できます。

### <a name="enable-company-owned-device-enrollment"></a>会社所有のデバイス登録を有効にする
次のような、[会社所有のデバイス登録](https://docs.microsoft.com/intune/deploy-use/manage-corporate-owned-devices)シナリオを有効にすることもできます。
- [Apple Device Enrollment Program](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
- [Apple Configurator セットアップ アシスタントでの登録](https://docs.microsoft.com/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
- [Apple Configurator セットアップ アシスタントでの登録](https://docs.microsoft.com/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)
- [デバイス登録マネージャー](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

### <a name="next-steps"></a>次のステップ
これで終了です。 *Intune のクイック スタート ガイド*の最後の手順が完了しました。 これで初期構成が完了したので、追加の MDM 機能の有効化を検討できます。

>[!div class="step-by-step"]

>[&larr; **デバイスを登録する**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)     [**構成後のタスク** &rarr;](.\post-configuration-tasks.md)  



<!--HONumber=Dec16_HO2-->


