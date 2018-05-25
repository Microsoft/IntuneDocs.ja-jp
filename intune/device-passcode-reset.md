---
title: Microsoft Intune でデバイス パスコードをリセットする - Azure | Microsoft Docs
description: Intune で管理または監視しているデバイスに対してパスコードの削除アクションを使用して、パスコードを削除またはリセットします。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5783558a768e1d58087168f81ad27e5acf9aae09
ms.sourcegitcommit: 91802e78cd5014d20a828ca25a54a381d452f0f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Intune でデバイスのパスコードをリセットまたは削除する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

デバイス用に新しいパスコードを作成するには、**[パスコードの削除]** アクションを使用します。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- 仕事用プロファイルと共に登録されている Android デバイス、バージョン 7.0 以降
- Android デバイス、バージョン 6.0 以前
- iOS 
     
## <a name="unsupported-platforms"></a>サポートされていないプラットフォーム

- 仕事用プロファイルと共に登録されている Android デバイス、バージョン 6.0 以前
- Android デバイス、バージョン 7.0 以降
- macOS
- Windows

## <a name="reset-a-passcode"></a>パスコードのリセット

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]**、**[すべてのデバイス]** の順に選択します。
4. 管理対象のデバイスのリストから、デバイスを選択して **[...詳細を表示]** を選択します。 次に、**[パスコードの削除]** デバイス リモート アクションを選択します。

## <a name="resetting-android-for-work-passcodes"></a>Android for Work パスコードのリセット

サポートされている Android for Work デバイスでは、エンド ユーザーの新しいマネージド プロファイル ロック解除パスワードまたはマネージド プロファイル チャレンジを受け取ります。 Android 7.0 以降と仕事用プロファイルのデバイスの場合、エンド ユーザーは、登録完了の直後、リセット パスコード トークンを有効にする旨が記載された通知を受け取ります。 仕事用プロファイル パスワードが要求され、設定されている場合、通知が表示されます。 パスコードが入力されると、通知が閉じられます。

## <a name="resetting-ios-passcodes"></a>iOS パスコードのリセット

パスコードは iOS デバイスから削除されます。 パスコード コンプライアンス ポリシーが設定されている場合、[設定] で新しいパスコードを設定するようにユーザーはデバイスから要求されます。 

## <a name="next-steps"></a>次の手順

実行したアクションの状態を確認するには、**[デバイス]** で **[デバイス アクション]** を選択します。
