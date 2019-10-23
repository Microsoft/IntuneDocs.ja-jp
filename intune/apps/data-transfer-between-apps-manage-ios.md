---
title: iOS アプリ間のデータ転送を管理する
titleSuffix: Microsoft Intune
description: Microsoft Intune でモバイル アプリ管理ポリシーを使用してアプリ間でデータの転送を管理する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db583b1fc89edf72f329a605cc86363593eaaa9d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72497916"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Microsoft Intune で iOS アプリ間のデータ転送を管理する方法

会社のデータを保護するには、管理しているアプリにのみファイルの転送を制限します。 iOS アプリは次の方法で管理できます。

- アプリ用のアプリ保護ポリシーを構成して、職場または学校アカウントの組織データを保護します。 これを "*ポリシー マネージド アプリ*" と呼びます。  [アプリ保護ポリシーで管理できるすべての Intune 管理アプリに関するページ](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)をご覧ください

- iOS デバイス管理を使用してアプリを展開し、管理します。そのためには、モバイル デバイス管理 (MDM) ソリューションにデバイスを登録する必要があります。 "*ポリシー マネージド アプリ*" または他の iOS マネージド アプリを展開できます。

登録された iOS デバイスの **Open In Management** 機能では、iOS で管理されたアプリ間のファイル転送を制限できます。 構成設定で *Open In Management* の制限を設定した後、MDM ソリューションを使用して制限を展開します。  展開されているアプリをユーザーがインストールすると、管理者が設定した制限が適用されます。

## <a name="use-app-protection-with-ios-apps"></a>iOS アプリでアプリ保護を使用する
アプリ保護ポリシーを iOS の **Open In Management** 機能と共に使用して、以下のように会社データを保護します。

- **MDM ソリューションによって管理されていないデバイス:** アプリ保護ポリシーの設定をセットして、"*Open In 拡張機能*" または "*Share 拡張機能*" により他のアプリケーションとのデータの共有を制御できます。  そのためには、 **[他のアプリに組織データを送信]** の設定を値 **[Policy managed apps with Open-In/Share filtering]\(Open In/Share フィルター利用のポリシー マネージド アプリ\)** に構成します。  "*ポリシー マネージド アプリ*" での *Open In/Share* 動作では、共有のオプションとして他の "*ポリシー マネージド アプリ*" のみが表示されます。 

- **MDM ソリューションで管理されるデバイス**: Intune またはサード パーティの MDM ソリューションに登録されているデバイスでは、アプリと、アプリ保護ポリシーおよび MDM を通して展開される他のマネージド iOS アプリの間でのデータ共有は、Intune のアプリ ポリシーおよび iOS の **Open in management** 機能によって制御されます。 MDM ソリューションを使用して展開するアプリを、Intune アプリ保護ポリシーとも関連付けるには、[ユーザー UPN 設定の構成](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm)に関するセクションに従って、ユーザー UPN 設定を構成します。 他のアプリへのデータ転送を許可する方法を指定するには、 **[他のアプリに組織データを送信]** を有効にして、希望する共有レベルを選択します。 アプリで他のアプリからのデータの受信を許可する方法を指定するには、 **[他のアプリからデータを受信]** を有効にして、希望するデータ受信レベルを選択します。 アプリ データの受信と共有の詳細については、「[データ再配置設定](app-protection-policy-settings-ios.md#data-protection)」を参照してください。

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Microsoft Intune またはサード パーティ EMM のユーザー UPN 設定を構成する
Intune またはサード パーティの EMM ソリューションによって管理されているデバイスで、登録されているユーザー アカウントを識別するには、ユーザー UPN 設定を構成することが**必要**です。 UPN 構成は、Intune から展開するアプリ保護ポリシーと連携します。 次に示す手順は、UPN の設定の構成方法とその結果のユーザー エクスペリエンスに関する一般的なフローです。

1. [Azure Portal](https://portal.azure.com) で、iOS 用の[アプリ保護ポリシーを作成して割り当て](app-protection-policies.md)ます。 企業の要件に合わせてポリシー設定を構成し、このポリシーを使う iOS アプリを選びます。

2. 次の汎用化された手順を使用して、Intune またはサード パーティの MDM ソリューションで管理するアプリとメール プロファイルをデプロイします。 このエクスペリエンスは*例 1* でも取り上げています。

3. 次のアプリ構成設定でアプリをマネージド デバイスにデプロイします。

      **キー** = IntuneMAMUPN、**値** = <username@company.com>

      例: [‘IntuneMAMUPN’, ‘janellecraig@contoso.com’]
      
     > [!NOTE]
     > Intune で、App Configuration ポリシーの登録の種類を、 **[マネージド デバイス]** に設定する必要があります。
     > さらに、アプリを、Intune ポータル サイトからインストールするか (使用可能として設定されている場合)、または必要に応じてデバイスにプッシュする必要があります。 

4. 登録済みデバイスに、Intune またはサード パーティの MDM プロバイダーを使用して **Open in management** ポリシーをデプロイします。


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>例 1:Intune またはサード パーティ MDM コンソールの管理エクスペリエンス

1. Intune またはサード パーティ MDM プロバイダーの管理コンソールに移動します。 登録済みの iOS デバイスにアプリケーション構成設定をデプロイするコンソールのセクションに移動します。

2. [アプリケーションの構成] セクションで、次の設定を入力します。

   **キー** = IntuneMAMUPN、**値** = <username@company.com>

   キー/値ペアの正確な構文は、サード パーティ MDM プロバイダーによって異なります。 次の表は、サードパーティ MDM プロバイダーの例と、キー/値ペアに入力する必要のある正確な値を示します。

   |サードパーティ MDM プロバイダー| Configuration キー | 値の種類 | 構成値|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | 文字列型 | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | 文字列型 | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | 文字列型 | ${userUPN} **または** ${userEmailAddress} |
   |Citrix Endpoint Management | IntuneMAMUPN | 文字列型 | ${user.userprincipalname} |
   |ManageEngine Mobile Device Manager | IntuneMAMUPN | 文字列型 | %upn% |

> [!NOTE]  
> iOS の Outlook アプリでは、[構成デザイナーを使用する] オプションを指定して App Configuration のポリシーを展開した場合、ポリシーに対して構成キー IntuneMAMUPN が暗黙で自動的に構成されます。 詳しくは、「[New Outlook for iOS and Android App Configuration Policy Experience – General App Configuration (iOS および Android 用 Outlook の新しい App Configuration ポリシー エクスペリエンス – 一般的なアプリの構成)](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481)」の FAQ セクションをご覧ください。 


### <a name="example-2-end-user-experience"></a>例 2:エンドユーザー エクスペリエンス

"*OS 共有を使用した*" ポリシー マネージド アプリ "*から他のアプリケーションへの共有*"

1. ユーザーが、登録されている iOS デバイスで Microsoft OneDrive アプリを開き、職場アカウントにサインインします。  ユーザーが入力するアカウントは、Microsoft OneDrive アプリのアプリ構成設定で指定したアカウントの UPN と一致している必要があります。

2. サインインすると、管理者が構成したアプリ設定が、Microsoft OneDrive のユーザー アカウントに適用されます。  これには、 **[他のアプリに組織データを送信]** の設定を値 **[OS 共有利用のポリシー マネージド アプリ]** に構成することが含まれます。

3. ユーザーが、作業ファイルをプレビューし、Open In を使用して iOS マネージド アプリへの共有を試みます。  

4. データ転送は成功し、データは iOS マネージド アプリの **Open In Management** によって保護されるようになります。  Intune APP は、"*ポリシー マネージド アプリ*" ではないアプリケーションには適用されません。

"*受信した組織データを使用した*" iOS マネージド アプリ "*から*" ポリシー マネージド アプリ "*への共有*"

1. ユーザーが、マネージド電子メール プロファイルを使用して登録されている iOS デバイスでネイティブ メールを開きます。  

1. ユーザーが、ネイティブ メールから作業ドキュメントの添付ファイルを Microsoft Word で開きます。

1. Word アプリが起動すると、次の 2 つのいずれかのエクスペリエンスが発生します。
   1. 次の場合、データは Intune APP によって保護されます。
      - ユーザーが、Microsoft Word アプリに対するアプリ構成設定で指定されているアカウントの UPN と一致する職場アカウントにサインインしています。 
      - 管理者が構成したアプリ設定が、Microsoft Word のユーザー アカウントに適用されます。  これには、 **[他のアプリからデータを受信]** の設定を値 **[受信した組織データを持つすべてのアプリ]** に構成することが含まれます。
      - データ転送が成功し、ドキュメントにはアプリで職場 ID のタグが付けられます。  Intune APP によって、ドキュメントに対するユーザー操作が保護されます。
   1. 次の場合、データは Intune APP によって保護され**ません**。
      - ユーザーが、職場アカウントにサインインして**いません**。
      - ユーザーがサインインしていないため、管理者が構成した設定が、Microsoft Word に適用され**ません**。
      - データ転送が成功し、ドキュメントにはアプリで職場 ID のタグが付けられ**ません**。  アクティブではないため、Intune APP によってドキュメントに対するユーザー操作が保護され**ません**。

    > [!NOTE]
    > ユーザーは Word を使用して個人用アカウントを追加し、利用することができます。 ユーザーが作業コンテキスト以外で Word を使用する場合は、アプリ保護ポリシーは適用されません。 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>サードパーティ EMM のユーザー UPN 設定を検証する

ユーザー UPN 設定を構成した後で、iOS アプリが Intune アプリ保護ポリシーを受信して準拠できることを検証します。

たとえば、**Require app PIN** ポリシー設定は簡単にテストできます。 ポリシー設定が **[Require]\(必要\)** の場合、会社のデータにアクセスする前に PIN の設定または入力を求めるプロンプトが表示されます。

まず、[アプリ保護ポリシーを作成し、iOS アプリに割り当て](app-protection-policies.md)ます。 アプリ保護ポリシーをテストする方法の詳細については、[アプリ保護ポリシーの検証](app-protection-policies-validate.md)に関するページを参照してください。


## <a name="see-also"></a>関連項目
[Intune アプリ保護ポリシーとは](app-protection-policy.md)
