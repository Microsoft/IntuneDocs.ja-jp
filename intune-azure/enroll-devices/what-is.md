---
title: "Microsoft Intune デバイス登録とは | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: iOS、Android、Windows デバイスの登録について説明します。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/26/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 10cf9980468eff912557747c31994747c17a3ab4
ms.openlocfilehash: 01bf32ef874385019ea4b0fb0ce278554459287d


---

# <a name="what-is-device-enrollment"></a>デバイス登録とは
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

このトピックでは登録について説明します。また、Intune 管理でモバイル デバイスを登録する方法をいくつか紹介します。

Intune で Windows PC などのデバイスを登録し、それらのデバイスを管理できるようにします。 この機能は、Intune ドキュメントでは、モバイル デバイス管理 (MDM) と呼ばれます。 デバイスを (PC ではなく) モバイル デバイスとして登録すると、MDM 証明書が発行されます。デバイスは、この証明書を使用して Intune サービスと通信します。 

デバイスの登録方法は、デバイスの種類、所有権、必要な管理レベルによって決まります。 "Bring Your Own Device" (BYOD) の登録では、ユーザーは個人で所有するスマートフォン、タブレット、PC を登録できます。 会社が所有しているデバイス (COD) の登録では、自動登録、共有デバイス、事前承認された登録要件などの管理シナリオが有効になります。

オンプレミスの、またはクラウドでホストされている Exchange ActiveSync を使用すると、登録を必要としない簡単な Intune 管理が可能です (詳細は近日公開予定)。 Windows PC はモバイル デバイスとして管理できます (推奨)。この方法については以下で説明します。 また、[Intune クライアント ソフトウェア](https://docs.microsoft.com/intune/deploy-use/manage-windows-pcs-with-microsoft-intune)を使用して PC として管理することもできます。


## <a name="overview-of-device-enrollment-methods"></a>デバイスの登録方法の概要

次の表は、Intune の登録方法とサポートされる機能、各方法の要件の一覧です。 また、機能と要件について説明しています。 ここで使用される用語を次に示します。

- **ワイプ** - ユーザーがデバイスを登録する前に、デバイスのワイプが必要かどうかを示します。 "ワイプ" という用語は、デバイスを出荷時の設定にリセットし、すべてのデータを削除することを意味します。 詳細については、[デバイスでのフル ワイプまたは選択的ワイプの使用](/intune-azure/manage-devices/use-full-or-selective-wipe-on-devices-using-microsoft-intune)に関するページを参照してください。
- **アフィニティ** - デバイスとユーザーを関連付けます。 モバイル アプリケーション管理 (MAM) および会社データへの条件付きアクセスのために必要です。 詳細については、「[ユーザー アフィニティ](enroll-ios-devices-using-device-enrollment-program.md)」を参照してください。
- **ロック** - ユーザーが管理メニューから自分のデバイスを登録解除できるかどうかを示します。 ユーザーは、ポータル サイト アプリを使用してすべてのプラットフォームで自分のデバイスを登録解除できます。 ネイティブのオペレーティング システムのメニューでは登録解除ができません。


**iOS の登録方法**

| **方法** |  **ワイプが必要?** |    **アフィニティ**    |   **ロック** | **詳細** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | いいえ|    ○ |   いいえ | 詳細は近日公開予定|
|**[DEM](#dem)**|   いいえ |いいえ |いいえ  | [詳細情報](enroll-ios-devices-using-device-enrollment-program.md)|
|**[DEP](#dep)**|   Yes |   省略可能 |  省略可能|[詳細情報](enroll-ios-devices-using-device-enrollment-program.md)|
|**[USB-SA](#usb-sa)**| Yes |   省略可能 |  いいえ| [詳細情報](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)|
|**[USB-Direct](#usb-direct)**| いいえ |    いいえ  | いいえ|[詳細情報](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md)|



**Windows の登録方法**

| **方法** |  **ワイプが必要?** |    **アフィニティ**    |   **ロック** | **詳細**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | [はい]|   ○ |   いいえ | 詳細は近日公開予定|
|**[DEM](#dem)**|   いいえ |いいえ |いいえ  |[詳細情報](enroll-devices-using-device-enrollment-manager.md)|

**Android の登録方法**

| **方法** |  **ワイプが必要?** |    **アフィニティ**    |   **ロック** | **詳細**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | いいえ|    ○ |   いいえ | 詳細は近日公開予定|
|**[DEM](#dem)**|   いいえ |いいえ |いいえ  |[詳細情報](enroll-ios-devices-using-device-enrollment-program.md)|


## <a name="byod"></a>BYOD
"Bring your own device" はユーザーがポータル サイト アプリをインストールし、自分のデバイスを登録します。 これにより、ユーザーは会社のネットワークに接続して、ドメインまたは Azure Active Directory に参加できます。 ほとんどのプラットフォームで、多くの COD シナリオのために BYOD 登録を有効にする必要があります。

## <a name="corporate-owned-devices"></a>企業所有のデバイス
企業所有のデバイス (COD) は、Azure Portal を利用して管理できます。 iOS デバイスは、Apple が提供するツールを利用して直接登録できます。 管理者またはマネージャーは、デバイス登録マネージャーを使用して、すべてのデバイスの種類を登録できます。 IMEI 番号を持つデバイスを識別し、会社所有としてタグ付けして、COD シナリオで使用することもできます。

### <a name="dem"></a>DEM
デバイス登録マネージャーは、複数の企業所有のデバイスを登録して管理するために使用される特別なユーザー アカウントです。 作成後は、マネージャーがポータル サイトをインストールし、多数のユーザーがいないデバイスを登録できます。 DEM の詳細については[ここ](enroll-devices-using-device-enrollment-manager.md)を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
Apple Device Enrollment Program (DEP) 管理では、ポリシーを作成し、DEP で購入および管理されている iOS デバイスに "無線で" 展開できます。 ユーザーが初めてデバイスの電源を入れて iOS Setup Assistant を実行した際に、デバイスが登録されます。 この方法は、**iOS 監視対象**モードをサポートしているので、以下が有効になります。

  - 登録のロック
  - キオスク モード、およびその他の高度な構成および制限

iOS 登録の詳細については、以下を参照してください。

- [iOS デバイスの登録方法を選択する](choose-ios-enrollment-method.md)
- [Device Enrollment Program を使用して iOS デバイスを登録する](enroll-ios-devices-using-device-enrollment-program.md)。 
- [上の表に戻る](#overview-of-device-enrollment-methods)

### <a name="usb-sa"></a>USB-SA
IT 管理者は、セットアップ アシスタントを使用した登録を行うため、USB を介し Apple Configurator を使用して、会社が所有するデバイスを手動で準備します。 IT 管理者は登録プロファイルを作成して、Apple Configurator にエクスポートします。 ユーザーは、自分のデバイスを受け取ると、セットアップ アシスタントを実行してデバイスを登録するように求められます。 この方法は、**iOS 監視対象**モードをサポートしているので、以下が有効になります。
  - 登録のロック
  - キオスク モード、およびその他の高度な構成および制限

iOS 登録の詳細については、以下を参照してください。

- [iOS デバイスの登録方法を決定する](choose-ios-enrollment-method.md)
- [Configurator とセットアップ アシスタントを使用して iOS デバイスを登録する](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)。 

### <a name="usb-direct"></a>USB-Direct
直接登録の場合、管理者は登録ポリシーを作成して Apple Configurator にエクスポートすることで、各デバイスを手動で登録する必要があります。 USB で接続された企業所有デバイスは直接登録されます。工場出荷時のリセットを必要としません。 デバイスはユーザーがいないデバイスとして管理されます。 これらのデバイスはロックされず、監視対象にもなりません。また、条件付きアクセス、脱獄の検出、モバイル アプリケーション管理がサポートされません。 

iOS 登録の詳細については、以下を参照してください。

- [iOS デバイスの登録方法を決定する](choose-ios-enrollment-method.md)
- [Configurator と直接登録を使用して iOS デバイスを登録する](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Exchange ActiveSync および Intune を使用したモバイル デバイス管理
登録されていないが Exchange ActiveSync (EAS) に接続するモバイル デバイスは、EAS MDM ポリシーを使用して Intune で管理できます。 Intune は Exchange Connector を使用し、オンプレミスまたはクラウドでホストされている EAS と通信します。 詳細は近日公開予定。


## <a name="windows-pc-management-with-intune"></a>Intune による Windows PC 管理  
Microsoft Intune では、Intune クライアント ソフトウェアを使用して Windows PC を管理することもできます。 Intune クライアントを使用して管理される PC では、次の操作を実行できます。

 - ソフトウェアおよびハードウェアのインベントリのレポート
 - デスクトップ アプリケーション (.exe ファイルや .msi ファイルなど) のインストール
 - ファイアウォール設定を管理します。

Intune クライアント ソフトウェアを利用して管理される PC は、選択的ワイプを利用できますが、完全にはワイプされません。 Intune クライアント ソフトウェアを使用して管理される PC では、条件付きアクセス、VPN と Wi-Fi の設定、証明書と電子メール構成の展開などの多数の Intune 管理機能を利用できません。 詳細は近日公開予定。

## <a name="supported-device-platforms-and-browsers"></a>サポートされるデバイス プラットフォームとブラウザー

[Intune でサポートされるデバイスとブラウザー](https://docs.microsoft.com/intune/get-started/supported-mobile-devices-and-computers)に関するトピックを参照してください

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 証明書の有効期限が切れた後のモバイル デバイスのクリーンアップ

MDM 証明書は、モバイル デバイスが Intune サービスと通信しているときに自動的に更新されます。 (PC ではなく) モバイル デバイスがワイプされたり、一定の時間 Intune サービスとモバイル デバイスが通信できなかったりすると、MDM 証明書は更新されません。 デバイスは、MDM 証明書の有効期限が切れてから 180 日後に、Azure Portal から削除されます。



<!--HONumber=Feb17_HO1-->


