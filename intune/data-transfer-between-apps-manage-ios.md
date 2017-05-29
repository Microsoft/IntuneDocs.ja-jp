---
title: "iOS アプリ間のデータ転送を管理する | Intune Azure プレビュー"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: このトピックを使用すると、iOS の開く機能とモバイル アプリ管理ポリシーを使用してアプリ間のデータ転送を管理する方法を把握できます。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 44747236ba1bda84ccb01f613e1702c536720a2c
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-manage-data-transfer-between-ios-apps"></a>iOS アプリ間のデータ転送を管理する方法
## <a name="manage-ios-apps"></a>iOS アプリを管理する
会社データの保護には、ファイル転送を管理対象のアプリに限定する処理も含まれます。  iOS アプリは次の方法で管理できます。

-   アプリ (**ポリシーで管理されている**アプリと呼ばれます) のアプリ保護ポリシーを構成して、会社データの損失を回避します。 [アプリ保護ポリシーで管理できるすべての Intune 対応アプリに関するページ](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)をご覧ください。

-   また、アプリは **MDM チャネル**から展開して管理することもできます。  これには、デバイスが MDM ソリューションに登録されていることが必要です。 これらは**ポリシーで管理されている**アプリであるか、またはその他の管理対象アプリである必要があります。

iOS デバイスの **Open In Management** 機能を使用すると、**MDM チャネル**を使用して展開されているアプリ間でのみファイル転送が行われるよう制限できます。 Open In Management の制限は、構成設定で設定され、MDM ソリューションを使用して展開されます。  展開されているアプリをユーザーがインストールすると、管理者が設定した制限が適用されます。
##  <a name="using-app-protection-with-ios-apps"></a>iOS アプリでのアプリ保護の使用
アプリ保護ポリシーは、iOS の **Open in Management** 機能と共に使用して、以下のように会社データを保護できます。

-   **MDM ソリューションで管理されていない従業員所有のデバイス:** アプリ保護ポリシー設定を **[Allow app to transfer data to only managed apps (アプリで管理対象アプリへのデータ転送のみ許可する)]** に設定できます。 エンドユーザーは保護されたファイルを、ポリシーで管理されていないアプリで開くことはできません。

-   **Intune で管理されているデバイス:** Intune で登録したデバイスの場合、アプリ保護ポリシーを使用するアプリと、Intune で展開された管理対象の他の iOS アプリの間で自動的にデータを転送できるようになります。 アプリ保護ポリシーを使用するアプリ間でデータを転送できるようにするには、**[Allow app to transfer data to only managed apps (アプリで管理対象アプリへのデータ転送のみ許可する)]** 設定を有効にします。 **Open in Management** 機能を使用して、Intune で展開されているアプリ間のデータ転送を制御できます。   

-   **サード パーティの MDM ソリューションで管理されているデバイス:** iOS の **Open In Management** 機能を使用して、データ転送が管理対象のアプリに対してのみ行われるよう制限できます。
サードパーティの MDM ソリューションを使用して展開するアプリを、Intune で構成したアプリ保護ポリシーとも関連付けるには、[ユーザー UPN 設定の構成](#configure-user-upn-setting-for-third-party-emm)チュートリアルに従ってユーザー UPN 設定を構成する必要があります。  アプリがユーザー UPN 設定を使用して展開されている場合、エンド ユーザーが職場アカウントを使用してサインインすると、アプリ保護ポリシーがアプリに適用されます。

> [!IMPORTANT]
> ユーザー UPN 設定は、サード パーティの MDM によって管理されるデバイスに展開されたアプリに対してのみ必要です。  Intune の管理対象デバイスの場合は、この設定は必要ありません。


## <a name="configure-user-upn-setting-for-third-party-emm"></a>サードパーティ EMM のユーザー UPN 設定を構成する
ユーザー UPN 設定の構成は、サード パーティの EMM ソリューションによって管理されているデバイスに**必要**となります。 以下に示す手順では、UPN 設定の一般的な構成方法と、その結果として得られるエンドユーザー エクスペリエンスを示しています。


1.  [Azure Portal](https://portal.azure.com) で、iOS 用の[アプリ保護ポリシーを作成して割り当て](app-protection-policies.md)ます。 企業の要件に合わせてポリシー設定を構成し、このポリシーを使う iOS アプリを選びます。

2.  次の汎用化された手順を使用して、**サードパーティの MDM ソリューションで**管理するアプリとメール プロファイルをデプロイします。 このエクスペリエンスは例 1 でも取り上げています。

  1.  次のアプリ構成設定でアプリをデプロイします。

      **キー** = IntuneMAMUPN、**値** = <username@company.com>

      例: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

  2.  登録済みデバイスに、サードパーティの MDM プロバイダーを使用して Open in management ポリシーをデプロイします。


### <a name="example-1-admin-experience-in-third-party-mdm-console"></a>例 1: サードパーティ MDM コンソールの管理エクスペリエンス

1. サードパーティ MDM プロバイダーの管理コンソールに移動します。 登録済みの iOS デバイスにアプリケーション構成設定をデプロイするコンソールのセクションに移動します。

2. [アプリケーションの構成] セクションで、次の設定を入力します。

  **キー** = IntuneMAMUPN、**値** = <username@company.com>

  キー/値ペアの正確な構文は、サード パーティ MDM プロバイダーによって異なります。 次の表は、サードパーティ MDM プロバイダーの例と、キー/値ペアに入力する必要のある正確な値を示します。

|サードパーティ MDM プロバイダー| Configuration キー | 値の種類 | 構成値|
| ------- | ---- | ---- | ---- |
|VMware AirWatch| IntuneMAMUPN | 文字列型 | {UserPrincipalName}|
|MobileIron | IntuneMAMUPN | 文字列型 | ${userUPN} **または** ${userEmailAddress} |


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

