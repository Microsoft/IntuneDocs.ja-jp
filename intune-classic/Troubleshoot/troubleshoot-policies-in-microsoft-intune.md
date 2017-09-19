---
title: "ポリシーに関するトラブルシューティング"
description: "ポリシー構成に関する問題のトラブルシューティングを行います。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 01/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3d8de720cc0b5973f4bbddb3e53b9ec838314f39
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2017
---
# <a name="troubleshoot-policies-in-microsoft-intune"></a>Microsoft Intune のポリシーのトラブルシューティング

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune ポリシーの展開と管理に関して問題がある場合は、ここから始めてください。 このトピックでは、発生する可能性がある一般的な問題とその解決策が示されています。

## <a name="general-issues"></a>一般的な問題

### <a name="was-a-deployed-policy-applied-to-the-device"></a>展開したポリシーはデバイスに適用されていますか。
**問題:** ポリシーが正しく適用されているかどうかがわかりません。

Intune の管理コンソールでは、すべてのデバイスの **[デバイスのプロパティ]**の下に [ポリシー] タブがあります。 各ポリシーには、 **[想定値]** と **[状態]**があります。 [想定値] は、ポリシーを割り当てるときに実現しようとした内容です。 [状態] は、ハードウェアとオペレーティング システムの制限事項と要件だけでなく、デバイスに適用されるすべてのポリシーがまとめて考慮されたときに実際に適用される内容です。 表示される状態は次のとおりです。

-   **[準拠]**: デバイスがポリシーを受信しており、設定に準拠していることをサービスに報告します。

-   **[該当なし]**: ポリシー設定は適用されません。 たとえば、iOS デバイス用の電子メール設定は、Android デバイスには適用されません。

-   **[保留]**: ポリシーはデバイスに送信されましたが、サービスに状態を報告していません。 たとえば、Android での暗号化では、ユーザーが暗号化を有効にする必要があるため、保留になる可能性があります。

下のスクリーンショットには、わかりやすい 2 つの例が示されています。

-   **[想定値]** 列に表示されているように、 **[単純なパスワードを使用する]**が **[はい]** に設定されていますが、その **[状態]** は **[該当なし]**になっています。 これは、Android デバイスでは単純なパスワードがサポートされていないことが原因です。

-   同様に、拡張ポリシー アイテム **[iOS デバイス用電子メールの設定]** は、このデバイスが Android デバイスであるため適用されません。

![Intune のデバイス ポリシー](../media/Intune-Device-Policy-v.2.jpg)

> [!NOTE]
> 制限レベルが異なる 2 つのポリシーを同じデバイスまたはユーザーに適用すると、より厳しい方のポリシーが実際に適用されます。


## <a name="issues-with-enrolled-devices"></a>登録済みデバイスに関する問題

### <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>アラート: アクセス ルールを Exchange に保存できませんでした
**問題**: 管理コンソールが「 **アクセス ルールを Exchange に保存できませんでした** 」のアラートを受信する。

管理コンソールの下の [Exchange On-Premises ポリシー] ワークスペースでポリシーを作成し、O365 を使用すると、構成されたポリシー設定が Intune によって適用されません。 アラートのポリシー ソースを確認してください。  [Exchange On-Premises ポリシー] ワークスペースで古いルールを削除します。古いルールはオンプレミスの Exchange で使用する、Intune 内のグローバルの Exchange ルールであり、O365 に関連しないためです。 次に、O365 の新しいポリシーを作成します。

### <a name="cannot-change-security-policy-for-various-enrolled-devices"></a>各種登録済みデバイスのセキュリティ ポリシーを変更できない
Windows Phone デバイスから、MDM または EAS で設定されたセキュリティ ポリシーのセキュリティを一度設定した後に緩くすることはできません。 たとえば、 **パスワードの最小文字数** を 8 に設定し、次に 4 に減らしてみます。 より制限の厳しいポリシーが、デバイスに既に適用されています。

ポリシーを安全度の低い値に変更する場合、デバイスのプラットフォームによっては、セキュリティ ポリシーをリセットしなければならない場合があります。
たとえば、Windows で、デスクトップを右からスワイプして、**[チャーム]** バーを開き、**[設定]** &gt; **[コントロール パネル]** の順にクリックします。  **[ユーザー アカウント]** アプレットを選択します。
左側のナビゲーション メニューの下部に、 **[セキュリティ ポリシーのリセット]** リンクがあります。 このリンクを選択し、**[ポリシーのリセット]** ボタンを選択します。
Android、Windows Phone 8.1 以降、iOS などのその他の MDM デバイスでは、制限の緩いポリシーを適用するにはいったんデバイスを削除して、サービスに再登録しなければならない場合があります。

## <a name="issues-with-pcs-that-run-the-intune-software-client"></a>Intune ソフトウェア クライアントを実行している PC に関する問題

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>policyplatform.log に記録される Microsoft Intune ポリシー関連エラー
Intune ソフトウェア クライアントで管理されている Windows PC では、policyplatform.log ファイルに記録されるポリシー エラーの原因としては、デバイスの Windows ユーザー アカウント制御 (UAC) で既定値以外が設定されていることが考えられます。 いくつかの既定値以外の UAC 設定は、Microsoft Intune クライアントのインストールやポリシーの実行に影響を与えます。

#### <a name="to-resolve-uac-issues"></a>UAC の問題を解決するには

1.  「[Retire devices from Microsoft Intune management](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management)」 (Microsoft Intune の管理からデバイスを削除する) の説明に従って、コンピューターを削除します。

2.  クライアント ソフトウェアが削除されるまで、20 分間待ちます。

    > [!NOTE]
    > [プログラムと機能] からクライアントを削除しないでください。

3.  スタート メニューで「**UAC**」と入力して、[ユーザー アカウント制御の設定] を開きます。

4.  通知のスライダーを既定の設定に移動します。

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>エラー: コンピューター 0x80041013 から値を取得できません
これは、ローカル システム上の時間が 5 分以上ずれている場合に発生します。 ローカル コンピューターの時間が同期されていない場合は、タイム スタンプが有効でないためセキュリティで保護されたトランザクションが失敗します。

この問題を解決するには、ローカル システムの時間をインターネット時間か、またはネットワーク上のドメイン コントローラーに設定された時間にできる限り近い時間に設定します。








### <a name="next-steps"></a>次のステップ
このトラブルシューティング情報を使っても問題が解決しない場合は、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」の説明に従って Microsoft サポートにお問い合わせください。
