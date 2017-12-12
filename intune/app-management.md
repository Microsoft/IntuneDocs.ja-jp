---
title: "アプリ管理とは"
titlesuffix: Azure portal
description: "このトピックでは、Microsoft Intune を使用したアプリ管理についての基本を説明します。\""
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 07/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5a1cbd6fc3244686c1f5a1db3e4365e615662f0e
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="what-is-microsoft-intune-app-management"></a>Microsoft Intune アプリの管理とは


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


IT 管理者は、エンド ユーザーのために、業務に必要なアプリへのアクセス手段を確保する必要があります。 これは、以下の理由により、困難になる可能性があります。
- さまざまなデバイス プラットフォームとアプリの種類が存在する。
- 会社のデバイスやユーザー所有のデバイスで、アプリの管理が必要になる場合がある。
- 社内のネットワークとデータの安全性を確保する必要がある。

また、Intune に登録されていないデバイスでアプリの割り当てと管理を行うことも必要になる可能性があります。

Intune では、必要なデバイスで必要なアプリを利用できるように、さまざまな機能を提供しています。

## <a name="app-management-capabilities-by-platform"></a>プラットフォーム別のアプリ管理機能

||||||
|-|-|-|-|-|
|&nbsp; |Android|iOS|Windows Phone 8。1|Windows 10|
|デバイスとユーザーにアプリを追加して割り当てる|[はい]|○|○|[はい]|
|Intune に登録されていないデバイスにアプリを割り当てる|Yes|○|[いいえ]|いいえ|
|アプリ構成ポリシーを使用してアプリのスタートアップ動作を制御する|いいえ|○|[いいえ]|いいえ|
|モバイル アプリ プロビジョニング ポリシーを使用して期限切れのアプリを更新する|いいえ|○|[いいえ]|いいえ|
|アプリ保護ポリシーでアプリ内の会社のデータを保護する|Yes|○|いいえ|×<sup>1</sup>|
|インストール済みのアプリから会社のデータのみを削除する (アプリの選択的ワイプ)|[はい]|○|○|[はい]|
|アプリの割り当てを監視する|[はい]|○|○|Yes|
|アプリ ストアからのボリューム購入アプリを割り当てて追跡する|いいえ|いいえ|[いいえ]|Yes|
|デバイスへのアプリのインストールを強制する (必須)<sup>2</sup>|Yes|○|○|[はい]|
|会社のポータルからデバイスへのオプション インストール (利用可能なインストール)|Yes|○|○|Yes|
|Web 上のアプリへのインストール ショートカット (Web クリップ)|Yes|○|○|Yes|
|社内 (基幹業務) アプリ|[はい]|○|[いいえ]|いいえ|
|ストアからのアプリ|Yes|○|○|Yes|
|アプリを更新する|Yes|○|○|[はい]|

<sup>1</sup> Windows 10 を実行しているデバイスでアプリを保護するには、[Windows 情報保護](windows-information-protection-configure.md)の使用を検討してください。

<sup>2</sup> Intune のみで管理されているデバイスに適用されます。

## <a name="how-to-get-started"></a>開始する方法

アプリに関連するものは、ほとんどが **[Mobile Apps]** ワークロード内にあり、以下の手順でアクセスできます。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[モバイル アプリ]** を選択します。

    ![[モバイル アプリ] ワークロード](./media/apps-workload.png)

### <a name="manage"></a>コンピューターの
- **[アプリ]** - ほとんどのアプリをこのノードで追加、割り当て、監視します。
    - [アプリを追加する](apps-add.md)
    - [アプリを割り当てる](apps-deploy.md)
    - [アプリの監視](apps-monitor.md)
- **[アプリの構成ポリシー]** - ユーザーがアプリを実行するときに必要となる可能性がある設定を指定できます。
    - [iOS アプリ構成ポリシー](app-configuration-policies-use-ios.md)
    - [Android アプリ構成ポリシー](app-configuration-policies-use-android.md)
- **[アプリ保護ポリシー]** - アプリに設定を関連付けて、アプリで使用する会社のデータを保護できます。 たとえば、アプリの機能による他のアプリとの通信を制限することや、会社のアプリにアクセスしようとするユーザーに PIN の入力を求めることができます。
    - [アプリ保護ポリシー](app-protection-policies.md)
- **[アプリの選択的ワイプ]** - 選択したユーザーのデバイスから会社のデータのみを削除します。
    - [アプリの選択的ワイプ](apps-selective-wipe.md)
- **[iOS プロビジョニング プロファイル]** - iOS アプリには、プロビジョニング プロファイルと、証明書によって署名されたコードが含まれます。 証明書の期限が切れると、アプリを実行できなくなります。 Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルのポリシーを事前に割り当てるツールが用意されています。
    - [iOS アプリ プロビジョニング プロファイル](app-provisioning-profile-ios.md)

### <a name="monitor"></a>モニター
- **[ライセンスされたアプリ]** - アプリ ストアからのボリューム購入アプリの表示、割り当て、監視を行います。
    - [ビジネス向け Microsoft ストアのボリューム購入アプリ](windows-store-for-business.md)
- **[検出されたアプリ]** - Intune によって割り当てられ、デバイスにインストールされたすべてのアプリを表示します。
- **[アプリ インストールの状態]** - 作成したアプリの割り当て状態を表示します。
- **[アプリの保護状態]** - 選択したユーザーのアプリ保護ポリシーの状態を表示します。

詳細については、[アプリの監視](apps-monitor.md)に関するページを参照してください。

### <a name="setup"></a>Setup
<!--- **iOS VPP Tokens**
    - [iOS volume-purchased apps](vpp-apps-ios.md) --->
- **[ビジネス向け Microsoft ストア]** - ビジネス向け Microsoft ストアとの統合を設定します。 その後、購入済みのアプリケーションを Intune に同期して割り当て、ライセンスの使用状況を追跡できるようになります。
    - [ビジネス向け Microsoft ストアのボリューム購入アプリ](windows-store-for-business.md)
- **[ポータル サイトのブランド化]** - 会社のポータルをカスタマイズして会社のブランドを付与します。
    - [会社のポータルの構成](company-portal-app.md)
