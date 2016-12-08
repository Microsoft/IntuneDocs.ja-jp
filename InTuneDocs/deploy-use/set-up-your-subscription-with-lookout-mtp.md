---
title: "Lookout を利用できるようにサブスクリプションを設定する | Microsoft Intune"
description: "このトピックでは、Lookout デバイス脅威保護を構成する方法について説明します。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1187ad3fdd4a427333d610686698c1f806c6ee33
ms.openlocfilehash: 1d8cdaa36a852fba5912c250daa500e16bd3b661


---

# <a name="set-up-your-subscription-for-lookout-device-threat-protection"></a>Lookout デバイス脅威保護用にサブスクリプションを設定する
サブスクリプションで Lookout デバイス脅威保護サービスを利用できるようにするには、Azure Active Directory (Azure AD) サブスクリプションに関する以下の情報を Lookout のサポート ((enterprisesupport@lookout.com)) に提出する必要があります。 Lookout を Intune に統合するために、Lookout Mobility Endpoint Security テナントが Azure AD サブスクリプションに関連付けられます。 

* **Azure AD テナント ID**
* Lookout コンソールへの**フル** アクセス用の **Azure AD グループ オブジェクト ID**
* Lookout コンソールへの**制限付き**アクセス用の **Azure AD グループ オブジェクト ID** (省略可能)

> [!IMPORTANT]
> Azure AD と Intune の統合に、Azure AD と関連付けられていない既存の Lookout Mobile Endpoint Security テナントを使用することはできません。 新しい Lookout Mobile Endpoint Security テナントを作成するように、Lookout のサポートに依頼してください。 Azure AD ユーザーの追加にはこの新しいテナントを使用してください。

次のセクションの説明に従って、Lookout サポート チームに提供する必要のある情報を収集してください。  

## <a name="get-your-azure-ad-information"></a>Azure AD の情報を取得する
### <a name="azure-ad-tenant-id"></a>Azure AD テナント ID
[Azure AD 管理ポータル](https://manage.windowsazure.com)にサインインして、サブスクリプションを選択します。 

![テナントの名前が表示される Azure AD ページのスクリーンショット](../media/mtp/aad_tenant_name.png) サブスクリプションの名前を選択すると、表示される URL にサブスクリプション ID が含まれています。  サブスクリプション ID を検索する際に問題が生じた場合は、サブスクリプション ID の検索方法に関するヒントが記載されているこちらの [Microsoft サポート記事](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US)を参照してください。   
### <a name="azure-ad-group-id"></a>Azure AD グループ ID
Lookout コンソールでは、次の 2 つのレベルのアクセスがサポートされます。  
* **フル アクセス:** Azure AD の管理者は、フル アクセス権を持つユーザーのグループを作成できるだけでなく、必要に応じて制限付きアクセス権を持つユーザーのグループも作成できます。  これらのグループのユーザーだけが、**Lookout コンソール**にログインできます。
* **制限付きアクセス:** このグループのユーザーは、Lookout コンソールの構成と登録に関するモジュールにはアクセスできません。Lookout コンソールの**セキュリティ ポリシー** モジュールには読み取り専用でアクセスできます。  

アクセス許可の詳細については、Lookout Web サイトの[こちらの記事](https://personal.support.lookout.com/hc/en-us/articles/114094105653)をご覧ください。

**グループ オブジェクト ID** は、**Azure AD 管理コンソール**のグループの**プロパティ** ページにあります。

![GroupID フィールドが強調して示されているプロパティ ページのスクリーンショット](../media/mtp/aad_group_object_id.png)

以上の情報を収集した後、Lookout のサポート (電子メール: enterprisesupport@lookout.com) に依頼します。

Lookout のサポート担当者は、お客様の連絡窓口となっている方と協力し、収集された情報を使用してサブスクリプションの登録と Lookout Enterprise アカウントの作成を行います。


## <a name="configure-your-subscription-with-lookout-device-threat-protection"></a>Lookout デバイス脅威保護を利用できるようにサブスクリプションを構成する
### <a name="step-1-set-up-your-device-threat-protection"></a>手順 1: デバイス脅威保護をセットアップする
Lookout サポートによる Lookout Enterprise アカウントの作成が完了すると、Lookout コンソールにサインインできるようになります。   ログイン URL (https://aad.lookout.com/les?action=consent) へのリンクを含む Lookout からの電子メールが、会社の主要な連絡先に送られます。

Lookout コンソールに初めてログインするときは、Azure AD の全体管理者ロールを持つユーザー アカウントを使用する必要があります。Lookout で Azure AD テナントを登録するためにその情報が必要だからです。   それ以降のサインインでは、ユーザーがこのレベルの Azure AD 権限を持つ必要はありません。  この最初のログインでは、同意ページが表示されます。 **[同意]** を選んで登録を完了します。

![Lookout コンソールの初回ログイン ページのスクリーンショット](../media/mtp/lookout_mtp_initial_login.png) 承諾して同意すると、Lookout コンソールが自動的に表示されます。 初期登録後のログインは、URL "https://aad.lookout.com" を使って行うことができます。

ログインで問題が発生する場合は、[トラブルシューティングに関する記事](https://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration)をご覧ください。

以下の手順では、Lookout のセットアップを完了するために [Lookout コンソール](https://aad.lookout.com)で行う必要のあるタスクの概要を示します。

### <a name="step-2-configure-the-intune-connector"></a>手順 2: Intune コネクタを構成する

1.  Lookout コンソールで **[System]** (システム) モジュールから **[Connectors]** (コネクタ) タブを選択し、**[Intune]** を選択します。

  ![Lookout コンソールの [Connectors] (コネクタ) タブが開き [Intune] オプションが強調されている状態のスクリーンショット](../media/mtp/lookout_mtp_setup-intune-connector.png)

2.  [Connection Settings] (接続設定) オプションで [Heartbeat Frequency] (ハートビート周期) を分単位で構成します。  Intune コネクタの準備ができました。  

  ![ハートビート周期が構成されている接続設定タブのスクリーンショット](../media/mtp/lookout-mtp-connection-settings.png)

### <a name="step-3-configure-enrollment-groups"></a>手順 3: 登録グループを構成する
**[Enrollment Management]** (登録管理) オプションで、デバイスを Lookout に登録する必要があるユーザーのセットを定義します。 最初に小さいユーザー グループでテストし、統合のしくみを理解することをお勧めします。  テスト結果に問題がなければ、他のユーザー グループに登録を拡張できます。

登録グループを作成するには、初めに Azure AD セキュリティ グループを定義します。このグループには、最初に Lookout デバイス脅威保護に登録されるユーザーが属します。 Azure AD でグループを作成したら、Lookout コンソールで **[Enrollement Management]** (登録管理) オプションに移動し、Azure AD セキュリティ グループの登録用の **[Display Name(s)]** (表示名) を追加します。

ユーザーが登録グループに追加されると、そのユーザーのデバイスのうち、Azure AD で識別されサポートされるものは Lookout デバイス脅威保護に登録されてアクティブ化の対象になります。  サポートされるデバイスでユーザーが Lookout for Work アプリを初めて開いたときに、そのデバイスが Lookout でアクティブ化されます。

![Intune コネクタ登録ページのスクリーンショット](../media/mtp/lookout-mtp-enrollment.png)

新しいデバイスをチェックする間隔には、既定値 (5 分) を使用することをお勧めします。

>[!IMPORTANT]
> 表示名では、大文字と小文字が区別されます。  Azure ポータルのセキュリティ グループの **[プロパティ]** ページに表示される **[表示名]** を使用してください。 下に示すセキュリティ グループの **[プロパティ]** ページでは、表示名は先頭が大文字になっています。  タイトルはすべて小文字で表示されていますが、これを Lookout コンソールへの入力に使用しないでください。
>![Azure Portal の Azure Active Directory サービスの [プロパティ] ページのスクリーンショット](../media/mtp/aad-group-display-name.png)

現在のリリースには次の制限があります。  
* グループの表示名の検証は行われません。  Azure ポータルで Azure AD セキュリティ グループの **[表示名]** フィールドに表示される値を必ず使用してください。
* グループ内でのグループの作成は現在サポートされていません。  指定する Azure AD セキュリティ グループにはユーザーのみが含まれ、入れ子になったグループを含めることはできません。


### <a name="step-4-configure-state-sync"></a>手順 4: 状態の同期を構成する
**[State Sync]** (状態同期) オプションで、Intune に送信する必要があるデータの種類を指定します。  現時点では、Lookout と Intune の統合が正常に動作するには、デバイスの状態と脅威の状態の両方を有効にする必要があります。  これらは既定で有効になっています。
### <a name="step-5-configure-error-report-email-recipient-information"></a>手順 5: エラー レポートの電子メール受信者情報を構成する
**[Error Management]** (エラー管理) オプションで、エラー レポートを受け取る電子メール アドレスを入力します。

![Intune コネクタ エラー管理ページのスクリーンショット](../media/mtp/lookout-mtp-connector-error-notifications.png)

### <a name="step-6-configure-enrollment-settings"></a>手順 6. 登録設定を構成する
**[System]** (モジュール) の **[Connectors]** (コネクタ) ページで、デバイスが切断されたと判断されるまでの日数を指定します。  切断されたデバイスは非準拠と見なされ、Intune の条件付きアクセス ポリシーに基づいて会社のアプリケーションにアクセスできなくなります。 1 から 90 日の値を指定できます。

![](../media/mtp/lookout-console-enrollment-settings.png)

### <a name="step-7-configure-email-notifications"></a>手順 7: 電子メール通知を構成する
脅威に関する電子メール通知を受け取りたい場合は、通知を受け取るユーザー アカウントで [Lookout コンソール](https://aad.lookout.com)にサインインします。 **[System]** (システム) モジュールの **[Preferences]** (基本設定) タブで、通知を選択して、**[ON]** (オン) に設定します。 変更を保存します。

![ユーザー アカウントが表示された [Preferences] (基本設定) ページのスクリーンショット](../media/mtp/lookout-mtp-email-notifications.png) 電子メール通知を受け取る必要がなくなった場合は、通知を **[OFF]** (オフ) に設定して変更を保存します。
### <a name="step-8-configure-threat-classification"></a>手順 8: 脅威の分類を構成する
Lookout デバイス脅威保護によって、さまざまな種類のモバイルの脅威が分類されます。 [Lookout の脅威の分類](http://personal.support.lookout.com/hc/en-us/articles/114094130693)には、既定のリスク レベルが関連付けられています。 これらは会社の要件に合わせていつでも変更できます。

![脅威と分類を示すポリシー ページのスクリーンショット](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> ここで指定するリスク レベルは、デバイス脅威保護における重要な要素の 1 つです。デバイスのコンプライアンスは、これらのリスク レベルに従って実行時に計算されるためです。 つまり、Intune 管理者が設定するポリシーのルールに従って、デバイスはアクティブな脅威の最低レベルが高、中、または低の場合に非準拠と判断されます。 Lookout デバイス脅威保護での脅威分類ポリシーは、Intune でのデバイスのコンプライアンス計算に直接影響を与えます。

## <a name="watching-enrollment"></a>登録を監視する
セットアップが完了すると、Lookout デバイス脅威保護は Azure AD のポーリングを開始し、指定された登録グループに対応するデバイスを探します。  登録されたデバイスに関する情報は、[Devices] (デバイス) モジュールで確認できます。  デバイスの初期状態は保留中と表示されます。  Lookout for Work アプリがデバイスでインストールされたり、オープンになったり、アクティブ化されたりすると、デバイスの状態が変わります。  Lookout for Work アプリをデバイスにプッシュする方法の詳細については、「[Lookout for Work アプリを構成して展開する](configure-and-deploy-lookout-for-work-apps.md)」をご覧ください。
## <a name="next-steps"></a>次のステップ
[Intune 管理コンソールで Lookout MTP の接続を有効にする](enable-lookout-mtp-connection-in-intune.md)



<!--HONumber=Nov16_HO1-->


