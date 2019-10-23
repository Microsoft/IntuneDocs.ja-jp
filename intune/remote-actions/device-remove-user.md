---
title: Microsoft Intune を使用して iOS デバイスからユーザーを削除する
titleSuffix: ''
description: Intune を使用して共有の iOS デバイスからユーザーを削除する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 030d455c366a9c447444c247e9690e5d31613982
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508601"
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>共有の iOS デバイスからユーザーを削除する


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

**ユーザーの削除**アクションでは、共有の iPad デバイス上のローカル キャッシュから選択したユーザーを削除します。 iPad デバイスは、[iOS 教育プロファイル](../fundamentals/education-settings-configure-ios.md)を使用して iOS Classroom アプリを管理するように設定する必要があります。 

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows - サポートされていません
- Windows Phone - サポートされていません
- iOS - iOS 9.3 以降 (共有 iPad デバイスのみ) でサポートされています
- macOS - サポートされていません
- Android - サポートされていません

## <a name="remove-a-user"></a>ユーザーを削除する

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
3. **[Intune]** ウィンドウで、 **[デバイス]** を選択します。
4. **[デバイス]** ウィンドウで、 **[すべてのデバイス]** を選択します。
5. 管理対象のデバイスのリストで、iOS デバイスを選択します。
6. デバイスのウィンドウで、 **[ユーザー]** を選択します。
7. リストで、削除するユーザーを右クリックして、 **[ユーザーの削除]** を選択します。

## <a name="next-steps"></a>次の手順

- **ユーザーの削除**アクションの状態を表示するには、 **[デバイス]**  >  **[デバイス アクション]** の順に選択します。
