---
title: Microsoft Intune のデバイスの機能と設定 - Azure | Microsoft Docs
description: 機能、制限事項、電子メール、WiFi、VPN、教育、証明書、Windows 10 のアップグレード、BitLocker と Windows Defender、Windows 情報保護、管理用テンプレート、および Azure portal のカスタム デバイス構成設定を含む、さまざまな Microsoft Intune デバイス プロファイルの概要。 これらのプロファイルを使用して、社内のデータとデバイスを管理および保護します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b9bd8aaca9aaf6e39c7a120518eeca1cef31511
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845093"
---
# <a name="apply-features-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>Microsoft Intune でデバイス プロファイルを使用してデバイスに機能設定を適用する

Microsoft Intune には、組織内のさまざまなデバイスで有効または無効にできる設定と機能が含まれています。 これらの設定と機能は "構成プロファイル" に追加されます。 プロファイルをさまざまなデバイス用に、また、iOS、Android、Windows を含め、さまざまなプラットフォーム用に作成してから、Intune を使用して、組織内のデバイスにそのプロファイルを適用することができます。

プロファイルの例には、次のようなものがあります。

- Windows 10 デバイスでは、Internet Explorer で ActiveX コントロールをブロックするプロファイル テンプレートを使用します。
- iOS および macOS デバイスでは、ユーザーが組織内の AirPrint プリンターを使用できるようにします。
- デバイス上の Bluetooth へのアクセスを許可または禁止します。
- さまざまなデバイスに企業ネットワークへのアクセスを提供する WiFi または VPN プロファイルを作成します。
- インストールのタイミングを含め、ソフトウェア更新プログラムを管理します。
- 1 つのアプリ、または多くのアプリを実行できる専用のキオスク デバイスである、Android デバイスを実行します。

この記事ではプロファイルを作成する手順を一覧表示し、作成できるさまざまな種類のプロファイルの概要を示します。 これらのプロファイルを使用して、デバイスで一部の機能を許可または禁止します。

## <a name="create-the-profile"></a>プロファイルの作成

1. [Azure portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**[Intune]** を選択します。

2. **[デバイス構成]** を選択します。 次のオプションがあります。

    - **概要**:プロファイルの状態を一覧表示し、ユーザーとデバイスに割り当てたプロファイルに関する追加の詳細を提供します。
    - **管理**:デバイス プロファイルを作成し、カスタムの [PowerShell スクリプト](intune-management-extension.md)をアップロードしてプロファイル内で実行し、[eSIM](esim-device-configuration.md) を使用してデバイスにデータ プランを追加します。
    - **監視**:プロファイルの状態が成功か失敗かを確認し、プロファイルのログも表示します。
    - **セットアップ**:SCEP または PFX 証明書機関を追加するか、プロファイルで[通信費管理サービス](telecom-expenses-monitor.md)を有効にします。

3. **[プロファイル]** > **[プロファイルの作成]** の順に選択します。 次のプロパティを入力します。

   - **名前**: プロファイルのわかりやすい名前を入力します。
   - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
   - **[プラットフォーム]**:デバイスのプラットフォームを選択します。 次のようなオプションがあります。  

       - **Android**
       - **Android エンタープライズ**
       - **Android**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 以降**
       - **Windows 10 以降**

   - **[プロファイルの種類]**:作成する設定の種類を選択します。 表示されるリストは、選択する**プラットフォーム**によって異なります。

       - [管理用テンプレート](administrative-templates-windows.md)
       - [カスタム](custom-settings-configure.md)
       - [配信の最適化](delivery-optimization-windows.md)
       - [デバイスの機能](device-features-configure.md)
       - [デバイスの制限](device-restrictions-configure.md)
       - [エディションのアップグレードとモードの切り替え](edition-upgrade-configure-windows-10.md)
       - [教育](education-settings-configure.md)
       - [電子メール](email-settings-configure.md)
       - [Endpoint Protection](endpoint-protection-configure.md)
       - [ID 保護](identity-protection-configure.md)  
       - [キオスク](kiosk-settings.md)
       - [PKCS 証明書](certficates-pfx-configure.md)
       - [SCEP 証明書](certificates-scep-configure.md)
       - [信頼された証明書](certificates-configure.md)
       - [更新ポリシー](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](advanced-threat-protection.md)
       - [Windows 情報保護](windows-information-protection-configure.md)

     たとえば、プラットフォームとして **iOS** を選択した場合、プロファイルの種類のオプションは次のようになります。

     ![Intune で iOS プロファイルを作成する](./media/create-device-profile.png)

4. **[設定]** を選択します。 設定はカテゴリごとに整理されます。 カテゴリを選択して、構成できるすべての設定のリストを表示します。

5. 完了したら、**[OK]** > **[作成]** の順に選択して変更を保存します。

さまざまなプロファイルの種類の詳細については、この記事の次のセクションをお読みください。

## <a name="administrative-templates-preview"></a>管理用テンプレート (プレビュー)

[管理用テンプレート](administrative-templates-windows.md)には数百の設定が含まれており、これらを Internet Explorer、OneDrive、リモート デスクトップ、Word、Excel、およびその他の Office プログラム用に構成することができます。

これらのテンプレートでは、管理者にグループ ポリシーと同様の設定の簡単な簡易ビューが提供されますが、それらは 100% クラウドベースです。 

この機能では以下をサポートします。

- Windows 10 以降

## <a name="device-features"></a>デバイスの機能

[デバイスの機能](device-features-configure.md)では、AirPrint、通知、ロック画面メッセージなど、iOS および macOS デバイスの機能を制御します。

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
- Windows 10 以降
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
- Windows 10 以降

## <a name="vpn"></a>VPN

[VPN 設定](vpn-settings-configure.md)は、VPN プロファイルを組織内のユーザーとデバイスに割り当て、社内ネットワークに簡単かつ安全に接続できるようにします。 

仮想プライベート ネットワーク (VPN) を使用すると、会社のユーザーが社内ネットワークにリモート アクセスする際にセキュリティで保護することができます。 デバイスは VPN 接続プロファイルを使用して VPN サーバーとの接続を開始します。 

この機能では以下をサポートします。 

- Android
- iOS
- macOS
- Windows Phone 8。1
- Windows 8.1
- Windows 10 以降

## <a name="wi-fi"></a>Wi-Fi

[Wi-Fi 設定](wi-fi-settings-configure.md)は、ユーザーとデバイスにワイヤレス ネットワーク設定を割り当てます。 Wi-Fi プロファイルを割り当てると、ユーザーは自分でプロファイルを構成することなく、会社の Wi-Fi にアクセスできます。 

この機能では以下をサポートします。 

- Android
- iOS
- macOS
- Windows 8.1 (インポートのみ)
- Windows 10 以降

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

Windows デバイスの更新プログラム ポリシーについては、[配信の最適化](delivery-optimization-windows.md)に関するページを参照してください。 

この機能では以下をサポートします。
- iOS

## <a name="certificates"></a>証明書

[証明書](certificates-configure.md)では、デバイスに割り当てられ Wi-Fi、VPN、電子メール プロファイルの認証に使用される、信頼済み証明書、SCEP 証明書、PKCS 証明書を構成します。

この機能では以下をサポートします。 

- Android
- iOS
- Windows Phone 8。1
- Windows 8.1
- Windows 10 以降

## <a name="windows-information-protection-profile"></a>Windows 情報保護プロファイル

[Windows 情報保護](windows-information-protection-configure.md)は、従業員のエクスペリエンスを妨げることなく、データ漏えいの防止に役立ちます。 また、企業が所有するデバイスと従業員が作業のために持ち込む個人用デバイスでもエンタープライズ アプリとデータを偶発的なデータ漏えいから保護します。 Windows Information Protection は、環境やその他のアプリを変更しなくても使用できます。

この機能では以下をサポートします。

- Windows 10 以降

## <a name="shared-multi-user-device"></a>共有のマルチ ユーザー デバイス

[Windows 10](shared-user-device-settings-windows.md) および [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) には、複数のユーザーが使用するデバイス (共有デバイスや共有 PC ともいう) を管理するための設定が含まれます。 ユーザーがデバイスにサインインするときに、そのユーザーがスリープ オプションを変更できるようにするか、デバイス上にファイルを保存できるようにするかを選択します。 また、領域を節約するために Windows HoloLens デバイスから非アクティブな資格情報を削除するポリシーを作成することもできます。

これらの共有のマルチ ユーザー デバイス設定では、管理者はデバイスの一部の機能を制御し、Intune を使用してその共有デバイスを管理することができます。

この機能では以下をサポートします。

- Windows 10 以降
- Windows Holographic for Business

## <a name="custom-profile"></a>カスタム プロファイル

管理者は[カスタム設定](custom-settings-configure.md)を使用して、Intune に組み込まれていないデバイス設定を割り当てることができます。 たとえば、Android デバイスでは、OMA-URI 値を入力できます。 iOS デバイスの場合は、Apple Configurator で作成した構成ファイルをインポートできます。 

この機能では以下をサポートします。

- Android
- iOS
- macOS
- Windows Phone 8。1

## <a name="manage-and-troubleshoot"></a>管理とトラブルシューティング

[プロファイルの管理](device-profile-monitor.md)に関する説明では、デバイスの状態や割り当てられているプロファイルの確認方法を説明しています。 競合を起こした設定と、これらの設定を含むプロファイルを確認することによって、競合も解決できます。 [一般的な問題とその解決方法](device-profile-troubleshoot.md)に関する説明では、プロファイルを削除すると起こることや、デバイスに通知が送信される原因など、プロファイルの使用に関する Q&A の一覧があります。

## <a name="next-steps"></a>次の手順
プラットフォームを選択して始めてください。

