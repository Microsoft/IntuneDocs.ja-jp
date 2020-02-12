---
title: Microsoft Intune で SCEP 証明書プロファイルを使用して証明書をプロビジョニングする際のトラブルシューティング | Microsoft Docs
description: デバイスから NDES へ、NDES から証明機関へ、Intune Certificate Connector から Intune サービスへの通信など、Intune で使用する証明書を要求するデバイスによる SCEP の使用についてトラブルシューティングします。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 38bc86b1b9ba85eb7885a0e00673e551821063c1
ms.sourcegitcommit: 459b0ee01eb6e69cc0ce66d4c4b81d73f510f96d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2020
ms.locfileid: "77034245"
---
# <a name="overview-for-troubleshooting-scep-certificate-profiles-with-microsoft-intune"></a>Microsoft Intune での SCEP 証明書プロファイルのトラブルシューティングの概要

Simple Certificate Enrollment Protocol (SCEP) 証明書プロファイルを使用すると、Intune でのトラブルシューティングが困難になることがあります。 この記事では、次のように問題の解決に役立つ概要を説明します。

- SCEP プロセスのアーキテクチャと通信フローについて説明します
- その通信フローの問題の発生箇所を絞り込めるように支援します
- 証明書プロファイルのトラブルシューティングに関する以下の記事で取り上げる主要なログ ファイルを特定します

この記事と、関連する SCEP 証明書のトラブルシューティング記事の情報は、Android デバイス、iOS および iPad デバイス、Windows デバイスで SCEP 証明書プロファイルを使用する場合に適用されます。 現時点では、macOS に関する同様の情報は提供されていません。

ネットワーク デバイス登録サービス (NDES) のトラブルシューティングについては、support.microsoft.com の次の記事を参照してください。

- [Intune の SCEP 証明書用のオンプレミスの NDES 構成を検証する](https://support.microsoft.com/help/4490130/ndes-configuration-on-premises-for-scep-certificates-in-intune)
- [Microsoft Intune 証明書プロファイルで使用するための NDES の構成のトラブルシューティング]( https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune)

先に進む前に、信頼できる証明書プロファイルを介したルート証明書の展開を含め、[SCEP 証明書プロファイルを使用するための前提条件](certificates-scep-configure.md#prerequisites-for-using-scep-for-certificates)を満たしていることを確認します。

## <a name="scep-communication-flow-overview"></a>SCEP 通信フローの概要

Intune の SCEP 通信プロセスの基本的な概要を次の図に示します。

![SCEP 証明書プロファイルのフロー](../protect/media/troubleshoot-scep-certificate-profiles/scep-certificate-profile-flow.png)

1. [SCEP 証明書プロファイルを展開する](troubleshoot-scep-certificate-profile-deployment.md) Intune を使うと、特定のユーザー、証明書の目的、および証明書の種類を必須とするチャレンジ文字列が生成されます。

2. [デバイスから NDES サーバーへの通信](troubleshoot-scep-certificate-device-to-ndes.md)。 デバイスでは、NDES サーバーへの接続にプロファイルの NDES の URI が使用されます。これにより、チャレンジを提示できるようになります。

3. [NDES からポリシー モジュールへの通信](troubleshoot-scep-certificate-ndes-policy-module.md)。 NDES から、要求の検証を行うサーバー上の Intune Certificate Connector ポリシー モジュールへチャレンジが転送されます。

4. [NDES から証明機関へ](troubleshoot-scep-certificate-ndes-policy-module.md)。 NDES から証明機関 (CA) に対して、証明書を発行できる有効な要求が渡されます。

5. [デバイスへの証明書の配信](troubleshoot-scep-certificate-delivery.md)。 証明書がデバイスに配信されます。

6. [Intune への展開のレポート](troubleshoot-scep-certificate-reporting.md)。 Intune Certificate Connector から Intune に対して、証明書の発行イベントが報告されます。

## <a name="log-files"></a>ログ ファイル

通信と証明書のプロビジョニング ワークフローに関する問題を特定するには、サーバー インフラストラクチャとデバイスの両方のログ ファイルを確認します。 後述する SCEP 証明書プロファイルのトラブルシューティングに関するセクションでは、このセクションで触れているログ ファイルが取り上げられています。

- [インフラストラクチャとサーバーのログ](#logs-for-on-premises-infrastructure)

デバイスのログは、デバイスのプラットフォームによって異なります。  

- [iOS と iPadOS](#logs-for-ios-and-ipados-devices)
- [Android](#logs-for-android-devices)
- [Windows](#logs-for-windows-devices)

### <a name="logs-for-on-premises-infrastructure"></a>オンプレミス インフラストラクチャのログ
  
証明書の展開に SCEP 証明書プロファイルの使用をサポートするオンプレミス インフラストラクチャには、Microsoft Intune Certificate Connector、Windows サーバー上で実行される NDES、証明機関などがあります。

これらのロールのログ ファイルには、Windows イベント ビューアー、証明書コンソールと、Intune Certificate Connector、NDES、またはオンプレミス インフラストラクチャの一部である他のロールと操作に固有のさまざまなログ ファイルが含まれます。

以降の SCEP トラブルシューティングの記事で取り上げるログまたはコンソールを次の一覧に示します。 

- **NDESConnector_date_time.svclog**:

  このログには、Microsoft Intune Certificate Connector から Intune クラウド サービスへの通信が示されます。 このログ ファイルを表示するには、[サービス トレース ビューアー ツール](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe)を使用できます。

  関連するレジストリ キー:*HKLM\SW\Microsoft\MicrosoftIntune\NDESConnector\ConnectionStatus*

  場所: *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs* の NDES をホストするサーバー上

- **CertificateRegistrationPoint_date_time.svclog**:

  このログには、証明書の要求を受信および確認する NDES ポリシー モジュールが示されます。 このログ ファイルを表示するには、[サービス トレース ビューアー ツール](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe)を使用できます。

  場所: *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs* の NDES をホストするサーバー上

- **NDESPlugin.log**:

  このログには、証明書登録ポイントへ証明書要求を渡す処理と、それらの要求の結果の検証が示されます。

  場所: *%program_files%\Microsoft Intune\NDESPolicyModule\logs* の NDES をホストするサーバー上

- **IIS ログ**:

  IIS ログには、モバイル デバイスから NDES に送信された証明書の要求が示されます。

  場所:*c:\inetpub\logs\LogFiles\W3SVC1* の NDES をホストするサーバー上

- **Windows アプリケーション ログ**:

  このログは、SCEP アプリケーション プールなど、IIS の問題を調査するときに役立ちます。

  場所:NDES をホストするサーバー上:**eventvwr.msc** を実行して Windows イベント ビューアーを開きます




### <a name="logs-for-android-devices"></a>Android デバイスのログ

Android を実行するデバイスの場合は、**Android ポータル サイト** アプリ ログ ファイル **OMADM.log** を使用します。 ログを収集して確認する前に、[[詳細なログ記録]](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) が有効であることを確認してから、問題を再現します。

デバイスから OMADM.logs を収集する方法については、「[USB ケーブルを使用してログをアップロードして電子メールを送信する](/intune-user-help/send-logs-to-your-it-admin-using-cable-android)」を参照してください。

サポートする[ログをアップロードして電子メールで送信する](/intune-user-help/send-logs-to-your-it-admin-by-email-android#upload-and-email-logs-from-microsoft-intune-app)こともできます。

### <a name="logs-for-ios-and-ipados-devices"></a>iOS および iPadOS デバイスのログ

iOS または iPadOS を実行するデバイスの場合、デバッグログと、Mac コンピューター上で実行される **Xcode** を使用します。

1. iOS デバイスを Mac に接続し、 **[Applications]\(アプリケーション\)**  >  **[Utilities]\(ユーティリティ\)** に移動してコンソール アプリを開きます。 

2. **[アクション]** で、 **[Include Info Messages]\(情報メッセージを含める\)** と **[Include Debug Messages]\(デバッグ メッセージを含める\)** を選択します。

   ![ログ オプションを選択する](../protect/media/troubleshoot-scep-certificate-profiles/message-options.png)

3. 問題を再現し、次のようにログをテキスト ファイルに保存します。
   1. **[編集]**  >  **[すべて選択]** を選択して現在の画面のすべてのメッセージを選択し、 **[編集]**  >  **[コピー]** を選択してメッセージをクリップボードにコピーします。 
   2. TextEdit アプリケーションを開き、コピーしたログを新しいテキスト ファイルに貼り付けて、ファイルを保存します。


iOS および iPadOS デバイスのポータル サイト ログには、SCEP 証明書プロファイルに関する情報は含まれていません。

### <a name="logs-for-windows-devices"></a>Windows デバイスのログ

Windows を実行するデバイスの場合、Windows イベント ログを使用して、Intune で管理するデバイスの登録またはデバイス管理の問題を診断します。

デバイスで、 **[イベント ビューアー]**  >  **[アプリケーションとサービス ログ]**  >  **[Microsoft]**  >  **[Windows]**  >  **[DeviceManagement-Enterprise-Diagnostics-Provider]** を開きます。

![Windows イベント ログ](../protect/media/troubleshoot-scep-certificate-profiles/windows-event-log.png)

## <a name="next-steps"></a>次のステップ

[SCEP 証明書プロファイルの展開](troubleshoot-scep-certificate-profile-deployment.md)を確認します 
