---
title: Microsoft Intune での Android デバイスのコンプライアンス設定 - Azure | Microsoft Docs
description: Microsoft Intune で Android デバイスにコンプライアンスを設定するときに使用できるすべての設定の一覧を表示します。 パスワード規則の設定、オペレーティング システムの最小バージョンまたは最大バージョンの選択、特定のアプリの制限、パスワードの再利用の防止などを行います。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: efff117ca79e4fa9a00fd8d9a4be792e246f1a86
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810165"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Intune を使用してデバイスを準拠または非準拠としてマークするための Android 設定

この記事では、Intune で Android デバイスに構成できるさまざまなコンプライアンス設定の一覧を示して説明します。 モバイル デバイス管理 (MDM) ソリューションの一部として、これらの設定を使用して、ルート化された (脱獄された) デバイスを非準拠としてマークする、許容される脅威レベルを設定する、Google Play Protect を有効にするなどを行います。

この機能は、以下に適用されます。

- Android デバイス管理者

Intune サービス管理者は、組織のリソースの保護に役立てるために、これらのコンプライアンス設定を使用します。 コンプライアンス ポリシーの詳細およびその機能については、[デバイス コンプライアンスの概要](device-compliance-get-started.md)に関するページを参照してください。

## <a name="before-you-begin"></a>始める前に

[コンプライアンス ポリシーの作成](create-compliance-policy.md#create-the-policy)。 **[プラットフォーム]** で、 **[Android デバイス管理者]** を選択します。

## <a name="device-health"></a>デバイスのヘルス

- **[ルート化されたデバイス]** : 
  - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。
  - **[ブロック]** - ルート化された (脱獄された) デバイスが非準拠としてマークされます。 

- **[デバイスは、デバイス脅威レベル以下であることが必要]** :  
  この設定を使用して、接続されているモバイル脅威防御サービスからのリスク評価をコンプライアンスの条件として実行します。 
  - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。 
  - **[セキュリティ保護]** - デバイスにはいかなる脅威も存在してはならないので、これはセキュリティ上最も安全なオプションです。 デバイスでいずれかのレベルの脅威が検出された場合、非準拠と評価されます。
  - **[低]** - 存在する脅威が低レベルの場合のみ、デバイスは準拠として評価されます。 低レベルより高い脅威が存在する場合、デバイスは非準拠状態になります。
  - **[中]** - デバイスに存在する脅威が低レベルまたは中レベルの場合、デバイスは準拠として評価されます。 デバイスで高レベルの脅威が検出された場合は、非準拠と判定されます。
  - **[高]** - 最も安全性の低いオプションであり、すべての脅威レベルが許容されます。 このソリューションをレポート目的のみで使用した場合、役立つ場合があります。

### <a name="google-play-protect"></a>Google Play Protect

- **[Google Play サービスが構成されています]** :  
  Google Play 開発者サービスはセキュリティ更新プログラムを許可し、Google の認定デバイスの多くのセキュリティ機能に対してベースレベルの依存関係となっています。
  - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。  
  - **[必須]** - Google Play 開発者サービス アプリがインストールされ、有効になっている必要があります。  

- **[最新のセキュリティ プロバイダー]** : 
  - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。  
  - **[必須]** - 最新のセキュリティ プロバイダーが既知の脆弱性からデバイスを保護できるようになっている必要があります。 

- **[アプリの脅威のスキャン]** :  
  - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。  
  - **[必須]** - Android の **[アプリの確認]** 機能が有効になっている必要があります。  
  > [!NOTE]
  > 従来の Android プラットフォームでは、この機能はコンプライアンス設定です。 Intune では、デバイス レベルでこの設定が有効になっているかどうかのみを確認できます。

- **[SafetyNet デバイスの構成証明]** :  
  満たす必要がある [SafetyNet デバイス構成証明](https://developer.android.com/training/safetynet/attestation.html)のレベルを入力します。 次のようなオプションがあります。
  - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。
  - **基本的な整合性のチェック**
  - **基本的な整合性と認定デバイスのチェック**

> [!NOTE]
> アプリ保護ポリシーを使用して Google Play Protect 設定を構成するには、Android で [Intune アプリ保護ポリシーの設定](../apps/app-protection-policy-settings-android.md#conditional-launch)を参照してください。

## <a name="device-properties"></a>デバイスのプロパティ

### <a name="operating-system-version"></a>オペレーティング システムのバージョン 

- **[最小 OS バージョン]** :  
  デバイスが最小 OS バージョンの要件を満たしていない場合、非準拠として報告されます。 アップグレード方法に関する情報のリンクが表示されます。 エンド ユーザーは、デバイスのアップグレードを行うことを選択できます。アップグレード後は、会社のリソースにアクセスできます。

   *既定では、バージョンは構成されていません*。

- **[最大 OS バージョン]** :  
  ルールで指定されたバージョンよりも新しいバージョンの OS がデバイスで使用されている場合、会社のリソースへのアクセスがブロックされます。 IT 管理者に問い合わせることをユーザーに促すメッセージが表示されます。対象の OS バージョンを許可するようにルールが変更されるまで、このデバイスを使用して会社のリソースにアクセスすることはできません。

  *既定では、バージョンは構成されていません*。

## <a name="system-security"></a>システム セキュリティ

### <a name="password"></a>パスワード
<!-- - **Minimum password length**: Enter the minimum number of digits or characters that the user's password must have.   


- **Maximum minutes of inactivity before password is required**: Enter the idle time before the user must reenter their password. When you choose **Not configured** (default), this setting isn't evaluated for compliance or non-compliance.

- **Password expiration (days)**: Select the number of days before the password expires and the user must create a new password.

- **Number of previous passwords to prevent reuse**: Enter the number of recent passwords that can't be reused. Use this setting to restrict the user from creating previously used passwords.

-->

- **[モバイル デバイスのロック解除にパスワードを必要とする]** : 
  - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。
  - **[必須]** - デバイスにアクセスするユーザーにパスワードを入力するよう求めます。  

- **[必要なパスワードの種類]** :  
  パスワードの内容を数字のみにするか、または数字と他の文字の組み合わせにするかを選択します。 次のようなオプションがあります。
  - **デバイスの既定**-パスワードの準拠を評価するには、 **[デバイスの既定]** 以外のパスワードの強度を選択してください。
  - **低レベルのバイオメトリック セキュリティ**
  - **最小数の数字** 
  - **数値複素数** - 繰り返しの番号や連続した番号 ("`1111`" や "`1234`" など) は許可されません。
  - **最小数の英字** 
  - **最小数の英数字**
  - **英数字と記号を使用する**


### <a name="encryption"></a>暗号化

- **[デバイス上のデータ ストレージの暗号化]** :  
  *Android 4.0 以降、または KNOX 4.0 以降でサポートされています。*  
  <br>
  - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。選択 
  - **必要**-デバイスのデータストレージを暗号化します。 **[モバイル デバイスのロック解除にパスワードを必要とする]** 設定を選択すると、デバイスは暗号化されます。  

### <a name="device-security"></a>［デバイス セキュリティ］

- **[提供元不明のアプリをブロックする]** :  
  - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。
  - **セキュリティ > 不明なソース**が有効になっているソースを**ブロック**ブロックするデバイス: android 2.x から android 4.0 でサポートされて *。Android 8.0 以降ではサポートされていません*)。  

  アプリをサイドローディングするには、提供元不明のアプリを許容する必要があります。 Android アプリをサイドローディングしていない場合は、この機能を **[ブロック]** に設定して、このコンプライアンス ポリシーを有効にします。 

  > [!IMPORTANT]
  > サイドローディング アプリケーションでは **[提供元不明のアプリをブロックする]** の設定を有効にする必要があります。 デバイス上で Android アプリをサイドローディングしていない場合のみ、このコンプライアンス ポリシーを適用します。

- **[ポータル サイト アプリのランタイム整合性]** :  
  - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。  
  - **[必須]** - *[必須]* を選択すると、次の要件がすべてポータル サイト アプリで満たされていることを確認します。
    - 既定のランタイム環境がインストールされている
    - 適切に署名されている
    - デバッグ モードになっていない
    - 既知の提供元からインストールされている

- **デバイスでの USB デバッグをブロック**する *(Android 4.2 以降)* :  
  - **[未構成]** ("*既定値*") - この設定に対して準拠であるか非準拠であるかの評価は行われません。
  - **[ブロック]** - デバイスで USB デバッグ機能を使用できなくなります。  

- **最低限のセキュリティパッチレベル** *(Android 6.0 以降)* :  
  デバイスに含めることができる最も古いセキュリティ パッチ レベルを選択します。 修正プログラムがこのレベルに達していないデバイスは非準拠になります。 日付は `YYYY-MM-DD` 形式で入力する必要があります。

  *既定では、日付は構成さ*れていません。

- **[制限付きアプリ]** :  
  制限する必要があるアプリの **[アプリ名]** と **[アプリ バンドル ID]** を入力してから、 **[追加]** を選択します。 制限付きアプリが少なくとも 1 つインストールされているデバイスは、非準拠としてマークされます。

## <a name="next-steps"></a>次の手順

- [非準拠デバイスに対するアクションを追加](actions-for-noncompliance.md)し、[スコープのタグを使用してポリシーをフィルター処理する](../fundamentals/scope-tags.md)
- [コンプライアンス ポリシーを監視します](compliance-policy-monitor.md)。
- [Android エンタープライズ デバイスのコンプライアンス ポリシー設定](compliance-policy-create-android-for-work.md)を参照してください。
