---
title: Microsoft Intune でデバイス パスコードをリセットする - Azure | Microsoft Docs
description: Intune で管理または監視しているデバイスに対してパスコードの削除アクションを使用して、パスコードを削除またはリセットします。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 8b5f86a8f0d9beaef9e55d2281e3500e0c298a16
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182400"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Intune でデバイスのパスコードをリセットまたは削除する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

このドキュメントでは、デバイス レベルのパスコードのリセット、および Android enterprise (以前は Android for Work、AfW と呼ばれていました) デバイス上の仕事用プロファイルのパスコードのリセットの両方について説明します。 それぞれの要件が異なる可能性があるとき、この違いに注意することが重要です。 デバイス レベルのパスコードのリセットでは、デバイス全体のパスコードがリセットされます。 仕事用プロファイルのパスコードのリセットでは、Android enterprise デバイス上のユーザーの仕事用プロファイル用のパスコードのみがリセットされます。

## <a name="supported-platforms-for-device-level-passcode-reset"></a>デバイス レベルのパスコード リセットに対してサポートされるプラットフォーム

| プラットフォーム | サポート対象 |
| ---- | ---- |
| Android デバイス、バージョン 6.x 以前 | はい |
| キオスク モードの Android enterprise デバイス | はい |
| iOS デバイス | はい |
| 仕事用プロファイルと共に登録されている Android デバイス、バージョン 7.0 以前 | [いいえ] |
| Android デバイス、バージョン 7.0 以降 | [いいえ] |
| macOS | [いいえ] |
| Windows | [いいえ] |

Android デバイスの場合、これは、デバイス レベルのパスコードのリセットは、6.x 以前を実行しているデバイス、またはキオスク モードで実行している Android enterprise デバイスでのみ効率的にサポートされるということです。 これは、Google がデバイス管理者が許可したアプリ内から Android 7 デバイスのパスコード/パスワードのリセットのサポートを削除し、すべての MDM ベンダーに適用しているためです。

## <a name="supported-platforms-for-android-enterprise-work-profile-passcode-reset"></a>Android enterprise 仕事用プロファイルのパスコードのリセットに対してサポートされるプラットフォーム

| プラットフォーム | サポート対象 |
| ---- | ---- |
| 仕事用プロファイルと共に登録され、バージョン 8.0 以降を実行している Android enterprise デバイス | はい |
| 仕事用プロファイルと共に登録され、バージョン 7.x 以前を実行している Android enterprise デバイス | [いいえ] |
| バージョン 7.x 以前を実行している Android デバイス | [いいえ] |
| iOS | [いいえ] |
| macOS | [いいえ] |

新しい仕事用プロファイルのパスコードを作成するには、パスコードのリセット アクションを使用します。 このアクションでは、パスコードのリセットが求められ、仕事用プロファイル専用に新しい一時パスワードが作成されます。 

## <a name="reset-a-passcode"></a>パスコードのリセット

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]**、**[すべてのデバイス]** の順に選択します。
4. 管理対象のデバイスのリストから、デバイスを選択して **[...詳細を表示]** を選択します。 次に、**[パスコードの削除]** デバイス リモート アクションを選択します。

## <a name="reset-android-work-profile-passcodes"></a>Android の仕事用プロファイルのパスコードをリセットする

仕事用プロファイルで登録されたサポートされている Android enterprise デバイスでは、エンド ユーザー用の新しいマネージド プロファイル ロック解除パスワードまたはマネージド プロファイル チャレンジを受け取ります。

バージョン 8.x 以降を実行していて、仕事用プロファイルで登録された Android enterprise デバイスの場合、エンド ユーザーは登録が完了した後に正しいリセット パスコードをアクティブ化する通知を受け取ります。 仕事用プロファイル パスワードが要求され、設定されている場合、通知が表示されます。 パスコードが入力されると、通知が閉じられます。


## <a name="remove-ios-passcodes"></a>iOS パスコードの削除

リセットする代わりに、パスコードが iOS デバイスから削除されます。 パスコード コンプライアンス ポリシーが設定されている場合、ユーザーは [設定] で新しいパスコードを設定するようにデバイスから要求されます。

## <a name="next-steps"></a>次の手順

実行したアクションの状態を確認するには、**[デバイス]** で **[デバイス アクション]** を選択します。
