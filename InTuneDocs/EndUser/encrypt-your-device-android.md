---
title: "暗号化を使用して Android デバイスを保護する方法 | Microsoft Docs"
description: "Android デバイスを保護する"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 879f8faa37309edae9d1cbb0456d372ff27b8b98
ms.openlocfilehash: a36c7dca0274b465315493261f03ab362c09383a
ms.lasthandoff: 02/23/2017


---


# <a name="how-to-protect-your-android-device-using-encryption"></a>暗号化を使用して Android デバイスを保護する方法

デバイスを暗号化するときに、承認されていないユーザーがアクセスできないように保護コード層でデバイスに関する情報をラップします。 ユーザーの情報を確実にセキュリティで保護するために、組織ではまず、企業のファイル、電子メール、またはデータにアクセスする前にユーザーに Android デバイスを暗号化するよう求める必要があります。

> [!Note]
> IT 管理者が要求する場合、暗号化の前に PIN またはパスワードを設定するように求められることがあります。

電話の登録を解除しても、暗号化は維持されます。

1.  デバイスの画面ロック PIN またはパスワードが設定されていることを確認します。

2.  **[設定]** から **[セキュリティ]** &gt; **[電話の暗号化]** の順に選択します。
    (電話によっては、"暗号か" オプションを表示するには、**[ストレージ]** &gt; **[ストレージの暗号化]** または **[ストレージ]** &gt; **[画面のロックとセキュリティ]** &gt; **[他のセキュリティ設定]** の順に選択する必要があります。)

3.  画面の指示に従います。 暗号化が行われている間、デバイスが何度か再起動する場合があります。

> [!Note]
> 一部の Android デバイスは暗号化できません。 詳細については、[こちら](your-device-appears-encrypted-but-cp-says-otherwise-android.md)を参照してください。

### <a name="what-to-do-if-you-have-issues"></a>問題がある場合の対処方法
**問題**: デバイスに既に暗号化を適用していますが、次のいずれかの状態に遭遇しました。

- 暗号化ボタンが無効です。
- 暗号化が必要であるというメッセージが引き続き表示されます。
- ポータル サイト アプリを使用しようとすると、エラーが表示されます。

**対処方法**

- デバイスが課金され、接続されていることを確認します。
- デバイスで PIN やパスワードが設定されていることを確認します。
- デバイスに PIN またはパスワードを既に設定してある場合は、次の手順を試してみます。IT 管理者がデバイスのセキュリティを強化する必要がある場合があります。 Android デバイスの種類により、手順で表示されるメニュー名が若干異なることがあります。

    1. **[Settings]** (設定) > **[Security]** (セキュリティ) > **[Screen lock]** (画面のロック) の順に移動します。 現在の PIN またはパスワードを確認します。

    2. **[Choose screen lock]** (画面のロックの選択) 画面で、使用する画面ロックの種類を選択します。

    3. **[Secure start-up]** (安全な起動) 画面で、**[Require PIN to start device]** (デバイスの起動に PIN が必要) をタップし、**[Continue]** (続行) をタップします。

    4. PIN を選択し (前に入力したものと同じものを入力できます)、**[Confirm your PIN]** (PIN の確認) をタップします。

    5. ポータル サイト アプリを開き、デバイスを選択して、**[Check Compliance]** (ポリシー準拠状況の確認) をタップします。


サポートが必要な場合は、 IT 管理者に問い合わせるか (連絡先情報については[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください)、または [Microsoft Android チーム](mailto:wintunedroidfbk@microsoft.com)にご連絡ください。

