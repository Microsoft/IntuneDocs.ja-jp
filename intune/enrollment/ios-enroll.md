---
title: Intune で iOS デバイスを登録する
titleSuffix: Microsoft Intune
description: Microsoft Intune で iOS デバイスの登録をセットアップします。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 80b9091b723e78631a13c9358687ae77c36b8d47
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722450"
---
# <a name="enroll-ios-devices-in-intune"></a>Intune で iOS デバイスを登録する

Intune では、iPad および iPhone のモバイル デバイス管理 (MDM) が有効になり、会社の電子メールおよびアプリへのアクセス権がユーザーに付与されます。

Intune 管理者として、iOS デバイスの登録を有効にすることができます。 "Bring Your Own Device" (BYOD) の登録と呼ばれる、個人所有のデバイスをユーザーが登録することを許可できます。 会社所有デバイスの登録を有効にすることもできます。

## <a name="prerequisites-for-ios-enrollment"></a>iOS の登録の前提条件

iOS デバイスを有効にする前に、次の手順を完了する必要があります。

- [デバイスが Apple デバイス登録の対象であることを確認します](https://support.apple.com/en-us/HT204142#eligibility)。
- [Intune のセットアップ](../fundamentals/setup-steps.md) - この手順で、Intune インフラストラクチャをセットアップします。 特に、デバイスの登録には [MDM 機関を設定する](../fundamentals/mdm-authority-set.md)必要があります。
- [Apple MDM プッシュ通知証明書の取得](apple-mdm-push-certificate-get.md) - Apple では、iOS および macOS デバイスの管理を有効にするために証明書が必要です。

## <a name="user-owned-ios-devices-byod"></a>ユーザー所有の iOS デバイス (BYOD)

Intune 管理のために、ユーザーに個人用デバイスを登録させることができます。これは "Bring Your Own Device" (BYOD) と呼ばれます。 前提条件を満たし、ユーザーのライセンスを割り当てたら、アプリ ストアから Intune ポータル サイト アプリをダウンロードして、アプリの登録手順に従います。 [プライバシーに関する声明のカスタマイズ](../apps/company-portal-app.md#privacy-statement-customization)に関するページで説明されているように、iOS デバイス上でポータル サイトのプライバシーに関する声明をカスタマイズできます。

## <a name="company-owned-ios-devices"></a>会社所有の iOS デバイス

Intune は、ユーザーのデバイスを購入する組織のため、次の会社所有の iOS デバイスの登録方法をサポートします。

- Apple の Device Enrollment Program (DEP)
- Apple School Manager
- Apple Configurator セットアップ アシスタントでの登録
- Apple Configurator の直接登録

[デバイス登録マネージャー](device-enrollment-manager-enroll.md)のアカウントで会社所有の iOS デバイスを登録することもできます。

## <a name="device-enrollment-program"></a>デバイス登録プログラム

組織は、Apple の Device Enrollment Program (DEP) を通して iOS デバイスを購入できます。 DEP では、登録プロファイルを “無線で” 展開して、デバイスを管理対象として登録できます。 詳細については、[Device Enrollment Program](device-enrollment-program-enroll-ios.md) に関するページを参照してください。

## <a name="apple-school-manager"></a>Apple School Manager

Apple School Manager は、学校向けのデバイス購入と登録プログラムです。 DEP と同様に、プロファイルを展開して管理にデバイスを登録できます。 詳細については、[Apple School Manager](apple-school-manager-set-up-ios.md) に関するページを参照してください。

## <a name="apple-configurator"></a>Apple Configurator

Mac コンピューターで実行している Apple Configurator を使って、iOS デバイスを登録することができます。 デバイスを準備するには、デバイスを USB 接続して、登録プロファイルをインストールします。 Apple Configurator では、次の 2 つの方法でデバイスを登録することができます。

- セットアップ アシスタントの登録 - デバイスをワイプし、セットアップ アシスタントを実行する準備を行い、デバイスの新しいユーザー用に会社のポリシーをインストールします。
- 直接登録 - デバイスをワイプせず、定義済みのポリシーでデバイスを登録します。 この方法は、ユーザー アフィニティなしのデバイス向けです。

詳細については、[Apple Configurator の登録](apple-configurator-enroll-ios.md)に関するページを参照してください。

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>DEP または Apple Configurator で登録されたデバイスでのポータル サイトの使用

ユーザー アフィニティが構成されているデバイスは、会社のポータル アプリをインストールして実行することにより、アプリをダウンロードしてデバイスを管理できるようになります。 ユーザーは、デバイスを受け取った後、セットアップ アシスタントを完了してポータル サイト アプリをインストールするために、いくつもの追加の手順を完了する必要があります。

以下をサポートするには、ユーザー アフィニティが必要です。

- モバイル アプリケーション管理 (MAM) アプリ
- 電子メールと会社データへの条件付きアクセス
- ポータル サイト アプリ

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>ユーザー アフィニティありで企業所有 iOS デバイスを登録する方法

1. ユーザーは、デバイスの電源をオンにすると、セットアップ アシスタントを完了するように求められます。
2. セットアップが完了すると、ユーザーは Apple ID を要求されます。 デバイスでポータル サイトをインストールできるように、Apple ID を入力する必要があります。
3. iOS デバイスは、App Store からポータル サイト アプリを自動的にインストールします。
4. ユーザーは、ポータル サイト アプリを起動し、Intune のサブスクリプションに関連付けられている資格情報 (一意の個人名や UPN など) を使用してサインインする必要があります。
5. ログインしたら、登録は完了です。 このデバイスのすべての機能を使用できるようになります。

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>ユーザー アフィニティなしの企業所有のマネージド デバイスについて

ユーザー アフィニティなしで構成されているデバイスではポータル サイトはサポートされません。そのようなデバイスにはポータル サイト アプリをインストールしないでください。 ポータル サイトは、会社の資格情報を持ち、カスタマイズされた企業リソース (電子メールなど) へのアクセスを必要とするユーザー向けです。 ユーザー アフィニティなしで登録されたデバイスは、専用ユーザー サインインのためのデバイスではありません。 ユーザー アフィニティなしで登録されているデバイスの一般的な使用例としては、キオスクや販売時点管理 (POS)、共有ユーティリティのデバイスがあります。

ユーザー アフィニティが必要な場合は、デバイスを登録する前に、デバイスの登録プロファイルで **[ユーザー アフィニティ]** が選択されていることを確認してください。 デバイスのアフィニティの状態を変更するには、デバイスをインベントリから削除してから再登録する必要があります。

## <a name="see-also"></a>関連項目

[Microsoft Intune での iOS デバイス登録の問題に関するトラブルシューティング](https://support.microsoft.com/help/4039809)
