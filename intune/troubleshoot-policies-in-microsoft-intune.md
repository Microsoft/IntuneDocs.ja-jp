---
title: Microsoft Intune のポリシーのトラブルシューティング - Azure | Microsoft Docs
description: Microsoft Intune でポリシーを使用するときの一般的な問題と解決策について説明します
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1d656dcc8c3abcf3a4b0a9c6aacbc42eb896289f
ms.sourcegitcommit: 7c70c3e0fcae7c4fa8c9e108aafb1cebb366332d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44096505"
---
# <a name="troubleshoot-policies-in-intune"></a>Intune でのポリシーのトラブルシューティング

Intune のポリシーの展開と管理に関して問題がある場合は、ここから始めてください。 この記事では、発生する可能性がある一般的な問題と、考えられる解決策について説明します。

## <a name="general-issues"></a>一般的な問題

### <a name="was-a-deployed-policy-applied-to-the-device"></a>展開したポリシーはデバイスに適用されていますか。
**問題:** ポリシーが正しく適用されているかどうかがわからない。

Intune で **[デバイス]** > **[すべてのデバイス]** を選択し、デバイスを選択して、**[デバイス構成]** を選択すると、すべてのデバイスでポリシーの一覧が表示されます。 各ポリシーに **[状態]** があります。 状態は、ハードウェアとオペレーティング システムの制限事項と要件など、デバイスに適用されるすべてのポリシーがまとめて考慮されたときに適用されます。 表示される状態は次のとおりです。

- **[準拠]**: デバイスがポリシーを受信しており、設定に準拠していることをサービスに報告します。

- **[該当なし]**: ポリシー設定は適用されません。 たとえば、iOS デバイス用の電子メール設定は、Android デバイスには適用されません。

- **[保留]**: ポリシーはデバイスに送信されましたが、サービスに状態を報告していません。 たとえば、Android での暗号化では、ユーザーが暗号化を有効にする必要があるため、保留と表示される可能性があります。

> [!NOTE]
> 制限レベルが異なる 2 つのポリシーを同じデバイスまたはユーザーに適用すると、より厳しい方のポリシーが適用されます。

## <a name="issues-with-enrolled-devices"></a>登録済みデバイスに関する問題

### <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>アラート: アクセス ルールを Exchange に保存できませんでした
**問題**: 管理コンソールが「 **アクセス ルールを Exchange に保存できませんでした** 」のアラートを受信する。

管理コンソールの下の [Exchange On-Premises ポリシー] ワークスペースでポリシーを作成し、O365 を使用すると、構成されたポリシー設定が Intune によって適用されません。 アラートのポリシー ソースを確認してください。  [Exchange On-Premises ポリシー] ワークスペースで、従来のルールを削除します。 従来のルールはオンプレミスの Exchange で使用する、Intune 内のグローバルの Exchange ルールであり、O365 に関連しないためです。 次に、O365 の新しいポリシーを作成します。

### <a name="cannot-change-security-policy-for-various-enrolled-devices"></a>各種登録済みデバイスのセキュリティ ポリシーを変更できない
Windows Phone デバイスから、MDM または EAS で設定されたセキュリティ ポリシーのセキュリティを一度設定した後に緩くすることはできません。 たとえば、 **パスワードの最小文字数** を 8 に設定し、次に 4 に減らしてみます。 より制限の厳しいポリシーが、デバイスに既に適用されています。

ポリシーを安全度の低い値に変更する場合、デバイスのプラットフォームによっては、セキュリティ ポリシーをリセットしなければならない場合があります。

たとえば、Windows で、デスクトップを右からスワイプして、**[チャーム]** バーを開きます。 **[設定]** > **[コントロール パネル]** を選択し、**[ユーザー アカウント]** を選択します。 左側で **[セキュリティ ポリシーのリセット]** リンクを選択し、**[ポリシーのリセット]** を選択します。

Android、Windows Phone 8.1 以降、iOS などのその他の MDM デバイスでは、制限の緩いポリシーを適用するにはいったんデバイスを削除して、サービスに再登録しなければならない場合があります。

## <a name="issues-with-pcs-that-run-the-intune-software-client"></a>Intune ソフトウェア クライアントを実行している PC に関する問題

クラシック ポータルに適用されます。

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>policyplatform.log に記録される Microsoft Intune ポリシー関連エラー
Intune ソフトウェア クライアントで管理されている Windows PC では、policyplatform.log ファイルに記録されるポリシー エラーの原因としては、デバイスの Windows ユーザー アカウント制御 (UAC) で既定値以外が設定されていることが考えられます。 いくつかの既定値以外の UAC 設定は、Microsoft Intune クライアントのインストールやポリシーの実行に影響を与えます。

#### <a name="resolve-uac-issues"></a>UAC の問題を解決する

1. コンピューターの使用を終了します。 「[デバイスの削除](devices-wipe.md)」をご覧ください。

2. クライアント ソフトウェアが削除されるまで、20 分間待ちます。

    > [!NOTE]
    > [プログラムと機能] からクライアントを削除しないでください。

3. スタート メニューで「**UAC**」と入力して、[ユーザー アカウント制御の設定] を開きます。

4. 通知のスライダーを既定の設定に移動します。

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>エラー: コンピューター 0x80041013 から値を取得できません
ローカル システム上の時間が 5 分以上ずれている場合に発生します。 ローカル コンピューターの時間が同期されていない場合は、タイム スタンプが有効でないためセキュリティで保護されたトランザクションが失敗します。

この問題を解決するには、ローカル システムの時間をインターネット時間か、またはネットワーク上のドメイン コントローラーに設定された時間にできる限り近い時間に設定します。

### <a name="next-steps"></a>次の手順
このトラブルシューティング情報を使っても問題が解決しない場合は、「[Microsoft Intune のサポートを受ける方法](get-support.md)」の説明に従って Microsoft サポートにお問い合わせください。
