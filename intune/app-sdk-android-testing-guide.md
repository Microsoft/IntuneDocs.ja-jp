---
title: Android 用 Microsoft Intune アプリ SDK 開発者テスト ガイド
description: Android のテスト ガイド用の Microsoft Intune アプリ SDK を使用して、Intune の管理対象の Android アプリをテストできます。
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4203f424c395399cb0ed1e7472b006602aa0b210
ms.sourcegitcommit: db7a6b8fc9e82dae4f2111ca0b2d3c14e33658f9
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072472"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Android 用 Microsoft Intune アプリ SDK 開発者テスト ガイド

Android のテスト ガイド用の Microsoft Intune アプリ SDK は、Intune の管理対象の Android アプリをテストするときに設計されています。  

## <a name="prerequisite-test-accounts"></a>前提条件のテスト アカウント
事前に生成されたデータなしでは、新しいアカウントを作成することができます。 新しいアカウントを作成するには:
1. 移動し、 [Microsoft デモ](https://demos.microsoft.com/environments/create/tenant)サイト。 
2. [Intune のセットアップ](https://docs.microsoft.com/intune/setup-steps)モバイル デバイス管理 (MDM) を有効にします。
3. [ユーザーを作成する](https://docs.microsoft.com/intune/users-add)します。
4. [グループを作成します](https://docs.microsoft.com/intune/groups-add)。
5. [ライセンスを割り当てる](https://docs.microsoft.com/intune/licenses-assign)に合わせて、テストします。


## <a name="azure-portal-policy-configuration"></a>Azure ポータルのポリシーの構成
[作成し、アプリ保護ポリシーを割り当てる](https://docs.microsoft.com/intune/app-protection-policies)で、 [Azure portal の [Intune] ブレード](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview)します。 [アプリ構成ポリシー](https://docs.microsoft.com/intune/app-configuration-policies-overview)も作成および Intune ブレードで割り当てられます。

> [!NOTE]
> 場合は、Azure portal で、アプリが表示されないことができますで対象とする、ポリシーを選択して、**アプリ**オプションと、テキスト ボックスにパッケージ名を指定します。

> [!IMPORTANT]
> アプリ構成ポリシーを適用する、ユーザーを登録する必要がありますの対象となる、 [Intune アプリ保護ポリシー](https://docs.microsoft.com/intune/app-protection-policy)します。

## <a name="test-cases"></a>テスト ケース

次のテスト_ケースでは、構成と確認の手順を提供します。 Intune の管理対象の Android アプリの問題をトラブルシューティングするのにには、このガイダンスを使用します。

### <a name="required-pin-and-corporate-credentials"></a>PIN 必要として、会社の資格情報

企業リソースにアクセスする際に pin を要求することができます。 また、ユーザーが管理対象アプリを使用する前に、会社の認証を適用できます。 これらの要件を設定するのにには、次の手順を使用します。

1. 構成**へのアクセスは PIN が必要**と**へのアクセスを会社の資格情報を必要と**に**はい**します。 詳細については、「[Microsoft Intune の Android アプリ保護ポリシー設定](app-protection-policy-settings-android.md#access-requirements)」を参照してください。
2. 次の条件を確認します。
    - アプリの起動には、PIN の入力/セットアップや会社のポータルでの登録中に使用された運用環境ユーザー プロンプトを表示する必要があります。
    - 正しく構成されていないの android マニフェスト、ADAL の統合 (SkipBroker、ClientID、および機関) の値は具体的には、有効なサインイン プロンプトを表示に失敗した可能性があります。
    - 任意のプロンプトを表示するエラーが正しくない統合が考えられます`MAMActivity`値。 詳細については`MAMActivity`を参照してください[Android 開発者ガイド用の Microsoft Intune アプリ SDK](app-sdk-android.md)します。

> [!NOTE] 
> 上記のテストが動作していない場合は、以下のテストも失敗する可能性が。 レビュー [SDK](app-sdk-android.md##sdk-integration)と[ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal)統合します。

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>転送して、他のアプリとデータの受信を制限します。
次のように会社の管理対象のアプリケーション間のデータ転送を制御できます。

1. 設定**他のアプリにデータを転送する許可アプリ**に**ポリシーで管理されたアプリ**します。
2. **[このアプリで他のアプリからデータを受信できるようにする]** を **[すべてのアプリ]** に設定します。 インテントとコンテンツ プロバイダーの使用は、これらのポリシーの影響を受けます。
3. 次の条件を確認します。
    - アプリケーションの機能に、正しく非管理対象アプリから開きます。
    - 管理対象アプリ間でコンテンツの共有が許可されます。
    - 管理対象アプリから管理対象外アプリ (たとえば、Chrome) への共有はブロックされます。

### <a name="restrict-cut-copy-and-paste"></a>切り取り、コピー、貼り付けを制限
次のように、マネージ アプリケーションをシステム クリップボードを制限できます。

1. 設定**Restrict 切り取り、コピー、および他のアプリと貼り付け**に**貼り付けを使用ポリシーが管理されている**します。
2. 次の条件を確認します。
    - マネージ アプリからコピーしたテキストを非管理対象アプリ (たとえば、メッセージ) はブロックされます。

### <a name="prevent-save-as"></a>**[名前を付けて保存]** を禁止する
制御できます**として保存**次のように機能します。

1. アプリが必要な場合[統合として保存する のコントロール](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted)設定**できないようにする ' 名前を付けて保存**に**はい**。
2. 次の条件を確認します。
    - 保存は、適切な管理された場所のみに制限されます。

### <a name="file-encryption"></a>ファイルの暗号化
次のように、デバイス上のデータを暗号化できます。

1. 設定**アプリケーション データを暗号化**に**はい**します。
2. 次の条件を確認します。
    - 通常のアプリケーションの動作は影響はありません。

### <a name="prevent-android-backups"></a>Android でのバックアップを禁止する
次のようにアプリのバックアップを制御できます。

1. 設定した場合[バックアップの制限事項を統合](app-sdk-android.md#protecting-backup-data)、構成**防止 Android でのバックアップ**に**はい**。
2. 次の条件を確認します。
    - バックアップは、制限されています。

### <a name="unenrollment"></a>登録解除
管理対象アプリから会社の電子メールとドキュメントを格納しているをリモートでワイプできるし、個人データは、次のように管理が不要になったときに復号化は。

1. Azure portal から[ワイプを発行](https://docs.microsoft.com/intune/apps-selective-wipe)します。
2. アプリは、ワイプのハンドラーは、次の条件を確認するを登録していない: 場合
    - アプリの完全なワイプが発生します。
3. アプリが登録されている場合`WIPE_USER_DATA`または`WIPE_USER_AUXILARY_DATA`、次の条件を確認します。
    - 管理されたコンテンツは、アプリから削除されます。 詳細については、次を参照してください。 [Intune App SDK for Android の開発者ガイド - 選択的ワイプ](app-sdk-android.md#selective-wipe)します。

### <a name="multi-identity"></a>複数 ID
統合[複数 id サポート](app-sdk-android.md#multi-identity-optional)徹底的にテストする必要がある危険度の高い変更です。 最も一般的な問題は、(脅威のレベルとコンテキスト) id の不適切な設定とも追跡ファイルが原因であるが (`MAMFileProtectionManager`)。

最低限の複数の id は、次のシナリオを再検証する必要があります。

- **名前を付けて保存**管理対象 id に対してポリシーが正しく動作します。
- 個人に貼り付けの制限が正しく適用からにコピーします。
- 管理対象 id に属するデータのみが暗号化されており、個人のファイルは変更されません。
- 選択的ワイプでの登録解除中には、管理対象 id データを削除するだけです。
- アンマネージからマネージ アカウント (初回のみ) に変更する際に、条件付き起動のエンド ユーザーに確認するとします。

### <a name="app-configuration-optional"></a>アプリの構成 (省略可能)
管理対象アプリの動作は次のように構成できます。

1. アプリでは、すべてのアプリ構成設定を消費する場合は、アプリは、(管理者) として設定できるすべての値を正しく処理をテストする必要があります。 [アプリ構成ポリシー](https://docs.microsoft.com/intune/app-configuration-policies-overview)作成し、Intune を使用して割り当てることができます。

## <a name="next-steps"></a>次の手順

- [Android の基幹業務アプリを Microsoft Intune に追加します](lob-apps-android.md)。
