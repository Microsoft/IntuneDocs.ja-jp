---
title: Microsoft Intune での電子メール プロファイルのトラブルシューティング - Azure | Microsoft Docs
description: 電子メール プロファイルの重複や Samsung KNOX Standard Android デバイスでのエラーなど、Microsoft Intune の電子メール プロファイルに関する一般的な問題と解決方法について説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/17/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: ec3a5a5aa4d30dcac0f954057f0cc51ffde6a950
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734298"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Microsoft Intune の電子メール プロファイルに関する一般的な問題と解決方法

一般的な電子メール プロファイルに関する問題と、そのトラブルシューティングと解決方法について説明します。

## <a name="what-you-need-to-know"></a>知っておく必要がある情報

- 電子メールプロファイルは、デバイスを登録したユーザーに対して展開されます。 電子メールプロファイルを構成するために、Intune では、登録時にユーザーの電子メールプロファイルで Azure Active Directory (AD) プロパティを使用します。 [デバイスへの電子メール設定の追加](email-settings-configure.md)は、適切なリソースである可能性があります。
- Configuration Manager ハイブリッドから Intune スタンドアロンに移行した後、Configuration Manager ハイブリッドからの電子メールプロファイルは、デバイスに7日間保持されます。 これは通常の動作です。 電子メールプロファイルをすぐに削除する必要がある場合は、 [Intune サポート](../fundamentals/get-support.md)にお問い合わせください。
- Android Enterprise の場合は、管理された Google Play ストアを使用して Gmail または9の for Work をデプロイします。 [管理された[Google Play アプリの追加](../apps/apps-add-android-for-work.md)の手順を示します。
- IOS および Android 用の Microsoft Outlook では、電子メールプロファイルはサポートされていません。 代わりに、アプリ構成ポリシーを展開します。 詳細については、「 [Outlook の構成設定](../apps/app-configuration-policies-outlook.md)」を参照してください。
- デバイスグループ (ユーザーグループではない) を対象とした電子メールプロファイルがデバイスに配信されない可能性があります。 デバイスにプライマリユーザーがいる場合は、デバイスのターゲット設定が機能します。 電子メールプロファイルにユーザー証明書が含まれている場合は、必ずユーザーグループを対象にしてください。
- ユーザーは、電子メールプロファイルのパスワードの入力を繰り返し求められる場合があります。 このシナリオでは、電子メールプロファイルで参照されているすべての証明書を確認します。 証明書のいずれかがユーザーを対象としていない場合、Intune は電子メールプロファイルの展開を再試行します。

## <a name="device-already-has-an-email-profile-installed"></a>デバイスに電子メール プロファイルが既にインストールされている

Intune または Office 365 MDM に登録する前にユーザーが電子メールプロファイルを作成した場合、Intune によって展開された電子メールプロファイルが想定どおりに動作しないことがあります。

- **iOS**: Intune は、ホスト名と電子メール アドレスに基づいて既存の重複する電子メール プロファイルを検出します。 ユーザーが作成した電子メール プロファイルがあると、Intune で作成されたプロファイルが展開されません。 これは一般的な問題です。iOS ユーザーは通常、電子メール プロファイルを作成し、それから登録するためです。 ポータル サイト アプリには、ユーザーが準拠していないと表示され、電子メール プロファイルを削除するようにユーザーが求められる場合があります。

  Intune プロファイルを展開できるように、ユーザーは電子メール プロファイルを削除する必要があります。 この問題を回避するには、電子メール プロファイルを登録し、展開を Intune に許可するようにユーザーに指示します。 これで、ユーザーは電子メール プロファイルを作成できるようになります。

- **Windows**: Intune は、ホスト名と電子メール アドレスに基づいて既存の重複する電子メール プロファイルを検出します。 Intune は、ユーザーによって作成された既存の電子メール プロファイルを上書きします。

- **Samsung KNOX Standard**: Intune は、電子メール アドレスに基づいて重複する電子メール アカウントを識別し、Intune プロファイルで上書きします。 ユーザーがそのアカウントを構成した場合、Intune プロファイルによって再び上書きされます。 このため、アカウントの構成を上書きされたユーザーが混乱する可能性があります。

Samsung KNOX では、プロファイルを識別するためにホスト名が使用されません。 異なるホスト上の同じ電子メール アドレスに展開する複数の電子メール プロファイルは、相互に上書きされるため、作成しないことをお勧めします。

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>KNOX Standard デバイスのエラー 0x87D1FDE8

**問題**: さまざまな Android デバイスで Samsung KNOX Standard の Exchange Active Sync 電子メール プロファイルを作成して展開すると、デバイスの [プロパティ] > [ポリシー] タブに **0x87D1FDE8** または "**修復できませんでした**" というエラーが報告される。

Samsung KNOX の EAS プロファイルおよびソース ポリシーの構成を確認します。 Samsung Note 同期オプションはサポートされなくなったため、このオプションをプロファイルで選択することはできません。 デバイスには、ポリシーを処理するための十分な時間を最大 24 時間設定してください。

## <a name="unable-to-send-images-from--email-account"></a>電子メール アカウントから画像を送信できない

電子メール アカウントを自動的に構成したユーザーが、自分のデバイスから画像を送信することができません。 このシナリオは、 **[サードパーティ アプリケーションからの電子メール送信を許可する]** が有効ではない場合に発生する可能性があります。

### <a name="intune-solution"></a>Intune での解決方法

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイス構成]**  >  **[プロファイル]** を選択します。
3. 電子メールプロファイル >**プロパティ** > **設定**を選択します。
4. **[サードパーティ製アプリケーションからの電子メールの送信を許可]** する 設定を **[有効]** に設定します。

### <a name="configuration-manager-hybrid"></a>Configuration Manager ハイブリッド

1. Configuration Manager コンソール > **[資産とコンプライアンス]** の順に開きます。

2. **[概要]**  >  **[コンプライアンス設定]**  >  **[会社のリソースへのアクセス]** の順に展開して、 **[電子メール プロファイル]** を選択します。

3. 電子メール プロファイルを右クリックし、 **[プロパティ]** を開きます。

4. **[同期設定]** タブで、 **[サード パーティ アプリケーションから電子メールを送信できるようにする]** をオンにします。

## <a name="next-steps"></a>次の手順

[Microsoft からサポート](../fundamentals/get-support.md)を受けるか、[コミュニティ フォーラム](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)を使用します。
