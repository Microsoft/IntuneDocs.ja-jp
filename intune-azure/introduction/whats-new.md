---
title: "Microsoft Intune プレビューの新機能"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビューの新機能を確認する"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: ffbc91edbdec4abbb5c3c9e28c3b44df03117492
ms.lasthandoff: 02/18/2017

---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Microsoft Intune プレビューの新機能

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

パブリック プレビューの状況や、新しく追加された新機能に関する情報は、こちらで公開します。

## <a name="february-2017"></a>2017 年 2 月

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>モバイル デバイス登録を制限する機能 <!--747600, 795782-->
Intune では、登録を許可されるモバイル デバイス プラットフォームを制御する新しい登録制限が追加されています。 Intune では、モバイル デバイス プラットフォームが iOS、macOS、Android、Windows、Windows Mobile に分かれています。

* モバイル デバイスの登録を制限しても、PC クライアントの登録は制限されません。  
* iOS と Android のみに、個人所有デバイスの登録をブロックする&1; つの追加オプションがあります。

[この記事](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices)で説明されているように、IT 管理者が明示的に会社所有と指定しない限り、Intune はすべての新しいデバイスを個人所有としてマークします。

### <a name="view-all-actions-on-managed-devices---677150--"></a>管理対象デバイスのすべての操作を表示 <!--677150-->
新しい__デバイス操作__レポートには、デバイスでの出荷時の設定にリセットなどのリモート操作を実行したユーザーが表示され、さらにその操作の状態が表示されます。 「[デバイス管理とは](https://docs.microsoft.com/intune-azure/manage-devices/what-is)」を参照してください。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>管理されていないデバイスから割り当てられているアプリにアクセス可能 <!--664691-->
ポータル Web サイトでの設計変更に伴い、iOS と Android ユーザーは、管理されていないデバイスで "登録なしで使用可能" として割り当てられているアプリをインストールできるようになります。 Intune 資格情報を使用して、ユーザーはポータル Web サイトにログインし、割り当てられているアプリの一覧を表示することができます。 "登録なしで使用可能" なアプリのアプリ パッケージは、ポータル Web サイトからダウンロードできます。 この変更は、インストールするために登録が必要なアプリには影響しません。そのようなアプリをインストールする場合は、デバイスの登録が求められます。

### <a name="custom-app-categories---748805--"></a>カスタム アプリのカテゴリ <!--748805-->
Intune に追加するアプリのカテゴリを作成、編集、および割り当てることができるようになりました。 現時点では、カテゴリは英語でのみ指定できます。
[Intune にアプリを追加する方法](/intune-azure/manage-apps/add-apps)に関するページを参照してください。

### <a name="display-device-categories---814654--"></a>デバイス カテゴリを表示する <!--814654-->
デバイスの一覧に、列としてデバイス カテゴリを表示できるようになりました。 デバイスのプロパティー ブレードのプロパティー セクションからカテゴリを編集することもできます。 [Intune にアプリを追加する方法](/intune-azure/manage-apps/add-apps)に関するページを参照してください。 

## <a name="january-2017"></a>2017 年 1 月

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>デバイスの登録に関係なく基幹業務アプリを割り当てられる <!--748823-->
デバイスが Intune に登録されているかどうかに関係なく、基幹業務アプリをストアからユーザーに割り当てられるようになりました。 ユーザーのデバイスが Intune に登録されていない場合は、ポータル サイト アプリではなく、ポータル Web サイトに移動してインストールする必要があります。 [アプリ管理](/intune-azure/manage-apps/what-is-app-management)に関するページを参照してください。

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>デバイスが無効か、管理コンソールとデバイスが通信できない問題を解決
ユーザーのデバイスと Intune の接続が失われるとき、新しいトラブルシューティング手順を指示できます。会社リソースへのアクセスを回復するのに役立ちます。 「[デバイスが無効か、管理コンソールとデバイスが通信できない](/intune-azure/enroll-devices/troubleshoot-device-enrollment#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them)」を参照してください。

## <a name="december-2016-initial-release"></a>2016 年 12 月 (初期リリース)

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Azure Portal のパブリック プレビューでの電気通信経費管理の統合<!--747605-->
Azure Portal では、サード パーティの電気通信経費管理 (TEM) サービスとの統合のプレビューが始められています。 Intune を使用して、国内およびローミングのデータ使用量を制限できます。 これらの統合は、[Saaswedo](http://www.saaswedo.com) で始まっています。 試用テナントでこの機能を有効にする場合は、[Microsoft サポートにお問い合わせください](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

- ストアから iOS、Android、Windows デバイスへのアプリの展開と管理
- iOS、Android、Windows デバイスへの基幹業務 (LOB) アプリの展開と管理
- iOS と Windows デバイスへのボリューム購入アプリの展開と管理
- Android、iOS、Windows デバイス用の Web アプリの展開と管理
- iOS 管理アプリの構成プロファイル
- アプリ保護ポリシーの構成、および Intune に登録されていないデバイスへの基幹業務アプリの展開
- VPN プロファイル、アプリごとの VPN、Wi-Fi、電子メール、証明書プロファイル
- Compliance ポリシー
- Azure AD の条件付きアクセス
- オンプレミス Exchange の条件付きのアクセス
- デバイスの登録
- ロールベースのアクセス制御

## <a name="deprecated-features-in-the-azure-portal"></a>Azure Portal の非推奨の機能

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>ハードウェア識別子の行単位レビューのサポート
Azure Portal では、IMEI 番号と Apple シリアル番号のハードウェア識別子に対する行単位のレビューがサポートされません。 従来の Intune コンソールでは、コンマ区切り値 (.csv) ファイルから詳細情報をインポートし、個別のハードウェア識別子の既存の情報を上書きできます。 Azure Portal には、効率的なオプションが&1; つ用意されており、ハードウェア識別子すべての詳細情報を自動的に上書きするか、既存の識別子の新しい詳細情報を無視することができます。

#### <a name="how-this-affects-you"></a>影響
Azure Portal では、どの International Mobile Equipment Identity (IMEI) デバイスを更新するかを、行単位で決めることができません。 従来の Intune コンソールでは、この機能が引き続きサポートされます。

#### <a name="how-to-get-ready-for-this-change"></a>この変更に対応する方法
この情報は事前に提供します。これにより、変更の影響を受ける場合に、サポート管理者に知らせることができます。 この変更は、2017 年の前半、Azure Portal への移行と同時に行われる予定です。


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Apple DEP での既定の企業デバイス登録プロファイルのサポート
Azure Portal では、Apple Device Enrollment Program (DEP) デバイス シリアル番号に対して、"既定" の業務用デバイス登録プロファイルがサポートされません。 この機能は、従来の Intune コンソールでは使用できますが、プロファイルが意図せず割り当てられることがないように、今後廃止される予定です。 Azure Portal では、Apple DEP アカウントから同期されたシリアル番号に、業務用デバイスの登録プロファイルが最初に割り当てられることはありません。

#### <a name="how-this-affects-you"></a>影響
Azure Portal では、すべての Apple デバイスに対して、既定のプロファイル ポリシーを設定することはできません。 従来の Intune コンソールでは、この機能が引き続きサポートされます。

#### <a name="how-to-get-ready-for-this-change"></a>この変更に対応する方法
この情報は事前に提供します。これにより、変更の影響を受ける場合に、サポート管理者に知らせることができます。 これは、2017 年の前半、Azure Portal への移行と同時に行われる予定です。

