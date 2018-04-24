---
title: Microsoft Intune でのアプリの管理とは
titlesuffix: ''
description: Microsoft Intune でのアプリの管理の基本について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/09/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 86cb0dfb67e81a7abbdc8f38dcbf5539b9855adb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="what-is-microsoft-intune-app-management"></a>Microsoft Intune アプリの管理とは


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune では、IT 管理者が会社の従業員が使用するモバイル アプリを管理することができます。 この機能は、デバイス管理とデータ保護に加え用意されています。 この機能の一部には、優先事項として、作業で使用するアプリにエンドユーザーがアクセスできるようにすることがあります。 これは、以下の理由により、困難になる可能性があります。
- さまざまなデバイス プラットフォームとアプリの種類が存在する。
- 会社のデバイスとユーザー所有のデバイスの両方で、アプリの管理が必要になる場合がある。
- 社内のネットワークとデータの安全性を確保する必要がある。

また、Intune に登録されていないデバイスでアプリの割り当てと管理が必要になる場合もあります。

Intune では、必要なデバイスで必要なアプリを利用できるように、さまざまな機能を提供しています。 次の表に、アプリの管理機能の概要を示します。 表の下には、Azure Portal での Microsoft Intune を理解するための基礎を説明します。

## <a name="app-management-capabilities-by-platform"></a>プラットフォーム別のアプリ管理機能

||||||
|-|-|-|-|-|
|&nbsp; |Android|iOS|Windows Phone 8。1|Windows 10|
|デバイスとユーザーにアプリを追加して割り当てる|はい|はい|はい|はい|
|Intune に登録されていないデバイスにアプリを割り当てる|はい|はい|[いいえ]|[いいえ]|
|アプリ構成ポリシーを使用してアプリのスタートアップ動作を制御する|[いいえ]|はい|[いいえ]|[いいえ]|
|モバイル アプリ プロビジョニング ポリシーを使用して期限切れのアプリを更新する|[いいえ]|はい|[いいえ]|[いいえ]|
|アプリ保護ポリシーでアプリ内の会社のデータを保護する|はい|はい|[いいえ]|×<sup>1</sup>|
|インストール済みのアプリから会社のデータのみを削除する (アプリの選択的ワイプ)|はい|はい|はい|はい|
|アプリの割り当てを監視する|はい|はい|はい|はい|
|アプリ ストアからのボリューム購入アプリを割り当てて追跡する|[いいえ]|[いいえ]|[いいえ]|はい|
|デバイスへのアプリのインストールを強制する (必須)<sup>2</sup>|はい|はい|はい|はい|
|会社のポータルからデバイスへのオプション インストール (利用可能なインストール)|はい|はい|はい|はい|
|Web 上のアプリへのインストール ショートカット (Web リンク)|はい|はい|はい|はい|
|社内 (基幹業務) アプリ|はい|はい|[いいえ]|はい|
|ストアからのアプリ|はい|はい|はい|はい|
|アプリを更新する|はい|はい|はい|はい|

<sup>1</sup> Windows 10 を実行しているデバイスでアプリを保護するには、[Windows 情報保護](windows-information-protection-configure.md)の使用を検討してください。

<sup>2</sup> Intune のみで管理されているデバイスに適用されます。

## <a name="how-to-get-started"></a>開始する方法

アプリに関連するものは、ほとんどが **[Mobile Apps]** ワークロード内にあり、以下の手順でアクセスできます。

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]**、**[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ブレードで、**[モバイル アプリ]** を選びます。

    ![[モバイル アプリ] ワークロード](./media/apps-workload.png)

以下の情報は、**モバイル アプリ** ブレードで使用可能なオプションに対応します。

### <a name="manage"></a>コンピューターの
- **アプリ** - 従業員が使用するアプリの追加、表示、割り当て、監視を行うには、このオプションを選択します。 詳細については、以下の記事を参照してください。
    - [アプリを追加する](apps-add.md)
    - [アプリを割り当てる](apps-deploy.md)
    - [アプリの監視](apps-monitor.md)
- **[アプリの構成ポリシー]** - ユーザーがアプリを実行するときに必要となる可能性がある設定を指定できます。 詳細については、以下の記事を参照してください。
    - [Intune 用アプリ構成ポリシー](app-configuration-policies-overview.md)
        - [iOS アプリ構成ポリシー](app-configuration-policies-use-ios.md)
        - [Android アプリ構成ポリシー](app-configuration-policies-use-android.md)
- **[アプリ保護ポリシー]** - アプリ保護ポリシーを使用して、アプリに設定を関連付けて、アプリで使用する会社のデータを保護できます。 たとえば、アプリの機能による他のアプリとの通信を制限することや、会社のアプリにアクセスしようとするユーザーに PIN の入力を求めることができます。 詳細については、次の各資料を参照してください。
    - [アプリ保護ポリシー](app-protection-policies.md)
- **[アプリの選択的ワイプ]** - 選択したユーザーのデバイスから会社のデータのみを削除します。 詳細については、次の各資料を参照してください。
    - [アプリの選択的ワイプ](apps-selective-wipe.md)
- **[iOS アプリ プロビジョニング プロファイル]** - iOS アプリには、プロビジョニング プロファイルと、証明書によって署名されたコードが含まれます。 証明書の期限が切れると、アプリを実行できなくなります。 Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルのポリシーを事前に割り当てるツールが用意されています。 詳細については、次の各資料を参照してください。
    - [iOS アプリ プロビジョニング プロファイル](app-provisioning-profile-ios.md)

詳細については、[アプリの管理](app-management.md)に関するページをご覧ください。

### <a name="monitor"></a>モニター
- **[アプリ ライセンス]** - アプリ ストアのボリューム購入アプリを表示、割り当て、監視します。 詳細については、以下の記事を参照してください。
    - [iOS ボリューム購入プログラム (VPP) アプリ](vpp-apps-ios.md)
    - [ビジネス向け Microsoft ストアのボリューム購入アプリ](windows-store-for-business.md)
- **[検出されたアプリ]** - Intune によって割り当てられ、デバイスにインストールされたすべてのアプリを表示します。
- **[アプリ インストールの状態]** - 作成したアプリの割り当て状態を表示します。
- **[アプリの保護状態]** - 選択したユーザーのアプリ保護ポリシーの状態を表示します。
- **[監査ログ]** - すべての IT 管理者によって行われた Intune アプリに関連するアクティビティを示します。

詳細については、[アプリの監視](apps-monitor.md)に関するページをご覧ください。

### <a name="setup"></a>Setup
- **[iOS VPP トークン]** - iOS Volume Purchase Program (VPP) のライセンスを適用し、表示します。
    - [iOS 大量購入アプリ](vpp-apps-ios.md)
- **[Windows Enterprise 証明書]** - 基幹業務アプリを管理対象 Windows デバイスに配信するのに使用する、コード署名証明書の状態を適用または表示します。
- **[Windows Symantec 証明書]** - XAP および WP8.x appx ファイルを Windows 10 Mobile デバイスに配布するのに必要な、Symantec コード署名証明書の状態を適用または表示します。
- **[ビジネス向け Microsoft ストア]** - ビジネス向け Microsoft ストアとの統合を設定します。 その後、購入済みのアプリケーションを Intune に同期して割り当て、ライセンスの使用状況を追跡できるようになります。 詳細については、次の各資料を参照してください。
    - [ビジネス向け Microsoft ストアのボリューム購入アプリ](windows-store-for-business.md)
- **[Windows サイドローディング キー]** - アプリを Windows ストアで公開、ダウンロードするのではなく、直接デバイスにインストールするのに使用可能な Windows サイドローディング キーを追加できます。 詳細については、次の各資料を参照してください。
    - [Windows アプリのサイドローディング](app-sideload-windows.md)
- **[ポータル サイトのブランド化]** - 会社のポータルをカスタマイズして会社のブランドを付与します。 詳細については、次の各資料を参照してください。
    - [会社のポータルの構成](company-portal-app.md)
- **[アプリのカテゴリ]** - アプリのカテゴリ名を追加、ピン留め、削除します。
- **[Android for Work]** - 企業で承認されたアプリを承認して同期します。 詳細については、次の各資料を参照してください。
    - [Android for Work アプリ](apps-add-android-for-work.md)

### <a name="help-and-support"></a>ヘルプとサポート
- **[ヘルプとサポート]** - トラブルシューティング、リクエスト サポート、または Intune の状態の表示を行います。 詳細については、次の各資料を参照してください。
    - [問題のトラブルシューティング](help-desk-operators.md)

## <a name="next-steps"></a>次の手順

- [アプリを Microsoft Intune に追加する方法](apps-add.md)
