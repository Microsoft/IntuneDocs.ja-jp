---
title: "Lookout の統合に関するトラブルシューティング | Microsoft Intune"
description: "このトピックでは、Lookout の統合で発生することが多い問題のトラブルシューティングについて説明します"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0736b5f24065f55d8fbd312395e4bb7226ebf619
ms.openlocfilehash: 5acf5c707a93aa0b5e7cefdcb0b160af09b9cf70


---

# Lookout と Intune の統合に関するトラブルシューティング
このトピックでは、Lookout Mobile Threat Protection (MTP) のセットアップで発生する可能性がある一般的な問題について説明します。
## ログイン エラーのトラブルシューティング
### 403 エラー
[Lookout MTP コンソール](https://aad.lookout.com)にログインするときに、403 エラーが発生することがあります。**サービスにアクセスする権限がありません**。これは、指定したユーザー名が、Lookout MTP アクセス用に構成されている Azure Active Directory (Azure AD) グループのメンバーではない場合に発生することがあります。

Lookout MTP は、アクセス権を持つように構成されている Azure AD グループのユーザーのみを許可するように構成されています。 Lookout MTP へのアクセス権を持つように構成されているグループがわからない場合は、Lookout のサポートに問い合わせてください。

Lookout のサポートには次の方法で連絡できます。

* 電子メール: enterprisesupport@lookout.com
* [MTP コンソール](http://aad.lookout.com)にログインして、**[Support]** (サポート) モジュールに移動します。
* https://enterprise.support.lookout.com/hc/en-us/requests にアクセスしてサポートを要求します。

### サインインできない
Azure AD グローバル管理者ユーザーが初期 Lookout セットアップを受け入れていない場合、次のエラーが表示されることがあります。

![サインイン エラーを示す Lookout ログイン画面のスクリーンショット](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

この問題を解決するには、グローバル管理者ユーザーが https://aad.lookout.com/les?action=consent にログインし、セットアップを開始するためのメッセージを承認する必要があります。 詳細については、「[Lookout MTP でサブスクリプションをセットアップする](set-up-your-subscription-with-lookout-mtp.md)」をご覧ください。

## デバイスの状態の問題のトラブルシューティング

### Lookout MTP コンソールのデバイス リストにデバイスが表示されない

この問題は、次のいずれかのシナリオで発生する可能性があります。
* そのデバイスの所有ユーザーが、**Lookout MTP コンソール**で指定されている**登録グループ**に含まれない場合。  **[System]** (システム) モジュールの **[Intune Connector]** (Intune コネクタ) タブで、**[Enrollment Management]** (登録管理) の設定を確認します。  1 つ以上の Azure AD グループが登録用に構成されている必要があります。  表示されないデバイスを所有するユーザーが、指定されているいずれかの Azure AD グループのメンバーであることを確認します。  登録グループに追加された新しいユーザーが、Lookout MTP コンソールの **[Devices]** (デバイス) モジュールに表示されるまでに、最大で構成されているポーリング間隔 (既定値は 5 分) だけかかります。

* デバイスが Lookout MTP でサポートされていない場合。  サポートされていないデバイスは、Lookout MTP コンソールのコネクタ設定の **[Managed Devices]** (管理対象デバイス) セクションに表示されます。

### デバイスが**保留中**と表示され続ける

デバイスが **[Pending]** (保留中) と表示される場合は、エンド ユーザーが Lookout for Work アプリを開いて **[Activate]** (アクティブ化) ボタンをタップしていないことを意味します。 Lookout for Work アプリによるデバイスのアクティブ化の詳細については、次のトピックをご覧ください。

[Android デバイスで Lookout for Work のインストールを求められる ](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

### Lookout MTP コンソールでアクティブと表示されているデバイスに、デバイス ID がない。  
これは、そのデバイスの所有ユーザーが Lookout MTP コンソールで指定されている登録グループに含まれていないことを意味します。   デバイスを所有するユーザーが登録グループから削除された場合、またはユーザーが属している登録グループが削除された場合、デバイスはこの状態になる可能性があります。

Lookout MTP コンソールの **[System]** (システム) モジュールの **[Intune Connector]** (Intune コネクタ) タブで、**[Enrollment]** (登録) の設定を確認します。  1 つ以上の Azure AD グループが登録用に構成されている必要があります。  デバイスを所有するユーザーが、指定されているいずれかの Azure AD グループのメンバーであることを確認します。  

デバイスがこの状態にある間、Lookout は検出された脅威をユーザーに通知し続けますが、Intune には脅威情報を送信しません。

### デバイスが切断状態を示す

切断とは、MTP が構成されている期間 (既定値は 30 日、最小は 7 日) 中にデバイスからのハートビートを受信しなかったことを意味します。 これは、ポータル サイト アプリまたは Lookout for Work アプリがデバイスにインストールされていないか、アンインストールされたことを示します。 アプリを再インストールすると、この問題は解決します。 ユーザーが Lookout for Work を開いてアプリをアクティブ化すると、デバイスは Lookout MTP および Intune と再同期します。    

### デバイスの強制的な再同期
Lookout MTP コンソールの **[Devices]** (デバイス) モジュールで、管理者はデバイスを選択して削除できます。   次にデバイス所有者が Lookout for Work アプリを開いて **[Activate]** (アクティブ化) をタップすると、デバイスの状態は完全に再同期されます。

### デバイスの所有者がこのデバイスを使用しなくなった
デバイスをワイプし、新しいユーザーに登録を要求する必要があります。  [Intune 管理者コンソール](https://manage.microsoft.com)でデバイスを選択して右クリックし、**[インベントリからの削除/ワイプ]** を選択してデバイスを管理から削除します。 デバイスをインベントリから削除した後は、デバイスを削除できます。

![Intune 管理者コンソールのデバイス モジュールの [インベントリからの削除/ワイプ] オプションが表示されたスクリーンショット](../media/mtp/mtp-retire-device-intune-console.png)

または、Lookout MTP コンソールの **[Devices]** (デバイス) モジュールで **[Delete]** (削除) を選択することもできます。  

新しいユーザーが Lookout MTP コンソールで指定されているいずれかの登録グループのメンバーである場合、Azure AD がデバイスを新しいユーザーに関連付けるとデバイスが表示されます。

## コンプライアンス修復のワークフロー
[Android デバイスで Lookout for Work のインストールを求められる]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

[Android デバイスで Lookout for Work が検出した脅威を解決する必要がある ](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)


### 関連項目
[Lookout MTP でサブスクリプションをセットアップする](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-your-subscription-with-lookout-mtp)



<!--HONumber=Oct16_HO1-->


