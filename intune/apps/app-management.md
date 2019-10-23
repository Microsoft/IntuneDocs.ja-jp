---
title: Microsoft Intune でのアプリの管理とは
titleSuffix: ''
description: Microsoft Intune のプラットフォームでクライアント アプリを管理する機能について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 56814550cae814bd89d55a6f72df98dd24df4caf
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507464"
---
# <a name="what-is-microsoft-intune-app-management"></a>Microsoft Intune アプリの管理とは


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune を使用すれば、IT 管理者として、会社の従業員が使用するクライアント アプリを管理することができます。 この機能は、デバイス管理とデータ保護に加え用意されています。 管理者の優先事項の 1 つは、エンド ユーザーが仕事を行う上で必要なアプリに確実にアクセスできるようにすることです。 この目標を達成するには以下の理由により、課題があります。
- さまざまなデバイス プラットフォームとアプリの種類が存在する。
- 会社のデバイスとユーザーの個人デバイスの両方で、アプリの管理が必要になる場合がある。
- 社内のネットワークとデータの安全性を確保する必要がある。

また、Intune に登録されていないデバイスでアプリの割り当てと管理が必要になる場合もあります。

## <a name="mobile-application-management-mam-basics"></a>モバイル アプリケーション管理 (MAM) の基本

[Intune モバイル アプリケーション管理](app-lifecycle.md)とは、ユーザーのモバイル アプリの公開、プッシュ、構成、セキュリティ保護、監視、および更新を可能にする一連の Intune 管理機能のことです。

MAM を使用すると、アプリケーション内の組織のデータを管理および保護することができます。 **登録を必要としない MAM** (MAM-WE) を使用すると、機密データが含まれる職場または学校関連のアプリを、**Bring Your Own Device** (BYOD) シナリオにおける個人用デバイスを含む、ほぼすべての[デバイス](app-management.md#app-management-capabilities-by-platform)で管理できます。 Microsoft Office アプリなどの多くの仕事効率化アプリを、Intune MAM で管理することができます。 一般使用が可能な [Microsoft Intune によって保護されたアプリ](apps-supported-intune-apps.md)の公式一覧を参照してください。

Intune MAM では次の 2 つの構成をサポートしています。
- **Intune MDM + MAM**: IT 管理者は、Intune モバイル デバイス管理 (MDM) に登録されているデバイスで MAM とアプリ保護ポリシーを使用したアプリの管理のみを行うことができます。 MDM と MAM を使用してアプリを管理するには、Azure Portal (https://portal.azure.com ) の Intune コンソールを使用する必要があります。
- **デバイス登録なしの MAM**: デバイス登録がない MAM や MAM-WE では、IT 管理者は、Intune MDM に登録されていないデバイス上で MAM とアプリ保護ポリシーを使用してアプリの管理を行うことしかできません。 つまり、サードパーティ EMM プロバイダーに登録されているデバイスで Intune によりアプリを管理できます。 MAM-WE を使用してアプリを管理するには、Azure Portal (https://portal.azure.com ) の Intune コンソールを使用する必要があります。 また、Intune では、サードパーティ製エンタープライズ モビリティ管理 (EMM) プロバイダーに登録されているデバイス上でも、MDM に全く登録されていないデバイス上でもアプリを管理することができます。 BYOD および Microsoft の EMS に関する詳細については、「[Microsoft Enterprise Mobility + Security (EMS) で BYOD を有効にするための技術の決定事項](../fundamentals/byod-technology-decisions.md)」を参照してください。

## <a name="app-management-capabilities-by-platform"></a>プラットフォーム別のアプリ管理機能

Intune では、アプリを実行するデバイス上で必要なアプリを取得するのに役立つさまざまな機能を提供しています。 次の表に、アプリの管理機能の概要を示します。

|  | Android/Android Enterprise | iOS | macOS | Windows 10 | Windows Phone 8.1 |
|-------------------------------------------------------------------------------------|---------|-----|-------|------------|-------------------|
| デバイスとユーザーにアプリを追加して割り当てる | はい | はい | はい | はい | はい |
| Intune に登録されていないデバイスにアプリを割り当てる | はい | はい | いいえ | [いいえ] | [いいえ] |
| アプリ構成ポリシーを使用してアプリのスタートアップ動作を制御する | はい | はい | いいえ | [いいえ] | [いいえ] |
| モバイル アプリ プロビジョニング ポリシーを使用して期限切れのアプリを更新する | [いいえ] | はい | いいえ | [いいえ] | [いいえ] |
| アプリ保護ポリシーでアプリ内の会社のデータを保護する | はい | はい | [いいえ] | いいえ <sup>1</sup> | [いいえ] |
| インストール済みのアプリから会社のデータのみを削除する (アプリの選択的ワイプ) | はい | はい | いいえ | はい | はい |
| アプリの割り当てを監視する | はい | はい | はい | はい | はい |
| アプリ ストアからのボリューム購入アプリを割り当てて追跡する | [いいえ] | [いいえ] | [いいえ] | はい | [いいえ] |
| デバイスへのアプリのインストールを強制する (必須) <sup>2</sup> | はい | はい | はい | はい | はい |
| 会社のポータルからデバイスへのオプション インストール (利用可能なインストール) | はい <sup>3</sup> | はい | はい | はい | はい |
| Web 上のアプリへのインストール ショートカット (Web リンク) | はい <sup>4</sup> | はい | はい | はい | はい |
| 社内 (基幹業務) アプリ | はい | はい | はい | はい | [いいえ] |
| ストアからのアプリ | はい | はい | いいえ | はい | はい |
| アプリを更新する | はい | はい | いいえ | はい | はい |

<sup>1</sup> Windows 10 を実行しているデバイスでアプリを保護するには、[Windows 情報保護](../protect/windows-information-protection-configure.md)の使用を検討してください。<br>
<sup>2</sup> Intune のみで管理されているデバイスに適用されます。<br>
<sup>3</sup> Intune では、Android Enterprise デバイス上にあるマネージド Google Play ストアから入手できるアプリがサポートされます。<br>
<sup>4</sup> Intune では、標準の Android Enterprise デバイス上にアプリへのショートカットを Web リンクとしてインストールする機能は提供されていません。 ただし、[複数アプリ専用の Android Enterprise デバイス](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings)では、Web リンクのサポートが提供されています。 


## <a name="get-started"></a>作業開始

アプリに関連する情報は、ほとんどが **[クライアント アプリ]** ワークロード内にあり、以下の手順でアクセスできます。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
3. **[Microsoft Intune]** ウィンドウで、 **[クライアント アプリ]** を選択します。

    ![[クライアント アプリ] ワークロード ウィンドウ](./media/app-management/apps-workload.png)

次の 4 つのセクションでは、 **[クライアント アプリ]** ウィンドウで使用可能なオプションについて説明します。

### <a name="manage"></a>コンピューターの
- **[アプリ]** :従業員が使用するアプリの追加、表示、割り当て、監視を行うには、このオプションを選択します。 詳細については、次をご覧ください。
  - [アプリを追加する](apps-add.md)。
  - [アプリを割り当てる](apps-deploy.md)。
  - [アプリを監視する](apps-monitor.md)。
- **[アプリ構成ポリシー]** :ユーザーがアプリを実行するときに必要となる場合がある設定を指定するには、このオプションを選択します。 詳細については、次をご覧ください。
  - [Intune 用アプリ構成ポリシー](app-configuration-policies-overview.md)。
    - [iOS アプリ構成ポリシー](app-configuration-policies-use-ios.md)。
    - [Android アプリ構成ポリシー](app-configuration-policies-use-android.md)。
- **[アプリ保護ポリシー]** :このオプションを選択すると、アプリに設定を関連付けて、使用される会社のデータを保護できます。 たとえば、アプリの機能による他のアプリとの通信を制限することや、会社のアプリにアクセスしようとするユーザーに PIN の入力を求めることができます。 詳細については、次をご覧ください。
  - [アプリ保護ポリシー](app-protection-policies.md)。
- **[アプリの選択的ワイプ]** :このオプションを選択すると、選択したユーザーのデバイスから会社のデータのみを削除することができます。 詳細については、次をご覧ください。
  - [アプリの選択的ワイプ](apps-selective-wipe.md)。
- **[iOS アプリ プロビジョニング プロファイル]** : iOS アプリには、プロビジョニング プロファイルと、証明書によって署名されたコードが含まれます。 証明書の期限が切れると、アプリを実行できなくなります。 Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルのポリシーを事前に割り当てるツールが用意されています。 詳細については、次をご覧ください。
  - [iOS アプリ プロビジョニング プロファイル](app-provisioning-profile-ios.md)。

このセクションの詳細については、[アプリの管理](app-management.md)に関するページを参照してください。

### <a name="monitor"></a>モニター
- **[アプリ ライセンス]** :アプリ ストアのボリューム購入アプリを表示、割り当て、監視します。 詳細については、次をご覧ください。
  - [iOS ボリューム購入プログラム (VPP) アプリ](vpp-apps-ios.md)。
  - [ビジネス向け Microsoft ストアのボリューム購入アプリ](windows-store-for-business.md)。
- **[検出されたアプリ]** :Intune によって割り当てられたか、デバイスにインストールされたアプリを表示します。 詳細については、「[Intune discovered apps (Intune で検出されたアプリ)](app-discovered-apps.md)」を参照してください。
- **[アプリ インストールの状態]** :作成したアプリ割り当ての状態を表示します。 詳しくは、「[Microsoft Intune でアプリの情報と割り当てを監視する](apps-monitor.md#device-and-user-status-graphs)」をご覧ください。
- **[アプリの保護状態]** :選択したユーザーのアプリ保護ポリシーの状態を表示します。
- **[監査ログ]** :すべての IT 管理者の Intune アプリに関連するアクティビティを表示します。

このセクションの詳細については、[アプリの管理](apps-monitor.md)に関するページを参照してください。

### <a name="set-up"></a>設定
- **[iOS VPP トークン]** :iOS Volume Purchase Program (VPP) のライセンスを適用し、表示します。 詳細については、次をご覧ください。
  - [iOS 大量購入アプリ](vpp-apps-ios.md)
- **[Windows Enterprise 証明書]** :基幹業務アプリを Windows マネージド デバイスに配布するために使うコード署名証明書の状態を適用または表示します。
- **[Windows Symantec 証明書]** :XAP および WP8.x appx ファイルを Windows 10 Mobile デバイスに配布するために必要となる、Symantec コード署名証明書の状態を適用または表示します。
- **[ビジネス向け Microsoft ストア]** :ビジネス向け Microsoft ストアとの統合を設定します。 その後、購入済みのアプリケーションを Intune に同期して割り当て、ライセンスの使用状況を追跡できるようになります。 詳細については、次をご覧ください。
  - [ビジネス向け Microsoft ストアのボリューム購入アプリ](windows-store-for-business.md)。
- **[Windows サイドローディング キー]** :Windows サイドローディング キーを追加します。これを使うと、Windows ストアでアプリを公開およびダウンロードするのではなく、アプリを直接デバイスにインストールできます。 詳細については、次をご覧ください。
  - [Windows アプリのサイドローディング](app-sideload-windows.md)。
- **[ポータル サイトのブランド化]** :ポータル サイトをカスタマイズして会社のブランドを付与します。 詳細については、次をご覧ください。
  - [会社のポータルの構成](company-portal-app.md)
- **[アプリのカテゴリ]** :アプリのカテゴリ名を追加、ピン留め、削除します。
- **[Android 仕事用プロファイル]** :企業で承認されたアプリを承認して同期します。 詳細については、次をご覧ください。
  - [Android 仕事用プロファイルのアプリ](apps-add-android-for-work.md)

### <a name="help-and-support"></a>ヘルプとサポート
- **[ヘルプとサポート]** :トラブルシューティング、サポートの要求、または Intune の状態の表示を行います。 詳細については、次をご覧ください。
  - [問題のトラブルシューティング](../fundamentals/help-desk-operators.md)。

## <a name="next-steps"></a>次の手順

- [アプリを Microsoft Intune に追加する](apps-add.md)
