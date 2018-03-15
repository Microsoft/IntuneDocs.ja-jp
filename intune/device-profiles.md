---
title: "Microsoft Intune - Azure のデバイス プロファイル | Microsoft Docs"
description: "機能、制限事項、電子メール、WiFi、VPN、教育、証明書、Windows 10 のアップグレード、BitLocker と Windows Defender、Windows 情報保護、Azure Portal でのデバイスのカスタム構成設定を含む、さまざまな Microsoft Intune デバイス プロファイルの概要。 これらのプロファイルを使用して、社内のデータとデバイスを管理および保護します。"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 79ca6eaf22233dd6d024a28e456e57a8a74d02aa
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="what-are-microsoft-intune-device-profiles"></a>Microsoft Intune のデバイス プロファイルとは

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune には、組織内のさまざまなデバイスで有効または無効にできる設定と機能が含まれています。 これらの設定と機能は、プロファイルを使用して管理されます。 プロファイルの例には、次のようなものがあります。 

- さまざまなデバイスに会社の WiFi へのアクセスを提供する WiFi プロファイル
- さまざまなデバイスに企業ネットワーク内の VPN サーバーへのアクセスを提供する VPN プロファイル

このトピックでは、ご利用のデバイス用に作成できるさまざまなプロファイルの概要を提供します。 これらのプロファイルを使用して、デバイスで一部の機能を許可または禁止します。

## <a name="before-you-begin"></a>始める前に
使用可能な機能を表示するには、[Azure Portal](https://portal.azure.com) を開き、Intune リソースを開きます。 

**デバイス構成**には、次のオプションが含まれます。

- **概要**: プロファイルの状態を一覧表示し、ユーザーとデバイスに割り当てたプロファイルに関する追加の詳細を提供します
- **管理**: デバイス プロファイルを作成し、カスタムの[PowerShell スクリプト](intune-management-extension.md)をアップロードしてプロファイル内で実行します
- **モニター**: プロファイルの状態が成功か失敗かを確認し、プロファイルのログも表示します
- **セットアップ**: 証明書機関 (SCEP または .PFX) を追加するか、プロファイルに通信費管理サービスを有効にします

## <a name="create-the-profile"></a>プロファイルの作成

[デバイス プロファイルの作成](device-profile-create.md)では、プロファイルを作成するための詳細な手順を提供しています。 

## <a name="device-features-profile"></a>デバイス機能プロファイル

[デバイス機能](device-features-configure.md)は、AirPrint、通知、共有デバイス構成など、iOS デバイスと macOS デバイスの機能を制御します。

この機能では以下をサポートします。  
- iOS 
- macOS

## <a name="device-restrictions-profile"></a>デバイスの制限プロファイル
[デバイスの制限](device-restrictions-configure.md)は、セキュリティ、ハードウェア、データの共有など、デバイス上の設定を制御します。 たとえば、iOS デバイス ユーザーにデバイスのカメラの使用を禁じるデバイスの制限プロファイルを作成できます。 

この機能では以下をサポートします。 

- Android
- iOS
- macOS
- Windows 10
- Windows 10 Team

## <a name="email-profile"></a>電子メールのプロファイル
[電子メールの設定](email-settings-configure.md)プロファイルは、デバイスで Exchange ActiveSync 電子メール設定の作成、割り当て、監視を行います。 電子メール プロファイルにより、一貫性の確保とサポート負荷の軽減が可能になり、エンド ユーザーは自分では何の設定もせずに個人デバイスで会社の電子メールにアクセスできるようになります。 

この機能では以下をサポートします。 

- Android
- iOS
- Windows Phone 8。1
- Windows 10

## <a name="wi-fi-profile"></a>Wi-Fi プロファイル
[Wi-Fi 設定](wi-fi-settings-configure.md)は、ユーザーとデバイスにワイヤレス ネットワーク設定を割り当てます。 Wi-Fi プロファイルを割り当てると、ユーザーは自分でプロファイルを構成することなく、会社の Wi-Fi にアクセスできます。 

この機能では以下をサポートします。 

- Android
- iOS
- macOS
- Windows 8.1 (インポートのみ)

## <a name="vpn-profile"></a>VPN プロファイル
[VPN 設定](vpn-settings-configure.md)は、VPN プロファイルを組織内のユーザーとデバイスに割り当て、社内ネットワークに簡単かつ安全に接続できるようにします。 

仮想プライベート ネットワーク (VPN) を使用すると、会社のユーザーが社内ネットワークにリモート アクセスする際にセキュリティで保護することができます。 デバイスは、VPN 接続プロファイルを使用して、VPN サーバーとの接続を開始します。 

この機能では以下をサポートします。 

- Android
- iOS
- macOS
- Windows Phone 8。1
- Windows 8.1
- Windows 10

## <a name="education-profile"></a>教育プロファイル
[教育設定](education-settings-configure.md)は、[Windows テスト アプリ](https://education.microsoft.com/gettrained/win10takeatest)のオプションを構成します。 これらのオプションを構成するとき、テストが完了するまで他のアプリをデバイスで実行できません。

## <a name="certificates-profile"></a>証明書プロファイル
[証明書](certificates-configure.md)は、デバイスに割り当てて Wi-Fi、VPN、電子メール プロファイルの認証に利用できる、信頼済み証明書、SCEP 証明書、PKCS 証明書を構成できます。

この機能では以下をサポートします。 

- Android
- iOS
- Windows Phone 8。1
- Windows 8.1
- Windows 10

## <a name="edition-upgrade-profile"></a>エディションのアップグレード プロファイル
[Windows 10 エディションのアップグレード](edition-upgrade-configure-windows-10.md)は、Windows 10 のいずれかのバージョンを実行するデバイスを自動的に新しいエディションにアップグレードします。

この機能がサポートしているのは、Windows 10 のみです。

## <a name="endpoint-protection-profile"></a>Endpoint Protection プロファイル
[Windows 10 用の Endpoint Protection 設定](endpoint-protection-windows-10.md)は、Windows 10 デバイス用の BitLocker および Windows Defender の設定を構成します。

この機能がサポートしているのは、Windows 10 のみです。

## <a name="windows-information-protection-profile"></a>Windows 情報保護プロファイル
[Windows 情報保護](windows-information-protection-configure.md)は、従業員のエクスペリエンスを妨げることなく、データ漏えいの防止に役立ちます。 また、企業が所有するデバイスと従業員が作業のために持ち込む個人用デバイスでもエンタープライズ アプリとデータを偶発的なデータ漏えいから保護します。 既存の環境や他のアプリを変更する必要はありません。

この機能がサポートしているのは、Windows 10 のみです。

## <a name="custom-profile"></a>カスタム プロファイル
[カスタム設定](custom-settings-configure.md)には、Intune に組み込まれていないデバイス設定を割り当てる機能が含まれています。 たとえば、Android デバイスでは、OMA-URI 値を入力できます。 iOS デバイスの場合は、Apple Configurator で作成した構成ファイルをインポートできます。 

この機能では以下をサポートします。 

- Android
- iOS
- macOS
- Windows Phone 8。1