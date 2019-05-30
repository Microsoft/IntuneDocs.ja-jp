---
title: Android の Microsoft Intune の電子メール設定 - Azure | Microsoft Docs
description: Exchange サーバーを使用するデバイス構成電子メール プロファイルを作成し、Azure Active Directory から属性を取得します。 Android Samsung Knox デバイス上で Microsoft Intune を使用して、SSL または SMIME を有効にする、証明書またはユーザー名/パスワードを使用してユーザーを認証する、および電子メールとスケジュールを同期することができます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 647e1cd6925df27d42186599ad6786e866742b44
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66042281"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Intune で電子メール、認証、および同期を構成するための Android デバイスの設定

この記事では、Android Samsung Knox デバイス上の Intune で制御できるさまざまな電子メール設定を一覧を示して説明します。 モバイル デバイス管理 (MDM) ソリューションの一部として、これらの設定を使って電子メール サーバーの構成や、SSL を使用した電子メールの暗号化などを行います。

Intune 管理者は、Android Samsung Knox Standard デバイスに対して電子メール設定を作成し、割り当てることができます。

Intune での電子メール プロファイルの詳細については、[電子メール設定の構成](email-settings-configure.md)に関するページを参照してください。

## <a name="before-you-begin"></a>始める前に

[デバイス構成プロファイルを作成します](email-settings-configure.md#create-a-device-profile)。

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **[電子メール サーバー]** : Exchange サーバーのホスト名を入力します。 たとえば、「`outlook.office365.com`」と入力します。
- **[アカウント名]** : 電子メール アカウントの表示名を入力します。 この名前は、ユーザーのデバイス上に表示されます。
- **[AAD からのユーザー名の属性]** : Intune が Azure Active Directory (Azure AD) から取得する名前。 Intune はこのプロファイルで使用されるユーザー名を動的に生成します。 次のようなオプションがあります。
  - **[ユーザー プリンシパル名]** : `user1` または `user1@contoso.com` などの名前を取得します。
  - **[ユーザー名]** : `user1` などの名前のみを取得します。
  - **[SAM アカウント名]** : `domain\user1` などのドメインを要求します。 SAM アカウント名は、Android デバイスにのみ使用されます。

    次の項目も入力します。  
    - **[ユーザー ドメイン名のソース]** : **[AAD]** (Azure Active Directory) または **[カスタム]** を選択します。

      **[AAD]** から属性を取得する場合、次を入力します。
      - **[AAD からのユーザー ドメイン名属性]** : ユーザーの **[完全なドメイン名]** または **[NetBIOS 名]** 属性を取得する選択を行います。

      **[カスタム]** 属性を使用する選択を行っている場合、次を入力します。
      - **[使用するカスタム ドメイン名]** : Intune がドメイン名として使用する、`contoso.com` や `contoso` などの値を入力します。

- **[AAD からのメール アドレス属性]** : この名前は、Intune が Azure AD から取得する電子メール属性です。 Intune では、このプロファイルに使用される電子メール アドレスが動的に生成されます。 次のようなオプションがあります。
  - **[ユーザー プリンシパル名]** : 電子メール アドレスとして完全プリンシパル名 (`user1@contoso.com`、`user1` など) を使用します。
  - **[プライマリ SMTP アドレス]** : プライマリ SMTP アドレス (`user1@contoso.com` など) を使用して Exchange にサインインします。

- **[認証方法]** - 電子メール プロファイルで使用する認証方法として、 **[ユーザー名とパスワード]** または **[証明書]** を選択します。
  - **[証明書]** を選択した場合は、Exchange 接続の認証のために事前に作成しておいたクライアント SCEP または PKCS 証明書プロファイルを選択します。

### <a name="security-settings"></a>セキュリティ設定

- **[SSL]** : 電子メールの送受信および Exchange サーバーとの通信に、SSL (Secure Sockets Layer) 通信を使用します。
- **[S/MIME]** : S/MIME 暗号化を使用して電子メールを送信します。
  - **[証明書]** を選択した場合は、Exchange 接続の認証のために事前に作成しておいたクライアント SCEP または PKCS 証明書プロファイルを選択します。

### <a name="synchronization-settings"></a>同期設定

- **[同期するメールの量]** : 同期する電子メールの日数を選択するか、利用可能なすべての電子メールを同期する場合は **[無制限]** を選択します。
- **[同期スケジュール]** : デバイスが Exchange サーバーからデータを同期するスケジュールを選択します。 **[メッセージの着信時]** を選択すると、電子メールの着信時にデータが同期されます。 **[手動]** を選択した場合は、デバイスのユーザーが同期を開始する必要があります。

### <a name="content-sync-settings"></a>コンテンツ同期設定

- **[同期するコンテンツの種類]** : デバイス上で同期するコンテンツの種類を選択します。 **[未構成]** の場合、この設定が無効になります。 **[未構成]** に設定すると、エンド ユーザーがデバイスで同期を有効にしても、デバイスと Intune が同期したとき、ポリシーが再適用され、再び無効になります。 

  次の内容を同期できます。  
  - **[連絡先]** : エンド ユーザーが自分のデバイスに連絡先を同期できるようにするには、 **[有効]** を選択します。
  - **[カレンダー]** : エンド ユーザーが自分のデバイスにカレンダーを同期できるようにするには、 **[有効]** を選択します。
  - **[タスク]** : エンド ユーザーが自分のデバイスにタスクを同期できるようにするには、 **[有効]** を選択します。

## <a name="next-steps"></a>次の手順

[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

また、[Android エンタープライズ - 仕事用プロファイル](email-settings-android-enterprise.md)、[iOS](email-settings-ios.md)、[Windows 10 以降](email-settings-windows-10.md)、および [Windows Phone 8.1](email-settings-windows-phone-8-1.md) 用の電子メール プロファイルを作成することもできます。
