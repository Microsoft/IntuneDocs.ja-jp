---
title: アプリ保護ポリシーのある iOS アプリ
description: このトピックでは、アプリ保護ポリシーを使用して iOS アプリを管理するときの注意点について説明します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4e272a9d3bbe770a17f82bdf367b8394414eb90
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721631"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>アプリ保護ポリシーを使用して iOS アプリを管理するときの注意点

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

 このトピックでは、アプリ保護ポリシーが適用されているアプリを使用するときのユーザー エクスペリエンスについて説明します。 アプリ保護ポリシーが適用されるのは、仕事でアプリが使用される場合に限られます。たとえば、職場のアカウントを使用してアプリにアクセスしたり、会社の OneDrive 事業拠点に格納されたファイルにアクセスしたりする場合です。

## <a name="access-apps"></a>アプリにアクセスする

デバイスが**Intune に登録されていない**場合、ユーザーはアプリを初めて使用すると、アプリの再起動を求められます。 再起動すると、アプリ保護ポリシーをアプリに適用することができます。

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

**Intune の管理対象として登録された**デバイスの場合、ユーザーにはアプリが管理された状態にあることを示すメッセージが表示されます。

## <a name="use-apps-with-multi-identity-support"></a>複数の ID に対応しているアプリを使用する

複数の ID をサポートするアプリの場合、アプリが作業コンテキストで利用されているときにアプリ保護ポリシーが適用されていれば、仕事用や個人用など、複数のアカウントを利用して同じアプリにアクセスできます。  

たとえば、ユーザーが職場のデータにアクセスすると、暗証番号 (PIN) を求めるプロンプトが表示されます。 **Outlook アプリ**の場合、ユーザーにはアプリの起動時に、暗証番号 (PIN) の入力を求めるプロンプトが表示されます。 **OneDrive アプリ**の場合、ユーザーが職場のアカウントを入力するとき、PIN の入力が求められます。  Microsoft **Word**、**PowerPoint**、**Excel** の場合、会社の OneDrive for Business 拠点に保存されているドキュメントにユーザーがアクセスするとき、PIN の入力が求められます。

- Intune で [アプリ保護と複数の ID](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) をサポートするアプリについての詳細を参照してください。

アプリ保護ポリシーは仕事関連でのみ適用されます。 そのため、仕事で使用する場合と個人的に使用する場合でアプリの動作が異なることがあります。

## <a name="manage-user-accounts-on-the-device"></a>デバイスのユーザー アカウントの管理

複数 ID のアプリケーションでは、ユーザーが複数のアカウントを追加できます。  Intune APP は、1 つの管理アカウントのみをサポートします。  Intune APP では、管理されていないアカウントの数が制限されていません。

1 つのアプリケーションに 1 つの管理アカウントが存在する場合:
* ユーザーが 2 つ目の管理アカウントを追加しようとすると、使用する管理アカウントの選択を求められます。  その他のアカウントは削除されます。
* IT 管理者が 2 つ目の既存のアカウントにポリシーを追加すると、ユーザーは使用する管理アカウントの選択を求められます。  その他のアカウントは削除されます。

次のサンプル シナリオを読んで、複数のユーザー アカウントがどのように処理されるかを深く理解してください。

ユーザー A は、**会社 X** と会社 **会社 Y** という 2 つの会社で働いています。ユーザー A は各会社の作業アカウントを持っており、どちらの会社も Intune を使用してアプリ保護ポリシーを展開しています。 **会社 X** は、**会社 Y** の**前に**アプリ保護ポリシーを展開しています。**会社 X** に関連付けられているアカウントが、最初にアプリの保護ポリシーを取得します。 会社 Y に関連付けられたユーザー アカウントをアプリ保護ポリシーで管理する場合は、会社 X に関連付けられたユーザー アカウントを削除して、会社 Y に関連付けられたアカウントを追加する必要があります。

### <a name="add-a-second-account"></a>2 つ目のアカウントを追加する

iOS デバイスを使用している場合は、そのデバイスに 2 つ目の作業アカウントを追加しようとすると、ブロック メッセージが表示されることがあります。 アカウントが表示され、削除するアカウントを選択できるようになります。

## <a name="next-steps"></a>次の手順
[アプリ保護ポリシーを使用して Android アプリを管理するときの注意点](end-user-mam-apps-android.md)
