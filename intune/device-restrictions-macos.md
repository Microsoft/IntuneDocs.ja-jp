---
title: "macOS の Intune デバイス制限設定"
titleSuffix: Intune on Azure
description: "macOS デバイスでデバイスの設定と機能を制御するために使用できる Intune 設定について説明します。\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3129cbaf-96c2-4837-8907-ca87a605a496
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 716ca0a2041bdd2ecfadd180999a09f80373cb2a
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="macos-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune での macOS デバイスの制限設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

この設定を使用して、デバイスの制限プロファイルの macOS デバイスを管理します。

## <a name="password"></a>パスワード
-   **[パスワードが必要です]** - エンド ユーザーがデバイスにアクセスする際にパスワードの入力を要求します。
    -   **[必要なパスワードの種類]** - パスワードを数字のみとすることができるかどうか、または英数字 (文字と数字を含む) にする必要があるかどうかを指定します。 この設定は、Mac OS X バージョン 10.10.3 以降でのみサポートされます。
    -   **[パスワードに使用する英数字以外の文字数]** - パスワードに必要な複雑な文字の数を指定します (**0** ～ **4** 文字)。<br>複雑な文字とは、**?** のような記号です。
    -   **[パスワードの最小文字数]** - ユーザーが構成する必要があるパスワードの最小文字数 (**4** ～ **16** 文字) を入力します。
    -   **[単純なパスワード]** - 単純なパスワードの使用を許可します (**0000**、**1234** など)。
    -   **[画面ロック後にパスワードが要求されるまでの最長時間 (分)]** - コンピューターの非アクティブ状態が許容される時間を指定します。この時間を超えると、ロックを解除するためにパスワードが必要となります。
    -   **[画面がロックされるまでの非アクティブな最長時間 (分)]** - コンピューターのアイドル状態が許容される時間を指定します。この時間を超えると、画面はロックされます。
    -   **[パスワードの有効期限 (日数)]** - どれだけの日数が経過すると、ユーザーがパスワードを変更する必要があるかを指定します **(1** から **255** 日)。
    -   **[Prevent reuse of previous passwords (前のパスワードを再利用できないようにする)]** - 何回前までのパスワードを使用できないようにするかを指定します (**1** ～ **24**)。

## <a name="restricted-apps"></a>制限付きアプリ

制限付きアプリの一覧では、次の一覧のいずれかを構成できます。

**[禁止されているアプリ]** の一覧 - ユーザーによるインストールと実行が許可されていないアプリ (Intune で管理されていない) アプリを一覧表示します。
**[承認済みアプリ]** の一覧 - ユーザーによるインストールが許可されているアプリを一覧表示します。 準拠性を維持するため、ユーザーは一覧表示されていないアプリをインストールできません。 管理対象アプリは Intune で自動的に許可されます。

一覧を構成するには、**[追加]** をクリックし、任意の名前、アプリの発行元 (省略可能)、アプリのバンドル ID (例: *com.apple.calculator*) を指定します。

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>マークされていないメール ドメイン

**[メール ドメイン URL]** フィールドで、1 つ以上の URL を一覧に追加します。 構成したドメイン以外のドメインからのメールをエンド ユーザーが受信すると、そのメールは iOS のメール アプリで信頼されていないメールとしてマークされます。

