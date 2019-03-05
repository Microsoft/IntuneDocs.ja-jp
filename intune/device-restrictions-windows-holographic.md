---
title: Windows Holographic Business デバイスの設定 - Microsoft Intune - Azure | Microsoft Docs
description: 登録解除、位置情報、パスワード、アプリ ストアからのアプリのインストール、Microsoft Edge の Cookie とポップアップ、Windows Defender、検索、クラウドと記憶域、Bluetooth の接続、システム時刻、Azure の使用状況データなど、Windows Holographic for Business の Microsoft Intune でのデバイス制限設定について説明し、これらの設定を構成します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f93ad05decb3cb4bf1fd6db87e9fb08f17280fcf
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2019
ms.locfileid: "57237607"
---
# <a name="windows-holographic-for-business-device-settings-to-allow-or-restrict-features-using-intune"></a>Intune を使用して機能を許可または制限する Windows Holographic for Business デバイスの設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事では、Microsoft Hololens などの Windows Holographic for Business デバイス上で制御できる、さまざまな設定について説明します。 モバイル デバイス管理 (MDM) ソリューションの一部として、これらの設定を使って機能の許可や無効化、セキュリティ管理などを行います。

## <a name="before-you-begin"></a>始める前に

[デバイス構成プロファイルを作成します](device-restrictions-configure.md#create-the-profile)。

## <a name="general"></a>全般

- **[手動での登録解除]**:ユーザーがデバイスから会社アカウントを手動で削除できるようにします。
- **[Cortana]**:Cortana による音声アシスタントを有効または無効にします。
- **[位置情報]**:デバイスが位置情報サービスの情報を使用できるかどうかを指定します。

## <a name="password"></a>パスワード

- **[パスワード]**:エンド ユーザーがデバイスにアクセスする際にパスワードの入力を要求します。
- **[デバイスがアイドル状態から戻るときにパスワードを必須とする]**:ユーザーがデバイスのロックを解除するときにパスワードの入力を必須にします。

## <a name="app-store"></a>アプリ ストア

- **[ストア アプリの自動更新]**:Microsoft ストアからインストールされたアプリの自動更新を許可します。
- **[信頼できるアプリのインストール]**:信頼済み証明書で署名されたアプリのサイドロードを許可します。
- **[開発者によるロック解除]**:サイドロードしたアプリのエンド ユーザーによる変更を許可するなど、Windows 開発者の設定を許可します。

## <a name="microsoft-edge-browser"></a>Microsoft Edge ブラウザー

- **[Cookie]**:ブラウザーがインターネット Cookie をデバイスに保存するように設定します。
- **[ポップアップ]**:ブラウザー内のポップアップ ウィンドウをブロックします (Windows 10 デスクトップのみに適用)。
- **[検索候補]**:検索語句を入力したときに、検索エンジンからサイトが提案されるようになります。
- **[パスワード マネージャー]**:Microsoft Edge Password Manager 機能を有効または無効にします。
- **[トラッキング拒否ヘッダーを送信する]**:ユーザーがアクセスする Web サイトへトラッキング拒否ヘッダーを送信できるように、Microsoft Edge ブラウザーを構成します。

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **[SmartScreen for Microsoft Edge]**:サイトへのアクセスとファイルのダウンロードに対して Microsoft Edge の SmartScreen を有効にします。

## <a name="search"></a>検索

- **[Search location]\(場所の検索\)** - 検索で場所を使用できるかどうかを指定します。 情報

## <a name="cloud-and-storage"></a>クラウドとストレージ

- **[Microsoft アカウント]**:ユーザーがデバイスに Microsoft アカウントを関連付けられるようにします。

## <a name="cellular-and-connectivity"></a>携帯ネットワークと接続性

- **[Bluetooth]**:ユーザーがデバイスの Bluetooth を有効にして構成できるようにするかどうかを制御します。
- **[Bluetooth の検出可能性]**:その他の Bluetooth 対応デバイスにより、デバイスが検出されるようにします。
- **[Bluetooth 広告]**:デバイスが Bluetooth 経由で広告を受信できるようにします。

## <a name="control-panel-and-settings"></a>コントロール パネルと設定

- **[システム時刻の変更]**:エンド ユーザーがシステム時刻を変更できないようにします。

## <a name="kiosk---obsolete"></a>キオスク - 現在不使用

これらの設定は読み取り専用であり、変更することはできません。 キオスク モードを構成する場合は、「[キオスクの設定](kiosk-settings-holographic.md)」を参照してください。

通常、キオスク デバイスでは特定のアプリが実行されます。 ユーザーは、キオスク アプリ以外のデバイスの機能にアクセスすることはできません。

- **[キオスク モード]**:ポリシーによってサポートされるキオスク モードの種類を識別します。 次のオプションがあります。

  - **[未構成]** (既定):このポリシーでは、キオスク モードが有効になりません。 
  - **[シングル アプリ キオスク]**:このプロファイルの場合、デバイス上で 1 つのアプリのみを実行できます。 ユーザーがサインインすると、特定のアプリが起動します。 また、このモードでは、ユーザーによる新しいアプリを開く操作や、実行中のアプリを変更する操作が制限されます。
  - **[マルチ アプリ キオスク]**:このプロファイルでは、デバイスは複数のアプリを実行できます。 ユーザーはプロファイルに追加されているアプリだけを利用できます。 マルチ アプリ キオスク (または固定目的デバイス) の利点は、ユーザーがアクセスできるのは必要なアプリだけなので、わかりやすいエクスペリエンスがユーザーに提供されることです。 また、必要のないアプリはビューから削除されます。 
  
    マルチ アプリ キオスク エクスペリエンス向けのアプリを追加する場合は、スタート メニュー レイアウト ファイルも追加します。 [スタート メニュー レイアウト ファイル](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-file-for-intune)には、Intune で使用できるサンプル XML が含まれています。 

#### <a name="single-app-kiosks"></a>シングル アプリ キオスク

次の設定を入力します。

- **[ユーザー アカウント]**:(デバイスの) ローカル ユーザー アカウントか、キオスク アプリに関連付けられている Azure AD アカウント ログインを入力します。 Azure AD ドメインに参加しているアカウントについては、`domain\username@tenant.org` 形式を使用してアカウントを入力します。 

    自動ログオンが有効になっている公開環境のキオスクの場合、最小特権 (ローカルの標準ユーザー アカウントなど) を持つユーザーの種類を使用する必要があります。 キオスク モードの Azure Active Directory (AD) アカウントを構成するには、`AzureAD\user@contoso.com` 形式を使用します。

- **[アプリのアプリケーション ユーザー モデル ID (AUMID)]**:キオスク アプリの AUMID を入力します。 詳細については、「[Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)」 (インストール済みアプリのアプリケーション ユーザー モデル ID を見つける) を参照してください。

## <a name="reporting-and-telemetry"></a>レポートとテレメトリ

- **[使用状況データの共有]**:診断データの送信レベルを選択します。

## <a name="next-steps"></a>次の手順

[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
