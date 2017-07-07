---
title: "Lookout の統合に関するトラブルシューティング"
description: "このトピックでは、Lookout の統合で発生することが多い問題のトラブルシューティングについて説明します"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: cd3c2809161aa438eb7aef91a65d68cb0f657607
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="troubleshoot-lookout-integration-with-intune"></a>Lookout と Intune の統合に関するトラブルシューティング

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

このトピックでは、Lookout Mobile Threat Protection (MTP) のセットアップで発生する可能性がある一般的な問題について説明します。

**ログイン エラー**

## <a name="403-errors"></a>403 エラー
[Lookout MTP コンソール](https://aad.lookout.com)にログインするときに、403 エラー "**サービスにアクセスする権限がありません**" が発生します。これは、指定したユーザー名が、Lookout MTP アクセス用に構成されている Azure Active Directory (AD) グループのメンバーではない場合に発生することがあります。

Lookout MTP は、構成されている Azure AD グループのユーザーのみに、サービスへのアクセスを許可します。 Lookout MTP へのアクセス権を持つように構成されているグループを確認するには、Lookout のサポートに問い合わせてください。

* 電子メール: enterprisesupport@lookout.com
* [MTP コンソール](http://aad.lookout.com)にログインして、**[Support]** (サポート) モジュールに移動します。
* https://enterprise.support.lookout.com/hc/requests にアクセスしてサポートを要求します。

## <a name="unable-to-sign-in"></a>サインインできない
Azure AD グローバル管理者ユーザーが初期 Lookout セットアップを受け入れていない場合、次のエラーが表示されます。

![サインイン エラーを示す Lookout ログイン画面のスクリーンショット](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

この問題を解決するには、グローバル管理者ユーザーが https://aad.lookout.com/les?action=consent にログインし、セットアップを開始するためのメッセージを承認する必要があります。 詳細については、「[Lookout MTP でサブスクリプションをセットアップする](../deploy-use/setup-your-lookout-mtd-subscription.md)」をご覧ください。

**デバイスの状態の問題**

## <a name="device-missing-from-lookout-device-list"></a>Lookout のデバイス リストにデバイスがない

この問題は、次のいずれかのシナリオで発生する可能性があります。
* デバイスのユーザーが、**Lookout MTP コンソール**で指定されている**登録グループ**に含まれません。  [Lookout コンソール](http://aad.lookout.com)で、**[System]** (システム) > **[Intune Connector]** (Intune コネクタ) > **[Enrollment Management]** (登録管理) に移動します。  登録用に構成されている Azure AD グループを確認し、デバイスのユーザーがいずれかの Azure AD グループのメンバーであることを確認します。  ユーザーが登録グループに追加されてから、デバイスが Lookout MTP コンソールの **[Devices]** (デバイス) モジュールに表示されるまでに、最大で構成されているポーリング間隔 (既定値は 5 分) だけかかります。
* デバイスが Lookout MTP でサポートされていない場合。  サポートされていないデバイスは、Lookout MTP コンソールのコネクタ設定の **[Managed Devices]** (管理対象デバイス) セクションに表示されます。

### <a name="device-reported-as-pending"></a>デバイスが**保留中**として報告される

エンド ユーザーが Lookout for Work アプリを開かずに **[Activate]** (アクティブ化) ボタンをタップした場合、デバイスは **[Pending]** (保留中) と表示されます。 Lookout for Work アプリでのデバイスのアクティブ化の詳細については、「[Android デバイスで Lookout for Work のインストールを求められる](http://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)」または「[iOS デバイスで Lookout for Work のインストールを求められる](https://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-ios)」をご覧ください。

## <a name="device-whos-active-but-has-no-device-id"></a>デバイスはアクティブであるがデバイス ID がない
Lookout MTP コンソールでアクティブなデバイスにデバイス ID が表示されない場合は、デバイスのユーザーが登録グループに含まれません。 デバイスのユーザーが登録グループから削除された場合、または登録グループが削除された場合、デバイスはこの状態になる可能性があります。

[Lookout コンソール](http://aad.lookout.com)で、**[System]** (システム) > **[Intune Connector]** (Intune コネクタ) > **[Enrollment]** (登録) に移動し、設定を確認します。  Azure AD グループを確認し、デバイスのユーザーがいずれかの Azure AD グループのメンバーであることを確認します。

デバイスがこの状態にある間、Lookout は検出された脅威をユーザーに通知し続けますが、Intune には脅威情報を送信しません。

## <a name="device-reported-as-disconnected"></a>デバイスが**切断**として報告される

**[Disconnected]** (切断) は、構成されている間隔 (既定は 30 日、最短 7 日) の期間内にデバイスが Lookout MTP と同期されていないことを意味します。 ポータル サイト アプリまたは Lookout for Work アプリがデバイスにありません。 アプリを再インストールすると、この問題は解決します。 ユーザーが Lookout for Work を開いてアプリをアクティブ化すると、デバイスは Lookout MTP および Intune と再同期します。

### <a name="forcing-a-device-sync"></a>デバイスの強制同期
Lookout MTP コンソールの **[Devices]** (デバイス) モジュールで、管理者はデバイスを選択して削除できます。   次にデバイス所有者が Lookout for Work アプリを開いて **[Activate]** (アクティブ化) をタップすると、デバイスの状態は完全に再同期されます。

## <a name="device-has-a-new-user"></a>デバイスに新しいユーザーがいる
デバイスをワイプし、新しいユーザーに登録を要求する必要があります。  [Intune 管理者コンソール](https://manage.microsoft.com)でデバイスを選択して右クリックし、**[インベントリからの削除/ワイプ]** を選択してデバイスを管理から削除します。 デバイスをインベントリから削除した後は、デバイスを削除できます。

![Intune 管理者コンソールのデバイス モジュールの [インベントリからの削除/ワイプ] オプションが表示されたスクリーンショット](../media/mtp/mtp-retire-device-intune-console.png)

または、[Lookout コンソール](http://aad.lookout.com)の **[Devices]** (デバイス) モジュールで **[Delete]** (削除) を選択することもできます。

新しいユーザーが Lookout MTP 登録グループのメンバーである場合、Azure AD がデバイスを新しいユーザーに関連付けるとデバイスが表示されます。

## <a name="compliance-remediation-workflows"></a>コンプライアンス修復のワークフロー
- [Android デバイスで Lookout for Work のインストールを求められる]( http://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)
- [Android デバイスで Lookout for Work が検出した脅威を解決する必要がある](http://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
- [iOS デバイスで Lookout for Work が検出した脅威を解決する必要がある](https://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-ios)


### <a name="see-also"></a>関連項目
[Lookout MTP でサブスクリプションをセットアップする](/intune-classic/deploy-use/set-up-your-subscription-with-lookout-mtp)
