---
title: Microsoft Intune での Android デバイスと Android 仕事用プロファイル デバイス用の電子メール設定 - Azure | Microsoft Docs
description: Exchange サーバーを使用するデバイス構成電子メール プロファイルを作成し、Azure Active Directory から属性を取得します。 Android デバイスと Android 仕事用プロファイル デバイス上で Microsoft Intune を使用して、SSL または SMIME を有効にする、証明書またはユーザー名/パスワードを使用してユーザーを認証する、電子メールとスケジュールを同期することもできます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 136ccb6079b16c13098c1dbd6ca49e8254c14f89
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905769"
---
# <a name="email-profile-settings-for-devices-running-android-and-android-enterprise---intune"></a>Android と Android エンタープライズを実行しているデバイスの電子メール プロファイル設定 - Intune

電子メールのプロファイル設定を使用して、Android を実行するデバイスを構成します。

Intune 管理者は、次の Android デバイスに対して電子メール設定の作成と割り当てができます。

- Android Samsung Knox Standard
- Android エンタープライズ

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **[電子メール サーバー]**: Exchange サーバーのホスト名を入力します。
- **[アカウント名]**: 電子メール アカウントの表示名を入力します。 この名前は、ユーザーのデバイス上に表示されます。
- **[AAD からのユーザー名の属性]**: これは、Intune が Azure Active Directory (AAD) から取得する名前です。 Intune はこのプロファイルで使用されるユーザー名を動的に生成します。 次のようなオプションがあります。
  - **[ユーザー プリンシパル名]**: `user1` または `user1@contoso.com` などの名前を取得します。
  - **[ユーザー名]**: `user1` などの名前のみを取得します。
  - **[SAM アカウント名]**: `domain\user1` などのドメインを要求します。 SAM アカウント名は、Android デバイスにのみ使用できます。 Android エンタープライズはサポートされていません。

    次の項目も入力します。  
    - **[ユーザー ドメイン名のソース]**: **[AAD]** (Azure Active Directory) または **[カスタム]** を選択します。

      **[AAD]** から属性を取得する場合、次を入力します。
      - **[AAD からのユーザー ドメイン名属性]**: ユーザーの **[完全なドメイン名]** または **[NetBIOS 名]** 属性を取得する選択を行います。

      **[カスタム]** 属性を使用する選択を行っている場合、次を入力します。
      - **[使用するカスタム ドメイン名]**: Intune がドメイン名として使用する、`contoso.com` や `contoso` などの値を入力します。

- **[AAD からのメール アドレス属性]**: ユーザーの電子メール アドレスを生成する方法を選択します。 完全プリンシパル名を電子メール アドレスとして使用する場合は **[ユーザー プリンシパル名]** (`user1@contoso.com` または `user1`) を選択し、Exchange へのサインインにプライマリ SMTP アドレスを使用する場合は **[プライマリ SMTP アドレス]** (`user1@contoso.com`) を選択します。

- **[認証方法]** - 電子メール プロファイルで使用する認証方法として、**[ユーザー名とパスワード]** または **[証明書]** を選択します。
  - **[証明書]** を選択した場合は、Exchange 接続の認証のために事前に作成しておいたクライアント SCEP または PKCS 証明書プロファイルを選択します。

### <a name="security-settings"></a>セキュリティ設定

- **[SSL]**: 電子メールの送受信および Exchange サーバーとの通信に、SSL (Secure Sockets Layer) 通信を使用します。
- **[S/MIME]**: S/MIME 暗号化を使用して電子メールを送信します。
  - **[証明書]** を選択した場合は、Exchange 接続の認証のために事前に作成しておいたクライアント SCEP または PKCS 証明書プロファイルを選択します。

### <a name="synchronization-settings"></a>同期設定

- **[同期するメールの量]**: 同期する電子メールの日数を選択するか、利用可能なすべての電子メールを同期する場合は **[無制限]** を選択します。
- **[同期スケジュール]**: デバイスが Exchange サーバーからデータを同期するスケジュールを選択します。 **[メッセージの着信時]** を選択すると、電子メールの着信時にデータが同期されます。**[手動]** を選択した場合は、デバイスのユーザーが同期を開始する必要があります。

### <a name="content-sync-settings"></a>コンテンツ同期設定

- **[同期するコンテンツの種類]**: デバイスに同期するコンテンツの種類を選択します。
  - **連絡先**
  - **カレンダー**
  - **タスク**

## <a name="android-enterprise"></a>Android エンタープライズ

- **[メール アプリ]**: **[Gmail]** または **[Nine Work]** を選択します。
- **[電子メール サーバー]**: Exchange サーバーのホスト名。
- **[AAD からのユーザー名の属性]**: この名前は Active Directory (AD) または Azure AD の属性で、この電子メール プロファイルのユーザー名の生成に使用されます。 **プライマリ SMTP アドレス** (user1@contoso.com など) または**ユーザー プリンシパル名** (user1、user1@contoso.com など) を選択します。
- **[AAD からのメール アドレス属性]**: 各デバイスでユーザーの電子メール アドレスを生成する方法。 **[ユーザー プリンシパル名]**  を選択して電子メール アドレスとして完全プリンシパル名を使用するか、**[ユーザー名]** を選択します。
- **[認証方法]** - 電子メール プロファイルで使用する認証方法として、**[ユーザー名とパスワード]** または **[証明書]** を選択します。
  - **[証明書]** を選択した場合は、Exchange 接続の認証のために事前に作成しておいたクライアント SCEP または PKCS 証明書プロファイルを選択します。
- **[SSL]**: 電子メールの送受信および Exchange サーバーとの通信に、SSL (Secure Sockets Layer) 通信を使用します。
- **[同期するメールの量]**: 同期する電子メールの日数を選択するか、利用可能なすべての電子メールを同期する場合は **[無制限]** を選択します。
- **[同期するコンテンツの種類]** (Nine Work のみ): デバイスに同期するコンテンツの種類を選択します。
  - **連絡先**
  - **カレンダー**
  - **タスク**

## <a name="next-steps"></a>次の手順
[Intune で電子メールを設定する](email-settings-configure.md)
