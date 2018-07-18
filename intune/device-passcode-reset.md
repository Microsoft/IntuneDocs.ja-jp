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
ms.openlocfilehash: a233c62b76901d9bad00aa6d8b2a8a4dd45dea96
ms.sourcegitcommit: 024cce10a99b12a13f32d3995b69c290743cafb8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2018
ms.locfileid: "39039303"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Intune でデバイスのパスコードをリセットまたは削除する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

デバイス用に新しいパスコードを作成するには、**[パスコードの削除]** アクションを使用します。 このアクションでは、仕事用プロファイルの PIN リセットのみが促されます。 Android 仕事用プロファイルに対して、デバイス PIN リセットはサポートされていません。

## <a name="work-profile-pin-reset-supported-platforms"></a>仕事用プロファイルの PIN リセットがサポートされているプラットフォーム

- 仕事用プロファイルと共に登録されている Android デバイス、バージョン 8.0 以降 
- Android デバイス、バージョン 6.0 以前
- Android エンタープライズ キオスク デバイス
- iOS 
     
## <a name="unsupported-platforms"></a>サポートされていないプラットフォーム

- 仕事用プロファイルと共に登録されている Android デバイス、バージョン 7.0 以前
- Android デバイス、バージョン 7.0 以降
- macOS
- Windows

## <a name="reset-a-passcode"></a>パスコードのリセット

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]**、**[すべてのデバイス]** の順に選択します。
4. 管理対象のデバイスのリストから、デバイスを選択して **[...詳細を表示]** を選択します。 次に、**[パスコードの削除]** デバイス リモート アクションを選択します。

## <a name="resetting-android-work-profile-passcodes"></a>Android 仕事用プロファイル パスコードをリセットする

サポートされている Android 仕事用プロファイル デバイスは、エンド ユーザー用の新しいマネージド プロファイル ロック解除パスワードまたはマネージド プロファイル チャレンジを受け取ります。 

Android 8.0 仕事用プロファイル デバイスの場合、登録が完了した直後に、エンド ユーザーはリセット パスコードをアクティブにするように通知されます。 仕事用プロファイル パスワードが要求され、設定されている場合、通知が表示されます。 パスコードが入力されると、通知が閉じられます。

## <a name="resetting-ios-passcodes"></a>iOS パスコードのリセット

パスコードは iOS デバイスから削除されます。 パスコード コンプライアンス ポリシーが設定されている場合、[設定] で新しいパスコードを設定するようにユーザーはデバイスから要求されます。 

## <a name="next-steps"></a>次の手順

実行したアクションの状態を確認するには、**[デバイス]** で **[デバイス アクション]** を選択します。
