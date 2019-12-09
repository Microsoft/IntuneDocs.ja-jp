---
title: Microsoft Intune で Outlook for iOS を使用して S/MIME を構成する
description: Microsoft Intune での Outlook for iOS を使用した S/MIME について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lance
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1b2f483415d050486ae9979899d9308154a9b131
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74411360"
---
# <a name="configure-smime-with-outlook-for-ios"></a>Outlook for iOS で S/MIME を構成する

Secure/Multipurpose Internet Mail Extensions (S/MIME) を使うと、Exchange ActiveSync (EAS) アカウントとの間で送受信されるメールにセキュリティ レイヤーが追加されます。 [Microsoft Outlook](https://aka.ms/omsmime) で S/MIME を利用すると、送信メッセージと添付ファイルの両方を暗号化することができ、Office 365 アカウントの使用時には、意図した受信者だけがメッセージの内容を読んだりアクセスしたりできるようにすることができます。 ユーザーはメッセージにデジタル署名することもでき、受信者は送信者の ID を確認すると共に、メッセージが改ざんされていないことを確認できます。 この機能は、証明書を利用することによって可能になります。 詳しくは、「[S/MIME について](https://docs.microsoft.com/previous-versions/tn-archive/aa995740(v=exchg.65)?redirectedfrom=MSDN)」をご覧ください。

> [!NOTE]
> このトピックでは、[Microsoft エンドポイント マネージャー](https://go.microsoft.com/fwlink/?linkid=2109431)を使って、信頼されたルート証明書を展開する方法について説明します。 Microsoft エンドポイント マネージャーは、すべてのエンドポイントを管理するための単一の統合エンドポイント管理プラットフォームです。 この Microsoft Endpoint Manager 管理センターでは、ConfigMgr と Microsoft Intune が統合されています。

## <a name="about-message-encryption"></a>メッセージの暗号化について
ユーザーは、暗号化証明書の公開部分を持っている、組織の内部と外部のユーザーに対し、暗号化されたメッセージを送信できます。 暗号化証明書に関連付けられている秘密キーは、暗号化されたメッセージの受信者によって常に、保護およびセキュリティ保護される必要があります。 受信者は、暗号化証明書の秘密キーを使って、メッセージの暗号化を解除します。

暗号化されたメッセージを読むことができるのは、メッセージの暗号化に使われた証明書に対応する証明書を持つ受信者だけです。 使用できる暗号化証明書を持っていない受信者に暗号化されたメッセージを送信しようとすると、メールを送信する前に、これらの受信者の削除を求めるメッセージが表示されます。

## <a name="about-digital-signatures"></a>デジタル署名について
メッセージにデジタル署名することで、メッセージが改ざんされていないこと、および送信者の ID が本物であることを保証して、受信者を安心させることができます。 受信者は、S/MIME をサポートするメール クライアントを使用している場合にのみ、デジタル署名を検証できます。

## <a name="prerequisites"></a>必要条件
- Outlook for iOS では、Office 365 アカウントの S/MIME のみがサポートされています。
- Office 365 用に S/MIME を構成する必要があります。 詳しくは、「[Office 365 で S/MIME を構成する方法](https://techcommunity.microsoft.com/t5/Exchange-Team-Blog/How-to-Configure-S-MIME-in-Office-365/ba-p/584516)」をご覧ください。
- 署名と暗号化に使用可能な証明書を発行できる証明機関が必要です。
- エンドポイント マネージャーを使用して、信頼されたルート証明書を展開します。 詳しくは、「[信頼された証明書プロファイルを作成する](~/protect/certificates-configure.md#create-trusted-certificate-profiles)」をご覧ください。
- 暗号化証明書をエンドポイント マネージャーにインポートする必要があります。 詳しくは、「[Intune でインポートした PKCS 証明書を構成して使用する](~/protect/certificates-imported-pfx-configure.md)」をご覧ください。
- Microsoft Intune 用の PFX コネクタをインストールして構成します。 詳しくは、「[PFX Certificate Connector for Microsoft Intune のダウンロード、インストール、および構成](~/protect/certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune)」をご覧ください。
- エンドポイント マネージャーから信頼されたルート証明書および S/MIME 証明書を自動的に受信するには、デバイスが MDM に登録されている必要があります。

> [!IMPORTANT]
> Outlook for iOS で S/MIME の暗号化証明書を使用するには、更新された Microsoft Intune 用 PFX コネクタ (バージョン 6.1911.11.0 以降) をダウンロードしてインストールする必要があります。

## <a name="smime-support-in-outlook-for-ios"></a>Outlook for iOS での S/MIME のサポート
Outlook for iOS では、証明書を使用した S/MIME 署名とメッセージの暗号化がサポートされています。 多くのお客様は、署名と暗号化の両方をサポートする 1 つの証明書ではなく、署名と暗号化に個別の証明書を使用しています。 一般に、署名証明書はユーザーの登録済みデバイスごとに固有ですが、暗号化証明書はユーザーの個々の登録済みデバイス間で共有されます。 多くの場合、ユーザーは長年にわたって S/MIME を使用しており、証明書が更新されるたびに異なる暗号化証明書を使用してきました。 過去の証明書のいずれかで暗号化されたメールを読めるよう、秘密キーを含む暗号化証明書の履歴がユーザーのデバイス上に存在している必要があります。 また、署名と暗号化をサポートする 1 つの証明書が存在する可能性もあります。

Outlook for iOS では、S/MIME に使用できるよう、2 つの方法でデバイスに証明書が提供されます。

- **ユーザー**は、自分宛に S/MIME 証明書をメールで送信し、モバイル デバイスの Outlook for iOS 内で添付ファイルから証明書をインストールできます。
- **管理者**は、暗号化証明書の履歴を任意の証明機関からエンドポイント マネージャーにインポートすることができます。 その後、エンドポイント マネージャーにより、ユーザーが登録したすべてのデバイスに証明書が自動的に配信されます。 一般に、署名証明書には Simple Certificate Enrollment Protocol (SCEP) が使用されます。 SCEP では、秘密キーが生成されて登録済みデバイスに保存され、ユーザーが登録した各デバイスに一意の証明書が配信されます。それを否認防止に使用できます。 管理者によってユーザーに対する暗号化証明書の履歴をインポートされたエンドポイント マネージャーでは、ユーザーが登録したすべてのデバイスに、ユーザーのすべての暗号化証明書が配信されます。 最後に、エンドポイント マネージャーでは、NIST 800-157 標準のサポートを必要とするお客様のために、派生した資格情報がサポートされます。 iOS では、Intune ポータル サイトを使用して、Intune から署名証明書と暗号化証明書が取得されます。

## <a name="configuring-outlook-for-ios-smime-in-endpoint-manager"></a>エンドポイント マネージャーでの Outlook for iOS の S/MIME の構成
Outlook for iOS で使用できる S/MIME 証明書の自動配信など、エンドポイント マネージャーで Outlook for iOS の S/MIME を構成するには、次の手順にのようにします。

### <a name="add-the-microsoft-outlook-app"></a>Microsoft Outlook アプリを追加する
1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. Microsoft Outlook for iOS をアプリ ストアからエンドポイント マネージャーに追加するか、Apple Volume Purchase Program から Outlook for iOS を同期します。 詳しくは、「[iOS ストア アプリを Microsoft Intune に追加する](~/apps/store-apps-ios.md)」または「[Apple Volume Purchase Program で購入した iOS アプリと macOS アプリを Microsoft Intune で管理する方法](~/apps/vpp-apps-ios.md)」をご覧ください。

### <a name="create-the-outlook-for-ios-smime-configuration-policy"></a>Outlook for iOS の S/MIME 構成ポリシーを作成する

次の手順のようにして、エンドポイント マネージャーで Outlook for iOS の S/MIME ポリシーを作成して構成できます。 これらの設定により、署名証明書と暗号化証明書が自動的に配信されます。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[アプリ]**  >  **[Apps configuration policies]\(アプリ構成ポリシー\)**  >  **[追加]** の順に選択します。<br>
**[構成ポリシーの追加]** ウィンドウが表示されます。
2. 構成ポリシーの **[名前]** と **[説明]** を入力します。
3. **[デバイス登録の種類]** として **[マネージド デバイス]** を選択します。
4. **[プラットフォーム]** として **[iOS/iPadOS]** を選択します。
5. **[必要なアプリの選択]** をクリックし、前に追加した Microsoft Outlook for iOS アプリを探して関連付けます。 
6. **[構成設定]** をクリックして、構成設定を追加します。 
    - **[構成設定の形式]** の隣にある **[構成デザイナーを使用する]** を選択し、既定の設定をそのまま使用します。 詳細については、「[Microsoft Outlook の構成設定](~/apps/app-configuration-policies-outlook.md)」を参照してください。
7. **[S/MIME]** をクリックして、 **[Outlook S/MIME の設定]** を表示します。

    ![Outlook for iOS の S/MIME の設定のスクリーンショット](./media/app-configuration-policies-outlook-smime/app-configuration-policies-outlook-smime-01.png)

8. **[S/MIME を有効にする]** を **[はい]** に設定します。
9. **[Intune から S/MIME 証明書を展開します]** を **[はい]** に設定します。
10. **[証明書プロファイルの種類]** の隣の **[署名証明書]** で、次のいずれかのオプションを選択します。
    - **[SCEP]** – Microsoft Outlook で署名に使用できる、デバイスとユーザーに対して一意の証明書が作成されます。 関連情報については、「[Intune を使用して SCEP をサポートするようにインフラストラクチャを構成する](~/protect/certificates-scep-configure.md)」および「[SCEP 証明書プロファイルを作成する](~/protect/certificates-profile-scep.md#create-a-scep-certificate-profile)」をご覧ください。 
    - **[PKCS のインポートされた証明書]** – ユーザーに対しては固有ですが、デバイス間では共有でき、ユーザーの代わりに管理者によってエンドポイント マネージャーにインポートされた証明書を使用します。 証明書は、ユーザーが登録したすべてのデバイスに配信されます。 エンドポイント マネージャーにより、署名をサポートするインポートされた証明書が自動的に選択されて、登録されたユーザーに対応するデバイスに配信されます。
    - **[派生資格情報]** – デバイス上に既に存在する、署名に使用できる証明書を使用します。 Intune の派生資格情報フローを使用して、デバイスで証明書を取得する必要があります。
11. **[証明書プロファイルの種類]** の隣の **[暗号化証明書]** で、次のいずれかのオプションを選択します。
    - **[PKCS のインポートされた証明書]** – 管理者によってエンドポイント マネージャーにインポートされた暗号化証明書を、ユーザーが登録したすべてのデバイスに配信します。任意のデバイスで証明書を配信します。エンドポイント マネージャーにより、暗号化をサポートするインポートされた証明書が自動的に選択されて、登録されたユーザーに対応するデバイスに配信されます。
    - **[派生資格情報]** – デバイス上に既に存在する、署名に使用できる証明書を使用します。 Intune の派生資格情報フローを使用して、デバイスで証明書を取得する必要があります。
12. **[エンドユーザー通知]** の隣で、 **[ポータル サイト]** または **[電子メール]** を選択して、Outlook for iOS 用の S/MIME 証明書を取得するようエンド ユーザーに通知します。

    iOS では、ユーザーはポータル サイトアプリを使って S/MIME 証明書を取得する必要があります。 エンドポイント マネージャーでは、ポータル サイトを起動し、ポータル サイトの [通知] セクション、プッシュ通知、または電子メールで S/MIME 証明書を取得する必要があることが、ユーザーに通知されます。 いずれかの通知をクリックすると、ユーザーはランディング ページに移動し、証明書の取得の進行状況が示されます。 証明書が取得されると、ユーザーは Microsoft Outlook for iOS 内から S/MIME を使用して、メールの署名と暗号化を行うことができます。
    
    エンド ユーザー通知には、次のオプションがあります。
       - **[ポータル サイト]** – オンにすると、ユーザーはデバイスでプッシュ通知を受け取り、そこから S/MIME 証明書が取得されるポータル サイトのランディング ページに移動します。
        - **[電子メール]** – ポータル サイトを起動して S/MIME 証明書を取得する必要があることを通知するメールを、エンド ユーザーに送信します。 ユーザーは、登録された iOS デバイスでメールのリンクをクリックすると、証明書を取得するためにポータル サイトにリダイレクトされます。
    
13. **[割り当て]** を選択して、アプリ構成ポリシーを Azure AD グループに割り当てます。 詳細については、「[Microsoft Intune を使用してアプリをグループに割り当てる方法](~/apps/apps-deploy.md)」を参照してください。

## <a name="next-steps"></a>次の手順

- 詳細については、「[Microsoft Intune 用アプリ構成ポリシー](app-configuration-policies-overview.md)」を参照してください。
