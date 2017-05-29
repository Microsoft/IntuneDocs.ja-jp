---
title: "Exchange On-premises への電子メールを保護する | Microsoft Docs"
description: "条件付きアクセスで Exchange On-premises の会社電子メールへのアクセスを保護および制御します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a55071f5-101e-4829-908d-07d3414011fc
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3098a301550413a982d3ce9664646f7dfc0b1d1f
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="protect-email-access-to-exchange-on-premises-and-legacy-exchange-online-dedicated-with-intune"></a>Intune で Exchange On-premises と従来の Exchange Online Dedicated への電子メール アクセスを保護する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune を使用して、Exchange On-premises または従来の Exchange Online Dedicated への電子メール アクセスを制御するように条件付きアクセスを構成することができます。
条件付きアクセスの動作の詳細については、「[電子メールと O365 サービスへのアクセスを保護する](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)」をご覧ください。

> [!NOTE]
> Exchange Online Dedicated 環境を使用していて、それが新しい構成であるか既存の構成であるかを確認する必要がある場合は、アカウント マネージャーに問い合わせてください。

## <a name="before-you-begin"></a>始める前に

以下のことを確認します。

-   Exchange のバージョンは、**Exchange 2010 以降**である必要があります。 Exchange Server クライアント アクセス サーバー (CAS) アレイがサポートされています。

-   Intune を Exchange On-premises に接続するために、[Intune On-Premises Exchange Connector](intune-on-premises-exchange-connector.md) を使用する必要があります。 これにより、Intune コンソールでデバイスを管理できます。

    -   Intune コンソールで利用可能な On-Premises Exchange Connector は、Intune テナントに固有であり、他のテナントでは使用できません。 また、テナントの Exchange Connector は **1 台のコンピューターにのみ**インストールすることが推奨されます。

        コネクタは Intune 管理コンソールからダウンロードできます。 On-Premises Exchange Connector の構成方法に関するチュートリアルについては、[オンプレミスまたはホスト型 Exchange に対する On-Premises Exchange Connector の構成](intune-on-premises-exchange-connector.md)に関するページをご覧ください。

    -   このコネクタは、Exchange サーバーと通信できるあらゆるコンピューターにインストールできます。

    -   このコネクタは、**Exchange CAS 環境**をサポートします。 Exchange CAS サーバーにコネクタを直接インストールすることも技術的には可能です。 ただし、サーバーの負荷が増えるため、推奨されません。 コネクタを構成するときには、Exchange CAS サーバーのいずれかと通信するように設定する必要があります。

-   **Exchange ActiveSync** は、証明書ベースの認証またはユーザーの資格情報のエントリで構成する必要があります。

### <a name="device-compliance-requirements"></a>デバイス コンプライアンスの要件

条件付きアクセス ポリシーを構成してユーザーに適用すると、ユーザーが電子メールに接続するには、使用する**デバイス**が以下の条件を満たさなくてはならなくなります。

-  ドメインに参加している PC であるか、Intune に**登録**されている。

-  **Azure Active Directory に登録されている**。 また、クライアントの Exchange ActiveSync ID を Azure Active Directory に登録する必要があります。

  Azure Active Directory Device Registration サービスは、Intune や Office 365 のお客様に対して自動的にアクティブ化されます。 ADFS Device Registration Service をデプロイ済みのお客様には、オンプレミスの Active Directory で登録されたデバイスは表示されません。 **これは、Windows PC と Windows Phone デバイスには適用されません。**

-   そのデバイスに展開されているすべての Intune コンプライアンス ポリシーに**準拠**している。

### <a name="how-conditional-access-works-with-exchange-on-premises"></a>Exchange On-Premises での条件付きアクセスのしくみ

次の図は、Exchange On-premises の条件付きアクセス ポリシーでデバイスを許可するかブロックするかを評価するフローを示しています。

![デバイスに Exchange On-premises へのアクセスを許可するかブロックするかを判断する決定ポイントを示す図](../media/ConditionalAccess8-2.png)

条件付きアクセス ポリシーが満たされない場合は、デバイスがブロックされてから 10 分経過すると、ユーザーはサインイン時に次のいずれかの検疫メッセージを受け取ります。

- デバイスが Intune に登録されていない、または Azure Active Directory に登録されていない場合は、メッセージが表示され、ポータル サイト アプリのインストール、デバイスの登録、および電子メールのアクティブ化の手順が示されます。 また、このプロセスによって、デバイスの Exchange ActiveSync ID が Azure Active Directory のデバイス レコードに関連付けられます。

-   デバイスが準拠していない場合は、Intune のポータル サイト Web サイトまたはポータル サイト アプリにユーザーを誘導するメッセージが表示されます。このポータルで、ユーザーは問題とその解決方法に関する情報を確認できます。

## <a name="support-for-mobile-devices"></a>モバイル デバイスのサポート
次のものがサポートされています。
-   Windows Phone 8.1 以降。

-   iOS のネイティブ電子メール アプリ。

-   Android 4 以降での Exchange ActiveSync メール クライアント (Gmail など)。
-   Exchange ActiveSync メール クライアント **Android for Work デバイス:** Android for Work デバイスでは、**仕事用プロファイル**の **Gmail** アプリと **Nine Work** アプリのみがサポートされています。 条件付きアクセスが Android for Work で動作するには、Gmail アプリまたは Nine Work アプリ用の電子メール プロファイルを展開する必要があります。また、必要なインストールとしてそのアプリを展開する必要があります。 

> [!NOTE]
> Android と iOS の Microsoft Outlook アプリはサポートされていません。

## <a name="support-for-pcs"></a>PC のサポート
次がサポートされています。
-   Windows 8.1 以降用の**メール** アプリケーション (PC が Intune に登録されている場合)。

##  <a name="configure-a-conditional-access-policy"></a>条件付きアクセス ポリシーの構成

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** > **[条件付きアクセス]** > **[Exchange On-premises ポリシー]** の順にクリックします。
![IntuneSA5aSelectExchOnPremPolicy](../media/IntuneSA5aSelectExchOnPremPolicy.png)

2.  必要な設定でポリシーを構成します。![Exchange On-premises ポリシー ページのスクリーンショット](../media/IntuneSA5bExchangeOnPremPolicy.png)

  - **[デバイスが Microsoft Intune に準拠していない場合や、登録されていない場合に、電子メール アプリから Exchange Online へのアクセスをブロックします]:** このオプションを選択すると、Intune で管理されていないデバイスまたはコンプライアンス ポリシーに準拠していないデバイスは、Exchange サービスへのアクセスがブロックされます。

  - **[既定のルールを無視 - 登録された準拠デバイスが常に Exchange にアクセスできるようにする]:** このオプションをオンにすると、Intune に登録され、コンプライアンス ポリシーに準拠しているデバイスは Exchange へのアクセスが許可されます。
  このルールは**既定のルール**に優先します。つまり、アクセスを検疫またはブロックする**既定のルール**を設定した場合でも、登録された準拠デバイスは引き続き Exchange にアクセスできます。

  - **[対象グループ]:** Exchange にアクセスするにはデバイスを Intune に登録する必要がある Intune ユーザー グループを選択します。

  - **[例外グループ]:** 条件付きアクセス ポリシーから除外される Intune ユーザー グループを選択します。 この一覧に指定されたユーザーは、同時に **[対象グループ]** の一覧に指定されている場合でも除外されます。

  - **[プラットフォーム例外]:** **[ルールの追加]** を選択して、指定したモバイル デバイスのファミリとモデルのアクセス レベルを定義するルールを構成します。 任意の種類のデバイスを使用できるので、Intune でサポートされていないデバイスの種類を構成することもできます。

  - **[既定のルール]:** 他のどのルールにも含まれていないデバイスの場合、Exchange へのアクセスの許可、Exchange へのアクセスのブロック、検疫のいずれかを選択できます。 登録された準拠デバイスに対してアクセスを許可するルールを設定すると、iOS、Windows、および Samsung KNOX のデバイスには電子メールへのアクセス権が自動的に付与されます。 ユーザーは自分の電子メールを取得するために何もプロセスを実行する必要はありません。
      - Samsung KNOX を実行していない Android デバイスの場合、ユーザーには、電子メールにアクセスする前に、登録とコンプライアンスの確認方法に関するチュートリアルを含む検疫電子メールが送信されます。 アクセスをブロックするか、デバイスを検疫するルールを設定すると、Intune に登録済みであるかどうかに関係なく、すべてのデバイスが Exchange にアクセスできなくなります。 登録および準拠デバイスがこのルールに影響されるのを防ぐためには、**[既定ルールの上書き]** ボックスをオンにします。
>[!TIP]
>電子メールへのアクセスを許可する前にすべてのデバイスをブロックする場合は、アクセスのブロック ルールまたは検疫ルールを選択します。 既定のルールはすべてのデバイスの種類に適用されるので、プラットフォームの例外として構成されているデバイスの種類や Intune でサポートされていないデバイスの種類も影響を受けます。

  - **[ユーザー通知]:** Exchange から送信される通知電子メールの他に、デバイスのブロック解除の手順が記載された電子メールが Intune によって送信されます。 この既定のメッセージは、ニーズに合わせてカスタマイズすることができます。 修復手順が記載されている Intune 通知電子メールが届く前にユーザーのデバイスがブロックされた場合 (このメールはユーザーの Exchange 受信トレイに送信されます)、ブロックされていないデバイスや、Exchange にアクセスする別の方法を使用して、メッセージを表示できます。
      - これは特に**既定のルール**がブロックまたは検疫に設定されている場合に当てはまります。 この場合、ユーザーはアプリ ストアに移動し、Microsoft ポータル サイト アプリをダウンロードして、デバイスを登録する必要があります。 これは iOS、Windows、および Samsung KNOX デバイスに適用されます。 Samsung KNOX を実行していないデバイスの場合は、代替の電子メール アカウントに検疫電子メールを送信する必要があります。 ユーザーはブロックされたデバイスにこの電子メールをコピーして、登録とコンプライアンス プロセスを完了する必要があります。
  > [!NOTE]
  > Exchange が通知電子メールを送信できるようにするには、通知電子メールの送信に使用されるアカウントを指定する必要があります。
  >
  > 詳細については、[オンプレミスまたはホスト型 Exchange に対する Exchange On-Premises Connector の構成](intune-on-premises-exchange-connector.md)に関するページをご覧ください。

3.  終了したら、**[保存]** を選択します。

-   条件付きアクセス ポリシーを展開する必要はありません。直ちに有効になります。

-   ユーザーが Exchange ActiveSync のプロファイルを設定してからデバイスがブロックされるまでに、1 ～ 3 時間かかる場合があります (Intune で管理されていない場合)。

-   ブロックされたユーザーがデバイスを Intune に登録し、非準拠の問題を修正すると、メールのアクセスは 2 分以内でブロック解除されます。

-   ユーザーが Intune から登録解除した場合、デバイスがブロックされるまでに 1 ～ 3 時間かかる場合があります。

**デバイスのアクセスを保護する条件付きアクセス ポリシーの構成方法を示したシナリオの例[を見るには、](restrict-email-access-example-scenarios.md)電子メール アクセスの保護のシナリオ例**をご覧ください。

## <a name="next-steps"></a>次のステップ
-   [SharePoint Online へのアクセスを保護する](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

-   [Skype for Business Online へのアクセスを保護する](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)

