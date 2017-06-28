---
title: "会社のリソースへのアクセスを有効にする"
description: "Wi-Fi、VPN、電子メール プロファイルを使用すると、ユーザーは必要なファイルとリソースにアクセスできます。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dd8dd4e-e165-4d0c-97b7-b3e86ebab909
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 18091d5dea0ff4b4519082973255a21e5cbc311e
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="enable-access-to-company-resources-with-microsoft-intune"></a>Microsoft Intune を使用して、会社のリソースへのアクセスを有効にする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune Wi-Fi、VPN、電子メール プロファイルを使用すると、ユーザーはどこにいても仕事を遂行するために必要なファイルとリソースにアクセスできます。 証明書プロファイルは、そのようなアクセスをセキュリティで保護するために役立ちます。

## <a name="wi-fi-profileswi-fi-connections-in-microsoft-intunemd-and-supported-platforms"></a>[Wi-Fi プロファイル](wi-fi-connections-in-microsoft-intune.md)とサポートされているプラットフォーム

ワイヤレス ネットワークの設定をユーザーに展開します。 これらの設定により、ユーザーは企業ネットワークに簡単に接続できるようになります。
#### <a name="supported-platforms"></a>サポートされているプラットフォーム

|Windows 8.1 以降|Windows Phone 8.1 以降|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|○ (Windows Wi-Fi プロファイルをインポートできます)|○ (OMA-URI を構成できます) |Yes|○|Yes|

## <a name="vpn-profilesvpn-connections-in-microsoft-intunemd-and-supported-platforms"></a>[VPN プロファイル](vpn-connections-in-microsoft-intune.md)とサポートされているプラットフォーム
仮想プライベート ネットワーク (VPN) の設定をユーザーに展開します。 これらの設定により、ユーザーは企業ネットワーク上のリソースに簡単に接続できるようになります。

|Windows 8.1 以降|Windows Phone 8.1 以降|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|Yes|○|○|○|Yes|

## <a name="email-profilesconfigure-access-to-corporate-email-using-email-profiles-with-microsoft-intunemd-and-supported-platforms"></a>[電子メール プロファイル](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)とサポートされているプラットフォーム
組織のデバイスに対するネイティブ電子メール クライアント設定を作成、展開、監視します。

|Windows 8.1 以降|Windows Phone 8.1 以降|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|いいえ|○|○|いいえ|Yes|
> [!NOTE]
> OMA-URI を使用する Windows Phone 8.1 Wi-Fi プロファイルを構成する方法については、[この Intune チームのブログの投稿](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/19/using-oma-uri-to-create-custom-wi-fi-profiles-for-windows-phone-8-1/)を参照してください。

## <a name="certificate-profilessecure-resource-access-with-certificate-profilesmd-and-supported-platforms"></a>[証明書プロファイル](secure-resource-access-with-certificate-profiles.md)とサポートされているプラットフォーム
ワイヤレス ネットワークや VPN 接続など、会社のリソースに対するアクセスをセキュリティで保護します。

|Windows 8.1 以降|Windows Phone 8.1 以降|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|Yes|○|○|○|Yes|

