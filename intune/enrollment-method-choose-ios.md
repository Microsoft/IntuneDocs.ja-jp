---
title: "Intune で iOS デバイスの登録方法を選択する"
titleSuffix: Intune on Azure
description: "Microsoft Intune で iOS デバイスの登録を設定する方法について説明します。\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 092f582cf30210858bd8cdd3879edfa873523ccb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="choose-how-to-enroll-ios-and-macos-devices"></a>iOS と macOS デバイスの登録方法を選択する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

このトピックでは、IT 管理者が Intune で iOS デバイスの登録を有効にするために使用できる方法について説明します。

次の情報を使用して、どの方法で iOS デバイスを登録するかを判断してください。 ここで紹介する登録方法はすべて (BYOD を除く)、会社所有のデバイスを対象としています。

**前提条件:** [Apple Push Notification サービス証明書](apple-mdm-push-certificate-get.md)が必要です。

## <a name="user-owned-ios-devices-byod"></a>ユーザー所有の iOS デバイス (BYOD)

個人の BYOD (Bring Your Own Device) デバイスを登録する場合は、ユーザーはアプリ ストアから iOS 向けポータル サイト アプリをダウンロードし、そのアプリに示されている登録手順に従います。 登録後、ユーザーは社内ネットワークに接続し、ドメインまたは Azure Active Directory に参加して、会社のリソースにアクセスできるようになります。 BYOD を有効にするための唯一の要件は [Apple Push Notification サービス証明書](apple-mdm-push-certificate-get.md)です。 また、個人所有の iOS デバイスの登録をブロックできます。 その手順については、「[Set device type restrictions](enrollment-restrictions-set.md)」 (デバイスの種類の制限を設定する) をご覧ください。

## <a name="user-owned-macos-devices-byod"></a>ユーザー所有の macOS デバイス (BYOD)

macOS デバイスの登録を有効にすることができます。 macOS の登録を有効にするための唯一の要件は [Apple Push Notification サービス証明書](apple-mdm-push-certificate-get.md)です。 詳細については、[macOS デバイスの登録](./macos-enroll.md)に関するページをご覧ください。

## <a name="enrollment-program-with-apple"></a>Apple での登録プログラム
Apple では、デバイスの登録と管理インフラストラクチャを含むデバイス購入プログラムを提供しています。 これらのプログラムのいずれかで購入したデバイスは、Intune 管理にデバイスのシリアル番号を割り当てることにより、"無線" で一括登録できます。

- **Device Enrollment Program (DEM)** - Apple による組織と企業向けのデバイス登録プログラムです。 詳細については、「[Device Enrollment Program を使用して iOS デバイスを登録する](device-enrollment-program-enroll-ios.md)」を参照してください。
- **Apple School Manager** - Apple による学校向けのデバイス登録プログラムです。 詳細については、「[Apple School Manager での iOS デバイス登録の有効化](apple-school-manager-set-up-ios.md)」をご覧ください。

## <a name="apple-configurator"></a>Apple Configurator

会社の登録プロファイルをエクスポートし、Apple Configurator を実行している Mac にモバイル デバイスを接続することで、iOS デバイスを登録できます。 Apple Configurator では、2 つの形式の登録がサポートされています。

- **セットアップ アシスタントを使用した登録**: デバイスを出荷時の設定に戻し、デバイスの新しいユーザーがセットアップできるようにします。 この方法では、管理者は Apple Configurator を実行している Mac コンピューターに iOS デバイスを USB で接続して、登録を事前構成する必要があります。 その後、デバイスをユーザーに配布し、ユーザーはデバイスの初回起動時にセットアップ アシスタントを実行します。 このプロセスで、デバイスをユーザーの職場または学校の資格情報で構成し、登録プロセスを完了します。 詳細については、「[Apple Configurator とセットアップ アシスタントを使用して iOS デバイスを登録する](apple-configurator-setup-assistant-enroll-ios.md)」を参照してください。

- **直接登録** - デバイスの準備で使用する Apple Configurator 準拠ファイルを作成します。 登録対象デバイスは出荷時の設定に戻されません。また、ユーザーの関連付け情報は含まれません。 デバイスを登録するために、管理者は Apple Configurator を実行している Mac コンピューターに iOS デバイスを USB で接続する必要があります。 詳しくは、[Apple Configurator の直接登録を使用した iOS デバイスの登録](apple-configurator-direct-enroll-ios.md)に関するページを参照してください。

## <a name="use-the-device-enrollment-program-dep"></a>Device Enrollment Program (DEP) のサポートを使用する場合

DEP では、DEP を通じて購入したデバイスに "無線で" 登録プロファイルが展開されます。 ユーザーがデバイスの初回起動時にセットアップ アシスタントを実行すると、デバイスが Intune に登録されます。 詳細については、「[Device Enrollment Program を使用して iOS デバイスを登録する](device-enrollment-program-enroll-ios.md)」を参照してください。

## <a name="use-the-device-enrollment-manager-dem"></a>デバイス登録マネージャー (DEM) の使用
デバイス登録マネージャーとは、最大 1,000 台のデバイスを登録および管理できる汎用ユーザー アカウントです。 DEM で管理されたデバイスではユーザー アフィニティを持てないため、そのデバイスに所有者が存在することはありません。 Intune ユーザーに DEM アクセス許可を与えることで、これらの機能を付与します。 DEM ユーザーが登録するデバイスごとに、1 つの Intune ライセンスが使用されます。 詳細については、「[デバイス登録マネージャーを使用してデバイスを登録する](device-enrollment-manager-enroll.md)」を参照してください。
