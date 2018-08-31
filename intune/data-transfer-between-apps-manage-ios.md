---
title: iOS アプリ間のデータ転送を管理する
titlesuffix: Microsoft Intune
description: Microsoft Intune でモバイル アプリ管理ポリシーを使用してアプリ間でデータの転送を管理する方法について説明します。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2991aa947a693d2eb71a355047ed266838dd92a4
ms.sourcegitcommit: be67f8293b47cc08a46d328a44a50a7ab67c2052
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2018
ms.locfileid: "40251902"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Microsoft Intune で iOS アプリ間のデータ転送を管理する方法
## <a name="manage-ios-apps"></a>iOS アプリを管理する
会社データの保護には、ファイル転送を管理対象のアプリに限定する処理も含まれます。  iOS アプリは次の方法で管理できます。

-   アプリ (**ポリシーで管理されている**アプリと呼ばれます) のアプリ保護ポリシーを構成して、会社データの損失を回避します。 [アプリ保護ポリシーで管理できるすべての Intune 管理アプリに関するページ](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)をご覧ください

-   また、アプリは **MDM チャネル**から展開して管理することもできます。  これには、デバイスが MDM ソリューションに登録されていることが必要です。 これらは**ポリシーで管理されている**アプリであるか、またはその他の管理対象アプリである必要があります。

iOS デバイスの **Open In Management** 機能を使用すると、**MDM チャネル**を使用して展開されているアプリ間でのみファイル転送が行われるよう制限できます。 Open In Management の制限は、構成設定で設定され、MDM ソリューションを使用して展開されます。  展開されているアプリをユーザーがインストールすると、管理者が設定した制限が適用されます。

##  <a name="using-app-protection-with-ios-apps"></a>iOS アプリでのアプリ保護の使用
アプリ保護ポリシーは、iOS の **Open in Management** 機能と共に使用して、以下のように会社データを保護できます。

-   **MDM ソリューションで管理されていない従業員所有のデバイス:** アプリ保護ポリシー設定を **[Allow app to transfer data to only Policy Managed apps]\(アプリでポリシー管理型アプリへのデータ転送のみ許可する\)** に設定できます。 ポリシー管理型アプリで Open-In 動作を行うと、その他のポリシー管理型アプリのみが共有対象のオプションとして表示されます。 ネイティブ メールで、ユーザーが OneDrive からポリシー保護ファイルを添付ファイルとして送信すると、そのファイルは読み取り不能になります。

-   **Intune で管理されているデバイス:** Intune で登録したデバイスの場合、アプリ保護ポリシーを使用するアプリと、Intune で展開された管理対象の他の iOS アプリの間で自動的にデータを転送できるようになります。 アプリ保護ポリシーを使用するアプリ間でデータを転送できるようにするには、**[Allow app to transfer data to only managed apps (アプリで管理対象アプリへのデータ転送のみ許可する)]** 設定を有効にします。 **Open in Management** 機能を使用して、Intune で展開されているアプリ間のデータ転送を制御できます。   

-   **サード パーティの MDM ソリューションで管理されているデバイス:** iOS の **Open In Management** 機能を使用して、データ転送が管理対象のアプリに対してのみ行われるよう制限できます。
サードパーティの MDM ソリューションを使用して展開するアプリを、Intune で構成したアプリ保護ポリシーとも関連付けるには、[ユーザー UPN 設定の構成](#configure-user-upn-setting-for-third-party-emm)チュートリアルに従ってユーザー UPN 設定を構成する必要があります。  アプリがユーザー UPN 設定を使用して展開されている場合、エンド ユーザーが職場アカウントを使用してサインインすると、アプリ保護ポリシーがアプリに適用されます。

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Microsoft Intune またはサード パーティ EMM のユーザー UPN 設定を構成する
ユーザー UPN 設定の構成は、Intune またはサード パーティの EMM ソリューションによって管理されているデバイスに**必要**となります。 以下に示す手順では、UPN 設定の一般的な構成方法と、その結果として得られるエンドユーザー エクスペリエンスを示しています。

1.  [Azure Portal](https://portal.azure.com) で、iOS 用の[アプリ保護ポリシーを作成して割り当て](app-protection-policies.md)ます。 企業の要件に合わせてポリシー設定を構成し、このポリシーを使う iOS アプリを選びます。

2.  次の汎用化された手順を使用して、Intune またはサード パーティの MDM ソリューションで管理するアプリとメール プロファイルをデプロイします。 このエクスペリエンスは例 1 でも取り上げています。

3.  次のアプリ構成設定でアプリをデプロイします。

      **キー** = IntuneMAMUPN、**値** = <username@company.com>

      例: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

4.  登録済みデバイスに、Intune またはサード パーティの MDM プロバイダーを使用して **Open in management** ポリシーをデプロイします。


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>例 1: Intune またはサード パーティ MDM コンソールの管理エクスペリエンス

1. Intune またはサード パーティ MDM プロバイダーの管理コンソールに移動します。 登録済みの iOS デバイスにアプリケーション構成設定をデプロイするコンソールのセクションに移動します。

2. [アプリケーションの構成] セクションで、次の設定を入力します。

   **キー** = IntuneMAMUPN、**値** = <username@company.com>

   キー/値ペアの正確な構文は、サード パーティ MDM プロバイダーによって異なります。 次の表は、サードパーティ MDM プロバイダーの例と、キー/値ペアに入力する必要のある正確な値を示します。

|サードパーティ MDM プロバイダー| Configuration キー | 値の種類 | 構成値|
| ------- | ---- | ---- | ---- |
|Microsoft Intune| IntuneMAMUPN | 文字列型 | {{UserPrincipalName}}|
|VMware AirWatch| IntuneMAMUPN | 文字列型 | {UserPrincipalName}|
|MobileIron | IntuneMAMUPN | 文字列型 | ${userUPN} **または** ${userEmailAddress} |
|ManageEngine Mobile Device Manager | IntuneMAMUPN | 文字列型 | %upn% |


### <a name="example-2-end-user-experience"></a>例 2: エンドユーザー エクスペリエンス

1.  エンド ユーザーは、デバイスに Microsoft Word アプリをインストールします。

2.  エンド ユーザーが管理対象のネイティブ メール アプリを起動して、自分の電子メールにアクセスします。

3.  エンド ユーザーがネイティブ メールから Microsoft Word でドキュメントを開こうとします。

4.  Word アプリが起動するとき、エンド ユーザーは職場アカウントを使用してログインするよう求められます。  プロンプトが表示されたときにエンド ユーザーが入力するこの職場アカウントは、Microsoft Word アプリのアプリ構成設定で構成し、指定したアカウントと一致する必要があります。

    > [!NOTE]
    > エンド ユーザーは、私用で Word アプリを使用するときに、個人の作業に使用し、アプリ保護ポリシーの影響を受けない個人アカウントを Word に追加することができます。

5.  ログインが成功すると、アプリの保護ポリシー設定が Word アプリに適用されます。

6.  これでデータ転送が成功し、ドキュメントにはアプリで企業 ID のタグが付けられます。 また、データが作業コンテキスト内で処理されるときには、ポリシー設定が適切に適用されます。

### <a name="validate-user-upn-setting-for-third-party-emm"></a>サードパーティ EMM のユーザー UPN 設定を検証する

ユーザー UPN 設定を構成した後で、iOS アプリが Intune アプリ保護ポリシーを受信して準拠できることを検証する必要があります。

たとえば、**Require app PIN** ポリシー設定はデバイスで簡単に視覚的にテストできます。 ポリシー設定が **[はい]** に設定されている場合、エンド ユーザーが会社のデータにアクセスしようとしたときに PIN の設定または入力を求めるプロンプトが表示されます。

まず、[アプリ保護ポリシーを作成し、iOS アプリに割り当て](app-protection-policies.md)ます。 アプリ保護ポリシーをテストする方法について詳しくは、「[アプリ保護ポリシーを確認する](app-protection-policies-validate.md)」をご覧ください。


### <a name="see-also"></a>関連項目
[Intune アプリ保護ポリシーとは](app-protection-policy.md)
