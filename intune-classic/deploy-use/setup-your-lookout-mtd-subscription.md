---
title: "Lookout でサブスクリプションを設定する"
description: "このトピックでは、Lookout デバイス脅威保護を構成する方法について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 215d579c7e8806f98d99db9319aa5808d99653c1
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="set-up-your-lookout-mobile-threat-defense-subscription"></a>Lookout Mobile Threat Defense サブスクリプションを設定する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Lookout Mobile Threat Defense を設定するには、次の手順を実行します。

| #        |手順  |
| ------------- |:-------------|
| 1 | [Azure AD の情報を収集する](#collect-azure-ad-information) |
| 2 | [サブスクリプションを構成する](#configure-your-subscription) |
| 3 | [登録グループを構成する](#configure-enrollment-groups) |
| 4 | [状態の同期を構成する](#configure-state-sync) |
| 5 | [エラー レポートの電子メール受信者情報を構成する](#configure-error-report-email-recipient-information) |
| 6 | [登録設定を構成する](#configure-enrollment-settings) |
| 7 | [電子メールの通知を構成する](#configure-email-notifications) |
| 8 | [脅威の分類を構成する](#configure-threat-classification) |
| 1 | [登録を監視する](#watching-enrollment) |


> [!IMPORTANT]
> Azure AD と Intune の統合に、Azure AD と関連付けられていない既存の Lookout Mobile Endpoint Security テナントを使用することはできません。 新しい Lookout Mobile Endpoint Security テナントを作成するように、Lookout のサポートに依頼してください。 Azure AD ユーザーの追加にはこの新しいテナントを使用してください。

## <a name="collect-azure-ad-information"></a>Azure AD の情報を収集する
Lookout を Intune に統合するために、Lookout Mobility Endpoint Security テナントが Azure AD サブスクリプションに関連付けられます。 Lookout Mobile Threat Defense サービスのサブスクリプションを有効にするには、Lookout のサポート (enterprisesupport@lookout.com) に次の情報を伝えてください。  

* **Azure AD テナント ID**
* Lookout コンソールへの**フル** アクセス用の **Azure AD グループ オブジェクト ID**
* Lookout コンソールへの**制限付き**アクセス用の **Azure AD グループ オブジェクト ID** (省略可能)

次の手順に従って、Lookout サポート チームに提供する必要のある情報を収集してください。

1. [Azure AD 管理ポータル](https://manage.windowsazure.com)にサインインして、サブスクリプションを選択します。 
  ![テナントの名前が表示される Azure AD ページのスクリーンショット](../media/mtp/aad_tenant_name.png)
2. サブスクリプションの名前を選択すると、表示される URL にサブスクリプション ID が含まれています。  サブスクリプション ID を検索する際に問題が生じた場合は、サブスクリプション ID の検索方法に関するヒントが記載されているこちらの [Microsoft サポート記事](https://support.office.com/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b)を参照してください。 
3. Azure AD のグループ ID を確認します。 Lookout コンソールでは、次の 2 つのレベルのアクセスがサポートされます。  
  * **フル アクセス:** Azure AD の管理者は、フル アクセス権を持つユーザーのグループを作成できるだけでなく、必要に応じて制限付きアクセス権を持つユーザーのグループも作成できます。  これらのグループのユーザーだけが、**Lookout コンソール**にログインできます。
  * **制限付きアクセス:** このグループのユーザーは、Lookout コンソールの構成と登録に関するモジュールにはアクセスできません。Lookout コンソールの**セキュリティ ポリシー** モジュールには読み取り専用でアクセスできます。  

  アクセス許可の詳細については、Lookout Web サイトの[こちらの記事](https://personal.support.lookout.com/hc/articles/114094105653)をご覧ください。

  **グループ オブジェクト ID** は、**Azure AD 管理コンソール**のグループの**プロパティ** ページにあります。

  ![[グループ ID] フィールドが強調表示されているプロパティ ページのスクリーンショット](../media/mtp/aad_group_object_id.png)

4. この情報を収集した後で、Lookout のサポート (メール: enterprisesupport@lookout.com) にお問い合わせください。 Lookout のサポート担当者は、お客様の連絡窓口となっている方と協力し、収集された情報を使用してサブスクリプションの登録と Lookout Enterprise アカウントの作成を行います。

## <a name="configure-your-subscription"></a>サブスクリプションを構成する
1. Lookout のサポート担当者が Lookout Enterprise アカウントを作成すると、ログイン URL (https://aad.lookout.com/les?action=consent) へのリンクを含む Lookout からの電子メールが、会社の主要な連絡先に送られます。

2.  Lookout コンソールに初めてログインする場合、グローバル管理者の Azure AD ロールを持つユーザー アカウントを使用し、Azure AD テナントを登録する必要があります。 以降のサインインにこのレベルの Azure AD 特権は必要ありません。 同意ページが表示されます。 **[同意]** を選んで登録を完了します。

  ![Lookout コンソールの初回ログイン ページのスクリーンショット](../media/mtp/lookout_mtp_initial_login.png) 承諾して同意すると、Lookout コンソールが自動的に表示されます。

  ログインで問題が発生した場合は、「[Lookout と Intune の統合に関するトラブルシューティング](/intune-classic/troubleshoot/troubleshooting-lookout-integration)」を参照してください。

3.  [Lookout コンソール](https://aad.lookout.com)で **[System]** (システム) モジュールから **[Connectors]\** (コネクタ) タブを選択し、**[Intune]** を選択します。

  ![Lookout コンソールの 「Connectors」\ (コネクタ) タブが開き [Intune] オプションが強調されている状態のスクリーンショット](../media/mtp/lookout_mtp_setup-intune-connector.png)

4.  **[Connectors]\(コネクタ)** > **[Connection Settings]\(接続設定)** を選択し、**[Heartbeat Frequency]\(ハートビート頻度)** を分単位で指定します。

  ![ハートビート周期が構成されている接続設定タブのスクリーンショット](../media/mtp/lookout-mtp-connection-settings.png)

## <a name="configure-enrollment-groups"></a>登録グループを構成する
1. ベスト プラクティスとして、Lookout の統合をテストする少数のユーザーを含む Azure AD セキュリティ グループを [Azure AD 管理ポータル](https://manage.windowsazure.com)に作成することをお勧めします。

  Azure AD で識別され、サポートされている登録グループのユーザーの Lookout のサポートを受け、Intune に登録されているすべてのデバイスは、Lookout デバイス脅威保護に登録されてアクティブ化の対象になります。

2. [Lookout コンソール](https://aad.lookout.com)の **[System]**\(システム) モジュールで、**[Connectors]**\(コネクタ) タブを選択し、**[Enrollment Management]**\(登録管理) を選択し、Lookout に登録するデバイスのユーザー セットを定義します。 Azure AD セキュリティ グループの登録の **[表示名]** を追加します。

  ![Intune コネクタ登録ページのスクリーンショット](../media/mtp/lookout-mtp-enrollment.png)

  >[!IMPORTANT]
  > Azure ポータルのセキュリティ グループの **[プロパティ]** に表示される **[表示名]** は大文字と小文字が区別されます。 次の画像のように、セキュリティ グループの **[表示名]** は大文字と小文字が混在していますが、タイトルはすべて小文字です。 Lookout コンソールでは、セキュリティ グループの **[表示名]** の大文字/小文字と一致させます。
  >![Azure Portal の Azure Active Directory サービスの [プロパティ] ページのスクリーンショット](../media/mtp/aad-group-display-name.png)

  新しいデバイスをチェックする間隔には、既定値 (5 分) を使用することをお勧めします。

  **現時点での制限事項:**
  * Lookout はグループの表示名を検証できません。  Azure ポータルの **[表示名]** フィールドは、Azure AD セキュリティ グループと完全に一致するようにします。
  * 入れ子のグループを作成することはできません。  Lookout で使用する Azure AD セキュリティ グループには、ユーザーのみを含める必要があります。 他のグループを含めることはできません。

3.  グループを追加して、次にサポートされるデバイスでユーザーが Lookout for Work アプリを開いたときに、そのデバイスが Lookout でアクティブ化されます。

4.  結果に問題がなければ、他のユーザー グループまで登録を広げます。

## <a name="configure-state-sync"></a>状態の同期を構成する
**[State Sync]** (状態同期) オプションで、Intune に送信する必要があるデータの種類を指定します。  Lookout と Intune の統合が正常に動作するには、デバイスの状態と脅威の状態の両方が必要です。  これらは既定で有効になっています。

## <a name="configure-error-report-email-recipient-information"></a>エラー レポートの電子メール受信者情報を構成する
**[Error Management]** (エラー管理) オプションで、エラー レポートを受け取る電子メール アドレスを入力します。

![Intune コネクタ エラー管理ページのスクリーンショット](../media/mtp/lookout-mtp-connector-error-notifications.png)

## <a name="configure-enrollment-settings"></a>登録設定を構成する
**[System]**\ (モジュール) の **[Connectors]**\ (コネクタ) ページで、デバイスが切断されたと判断されるまでの日数を指定します。  切断されたデバイスは非準拠と見なされ、Intune の条件付きアクセス ポリシーに基づいて会社のアプリケーションにアクセスできなくなります。 1 から 90 日の値を指定できます。

![](../media/mtp/lookout-console-enrollment-settings.png)

## <a name="configure-email-notifications"></a>電子メールの通知を構成する
脅威に関する電子メール通知を受け取りたい場合は、通知を受け取るユーザー アカウントで [Lookout コンソール](https://aad.lookout.com)にサインインします。 **[System]** (システム) モジュールの **[Preferences]** (基本設定) タブで、通知が必要な脅威レベルを選択して、**[ON]** (オン) に設定します。 変更を保存します。

![ユーザー アカウントが表示された基本設定ページのスクリーンショット](../media/mtp/lookout-mtp-email-notifications.png) 電子メール通知を受け取る必要がなくなった場合は、通知を **[OFF]** (オフ) に設定して変更を保存します。

### <a name="configure-threat-classification"></a>脅威の分類を構成する
Lookout Mobile Threat Defense によって、さまざまな種類のモバイルの脅威が分類されます。 [Lookout の脅威の分類](http://personal.support.lookout.com/hc/articles/114094130693)には、既定のリスク レベルが関連付けられています。 これらは会社の要件に合わせていつでも変更できます。

![脅威と分類を示すポリシー ページのスクリーンショット](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> リスク レベルは、Mobile Threat Defense における重要な要素の 1 つです。デバイスのコンプライアンスは、これらのリスク レベルに従って実行時に計算されるためです。 Intune 管理者が設定するポリシーのルールに従って、デバイスはアクティブな脅威の最低レベルが**高**、**中**、または**低**の場合に非準拠と判断されます。 Mobile Threat Defense での脅威分類ポリシーは、Intune でのデバイスのコンプライアンス計算に直接影響を与えます。

## <a name="watching-enrollment"></a>登録を監視する
セットアップが完了すると、Mobile Threat Defense は Azure AD のポーリングを開始し、指定された登録グループに対応するデバイスを探します。  登録されたデバイスに関する情報は、「Devices」 (デバイス) モジュールで確認できます。  デバイスの初期状態は保留中と表示されます。  Lookout for Work アプリがデバイスでインストールされたり、オープンになったり、アクティブ化されたりすると、デバイスの状態が変わります。  Lookout for Work アプリをデバイスにプッシュする方法の詳細については、「[Lookout for Work アプリを構成して展開する](configure-deploy-lookout-for-work-app.md)」をご覧ください。
## <a name="next-steps"></a>次のステップ
[Intune 管理コンソールで Lookout MTP の接続を有効にする](/intune-classic/deploy-use/enable-lookout-mtd-connection)

