---
title: "Microsoft Intune プレビューの既知の問題"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: プレビューの既知の問題について説明します"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/13/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 24498abc504f05bd22dc7309bc22948292f9b1e6
ms.openlocfilehash: 4c81c17ba1419f0b5bdc4910be7d26a5893b32e0
ms.lasthandoff: 04/13/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Microsoft Intune プレビューの既知の問題


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


このトピックでは、Intune プレビューの既知の問題について説明します。

ここに記載されていないバグを報告する場合は、[サポートを依頼](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)してください。

Intune への新機能の追加を依頼する場合は、[Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console) サイトでレポートを提出することを検討してください。

## <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>移行中に Intune で作成されるグループは、他の Microsoft 製品の機能に影響する可能性がある

クラシック Intune から Azure Portal に移行する場合、**All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421** という新しい名前が表示されます。 このグループには、Intune のライセンスを持つユーザーだけでなく、Azure Active Directory のすべてのユーザーが含まれる点に注意してください。 そのため、一部の既存のユーザーまたは新規ユーザーがどのグループの一員でもない場合に発生するその他の Microsoft 製品の問題も含まれます。

## <a name="altering-groups-created-by-intune-during-migration-will-delay-migration"></a>Intune で作成されたグループを移行中に変更すると移行に遅延が生じる

移行の準備と整えるために、グループは Intune から Azure AD にコピーします。 クラシック Intune ポータルで行うその他の変更は、Azure AD グループで更新されます。 ただし、Azure AD で行ったすべての変更は、再びクラシック Intune コンソールに同期されません。 そのため、Azure Portal への移行が失敗し、移行が遅延する可能性があります。

## <a name="compliance-policies-from-intune-will-not-show-up-in-new-console"></a>Intune のコンプライアンス ポリシーに新しいコンソールへのサインインは表示されない 

クラシック Intune ポータルで作成したコンプライアンス ポリシーを移行します。Azure Portal には表示されません。 これは、Azure Portal の設計の変更のためです。 クラシック Intune ポータルで作成してコンプライアンス ポリシーが必要で、クラシック ポータルで内容を確認し、編集する必要があります。
または、Azure Portal で作成した新しいコンプライアンス ポリシーは、クラシック ポータルに表示されません。
詳細については、「[Intune Azure プレビューでのデバイス コンプライアンスとは](https://docs.microsoft.com/intune-azure/set-device-compliance/what-is-device-compliance)」を参照してください。




## <a name="administration-and-accounts"></a>管理とアカウント

グローバル管理者 (テナント管理者とも呼ばれる) は別個の Intune または Enterprise Mobility Suite (EMS) ライセンスがなくても日常的な管理タスクを続行できます。 ただし、グローバル管理者が自分自身のデバイスの登録、会社のデバイスの登録、Intune ポータル サイトの使用などを行うためにサービスを使用する場合は、他のユーザーと同じように Intune または EMS のライセンスが必要になります。

## <a name="apple-enrollment-profile-migration"></a>Apple 登録プロファイルの移行
今後数か月のうちに、Intune では、新しい Azure Portal を使用して、Apple Device Enrollment Program および Apple Configurator の登録の管理が可能になります。 Apple Device Enrollment Program トークンを削除したり、更新されたトークンをアップロードしなかった場合、元のトークンが Intune アカウントの移行の一部として新しい Azure Portal に復元されます。 このトークンを削除し、DEP 登録をブロックするには、Azure Portal で単にトークンを削除します。 

