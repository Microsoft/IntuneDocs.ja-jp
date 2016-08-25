---
title: "デバイスを暗号化する |Microsoft Intune"
description: "Android デバイスを暗号化する方法について説明します"
keywords: 
author: staciebarker
manager: angrobe
ms.date: 06/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6c6a6fed876e49888d8fda1fd93b39313387ba38
ms.openlocfilehash: 6cb6c0b8a8f4c1b88565ce4b7a5690406b4ddf40


---


# デバイスを暗号化する

勤務先の会社や組織で、社内のファイルや電子メール、データにアクセスする Android デバイスの暗号化が義務付けられている場合、以下の手順に従ってお使いのデバイスを暗号化してください。 IT 管理者が要求する場合、暗号化の前に PIN またはパスワードを設定するように求められることがあります。

電話の登録を解除しても、暗号化は維持されます。

1.  デバイスの画面ロック PIN またはパスワードが設定されていることを確認します。

2.  **[設定]** から **[セキュリティ]** &gt; **[電話の暗号化]** の順にクリックします。
    (電話によっては、"暗号か" オプションを表示するには、**[ストレージ]** &gt; **[ストレージの暗号化]** または **[ストレージ]** &gt; **[画面のロックとセキュリティ]** &gt; **[他のセキュリティ設定]** の順にクリックする必要があります。)

3.  画面の指示に従います。 暗号化が行われている間、デバイスが何度か再起動する場合があります。

### 問題がある場合の対処方法
**問題**: デバイスに既に暗号化を適用していますが、次のいずれかの状態に遭遇しました。

- 暗号化ボタンが無効です。
- 暗号化が必要であるというメッセージが引き続き表示されます。
- ポータル サイト アプリを使用しようとすると、エラーが表示されます。

**対処方法**: 

1. デバイスが課金され、接続されていることを確認します。

2. デバイスで PIN やパスワードが設定されていることを確認します。

3. デバイスに PIN またはパスワードを既に設定してある場合は、次の手順を試してみます。IT 管理者がデバイスのセキュリティを強化する必要がある場合があります。 Android デバイスの種類により、手順で表示されるメニュー名が若干異なることがあります。

    a. **[Settings]** (設定) > **[Security]** (セキュリティ) > **[Screen lock]** (画面のロック) の順に移動します。 現在の PIN またはパスワードを確認します。

    b. **[Choose screen lock]** (画面のロックの選択) 画面で、使用する画面ロックの種類を選択します。

    c. **[Secure start-up]** (安全な起動) 画面で、**[Require PIN to start device]** (デバイスの起動に PIN が必要) をタップし、**[Continue]** (続行) をタップします。

    d. PIN を選択し (前に入力したものと同じものを入力できます)、**[Confirm your PIN]** (PIN の確認) をタップします。

    e. ポータル サイト アプリを開き、デバイスを選択して、**[Check Compliance]** (ポリシー準拠状況の確認) をタップします。

サポートが必要な場合は、 IT 管理者に問い合わせるか (連絡先情報については[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください)、または Microsoft Android チーム (wintunedroidfbk@microsoft.com) にご連絡ください。

### 関連項目
[Android デバイスを Intune で使用する](using-your-android-device-with-intune.md)



<!--HONumber=Aug16_HO2-->


