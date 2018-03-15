---
title: "Intune で iOS デバイスの登録方法を選択する"
titlesuffix: Microsoft Intune
description: "Microsoft Intune で iOS デバイスの登録をセットアップします。"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e79122c1bea970525faaf443f9bf4271d050abe2
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="enroll-ios-devices-in-intune"></a>Intune で iOS デバイスを登録する

Intune では、iPad および iPhone のモバイル デバイス管理 (MDM) が有効になり、会社の電子メールおよびアプリへのアクセス権がユーザーに付与されます。

Intune 管理者として、iOS デバイスの登録を有効にすることができます。 "Bring Your Own Device" (BYOD) の登録と呼ばれる、個人所有のデバイスをユーザーが登録することを許可できます。 会社所有デバイスの登録を有効にすることもできます。

## <a name="prerequisites-for-ios-enrollment"></a>iOS の登録の前提条件
iOS デバイスを有効にする前に、次の手順を完了する必要があります。
- [Intune のセットアップ](setup-steps.md) - この手順で、Intune インフラストラクチャをセットアップします。 特に、デバイスの登録には [MDM 機関を設定する](mdm-authority-set.md)必要があります。
- [Apple MDM プッシュ通知証明書の取得](apple-mdm-push-certificate-get.md) - Apple では、iOS および macOS デバイスの管理を有効にするために証明書が必要です。

## <a name="user-owned-ios-devices-byod"></a>ユーザー所有の iOS デバイス (BYOD)

Intune 管理のために、ユーザーに個人用デバイスを登録させることができます。これは "Bring Your Own Device" (BYOD) と呼ばれます。 前提条件を満たし、ユーザーのライセンスを割り当てたら、アプリ ストアから Intune ポータル サイト アプリをダウンロードして、アプリの登録手順に従います。

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
- セットアップ アシスタントの登録 - デバイスを工場出荷時の設定にリセットし、セットアップ アシスタントを実行する準備を行い、デバイスの新しいユーザー用に会社のポリシーをインストールします。
- 直接登録 - デバイスを工場出荷時の設定に戻さず、定義済みのポリシーでデバイスを登録します。 この方法は、ユーザー アフィニティなしのデバイス向けです。

詳細については、[Apple Configurator の登録](apple-configurator-setup-assistant-enroll-ios.md)に関するページを参照してください。

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>DEP または Apple Configurator で登録されたデバイスでのポータル サイトの使用

ユーザー アフィニティが構成されたデバイスでは、ポータル サイト アプリをインストールして実行し、アプリをダウンロードしてデバイスを管理できます。 ユーザーは、デバイスを受け取った後、セットアップ アシスタントを完了してポータル サイト アプリをインストールするために、いくつもの追加の手順を完了する必要があります。

以下をサポートするには、ユーザー アフィニティが必要です。
  - モバイル アプリケーション管理 (MAM) アプリ
  - 電子メールと会社データへの条件付きアクセス
  - ポータル サイト アプリ

**ユーザー アフィニティありで企業所有 iOS デバイスを登録する方法**
1. ユーザーは、デバイスの電源をオンにすると、セットアップ アシスタントを完了するように求められます。 セットアップ中にユーザーは資格情報を要求されます。 Intune のサブスクリプションに関連付けられている資格情報 (つまり一意の個人名または UPN) を使用する必要があります。

2. セットアップ中にユーザーは Apple ID を要求されます。 デバイスでポータル サイトをインストールできるように、Apple ID を入力する必要があります。 この ID は、セットアップの完了後に iOS の設定メニューから入力することもできます。

3. セットアップが完了したら、iOS デバイスで App Store からポータル サイト アプリをインストールする必要があります。

4. これでユーザーは、デバイスを設定するときに使用した UPN を使用して、ポータル サイトにサインインできるようになります。

5. ユーザーはログインすると、デバイスを登録するように求められます。 最初の手順は、デバイスを指定することです。 アプリには、ユーザーの Intune アカウントに割り当てられている企業登録済みの iOS デバイスの一覧が表示されます。 一致するデバイスを選択する必要があります。

  ユーザーのデバイスがまだ企業登録済みでない場合は、**[新しいデバイス]** を選択して標準の登録フローを行う必要があります。

6. 次の画面で、ユーザーは、新しいデバイスのシリアル番号を確認する必要があります。 **[シリアル番号を確認]** リンクをタップすると、設定アプリを使用してシリアル番号を確認するための説明が起動します。 その後、ポータル サイト アプリにシリアル番号の最後の 4 文字を入力する必要があります。

  この手順では、デバイスが Intune に登録されている会社のデバイスであることが確認されます。 デバイスのシリアル番号が一致しない場合は、間違ったデバイスが選択されています。 その場合は、前の画面に戻って、別のデバイスを選択する必要があります。

7. シリアル番号が確認されると、ポータル サイト アプリはポータル サイトの Web サイトにリダイレクトされ、登録の最終処理が行われます。 Web サイトでは、ユーザーにアプリに戻るように促すメッセージが表示されます。

8. これで登録が完了します。 これで、このデバイスのすべての機能を使用できるようになります。

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>ユーザー アフィニティなしの企業所有の管理対象デバイスについて

ユーザー アフィニティなしで構成されているデバイスではポータル サイトはサポートされません。そのようなデバイスにはポータル サイト アプリをインストールしないでください。 会社ポータルは、会社の資格情報を持ち、カスタマイズされた企業リソース (電子メールなど) へのアクセスを必要とするユーザー向けです。 ユーザー アフィニティなしで登録されたデバイスは、専用ユーザー サインインのためのデバイスではありません。 ユーザー アフィニティなしで登録されているデバイスの一般的な使用例としては、キオスクや販売時点管理 (POS)、共有ユーティリティのデバイスがあります。

ユーザー アフィニティが必要な場合は、デバイスを登録する前に、デバイスの登録プロファイルで **[ユーザー アフィニティ]** が選択されていることを確認してください。 デバイスのアフィニティの状態を変更するには、デバイスをインベントリから削除してから再登録する必要があります。

