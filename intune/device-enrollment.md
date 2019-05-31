---
title: Microsoft Intune デバイスの登録とは
titleSuffix: Microsoft Intune
description: iOS、Android、Windows デバイスの登録について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 4/24/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68f5fad9d05787b6e79792d594480547ce10cf81
ms.sourcegitcommit: b0cf661145ccc6e3518db620af199786a623a0d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64764918"
---
# <a name="what-is-device-enrollment"></a>デバイス登録とは
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune では、従業員のデバイスやアプリ、従業員が会社のデータにアクセスする手段を管理できます。 このモバイル デバイス管理 (MDM) を使用するには、まず Intune サービスにデバイスを登録する必要があります。 デバイスが登録されると、MDM 証明書が発行されます。 この証明書を使用して、Intune サービスと通信します。

次の表に示すように、従業員のデバイスを登録する方法は複数あります。 各方法は、デバイスの所有権 (個人または会社)、デバイスの種類 (iOS、Windows、Android)、および管理要件 (リセット、アフィニティ、ロック) によって異なります。

既定では、すべてのプラットフォーム用のデバイスを Intune に登録することができます。 ただし、[プラットフォームによってデバイスを制限する](enrollment-restrictions-set.md#set-device-type-restrictions)ことができます。

## <a name="ios-enrollment-methods"></a>iOS の登録方法

| **方法** |  **リセットが必要** |    [**ユーザー アフィニティ**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) |   **ロック済み** | **詳細** |
|:---:|:---:|:---:|:---:|:---:|
| | 登録時にデバイスがワイプされます。 |  各デバイスをユーザーに関連付ける。| ユーザーによる登録解除が可能である。  | |
|**[BYOD](#bring-your-own-device)** | [いいえ]|   はい |   [いいえ] | [詳細情報](./apple-mdm-push-certificate-get.md)|
|**[DEM](#device-enrollment-manager)**| [いいえ] |[いいえ] |[いいえ]  | [詳細情報](./device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**|   はい |   省略可能 |  省略可能|[詳細情報](./device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| はい |   省略可能 |  [いいえ]| [詳細情報](./apple-configurator-setup-assistant-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| [いいえ] |    [いいえ]  | [いいえ]|[詳細情報](./apple-configurator-direct-enroll-ios.md)|

## <a name="macos-enrollment-methods"></a>macOS の登録方法
| **方法** |  **リセットが必要** |  **ユーザー アフィニティ** | **ロック済み** | **詳細**|
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | [いいえ]| はい | [いいえ] | [詳細情報](./macos-enroll.md)|
|**[DEM](#device-enrollment-manager)**| [いいえ] |[いいえ] |[いいえ]  | [詳細情報](./device-enrollment-manager-enroll.md)|
|**[DEP](#apple-device-enrollment-program)**|   はい |   省略可能 |  省略可能|[詳細情報](./device-enrollment-program-enroll-macos.md)|


## <a name="windows-enrollment-methods"></a>Windows の登録方法

| **方法** |  **リセットが必要** |    **ユーザー アフィニティ**   |   **ロック済み** | **詳細**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | [いいえ] |  はい |   [いいえ] | [詳細情報](windows-enroll.md)|
|**[DEM](#device-enrollment-manager)**| [いいえ] |[いいえ] |[いいえ]  |[詳細情報](device-enrollment-manager-enroll.md)|
|**自動登録** | [いいえ] |はい |[いいえ] | [詳細情報](./windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Autopilot** |はい |はい |[いいえ] | [詳細情報](enrollment-autopilot.md)
|**一括登録** |[いいえ] |[いいえ] |[いいえ] | [詳細情報](./windows-bulk-enroll.md) |
|**共同管理** |[いいえ] |はい |[いいえ] | [詳細情報](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)
|**GPO** |[いいえ] |はい |[いいえ] | [詳細情報](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)


## <a name="android-enrollment-methods"></a>Android の登録方法

| **個人用** | **登録方法** | **リセットが必要** | **ユーザー アフィニティ** | **ロック済み** | **詳細**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Android のデバイス管理**|**ポータル サイトからユーザーが開始** | [いいえ] | はい | [いいえ] | [詳細情報](https://docs.microsoft.com/intune-user-help/enroll-device-android-company-portal)|
|**Android エンタープライズの仕事用プロファイル**|**ポータル サイトからユーザーが開始**| [いいえ] | はい | [いいえ] | [詳細情報](./android-work-profile-enroll.md)|


| **企業** | **登録方法** | **リセットが必要** | **ユーザー アフィニティ** | **ロック済み** | **詳細**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Android のデバイス管理**|**ポータル サイトから [DEM](#device-enrollment-manager) が開始**| [いいえ] | [いいえ] | [いいえ] |[詳細情報](./device-enrollment-manager-enroll.md)|
|**Android のデバイス管理**|**(事前に宣言されている IMEI または SN) ポータル サイトからユーザーが開始**| [いいえ] | はい | [いいえ] | [詳細情報](./corporate-identifiers-add.md)|
|**Zebra モビリティ拡張が装備された Android デバイス管理**|**ポータル サイトからユーザーまたは[DEM](#device-enrollment-manager) が開始**| [いいえ] | ユーザーが開始した場合は [はい]、[DEM](#device-enrollment-manager) が開始した場合は [いいえ] | [いいえ] | [詳細情報](./android-zebra-mx-overview.md)|
|**Android Enterprise 専用**|**NFC、トークン、QR コード、ゼロ タッチ**| はい | [いいえ] | ポリシーで構成可能 | [詳細情報](./android-kiosk-enroll.md)|
|**Android Enterprise のフル マネージド (プレビュー)**|**NFC、トークン、QR コード、ゼロ タッチ**| はい | はい | ポリシーで構成可能 | [詳細情報](./android-dedicated-devices-fully-managed-enroll.md)|


## <a name="bring-your-own-device"></a>Bring Your Own Device
BYOD (私物デバイスの業務利用) デバイスには、個人の電話、タブレット、PC があります。 ユーザーは、ポータル サイト アプリをインストール、および実行して、BYOD デバイスを登録します。 このプログラムによって、ユーザーは電子メールなどの会社のリソースにアクセスできます。

## <a name="corporate-owned-device"></a>企業所有のデバイス
[企業所有のデバイス (COD) ](corporate-identifiers-add.md)には、組織が所有し、従業員に配布されている電話、タブレット、PC があります。 COD 登録では、自動登録、共有デバイス、事前承認された登録要件などのシナリオがサポートされます。 管理者やマネージャーによる COD の一般的な登録方法は、デバイス登録マネージャー (DEM) を使用することです。 iOS デバイスは、Apple から提供される Device Enrollment Program (DEP) ツールから直接登録できます。 IMEI 番号を持つデバイスも、会社所有として識別して、タグを付けることができます。

### <a name="device-enrollment-manager"></a>デバイス登録マネージャー
デバイス登録マネージャー (DEM) は、複数の会社所有のデバイスを登録して管理するために使用される特別なユーザー アカウントです。 作成後は、マネージャーがポータル サイトをインストールし、多数のユーザーがいないデバイスを登録できます。 この種のデバイスは、POS アプリやユーティリティ アプリなどには適していますが、電子メールや会社のリソースにアクセスする必要があるユーザーには適していません。 DEM の詳細については[ここ](./device-enrollment-manager-enroll.md)を参照してください。 

### <a name="apple-device-enrollment-program"></a>Apple Device Enrollment Program
Apple Device Enrollment Program (DEP) 管理では、ポリシーを作成し、DEP で購入および管理されている iOS および macOS デバイスに "無線で" 展開できます。 ユーザーが初めてデバイスの電源を入れて Setup Assistant を実行した際に、デバイスが登録されます。 この方法は、iOS 監視対象モードをサポートしているため、特定の機能でデバイスを構成することができます。

iOS DEP 登録の詳細については、以下をご覧ください。

- [iOS デバイスの登録方法を選択する](ios-enroll.md)
- [Device Enrollment Program を使用して iOS デバイスを登録する](https://docs.microsoft.com/intune/device-restrictions-ios#device-enrollment-program)

### <a name="usb-sa"></a>USB-SA
IT 管理者は、セットアップ アシスタントを使用した登録を行うため、USB 経由で Apple Configurator を使用して、会社が所有するデバイスを手動で準備します。 IT 管理者は登録プロファイルを作成して、Apple Configurator にエクスポートします。 ユーザーは、自分のデバイスを受け取ると、セットアップ アシスタントを実行してデバイスを登録するように求められます。 この方法は、**iOS 監視対象**モードをサポートしているため、以下の機能が有効になります。
  - 登録のロック
  - キオスク モード、およびその他の高度な構成および制限

セットアップ アシスタントを使用した iOS Apple Configurator 登録については、以下をご覧ください。

- [iOS デバイスの登録方法を決定する](enrollment-method-choose-ios.md)
- [Configurator とセットアップ アシスタントを使用して iOS デバイスを登録する](apple-configurator-setup-assistant-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
直接登録の場合、管理者は登録ポリシーを作成して Apple Configurator にエクスポートすることで、各デバイスを手動で登録する必要があります。 USB で接続された会社所有デバイスは直接登録されます。ワイプを必要としません。 デバイスはユーザーがいないデバイスとして管理されます。 これらのデバイスはロックされず、監視対象にもなりません。また、条件付きアクセス、脱獄の検出、モバイル アプリケーション管理がサポートされません。

iOS 登録の詳細については、以下を参照してください。

- [iOS デバイスの登録方法を決定する](enrollment-method-choose-ios.md)
- [Configurator と直接登録を使用して iOS デバイスを登録する](apple-configurator-direct-enroll-ios.md)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 証明書の有効期限が切れた後のモバイル デバイスのクリーンアップ

MDM 証明書は、モバイル デバイスが Intune サービスと通信しているときに自動的に更新されます。 モバイル デバイスがワイプされたり、一定の時間 Intune サービスとモバイル デバイスが通信できなかったりすると、MDM 証明書は更新されません。 デバイスは、MDM 証明書の有効期限が切れてから 180 日後に、Azure Portal から削除されます。
