---
title: "Intune で iOS デバイスの登録方法を選択する"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Microsoft Intune で iOS デバイスの登録を設定する方法について説明します。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 748f5b6e18b7bc6d9e9d3e6635ac2c3e7eb11a67
ms.lasthandoff: 02/18/2017


---

# <a name="choose-how-to-enroll-ios-devices"></a>iOS デバイスの登録方法を選択する

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

このトピックでは、iOS デバイスの登録方法と登録の前提条件について説明します。

次の情報を使用して、どの方法で iOS デバイスを登録するかを判断してください。 ここで紹介する登録方法はすべて (BYOD を除く)、企業所有のデバイスを対象としています。

**前提条件:** [Apple Push Notification サービス証明書](get-an-apple-mdm-push-certificate.md)が必要です。

## <a name="user-owned-ios-devices-byod"></a>ユーザー所有の iOS デバイス (BYOD)

個人の BYOD (Bring Your Own Device) デバイスを登録する場合は、ユーザーがアプリ ストアから iOS 向けポータル サイト アプリをダウンロードし、そのアプリに示されている登録手順に従う必要があります。 登録後、ユーザーは社内ネットワークに接続し、ドメインまたは Azure Active Directory に参加して、企業リソースにアクセスできるようになります。 個人所有の iOS デバイスの登録をブロックすることができます。 その手順については、「[Set device type restrictions](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions)」 (デバイスの種類の制限を設定する) を参照してください。

## <a name="apple-configurator"></a>Apple Configurator

会社の登録プロファイルをエクスポートし、[Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) を実行している Mac にモバイル デバイスを接続することで、iOS デバイスを登録できます。 Apple Configurator では、2 つの形式の登録がサポートされています。

- **セットアップ アシスタントを使用した登録**: デバイスを出荷時の設定に戻し、デバイスの新しいユーザーがセットアップできるようにします。 この方法では、管理者は Apple Configurator を実行している Mac コンピューターに iOS デバイスを USB で接続して、登録を事前構成する必要があります。 その後、デバイスをユーザーに配布し、ユーザーがセットアップ アシスタント プロセスを実行します。 このプロセスで、デバイスをユーザーの職場または学校の資格情報で構成し、登録プロセスを完了します。 詳細については、「[Apple Configurator とセットアップ アシスタントを使用して iOS デバイスを登録する](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)」を参照してください。

- **直接登録** - デバイスの準備で使用する Apple Configurator 準拠ファイルを作成します。 登録対象デバイスは出荷時の設定に戻されません。また、ユーザーの関連付け情報は含まれません。 デバイスを登録するために、管理者は Apple Configurator を実行している Mac コンピューターに iOS デバイスを USB で接続する必要があります。 詳しくは、[Apple Configurator の直接登録を使用した iOS デバイスの登録](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md)に関するページを参照してください。

## <a name="use-the-device-enrollment-program-dep"></a>Device Enrollment Program (DEP) のサポートを使用する場合

DEP では、DEP を通じて購入したデバイスに "無線で" 登録プロファイルが展開されます。 ユーザーがデバイスでセットアップ アシスタントを実行すると、デバイスが Intune に登録されます。 DEP を使用して登録したデバイスの場合は、ユーザーが登録を解除することはできません。 詳細については、「[Device Enrollment Program を使用して iOS デバイスを登録する](enroll-ios-devices-using-device-enrollment-program.md)」を参照してください。

## <a name="use-the-device-enrollment-manager-dem"></a>デバイス登録マネージャー (DEM) の使用
デバイス登録マネージャーは、最大 1,000 台のデバイスを登録して管理できるユーザー アカウントの種類です。 こうした機能を既存のユーザーに提供するには、そのユーザーを DEM アカウントに追加します。 DEM ユーザーの登録デバイスごとに&1; つの Intune ライセンスが使用されます。 詳細については、「[デバイス登録マネージャーを使用してデバイスを登録する](enroll-devices-using-device-enrollment-manager.md)」を参照してください。

