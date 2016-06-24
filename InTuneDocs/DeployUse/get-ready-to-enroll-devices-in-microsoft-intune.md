---
# required metadata

title: デバイスを登録する準備 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune にデバイスを登録する準備
従業員が Intune にモバイル デバイス ([Android](set-up-android-management-with-microsoft-intune.md)、[iOS、Mac](set-up-ios-and-mac-management-with-microsoft-intune.md)、[Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)、[Windows PC](set-up-windows-device-management-with-microsoft-intune.md) など) を登録できるようにするには、デバイスの登録を有効にする必要があります。 登録を許可するには、モバイル デバイス管理機関を設定し、Intune ポータル サイトを構成し、ライセンスを割り当て、デバイス プラットフォームの登録を有効にする必要があります。

## <a name="BKMK_Set_MDM_Authority"></a>モバイル デバイス管理機関を設定する
MDM 機関では、一連のデバイスを管理するためのアクセス許可を持つ管理サービスを定義します。 MDM 機関のオプションには、Intune 単体で使用するか、Intune を Configuration Manager と連携させて使用する方法があります。 Configuration Manager を管理機関として設定した場合、モバイル デバイス管理のために使用できるサービスは他にありません。

>[!IMPORTANT]
> モバイル デバイスの管理に Intune のみ (オンライン サービス) を使用するか、System Center Configuration Manager と Intune との統合 (オンプレミス ソフトウェア ソリューションをオンライン サービスと組み合わせて使用) を使用するのかについて、慎重に検討します。 モバイル デバイス管理機関は、設定したら変更できません。



1.  [Microsoft Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** の順に選択します。

2.  **[タスク]** リストで **[モバイル デバイス管理機関の設定]**をクリックします。 **[MDM 機関の設定]** ダイアログ ボックスが開きます。

    ![[MDM 機関の設定] ダイアログ ボックス](../media/intune-mdm-authority.png)

3.  Intune によって、Intune を MDM 機関にすることを確認するよう求められます。 チェック ボックスをオンにしてから、**[はい]** を選択し、Microsoft Intune を使用してモバイル デバイスを管理します。

## Intune ポータル サイトを構成する
ポータル サイトをカスタマイズすることで、エンド ユーザーの利便性を向上させることができます。 これを行うには、テナント管理者またはサービス管理者として [Microsoft Intune 管理コンソール](https://manage.microsoft.com)にログインし、**[管理者]** &gt; **[ポータル サイト]** の順にクリックして、ポータル サイトの設定を構成します。

![admin-console-admin-workspace-comp-portal-settings](../media/cp_setup.png)

#### 会社の連絡先情報とプライバシーに関する声明
会社名は、ポータル サイトのタイトルとして表示されます。 連絡先情報と詳細は、ポータル サイトの [IT に連絡] 画面でユーザーに対して表示されます。 プライバシーに関する声明は、ユーザーがプライバシー リンクをクリックすると表示されます。

|フィールド名|最大長|詳細情報|
    |----------|------------------------|----------------|
    |会社名|40|ポータル サイトのタイトルとして表示される名前です。|
    |IT 部門の担当者名|40|**[IT に連絡]** ページに表示される名前です。|
    |IT 部門の電話番号|20|**[IT に連絡]** ページに表示される連絡先の電話番号です。|
    |IT 部門の電子メール アドレス|40|**[IT に連絡]** ページに表示される連絡先の電子メール アドレスです。 **alias@domainname.com** の形式で有効な電子メール アドレスを入力する必要があります。|
    |追加情報|120|**[IT に連絡]** ページに表示されます。|
    |会社のプライバシーに関する声明の URL|79|ポータル サイトでユーザーがプライバシー リンクをクリックすると表示される、各社のプライバシーに関する声明を指定できます。 https://www.contoso.com の形式で URL を入力します。|

#### サポートの連絡先
サポート Web サイトは、ポータル サイトに表示されます。ユーザーは、サポート サイトからオンライン サポートを利用できます。

|フィールド名|最大長|詳細情報|
    |----------|------------------------|----------------|
    |サポート Web サイトの URL|150|ユーザーが使用するサポート Web サイトがある場合、その URL を指定します。 URL は、https://www.contoso.com という形式にする必要があります。 URL を指定しない場合、ポータル サイトの **[IT に連絡]** ページのサポート Web サイトには何も表示されません。|
    |Web サイト名|40|サポート Web サイトの URL に表示されるフレンドリ名です。 サポート Web サイトの URL を指定し、フレンドリ名を指定しない場合、ポータル サイトの **[IT に連絡]** ページに **[IT Web サイトに移動する]** が表示されます。|

## 会社のブランドのカスタマイズ
ポータル サイトのロゴや会社名、テーマの色や背景をカスタマイズできます。

|フィールド名|詳細情報|
    |----------|----------------|
    |テーマの色|ポータル サイトに適用するテーマの色を選択します。|
    |会社のロゴを含める|このオプションを有効にすると、ポータル サイトに表示する会社のロゴをアップロードできます。 2 つのロゴをアップロードできます。1 つは、ポータル サイトの背景が白の場合に表示するロゴ、もう 1 つは、選択したテーマの色がポータル サイトの背景に使用されている場合に表示するロゴです。 各ロゴは、.png または .jpg ファイルの種類にし、最大解像度が 400 x 100 ピクセルで、750 KB 以下のサイズにします。|
    |[!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)] ポータル サイト アプリ用の背景を選択する|この設定は、[!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)] ポータル サイト アプリの背景のみに適用されます。|


変更を保存した後で、管理コンソールの **[ポータル サイト]** ページの下部に表示されるリンクを使用して、ポータル サイト Web サイトを表示できます。 これらのリンクは変更できません。 ユーザーがサインインするときに、これらのリンクでポータル サイトが表示されます。



## Intune のユーザー ライセンスを割り当てる

**[!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)]**を使用して、手動でクラウドベースのユーザーを追加し、クラウドベースのユーザー アカウントと、オンプレミスの Active Directory から Azure AD に同期されているアカウントの両方にライセンスを割り当てます。

1.  テナント管理者の資格情報を使用して、[Intune アカウント ポータル](https://portal.office.com/Admin/Default.aspx)にサインインします。

2.  Intune のユーザー ライセンスを割り当てるユーザー アカウントを選択し、そのユーザー アカウントのプロパティの **[Microsoft Intune]** チェック ボックスをオンにします。

3.  これで、ユーザー アカウントが Microsoft Intune ユーザー グループに追加され、サービスを使用し、デバイスを管理対象に登録する権限がユーザーに付与されます。

## デバイス管理のセットアップ
MDM 機関を設定したら、組織がサポートするオペレーティング システムにデバイス管理をセットアップする必要があります。 デバイス管理のセットアップに必要な手順は、オペレーティング システムによって異なります。 たとえば、Android OS では、Intune 管理コンソールで必要になる操作はありません。 これに対して、Windows および iOS では管理を許可するため、デバイスと Intune との間に信頼関係が必要です。

> [!div class="op_single_selector"]
- [Microsoft Intune を使用して Android の管理をセットアップする](set-up-android-management-with-microsoft-intune.md)
- [Set up iOS and Mac management with Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Microsoft Intune を使用して Windows Phone の管理をセットアップする](set-up-windows-phone-management-with-microsoft-intune.md)
- [Microsoft Intune を使用して Windows デバイスの管理をセットアップする](set-up-windows-device-management-with-microsoft-intune.md)

次も実行できます。
 - [デバイス登録マネージャー アカウント](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)を使用して多数のデバイスを登録する
 - [会社所有のデバイスを IMEI 番号を使用してデバイスおよびターゲット ポリシーを登録できるように指定する](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)


<!--HONumber=Jun16_HO1-->


