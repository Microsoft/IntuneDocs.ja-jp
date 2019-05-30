---
title: Microsoft Intune での Android エンタープライズの電子メール設定 - Azure | Microsoft Docs
description: Exchange サーバーを使用するデバイス構成電子メール プロファイルを作成し、Azure Active Directory から属性を取得します。 Android 仕事用プロファイル デバイス上で Microsoft Intune を使用して、SSL または SMIME を有効にする、証明書またはユーザー名/パスワードを使用してユーザーを認証する、および電子メールとスケジュールを同期することができます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7e37d6a2b7371cf20cd36a6f3f75a4dd252c332f
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048039"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Intune を使用して電子メール、認証、および同期を構成するための Android エンタープライズ デバイスの設定

この記事では、Android エンタープライズ デバイスで制御できるさまざまな電子メール設定の一覧を示して説明します。 モバイル デバイス管理 (MDM) ソリューションの一部として、これらの設定を使って電子メール サーバーの構成や、SSL を使用した電子メールの暗号化などを行います。

Intune 管理者は、仕事用プロファイルに電子メール設定を作成し、Android エンタープライズ デバイスに割り当てることができます。

Intune での電子メール プロファイルの詳細については、[電子メール設定の構成](email-settings-configure.md)に関するページを参照してください。

## <a name="before-you-begin"></a>始める前に

[デバイス構成プロファイルを作成](email-settings-configure.md#create-a-device-profile)し、仕事用プロファイルを選択します。

## <a name="android-enterprise"></a>Android エンタープライズ

- **[メール アプリ]** : **[Gmail]** または **[Nine Work]** を選択します。
- **[電子メール サーバー]** : Exchange サーバーのホスト名。 たとえば、「`outlook.office365.com`」と入力します。
- **[AAD からのユーザー名の属性]** : Intune が Azure Active Directory (Azure AD) から取得する名前。 Intune はこのプロファイルで使用されるユーザー名を動的に生成します。 次のようなオプションがあります。

  - **[ユーザー プリンシパル名]** : `user1` または `user1@contoso.com` などの名前を取得します。
  - **[ユーザー名]** : `user1` などの名前のみを取得します。

- **[AAD からのメール アドレス属性]** : この名前は、Intune が Azure AD から取得する電子メール属性です。 Intune では、このプロファイルに使用される電子メール アドレスが動的に生成されます。 次のようなオプションがあります。
  - **[ユーザー プリンシパル名]** : 電子メール アドレスとして完全プリンシパル名 (`user1@contoso.com`、`user1` など) を使用します。
  - **[プライマリ SMTP アドレス]** : プライマリ SMTP アドレス (`user1@contoso.com` など) を使用して Exchange にサインインします。

- **[認証方法]** : 電子メール プロファイルで使用する認証方法として、 **[ユーザー名とパスワード]** または **[証明書]** を選択します。
  - **[証明書]** を選択した場合は、Exchange 接続の認証のために事前に作成しておいたクライアント SCEP または PKCS 証明書プロファイルを選択します。
- **[SSL]** : 電子メールの送受信および Exchange サーバーとの通信に、SSL (Secure Sockets Layer) 通信を使用するには、 **[有効]** を選択します。
- **[同期するメールの量]** : 同期する電子メールの日数を選択します。 または、利用可能なすべての電子メールを同期する場合は **[無制限]** を選択します。
- **[同期するコンテンツの種類]** (Nine Work のみ): デバイス上で同期するデータを選択します。 次のようなオプションがあります。
  - **[連絡先]** : エンド ユーザーが自分のデバイスに連絡先を同期できるようにするには、 **[有効]** を選択します。
  - **[カレンダー]** : エンド ユーザーが自分のデバイスにカレンダーを同期できるようにするには、 **[有効]** を選択します。
  - **[タスク]** : エンド ユーザーが自分のデバイスにタスクを同期できるようにするには、 **[有効]** を選択します。

## <a name="next-steps"></a>次の手順

[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

また、[Android Samsung Knox](email-settings-android.md)、[iOS](email-settings-ios.md)、[Windows 10 以降](email-settings-windows-10.md)、および [Windows Phone 8.1](email-settings-windows-phone-8-1.md) デバイス用の電子メール プロファイルを作成することもできます。
