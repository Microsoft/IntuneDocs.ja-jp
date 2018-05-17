---
title: Microsoft Intune - Azure での Windows Holographic for Business のデバイス制限 | Microsoft Docs
description: 登録解除、位置情報、パスワード、アプリ ストアからのアプリのインストール、Edge の Cookie とポップアップ、Windows Defender、検索、クラウドと記憶域、Bluetooth の接続、システム時刻、Azure の使用状況データなど、Windows Holographic for Business の Microsoft Intune でのデバイス制限設定について説明し、これらの設定を構成します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e8a1abb4229b3e6b4c91cfd49b4f66dbe739ea7d
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="device-restriction-settings-for-windows-holographic-for-business-in-intune"></a>Intune での Windows Holographic for Business のデバイス制限設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Hololens など、Windows Holographic for Business を実行しているデバイスでは、以下のデバイス制限設定がサポートされます。

## <a name="general"></a>全般

- **[手動での登録解除]** - ユーザーがデバイスから会社アカウントを手動で削除できるようにします。
- **[Cortana]** - Cortana による音声アシスタントを有効または無効にします。
- **[位置情報]** - デバイスが位置情報サービスの情報を使用できるかどうかを指定します。

## <a name="password"></a>パスワード
-   **[パスワード]** - エンド ユーザーがデバイスにアクセスする際にパスワードの入力を要求します。
    -   **[デバイスがアイドル状態から戻るときにパスワードを必須にする]** - ユーザーがデバイスのロックを解除するときにパスワードの入力を必須にします。

## <a name="app-store"></a>アプリ ストア

-   **[ストア アプリの自動更新]** - Microsoft ストアからインストールされたアプリの自動更新を許可します。
-   **[信頼できるアプリのインストール]** - 信頼済み証明書で署名されたアプリのサイドロードを許可します。
-   **[開発者によるロック解除]** - サイドロードしたアプリのエンド ユーザーによる変更を許可するなど、Windows 開発者の設定を許可します。

## <a name="edge-browser"></a>Microsoft Edge ブラウザー

-   **[Cookie]** - ブラウザーがインターネット Cookie をデバイスに保存するように設定します。
-   **[ポップアップ]** - ブラウザー内のポップアップ ウィンドウをブロックします (Windows 10 デスクトップのみに適用)。
-   **[検索候補]** - 検索語句を入力したときに、検索エンジンからサイトが提案されるようになります。
-   **[パスワード マネージャー]** - Microsoft Edge Password Manager 機能を有効または無効にします。
- **[トラッキング拒否ヘッダーを送信する]** - ユーザーがアクセスする Web サイトに Do Not Track ヘッダーを送信するように、Microsoft Edge ブラウザーを構成します。

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **[SmartScreen for Microsoft Edge]** - サイトへのアクセスとファイルのダウンロードに対して Edge の SmartScreen を有効にします。

## <a name="search"></a>検索
- **[Search location]\(場所の検索\)** - 検索で場所を使用できるかどうかを指定します。 情報

## <a name="cloud-and-storage"></a>クラウドとストレージ
-   **[Microsoft アカウント]** - ユーザーがデバイスに Microsoft アカウントを関連付けられるようにします。

## <a name="cellular-and-connectivity"></a>携帯ネットワークと接続性

-   **[Bluetooth]** - ユーザーがデバイスの Bluetooth を有効にして構成できるようにするかどうかを制御します。
-   **[Bluetooth の検出可能性]** - その他の Bluetooth 対応デバイスにより、デバイスが検出されるようにします。
-   **[Bluetooth 広告]** - デバイスが Bluetooth 経由で広告を受信できるようにします。

## <a name="control-panel-and-settings"></a>コントロール パネルと設定

- **[システム時刻の変更]** - エンド ユーザーがデバイスの日付と時刻を変更することを防止します。

## <a name="kiosk"></a>キオスク

通常、キオスク デバイスでは特定のアプリが実行されます。 ユーザーは、キオスク アプリ以外のデバイスの機能にアクセスすることはできません。

- **[キオスク モード]** - ポリシーによってサポートされるキオスク モードの種類を識別します。 次のオプションがあります。

  - **[未構成]** (既定) - このポリシーでは、キオスク モードが有効になりません。 
  - **[シングル アプリ キオスク]** - このプロファイルの場合、デバイスで 1 つのアプリのみを実行できます。 ユーザーがサインインすると、特定のアプリが起動します。 また、このモードでは、ユーザーによる新しいアプリを開く操作や、実行中のアプリを変更する操作が制限されます。
  - **[マルチ アプリ キオスク]** - このプロファイルでは、デバイスは複数のアプリを実行できます。 ユーザーはプロファイルに追加されているアプリだけを利用できます。 マルチ アプリ キオスク (または固定目的デバイス) の利点は、ユーザーがアクセスできるのは必要なアプリだけなので、わかりやすいエクスペリエンスがユーザーに提供されることです。 また、必要のないアプリはビューから削除されます。 
  
    マルチ アプリ キオスク エクスペリエンス向けのアプリを追加する場合は、スタート メニュー レイアウト ファイルも追加します。 [スタート メニュー レイアウト ファイル](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-file-for-intune)には、Intune で使用できるサンプル XML が含まれています。 

#### <a name="single-app-kiosks"></a>シングル アプリ キオスク
次の設定を入力します。

- **[ユーザー アカウント]** - (デバイスの) ローカル ユーザー アカウントか、キオスク アプリに関連付けられている Azure AD アカウント ログインを入力します。 Azure AD ドメインに参加しているアカウントについては、`domain\username@tenant.org` 形式を使用してアカウントを入力します。 

    自動ログオンが有効になっている公開環境のキオスクの場合、最小特権 (ローカルの標準ユーザー アカウントなど) を持つユーザーの種類を使用する必要があります。 キオスク モードの Azure Active Directory (AD) アカウントを構成するには、`AzureAD\user@contoso.com` 形式を使用します。

- **[アプリのアプリケーション ユーザー モデル ID (AUMID)]** - キオスク アプリの AUMID を入力します。 詳細については、「[Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)」 (インストール済みアプリのアプリケーション ユーザー モデル ID を見つける) を参照してください。

## <a name="reporting-and-telemetry"></a>レポートとテレメトリ

- **[使用状況データの共有]** - 診断データの送信レベルを選択します。
