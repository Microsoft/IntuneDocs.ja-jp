---
title: "デバイスを登録する | Microsoft Intune"
description: "モバイル デバイス管理 (MDM) では、登録を使用してデバイスを管理対象にし、リソースへのアクセスを許可します。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a7a0f834df939432910e32e6e635a70f021b37a9
ms.openlocfilehash: 63405b43609eda515656ad397c5c7ff4253a8167


---

# 管理するデバイスを Intune に登録する
Microsoft Intune のモバイル デバイス管理 (MDM) では、登録を使用してデバイスを管理対象にし、リソースへのアクセスを許可します。 デバイスの登録方法は、デバイスの種類、所有権、および必要な管理レベルによって決まります。 "私物のデバイスの持ち込み" (BYOD) と企業所有のデバイス (COD) を使用するシナリオでは、登録プロセスが必要です。 オンプレミスの、またはクラウドでホストされている Exchange ActiveSync を使用している組織は、登録要件のない軽い管理が可能です。 Windows PC は、Intune クライアント ソフトウェアを使用して管理することもできます。

方法については、「[モバイル デバイスの登録方法の選択](/intune/get-started/choose-how-to-enroll-devices1)」を参照してください。

###  サポートされるデバイス プラットフォーム

Intune では、次のデバイス プラットフォームを管理できます。

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## モバイル デバイス管理機関を設定する
MDM 機関では、一連のデバイスを管理するためのアクセス許可を持つ管理サービスを定義します。 MDM 機関のオプションには、Intune 単体で使用するか、Intune を Configuration Manager と連携させて使用する方法があります。 Configuration Manager を管理機関として設定した場合、モバイル デバイス管理のために使用できるサービスは他にありません。

>[!IMPORTANT]
> モバイル デバイスの管理に Intune のみ (オンライン サービス) を使用するか、System Center Configuration Manager と Intune との統合 (オンプレミス ソフトウェア ソリューションをオンライン サービスと組み合わせて使用) を使用するのかについて、慎重に検討します。 モバイル デバイス管理機関は、設定後に変更することはできません。

1.  [Microsoft Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** の順に選択します。

2.  **[タスク]** リストで **[モバイル デバイス管理機関の設定]**をクリックします。 **[MDM 機関の設定]** ダイアログ ボックスが開きます。

    ![[MDM 機関の設定] ダイアログ ボックス](../media/intune-mdm-authority.png)

3.  Intune によって、Intune を MDM 機関にすることを確認するよう求められます。 チェック ボックスを選択してから、**[はい]** を選択し、Microsoft Intune を使用してモバイル デバイスを管理します。

## Intune ポータル サイトを構成する

ユーザーは、Intune ポータル サイトを使用して、会社のデータにアクセスしたり、デバイスの登録、アプリケーションのインストール、IT 部門からのサポート情報の検索などの一般的なタスクを実行したりできます。

> [!TIP]
> ポータル サイトをカスタマイズすると、構成がポータル サイトの Web サイトとポータル サイト アプリの両方に適用されます。

ポータル サイトをカスタマイズすることで、エンド ユーザーの利便性を向上させることができます。 これを行うには、テナント管理者またはサービス管理者として [Microsoft Intune 管理コンソール](https://manage.microsoft.com)にサインインし、**[管理者]** &gt; **[ポータル サイト]** の順にクリックして、ポータル サイトの設定を構成します。

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

## デバイスの登録方法の概要

次の表は、企業所有デバイスの登録方法とその利点です。

**iOS の登録方法**

| **方法** |  **[ワイプ](#Wipe)** | **[アフィニティ](#Affinity)**   |   **[Locked](#Lock)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | ×|    ○ |   × |
|**[DEM](#DEM)**|   × |× |×  |
|**[DEP](#DEP)**|   ○ |   任意 |   任意|
|**[USB-SA](#USB-SA)**| ○ |   任意 |   ×|
|**[USB-Direct](#USB-Direct)**| × |    ×  | ×|

**Windows と Android の登録方法**

| **方法** |  **[ワイプ](#Wipe)** | **[アフィニティ](#Affinity)**   |   **[Locked](#Lock)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | ×|    ○ |   × |
|**[DEM](#DEM)**|   × |× |×  |

**デバイスの登録方法**

### BYOD
"Bring Your Own Device"。 ユーザーがポータル サイト アプリをインストールし、自分のデバイスを登録します。 デバイスをポータル サイトに登録すると、デバイスが社内参加されます。 iOS デバイスをポータル サイトに登録するには、Apple ID が必要です。 BYOD の場合、企業所有デバイスに追加の構成は必要ありません。 「[デバイス管理のセットアップ](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management)」手順を参照してください ([表に戻る](#overview-of-device-enrollment-methods))

### DEM
デバイス登録マネージャー。 管理者は、企業所有のデバイスを管理する DEM アカウントを作成します。 作成後は、マネージャーがポータル サイトをインストールし、多数のユーザーがいないデバイスを登録できます。 DEM の詳細については[ここ](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)を参照してください。 ([表に戻る](#overview-of-device-enrollment-methods))

### DEP
Apple Device Enrollment Program。 管理者がポリシーを作成し、DEP で管理する購入済みの企業所有 iOS デバイスに "無線で" ポリシーを展開します。 デバイスは、ユーザーが iOS のセットアップ アシスタントを実行するときに登録されます。 この方法は、**iOS 監督下**モードをサポートしているので、以下が有効になります。
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

**企業所有のモバイル デバイスの動作**

### ワイプ
デバイスを登録する場合、工場出荷時のリセットを実行してデバイスからすべてのデータを削除し、初期状態に戻す必要があるかどうかを指定します。
[デバイスを削除する](retire-devices-from-microsoft-intune-management.md) ([表に戻る](#overview-of-device-enrollment-methods))

### アフィニティ
デバイスを特定のユーザーと接続する "ユーザー アフィニティ" をサポートする登録方法かどうかを指定します。 "任意" デバイスは、ユーザー アフィニティの有無にかかわらず登録できます。 以下をサポートするには、ユーザー アフィニティが必要です。
  - モバイル アプリケーション管理 (MAM) アプリ
  - 電子メールと会社データへの条件付きアクセス
  - ポータル サイト アプリ

[ユーザー アフィニティ](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices) ([表に戻る](#overview-of-device-enrollment-methods))

### ロック
ユーザーが Intune ポリシーを削除して、実質的にデバイスが管理対象から外れないように、デバイスをロックするかどうかを指定します。 iOS デバイスの場合、デバイスをロックするには、監督下モードにする必要があります。
([表に戻る](#overview-of-device-enrollment-methods))

## デバイスの登録を可能にする  
 登録は、ユーザーが個人のデバイスで会社のリソースにアクセスできるようにし、これらのデバイスが会社のリソースを保護するポリシーに準拠していることを管理者が保証できるようにします。 これは、Intune で "私物のデバイスの持ち込み" シナリオを可能にする最善の方法です。 管理者は、Intune コンソールで登録を有効にする必要があります。これを行うには、デバイスとユーザーに割り当てるライセンスの間で信頼関係を作成しなければならないことがあります。 その後、デバイスが登録されますが、この操作は、通常はユーザーが自分の職場または学校の資格情報を入力することで行います。 これで、デバイスが Intune からポリシーを受信し、リソースへのアクセス許可を取得するようになります。

[Intune にデバイスを登録する準備](get-ready-to-enroll-devices-in-microsoft-intune.md)

## 企業所有のデバイスを登録する
企業所有のデバイス (COD) は、Intune コンソールで管理できます。 iOS デバイスは、Apple が提供するツールを通して直接登録できます。 管理者またはマネージャーは、デバイス登録マネージャーを使用して、すべてのデバイスの種類を登録できます。 IMEI 番号を持つデバイスを識別し、会社所有としてタグ付けして、COD シナリオで使用することもできます。

[企業所有のデバイスを登録する](manage-corporate-owned-devices.md)

## Exchange ActiveSync および Intune を使用したモバイル デバイス管理
登録されていないが Exchange ActiveSync (EAS) に接続するモバイル デバイスは、EAS MDM ポリシーを使用して Intune で管理できます。 Intune は、Exchange Connector を使用して、オンプレミスのまたはクラウドでホストされている EA と通信します。

[Exchange ActiveSync および Intune を使用したモバイル デバイス管理](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Intune を使用して Windows PC を管理する  
Microsoft Intune では、Intune Windows PC クライアント ソフトウェアを使用して Windows PC を管理することもできます。 Intune クライアントを使用して管理される PC では、次の操作を実行できます。

 - ソフトウェアおよびハードウェアのインベントリのレポート
 - デスクトップ アプリケーション (.exe ファイルや .msi ファイルなど) のインストール
 - ファイアウォール設定

Intune クライアント ソフトウェアを使用して管理されるコンピューターでは、選択的なワイプや削除は実行できません。さらに、条件付きアクセス、VPN と Wi-Fi の設定、証明書と電子メール構成の展開などの多数の Intune 管理機能を利用することはできません。

[Intune を使用して Windows PC を管理する](manage-windows-pcs-with-microsoft-intune.md)



<!--HONumber=Aug16_HO4-->


