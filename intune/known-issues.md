---
title: Microsoft Intune - Azure の既知の問題 | Microsoft Docs
description: Microsoft Intune の既知の問題について説明します。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 08/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: db655c49277051267036d76e518cc870757f67c2
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183045"
---
# <a name="known-issues-in-microsoft-intune"></a>Microsoft Intune の既知の問題


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事では、Microsoft Intune の既知の問題について説明します。

ここに記載されていないバグを報告する場合は、[サポートを依頼](get-support.md)してください。

Intune への新機能の追加を依頼する場合は、[Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console) サイトでレポートを提出することをご検討ください。

## <a name="migration"></a>移行

### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal"></a>Azure クラシック ポータルのコンプライアンス ポリシーをエクスポートして、Intune Azure portal でこれらのポリシーを再作成する

Azure クラシック ポータルで作成されたコンプライアンス ポリシーは非推奨になる予定です。 既存のコンプライアンス ポリシーは確認したり、削除したりできますが、更新することはできません。 現在の Intune Azure portal に任意のコンプライアンス ポリシーを移行する必要がある場合は、コンマ区切りファイル (.csv ファイル) としてポリシーをエクスポートできます。 その後、ファイルの詳細を使って、Intune Azure portal でこれらのポリシーを再作成します。

> [!IMPORTANT]
> Azure クラシック ポータルが廃止されると、ご自分のコンプライアンス ポリシーにアクセスしたり、表示したりすることはできなくなります。 そのため、Azure クラシック ポータルが廃止される前に、必ずご利用のポリシーをエクスポートし、Azure portal で再作成してください。

### <a name="intune-legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Intune の従来の PC クライアント機能が使用できるのは Silverlight コンソールのみです。

Azure Portal 上の Intune で Windows 10 を管理する機能は、Windows MDM を通して提供されます。 詳細については、「[Azure コンソールと従来の Intune PC クライアントでの Intune](https://docs.microsoft.com/intune-classic/deploy-use/intune-on-azure)」を参照してください。

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>移行中に Intune で作成されるグループは、他の Microsoft 製品の機能に影響する可能性がある

Intune から Azure Portal に移行すると、**All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421** という新しいグループが表示される場合があります。 このグループには、Intune のライセンスを持つユーザーだけでなく、ご利用の Azure Active Directory のすべてのユーザーが含まれます。 このグループを使用すると、一部の既存のユーザーまたは新規ユーザーがどのグループにも属さない場合に、他の Microsoft 製品に関する問題が発生することがあります。

### <a name="status-blades-for-migrated-policies-do-not-work"></a>移行したポリシーの状態を示すブレードが機能しない

Azure クラシック ポータルから移行したポリシーの状態に関する情報は、Azure Portal では表示できません。 ただし、クラシック ポータルではこれらのポリシーに関するレポートを引き続き表示できます。 移行した構成ポリシーの状態に関する情報を表示するには、Azure Portal でポリシーを再作成します。

## <a name="apps"></a>アプリ


### <a name="multiple-app-install-prompts-for-certain-vpp-apps"></a>特定の VPP アプリについてアプリのインストール プロンプトが複数回表示される
エンド ユーザー デバイスに既にインストールされている特定の VPP アプリについて、アプリのインストール プロンプトが複数回表示されることがあります。 この問題は、Intune Azure Portal にアップロードした VPP トークンの **[アプリの自動更新]** オプションが **[オン]** に設定されている場合に発生します。    

この問題を回避するには、VPP トークンの **[アプリの自動更新]** オプションを無効にします。 この操作を行うには、Azure Portal で Microsoft Intune を開きます。 Intune から **[クライアント アプリ]** > **[iOS VPP トークン]** の順に選択します。 次に、影響を受けるアプリを展開した VPP トークンを選択し、**[編集]** > **[アプリの自動更新]** > **[オフ]** > **[保存]** の順に選択します。 また、影響を受けるアプリケーションの VPP アプリケーションとしての展開を停止する方法もあります。この操作でプロンプトは表示されなくなります。    

これは、現在のリリースで既知の問題です。 今後、この問題を解決する修正プログラムがリリースされる予定です。 修正が実装された場合、アプリのインストール プロンプトが複数回表示されることはなくなります。

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>iOS ボリューム購入アプリが Intune テナントの既定の言語でしか利用できない
iOS ボリューム購入アプリが表示されても、Intune アカウントと同じ国コードに対してしか割り当てることができません。 Intune は、Intune テナント アカウントの国コードと同じ iTunes ロケールのアプリのみを同期します。 たとえば、米国のストアでのみ利用可能なアプリを購入したが、自分の Intune アカウントがドイツ語である場合、Intune ではそのアプリが表示されません。

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>同じ iOS ボリューム購入プログラムの複数のコピーがアップロードされる
同じ VPP トークンで **[アップロード]** ボタンを複数回クリックしないでください。 これにより、重複した VPP トークンがアップロードされ、同じ VPP トークンに対してアプリが複数回同期されます。

### <a name="some-managed-browser-traffic-not-routed-through-azure-app-proxy----2463492---"></a>一部の管理対象ブラウザーのトラフィックが Azure App プロキシ経由でルーティングされない <!-- 2463492 -->
特定の第 3 のトラフィック (javascript や AJAX コールなど) が Azure App プロキシ経由でルーティングされないという、管理対象ブラウザーとアプリ プロキシの統合に関する既知の問題があります。 これは、現在のリリースで既知の問題です。  

<!-- ## Groups -->

## <a name="device-configuration"></a>デバイス構成

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>一部のデバイスで Windows 情報保護ポリシーを保存できない

Intune に登録されていないデバイスでは、Windows 情報保護ポリシー設定の **[Corporate Identify]\(業務用の特定\)** フィールドにプライマリ ドメインのみを指定できます。
(**[詳細設定]** > **[ネットワーク境界]** > **[Add a protected domain]\(保護されているドメインの追加\)** で追加ドメインを追加する場合に、ポリシーを保存できません。 表示されるエラー メッセージは間もなく変更され、より正確な内容となる予定です。

### <a name="cisco-anyconnect-and-cisco-legacy-anyconnect-vpn-client-support---ios"></a>Cisco AnyConnect と Cisco Legacy AnyConnect VPN クライアントのサポート - iOS

iOS デバイスでは、ネットワーク アクセス制御 (NAC) 統合は新しい Cisco AnyConnect クライアントに対応していません。 NAC 統合を提供できるように、Cisco と協力しています。

[Intune での VPN プロファイルの作成](vpn-settings-ios.md)に関するページでは、Cisco AnyConnect クライアントと Cisco Legacy AnyConnect クライアントの詳細について説明しています。

### <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>macOS Sierra デバイスで数字のパスワードを使用する

現在、macOS Sierra デバイスのデバイス制限プロファイルで **[必要なパスワードの種類]** に **[数字]** を選択すると、**[英数字]** が強制的に適用されます。 これらのデバイスで数字のパスワードを使用する場合は、この設定を構成しないでください。
この問題は、macOS の今後のバージョンで修正される可能性があります。

これらの設定の詳細については、「[Microsoft Intune での macOS デバイスの制限設定](device-restrictions-macos.md)」をご覧ください。

## <a name="compliance"></a>コンプライアンス

### <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>Intune のコンプライアンス ポリシーが新しいコンソールに表示されない

クラシック Intune ポータルで作成したコンプライアンス ポリシーは移行できますが、Azure Portal では設計が変更されているため、Azure Portal には表示されません。 Intune クラシック ポータルで作成したコンプライアンス ポリシーは依然として有効ですが、ポリシーの表示や編集はクラシック ポータル上で行う必要があります。

また、Azure Portal で作成した新しいコンプライアンス ポリシーは、クラシック ポータル上には表示されません。

詳細については、「[Intune Azure プレビューでのデバイス コンプライアンスとは](device-compliance.md)」を参照してください。

<!-- ## Enrollment -->

## <a name="conditional-access"></a>条件付きアクセス

### <a name="conditional-access-settings-from-intune-do-not-show-up-in-new-console"></a>Intune の条件付きアクセスの設定が新しいコンソールに表示されない

ご利用のテナントが Azure portal に移行された後、その条件付きアクセスの設定は引き続き適用されます。ただし、それらの設定は Azure Intune ポータルに表示されません。 

条件付きアクセスの設定を Azure portal で表示して管理したい場合は、クラシック ポータルから以前の設定を削除し、それらを Azure portal で再作成する必要があります。 

詳細については、「[Azure Active Directory の条件付きアクセスのベスト プラクティス](https://docs.microsoft.com/azure/active-directory/conditional-access/best-practices)」を参照してください。

## <a name="data-protection"></a>データの保護

### <a name="ios-app-protection-policies"></a>iOS アプリの保護ポリシー

登録しなくてもモバイル アプリ管理 (MAM) によって管理されているデバイス上で、ユーザーが利用できる [iOS 用のアプリ保護ポリシー](app-protection-policy-settings-ios.md)を定義できます。 一時的なエラーのため、これらのポリシーは、複数の小数点ではなく、1 つの小数点のバージョンでの iOS バージョンに対してのみ定義できます。 最小バージョンの iOS 10.3.1 を設定するのではなく、iOS 10.3 に対して設定します。 これは、iOS SDK への近日公開予定の更新プログラミングによって解決されます。


## <a name="administration-and-accounts"></a>管理とアカウント

グローバル管理者 (テナント管理者とも呼ばれる) は別個の Intune または Enterprise Mobility Suite (EMS) のライセンスがなくても日常的な管理タスクを引き続き行うことができます。 ただし、自分自身のデバイスの登録、業務用デバイスの登録、Intune ポータル サイトの使用などのサービスを使用するためには、Intune または EMS のライセンスが必要になります。

<!-- ## Additional items -->
