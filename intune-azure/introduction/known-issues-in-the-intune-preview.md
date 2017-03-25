---
title: "Microsoft Intune プレビューの既知の問題"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: プレビューの既知の問題について説明します"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b6c245d60c661c04b4c4d29c9bdcdd752254d978
ms.openlocfilehash: ec3f87994b19591bda4ec201eac3c839798d634c
ms.lasthandoff: 03/15/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Microsoft Intune プレビューの既知の問題


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


このトピックでは、Intune プレビューの既知の問題について説明します。

ここに記載されていないバグを報告する場合は、[サポートを依頼](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)してください。

Intune への新機能の追加を依頼する場合は、[Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console) サイトでレポートを提出することを検討してください。

## <a name="administration-and-accounts"></a>管理とアカウント

- グローバル管理者 (テナント管理者とも呼ばれる) は別個の Intune または Enterprise Mobility Suite (EMS) ライセンスがなくても日常的な管理タスクを続行できます。 ただし、グローバル管理者が自分自身のデバイスの登録、会社のデバイスの登録、Intune ポータル サイトの使用などを行うためにサービスを使用する場合は、他のユーザーと同じように Intune または EMS のライセンスが必要になります。

## <a name="apple-enrollment-profile-migration"></a>Apple 登録プロファイルの移行
- 今後数か月のうちに、Intune では、新しい Azure Portal を使用して、Apple Device Enrollment Program および Apple Configurator の登録の管理が可能になります。 Apple Device Enrollment Program トークンを削除したり、更新されたトークンをアップロードしなかった場合、元のトークンが Intune アカウントの移行の一部として新しい Azure Portal に復元されます。 このトークンを削除し、DEP 登録をブロックするには、Azure Portal で単にトークンを削除します。 

