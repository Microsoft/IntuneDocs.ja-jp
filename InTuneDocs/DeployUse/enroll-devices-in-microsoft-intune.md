---
# required metadata

title: デバイスを登録する | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: damionw
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 管理するデバイスを Intune に登録する
Microsoft Intune のモバイル デバイス管理 (MDM) では、登録を使用してデバイスを管理対象にし、リソースへのアクセスを許可します。 デバイスの登録方法は、デバイスの種類、所有権、および必要な管理レベルによって決まります。 "私物のデバイスの持ち込み" (BYOD) と企業所有のデバイス (COD) を使用するシナリオでは、登録プロセスが必要です。 オンプレミスの、またはクラウドでホストされている Exchange ActiveSync を使用している組織は、登録要件のない軽い管理が可能です。 Windows PC は、Intune クライアント ソフトウェアを使用して管理することもできます。

###  サポートされるデバイス プラットフォーム

Intune では、次のデバイス プラットフォームを管理できます。

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

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


<!--HONumber=Jun16_HO2-->


