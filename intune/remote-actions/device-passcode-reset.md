---
title: Microsoft Intune でデバイス パスコードをリセットする - Azure | Microsoft Docs
description: Intune で管理または監視しているデバイスに対してパスコードの削除アクションを使用して、パスコードを削除またはリセットします。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be6a254360d8e8e9ef1396515d261b6ff9077b87
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713122"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Intune でデバイスのパスコードをリセットまたは削除する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

このドキュメントでは、Android Enterprise (以前は Android for Work (AfW) と呼ばれていた) デバイス上での、デバイス レベルのパスコードのリセットと仕事用プロファイルのパスコードのリセットの両方について説明します。 それぞれの要件が異なる場合があるので、この区別に注意することが重要です。 デバイス レベルのパスコードのリセットでは、デバイス全体のパスコードがリセットされます。 仕事用プロファイルのパスコードのリセットでは、Android enterprise デバイス上のユーザーの仕事用プロファイル用のパスコードのみがリセットされます。

## <a name="supported-platforms-for-device-level-passcode-reset"></a>デバイス レベルのパスコード リセットに対してサポートされるプラットフォーム

| プラットフォーム | サポート対象 |
| ---- | ---- |
| Android デバイス、バージョン 6.x 以前 | はい |
| キオスク モードの Android enterprise デバイス | はい |
| iOS デバイス | はい |
| ユーザー登録に登録されている iOS デバイス | [いいえ] |
| 仕事用プロファイルに登録されている Android デバイス | [いいえ] |
| Android デバイス、バージョン 7.0 以降 | [いいえ] |
| macOS | [いいえ] |
| Windows | [いいえ] |

Android デバイスの場合、これは、デバイス レベルのパスコードのリセットは、6.x 以前を実行しているデバイス上、またはキオスク モードで実行している Android Enterprise デバイス上でのみサポートされることを意味します。 これは、Google がデバイス管理者が許可したアプリ内から Android 7 デバイスのパスコード/パスワードのリセットのサポートを削除し、すべての MDM ベンダーに適用しているためです。

## <a name="supported-platforms-for-android-enterprise-work-profile-passcode-reset"></a>Android enterprise 仕事用プロファイルのパスコードのリセットに対してサポートされるプラットフォーム

| プラットフォーム | サポート対象 |
| ---- | ---- |
| 仕事用プロファイルと共に登録され、バージョン 8.0 以降を実行している Android enterprise デバイス | はい |
| 仕事用プロファイルと共に登録され、バージョン 7.x 以前を実行している Android enterprise デバイス | [いいえ] |
| バージョン 7.x 以前を実行している Android デバイス | [いいえ] |

新しい仕事用プロファイルのパスコードを作成するには、パスコードのリセット アクションを使用します。 このアクションでは、パスコードのリセットが求められ、仕事用プロファイル専用に新しい一時パスワードが作成されます。 

## <a name="reset-a-passcode"></a>パスコードのリセット


1. 次のいずれかのロールで [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。Azure Active Directory グローバル管理者、Azure Active Directory Intune サービスの管理者、ヘルプデスク担当者、ロール管理者のいずれかでサインインします。
2. **[デバイス]** 、 **[すべてのデバイス]** の順に選択します。
3. 管理対象のデバイスのリストから、デバイスを選択して **[...詳細を表示]** を選択します。 次に、 **[パスコードの削除]** デバイス リモート アクションを選択します。

## <a name="reset-android-work-profile-passcodes"></a>Android の仕事用プロファイルのパスコードをリセットする

仕事用プロファイルで登録されたサポートされている Android enterprise デバイスでは、エンド ユーザー用の新しいマネージド プロファイル ロック解除パスワードまたはマネージド プロファイル チャレンジを受け取ります。

バージョン 8.x 以降を実行していて、仕事用プロファイルで登録された Android enterprise デバイスの場合、エンド ユーザーは登録が完了した後に正しいリセット パスコードをアクティブ化する通知を受け取ります。 仕事用プロファイル パスワードが要求され、設定されている場合、通知が表示されます。 パスコードが入力されると、通知が閉じられます。


## <a name="remove-ios-passcodes"></a>iOS パスコードの削除

リセットする代わりに、パスコードが iOS デバイスから削除されます。 パスコード コンプライアンス ポリシーが設定されている場合、ユーザーは [設定] で新しいパスコードを設定するようにデバイスから要求されます。

## <a name="next-steps"></a>次の手順

実行したアクションの状態を確認するには、 **[デバイス]** で **[デバイス アクション]** を選択します。
