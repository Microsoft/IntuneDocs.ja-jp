---
title: "Microsoft Intune プレビューの新機能"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビューの新機能を確認する"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: 92bb81440b9374b2b0b433b32fc0a1301998ea80
ms.lasthandoff: 03/15/2017

---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Microsoft Intune プレビューの新機能

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

パブリック プレビューの状況や、新しく追加された新機能に関する情報は、こちらで公開します。

> [!Note]
> Azure Portal プレビューについて、このページに記載されている変更が展開されます。 ただし、Intune サービスの更新方法により、変更はすぐに入手できない場合があります。  新しいポータル機能を入手できるようになる前に、サービスのいくつかのコンポーネントを順次更新する必要があります。 今後、今月ロールアウトされる変更を随時ご確認ください。

## <a name="march-2017"></a>2017 年 3 月

### <a name="support-for-ios-lost-mode---431695--"></a>iOS 紛失モードのサポート<!--431695-->

iOS 9.3 以降のデバイスについて、Intune で**紛失モード**のサポートが追加されました。 デバイスをロックダウンしてすべての使用を回避し、デバイスのロック画面のメッセージおよび連絡先の電話番号を表示できるようになりました。

エンドユーザーは、管理者が紛失モードを無効にするまで、デバイスのロックを解除することはできません。 紛失モードを有効にした場合、デバイスを探索するアクションを使用して、Intune コンソールでマップ上にデバイスの地理的な場所を表示することができます。

詳細については、「[Microsoft Intune デバイスの管理とは](/intune-azure/manage-devices/what-is)」を参照してください。

### <a name="improvements-to-device-actions-report---677150--"></a>Device Actions レポートの機能強化 <!--677150-->

Device Actions レポートの機能が強化され、パフォーマンスが向上しました。 さらに、レポートを状態別にフィルター処理できるようになりました。 たとえば、レポートをフィルター処理して、完了したデバイス アクションのみを表示できます。

### <a name="actions-for-non-compliance---730266--"></a>コンプライアンス非対応に対するアクション <!--730266-->

**コンプライアンス非対応に対するアクション**は、コンプライアンス非対応のデバイスに対してアクションを実行できるようにするコンプライアンス ポリシーの新しい機能です。 単一または複数のアクションを指定できます。また、実行する必要があるアクションの期間を指定することもできます。 たとえば、デバイスが非対応になった直後に電子メールで、その非対応デバイスのユーザーに通知することができます。あるいは、非対応デバイスに対して、条件付きアクセスで 3 日間の猶予期間後の企業リソースへのアクセスをブロックすることができます。

### <a name="custom-app-categories---748805--"></a>カスタム アプリのカテゴリ <!--748805-->

Intune に追加するアプリのカテゴリを作成、編集、および割り当てることができるようになりました。 現時点では、カテゴリは英語でのみ指定できます。
[Intune にアプリを追加する方法](/intune-azure/manage-apps/add-apps)に関するページを参照してください。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>登録していないデバイスを使用しているユーザーに LOB アプリを割り当てる <!--748823-->

デバイスが Intune に登録されているかどうかに関係なく、基幹業務アプリをストアからユーザーに割り当てられるようになりました。 ユーザーのデバイスが Intune に登録されていない場合は、ポータル サイト アプリではなく、ポータル Web サイトに移動してインストールする必要があります。

### <a name="new-compliance-reports---846671--"></a>新しいコンプライアンス レポート <!--846671-->

コンプライアンス レポートにより、会社内のコンプライアンスの状況を表示して、社内のユーザーがコンプライアンス関連の問題に直面したときに迅速にトラブルシューティングできるようになりました。 次の情報を表示できます。

- デバイスの総合的なコンプライアンスの状態
- 設定別のコンプライアンスの状態
- ポリシー別のコンプライアンスの状態

これらのレポートを使用して個々のデバイスをドリルダウンし、そのデバイスに影響を与えている特定の設定およびポリシーを確認することもできます。

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->

Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure プレビュー ポータルの Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューはクラシックの Intune ポータルのリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントでプレビューにアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。


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

### <a name="configure-windows-update-for-business-settings---776716--"></a>ビジネス設定向けの Windows Update の構成<!--776716-->

サービスとしての Windows は、Windows 10 の更新プログラムを提供するための新しい方法です。 Windows 10 以降、すべての新しい機能更新プログラムと品質更新プログラムには、以前の更新プログラムすべての内容が含まれます。 つまり、最新の更新プログラムをインストールしている限り、Windows 10 デバイスが完全に最新の状態であることを把握できます。 以前のバージョンの Windows とは異なり、更新プログラムの一部ではなく全体をインストールすることが必要になります。

Windows Update for Business を使用することで、デバイスのグループに対して個々の更新プログラムを承認する必要がなくなるため、更新プログラム管理エクスペリエンスを簡略化できます。 更新プログラムの展開戦略を構成することで環境内のリスクを引き続き管理でき、さらに Windows Update により更新プログラムが適切なタイミングでインストールされるようになります。 Microsoft Intune では、デバイスでの更新プログラムの設定を構成でき、また更新プログラムのインストールを遅らせることができます。 Intune では更新プログラムは格納されず、更新プログラムのポリシー割り当てのみが格納されます。 デバイスは更新プログラムのため Windows Update に直接アクセスします。**Windows 10 更新プログラム リング**を構成し管理するには Intune を使用します。 更新プログラム リングには、Windows 10 更新プログラムがインストールされるタイミングと方法を構成する設定のグループが含まれています。 詳しくは、「[ビジネス設定向けの Windows Update の構成](/intune-azure/configure-devices/how-to-configure-windows-update-for-business)」をご覧ください。

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

