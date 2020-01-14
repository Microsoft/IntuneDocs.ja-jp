---
title: macOS デバイスの登録をセットアップする
titleSuffix: Microsoft Intune
description: Intune で macOS デバイスの登録をセットアップする方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cddb9b74d9132ace07c17a3156e61148b720d66
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207181"
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Intune で macOS デバイスの登録をセットアップする

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune を使用すると、macOS デバイスを管理して、会社の電子メールやアプリへのアクセスをユーザーに提供できます。

Intune 管理者は、会社所有の macOS デバイスと個人所有の macOS デバイス ("bring your own device" すなわち BYOD) の登録を設定できます。 

## <a name="prerequisites"></a>[前提条件]

macOS デバイスの登録を設定する前に、以下の前提条件を満たしている必要があります。

- [デバイスが Apple デバイス登録の対象であることを確認します](https://support.apple.com/en-us/HT204142#eligibility)。
- [ドメインを構成する](../fundamentals/custom-domain-name-configure.md)
- [MDM 機関を設定する](../fundamentals/mdm-authority-set.md)
- [グループの作成](../fundamentals/groups-add.md)
- [ポータル サイト アプリを構成する](../apps/company-portal-app.md)
- [Microsoft 365 管理センター](https://go.microsoft.com/fwlink/p/?LinkId=698854)でユーザー ライセンスを割り当てる
- [Apple MDM プッシュ証明書を取得する](../enrollment/apple-mdm-push-certificate-get.md)

## <a name="user-owned-macos-devices-byod"></a>ユーザー所有の macOS デバイス (BYOD)

ユーザーが自分の個人用デバイスを Intune の管理に登録できるようにすることができます。 これは、"bring your own device" または BYOD と呼ばれます。 前提条件を満たし、ユーザーにライセンスを割り当てると、ユーザーは次の方法で各自のデバイスを登録できます。
- [会社のポータル Web サイト](https://portal.manage.microsoft.com)にアクセスします。(または)
- [aka.ms/EnrollMyMac](https://aka.ms/EnrollMyMac) で Mac ポータル サイト アプリをダウンロードする。

また、オンライン登録手順へのリンクをユーザーに送信することもできます。(「[Intune に macOS デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)」) へのリンクを送信することもできます。

その他のエンドユーザー タスクの詳細については、次の記事を参照してください。

- [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](../fundamentals/end-user-educate.md)
- [macOS デバイスを Intune で使用する](/intune-user-help/using-your-macos-device-with-intune)

## <a name="company-owned-macos-devices"></a>会社所有の macOS デバイス
Intune は、ユーザーのデバイスを購入する組織のため、次の会社所有の macOS デバイスの登録方法をサポートします。
- [Apple の Device Enrollment Program (DEP)](device-enrollment-program-enroll-macos.md):組織は、Apple の Device Enrollment Program (DEP) を通して macOS デバイスを購入できます。 DEP では、登録プロファイルを “無線で” 展開して、デバイスを管理対象として登録できます。
- [デバイス登録マネージャー (DEM)](device-enrollment-manager-enroll.md):DEM アカウントを使用して、最大で 1,000 台のデバイスを登録できます。

## <a name="block-macos-enrollment"></a>macOS の登録をブロックする
既定では、Intune で macOS デバイスを登録できます。 macOS デバイスの登録をブロックする場合は、「[Set device type restrictions](enrollment-restrictions-set.md)」 (デバイスの種類の制限を設定する) を参照してください。

## <a name="enroll-virtual-macos-machines-for-testing"></a>テスト用に仮想 macOS マシンを登録する

> [!NOTE]
> macOS 仮想マシンは、テスト目的でのみサポートされます。 macOS 仮想マシンをエンドユーザーの実稼働デバイスとして使用しないでください。 

テスト目的の macOS 仮想マシンは、Parallels Desktop または VMware Fusion のいずれかを使用して登録することができます。 

Parallels Desktop の場合、Intune が認識できるように、ハードウェアの種類と仮想マシンのシリアル番号を設定する必要があります。 ハードウェアの種類と[シリアル番号](http://kb.parallels.com/123455)の設定に関する Parallels の指示に従って、テストに必要な設定を行います。 仮想マシンを実行しているデバイスのハードウェアの種類と、作成している仮想マシンのハードウェアの種類とを一致させることをお勧めします。 このハードウェアの種類は、 **[アップル メニュー]**  >  **[この Mac について]**  >  **[システム レポート]**  >  **[機種 ID]** で調べることができます。 

VMware Fusion の場合、[.vmx ファイルを編集して](https://kb.vmware.com/s/article/1014782)、仮想マシンのハードウェア モデルとシリアル番号を設定する必要があります。 仮想マシンを実行しているデバイスのハードウェアの種類と、作成している仮想マシンのハードウェアの種類とを一致させることをお勧めします。 このハードウェアの種類は、 **[アップル メニュー]**  >  **[この Mac について]**  >  **[システム レポート]**  >  **[機種 ID]** で調べることができます。 

## <a name="user-approved-enrollment"></a>ユーザー承認済みの登録
ユーザー承認済みの MDM 登録は、セキュリティ上重要な特定の設定を管理するために使用できる macOS の登録の種類です。 詳しくは、[Apple のサポート ドキュメント](https://support.apple.com/HT208019)をご覧ください。  
 
BYOD 登録プロセスの間に、ユーザーは Apple 管理プロファイルを手動で承認するように求められます。 手順は、macOS 用の Intune ポータル サイト アプリで示されます。 管理プロファイルの承認は登録を完了するために必要ではありませんが、登録を承認することをお勧めします。 登録の間にプロファイルを承認しなかった場合、ユーザーは、 **[System Preferences]\(システム設定\)**  >  **[プロファイル]** に移動し、管理プロファイルを選択して、 **[承認]** を選択できます。    

### <a name="find-out-if-a-device-is-user-approved"></a>デバイスがユーザー承認済みかどうかを確認する
1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]**  >  **[すべてのデバイス]** の順に選択してデバイスを選択し、 **[ハードウェア]** を選択します。
3. **[ユーザー承認済み登録]** フィールドを確認します。


## <a name="next-steps"></a>次のステップ

macOS デバイスを登録したら、[macOS デバイスのカスタム設定を作成](../configuration/custom-settings-macos.md)できます。
