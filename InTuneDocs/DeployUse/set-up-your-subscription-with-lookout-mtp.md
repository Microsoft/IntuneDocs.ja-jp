---
title: "Lookout MTP でサブスクリプションをセットアップする | Microsoft Intune"
description: "このトピックでは、Lookout MTP を構成する方法について説明します。"
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba2196ff03975df1f8969e1522f7af459343694d
ms.openlocfilehash: 530a34c7c75a4fa73cbb62873e2d28883b91b57e


---

# Lookout Mobile Threat Protection 用にサブスクリプションを設定する
サブスクリプションを Lookout MTP サービス対応にするには、Lookout のサポート (enterprisesupport@lookout.com) に Azure Active Directory (Azure AD) サブスクリプションに関する以下の情報を提供する必要があります。 

* **Azure AD テナント ID**
* Lookout MTP コンソールへの**フル** アクセス用の **Azure AD グループ オブジェクト ID**
* Lookout MTP コンソールへの**制限付き**アクセス用の **Azure AD グループ オブジェクト ID** (省略可能)

次のセクションの説明に従って、Lookout サポート チームに提供する必要のある情報を収集してください。  

## Azure AD の情報を取得する
### Azure AD テナント ID
[Azure AD 管理ポータル](https://manage.windowsazure.com)にサインインして、サブスクリプションを選択します。 

![テナントの名前が表示される Azure AD ページのスクリーンショット](../media/mtp/aad_tenant_name.png) サブスクリプションの名前を選択すると、表示される URL にサブスクリプション ID が含まれています。  サブスクリプション ID を検索する際に問題が生じた場合は、サブスクリプション ID の検索方法に関するヒントが記載されているこちらの [Microsoft サポート記事](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US)を参照してください。   
### Azure AD のグループ ID を取得する
Lookout MTP コンソールでは、2 つのレベルのアクセスがサポートされています。  
* **フル アクセス:** Azure AD の管理者は、フル アクセス権を持つユーザーのグループを作成できるだけでなく、必要に応じて制限付きアクセス権を持つユーザーのグループも作成できます。  これらのグループのユーザーだけが、**Lookout MTP コンソール**にログインできます。
* **制限付きアクセス:** このグループのユーザーは、Lookout MTP コンソールの構成と登録に関する一部のモジュールにアクセスできません。Lookout MTP コンソールの**セキュリティ ポリシー** モジュールへのアクセスは読み取り専用です。  

アクセス許可の詳細については、Lookout Web サイトの[こちらの記事](https://personal.support.lookout.com/hc/en-us/articles/114094105653)をご覧ください。

**グループ オブジェクト ID** は、**Azure AD 管理コンソール**のグループの**プロパティ** ページにあります。

![GroupID フィールドが強調して示されているプロパティ ページのスクリーンショット](../media/mtp/aad_group_object_id.png)

以上の情報を収集した後、Lookout のサポート (電子メール: enterprisesupport@lookout.com) に依頼します。

Lookout のサポートは主要な連絡先と協力し、収集した情報を使用してサブスクリプションの登録と Lookout MTP Enterprise アカウントの作成を行います。


## Lookout MTP でサブスクリプションを構成する
### 手順 1: MTP をセットアップする
Lookout サポートが Lookout MTP Enterprise アカウントを作成した後は、Lookout MTP コンソールにサインインできます。   ログイン URL (https://aad.lookout.com/les?action=consent) へのリンクを含む Lookout からの電子メールが、会社の主要な連絡先に送られます。

Lookout MTP コンソールに初めてログインするときは、Azure AD の全体管理者ロールを持つユーザー アカウントを使用する必要があります。Lookout MTP で、Azure AD テナントを登録するためにその情報が必要だからです。   それ以降のサインインでは、ユーザーがこのレベルの Azure AD 権限を持つ必要はありません。  この最初のログインでは、同意ページが表示されます。 **[同意]** を選んで登録を完了します。

![Lookout MTP コンソールの初回ログイン ページのスクリーンショット](../media/mtp/lookout_mtp_initial_login.png) 承諾して同意すると、Lookout MTP コンソールに移動します。 初期登録後のログインは、URL "https://aad.lookout.com" を使って行うことができます。

ログインで問題が発生する場合は、[トラブルシューティングに関する記事](https://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration)をご覧ください。

以下の手順では、Lookout MTP のセットアップを完了するために [Lookout MTP コンソール](https://aad.lookout.com)で行う必要があるタスクの概要を示します。

### 手順 2: Intune コネクタを構成する

1.  Lookout MTP コンソールで **[System]** (システム) モジュールに移動し、**[Connectors]** (コネクタ) タブを選択し、**[Intune]** を選択します。

  ![[Connectors] (コネクタ) タブの [Intune] オプションが強調して示されている Lookout MTP コンソールのスクリーンショット](../media/mtp/lookout_mtp_setup-intune-connector.png)

2.  [Connection Settings] (接続設定) オプションで [Heartbeat Frequency] (ハートビート周期) を分単位で構成します。  Intune コネクタの準備ができました。  

  ![ハートビート周期が構成されている接続設定タブのスクリーンショット](../media/mtp/lookout-mtp-connection-settings.png)

### 手順 3: 登録グループを構成する
**[Enrollment Management]** (登録管理) オプションで、デバイスを Lookout に登録する必要があるユーザーのセットを定義します。 最初に小さいユーザー グループでテストし、統合のしくみを理解することをお勧めします。  テスト結果に問題がなければ、他のユーザー グループに登録を拡張できます。

登録グループの手始めとして、Lookout MTP に登録する最初のユーザー セットとして適した Azure AD セキュリティ グループを定義します。 Azure AD でグループを作成した後、Lookout MTP コンソールで **[Enrollement Management]** (登録管理) オプションに移動し、Azure AD セキュリティ グループの登録用の **[Display Name(s)]** (表示名) を追加します。

登録グループに含まれるユーザーの、Azure AD で識別されてサポートされるデバイスは、Lookout MTP に登録されてアクティブ化の対象になります。  サポートされるデバイスで Lookout for Work アプリを初めて開くと、デバイスが Lookout MTP でアクティブ化されます。
![Intune コネクタ登録ページのスクリーンショット](../media/mtp/lookout-mtp-enrollment.png)

新しいデバイスをチェックする間隔には、既定値 (5 分) を使用することをお勧めします。

>[!IMPORTANT]
> 表示名では、大文字と小文字が区別されます。  Azure ポータルでは、セキュリティ グループの **[プロパティ]** ページに表示される **[表示名]** を使用します。 下に示すセキュリティ グループの **[プロパティ]** ページでは、表示名は先頭が大文字になっています。  ただし、タイトルはすべて小文字で表示されているので、それを Lookout MTP コンソールへの入力に使用しないでください。
>![Azure ポータル、Azure Active Directory サービス、プロパティ ページのスクリーンショット](../media/mtp/aad-group-display-name.png)

現在のリリースには次の制限があります。  
* グループの表示名の検証は行われません。  Azure ポータルで Azure AD セキュリティ グループの **[表示名]** フィールドに表示される値を必ず使用してください。
* グループ内でのグループの作成は現在サポートされていません。  指定する Azure AD セキュリティ グループにはユーザーのみが含まれ、入れ子になったグループを含めることはできません。


### 手順 4: 状態の同期を構成する
**[State Sync]** (状態同期) オプションで、Intune に送信する必要があるデータの種類を指定します。  現時点では、Lookout と Intune の統合が正常に動作するには、デバイスの状態と脅威の状態の両方を有効にする必要があります。  これらは既定で有効になっています。
### 手順 5: エラー レポートの電子メール受信者情報を構成する
**[Error Management]** (エラー管理) オプションで、エラー レポートを受け取る電子メール アドレスを入力します。

![Intune コネクタ エラー管理ページのスクリーンショット](../media/mtp/lookout-mtp-connector-error-notifications.png)

### 手順 6: 電子メール通知を構成する
脅威に対する電子メール通知を受け取る場合は、通知を受け取るユーザー アカウントで [Lookout MTP コンソール](https://aad.lookout.com)にサインインします。 **[System]** (システム) モジュールの **[Preferences]** (基本設定) タブで、通知を選択して、**[ON]** (オン) に設定します。 変更を保存します。

![ユーザー アカウントが表示された基本設定ページのスクリーンショット](../media/mtp/lookout-mtp-email-notifications.png) 電子メール通知を受け取る必要がなくなった場合は、通知を **[OFF]** (オフ) に設定して変更を保存します。
### 手順 7: 脅威の分類を構成する
Lookout MTP はさまざまな種類のモバイルの脅威を分類します。 [Lookout MTP の脅威の分類](http://personal.support.lookout.com/hc/en-us/articles/114094130693)には、既定のリスク レベルが関連付けられています。 これらは会社の要件に合わせていつでも変更できます。

![脅威と分類を示すポリシー ページのスクリーンショット](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Intune の統合は、ここで指定したリスク レベルに従って実行時にデバイスのコンプライアンスを計算するため、それらのリスク レベルは MTP の重要な要素となります。 つまり、Intune 管理者が設定するポリシーのルールに従って、デバイスはアクティブな脅威の最低レベルが高、中、または低の場合に非準拠と判断されます。 MTP での脅威分類ポリシーは、Intune でのデバイスのコンプライアンス計算に直接影響を与えます。

## 登録を監視する
セットアップが完了すると、Lookout MTP は指定された登録グループに対応するデバイスを探す Azure AD のポーリングを開始します。  登録されたデバイスに関する情報は、[Devices] (デバイス) モジュールで確認できます。  デバイスの初期状態は保留中と表示されます。  Lookout for Work アプリがデバイスでインストールされたり、オープンになったり、アクティブ化されたりすると、デバイスの状態が変わります。  Lookout for Work アプリをデバイスにプッシュする方法の詳細については、「[Lookout for Work アプリを構成して展開する](configure-and-deploy-lookout-for-work-apps.md)」をご覧ください。
## 次のステップ
[Intune 管理コンソールで Lookout MTP の接続を有効にする](enable-lookout-mtp-connection-in-intune.md)



<!--HONumber=Sep16_HO3-->


