---
title: Microsoft Intune での電子メール プロファイルのトラブルシューティング - Azure | Microsoft Docs
description: 電子メール プロファイルの重複や Samsung KNOX Standard Android デバイスでのエラーなど、Microsoft Intune の電子メール プロファイルに関する一般的な問題と解決方法について説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a19830130f992a002b73402f5e13a8f062539917
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512672"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Microsoft Intune の電子メール プロファイルに関する一般的な問題と解決方法

一般的な電子メール プロファイルに関する問題と、そのトラブルシューティングと解決方法について説明します。

## <a name="what-you-need-to-know"></a>知っておく必要がある情報

- 電子メール プロファイルは、デバイスを登録したユーザーに対して展開されます。 電子メール プロファイルを構成するために、Intune では、登録時にユーザーの電子メール プロファイルの Azure Active Directory (AD) プロパティが使用されます。 「[デバイスにメール設定を追加する](email-settings-configure.md)」はお勧めのリソースです。
- Android Enterprise の場合、マネージド Google Play ストアを使用して Gmail または Nine for Work を展開します。 手順については、[マネージド Google Play アプリの追加](../apps/apps-add-android-for-work.md)に関する記事を参照してください。
- iOS および iPadOS 用と Android 用の Microsoft Outlook は、電子メール プロファイルをサポートしていません。 代わりに、アプリ構成ポリシーを展開します。 詳細については、[Outlook の構成設定](../apps/app-configuration-policies-outlook.md)に関する記事を参照してください。
- (ユーザー グループではなく) デバイス グループを対象とした電子メール プロファイルがデバイスに配信されない可能性があります。 デバイスにプライマリ ユーザーがいる場合、デバイスのターゲット設定は機能するはずです。 電子メール プロファイルにユーザー証明書が含まれている場合は、必ずユーザー グループをターゲットにしてください。
- ユーザーには、電子メール プロファイルのパスワードの入力が繰り返し求められる場合があります。 このシナリオでは、電子メール プロファイルで参照されているすべての証明書を確認してください。 いずれかの証明書がユーザーを対象としていない場合、Intune では電子メール プロファイルの展開が再試行されます。

## <a name="device-already-has-an-email-profile-installed"></a>デバイスに電子メール プロファイルが既にインストールされている

ユーザーが Intune または Office 365 MDM に登録する前に電子メール プロファイルを作成すると、Intune によって展開された電子メール プロファイルが想定どおりに動作しない場合があります。

- **iOS および iPadOS**:Intune は、ホスト名と電子メール アドレスに基づいて既存の重複する電子メール プロファイルを検出します。 ユーザーが作成した電子メール プロファイルがあると、Intune で作成されたプロファイルが展開されません。 これは一般的な問題です。iOS および iPadOS ユーザーは、通常、電子メール プロファイルを作成し、それから登録するためです。 ポータル サイト アプリには、ユーザーが準拠していないと表示され、電子メール プロファイルを削除するようにユーザーが求められる場合があります。

  Intune プロファイルを展開できるように、ユーザーは電子メール プロファイルを削除する必要があります。 この問題を回避するには、電子メール プロファイルを登録し、展開を Intune に許可するようにユーザーに指示します。 これで、ユーザーは電子メール プロファイルを作成できるようになります。

- **Windows**: Intune は、ホスト名と電子メール アドレスに基づいて既存の重複する電子メール プロファイルを検出します。 Intune は、ユーザーによって作成された既存の電子メール プロファイルを上書きします。

- **Samsung KNOX Standard**:Intune は、電子メール アドレスに基づいて重複する電子メール アカウントを識別し、Intune プロファイルで上書きします。 ユーザーがそのアカウントを構成した場合、Intune プロファイルによって再び上書きされます。 このため、アカウントの構成を上書きされたユーザーが混乱する可能性があります。

Samsung KNOX では、プロファイルを識別するためにホスト名が使用されません。 異なるホスト上の同じ電子メール アドレスに展開する複数の電子メール プロファイルは、相互に上書きされるため、作成しないことをお勧めします。

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>KNOX Standard デバイスのエラー 0x87D1FDE8

**問題**:さまざまな Android デバイスで Samsung KNOX Standard の Exchange Active Sync 電子メール プロファイルを作成して展開すると、デバイスの [プロパティ] > [ポリシー] タブに **0x87D1FDE8** または "**修復できませんでした**" というエラーが報告される。

Samsung KNOX の EAS プロファイルおよびソース ポリシーの構成を確認します。 Samsung Note 同期オプションはサポートされなくなったため、このオプションをプロファイルで選択することはできません。 デバイスには、ポリシーを処理するための十分な時間を最大 24 時間設定してください。

## <a name="unable-to-send-images-from--email-account"></a>電子メール アカウントから画像を送信できない

電子メール アカウントを自動的に構成したユーザーが、自分のデバイスから画像を送信することができません。 このシナリオは、 **[サードパーティ アプリケーションからの電子メール送信を許可する]** が有効ではない場合に発生する可能性があります。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** 、 **[構成プロファイル]** の順に選択します。
3. 電子メール プロファイル > **[プロパティ]**  >  **[設定]** の順に選択します。
4. **[Allow e-mail to be sent from third-party applications]\(サードパーティ製アプリケーションからの電子メールの送信を許可\)** する設定を **[有効]** に設定します。

## <a name="next-steps"></a>次のステップ

[Microsoft からサポート](../fundamentals/get-support.md)を受けるか、[コミュニティ フォーラム](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)を使用します。
