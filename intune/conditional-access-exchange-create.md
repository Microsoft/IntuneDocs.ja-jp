---
title: Exchange の条件付きアクセス ポリシーを作成する
titlesuffix: Microsoft Intune
description: Intune で Exchange On-Premises と従来の Exchange Online Dedicated の条件付きアクセスを構成します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d44b7483d65eeb7b2a39783fb113c444184db4f3
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48232224"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Exchange On-Premises と従来の Exchange Online Dedicated の条件付きアクセス ポリシーを作成する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事では、デバイスのポリシー準拠に基づいて、Exchange On-Premises の条件付きアクセスを構成する方法を示します。

Exchange Online Dedicated 環境を使用していて、それが新しい構成であるか既存の構成であるかを確認する必要がある場合は、アカウント マネージャーに問い合わせてください。 Exchange On-premises または従来の Exchange Online Dedicated 環境への電子メール アクセスを制御するには、Intune で Exchange On-premises の条件付きアクセスを構成します。

## <a name="before-you-begin"></a>始める前に

条件付きアクセスを構成する前に、次のことを確認します。

- Exchange のバージョンは、**Exchange 2010 SP1 以降**である必要があります。 Exchange Server クライアント アクセス サーバー (CAS) アレイがサポートされています。

- [Exchange Active Sync On-Premises Exchange Connector](exchange-connector-install.md) を使用する必要があります。これは、Intune を Exchange On-Premises に接続します。

    >[!IMPORTANT]
    >On-Premises Exchange Connector は、Intune テナントに固有であり、他のテナントでは使用できません。 Intune は、サブスクリプションあたり複数のオンプレミス Exchange コネクタに対応できるようになりました。 オンプレミス Exchange 組織が複数ある場合、Exchange 組織別にコネクタを設定できます。

- オンプレミス Exchange 組織のコネクタは、Exchange サーバーと通信できる任意のコンピューターにインストールできます。

- このコネクタは、**Exchange CAS 環境**をサポートします。 必要であれば、このコネクタを Exchange CAS サーバーに直接インストールすることは技術的に可能ですが、サーバーの負荷が増加するため、お勧めしません。 コネクタを構成するときには、Exchange CAS サーバーのいずれかと通信するように設定する必要があります。

- **Exchange ActiveSync** は、証明書ベースの認証またはユーザーの資格情報のエントリで構成する必要があります。

- 条件付きアクセス ポリシーを構成してユーザーに適用すると、ユーザーが電子メールに接続するには、使用する**デバイス**が以下の条件を満たさなくてはならなくなります。
    - Intune に**登録**されているか、ドメインに参加している PC である。
    - **Azure Active Directory に登録されている**。 また、クライアントの Exchange ActiveSync ID を Azure Active Directory に登録する必要があります。
<br></br>
- Azure AD Device Registration サービス (DRS) は、Intune や Office 365 のお客様に対して自動的にアクティブ化されます。 ADFS Device Registration Service を展開済みのお客様には、オンプレミスの Active Directory で登録されたデバイスは表示されません。 **これは、Windows PC と Windows Phone デバイスには適用されません。**

- そのデバイスに展開されているデバイス コンプライアンス ポリシーに**準拠**している。

- デバイスが条件付きアクセス設定を満たしていない場合、ユーザーのサインイン時に、次のいずれかのメッセージが表示されます。
    - デバイスが Intune に登録されていない、または Azure Active Directory に登録されていない場合は、ポータル サイト アプリのインストール、デバイスの登録、電子メールのアクティブ化の手順が示されたメッセージが表示されます。 また、このプロセスによって、デバイスの Exchange ActiveSync ID が Azure Active Directory のデバイス レコードに関連付けられます。
    - デバイスが準拠していない場合は、Intune のポータル サイト Web サイトまたはポータル サイト アプリにユーザーを誘導するメッセージが表示されます。このポータルで、ユーザーは問題とその解決方法に関する情報を確認できます。

### <a name="support-for-mobile-devices"></a>モバイル デバイスのサポート

- Windows Phone 8.1 以降
- iOS のネイティブ電子メール アプリ。
- Android 4 以降での EAS メール クライアント (Gmail など)。
- EAS メール クライアント **Android 仕事用プロファイル デバイス:** Android 仕事用プロファイル デバイスでは、**仕事用プロファイル**の **Gmail** と **Nine Work for Android Enterprise** のみがサポートされています。 条件付きアクセスが Android 仕事用プロファイルで動作するには、Gmail アプリまたは Nine Work for Android Enterprise アプリ用の電子メール プロファイルを展開する必要があります。また、必要なインストールとしてそのアプリを展開する必要があります。

> [!NOTE]
> Android と iOS の Microsoft Outlook アプリはサポートされていません。 

### <a name="support-for-pcs"></a>PC のサポート

Windows 8.1 以降用のネイティブ **メール** アプリケーション (Intune に登録されている場合)


## <a name="configure-exchange-on-premises-access"></a>Exchange On-premises アクセスの構成

1. [Azure Portal](https://portal.azure.com/) に移動し、Intune 資格情報でサインインします。

1. 正常にサインインすると、**Azure ダッシュボード**が開きます。

1. 左側のメニューから **[すべてのサービス]** を選択し、テキスト ボックス フィルターに「**Intune**」と入力します。

1. **[Intune]** を選ぶと、**Intune ダッシュボード**が表示されます。

1. **[オンプレミス アクセス]** を選択します。 **[オンプレミス アクセス]** ウィンドウには、条件付きアクセス ポリシーの状態と、その影響を受けるデバイスが表示されます。

1. **[管理]** で、**[Exchange On-Premises のアクセス]** を選択します。

1. **[Exchange On-premises のアクセス]** ウィンドウで **[はい]** を選択し、Exchange On-premises アクセス制御を有効にします。

    > [!NOTE]
    > Exchange Active Sync オンプレミス コネクタを構成していない場合、このオプションは無効です。  Exchange オンプレミスの条件付きアクセスを有効にするには、コネクタを少なくとも 1 つインストールして構成しておく必要があります。 詳細については、[Intune On-premises Exchange Connector のインストール](exchange-connector-install.md)に関するページを参照してください

1. **[割り当て]** で、**[組み込まれたグループ]** を選択します。  条件付きアクセスが適用されているセキュリティ ユーザー グループを使用します。 この操作では、ユーザーは自分のデバイスを Intune に登録し、コンプライアンス プロファイルに準拠する必要があります。

1. 特定のユーザー グループを除外するには、**[除外されたグループ]** を選択し、デバイスの登録とコンプライアンスから除外するユーザー グループを選択します。

1. **[設定]** で **[ユーザーへの通知]** を選択して、既定の電子メール メッセージを変更します。 このメッセージは、準拠していないデバイスでユーザーが Exchange On-premises にアクセスしようとしたときに送信されます。 メッセージ テンプレートでは、マークアップ言語が使用されます。  また、入力しながら、メッセージがどのように表示されるかをプレビュー表示できます。
    > [!TIP]
    > マークアップ言語の詳細については、Wikipedia の[こちらの記事](https://en.wikipedia.org/wiki/Markup_language)を参照してください。

1. 次の 2 つの手順に従って、**[Advanced Exchange Active Sync access settings] \(Exchange Active Sync アクセスの詳細設定\)** ウィンドウで、Intune で管理されていないデバイスからのアクセスに対して既定のグローバル ルールを設定するか、プラットフォームレベルのルールを設定します。

1. 条件付きアクセスまたは他のルールの影響を受けないデバイスについては、デバイスによる Exchange へのアクセスを許可するかブロックするかを選択できます。

   - アクセスを許可するように設定した場合、すべてのデバイスから Exchange On-premises にすぐにアクセスできます。  **[組み込まれたグループ]** のユーザーのデバイスについては、そのデバイスが後でコンプライアンス ポリシーに非準拠と評価されたり、Intune に登録されていなかったりするとブロックされます。
   - アクセスをブロックするように設定した場合、最初はすべてのデバイスから Exchange On-premises にすぐにアクセスできません。  **[組み込まれたグループ]** のユーザーに属するデバイスについては、そのデバイスが Intune に登録され、準拠と評価された場合にアクセスが許可されます。 Samsung KNOX Standard が実行されていない Android デバイスは、この設定をサポートしていないため常にブロックされます。

1. **[デバイス プラットフォームの例外]** で、**[追加]** を選択してプラットフォームを指定します。 **[管理対象外デバイス アクセス]** 設定が**ブロック済み**に設定されている場合は、ブロックに対してプラットフォーム例外があっても、登録済みの準拠デバイスは許可されます。 **[OK]** を選択して、設定を保存します。

1. **[On-premises]** ウィンドウで **[保存]** をクリックして、条件付きアクセス ポリシーを保存します。

## <a name="create-azure-ad-conditional-access-policies-in-intune"></a>Intune で Azure AD の条件付きアクセス ポリシーを作成する

Intune 1704 リリース以降では、管理者は Intune Azure Portal から Azure AD の条件付きアクセス ポリシーを作成できるため、Azure と Intune のワークロードを切り替える必要はありません。

> [!IMPORTANT]
> Intune Azure Portal から Azure AD の条件付きアクセス ポリシーを作成するには、Azure AD Premium ライセンスが必要です。

### <a name="to-create-azure-ad-conditional-access-policy"></a>Azure AD 条件付きアクセス ポリシーを作成するには

1. **Intune ダッシュボード**で、**[条件付きアクセス]** を選びます。

2. **[ポリシー]** ウィンドウで、**[新しいポリシー]** を選択し、新しい Azure AD 条件付きアクセス ポリシーを作成します。

## <a name="see-also"></a>関連項目

[Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
