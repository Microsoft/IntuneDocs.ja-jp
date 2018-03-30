---
title: Microsoft Intune でデバイス パスコードをリセットする - Azure | Microsoft Docs
description: Intune で管理または監視しているデバイスに対してパスコードの削除アクションを使用して、パスコードを削除またはリセットします。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4cca5922f036711093469e71489e267af53f05a9
ms.sourcegitcommit: e6319ff186d969da34bd19c9730ba003d6cce353
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Intune でデバイスのパスコードをリセットまたは削除する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

デバイス用に新しいパスコードを作成するには、**[パスコードの削除]** アクションを使用します。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows 10 Creators Update までのリリースを含む、Windows Phone 8.1 (Azure Active Directory に参加していない)
- Windows 10 Creators Update 以降
- iOS
- Android 7 より前の Android バージョン

次のシステムについては、この機能はサポートされません。

- Windows
- macOS
- Android for Work

## <a name="reset-a-passcode"></a>パスコードのリセット

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]**、**[すべてのデバイス]** の順に選択します。
4. 管理対象のデバイスのリストから、デバイスを選択して **[...詳細を表示]** を選択します。 次に、**[パスコードの削除]** デバイス リモート アクションを選択します。

## <a name="next-steps"></a>次の手順

実行したアクションの状態を確認するには、**[デバイス]** で **[デバイス アクション]** を選択します。
