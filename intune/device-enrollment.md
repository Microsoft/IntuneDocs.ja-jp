---
title: "Microsoft Intune デバイスの登録とは"
titlesuffix: Azure portal
description: "iOS、Android、Windows デバイスの登録について説明します。\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dda7108aedcc4d3878fe3743ee0b88b26fabbe6f
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="what-is-device-enrollment"></a>デバイス登録とは
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

このトピックでは登録について説明します。また、Intune 管理でモバイル デバイスを登録する方法をいくつか紹介します。

Intune にデバイスを登録して、それらのデバイスを管理できるようにします。 この機能は、Intune ドキュメントでは、モバイル デバイス管理 (MDM) と呼ばれます。 デバイスを Intune に登録すると、MDM 証明書が発行されます。デバイスは、この証明書を使用して Intune サービスと通信します。

デバイスの登録方法は、デバイスの種類、所有権、必要な管理レベルによって決まります。 "Bring Your Own Device" (BYOD) の登録では、ユーザーは個人で所有するスマートフォン、タブレット、PC を登録できます。 会社が所有しているデバイス (COD) の登録では、自動登録、共有デバイス、事前承認された登録要件などの管理シナリオが有効になります。

オンプレミスの、またはクラウドでホストされている Exchange ActiveSync を使用すると、登録を必要としない簡単な Intune 管理が可能です (詳細は近日公開予定)。 Windows PC はモバイル デバイスとして管理できます (推奨)。この方法については以下で説明します。


## <a name="overview-of-device-enrollment-methods"></a>デバイスの登録方法の概要

以下の表では、Intune の登録方法の概要を、機能と要件とともにまとめています。
**凡例**

- **リセットが必要** - デバイスは登録時に工場出荷時の状態にリセットされます。
- **ユーザー アフィニティ** - デバイスとユーザーを関連付けます。 詳細については、「[ユーザー アフィニティ](device-enrollment-program-enroll-ios.md)」を参照してください。
- **ロック済み** - ユーザーによるデバイス登録解除を防ぎます。

**iOS の登録方法**

| **方法** |  **リセットが必要** |    **ユーザー アフィニティ**   |   **ロック済み** | **詳細** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | いいえ|    ○ |   いいえ | [詳細情報](./apple-mdm-push-certificate-get.md)|
|**[DEM](#dem)**|   いいえ |いいえ |いいえ  | [詳細情報](./device-enrollment-program-enroll-ios.md)|
|**[DEP](#dep)**|   Yes |   省略可能 |  省略可能|[詳細情報](./device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| Yes |   省略可能 |  いいえ| [詳細情報](./apple-configurator-setup-assistant-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| いいえ |    いいえ  | いいえ|[詳細情報](./apple-configurator-direct-enroll-ios.md)|

**Windows の登録方法**

| **方法** |  **リセットが必要** |    **ユーザー アフィニティ**   |   **ロック済み** | **詳細**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | いいえ |   ○ |   いいえ | [詳細情報](windows-enroll.md)|
|**[DEM](#dem)**|   いいえ |いいえ |いいえ  |[詳細情報](device-enrollment-manager-enroll.md)|
|**自動登録** | いいえ |○ |いいえ | [詳細情報](./windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**一括登録** |いいえ |いいえ |いいえ | [詳細情報](./windows-bulk-enroll.md) |

**Android の登録方法**

| **方法** |  **リセットが必要** |    **ユーザー アフィニティ**   |   **ロック済み** | **詳細**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | いいえ|    ○ |   いいえ | [詳細情報](./android-enroll.md)|
|**[DEM](#dem)**|   いいえ |いいえ |いいえ  |[詳細情報](./device-enrollment-program-enroll-ios.md)|
|**Android for Work**| いいえ | ○ | いいえ| [詳細情報](./android-enroll.md#enable-enrollment-of-android-for-work-devices) |


## <a name="byod"></a>BYOD
"Bring your own device" のユーザーは、ポータル サイト アプリをインストールして実行し、自分のデバイスを登録します。 このプログラムによって、ユーザーは電子メールなどの会社のリソースにアクセスできます。

## <a name="corporate-owned-devices"></a>会社所有のデバイス
会社所有のデバイス (COD) の登録シナリオを次に示します。 iOS デバイスは、Apple が提供するツールを利用して直接登録できます。 管理者またはマネージャーは、デバイス登録マネージャーを使用して、すべてのデバイスの種類を登録できます。 IMEI 番号を持つデバイスを識別し、会社所有としてタグ付けして、COD シナリオで使用することもできます。

### <a name="dem"></a>DEM
デバイス登録マネージャー (DEM) は、複数の会社所有のデバイスを登録して管理するために使用される特別なユーザー アカウントです。 作成後は、マネージャーがポータル サイトをインストールし、多数のユーザーがいないデバイスを登録できます。 DEM の詳細については[ここ](./device-enrollment-manager-enroll.md)を参照してください。

### <a name="dep"></a>DEP
Apple Device Enrollment Program (DEP) 管理では、ポリシーを作成し、DEP で購入および管理されている iOS デバイスに "無線で" 展開できます。 ユーザーが初めてデバイスの電源を入れて iOS Setup Assistant を実行した際に、デバイスが登録されます。 この方法は、**iOS 監視対象**モードをサポートしているため、以下の機能が有効になります。

  - 登録のロック
  - キオスク モード、およびその他の高度な構成および制限

iOS DEP 登録の詳細については、以下をご覧ください。

- [iOS デバイスの登録方法を選択する](enrollment-method-choose-ios.md)
- [Device Enrollment Program を使用して iOS デバイスを登録する](device-enrollment-program-enroll-ios.md)

### <a name="usb-sa"></a>USB-SA
IT 管理者は、セットアップ アシスタントを使用した登録を行うため、USB 経由で Apple Configurator を使用して、会社が所有するデバイスを手動で準備します。 IT 管理者は登録プロファイルを作成して、Apple Configurator にエクスポートします。 ユーザーは、自分のデバイスを受け取ると、セットアップ アシスタントを実行してデバイスを登録するように求められます。 この方法は、**iOS 監視対象**モードをサポートしているため、以下の機能が有効になります。
  - 登録のロック
  - キオスク モード、およびその他の高度な構成および制限

セットアップ アシスタントを使用した iOS Apple Configurator 登録については、以下をご覧ください。

- [iOS デバイスの登録方法を決定する](enrollment-method-choose-ios.md)
- [Configurator とセットアップ アシスタントを使用して iOS デバイスを登録する](apple-configurator-setup-assistant-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
直接登録の場合、管理者は登録ポリシーを作成して Apple Configurator にエクスポートすることで、各デバイスを手動で登録する必要があります。 USB で接続された会社所有デバイスは直接登録されます。工場出荷時のリセットを必要としません。 デバイスはユーザーがいないデバイスとして管理されます。 これらのデバイスはロックされず、監視対象にもなりません。また、条件付きアクセス、脱獄の検出、モバイル アプリケーション管理がサポートされません。

iOS 登録の詳細については、以下を参照してください。

- [iOS デバイスの登録方法を決定する](enrollment-method-choose-ios.md)
- [Configurator と直接登録を使用して iOS デバイスを登録する](apple-configurator-direct-enroll-ios.md)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Exchange ActiveSync および Intune を使用したモバイル デバイス管理
登録されていないが Exchange ActiveSync (EAS) に接続するモバイル デバイスは、EAS MDM ポリシーを使用して Intune で管理できます。 Intune は Exchange Connector を使用し、オンプレミスまたはクラウドでホストされている EAS と通信します。 詳細は近日公開予定。

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 証明書の有効期限が切れた後のモバイル デバイスのクリーンアップ

MDM 証明書は、モバイル デバイスが Intune サービスと通信しているときに自動的に更新されます。 モバイル デバイスがワイプされたり、一定の時間 Intune サービスとモバイル デバイスが通信できなかったりすると、MDM 証明書は更新されません。 デバイスは、MDM 証明書の有効期限が切れてから 180 日後に、Azure Portal から削除されます。
