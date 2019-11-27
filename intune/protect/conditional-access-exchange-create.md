---
title: Exchange の条件付きアクセス ポリシーを作成する
titleSuffix: Microsoft Intune
description: Intune で Exchange On-Premises と従来の Exchange Online Dedicated の条件付きアクセスを構成します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 644297777e8a103d6ffdc5f025ebf8f29591fda8
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188467"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Exchange On-Premises と従来の Exchange Online Dedicated の条件付きアクセス ポリシーを作成する

この記事では、デバイスのコンプライアンスに基づく Exchange On-Premises の条件付きアクセスを構成する方法を示します。

Exchange Online Dedicated 環境を使用していて、それが新しい構成であるか既存の構成であるかを確認する必要がある場合は、アカウント マネージャーに問い合わせてください。 Exchange On-Premises または従来の Exchange Online Dedicated 環境への電子メール アクセスを制御するには、Intune で Exchange On-Premises に対する条件付きアクセスを構成します。

## <a name="before-you-begin"></a>始める前に

条件付きアクセスを構成する前に、次の構成が存在することを確認します。

- Exchange のバージョンが **Exchange 2010 SP1 以降**であること。 Exchange Server クライアント アクセス サーバー (CAS) アレイがサポートされています。

- [Exchange Active Sync On-Premises Exchange Connector](exchange-connector-install.md) をインストールして使用していること。これにより、Intune が Exchange On-Premises に接続されます。

    >[!IMPORTANT]  
    >Intune は、サブスクリプションあたり複数のオンプレミス Exchange コネクタに対応できます。  ただし、それぞれのオンプレミスの Exchange コネクタは、単一の Intune テナントに固有であり、他のテナントでは使用できません。  オンプレミス Exchange 組織が複数ある場合、Exchange 組織別にコネクタを設定できます。

- オンプレミス Exchange 組織用のコネクタは、Exchange サーバーと通信できる任意のコンピューターにインストールできます。

- このコネクタは、**Exchange CAS 環境**をサポートします。 Intune では、Exchange CAS サーバーにコネクタを直接インストールすることがサポートされています。 これは別のコンピューターにインストールすることをお勧めします。そのコネクタによって、サーバーにさらなる負荷が追加されるためです。 コネクタを構成するときには、Exchange CAS サーバーのいずれかと通信するように設定する必要があります。

- **Exchange ActiveSync** は、証明書ベースの認証またはユーザーの資格情報のエントリで構成する必要があります。

- 条件付きアクセス ポリシーを構成してユーザーに適用すると、ユーザーが電子メールに接続するには、使用している**デバイス**が以下の条件を満たしている必要があります。
  - Intune に**登録**されているか、ドメインに参加している PC である。
  - **Azure Active Directory に登録されている**。 また、クライアントの Exchange ActiveSync ID を Azure Active Directory に登録する必要があります。

- Azure AD Device Registration サービス (DRS) は、Intune や Office 365 のお客様に対して自動的にアクティブ化されます。 ADFS Device Registration Service をデプロイ済みのお客様には、オンプレミスの Active Directory に登録されたデバイスは表示されません。 **これは、Windows PC と Windows Phone デバイスには適用されません。**

- そのデバイスに展開されているデバイス コンプライアンス ポリシーに**準拠**している。

- デバイスが条件付きアクセス設定を満たしていない場合、ユーザーのサインイン時に、次のいずれかのメッセージが表示されます。
  - デバイスが Intune に登録されていない、または Azure Active Directory に登録されていない場合はメッセージが表示され、ポータル サイト アプリのインストール、デバイスの登録、および電子メールのアクティブ化の手順が示されます。 また、このプロセスによって、デバイスの Exchange ActiveSync ID が Azure Active Directory のデバイス レコードに関連付けられます。
  - デバイスが準拠していない場合は、ユーザーを Intune ポータル サイト Web サイトまたはポータル サイト アプリに誘導するメッセージが表示されます。 会社のポータルから、問題とその修復方法に関する情報を確認することができます。

### <a name="support-for-mobile-devices"></a>モバイル デバイスのサポート

- Windows Phone 8.1 以降
- iOS のネイティブ電子メール アプリ。
- Android 4 以降での EAS メール クライアント (Gmail など)。
- EAS メール クライアント **Android 仕事用プロファイル デバイス:** Android 仕事用プロファイル デバイスでは、**仕事用プロファイル**の **Gmail** と **Nine Work for Android Enterprise** のみがサポートされています。 Android 仕事用プロファイルで条件付きアクセスを機能させるには、Gmail アプリまたは Nine Work for Android Enterprise アプリ用の電子メール プロファイルを配置する必要があります。また、これらのアプリを必要なインストールとしてデプロイする必要があります。

> [!NOTE]
> Exchange のオンプレミス コネクタを介した Android および iOS 用 Microsoft Outlook の使用はサポートされていません。 オンプレミスのメールボックスに対して iOS および Android 用 Outlook と共に Azure Active Directory の条件付きアクセス ポリシーおよび Intune アプリ保護ポリシーを活用したい場合は、[iOS および Android 用 Outlook でのハイブリッド先進認証の使用](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)に関するページをご覧ください。

### <a name="support-for-pcs"></a>PC のサポート

Windows 8.1 以降用のネイティブ **メール** アプリケーション (Intune で MDM に登録される場合)

## <a name="configure-exchange-on-premises-access"></a>Exchange On-premises アクセスの構成

次の手順を使用して Exchange On-Premises アクセス制御を設定する前に、Exchange On-Premises 用の [Intune On-Premises Exchange コネクタ](exchange-connector-install.md)を少なくとも 1 つインストールして構成しておく必要があります。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[テナント管理]**  >  **[Exchange へのアクセス]** に移動し、 **[Exchange On-Premises のアクセス]** を選択します。

3. **[Exchange On-Premises のアクセス]** ウィンドウで **[はい]** を選択し、*Exchange On-Premises のアクセス制御を有効にします*。

4. **[割り当て]** で **[含めるグループを選択]** を選択し、アクセスを構成する 1 つまたは複数のグループを選択します。

   選択したグループのメンバーに、Exchange On-Premises アクセスの条件付きアクセス ポリシーが適用されます。 このポリシーを受け取ったユーザーは、Exchange On-Premises にアクセスする前に、Intune にデバイスを登録し、コンプライアンス プロファイルに準拠しておく必要があります。

5. グループを除外するには、 **[含めないグループを選択]** を選択し、Exchange On-Premises にアクセスする前にデバイスを登録してコンプライアンス プロファイルに準拠しておくという要件から除外する 1 つまたは複数のグループを選択します。 

6. 次に、Intune On-Premises Exchange コネクタの設定を構成します。  *[Exchange On-Premises のアクセス]* ウィンドウの **[設定]** で、 **[Exchange ActiveSync のオンプレミス コネクタ]** を選択した後、構成する Exchange 組織用のコネクタを選択します。

7. **[設定]** で **[ユーザーへの通知]** を選択し、準拠していないデバイスで Exchange On-Premises にアクセスしようとしているユーザーに送信される既定の電子メール メッセージを変更します。 メッセージ テンプレートでは、マークアップ言語が使用されます。  また、入力しながら、メッセージがどのように表示されるかをプレビュー表示できます。
   > [!TIP]
   > マークアップ言語の詳細については、Wikipedia の[こちらの記事](https://en.wikipedia.org/wiki/Markup_language)を参照してください。
 
   **[OK]** を選択して編集を保存し、Exchange On-Premises アクセスの構成を完了します。

8. 次に、 **[Exchange Active Sync アクセスの詳細設定]** を選択して *[Exchange ActiveSync アクセスの詳細設定]* ウィンドウを開き、デバイス アクセス ルールを構成します。  

   - **[アンマネージド デバイス アクセス]** では、条件付きアクセスやその他のルールの影響を受けないデバイスからのアクセスに対するグローバルな既定のルールを設定します。

     - **[アクセスを許可]** - すべてのデバイスから Exchange On-Premises にすぐにアクセスできます。 前の手順で含まれるように構成したグループのユーザーのデバイスについては、そのデバイスが後でコンプライアンス ポリシーに非準拠と評価されたり、Intune に登録されていなかったりするとブロックされます。

     - **[アクセスのブロック]** および **[検査]** - 最初はすべてのデバイスが Exchange On-Premises へのアクセスをすぐにブロックされます。 前の手順で含まれるように構成されたグループのユーザーのデバイスについては、デバイスが Intune に登録され、準拠として評価された後でアクセスできるようになります。 

       Samsung KNOX Standard が実行されて "*いない*" Android デバイスは、この設定がサポートされていないため、常にブロックされます。

   -  **[デバイス プラットフォームの例外]** では、 **[追加]** を選択し、環境の必要に応じてプラットフォームの詳細を指定します。 
   
      **[アンマネージド デバイス アクセス]** 設定が **[ブロック済み]** に設定されている場合は、それらをブロックするプラットフォーム例外があっても、登録済みの準拠デバイスは許可されます。  
   
   **[OK]** を選択して編集を保存します。

9. **[保存]** を選択して、Exchange の条件付きアクセス ポリシーを保存します。

次に、コンプライアンス ポリシーを作成し、それを Intune のユーザーに割り当てて、ユーザーのモバイル デバイスを評価します。[デバイス コンプライアンスの概要](device-compliance-get-started.md)に関する記事を参照してください。

## <a name="next-steps"></a>次の手順

[Microsoft Intune での Intune オンプレミス Exchange コネクタのトラブルシューティング](https://support.microsoft.com/help/4471887)
