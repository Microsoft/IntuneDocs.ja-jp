---
title: "会社のリソースへのアクセスを有効にする | Microsoft Intune"
description: "Wi-Fi、VPN、電子メール プロファイルを使用すると、ユーザーは必要なファイルとリソースにアクセスできます。"
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dd8dd4e-e165-4d0c-97b7-b3e86ebab909
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 167db9027e69dd6419d5deec758a8a0a0b119a97
ms.openlocfilehash: 8605a665a0033fdc9b05ba452f5bf966e76699ca


---

# Microsoft Intune を使用して、会社のリソースへのアクセスを有効にする
Microsoft Intune Wi-Fi、VPN、電子メール プロファイルを使用すると、ユーザーはどこにいても仕事を遂行するために必要なファイルとリソースにアクセスできます。 証明書プロファイルは、そのようなアクセスをセキュリティで保護するために役立ちます。

## [Wi-Fi プロファイル](wi-fi-connections-in-microsoft-intune.md)とサポートされているプラットフォーム

ワイヤレス ネットワークの設定をユーザーに展開します。 これらの設定により、ユーザーは企業ネットワークに簡単に接続できるようになります。
#### サポートされているプラットフォーム

|Windows 8.1 以降|Windows Phone 8.1 以降|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|○ (Windows Wi-Fi プロファイルをインポートできます)|○ (OMA-URI を構成できます) |Yes|○|Yes|

## [VPN プロファイル](vpn-connections-in-microsoft-intune.md)とサポートされているプラットフォーム
仮想プライベート ネットワーク (VPN) の設定をユーザーに展開します。 これらの設定により、ユーザーは企業ネットワーク上のリソースに簡単に接続できるようになります。

|Windows 8.1 以降|Windows Phone 8.1 以降|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|[はい]|○|○|○|Yes|

## [電子メール プロファイル](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)とサポートされているプラットフォーム
組織のデバイスに対するネイティブ電子メール クライアント設定を作成、展開、監視します。

|Windows 8.1 以降|Windows Phone 8.1 以降|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|×|○|○|×|Yes|
> [!NOTE]
> OMA-URI を使用する Windows Phone 8.1 Wi-Fi プロファイルを構成する方法については、[この Intune チームのブログの投稿](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/19/using-oma-uri-to-create-custom-wi-fi-profiles-for-windows-phone-8-1/)を参照してください。

## [証明書プロファイル](secure-resource-access-with-certificate-profiles.md)とサポートされているプラットフォーム
ワイヤレス ネットワークや VPN 接続など、会社のリソースに対するアクセスをセキュリティで保護します。

|Windows 8.1 以降|Windows Phone 8.1 以降|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|[はい]|○|○|○|Yes|



<!--HONumber=Aug16_HO3-->


