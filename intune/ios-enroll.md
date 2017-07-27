---
title: "Intune で Windows デバイスの登録方法を選択する"
titleSuffix: Intune on Azure
description: "Microsoft Intune で Windows デバイスの登録を設定する方法について説明します。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 61bdbc7ca68995e23295cf099ce73dfdcaeba37c
ms.sourcegitcommit: 5eb209ae48173ddfdbbab131f12f3ac3498dcd87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2017
---
# <a name="enroll-ios-devices-in-intune"></a>Intune で iOS デバイスを登録する

Intune では、iPad および iPhone のモバイル デバイス管理 (MDM) が有効になり、会社の電子メールおよびアプリへのアクセス権がユーザーに付与されます。

Intune 管理者として、iOS デバイスの登録を有効にすることができます。 "Bring Your Own Device" (BYOD) の登録と呼ばれる、個人所有のデバイスをユーザーが登録することを許可できます。 会社所有デバイスの登録を有効にすることもできます。

## <a name="prerequisites-for-ios-enrollment"></a>iOS の登録の前提条件
iOS デバイスを有効にする前に、次の手順を完了する必要があります。
- [Intune のセットアップ](setup-steps.md) - この手順で、Intune インフラストラクチャをセットアップします。 特に、デバイスの登録には [MDM 機関を設定する](mdm-authority-set.md)必要があります。
- [Apple MDM プッシュ通知証明書の取得](apple-mdm-push-certificate-get.md) - Apple では、iOS および macOS デバイスの管理を有効にするために証明書が必要です。

前提条件を満たした後に、ユーザーは会社ポータル アプリをインストールして自分の iOS デバイスを登録できます。または管理者が企業所有の iOS デバイス管理をセットアップできます。 また、管理者は、1 つの管理アカウントを使って複数のデバイスを登録できる、[デバイス登録マネージャー](device-enrollment-manager-enroll.md)を割り当てることもできます。 Intune では、次の iOS の会社所有デバイスの登録方法をサポートします。

## <a name="device-enrollment-program"></a>デバイス登録プログラム
組織は、Apple の Device Enrollment Program (DEP) を通して iOS デバイスを購入できます。 DEP では、登録プロファイルを “無線で” 展開して、デバイスを管理対象として登録できます。 詳細については、[Device Enrollment Program](device-enrollment-program-enroll-ios.md) に関するページを参照してください。

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager は、学校向けのデバイス購入と登録プログラムです。 DEP と同様に、プロファイルを展開して管理にデバイスを登録できます。 詳細については、[Apple School Manager](apple-school-manager-set-up-ios.md) に関するページを参照してください。

## <a name="apple-configurator"></a>Apple Configurator
Mac コンピューターで実行している Apple Configurator を使って、iOS デバイスを登録することができます。 デバイスを準備するには、デバイスを USB 接続して、登録プロファイルをインストールします。 Apple Configurator では、次の 2 つの方法でデバイスを登録することができます。
- セットアップ アシスタントの登録 - デバイスを工場出荷時の設定にリセットし、セットアップ アシスタントを実行する準備を行い、デバイスの新しいユーザー用に会社のポリシーをインストールします。
- 直接登録 - デバイスを工場出荷時の設定に戻さず、定義済みのポリシーでデバイスを登録します。 この方法は、ユーザー アフィニティなしのデバイス向けです。

詳細については、[Apple Configurator の登録](apple-configurator-setup-assistant-enroll-ios.md)に関するページを参照してください。
