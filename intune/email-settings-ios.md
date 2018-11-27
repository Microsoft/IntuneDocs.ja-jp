---
title: Microsoft Intune での iOS デバイスに対する電子メールの設定 - Azure | Microsoft Docs
description: Exchange サーバーを使用するデバイス構成電子メール プロファイルを作成し、Azure Active Directory から属性を取得します。 iOS デバイス上で Microsoft Intune を使用して、SSL を有効にする、証明書またはユーザー名/パスワードを使用してユーザーを認証する、電子メールを同期することもできます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b3aa3e7a4cd79ab990afe7f02a1d6960bc66494a
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180189"
---
# <a name="email-profile-settings-for-ios-devices---intune"></a>iOS デバイスの電子メール プロファイル設定 - Intune

電子メールのプロファイル設定を使用して、iOS を実行するデバイスを構成します。

> [!IMPORTANT]
> この記事で説明する S/MIME 機能を改善しています。 そのため、S/MIME 機能は一時的に Intune から除去されています。 この機能がリリースされたときに、この記述を削除します。

## <a name="email-settings"></a>電子メールの設定

- **[電子メール サーバー]**: Exchange サーバーのホスト名を入力します。
- **[アカウント名]**: 電子メール アカウントの表示名を入力します。 この名前は、ユーザーのデバイス上に表示されます。
- **[AAD からのユーザー名の属性]**: これは、Intune が Azure Active Directory (AAD) から取得する名前です。 Intune はこのプロファイルで使用されるユーザー名を動的に生成します。 次のようなオプションがあります。
  - **[ユーザー プリンシパル名]**: `user1` または `user1@contoso.com` などの名前を取得します。
  - **[プライマリ SMTP アドレス]**: `user1@contoso.com` のような書式で電子メール アドレスを取得します。
  - **[SAM アカウント名]**: `domain\user1` などのドメインを要求します。

    次の項目も入力します。  
    - **[ユーザー ドメイン名のソース]**: **[AAD]** (Azure Active Directory) または **[カスタム]** を選択します。

      **[AAD]** から属性を取得する場合、次を入力します。
      - **[AAD からのユーザー ドメイン名属性]**: ユーザーの **[完全なドメイン名]** または **[NetBIOS 名]** 属性を取得する選択を行います。

      **[カスタム]** 属性を使用する選択を行っている場合、次を入力します。
      - **[使用するカスタム ドメイン名]**: Intune がドメイン名として使用する、`contoso.com` や `contoso` などの値を入力します。

- **[AAD からのメール アドレス属性]**: ユーザーの電子メール アドレスを生成する方法を選択します。 メール アドレスとして完全なプリンシパル名を使用するには、**[ユーザー プリンシパル名]** (`user1@contoso.com` または `user1`) を選択します。 プライマリ SMTP アドレスを使用して Exchange にログオンするには、**[プライマリ SMTP アドレス]** (`user1@contoso.com`) を選択します。
- **[認証方法]** - 電子メール プロファイルで使用する認証方法として、**[ユーザー名とパスワード]** または **[証明書]** を選択します。 Azure Multi-Factor Authentication はサポートされていません。
  - **[証明書]** を選択した場合は、Exchange 接続の認証に使用するために事前に作成しておいたクライアント SCEP または PKCS 証明書プロファイルを選択します。
- **[SSL]**: **[有効]** を選択すると、電子メールの送受信および Exchange サーバーとの通信に、SSL (Secure Sockets Layer) 通信が使用されます。
- **[OAuth]**: **[有効]** を選択すると、メールの送受信および Exchange との通信に、Open Authorization (OAuth) 通信が使用されます。 OAuth サーバーで証明書認証が使用されている場合は、**[認証方法]** として **[証明書]** を選択し、プロファイルで証明書を含めます。 それ以外の場合は、**[認証方法]** として **[ユーザー名とパスワード]** を選択します。 OAuth を使用するときは、次のことを確認してください。

  - ユーザーに対してこのプロファイルを使用する前に、メール ソリューションで OAuth がサポートされていることを確認します。 Office 365 Exchange Online は OAuth をサポートしています。 オンプレミスの Exchange および他のパートナーやサード パーティのソリューションでは、OAuth がサポートされていない可能性があります。 オンプレミスの Exchange は、先進認証用に構成できます (ブログ投稿「[Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/)」(オンプレミス Exchange 用のハイブリッド先進認証の発表) を参照)。

    メール プロファイルで OAuth が使われていて、メール サービスではサポートされていない場合は、**[パスワードの確認入力]** オプションが破損しているように表示されます。 たとえば、Apple のデバイス設定でユーザーが **[パスワードの確認入力]** を選択しても、何も起こりません。

  - OAuth が有効になっていると、多要素認証 (MFA) をサポートする異なる "先進認証" メール サインイン エクスペリエンスが、エンド ユーザーに表示されます。 

  - 組織によっては、[セルフサービスのアプリケーション アクセス](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access)をエンド ユーザーが実行できないようにしている場合があります。 このシナリオでは、管理者が "iOS アカウント" エンタープライズ アプリを作成し、Azure AD でアプリへのアクセスをユーザーに許可するまで、先進認証のサインインが失敗する場合があります。

    既定のアクションは、**ビジネス承認なし**で[アプリケーション アクセス パネル](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction)の **[アプリの追加]** 機能を使用してアプリケーションを追加することです。 詳しくは、「[ユーザーをアプリケーションに割り当てる方法](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications)」をご覧ください。

  > [!NOTE]
  > OAuth を有効にすると、次のようになります。  
  > 1. 既に対象となっているデバイスに新しいプロファイルが発行されます。
  > 2. エンド ユーザーは再び資格情報の入力を求められます。

- **[S/MIME]**: **[S/MIME を有効にする]** を選択すると、S/MIME 署名を使用して送信メールが送信されます。 有効にすると、暗号化された電子メールを受信できる受信者への電子メールを暗号化し、送信者から受信した電子メールを復号化することもできます。
  - **[証明書]** を選択する場合は、Exchange 接続の認証や、メール交換の暗号化のために、既存の PKCS 証明書プロファイルを選択します。
- **[同期するメールの量]**: 同期する電子メールの日数を選択します。 または、利用可能なすべての電子メールを同期する場合は **[無制限]** を選択します。
- **[他の電子メール アカウントにメッセージを移動することを許可する]**: **[有効]** を選択すると、ユーザーがデバイスで構成した複数のアカウント間で、ユーザーがメール メッセージを移動することを許可します。
- **[サードパーティ アプリケーションからの電子メール送信を許可する]**: **[有効]** を選択すると、ユーザーがメール送信用の既定のアカウントとしてこのプロファイルを選択することを許可します。 サード パーティ製アプリケーションがネイティブ メール アプリでメールを開くことを許可します (メールへのファイルの添付など)。
- **[最近使用した電子メール アドレスを同期する]**: **[Unicode ]** を選択すると、ユーザーがデバイスで最近使用された電子メール アドレスのリストをサーバーと同期することを許可します。

## <a name="next-steps"></a>次の手順
[Intune で電子メールを設定する](email-settings-configure.md)
