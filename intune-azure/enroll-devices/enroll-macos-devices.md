---
title: "Intune で macOS デバイスを登録する"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Intune Azure プレビューで macOS デバイスを登録する方法について説明します。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: 3ef80446889e40464aed39fc83d9777dbfcc4d11
ms.lasthandoff: 03/22/2017


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>Intune Azure プレビューで macOS デバイスを登録する

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune では、macOS デバイスを管理することができます。 デバイスの管理を有効にするには、[ポータル Web サイト](http://portal.manage.microsoft.com)に移動し、画面の指示に従ってデバイスを登録する必要があります。 macOS デバイスを管理下に置いたら、[macOS デバイスのカスタム設定を作成](https://docs.microsoft.com/intune-azure/configure-devices/custom-for-macos)できます。 その他の機能は近日公開予定です。

## <a name="prerequisites"></a>必要条件

macOS デバイスの登録を設定する前に、以下の前提条件を満たしている必要があります。

- [ドメインを構成する](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [MDM 機関を設定する](set-mdm-authority.md)
- [グループの作成](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [ポータル サイト アプリを構成する](/intune-azure/manage-apps/company-portal-app.md)
- [Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)でユーザー ライセンスを割り当てる
- [Apple MDM プッシュ証明書を取得する](get-an-apple-mdm-push-certificate.md)

## <a name="set-up-macos-enrollment"></a>macOS の登録を設定する

Intune では、既定で macOS デバイスの登録が既に許可されています。

macOS デバイスの登録をブロックする場合は、「[Set device type restrictions](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions)」 (デバイスの種類の制限を設定する) を参照してください。

ユーザーが登録できるデバイスの最大数を設定する場合は、「[Set device limit restrictions](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-limit-restrictions)」 (デバイス数の制限を設定する) を参照してください。

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>デバイスを登録して会社のリソースにアクセスする方法をユーザーに知らせる

エンド ユーザーに対して、[ポータル Web サイト](http://portal.manage.microsoft.com)に移動し、画面の指示に従ってデバイスを登録するように指示する必要があります。 オンライン登録の手順 (「[Intune に macOS デバイスを登録する](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos)」) へのリンクを送信することもできます。

その他のエンドユーザー タスクの詳細については、次の記事を参照してください。

- [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)
- [iOS デバイスまたは macOS デバイスを Intune で使用する](https://docs.microsoft.com/intune/enduser/using-your-ios-or-mac-os-x-device-with-intune)

