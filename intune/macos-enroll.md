---
title: macOS デバイスの登録をセットアップする
titlesuffix: Microsoft Intune
description: Intune で macOS デバイスの登録をセットアップする方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4f8cddb69ac85e45acde8a846df3b5413c3b75bf
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Intune で macOS デバイスの登録をセットアップする

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune では、macOS デバイスを管理することができます。 デバイスの管理を有効にするには、[ポータル Web サイト](http://portal.manage.microsoft.com)に移動し、画面の指示に従ってデバイスを登録する必要があります。 macOS デバイスを管理下に置いたら、[macOS デバイスのカスタム設定を作成](custom-settings-macos.md)できます。 その他の機能は近日公開予定です。

## <a name="prerequisites"></a>必要条件

macOS デバイスの登録を設定する前に、以下の前提条件を満たしている必要があります。

- [ドメインを構成する](custom-domain-name-configure.md)
- [MDM 機関を設定する](mdm-authority-set.md)
- [グループの作成](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [ポータル サイト アプリを構成する](company-portal-app.md)
- [Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)でユーザー ライセンスを割り当てる
- [Apple MDM プッシュ証明書を取得する](apple-mdm-push-certificate-get.md)

## <a name="user-owned-ios-devices-byod"></a>ユーザー所有の iOS デバイス (BYOD)

Intune 管理のために、ユーザーに個人用デバイスを登録させることができます。これは "Bring Your Own Device" (BYOD) と呼ばれます。 前提条件を満たし、ユーザーのライセンスを割り当てたら、アプリ ストアから macOS ポータル サイト アプリをダウンロードして、アプリの登録手順に従います。

## <a name="company-owned-ios-devices"></a>会社所有の iOS デバイス
Intune は、ユーザーのデバイスを購入する組織のため、[デバイス登録マネージャー](device-enrollment-manager-enroll.md) アカウントを使用する会社所有の macOS デバイスの登録をサポートします。

## <a name="set-up-macos-enrollment"></a>macOS の登録を設定する

Intune では、既定で macOS デバイスの登録が既に許可されています。

macOS デバイスの登録をブロックする場合は、「[Set device type restrictions](enrollment-restrictions-set.md)」 (デバイスの種類の制限を設定する) を参照してください。

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>デバイスを登録して会社のリソースにアクセスする方法をユーザーに知らせる

エンド ユーザーに対して、[ポータル Web サイト](https://portal.manage.microsoft.com)に移動し、画面の指示に従ってデバイスを登録するように指示してください。 オンライン登録の手順 (「[Intune に macOS デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)」) へのリンクを送信することもできます。

その他のエンドユーザー タスクの詳細については、次の記事を参照してください。

- [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](end-user-educate.md)
- [macOS デバイスを Intune で使用する](/intune-user-help/using-your-macos-device-with-intune)

## <a name="enroll-virtual-macos-machines-for-testing"></a>テスト用に仮想 macOS マシンを登録する

> [!NOTE]
> macOS 仮想マシンは、テスト目的でのみサポートされます。 macOS 仮想マシンをエンドユーザーの実稼働デバイスとして使用しないでください。 

テスト目的の macOS 仮想マシンは、Parallels Desktop または VMware Fusion のいずれかを使用して登録することができます。 

Parallels Desktop の場合、Intune が認識できるように、ハードウェアの種類と仮想マシンのシリアル番号を設定する必要があります。 [ハードウェアの種類の設定](http://kb.parallels.com/123594)と[シリアル番号](http://kb.parallels.com/123455)に関する Parallels の指示に従って、テストに必要な設定を設定します。 仮想マシンを実行しているデバイスのハードウェアの種類と、作成している仮想マシンのハードウェアの種類とを一致させることをお勧めします。 このハードウェアの種類は、**[アップル メニュー]** > **[この Mac について]** > **[システム レポート]** > **[機種 ID]** で調べることができます。 

VMware Fusion の場合、[.vmx ファイルを編集して](https://kb.vmware.com/s/article/1014782)、仮想マシンのハードウェア モデルとシリアル番号を設定する必要があります。 仮想マシンを実行しているデバイスのハードウェアの種類と、作成している仮想マシンのハードウェアの種類とを一致させることをお勧めします。 このハードウェアの種類は、**[アップル メニュー]** > **[この Mac について]** > **[システム レポート]** > **[機種 ID]** で調べることができます。 

## <a name="user-approved-enrollment"></a>ユーザー承認済みの登録

ユーザー承認済みの MDM 登録は、セキュリティ上重要な特定の設定を管理するために使用できる macOS の登録の種類です。 詳しくは、[Apple のサポート ドキュメント](https://support.apple.com/HT208019)をご覧ください。

ユーザー承認済みにするには、エンド ユーザーが、macOS ポータル サイトを使って登録した後、[システム環境設定] を使って手動で承認する必要があります。 macOS ポータル サイトでは、macOS 10.13.2 以降のユーザー向けに、これを行う方法の説明が提供されています。

デバイスがユーザー承認済みかどうかを確認するには、Intune ポータルに移動し、**[デバイス]** > **[すべてのデバイス]** の順に選び、デバイスを選んで、**[ハードウェア]** を選びます。 **[User Approved]\(ユーザー承認済み\)** フィールドを確認します。