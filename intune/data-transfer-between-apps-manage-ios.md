---
title: iOS アプリ間のデータ転送を管理する
titleSuffix: Microsoft Intune
description: Microsoft Intune でモバイル アプリ管理ポリシーを使用してアプリ間でデータの転送を管理する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9be961908920420dbb4111c2c3ba108b7e11c09f
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66042782"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Microsoft Intune で iOS アプリ間のデータ転送を管理する方法

会社のデータを保護するには、管理しているアプリにのみファイルの転送を制限します。 iOS アプリは次の方法で管理できます。

-   アプリ (**ポリシー マネージド** アプリと呼びます) のアプリ保護ポリシーを構成して、会社データの損失を回避します。 [アプリ保護ポリシーで管理できるすべての Intune 管理アプリに関するページ](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)をご覧ください

-   **MDM チャネル**を介してアプリを展開して管理します。これには、モバイル デバイス管理 (MDM) ソリューションにデバイスを登録する必要があります。 展開するアプリは、**ポリシー マネージド** アプリか、その他の管理されているアプリである必要があります。

iOS デバイスの **Open In Management** 機能を使用すると、**MDM チャネル**を使用して展開されているアプリ間でのみファイル転送が行われるよう制限できます。 *Open In Management* の制限は、構成設定で設定し、MDM ソリューションを使用して展開します。  展開されているアプリをユーザーがインストールすると、管理者が設定した制限が適用されます。

##  <a name="use-app-protection-with-ios-apps"></a>iOS アプリでアプリ保護を使用する
アプリ保護ポリシーを iOS の **Open in Management** 機能と共に使用して、以下のように会社データを保護します。

-   **MDM ソリューションで管理されていない従業員所有のデバイス:** アプリ保護ポリシー設定を **[Allow app to transfer data to only Policy Managed apps]\(アプリでポリシー管理型アプリへのデータ転送のみ許可する\)** に設定できます。 ポリシー マネージド アプリで *Open-In* 動作を行うと、その他のポリシー マネージド アプリのみが共有対象のオプションとして表示されます。 ネイティブ メール アプリで、ユーザーが OneDrive からポリシー保護ファイルを添付ファイルとして送信すると、そのファイルは読み取り不能になります。

-   **Intune で管理されているデバイス:** Intune で登録したデバイスの場合、アプリ保護ポリシーを使用するアプリと、Intune で展開された管理対象の他の iOS アプリの間で自動的にデータを転送できるようになります。 他のアプリへのデータ転送を許可する方法を指定するには、**[アプリで他のアプリへのデータ転送を許可する]** を有効にし、希望する共有レベルを選択します。 アプリで他のアプリからのデータの受信を許可する方法を指定するには、**[アプリで他のアプリからのデータの受信を許可する]** を有効にし、希望するデータ受信レベルを選択します。 **Open in Management** 機能を使用して、Intune で展開されているアプリ間のデータ転送を制御できます。 アプリ データの受信と共有の詳細については、「[データ再配置設定](app-protection-policy-settings-ios.md#data-protection)」を参照してください。   

-   **サードパーティの MDM ソリューションで管理されているデバイス:** iOS の **Open In Management** 機能を使用して、データ転送が管理対象のアプリに対してのみ行われるよう制限できます。
サードパーティの MDM ソリューションを使用して展開するアプリを、Intune アプリ保護ポリシーとも関連付けるには、[ユーザー UPN 設定の構成](#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm)に関するセクションに従ってユーザー UPN 設定を構成します。 アプリがユーザー UPN 設定を使用して展開されている場合、エンド ユーザーが職場アカウントを使用してサインインすると、アプリ保護ポリシーがアプリに適用されます。

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Microsoft Intune またはサード パーティ EMM のユーザー UPN 設定を構成する
ユーザー UPN 設定の構成は、Intune またはサード パーティの EMM ソリューションによって管理されているデバイスに**必要**となります。 UPN 構成は、Intune から展開するアプリ保護ポリシーと連携します。 次に示す手順は、UPN の設定の構成方法とその結果のユーザー エクスペリエンスに関する一般的なフローです。

1.  [Azure Portal](https://portal.azure.com) で、iOS 用の[アプリ保護ポリシーを作成して割り当て](app-protection-policies.md)ます。 企業の要件に合わせてポリシー設定を構成し、このポリシーを使う iOS アプリを選びます。

2.  次の汎用化された手順を使用して、Intune またはサード パーティの MDM ソリューションで管理するアプリとメール プロファイルをデプロイします。 このエクスペリエンスは*例 1* でも取り上げています。

3.  次のアプリ構成設定でアプリをマネージド デバイスにデプロイします。

      **キー** = IntuneMAMUPN、**値** = <username@company.com>

      例: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]
      
       > [!NOTE]
       > Intune では、App Configuration ポリシーを登録の種類 "マネージド デバイス" 用にする必要があります。
       > さらに、アプリは、Intune ポータル サイト (使用可能として設定されている場合) からインストールするか、または必要に応じてデバイスにプッシュする必要があります。 

4.  登録済みデバイスに、Intune またはサード パーティの MDM プロバイダーを使用して **Open in management** ポリシーをデプロイします。


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>例 1:Intune またはサード パーティ MDM コンソールの管理エクスペリエンス

1. Intune またはサード パーティ MDM プロバイダーの管理コンソールに移動します。 登録済みの iOS デバイスにアプリケーション構成設定をデプロイするコンソールのセクションに移動します。

2. [アプリケーションの構成] セクションで、次の設定を入力します。

   **キー** = IntuneMAMUPN、**値** = <username@company.com>

   キー/値ペアの正確な構文は、サード パーティ MDM プロバイダーによって異なります。 次の表は、サードパーティ MDM プロバイダーの例と、キー/値ペアに入力する必要のある正確な値を示します。

   |サードパーティ MDM プロバイダー| Configuration キー | 値の種類 | 構成値|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | String | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | String | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | String | ${userUPN} **または** ${userEmailAddress} |
   |Citrix Endpoint Management | IntuneMAMUPN | String | ${user.userprincipalname} |
   |ManageEngine Mobile Device Manager | IntuneMAMUPN | 文字列型 | %upn% |


### <a name="example-2-end-user-experience"></a>例 2: エンドユーザー エクスペリエンス

1.  ユーザーは、デバイスに Microsoft Word アプリをインストールします。

2.  ユーザーが管理対象のネイティブ メール アプリを起動して、自分の電子メールにアクセスします。

3.  ユーザーがネイティブ メールから Microsoft Word でドキュメントを開こうとします。

4.  Word アプリが起動するとき、ユーザーは職場アカウントを使用してサインインするよう求められます。 ユーザーが入力するアカウントは、Microsoft Word アプリのアプリ構成設定で指定したアカウントと一致している必要があります。

    > [!NOTE]
    > ユーザーは Word を使用して個人用アカウントを追加し、利用することができます。 ユーザーが作業コンテキスト以外で Word を使用する場合は、アプリ保護ポリシーは適用されません。 

5.  サインイン後、アプリ保護ポリシー設定が Word アプリに適用されます。

6.  これでデータ転送が成功し、ドキュメントにはアプリで企業 ID のタグが付けられます。  データは作業コンテキストで処理され、ポリシー設定が適用されます。 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>サードパーティ EMM のユーザー UPN 設定を検証する

ユーザー UPN 設定を構成した後で、iOS アプリが Intune アプリ保護ポリシーを受信して準拠できることを検証します。

たとえば、**Require app PIN** ポリシー設定は簡単にテストできます。 ポリシー設定が **[はい]** の場合、会社のデータにアクセスする前に PIN の設定または入力を求めるプロンプトが表示されます。

まず、[アプリ保護ポリシーを作成し、iOS アプリに割り当て](app-protection-policies.md)ます。 アプリ保護ポリシーをテストする方法の詳細については、[アプリ保護ポリシーの検証](app-protection-policies-validate.md)に関するページを参照してください。


### <a name="see-also"></a>「
[Intune アプリ保護ポリシーとは](app-protection-policy.md)
