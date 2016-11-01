---
title: "デバイスを登録する | Microsoft Intune"
description: "モバイル デバイス管理 (MDM) では、登録を使用してデバイスを管理対象にし、リソースへのアクセスを許可します。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 92e40930c0ccbeb3d98bef43b115fd92f24beaef
ms.openlocfilehash: 136f91e26a367ab107a80673930e735c85008ac7


---

# 管理するデバイスを Intune に登録する
Windows PC などのデバイスを登録し、Microsoft Intune によるモバイル デバイス管理 (MDM) を有効にできます。 このトピックでは、Intune の管理にモバイル デバイスを登録するさまざまな方法について説明します。 デバイスの登録方法は、デバイスの種類、所有権、および必要な管理レベルによって決まります。 "Bring Your Own Device" (BYOD) の登録では、ユーザーは個人で所有するスマートフォン、タブレット、PC を登録できます。 企業所有のデバイス (COD) の登録では、リモート ワイプ、共有デバイス、デバイスのユーザー アフィニティなどの管理シナリオが有効になります。

オンプレミスの、またはクラウドでホストされている [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune) を使用すると、登録を必要としない簡単な Intune 管理が可能です。 Windows PC は、[Intune クライアント ソフトウェア](#manage-windows-pcs-with-intune)を使用して管理することもできます。

## デバイスの登録方法の概要

次の表では、Intune の登録方法とサポートされている機能を示します。 次のような機能が含まれます。
- **ワイプ** - デバイスを工場出荷時の状態にリセットし、すべてのデータを削除します。 詳細については、「[Retire devices](retire-devices-from-microsoft-intune-management.md)」 (デバイスの削除) を参照してください。
- **アフィニティ** - デバイスとユーザーを関連付けます。 モバイル アプリケーション管理 (MAM) および会社データへの条件付きアクセスのために必要です。 詳細については、「[ユーザー アフィニティ](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices)」を参照してください。
- **ロック** - ユーザーが管理からデバイスを削除できないようにします。 iOS デバイスでは、ロックには監視モードが必要です。 詳細については、「[リモート ロック](retire-devices-from-microsoft-intune-management.md#block-access-a-device)」を参照してください。

**iOS の登録方法**

| **方法** |  **ワイプ** |  **アフィニティ**    |   **ロック** | **説明** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | いいえ|    ○ |   いいえ | [説明](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   いいえ |いいえ |いいえ  | [説明](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   Yes |   省略可能 |  省略可能|[説明](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| [はい] |   省略可能 |  いいえ| [説明](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| いいえ |    いいえ  | いいえ|[説明](ios-direct-enrollment-in-microsoft-intune.md)|

**Windows の登録方法**

| **方法** |  **ワイプ** |  **アフィニティ**    |   **ロック** | **説明**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Yes|   ○ |   いいえ | [説明](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   いいえ |いいえ |いいえ  |[説明](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Android の登録方法**

| **方法** |  **ワイプ** |  **アフィニティ**    |   **ロック** | **説明**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | いいえ|    ○ |   いいえ | [説明](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   いいえ |いいえ |いいえ  |[説明](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

適切な方法を選択するのに役立つ一連の質問については、「[モバイル デバイスの登録方法の選択](/intune/get-started/choose-how-to-enroll-devices1)」をご覧ください。

## BYOD
"Bring your own device" はユーザーがポータル サイト アプリをインストールし、自分のデバイスを登録します。 これにより、ユーザーは会社のネットワークに接続して、ドメインまたは Azure Active Directory に参加できます。 ほとんどのプラットフォームで、多くの COD シナリオのために BYOD 登録を有効にする必要があります。 詳細については、「[デバイス登録の前提条件](prerequisites-for-enrollment.md)」を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

## 企業所有のデバイス
企業所有のデバイス (COD) は、Intune コンソールを利用して管理できます。 iOS デバイスは、Apple が提供するツールを利用して直接登録できます。 管理者またはマネージャーは、デバイス登録マネージャーを使用して、すべてのデバイスの種類を登録できます。 IMEI 番号を持つデバイスを識別し、会社所有としてタグ付けして、COD シナリオで使用することもできます。

詳細については、「[Microsoft Intune で企業所有のデバイスを登録する](manage-corporate-owned-devices.md)」を参照してください。

### DEM
デバイス登録マネージャーは、複数の企業所有デバイスを登録して管理するために使用される特別な Intune アカウントです。 作成後は、マネージャーがポータル サイトをインストールし、多数のユーザーがいないデバイスを登録できます。 DEM の詳細については[ここ](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

### DEP
Apple Device Enrollment Program (DEP) 管理では、ポリシーを作成し、DEP で購入および管理されている iOS デバイスに "無線で" 展開できます。 ユーザーが初めてデバイスの電源を入れて iOS Setup Assistant を実行した際に、デバイスが登録されます。 この方法は、**iOS 監視対象**モードをサポートしているので、以下が有効になります。
  - 登録のロック
  - 条件付きアクセス
  - 脱獄の検出
  - モバイル アプリケーション管理

DEP の詳細については[ここ](ios-device-enrollment-program-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

### USB-SA
USB で接続された企業所有デバイスは、Intune ポリシーで準備されます。 セットアップ アシスタント登録の場合、管理者がこの Intune ポリシーを作成し、Apple Configurator にエクスポートします。 管理者は手動で各デバイスを登録する必要があります。 ユーザーはデバイスを受け取り、セットアップ アシスタントを実行してデバイスを登録します。 この方法は、**iOS 監視対象**モードをサポートしているので、以下が有効になります。
  - 条件付きアクセス
  - 脱獄の検出
  - モバイル アプリケーション管理

Apple Configurator を使用したセットアップ アシスタントの登録については、[ここ](ios-setup-assistant-enrollment-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

### USB-Direct
直接登録の場合、管理者がこの Intune ポリシーを作成し、Apple Configurator にエクスポートします。 USB で接続された企業所有デバイスは直接登録されます。工場出荷時のリセットを必要としません。 管理者は手動で各デバイスを登録する必要があります。 デバイスはユーザーがいないデバイスとして管理されます。 これらのデバイスはロックされず、監視対象にもなりません。また、条件付きアクセス、脱獄の検出、モバイル アプリケーション管理がサポートされません。 Apple Configurator を使用した直接登録については、[ここ](ios-direct-enrollment-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

## Exchange ActiveSync および Intune を使用したモバイル デバイス管理
登録されていないが Exchange ActiveSync (EAS) に接続するモバイル デバイスは、EAS MDM ポリシーを使用して Intune で管理できます。 Intune は Exchange Connector を使用し、オンプレミスまたはクラウドでホストされている EAS と通信します。

詳細については、「[Exchange ActiveSync および Intune を使用したモバイル デバイス管理](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)」を参照してください。


## Intune による Windows PC 管理  
Microsoft Intune では、Intune クライアント ソフトウェアを使用して Windows PC を管理することもできます。 Intune クライアントを使用して管理される PC では、次の操作を実行できます。

 - ソフトウェアおよびハードウェアのインベントリのレポート
 - デスクトップ アプリケーション (.exe ファイルや .msi ファイルなど) のインストール
 - ファイアウォール設定

Intune クライアント ソフトウェアを利用して管理される PC は、選択的ワイプを利用できますが、完全にはワイプされません。 Intune クライアント ソフトウェアを使用して管理される PC では、条件付きアクセス、VPN と Wi-Fi の設定、証明書と電子メール構成の展開などの多数の Intune 管理機能を利用できません。

詳細については、「[Intune を使用して Windows PC を管理する](manage-windows-pcs-with-microsoft-intune.md)」をご覧ください。

## サポートされるデバイス プラットフォーム

Intune では、次のデバイス プラットフォームを管理できます。

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## 次のステップ
- [デバイス登録の前提条件](prerequisites-for-enrollment.md)
- [企業所有のデバイスの管理](manage-corporate-owned-devices.md)
- [サポートされるモバイル デバイスとコンピューター](../get-started/supported-mobile-devices-and-computers.md)



<!--HONumber=Oct16_HO3-->


