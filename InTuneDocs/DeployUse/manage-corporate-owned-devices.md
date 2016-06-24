---
# required metadata

title: 企業所有のデバイスの管理 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune で企業所有のデバイスを登録する
組織または企業所有のデバイス (COD) は、デバイス、購入方法、組織のニーズに応じて多様な方法で Intune の管理対象にすることができます。

## 企業所有の iOS デバイス
これらの登録方法は、組織がユーザーのデバイスを購入し、デバイスの管理は組織が行う "Choose Your Own Device (CYOD)" シナリオに適しています。 組織が iOS デバイスを購入した場合、登録を事前に構成し、ユーザーが初めて起動したときからデバイスを管理対象にすることができます。 Intune は、[Apple のデバイス登録プログラム (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) による登録、または Mac コンピューターで実行されている Apple Configurator ツールを使用した[直接](ios-direct-enrollment-in-microsoft-intune.md)登録、または[セットアップ アシスタント](ios-setup-assistant-enrollment-in-microsoft-intune.md)による登録をサポートしています。

[企業所有の iOS デバイスの登録](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## デバイス登録マネージャー
組織は、Intune を使用して、デバイス登録マネージャー アカウントという 1 つのユーザー アカウントで多数のモバイル デバイスを管理できます。 通常のユーザーが登録できる既定の標準デバイス数は 5 台ですが、デバイス登録マネージャー アカウントを作成すると、マネージャーはそのアカウントを使用して 5 台を超える台数を登録できます。 デバイス登録マネージャーを使用したデバイスの登録は、特定のユーザーが使用していないデバイスにのみ利用できます。 このようなデバイスは、たとえば POS アプリやユーティリティ アプリには適していますが、電子メールや会社のリソースにアクセスする必要がある場合には適していません。

[デバイス登録マネージャーを使った企業所有のデバイスの登録](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## International Mobile Equipment Identity (IMEI)
一意の IMEI (国際移動体装置識別番号) は、多くのモバイル デバイス製造元が採用している共通のデバイス プロパティです。 Intune 管理者は、会社が所有するデバイスの IMEI をインポートできます。 デバイスが Intune の管理対象になると、企業所有のデバイスというタグを付け、適切なポリシーの対象にすることができます。

[IMEI (国際移動体装置識別番号) を使って企業所有のデバイスを指定する](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

## 企業所有デバイスの登録方法の概要

次の表は、企業所有デバイスの登録方法とその利点です。

**iOS の登録方法**

| **方法** |  **[リセット](#Reset)** |   **[アフィニティ](#Affinity)**   |   **[Locked](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | ×|    ○ |   × |
|**[DEM](#DEM)**|   × |× |×  |
|**[DEP](#DEP)**|   ○ |   任意 |   任意|
|**[USB-SA](#USB-SA)**| ○ |   任意 |   ×|
|**[USB-Direct](#USB-Direct)**| × |    ×  | ×|

**Windows と Android の登録方法**

| **方法** |  **[ワイプ](#Wipe)** | **[User](#User)**   |   **[Locked](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | ×|    ○ |   × |
|**[DEM](#DEM)**|   × |× |×  |

**企業所有デバイスの登録方法**

### BYOD
"Bring Your Own Device"。 ユーザーがポータル サイト アプリをインストールし、自分のデバイスを登録します。 デバイスをポータル サイトに登録すると、デバイスが社内参加されます。 iOS デバイスをポータル サイトに登録するには、Apple ID が必要です。 BYOD の場合、企業所有デバイスに追加の構成は必要ありません。 [デバイス管理のセットアップ](get-ready-to-enroll-devices-in-microsoft-intune#set-up-device-management.md)手順を参照してください。 ([表に戻る](#overview-of corporate-owned-device-enrollment-methods))

### DEM
デバイス登録マネージャー。 管理者が DEM アカウントを作成します。 作成後は、マネージャーがポータル サイトをインストールし、多数のユーザーがいないデバイスを登録できます。 DEM の詳細については[ここ](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of corporate-owned-device-enrollment-methods))

### DEP
Apple Device Enrollment Program。 管理者がポリシーを作成し、DEP で管理する購入済み iOS デバイスに "無線で" ポリシーを展開します。 デバイスは、ユーザーが iOS のセットアップ アシスタントを実行するときに登録されます。 この方法は、**iOS 監督下**モードをサポートしているので、以下が有効になります。
  - 登録のロック
  - 条件付きアクセス
  - 脱獄の検出
  - モバイル アプリケーション管理

DEP の詳細については[ここ](ios-device-enrollment-program-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of corporate-owned-device-enrollment-methods))

### USB-SA
USB 接続のセットアップ アシスタント登録。 管理者が Intune ポリシーを作成し、Apple Configurator にエクスポートします。 USB で接続されたデバイスは、Intune ポリシーで準備されます。 管理者は手動で各デバイスを登録する必要があります。 ユーザーはデバイスを受け取り、セットアップ アシスタントを実行してデバイスを登録します。 この方法は、**iOS 監督下**モードをサポートしているので、以下が有効になります。
  - 条件付きアクセス
  - 脱獄の検出
  - モバイル アプリケーション管理

Apple Configurator を使用したセットアップ アシスタントの登録については、[ここ](ios-setup-assistant-enrollment-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of corporate-owned-device-enrollment-methods))

### USB-Direct
直接登録。 管理者が Intune ポリシーを作成し、Apple Configurator にエクスポートします。 USB で接続されたデバイスは、工場出荷時のリセットを実行せずに、直接登録されます。 管理者は手動で各デバイスを登録する必要があります。 デバイスはユーザーがいないデバイスとして管理されます。 これらのデバイスはロックされず、監督下に置かれません。条件付きアクセス、脱獄の検出、モバイル アプリケーション管理はサポートできません。 Apple Configurator を使用した直接登録については、[ここ](ios-direct-enrollment-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of corporate-owned-device-enrollment-methods))

**企業所有のモバイル デバイスの動作**

### リセット
デバイスを登録する場合、工場出荷時のリセットを実行してデバイスからすべてのデータを削除し、初期状態に戻す必要があるかどうかを指定します。
([表に戻る](#overview-of corporate-owned-device-enrollment-methods))

### アフィニティ
デバイスを特定のユーザーと接続する "ユーザー アフィニティ" をサポートする登録方法かどうかを指定します。 "任意" デバイスは、ユーザー アフィニティの有無にかかわらず登録できます。 以下をサポートするには、ユーザー アフィニティが必要です。
  - モバイル アプリケーション管理 (MAM) アプリ
  - 電子メールと会社データへの条件付きアクセス
  - ポータル サイト アプリ

([表に戻る](#overview-of corporate-owned-device-enrollment-methods))

### ロック
ユーザーが Intune ポリシーを削除して、実質的にデバイスが管理対象から外れないように、デバイスをロックするかどうかを指定します。 iOS デバイスの場合、デバイスをロックするには、監督下モードにする必要があります。
([表に戻る](#overview-of corporate-owned-device-enrollment-methods)) ([表に戻る](#overview-of corporate-owned-device-enrollment-methods))


<!--HONumber=Jun16_HO3-->


