---
title: Microsoft Intune - Azure のデバイス プロファイル | Microsoft Docs
description: 機能、制限事項、電子メール、WiFi、VPN、教育、証明書、Windows 10 のアップグレード、BitLocker と Windows Defender、Windows 情報保護、Azure Portal でのデバイスのカスタム構成設定を含む、さまざまな Microsoft Intune デバイス プロファイルの概要。 これらのプロファイルを使用して、社内のデータとデバイスを管理および保護します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: c9a3146b1ad5f6f7c439d2e49cf534e14d154f76
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728703"
---
# <a name="what-are-microsoft-intune-device-profiles"></a>Microsoft Intune のデバイス プロファイルとは

Microsoft Intune には、組織内のさまざまなデバイスで有効または無効にできる設定と機能が含まれています。 これらの設定と機能は、プロファイルを使用して管理されます。 プロファイルの例には、次のようなものがあります。 

- さまざまなデバイスに会社の WiFi へのアクセスを提供する WiFi プロファイル
- さまざまなデバイスに企業ネットワーク内の VPN サーバーへのアクセスを提供する VPN プロファイル

この記事では、ご利用のデバイス用に作成できるさまざまなプロファイルの概要を提供します。 これらのプロファイルを使用して、デバイスで一部の機能を許可または禁止します。

## <a name="before-you-begin"></a>始める前に

使用可能な機能を表示するには、[Azure Portal](https://portal.azure.com) を開き、Intune リソースを開きます。 

**デバイス構成**には、次のオプションが含まれます。

- **概要**: プロファイルの状態を一覧表示し、ユーザーとデバイスに割り当てたプロファイルに関する追加の詳細を提供します
- **管理**: デバイス プロファイルを作成し、カスタムの[PowerShell スクリプト](intune-management-extension.md)をアップロードしてプロファイル内で実行します
- **モニター**: プロファイルの状態が成功か失敗かを確認し、プロファイルのログも表示します
- **セットアップ**: 証明書機関 (SCEP または .PFX) を追加するか、プロファイルに通信費管理サービスを有効にします

## <a name="create-the-profile"></a>プロファイルの作成

[デバイス プロファイルの作成](device-profile-create.md)では、プロファイルを作成するための詳細な手順を提供しています。 

## <a name="device-features---ios-and-macos"></a>デバイス機能 - iOS と macOS

[デバイス機能](device-features-configure.md)は、AirPrint、通知、共有デバイス構成など、iOS デバイスと macOS デバイスの機能を制御します。

この機能では以下をサポートします。
- iOS 
- macOS

## <a name="device-restrictions"></a>デバイスの制限

[デバイスの制限](device-restrictions-configure.md)は、セキュリティ、ハードウェア、データの共有など、デバイス上の設定を制御します。 たとえば、iOS デバイス ユーザーにデバイスのカメラの使用を禁じるデバイスの制限プロファイルを作成できます。 

この機能では以下をサポートします。

- Android
- Android エンタープライズ
- iOS
- macOS
- Windows 10
- Windows 10 Team

## <a name="delivery-optimization"></a>配信の最適化

[配信の最適化](delivery-optimization-windows.md)では、ソフトウェア更新プログラムの配信に関するエクスペリエンスを向上させることができます。 これらの設定は、**[ソフトウェア更新プログラム]** > **[Windows 10 更新プログラムのリング]** 設定に置き換わるものです。

これらの設定は、ソフトウェア更新プログラムを組織内のデバイスにダウンロードする方法を制御するために使用します。 たとえば、デバイス プロファイル内で、ユーザーが自分で更新プログラムを取得できるように設定することも、配信の最適化クラウド サービスを通じて更新プログラムを取得できるように設定することもできます。

この機能では以下をサポートします。

- Windows 10 以降

## <a name="endpoint-protection"></a>Endpoint Protection

[Windows 10 用の Endpoint Protection 設定](endpoint-protection-windows-10.md)は、Windows 10 デバイス用の BitLocker および Windows Defender の設定を構成します。

Windows Defender Advanced Threat Protection (WDATP) と Microsoft Intune をオンボードするには、「[Configure endpoints using Mobile Device Management (MDM) tools](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection)」 (モバイル デバイス管理 (MDM) ツールを使用してエンドポイントを構成する) を参照してください。

この機能では以下をサポートします。

- Windows 10 以降

## <a name="identity-protection"></a>ID 保護

[ID 保護](identity-protection-configure.md)により、Windows 10 デバイスと Windows 10 Mobile デバイスにおける Windows Hello for Business の操作が制御されます。 この設定を構成し、Windows Hello for Business をユーザーやデバイスが利用できるようにし、デバイスの PIN とジェスチャの要件を指定します。  

この機能では以下をサポートします。  

- Windows 10 以降
- Windows Holographic for Business  

## <a name="kiosk"></a>キオスク

[キオスク設定](kiosk-settings.md)プロファイルでは、1 つのアプリを実行するようにデバイスを構成することも、多数のアプリを実行するようにデバイスを構成することもできます。 スタート メニューや Web ブラウザーなど、その他の機能もキオスクでカスタマイズできます。

この機能では以下をサポートします。

- Windows 10 以降

キオスク設定は、[Android](device-restrictions-android.md#kiosk)、[Android エンタープライズ](device-restrictions-android-for-work.md#kiosk-settings)、および [ios](device-restrictions-ios.md#kiosk-supervised-only) 用のデバイス制限としても使用できます。

## <a name="email"></a>Email

[電子メールの設定](email-settings-configure.md)では、デバイス上の Exchange ActiveSync 電子メール設定の作成、割り当て、監視を行います。 電子メール プロファイルにより、一貫性の確保とサポート負荷の軽減が可能になり、エンド ユーザーは自分では何の設定もせずに個人デバイスで会社の電子メールにアクセスできるようになります。 

この機能では以下をサポートします。 

- Android
- iOS
- Windows Phone 8。1
- Windows 10

## <a name="vpn"></a>VPN

[VPN 設定](vpn-settings-configure.md)は、VPN プロファイルを組織内のユーザーとデバイスに割り当て、社内ネットワークに簡単かつ安全に接続できるようにします。 

仮想プライベート ネットワーク (VPN) を使用すると、会社のユーザーが社内ネットワークにリモート アクセスする際にセキュリティで保護することができます。 デバイスは VPN 接続プロファイルを使用して VPN サーバーとの接続を開始します。 

この機能では以下をサポートします。 

- Android
- iOS
- macOS
- Windows Phone 8。1
- Windows 8.1
- Windows 10

## <a name="wi-fi"></a>Wi-Fi

[Wi-Fi 設定](wi-fi-settings-configure.md)は、ユーザーとデバイスにワイヤレス ネットワーク設定を割り当てます。 Wi-Fi プロファイルを割り当てると、ユーザーは自分でプロファイルを構成することなく、会社の Wi-Fi にアクセスできます。 

この機能では以下をサポートします。 

- Android
- iOS
- macOS
- Windows 8.1 (インポートのみ)

## <a name="esim-cellular---public-preview"></a>eSIM 携帯電話 - パブリック プレビュー

管理者は [eSIM 携帯電話プロファイル](esim-device-configuration.md)を使用して、インターネットおよびデータ アクセスに関する、マネージド デバイスの携帯データ通信プランを構成できます。 携帯電話会社からアクティブ化コードを取得した後、Intune を使用して、このアクティブ化コードをインポートし、eSIM 対応デバイスに割り当てます。

この機能では以下をサポートします。
- Windows 10 Fall Creators Update 以降

## <a name="education"></a>教育

[教育設定 - Windows 10](education-settings-configure.md) では、[Windows テスト アプリ](https://education.microsoft.com/gettrained/win10takeatest)のオプションを構成します。 これらのオプションを構成するとき、テストが完了するまで他のアプリをデバイスで実行できません。

[教育設定 - iOS](education-settings-configure-ios-shared.md) では、iOS Classroom アプリを使用し、教室で学習を指導し、生徒のデバイスを操作します。 多数の学生が 1 台のデバイスを共有できるように iPad デバイスを構成できます。

## <a name="edition-upgrade"></a>エディションのアップグレード

[Windows 10 エディションのアップグレード](edition-upgrade-configure-windows-10.md)は、Windows 10 のいずれかのバージョンを実行するデバイスを自動的に新しいエディションにアップグレードします。

この機能では以下をサポートします。 
- Windows 10 以降

## <a name="update-policies"></a>更新ポリシー

[iOS 更新ポリシー](software-updates-ios.md)には、iOS デバイスにソフトウェア更新プログラムをインストールするための iOS ポリシーを作成し、割り当てる方法が示されます。 インストールの状態を確認することもできます。

この機能では以下をサポートします。
- iOS

## <a name="certificates"></a>証明書

[証明書](certificates-configure.md)では、デバイスに割り当てられ Wi-Fi、VPN、電子メール プロファイルの認証に使用される、信頼済み証明書、SCEP 証明書、PKCS 証明書を構成します。

この機能では以下をサポートします。 

- Android
- iOS
- Windows Phone 8。1
- Windows 8.1
- Windows 10

## <a name="windows-information-protection-profile"></a>Windows 情報保護プロファイル

[Windows 情報保護](windows-information-protection-configure.md)は、従業員のエクスペリエンスを妨げることなく、データ漏えいの防止に役立ちます。 また、企業が所有するデバイスと従業員が作業のために持ち込む個人用デバイスでもエンタープライズ アプリとデータを偶発的なデータ漏えいから保護します。 Windows Information Protection は、環境やその他のアプリを変更しなくても使用できます。

この機能では以下をサポートします。
- Windows 10 以降

## <a name="custom-profile"></a>カスタム プロファイル

管理者は[カスタム設定](custom-settings-configure.md)を使用して、Intune に組み込まれていないデバイス設定を割り当てることができます。 たとえば、Android デバイスでは、OMA-URI 値を入力できます。 iOS デバイスの場合は、Apple Configurator で作成した構成ファイルをインポートできます。 

この機能では以下をサポートします。

- Android
- iOS
- macOS
- Windows Phone 8。1

## <a name="manage-and-troubleshoot"></a>管理とトラブルシューティング

[プロファイルの管理](device-profile-monitor.md)に関する説明では、デバイスの状態や割り当てられているプロファイルの確認方法を説明しています。 競合を起こした設定と、これらの設定を含むプロファイルを確認することによって、競合も解決できます。 [一般的な問題とその解決方法](device-profile-troubleshoot.md)に関する説明では、プロファイルを削除すると起こることや、デバイスに通知が送信される原因など、プロファイルの使用に関する Q&A の一覧があります。
