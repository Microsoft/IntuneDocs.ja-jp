---
title: "会社のリソースへのアクセスを有効にする | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dd8dd4e-e165-4d0c-97b7-b3e86ebab909
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 8c1f4f209c5ec704290882b8f6f71e0b1b01d21c
ms.openlocfilehash: 556b9ea5ac5edcc1126dbcc6310ab7dfa917cb56


---

# Microsoft Intune を使用して、会社のリソースへのアクセスを有効にする
Microsoft Intune Wi-Fi、VPN、電子メール プロファイルを使用すると、ユーザーはどこにいても仕事を確実に遂行するために必要なファイルとリソースにアクセスできます。 証明書プロファイルは、そのようなアクセスをセキュリティで保護するために役立ちます。

## [Wi-Fi プロファイル](wi-fi-connections-in-microsoft-intune.md)とサポートされているプラットフォーム

ワイヤレス ネットワークの設定をユーザーに展開します。 これらの設定を展開して、企業ネットワークに接続するために必要なエンド ユーザーの作業を最小化します。
#### サポートされているプラットフォーム

|Windows 8.1 以降|Windows Phone 8.1 以降|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|○ (Windows Wi-Fi プロファイルをインポートできます)|○ (OMA-URI を構成できます) |○|○|○|

## [VPN プロファイル](vpn-connections-in-microsoft-intune.md)とサポートされているプラットフォーム
仮想プライベート ネットワーク (VPN) の設定をユーザーに展開します。 これらの設定を展開して、企業ネットワーク上のリソースに接続するために必要なエンド ユーザーの作業を最小化します。

|Windows 8.1 以降|Windows Phone 8.1 以降|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|○|○|○|○|○|

## [電子メール プロファイル](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)とサポートされているプラットフォーム
組織のデバイスに対するネイティブ電子メール クライアント設定を作成、展開、監視します。す。

|Windows 8.1 以降|Windows Phone 8.1 以降|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|×|○|○|×|○|
> [!NOTE]
> OMA-URI を使用する Windows Phone 8.1 Wi-Fi プロファイルを構成する方法については、[この Intune チームのブログの投稿](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/19/using-oma-uri-to-create-custom-wi-fi-profiles-for-windows-phone-8-1/)を参照してください。

## [証明書プロファイル](secure-resource-access-with-certificate-profiles.md)とサポートされているプラットフォーム
ワイヤレス ネットワークや VPN 接続など、会社のリソースに対するアクセスをセキュリティで保護します。

|Windows 8.1 以降|Windows Phone 8.1 以降|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|○|○|○|○|○|



<!--HONumber=Jul16_HO2-->


