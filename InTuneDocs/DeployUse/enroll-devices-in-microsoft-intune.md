---
title: "デバイスを登録する | Microsoft Intune"
description: "モバイル デバイス管理 (MDM) では、登録を使用してデバイスを管理対象にし、リソースへのアクセスを許可します。"
keywords: 
author: NathBarn
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
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: 145d373edd65d7ba01c696c3b851692a13831dad


---

# 管理するデバイスを Intune に登録する
Windows PC などのデバイスを登録し、Microsoft Intune によるモバイル デバイス管理 (MDM) を有効にできます。 このトピックでは、Intune の管理にモバイル デバイスを登録するさまざまな方法について説明します。 デバイスの登録方法は、デバイスの種類、所有権、および必要な管理レベルによって決まります。 "Bring Your Own Device" (BYOD) の登録では、ユーザーは個人で所有するスマートフォン、タブレット、PC を登録できます。 企業所有のデバイス (COD) の登録では、リモート ワイプ、共有デバイス、デバイスのユーザー アフィニティなどの管理シナリオが有効になります。

オンプレミスの、またはクラウドでホストされている [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune) を使用すると、登録を必要としない簡単な Intune 管理が可能です。 Windows PC は、[Intune クライアント ソフトウェア](#manage-windows-pcs-with-intune)を使用して管理することもできます。

## デバイスの登録方法の概要

次の表では、Intune の登録方法とサポートされている機能を示します。 次のような機能が含まれます。
- **ワイプ** - デバイスを工場出荷時の状態にリセットし、すべてのデータを削除します。 [デバイスをインベントリから削除する](retire-devices-from-microsoft-intune-management.md)
- **アフィニティ** - デバイスとユーザーを関連付けます。 モバイル アプリケーション管理 (MAM) および会社データへの条件付きアクセスのために必要です。 [ユーザー アフィニティ](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices)
- **ロック** - ユーザーが管理からデバイスを削除できないようにします。 iOS デバイスでは、ロックには監視モードが必要です。 [リモート ロック](retire-devices-from-microsoft-intune-management.md#block-access-a-device)

**iOS の登録方法**

| **方法** |  **ワイプ** |  **アフィニティ**    |   **ロック** | **説明** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | いいえ|    ○ |   いいえ | [情報](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   いいえ |いいえ |いいえ  | [情報](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   Yes |   省略可能 |  省略可能|[情報](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| [はい] |   省略可能 |  いいえ| [情報](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| いいえ |    いいえ  | いいえ|[情報](ios-direct-enrollment-in-microsoft-intune.md)|

**Windows の登録方法**

| **方法** |  **ワイプ** |  **アフィニティ**    |   **ロック** | **説明**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Yes|   ○ |   いいえ | [情報](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   いいえ |いいえ |いいえ  |[情報](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Android の登録方法**

| **方法** |  **ワイプ** |  **アフィニティ**    |   **ロック** | **説明**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | いいえ|    ○ |   いいえ | [情報](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   いいえ |いいえ |いいえ  |[情報](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

適切な方法を選択するのに役立つ一連の質問については、「[モバイル デバイスの登録方法の選択](/intune/get-started/choose-how-to-enroll-devices1)」をご覧ください。

## BYOD
"Bring your own device" はユーザーがポータル サイト アプリをインストールし、自分のデバイスを登録します。 これにより、ユーザーは会社のネットワークに接続して、ドメインまたは Azure Active Directory に参加できます。 BYOD 登録を有効にすることは、ほとんどのプラットフォームの多くの COD シナリオの前提条件です。 「[Prerequisites for mobile device management in Intune](prerequisites-for-enrollment.md)」 (Intune でのモバイル デバイス管理の前提条件) をご覧ください。 ([表に戻る](#overview-of-device-enrollment-methods))

## 企業所有のデバイス
企業所有のデバイス (COD) は、Intune コンソールで管理できます。 iOS デバイスは、Apple が提供するツールを通して直接登録できます。 管理者またはマネージャーは、デバイス登録マネージャーを使用して、すべてのデバイスの種類を登録できます。 IMEI 番号を持つデバイスを識別し、会社所有としてタグ付けして、COD シナリオで使用することもできます。

[企業所有のデバイスを登録する](manage-corporate-owned-devices.md)

### DEM
デバイス登録マネージャーは、複数の企業所有デバイスを登録して管理するために使用される特別な Intune アカウントです。 作成後は、マネージャーがポータル サイトをインストールし、多数のユーザーがいないデバイスを登録できます。 DEM の詳細については[ここ](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

### DEP
Apple Device Enrollment Program (DEP) 管理では、ポリシーを作成し、DEP で購入および管理されている iOS デバイスに "無線で" 展開できます。 ユーザーが初めてデバイスの電源を入れて iOS Setup Assistant を実行すると、デバイスが登録されます。 この方法は、**iOS 監督下**モードをサポートしているので、以下が有効になります。
  - 登録のロック
  - 条件付きアクセス
  - 脱獄の検出
  - モバイル アプリケーション管理

DEP の詳細については[ここ](ios-device-enrollment-program-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

### USB-SA
USB 接続のセットアップ アシスタント登録。 管理者が Intune ポリシーを作成し、Apple Configurator にエクスポートします。 USB で接続された企業所有デバイスは、Intune ポリシーで準備されます。 管理者は手動で各デバイスを登録する必要があります。 ユーザーはデバイスを受け取り、セットアップ アシスタントを実行してデバイスを登録します。 この方法は、**iOS 監督下**モードをサポートしているので、以下が有効になります。
  - 条件付きアクセス
  - 脱獄の検出
  - モバイル アプリケーション管理

Apple Configurator を使用したセットアップ アシスタントの登録については、[ここ](ios-setup-assistant-enrollment-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

### USB-Direct
直接登録。 管理者が Intune ポリシーを作成し、Apple Configurator にエクスポートします。 USB で接続された企業所有デバイスは、工場出荷時のリセットを実行せずに、直接登録されます。 管理者は手動で各デバイスを登録する必要があります。 デバイスはユーザーがいないデバイスとして管理されます。 これらのデバイスはロックされず、監督下に置かれません。条件付きアクセス、脱獄の検出、モバイル アプリケーション管理はサポートできません。 Apple Configurator を使用した直接登録については、[ここ](ios-direct-enrollment-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

## Exchange ActiveSync および Intune を使用したモバイル デバイス管理
登録されていないが Exchange ActiveSync (EAS) に接続するモバイル デバイスは、EAS MDM ポリシーを使用して Intune で管理できます。 Intune は、Exchange Connector を使用して、オンプレミスのまたはクラウドでホストされている EA と通信します。

[Exchange ActiveSync および Intune を使用したモバイル デバイス管理](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Intune を使用して Windows PC を管理する  
Microsoft Intune では、Intune クライアント ソフトウェアを使用して Windows PC を管理することもできます。 Intune クライアントを使用して管理される PC では、次の操作を実行できます。

 - ソフトウェアおよびハードウェアのインベントリのレポート
 - デスクトップ アプリケーション (.exe ファイルや .msi ファイルなど) のインストール
 - ファイアウォール設定

Intune クライアント ソフトウェアを使用して管理される PC では、ワイプは実行できません。さらに、条件付きアクセス、VPN と Wi-Fi の設定、証明書と電子メール構成の展開などの多数の Intune 管理機能を利用することはできません。

[Intune を使用して Windows PC を管理する](manage-windows-pcs-with-microsoft-intune.md)

##  サポートされるデバイス プラットフォーム

Intune では、次のデバイス プラットフォームを管理できます。

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## 次のステップ
- [デバイス登録の前提条件](prerequisites-for-enrollment.md)
- [企業所有のデバイスの管理](manage-corporate-owned-devices.md)
- [サポートされるモバイル デバイスとコンピューター](../get-started/supported-mobile-devices-and-computers.md)



<!--HONumber=Sep16_HO4-->


