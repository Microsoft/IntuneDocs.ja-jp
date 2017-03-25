---
title: "Intune で Android デバイスを登録する"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Intune Azure プレビューで Android デバイスを登録する方法について説明します。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: b664620f424f9ef612d17beb810564dbdd68ff79
ms.lasthandoff: 03/22/2017


---

# <a name="enroll-android-devices"></a>Android デバイスの登録

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune では、Samsung Knox Standard デバイスを含む、Android デバイスを管理することができます。 デバイス管理を有効にするには、ユーザーは Intune ポータル サイト アプリ (Google Play から入手可能) をダウンロードし、アプリを開き、登録に関する画面の指示に従って、デバイスを登録する必要があります。 Android デバイスを管理下に置いたら、[コンプライアンス ポリシーの作成](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android)や[アプリの管理](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-management)などを行うことができます。

## <a name="prerequisite"></a>前提条件

モバイル デバイスの管理を準備するには、MDM 機関を **Microsoft Intune** に設定する必要があります。 手順については、[MDM 機関の設定](set-mdm-authority.md)に関するページを参照してください。 この項目は、モバイル デバイス管理について初めて Intune を設定するときに一度だけ設定します。したがって、これは既に設定されている可能性があります。

## <a name="set-up-android-enrollment"></a>Android の登録を設定する

Intune では、既定で Android および Samsung Knox Standard デバイスの登録が既に許可されています。

Android デバイスをブロックする場合や、個人所有の Android デバイスのみの登録をブロックする場合は、「[Set device type restrictions](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions)」 (デバイスの種類の制限を設定する) を参照してください。

ユーザーが登録できるデバイスの最大数を設定する場合は、「[Set device limit restrictions](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-limit-restrictions)」 (デバイス数の制限を設定する) を参照してください。

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>デバイスを登録して会社のリソースにアクセスする方法をユーザーに知らせる

Google Play に移動して Intune ポータル サイト アプリをダウンロードしてから、アプリを開き、画面の指示に従ってデバイスを登録するようにエンド ユーザーに指示する必要があります。 アプリに登録プロセスが示されます。このプロセスでは、登録により可能になる操作、および IT 管理者が見ることのできるデバイス上のデータと見ることのできないデータが説明されます。

オンライン登録の手順 (「[Intune に Android デバイスを登録する](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android)」) へのリンクを送信することもできます。

その他のエンドユーザー タスクの詳細については、次の記事を参照してください。

- [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)
- [Android デバイスを Intune で使用する](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)

