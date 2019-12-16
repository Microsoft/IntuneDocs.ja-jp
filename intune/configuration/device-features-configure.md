---
title: Microsoft Intune - Azure での iOS または macOS デバイス プロファイルの作成 | Microsoft Docs
description: Microsoft Intune で iOS または macOS デバイス プロファイルを追加または作成し、AirPrint、ホーム画面のレイアウト、アプリの通知、共有デバイス、シングル サインイン、Web コンテンツ フィルター設定を構成します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d887c7bc3c7e9ea8b6719993b5ba4909e9c18ea8
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992924"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Intune での iOS または macOS デバイスの機能設定の追加

Intune には、管理者が iOS および macOS デバイスを制御するために役立つ多くの機能と設定が含まれています。 たとえば、管理者には次の機能があります。

- ネットワーク内の AirPrint プリンターへのアクセスをユーザーに許可する
- 新しいページの追加を含め、アプリとフォルダーをホーム画面に追加する
- アプリの通知を表示する場合と方法を選択する
- 特に共有デバイスに対して、メッセージまたは資産タグを表示するようにロック画面を構成する
- アプリ間で資格情報を共有するためのセキュリティで保護されたシングル サインオン エクスペリエンスをユーザーに提供する
- 成人向けの言葉を使用している Web サイトをフィルター処理し、特定の Web サイトを許可またはブロックする

Intune では、"構成プロファイル" を使用して、お客様の組織のニーズに合わせてこのような設定を作成およびカスタマイズします。 これらの機能をプロファイルに追加した後は、そのプロファイルをお客様の組織内の iOS および macOS デバイスにプッシュまたは展開します。

この記事では、構成できるさまざまな機能について説明し、デバイス構成プロファイルを作成する方法を示します。 また、[iOS](ios-device-features-settings.md) および [macOS](macos-device-features-settings.md) デバイスで使用できるすべての設定を確認することもできます。

## <a name="airprint"></a>AirPrint

AirPrint は、デバイスからワイヤレス ネットワーク経由でファイルを印刷できるようにする Apple の機能です。 Intune では、AirPrint の情報をデバイスに追加できます。

Intune で構成できる設定の一覧については、[iOS での AirPrint](ios-device-features-settings.md#airprint) および [macOS での AirPrint](macos-device-features-settings.md#airprint) に関する記事を参照してください。

AirPrint の詳細については、Apple の Web サイトの「[AirPrint について](https://support.apple.com/HT201311)」を参照してください。

適用対象:

- iOS 7.0 以降
- iPadOS 13.0 以降
- macOS 10.10 以降

## <a name="app-notifications"></a>アプリの通知

iOS および iPad デバイス上のアプリで通知を受け取る方法を選択します。 たとえば、Intune から、通知センターに表示されるようにアプリの通知を送信したり、ロック画面に表示したり、音を鳴らしたりすることができます。

Intune で構成できる設定の一覧については、[iOS でのアプリの通知](ios-device-features-settings.md#app-notifications)に関する記事を参照してください。

この機能の詳細については、Apple の Web サイトの「[通知](https://developer.apple.com/notifications/)」を参照してください。

適用対象:

- iOS 9.3 以降
- iPadOS 13.0 以降

## <a name="associated-domains"></a>関連付けられたドメイン

関連付けられたドメインを使用すると、お使いのドメイン (`contoso.com` など) と自分のアプリの間にリレーションシップを作成できます。 この機能では次のことができます。

- アプリと組織の Web サイトの間で、データやサインインの資格情報を共有します。
- シングル サインオン アプリ拡張機能、ユニバーサル リンク、パスワード オートコンプリートなど、Web サイトに基づくアプリの機能を使用します。

  たとえば、関連付けられたドメインを作成し、アプリに関連付けられている Web サイトで、パスワードをオートコンプリートして、パスワードなどの資格情報を推奨できるようにします。

Intune で構成できる設定の一覧については、[macOS での関連付けられたドメイン](macos-device-features-settings.md#associated-domains)に関する記事をご覧ください。

この機能の詳細については、Apple の Web サイトの「[アプリの関連付けられたドメインの設定](https://developer.apple.com/documentation/security/password_autofill/setting_up_an_app_s_associated_domains)」を参照してください。

適用対象:

- macOS 10.15 以降

## <a name="home-screen-layout"></a>ホーム画面のレイアウト

これらの設定では、iOS および iPadOS デバイスのドック画面とホーム画面上のアプリのレイアウトとフォルダーを構成します。 次の操作を行います。

- **[ドッキング]** の設定を使用して、アプリまたはフォルダーを画面に追加します。 たとえば、デバイスのドックに Safari や Mail アプリを表示します。
- ホーム画面に表示したい**ページ**や、各ページに表示するアプリを追加します。 たとえば、**Contoso** ページを追加し、このページに設定アプリを追加します。

Intune で構成できる設定の一覧については、[iOS でのホーム画面のレイアウト](ios-device-features-settings.md#home-screen-layout)に関する記事を参照してください。

適用対象:

- iOS 9.3 以降
- iPadOS 13.0 以降

## <a name="lock-screen-message"></a>ロック画面のメッセージ

これらの設定を使用して、サインイン ウィンドウとロック画面にカスタム メッセージまたはテキストを表示します。 たとえば、"忘れ物として見つけた場合の返却先" メッセージを入力したり、資産タグ情報を表示したりできます。

Intune で構成できる設定の一覧については、[iOS でのロック画面メッセージの設定](ios-device-features-settings.md#lock-screen-message)に関する記事を参照してください。

ロック画面のメッセージの詳細については、Apple の Web サイトの「[LockScreenMessage](https://developer.apple.com/documentation/devicemanagement/lockscreenmessage)」を参照してください。

適用対象:

- iOS 9.3 以降
- iPadOS 13.0 以降

## <a name="login-items"></a>ログイン項目

この機能は、ユーザーがデバイスにサインインしたときに開くアプリ、カスタム アプリ、ファイル、フォルダーを選択するために使用します。

Intune で構成できる設定の一覧については、[macOS でのログイン項目](macos-device-features-settings.md#login-items)に関する記事を参照してください。

適用対象:

- macOS 10.13 以降

## <a name="login-window"></a>ログイン ウィンドウ

ログイン画面の表示およびサインインする前にユーザーが使用できる機能を制御します。 たとえば、カスタム メッセージを含むバナーを追加したり、スリープ ボタンを表示するかどうかを選択したりします。

Intune で構成できる設定の一覧については、[macOS でのログイン ウィンドウ](macos-device-features-settings.md#login-window)に関する記事を参照してください。

適用対象:

- macOS 10.7 以降

## <a name="single-sign-on"></a>シングル サインオン

ほとんどの基幹業務 (LOB) アプリでは、セキュリティに対応するために、何らかのレベルのユーザー認証が必要です。 多くの場合、ユーザーは認証のために同じ資格情報を繰り返し入力する必要があります。 ユーザーの操作環境を改善するため、開発者はシングル サインオン (SSO) を使うアプリを作成できます。 シングル サインオンを使用すると、ユーザーが資格情報を入力する必要のある回数が減ります。

シングル サインオンを使用するには、次の条件を満たしている必要があります。

- デバイス上のシングル サインオンでユーザー資格情報ストアを探すようにアプリがコーディングされていること。
- iOS デバイスのシングル サインオン用に Intune が構成されていること。

![[シングル サインオン] ウィンドウ](./media/device-features-configure/sso-blade.png)

Intune で構成できる設定の一覧については、[iOS でのシングル サインオン](ios-device-features-settings.md#single-sign-on)に関する記事を参照してください。

適用対象:

- iOS 7.0 以降
- iPadOS 13.0 以降

## <a name="single-sign-on-app-extension"></a>シングル サインオン アプリの拡張機能

これらの設定では、iOS、iPadOS、macOS デバイスでのシングル サインオン (SSO) を有効にするアプリ拡張機能を構成します。 ほとんどの基幹業務 (LOB) アプリおよび組織の Web サイトでは、何らかのレベルのセキュリティで保護されたユーザー認証が必要です。 多くの場合、ユーザーは認証のために同じ資格情報を繰り返し入力する必要があります。 SSO を使用すると、ユーザーは資格情報を 1 回入力した後でアプリや Web サイトにアクセスできます。 サインインした後、ユーザーは、アプリや Web サイトに自動的にアクセスするか、または顔 ID、タッチ ID、Apple のパスコードを使用してアクセスすることができます。

Intune では、これらの設定を使用して、組織、ID プロバイダー、または Apple によって作成された SSO アプリ拡張機能を構成します。 SSO アプリ拡張機能では、ユーザーの認証が処理されます。 これらの設定により、リダイレクトの種類と資格情報の種類の SSO アプリ拡張機能が構成されます。

- このリダイレクトの種類は、OAuth や SAML2 などの最新の認証プロトコル向けに設計されています。
- 資格情報の種類は、チャレンジと応答の認証フロー用に設計されています。 Apple で提供される Kerberos 固有の資格情報拡張機能と汎用的な資格情報拡張機能から選択できます。

Intune で構成できる設定の一覧については、[iOS SSO アプリ拡張機能](ios-device-features-settings.md#single-sign-on-app-extension)と [macOS SSO アプリ拡張機能](macos-device-features-settings.md#single-sign-on-app-extension)の記事を参照してください。

SSO アプリ拡張機能の開発の詳細については、Apple の Web サイトの「[Extensible Enterprise SSO](https://developer.apple.com/videos/play/tech-talks/301)」を参照してください。 機能に関する Apple の説明をお読みになるには、「[シングル サインオン機能拡張ペイロードの設定](https://support.apple.com/guide/mdm/single-sign-on-extensions-mdmfd9cdf845/web)」を参照してください。 

> [!NOTE]
> **シングル サインオン アプリの拡張機能**の機能は、**シングル サインオン**機能とは異なります。
>
> - **シングル サインオン アプリの拡張機能**設定は、iPadOS 13.0 以降、iOS 13.0 以降、および macOS 10.15 以降に適用されます。 **シングル サインオン**設定は、iPadOS 13.0 (およびそれ以降) および iOS 7.0 以降に適用されます。
>
> - **シングル サインオン アプリの拡張機能**設定では、ID プロバイダーまたは組織がシームレスなエンタープライズ サインオン エクスペリエンスを提供するために使用する、拡張機能を定義します。 **シングル サインオン**設定では、ユーザーがサーバーまたはアプリにアクセスするときの Kerberos アカウント情報を定義します。
>
> - **シングル サインオン アプリ拡張機能**では、Apple オペレーティング システムを使用して認証が行われます。 そのため、**シングル サインオン**よりも優れたエンドユーザー エクスペリエンスが提供される可能性があります。
>
> - 開発の観点から説明すると、**シングル サインオン アプリの拡張機能**を使用すると、任意の種類のリダイレクト SSO または資格情報 SSO 認証を使用できます。 **シングル サインオン**では、Kerberos SSO 認証のみを使用できます。
>
> - Kerberos **シングル サインオン アプリの拡張機能**は、Apple によって開発され、iOS 13.0 以降と macOS 10.15 以降のプラットフォームに組み込まれています。 組み込みの Kerberos 拡張機能を使用すると、Kerberos 認証をサポートするネイティブ アプリや Web サイトにユーザーをログインさせることができます。 **シングル サインオン**は、Apple による Kerberos の実装ではありません。
>
> - 組み込みの Kerberos **シングル サインオン アプリの拡張機能**では、Web ページとアプリへの Kerberos チャレンジが**シングル サインオン**と同じように処理されます。 ただし、組み込みの Kerberos 拡張機能では、パスワードの変更がサポートされ、エンタープライズ ネットワークでの動作が優れています。 Kerberos **シングル サインオン アプリの拡張機能**と**シングル サインオン**のどちらにするかを決定するときは、パフォーマンスと機能がより優れている拡張機能を使用することをお勧めします。

適用対象:

- iOS 13.0 以降
- iPadOS 13.0 以降
- macOS 10.15 以降

## <a name="wallpaper"></a>壁紙

監視対象の iOS デバイスにカスタムの .png、.jpg、または .jpeg 画像を追加します。 たとえば、Intune を使用して、デバイスのロック画面に会社のロゴを追加します。

Intune で構成できる設定の一覧については、[iOS の壁紙](ios-device-features-settings.md#wallpaper)に関する記事を参照してください。

適用対象:

- iOS
- iPadOS 13.0 以降

## <a name="web-content-filter"></a>Web コンテンツ フィルター

これらの設定では、Apple の組み込みの AutoFilter アルゴリズムを使用して Web ページを評価し、成人向けのコンテンツと成人向けの言葉をブロックできます。 また、許可されている Web リンクと制限された Web リンクの一覧を作成することもできます。 たとえば、`contoso` の Web サイトのみを開くことを許可できます。

Intune で構成できる設定の一覧については、[iOS の Web コンテンツ フィルター](ios-device-features-settings.md#web-content-filter)に関する記事を参照してください。

適用対象:

- iOS 7.0 以降
- iPadOS 13.0 以降

## <a name="create-a-device-profile"></a>デバイス プロファイルの作成

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **名前**: ポリシーのわかりやすい名前を入力します。 後で簡単に識別できるよう、ポリシーに名前を付けます。 たとえば、適切なポリシー名は **macOS: ログイン画面を構成する**などです。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]** :デバイスのプラットフォームを選択します。 次のようなオプションがあります。  
        - **iOS/iPadOS**
        - **macOS**
    - **[プロファイルの種類]** : **[デバイスの機能]** を選択します。

4. 選択したプラットフォームによって構成できる設定が異なります。 詳細な設定については、お使いのプラットフォームを選択してください。

    - [iOS/iPadOS](ios-device-features-settings.md)
    - [macOS](macos-device-features-settings.md)

5. 完了したら、 **[OK]**  >  **[作成]** を選択して変更を保存します。

プロファイルが作成されて、プロファイル一覧に表示されます。 必ず[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)してください。

## <a name="next-steps"></a>次の手順

プロファイルが作成されると、割り当てることができます。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

[iOS](ios-device-features-settings.md) および [macOS](macos-device-features-settings.md) デバイスのすべてのデバイス機能設定を表示します。
