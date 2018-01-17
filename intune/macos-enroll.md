---
title: "Intune で macOS デバイスを登録する"
titlesuffix: Azure portal
description: "Intune で macOS デバイスを登録する方法について説明します。\""
keywords: 
author: ErikjeMS
ms.author: erikje
nmanager: angrobe
ms.date: 10/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3d1382e85b9ce58cd65380a799ca8eb4da98b84c
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2018
---
# <a name="enroll-macos-devices-in-intune"></a>Intune で macOS デバイスを登録する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune では、macOS デバイスを管理することができます。 デバイスの管理を有効にするには、[ポータル Web サイト](http://portal.manage.microsoft.com)に移動し、画面の指示に従ってデバイスを登録する必要があります。 macOS デバイスを管理下に置いたら、[macOS デバイスのカスタム設定を作成](custom-settings-macos.md)できます。 その他の機能は近日公開予定です。

## <a name="prerequisites"></a>必要条件

macOS デバイスの登録を設定する前に、以下の前提条件を満たしている必要があります。

- [ドメインを構成する](custom-domain-name-configure.md)
- [MDM 機関を設定する](mdm-authority-set.md)
- [グループの作成](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [ポータル サイト アプリを構成する](company-portal-app.md)
- [Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)でユーザー ライセンスを割り当てる
- [Apple MDM プッシュ証明書を取得する](apple-mdm-push-certificate-get.md)

## <a name="set-up-macos-enrollment"></a>macOS の登録を設定する

Intune では、既定で macOS デバイスの登録が既に許可されています。

macOS デバイスの登録をブロックする場合は、「[Set device type restrictions](enrollment-restrictions-set.md)」 (デバイスの種類の制限を設定する) を参照してください。

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>デバイスを登録して会社のリソースにアクセスする方法をユーザーに知らせる

エンド ユーザーに対して、[ポータル Web サイト](http://portal.manage.microsoft.com)に移動し、画面の指示に従ってデバイスを登録するように指示してください。 オンライン登録の手順 (「[Intune に macOS デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)」) へのリンクを送信することもできます。

その他のエンドユーザー タスクの詳細については、次の記事を参照してください。

- [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](end-user-educate.md)
- [iOS デバイスまたは macOS デバイスを Intune で使用する](https://docs.microsoft.com/intune-user-help/using-your-ios-or-mac-os-x-device-with-intune)
