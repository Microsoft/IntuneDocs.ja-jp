---
title: Microsoft Intune での iOS デバイスおよび Android デバイス向けの Outlook 設定
description: iOS デバイスと Android デバイスで実行されている Microsoft Outlook を設定するための構成ポリシーを作成します。
keywords: ''
author: Erikre
ms.author: erikre
ms.reviewer: smithre4
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 24ed1a895dd3e4cad6111b40913b43fa9c6a3cec
ms.sourcegitcommit: 11bd3dbbc9dd762df7c6d20143f2171799712547
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2018
ms.locfileid: "48903524"
---
# <a name="microsoft-outlook-configuration-settings"></a>Microsoft Outlook の構成設定 

iOS デバイスと Android デバイスで実行されている Microsoft Outlook を設定するための構成ポリシーを使用します。 

管理対象の iOS デバイス用のアプリ構成ポリシーを作成するには、「[管理対象の iOS デバイス用アプリ構成ポリシーを追加する](app-configuration-policies-use-ios.md)」を参照してください。 管理対象の Android デバイス用のアプリ構成ポリシーを作成するには、「[管理対象の Android デバイス用アプリ構成ポリシーを追加する](app-configuration-policies-use-android.md)」を参照してください。 

## <a name="configuration-settings"></a>構成設定

Intune で構成ポリシーを追加すると、Microsoft Outlook を構成する特定の設定を行うことができます。 **[構成設定]** ウィンドウで、メール アカウントの構成を設定できます。

### <a name="basic-authentication-email-account-settings"></a>基本認証用メール アカウントの設定
iOS および Android 用 Outlook を使用すると、Exchange 管理者は、ActiveSync プロトコルによる基本認証を使用するオンプレミスのユーザーに対して、アカウントの構成を "プッシュ" することができます。 詳細については、「[基本認証を使用した iOS および Android 向けの Outlook でのアカウントのセットアップ](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/account-setup)」を参照してください。 アカウントのセットアップ構成を有効にするには、次の設定を構成します。

- **[電子メール サーバー]**: オンプレミスの Exchange サーバーのホスト名を入力します (mail.contoso.com など)。
- **[メール アカウント名]**: メール アカウントの表示名を入力します。 この名前は、ユーザーのデバイス上に表示されます。
- **[AAD からのユーザー名の属性]**: Intune が Azure Active Directory (Azure AD) から取得する名前。 Intune はこのプロファイルで使用されるユーザー名を動的に生成します。 次のような方法があります。
  - **[ユーザー プリンシパル名]**: `user1` または `user1@contoso.com` などの名前を取得します。
  - **[プライマリ SMTP アドレス]**: `user1@contoso.com` のような書式で電子メール アドレスを取得します。
- **[AAD からのメール アドレス属性]**: ユーザーの電子メール アドレスを生成する方法を選択します。 完全プリンシパル名を電子メール アドレスとして使用する場合は **[ユーザー プリンシパル名]** (`user1@contoso.com` または `user1`) を選択し、Exchange へのサインインにプライマリ SMTP アドレスを使用する場合は **[プライマリ SMTP アドレス]** (`user1@contoso.com`) を選択します。 **[プライマリ SMTP アドレス]** を選択することをお勧めします。
- **[アカウントのドメイン]**: (省略可能) アカウントのドメイン。

## <a name="next-steps"></a>次の手順
[Intune で電子メールを設定する](email-settings-configure.md)

