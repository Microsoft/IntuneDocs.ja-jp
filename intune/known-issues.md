---
title: "Azure での Microsoft Intune の既知の問題"
titleSuffix: Intune on Azure
description: "Intune の既知の問題についての説明"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/13/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: db17387360e5d40cd19613266aec153f01bdaedc
ms.openlocfilehash: 754f20c7f10f6421e7a9a0aa5429b3c3c6b2fd72
ms.contentlocale: ja-jp
ms.lasthandoff: 06/15/2017


---

# <a name="known-issues-in-microsoft-intune"></a>Microsoft Intune の既知の問題


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


このトピックでは、Microsoft Intune の既知の問題について説明します。

ここに記載されていないバグを報告する場合は、[サポートを依頼](get-support.md)してください。

Intune への新機能の追加を依頼する場合は、[Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console) サイトでレポートを提出することをご検討ください。

## <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>移行中に Intune で作成されるグループは、他の Microsoft 製品の機能に影響する可能性がある

クラシック Intune から Azure に移行する場合、**All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421** という新しいグループが表示されます。 このグループには、Intune のライセンスを持つユーザーだけでなく、ご利用の Azure Active Directory のすべてのユーザーが含まれます。 このグループを使用すると、一部の既存のユーザーまたは新規ユーザーがどのグループにも属さない場合に、他の Microsoft 製品に関する問題が発生することがあります。

## <a name="secondary-migration-required-for-select-capabilities"></a>特定の機能に必要な二次移行

2017 年 1 月よりも前に作成された Intune アカウントでは、Azure Portal で以下の機能を使用する前に、移行が必要です。

- 業務用デバイスの登録プロファイル
- Apple Device Enrollment Program
- iOS シリアル番号グループに事前登録された業務用デバイス
- デバイス登録マネージャー
- Apple Volume Purchase Program

これらの機能は、従来の Silverlight コンソールや Azure コンソールでは管理できないため、移行することで以下のようになります。
- 従来のコンソールでは無効になります。
- Azure コンソールでは有効になります。  

現在 Azure Portal でこれらの Intune 機能を管理している場合は、以下の変更点にご注意ください。

### <a name="removes-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Apple DEP における、既定の業務用デバイスの登録プロファイルの削除
Azure Portal では、Apple Device Enrollment Program (DEP) デバイスについての、既定の業務用デバイスの登録プロファイルがサポートされません。 この機能は、従来の Silverlight Intune コンソールでは使用できますが、プロファイルが意図せずに割り当てられることを防ぐため、廃止されています。 DEP シリアル番号が Azure Portal で同期されている場合、業務用デバイスの登録プロファイルは割り当てられません。 登録プロファイルは、デバイスを使用する前に割り当てられている必要があります。

## <a name="altering-groups-created-by-intune-during-migration-delays-migration"></a>Intune で作成されたグループを移行中に変更すると遅延が生じる

移行の準備を整えるために、グループは Intune から Azure AD にコピーされます。 その後クラシック Intune ポータルで行われた変更は、Azure AD グループで更新されます。 ただし、Azure AD で行われた変更は、クラシック Intune コンソールには同期されません。 このことが原因で Azure Portal への移行が失敗し、遅延することがあります。

## <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>Intune のコンプライアンス ポリシーが新しいコンソールに表示されない

クラシック Intune ポータルで作成したコンプライアンス ポリシーは移行できますが、Azure Portal では設計が変更されているため、Azure Portal には表示されません。 クラシック Intune ポータルで作成したコンプライアンス ポリシーは依然として有効ですが、ポリシーの表示や編集はクラシック Intune ポータル上で行う必要があります。
また、Azure Portal で作成した新しいコンプライアンス ポリシーは、クラシック Intune ポータル上には表示されません。

詳細については、「[Intune Azure プレビューでのデバイス コンプライアンスとは](device-compliance.md)」を参照してください。

## <a name="administration-and-accounts"></a>管理とアカウント

グローバル管理者 (テナント管理者とも呼ばれる) は別個の Intune または Enterprise Mobility Suite (EMS) のライセンスがなくても日常的な管理タスクを引き続き行うことができます。 ただし、自分自身のデバイスの登録、業務用デバイスの登録、Intune ポータル サイトの使用などのサービスを使用するためには、Intune または EMS のライセンスが必要になります。

## <a name="apple-enrollment-profile-migration"></a>Apple 登録プロファイルの移行

今後数か月のうちに、Intune では新しい Azure Portal を使用して Apple Device Enrollment Program と Apple Configurator の登録を管理できるようになります。 Apple Device Enrollment Program トークンを削除し、新しいトークンをアップロードしない場合、移行の際に元のトークンが Azure Portal 上に復元されます。 このトークンを削除して DEP 登録をブロックするには、Azure Portal でトークンを削除します。 

## <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>macOS Sierra デバイスで数字のパスワードを使用する

現在、macOS Sierra デバイスのデバイス制限プロファイルで **[必要なパスワードの種類]** に **[数字]** を選択すると、**[英数字]** が強制的に適用されます。 これらのデバイスで数字のパスワードを使用する場合は、この設定を構成しないでください。
この問題は、macOS の今後のバージョンで修正される可能性があります。

これらの設定の詳細については、「[Microsoft Intune での macOS デバイスの制限設定](device-restrictions-macos.md)」をご覧ください。

## <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>一部のデバイスで Windows 情報保護ポリシーを保存できない

Intune に登録されていないデバイスでは、Windows 情報保護ポリシー設定の **[Corporate Identify]\(業務用の特定\)** フィールドにプライマリ ドメインのみを指定できます。
(**[詳細設定]** > **[ネットワーク境界]** > **[Add a protected domain]\(保護されているドメインの追加\)** で追加ドメインを追加する場合に、ポリシーを保存できません。 表示されるエラー メッセージはまもなく変更され、より正確な内容となる予定です。

## <a name="status-blades-for-migrated-policies-do-not-work"></a>移行したポリシーの状態を示すブレードが機能しない

クラシック ポータルから移行したポリシーの状態に関する情報は、Azure Portal では表示できません。 ただし、クラシック ポータルでこれらのポリシーに関するレポートを表示することは引き続き可能です。
移行した構成ポリシーの状態に関する情報を表示するには、Azure Portal でポリシーを再作成します。

