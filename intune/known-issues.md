---
title: "Microsoft Intune の既知の問題"
titlesuffix: Microsoft Intune
description: "Microsoft Intune の既知の問題について説明します。"
keywords: 
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 02efc7e2369c590e2d21ac8c27db54ffbaae38c1
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="known-issues-in-microsoft-intune"></a>Microsoft Intune の既知の問題


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


このトピックでは、Microsoft Intune の既知の問題について説明します。

ここに記載されていないバグを報告する場合は、[サポートを依頼](get-support.md)してください。

Intune への新機能の追加を依頼する場合は、[Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console) サイトでレポートを提出することをご検討ください。

## <a name="migration"></a>移行

### <a name="intune-legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Intune の従来の PC クライアント機能が使用できるのは Silverlight コンソールのみです。

Azure Portal 上の Intune で Windows 10 を管理する機能は、Windows MDM を通して提供されます。 詳細については、「[Azure コンソールと従来の Intune PC クライアントでの Intune](https://docs.microsoft.com/intune-classic/deploy-use/intune-on-azure)」を参照してください。

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>移行中に Intune で作成されるグループは、他の Microsoft 製品の機能に影響する可能性がある

Intune から Azure Portal に移行すると、**All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421** という新しいグループが表示される場合があります。 このグループには、Intune のライセンスを持つユーザーだけでなく、ご利用の Azure Active Directory のすべてのユーザーが含まれます。 このグループを使用すると、一部の既存のユーザーまたは新規ユーザーがどのグループにも属さない場合に、他の Microsoft 製品に関する問題が発生することがあります。

### <a name="status-blades-for-migrated-policies-do-not-work"></a>移行したポリシーの状態を示すブレードが機能しない

クラシック ポータルから移行したポリシーの状態に関する情報は、Azure Portal では表示できません。 ただし、クラシック ポータルではこれらのポリシーに関するレポートを引き続き表示できます。 移行した構成ポリシーの状態に関する情報を表示するには、Azure Portal でポリシーを再作成します。

## <a name="apps"></a>アプリ

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>iOS ボリューム購入アプリが Intune テナントの既定の言語でしか利用できない
iOS ボリューム購入アプリが表示されても、Intune アカウントと同じ国コードに対してしか割り当てることができません。 Intune は、Intune テナント アカウントの国コードと同じ iTunes ロケールのアプリのみを同期します。 たとえば、米国のストアでのみ利用可能なアプリを購入したが、自分の Intune アカウントがドイツ語である場合、Intune ではそのアプリが表示されません。

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>同じ iOS ボリューム購入プログラムの複数のコピーがアップロードされる
同じ VPP トークンで **[アップロード]** ボタンを複数回クリックしないでください。 これにより、重複した VPP トークンがアップロードされ、同じ VPP トークンに対してアプリが複数回同期されます。


<!-- ## Groups -->

## <a name="device-configuration"></a>デバイス構成

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>一部のデバイスで Windows 情報保護ポリシーを保存できない

Intune に登録されていないデバイスでは、Windows 情報保護ポリシー設定の **[Corporate Identify]\(業務用の特定\)** フィールドにプライマリ ドメインのみを指定できます。
(**[詳細設定]** > **[ネットワーク境界]** > **[Add a protected domain]\(保護されているドメインの追加\)** で追加ドメインを追加する場合に、ポリシーを保存できません。 表示されるエラー メッセージは間もなく変更され、より正確な内容となる予定です。

### <a name="cisco-anyconnect-vpn-client-support"></a>Cisco AnyConnect VPN クライアントのサポート

Cisco AnyConnect VPN クライアント (4.0.07072) の最新のリリースは、現在 Intune との互換性がありません。
Intune の今後の更新には、この VPN クライアントのバージョンとの互換性が含まれる予定です。 それまでは、Cisco AnyConnect VPN クライアントを更新せず、既存のバージョンを使い続けることをお勧めします。

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


## <a name="data-protection"></a>データの保護

### <a name="ios-app-protection-policies"></a>iOS アプリの保護ポリシー

登録しなくてもモバイル アプリ管理 (MAM) によって管理されているデバイス上で、ユーザーが利用できる [iOS 用のアプリ保護ポリシー](app-protection-policy-settings-ios.md)を定義できます。 一時的なエラーのため、これらのポリシーは、複数の小数点ではなく、1 つの小数点のバージョンでの iOS バージョンに対してのみ定義できます。 最小バージョンの iOS 10.3.1 を設定するのではなく、iOS 10.3 に対して設定します。 これは、iOS SDK への近日公開予定の更新プログラミングによって解決されます。


## <a name="administration-and-accounts"></a>管理とアカウント

グローバル管理者 (テナント管理者とも呼ばれる) は別個の Intune または Enterprise Mobility Suite (EMS) のライセンスがなくても日常的な管理タスクを引き続き行うことができます。 ただし、自分自身のデバイスの登録、業務用デバイスの登録、Intune ポータル サイトの使用などのサービスを使用するためには、Intune または EMS のライセンスが必要になります。

<!-- ## Additional items -->
