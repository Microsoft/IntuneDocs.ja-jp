---
title: "Microsoft Intune のデバイス プロファイルとは"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Intune デバイス プロファイルと、それを活用して社内のデバイスを管理および保護する方法について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: eb48265e4655117976c9847b1f5bee712f0c2e3c
ms.lasthandoff: 02/18/2017


---

# <a name="what-are-microsoft-intune-device-profiles"></a>Microsoft Intune のデバイス プロファイルとは

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Microsoft Intune の **[デバイスの構成]** ワークロードを使用して、管理対象とするすべてのデバイスの設定と機能を管理します。 ほとんどの場合、このワークロードを使用してデバイス プロファイルを作成します。これにより、管理対象デバイスであらゆる種類の機能を管理および制御することができます。

このワークロードを開くと、以下のオプションが表示されます。

- **[概要]** - このページには、ユーザーとデバイスに割り当てたデバイス構成を監視するのに役立つ状態およびレポートが表示されます。
- **[管理] > [プロファイル]** - このセクションでは、デバイス構成プロファイルを作成します。 作成できるすべてのプロファイルの種類については、以下の一覧を参照してください。
- **[セットアップ] > [証明機関]** - このワークフローでは、証明書の構成に必要な手順が説明されています。 Intune 証明書プロファイルを使用する場合は、このワークフローを実行する必要があります。

## <a name="getting-started"></a>はじめに

デバイス プロファイルを作成するためのワークフローには、プロファイルごとの違いはありません。 プロファイルの作成方法については、[Microsoft Intune のデバイス構成プロファイルの作成方法](/intune-azure/configure-devices/how-to-create-device-profiles)に関するページを参照してください。 その後は、各種プロファイル向けの設定の具体的な作成方法について読み進めてください。

以下に挙げるデバイスの機能を管理することができます。

## <a name="device-restrictions"></a>デバイスの制限
デバイスの制限では、セキュリティ、ブラウザー、ハードウェア、データ共有設定を含む広範なカテゴリにわたって、管理対象のさまざまな設定と機能を制御できます。 たとえば、iOS デバイスのユーザーがデバイスのカメラにアクセスできないようにするデバイスの制限プロファイルを作成できます。
詳細については、[デバイス制限設定の構成方法](how-to-configure-device-restrictions.md)に関するページを参照してください。サポート対象: Android、iOS、macOS、Windows 10、Windows 10 Team。

## <a name="email"></a>電子メール
電子メール プロファイルを使用すると、管理対象とするデバイスの Exchange ActiveSync 電子メール設定を作成、展開、監視できます。 このような設定を展開することで一貫性の確保とサポート負荷の軽減が可能になり、エンド ユーザーは自分では何の設定もせずに個人デバイスで会社の電子メールにアクセスできるようになります。
詳細については、[電子メール設定の構成方法](how-to-configure-email-settings.md)に関するページを参照してください。サポート対象: Android、iOS、Windows Phone 8.1、Windows 10。

## <a name="wi-fi"></a>Wi-Fi
Wi-Fi プロファイルを使用すると、ワイヤレス ネットワーク設定を組織内のユーザーとデバイスに展開できます。 Wi-Fi プロファイルをデプロイするときに、ユーザーはプロファイルを構成することなく、会社の Wi-Fi にアクセスできます。
詳細については、[Wi-Fi 設定の構成方法](how-to-configure-wi-fi-settings.md)に関するページを参照してください。サポート対象: Android、iOS、macOS、Windows 8.1 (インポートのみ)。

## <a name="vpn"></a>VPN
仮想プライベート ネットワーク (VPN) を使用すると、会社のユーザーが社内ネットワークにリモート アクセスする際にセキュリティで保護することができます。 デバイスは、VPN 接続プロファイルを使用して、VPN サーバーとの接続を開始します。 VPN プロファイルを使用すると、VPN 設定を組織内のユーザーとデバイスに展開し、社内ネットワークに簡単かつ安全に接続できるようになります。
詳細については、[VPN 設定の構成方法](how-to-configure-vpn-settings.md)に関するページを参照してください。
サポート対象: Android、iOS、macOS、Windows Phone 8.1、Windows 8.1、Windows 10。

## <a name="certificates"></a>証明書
この種類のプロファイルでは、デバイスに割り当てて Wi-Fi、VPN、電子メール プロファイルの認証に利用できる、信頼済み証明書、SCEP 証明書、PKCS 証明書を構成できます。
詳細については、[証明書の構成方法](how-to-configure-certificates.md)に関するページを参照してください。サポート対象: Android、iOS、Windows Phone 8.1、Windows 8.1、Windows 10。

## <a name="edition-upgrade"></a>エディションのアップグレード
この種類のプロファイルでは、一部のバージョンの Windows 10 が実行されているデバイスを自動的に新しいエディションにアップグレードできます。詳細については、[Windows 10 エディションのアップグレードの構成方法](how-to-configure-windows-10-edition-upgrade.md)に関するページを参照してください。サポート対象: Windows 10 のみ。

## <a name="windows-information-protection"></a>Windows 情報保護
Windows 情報保護はデータ漏えいの防止に役立ち、それ以外の目的で従業員のエクスペリエンスを妨げることはありません。 また、企業が所有するデバイスと従業員が作業のために持ち込む個人用デバイスでもエンタープライズ アプリとデータを偶発的なデータ漏えいから保護します。既存の環境や他のアプリを変更する必要はありません。
詳細については、[Windows 情報保護の構成方法](how-to-configure-windows-information-protection.md)に関するページを参照してください。サポート対象: Windows 10 のみ。

## <a name="custom"></a>カスタム
カスタム設定により、Intune に組み込まれていないデバイス設定を割り当てることができます。 たとえば、Android デバイスでは、デバイスを構成する OMA-URI 値を指定できます。 iOS デバイスの場合は、Apple Configurator で作成した構成ファイルをインポートできます。
詳細については、[カスタム設定の構成方法](how-to-configure-custom-settings.md)に関するページを参照してください。サポート対象: Android、iOS、macOS、Windows Phone 8.1。

