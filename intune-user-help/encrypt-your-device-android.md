---
title: "暗号化を使用して Android デバイスを保護する方法 | Microsoft Docs"
description: "Android デバイスを保護する"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 8ad13a8534f142ec97fc15759bf863e04c36d266
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="how-to-protect-your-android-device-using-encryption"></a>暗号化を使用して Android デバイスを保護する方法

デバイスを暗号化するときに、承認されていないユーザーがアクセスできないように保護コード層でデバイスに関する情報をラップします。 ユーザーの情報を確実にセキュリティで保護するために、組織ではまず、企業のファイル、電子メール、またはデータにアクセスする前にユーザーに Android デバイスを暗号化するよう求める必要があります。

> [!Note]
> Huawei 製や Vivo および OPPO 製の特定の Android デバイスは暗号化できません。 詳細については、[こちら](your-device-appears-encrypted-but-cp-says-otherwise-android.md)を参照してください。

電話の登録を解除しても、暗号化は維持されます。

1.  デバイスの画面ロック PIN またはパスワードが設定されていることを確認します。

2.  **[設定]** で、**[セキュリティ]** > **[Encrypt Device]\(デバイスの暗号化\)** の順に選択します。
    (一部の電話では、"暗号化" オプションを表示するために、**[ストレージ]** > **[ストレージの暗号化]** または **[ストレージ]** > **[画面のロックとセキュリティ]** > **[他のセキュリティ設定]** の順に選択する必要があります。)

3.  画面の指示に従います。 暗号化が行われている間、デバイスが何度か再起動する場合があります。

### <a name="what-to-do-if-you-have-issues"></a>問題がある場合の対処方法
**問題**: デバイスに既に暗号化を適用していますが、次のいずれかの状態に遭遇しました。

- 暗号化ボタンが無効です。
- 暗号化が必要であるというメッセージが引き続き表示されます。
- ポータル サイト アプリを使用しようとすると、エラーが表示されます。

**対処方法**

- デバイスが課金され、接続されていることを確認します。
- デバイスで PIN やパスワードが設定されていることを確認します。
- デバイスに PIN またはパスワードを既に設定してある場合は、次の手順を試してみます。会社のサポートがデバイスのセキュリティを強化する必要がある場合があります。 Android デバイスの種類により、手順で表示されるメニュー名が若干異なることがあります。

    1. **[設定]** > **[ロック画面とセキュリティ]** > **[画面のロック]** の順に進みます。 現在の PIN またはパスワードを確認します。

    2. **[Choose screen lock]** (画面のロックの選択) 画面で、使用する画面ロックの種類を選択します。 

    3. 画面のロックを選択したら、**[ロック画面とセキュリティ]** 画面に戻り、**[安全な起動]** を選択します。 
    
    4. **[安全な起動]** 画面で、**[Require PIN to start device]\(デバイスの起動に PIN が必要\)** をタップし、**[続行]** をタップします。

    5. PIN を選択し (前に入力したものと同じものを入力できます)、**[Confirm your PIN]** (PIN の確認) をタップします。

    6. ポータル サイト アプリを開き、デバイスを選択して、**[Check Compliance]** (ポリシー準拠状況の確認) をタップします。

サポートが必要な場合は、 会社のサポートに問い合わせるか (連絡先情報については[ポータル Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください)、または <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android チーム</a>にご連絡ください。
