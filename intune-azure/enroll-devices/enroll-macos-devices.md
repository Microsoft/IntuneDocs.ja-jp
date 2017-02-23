---
title: "Intune に macOS デバイスを登録する | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Intune Azure プレビューで macOS デバイスを登録する方法について説明します。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 1/3/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba2affcdbcdfcd690d671c7b20f9d1e14a74f764
ms.openlocfilehash: 171175689adca027181f3da4d05222117de97e13


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>Intune Azure プレビューで macOS デバイスを登録する

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune 管理者は、macOS デバイスを管理できます。 ユーザーは、既定で Azure Portal を使用して macOS デバイスを登録できます。 管理者は、ユーザーに対して、[ポータル Web サイト](http://portal.manage.microsoft.com)にアクセスして macOS デバイスを登録するよう通知するだけです。 

## <a name="prerequisites"></a>必要条件

macOS デバイスの登録を設定する前に、以下の前提条件を満たしている必要があります。

- [ドメインを構成する](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [MDM 機関を設定する](set-mdm-authority.md)
- [グループの作成](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [ポータル サイト アプリを構成する](/intune-azure/manage-apps/company-portal-app.md)
- [Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)でユーザー ライセンスを割り当てる
- [Apple MDM プッシュ証明書を取得する](get-an-apple-mdm-push-certificate.md)

## <a name="set-up-macos-enrollment"></a>macOS の登録を設定する

Intune では、既定で、macOS デバイスの登録を許可するように既に設定されています。 

macOS デバイスの登録を許可またはブロックする設定を確認するには、Azure Portal の [Intune] ブレードに移動し、**[登録]** > **[登録の制限]** の順に選択します。 

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>デバイスを登録して会社のリソースにアクセスする方法をユーザーに知らせる

エンドユーザー用の登録手順については、「[Intune に macOS デバイスを登録する](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos)」を参照してください。 登録プロセスでは、登録により可能になる操作、および IT 管理者が見ることのできるデバイス上のデータと見られないデータについての説明が行われます。

その他のエンドユーザー タスクの詳細については、次の記事を参照してください。

- [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [iOS デバイスまたは macOS デバイスを Intune で使用する](https://docs.microsoft.com/intune/enduser/using-your-ios-or-mac-os-x-device-with-intune)


<!--HONumber=Feb17_HO1-->


