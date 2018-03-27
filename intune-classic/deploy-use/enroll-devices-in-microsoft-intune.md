---
title: デバイスの登録
description: モバイル デバイス管理 (MDM) では、登録を使用してデバイスを管理対象にし、リソースへのアクセスを許可します。
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 09/22/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 99a4273a5f3ef2e1696d2fdc1c2a9b9f251b5b87
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="enroll-devices-for-management-in-intune"></a>管理するデバイスを Intune に登録する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Windows PC などのデバイスを登録し、Microsoft Intune によるモバイル デバイス管理 (MDM) を有効にできます。 このトピックでは、Intune の管理にモバイル デバイスを登録するさまざまな方法について説明します。 デバイスの登録方法は、デバイスの種類、所有権、および必要な管理レベルによって決まります。 "Bring Your Own Device" (BYOD) の登録では、ユーザーは個人で所有するスマートフォン、タブレット、PC を登録できます。 会社が所有しているデバイス (COD) の登録では、自動登録、共有デバイス、事前承認された登録要件などの管理シナリオが有効になります。

オンプレミスの、またはクラウドでホストされている [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune) を使用すると、登録を必要としない簡単な Intune 管理が可能です。 Windows PC は、[Intune クライアント ソフトウェア](#windows-pc-management-with-intune)を使用して管理することもできます。

既定では、すべてのプラットフォーム用のデバイスを Intune に登録することができます。 デバイスの登録をブロックするには、管理者資格情報を使用して [Microsoft Intune 管理ポータル](https://manage.microsoft.com)にサインインします。 **[管理]** > **[モバイル デバイス管理]** > **[登録ルール]** の順に選択し、登録をブロックするプラットフォームの該当するチェック ボックスをオフにします。

## <a name="overview-of-device-enrollment-methods"></a>デバイスの登録方法の概要

次の表は、Intune の登録方法とサポートされる機能、各方法の要件の一覧です。 また、機能と要件について説明しています。

- **ワイプ** - ユーザーがデバイスを登録する前に、デバイスのワイプが必要かどうかを示します。 "ワイプ" という用語は、デバイスを出荷時の設定にリセットし、すべてのデータを削除することを意味します。 詳細については、「[Retire devices](retire-devices-from-microsoft-intune-management.md)」 (デバイスの削除) を参照してください。
- **アフィニティ** - デバイスとユーザーを関連付けます。 モバイル アプリケーション管理 (MAM) および会社データへの条件付きアクセスのために必要です。 詳細については、「[ユーザー アフィニティ](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices)」を参照してください。
- **ロック** - ユーザーがネイティブ オペレーティング システムのメニューを使用して、デバイスを登録解除できるかどうかを示します。 ユーザーは、ポータル サイト アプリを使用してすべてのプラットフォームで自分のデバイスを登録解除できます。

**iOS の登録方法**

| **方法** |  **ワイプが必要?** |    **アフィニティ**    |   **ロック** | **詳細** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | [いいえ]|    はい |   [いいえ] | [詳細情報](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   [いいえ] |[いいえ] |[いいえ]  | [詳細情報](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   はい |   省略可能 |  省略可能|[詳細情報](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| はい |   省略可能 |  [いいえ]| [詳細情報](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| [いいえ] |    [いいえ]  | [いいえ]|[詳細情報](ios-direct-enrollment-in-microsoft-intune.md)|

**Windows の登録方法**

| **方法** |  **ワイプが必要?** |    **アフィニティ**    |   **ロック** | **詳細**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | [いいえ]|    はい |   [いいえ] | [詳細情報](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   [いいえ] |[いいえ] |[いいえ]  |[詳細情報](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Android の登録方法**

| **方法** |  **ワイプが必要?** |    **アフィニティ**    |   **ロック** | **詳細**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | [いいえ]|    はい |   [いいえ] | [詳細情報](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   [いいえ] |[いいえ] |[いいえ]  |[詳細情報](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Android for Work の登録方法**

| **方法** |  **ワイプが必要?** |    **アフィニティ**    |   **ロック** | **詳細**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | [いいえ]|    はい |   [いいえ] | [詳細情報](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   [いいえ] |[いいえ] |[いいえ]  |[詳細情報](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**macOS の登録方法**

| **方法** |  **ワイプが必要?** |    **アフィニティ**    |   **ロック** | **詳細**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | [いいえ]|    はい |   [いいえ] | [詳細情報](prerequisites-for-enrollment.md)|


適切な方法を選択するのに役立つ一連の質問については、「[モバイル デバイスの登録方法の選択](/intune-classic/get-started/choose-how-to-enroll-devices1)」をご覧ください。

## <a name="byod"></a>BYOD
"Bring your own device" はユーザーがポータル サイト アプリをインストールし、自分のデバイスを登録します。 これにより、ユーザーは会社のネットワークに接続して、ドメインまたは Azure Active Directory に参加できます。 ほとんどのプラットフォームで、多くの COD シナリオのために BYOD 登録を有効にする必要があります。 詳細については、「[デバイス登録の前提条件](prerequisites-for-enrollment.md)」を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

## <a name="corporate-owned-devices"></a>会社所有のデバイス
企業所有のデバイス (COD) は、Intune コンソールを利用して管理できます。 iOS デバイスは、Apple が提供するツールを利用して直接登録できます。 管理者またはマネージャーは、デバイス登録マネージャーを使用して、すべてのデバイスの種類を登録できます。 IMEI 番号を持つデバイスを識別し、会社所有としてタグ付けして、COD シナリオで使用することもできます。

詳細については、「[Microsoft Intune で企業所有のデバイスを登録する](manage-corporate-owned-devices.md)」を参照してください。

### <a name="dem"></a>DEM
デバイス登録マネージャーは、複数の企業所有デバイスを登録して管理するために使用される特別な Intune アカウントです。 作成後は、マネージャーがポータル サイトをインストールし、多数のユーザーがいないデバイスを登録できます。 DEM の詳細については[ここ](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
Apple Device Enrollment Program (DEP) 管理では、ポリシーを作成し、DEP で購入および管理されている iOS デバイスに "無線で" 展開できます。 ユーザーが初めてデバイスの電源を入れて iOS Setup Assistant を実行した際に、デバイスが登録されます。 この方法は、**iOS 監視対象**モードをサポートしているので、以下が有効になります。
  - 登録のロック
  - キオスク モード、およびその他の高度な構成および制限

DEP の詳細については[ここ](ios-device-enrollment-program-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

### <a name="usb-sa"></a>USB-SA
IT 管理者は、セットアップ アシスタントを使用した登録を行うため、USB を介し Apple Configurator を使用して、会社が所有するデバイスを手動で準備します。 IT 管理者は登録プロファイルを作成して、Apple Configurator にエクスポートします。 ユーザーは、自分のデバイスを受け取ると、セットアップ アシスタントを実行してデバイスを登録するように求められます。 この方法は、**iOS 監視対象**モードをサポートしているので、以下が有効になります。
  - 登録のロック
  - キオスク モード、およびその他の高度な構成および制限

Apple Configurator を使用したセットアップ アシスタントの登録については、[ここ](ios-setup-assistant-enrollment-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

### <a name="usb-direct"></a>USB-Direct
直接登録の場合、管理者は登録ポリシーを作成して Apple Configurator にエクスポートすることで、各デバイスを手動で登録する必要があります。 USB で接続された会社所有デバイスは直接登録されます。工場出荷時のリセットを必要としません。 デバイスはユーザーがいないデバイスとして管理されます。 これらのデバイスはロックされず、監視対象にもなりません。また、条件付きアクセス、脱獄の検出、モバイル アプリケーション管理がサポートされません。  Apple Configurator を使用した直接登録については、[ここ](ios-direct-enrollment-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Exchange ActiveSync および Intune を使用したモバイル デバイス管理
登録されていないが Exchange ActiveSync (EAS) に接続するモバイル デバイスは、EAS MDM ポリシーを使用して Intune で管理できます。 Intune は Exchange Connector を使用し、オンプレミスまたはクラウドでホストされている EAS と通信します。 詳細については、「[Exchange ActiveSync および Intune を使用したモバイル デバイス管理](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)」を参照してください。


## <a name="windows-pc-management-with-intune"></a>Intune による Windows PC 管理  
Microsoft Intune では、Intune クライアント ソフトウェアを使用して Windows PC を管理することもできます。 Intune クライアントを使用して管理される PC では、次の操作を実行できます。

 - ソフトウェアおよびハードウェアのインベントリのレポート
 - デスクトップ アプリケーション (.exe ファイルや .msi ファイルなど) のインストール
 - ファイアウォール設定を管理します。

Intune クライアント ソフトウェアを利用して管理される PC は、選択的ワイプを利用できますが、完全にはワイプされません。 Intune クライアント ソフトウェアを使用して管理される PC では、条件付きアクセス、VPN と Wi-Fi の設定、証明書と電子メール構成の展開などの多数の Intune 管理機能を利用できません。 詳細については、「[Intune を使用して Windows PC を管理する](manage-windows-pcs-with-microsoft-intune.md)」をご覧ください。

## <a name="supported-device-platforms"></a>サポートされるデバイス プラットフォーム

Intune では、次のデバイス プラットフォームを管理できます。

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## <a name="next-steps"></a>次の手順
- [デバイス登録の前提条件](prerequisites-for-enrollment.md)
- [企業所有のデバイスの管理](manage-corporate-owned-devices.md)
- [サポートされるモバイル デバイスとコンピューター](/intune/supported-devices-browsers#intune-supported-devices)
