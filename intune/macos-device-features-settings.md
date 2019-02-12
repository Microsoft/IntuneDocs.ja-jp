---
title: Microsoft Intune の macOS デバイスの機能設定 - Azure | Microsoft Docs
description: Microsoft Intune で AirPrint 用の macOS デバイスを構成するためのすべての設定について説明します。 また、ネットワーク内の AirPrint サーバーの IP アドレス、パス、およびポート設定を取得する手順についても説明します。 デバイス構成プロファイルでこれらの設定を使用して、ネットワーク内の AirPrint サーバーを使用するように macOS デバイスを構成します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db89dd2cce679597533d2861a43a7a2fd82abd14
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850575"
---
# <a name="macos-device-feature-settings-in-intune"></a>Intune での macOS デバイスの機能設定

Intune には、macOS ユーザーがネットワーク内の AirPrint プリンターに印刷できるようにする組み込み設定がいくつかあります。 この記事では、このような設定を一覧で示し、各設定の機能について説明します。 また、ターミナル アプリ (エミュレーター) を使って AirPrint プリンターの IP アドレス、パス、ポートを取得する手順についても説明します。

## <a name="before-you-begin"></a>始める前に

[macOS デバイス構成プロファイルを作成します](device-features-configure.md)。

## <a name="airprint-settings"></a>AirPrint の設定

1. **[設定]** で **[AirPrint]** を選択します。 AirPrint サーバーの次のプロパティを入力します。

    - **[IP アドレス]**: プリンターの IPv4 アドレスまたは IPv6 アドレスを入力します。 ホスト名を使用してプリンターを識別している場合は、ターミナル アプリでプリンターに ping を実行することで IP アドレスを取得できます。 詳細については、「[IP アドレスとパスを取得する](#get-the-ip-address-and-path)」(この記事) を参照してください。
    - **パス**:プリンターのパスを入力します。 通常、このパスはネットワーク上のプリンターの `ipp/print` です。 詳細については、「[IP アドレスとパスを取得する](#get-the-ip-address-and-path)」(この記事) を参照してください。
    - **ポート**:AirPrint の接続先のリスニング ポートを入力します。 このプロパティを空白のままにすると、AirPrint には既定のポートが使用されます。 iOS 11.0 以降で使用できます。
    - **TLS**:トランスポート層セキュリティ (TLS) で AirPrint の接続を保護するには、**[有効]** を選択します。 iOS 11.0 以降で使用できます。

2. **[追加]** を選択します。 AirPrint サーバーが一覧に追加されます。 多数の AirPrint サーバーを追加できます。

    AirPrint プリンターの一覧を含むコンマ区切りファイル (.csv) を **[インポート]** することもできます。 また、Intune に AirPrint プリンターを追加した後、この一覧を **[エクスポート]** することもできます。

3. 完了したら、**[OK]** を選択して一覧を保存します。

## <a name="get-the-ip-address-and-path"></a>IP アドレスとパスを取得する

AirPrinter サーバーを追加するには、プリンターの IP アドレス、リソース パス、およびポートが必要です。 この情報を取得する手順は次のとおりです。

1. AirPrint プリンターと同じローカル ネットワーク (サブネット) に接続している Mac 上で、(**/アプリケーション/ユーティリティ**から) **ターミナル**を開きます。
2. ターミナル アプリで「`ippfind`」と入力し、Enter キーを押します。

    プリンター情報をメモします。 たとえば、`ipp://myprinter.local.:631/ipp/port1` のような内容が返されます。 最初の部分はプリンターの名前です。 最後の部分 (`ipp/port1`) はリソース パスです。

3. ターミナルで「`ping myprinter.local`」と入力し、Enter キーを押します。

   IP アドレスをメモします。 たとえば、`PING myprinter.local (10.50.25.21)` のような内容が返されます。

4. この IP アドレスとリソース パスの値を使用します。 この例では、IP アドレスは `10.50.25.21`、リソース パスは `/ipp/port1` です。

## <a name="next-steps"></a>次の手順

- [iOS](ios-device-features-settings.md) デバイス用のすべての設定を確認します。
- このプロファイルをグループに割り当てます。[デバイス プロファイルの割り当て](device-profile-assign.md)に関するページを参照してください。
