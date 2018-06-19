---
title: コンプライアンスのために Jamf Pro を Microsoft Intune と統合する
titlesuffix: ''
description: Microsoft Intune コンプライアンス ポリシーと Azure Active Directory の条件付きアクセスを使って、Jamf で管理されるデバイスをセキュリティ保護できます。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 01/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cdeb3a21af2b4cf020d3e5029eeb5b0bc31db062
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31024727"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>コンプライアンスのために Jamf Pro を Intune と統合する

|適用先: Azure Portal での Intune |
|--|
|クラシック ポータルで Intune に関するドキュメントをお探しですか。 [こちらを検索してください](/intune/introduction-intune?toc=/intune-classic/toc.json)。|
| |

組織で [Jamf Pro](https://www.jamf.com) を使用してエンド ユーザーの Mac を管理している場合、Microsoft Intune コンプライアンス ポリシーと Azure Active Directory の条件付きアクセスを使用して、組織内のデバイスがコンプライアンスに確実に準拠するようにできます。

## <a name="prerequisites"></a>必要条件

Jamf Pro で条件付きアクセスを構成するには、次のものが必要です。

- Jamf Pro 10.1.0 以降
- [macOS 用ポータル サイト アプリ](https://aka.ms/macoscompanyportal)
- OS X 10.11 Yosemite 以降を使用する macOS デバイス

## <a name="connecting-intune-to-jamf-pro"></a>Intune の Jamf Pro への接続

次の方法で Intune を Jamf Pro に接続できます。

1. Azure で新しいアプリケーションを作成する
2. Intune の Jamf Pro との統合を有効にする
3. Jamf Pro で条件付きアクセスを構成する

## <a name="create-a-new-application-in-azure-active-directory"></a>Azure Active Directory で新しいアプリケーションを作成する

1. **[Azure Active Directory]** > **[アプリの登録]** を開きます。
2. **[新しいアプリケーションの登録]** をクリックします。
3. 「**Jamf 条件付きアクセス**」など、**表示名**を入力します。
4. **[Web アプリ/API]** を選択します。
5. Jamf Pro インスタンス URL を使用して、**サインオン URL** を指定します。
6. **[アプリケーションの作成]** をクリックします。
7. 新しく作成した**アプリケーション ID** を保存し、**[設定]** を開き、**[API アクセス]** > **[キー]** に移動して、新しいアプリケーション キーを作成します。 **説明** (**期限切れ**になるまでの期間) を入力し、アプリケーション キーを保存します。

   > [!IMPORTANT]
   > アプリケーション キーは、このプロセス中 1 回のみ表示されます。 簡単に取得できる場所に保存してください。

8. **[設定]** を開き、**[API アクセス]** > **[必要なアクセス許可]** に移動し、すべてのアクセス許可を削除します。

   > [!NOTE]
   > 新しい必要なアクセス許可を追加します。 アプリケーションは必要なアクセス許可が 1 つの場合にのみ正しく動作します。

9. **[Microsoft Intune API]** を選択し、**[選択]** をクリックします。
10. **[Send device attributes to Microsoft Intune]\(デバイス属性を Microsoft Intune に送信する\)** を選択し、**[選択]** をクリックします。
11. アプリケーションの必要なアクセス許可を保存した後、**[アクセス許可の付与]** をクリックします。

    > [!NOTE]
    > アプリケーション キーが期限切れになった場合は、Microsoft Azure で新しいアプリケーション キーを作成し、Jamf Pro で条件付きアクセス データを更新する必要があります。 Azure では、サービスの中断を防ぐため、古いキーと新しいキーの両方をアクティブにすることができます。

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Intune の Jamf Pro との統合を有効にする

1. Microsoft Azure Portal で **[Microsoft Intune]** > **[デバイスのポリシー準拠]** > **[Partner device management]\(パートナー デバイス管理\)** を開きます。
2. アプリケーション ID を **[Jamf Azure Active Directory App ID]** フィールドに貼り付けることによって、Jamf 用コンプライアンス コネクタを有効にします。
3. **[Save]**(保存) をクリックします。

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Jamf Pro で Microsoft Intune 統合を構成する

1. Jamf Pro で、**[グローバル管理]** > **[条件付きアクセス]** に移動します。 **[Microsoft Intune 統合]** タブの **[編集]** ボタンをクリックします。
2. **[Microsoft Intune 統合の有効化]** チェック ボックスをオンにします。
3. 前の手順で保存した、**場所**、**ドメイン名**、**アプリケーション ID**、**アプリケーション キー**を含む、Azure テナントについての必要な情報を入力します。
4. **[Save]**(保存) をクリックします。 Jamf Pro は設定をテストし、成功を確認します。

## <a name="set-up-compliance-policies-and-register-devices"></a>コンプライアンス ポリシー設定してデバイスを登録する

Intune と Jamf の統合の構成が完了したら、[Jamf で管理されたデバイスにコンプライアンス ポリシーを適用する](conditional-access-assign-jamf.md)必要があります。

## <a name="information-shared-from-jamf-pro-to-intune"></a>Intune に Jamf Pro から共有する情報

Jamf Pro は、管理対象の macOS デバイスについてのインベントリ情報をキャプチャします。 Jamf Pro は、Intune に次の情報をレポートします。

* デバイスの Azure AD ID
* JAMF のインベントリ状態 (過去 24 時間以内に Jamf Pro でチェックインされたコンピューターのインベントリ状態)
* OS のバージョン
* ユーザーの Azure AD ID
* 暗号化 (FileVault 2)
* Gatekeeper ステータス
* パスワード: 文字セットの最小数
* パスワードの有効期限 (日)
* パスワードの種類 - 簡易、英数字、または不明
* 自動ログインの防止
* 必要なパスコードの長さ
* パスワード: 再利用を防止する前のパスワードの数
* システム整合性の保護
* 最後のチェックイン時刻
* アーキテクチャの種類
* 使用可能な RAM スロット
* バッテリ容量
* ブート ROM
* バス速度
* キャッシュ サイズ
* ［デバイス名］
* ドメイン参加
* Jamf ID
* MAC アドレス
* Make
* モデル
* モデル識別子
* NIC 速度
* コア数
* プロセッサ数
* OS
* プラットフォーム
* プロセッサ速度
* プロセッサの種類
* セカンダリ MAC アドレス
* シリアル番号
* SMC バージョン
* RAM 合計
* UDID
* ユーザーの電子メール

## <a name="next-steps"></a>次の手順

- [Jamf で管理されたデバイスにコンプライアンス ポリシーを適用する](conditional-access-assign-jamf.md)
