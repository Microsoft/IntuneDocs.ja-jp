---
title: "アプリ保護ポリシー付きの iOS アプリ | Microsoft Docs"
description: "このトピックでは、アプリ保護ポリシーを使用して iOS アプリを管理するときの注意点について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 92a91fab353c78c751ae5eb25c9853df5cbcfe53
ms.contentlocale: ja-jp
ms.lasthandoff: 05/31/2017


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>アプリ保護ポリシーを使用して iOS アプリを管理するときの注意点

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

 このトピックでは、アプリ保護ポリシーが適用されているアプリを使用するときのユーザー エクスペリエンスについて説明します。 アプリ保護ポリシーが適用されるのは、仕事でアプリが使用される場合に限られます。たとえば、職場のアカウントを使用してアプリにアクセスしたり、会社の OneDrive 事業拠点に格納されたファイルにアクセスしたりする場合です。

##  <a name="access-apps"></a>アプリにアクセスする

デバイスが**Intune に登録されていない**場合、ユーザーはアプリを初めて使用すると、アプリの再起動を求められます。 再起動すると、アプリ保護ポリシーをアプリに適用することができます。 

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

**Intune の管理対象として登録された**デバイスの場合、ユーザーにはアプリが管理された状態にあることを示すメッセージが表示されます。

##  <a name="use-apps-with-multi-identity-support"></a>複数の ID に対応しているアプリを使用する

複数の ID をサポートするアプリの場合、アプリが作業コンテキストで利用されているときにアプリ保護ポリシーが適用されていれば、仕事用や個人用など、複数のアカウントを利用して同じアプリにアクセスできます。  

たとえば、ユーザーが職場のデータにアクセスすると、暗証番号 (PIN) を求めるプロンプトが表示されます。 **Outlook アプリ**の場合、ユーザーにはアプリの起動時に、暗証番号 (PIN) の入力を求めるプロンプトが表示されます。 **OneDrive アプリ**の場合、ユーザーが職場のアカウントを入力するとき、PIN の入力が求められます。  Microsoft **Word**、**PowerPoint**、**Excel** の場合、会社の OneDrive for Business 拠点に保存されているドキュメントにユーザーがアクセスするとき、PIN の入力が求められます。

- Intune で [MAM と複数の ID](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) をサポートするアプリについての詳細を参照してください。

アプリ保護ポリシーは仕事関連でのみ適用されます。 そのため、仕事で使用する場合と個人的に使用する場合でアプリの動作が異なることがあります。

##  <a name="manage-user-accounts-on-the-device"></a>デバイスのユーザー アカウントの管理

Intune では、アプリ保護ポリシーの展開は、デバイスごとに 1 ユーザー アカウントに限られます。

* 2 つ目のユーザーがデバイスでブロックされるかどうかは、使用中のアプリによって決まります。 ただし、どの場合でも、ポリシーの影響を受けるのは、アプリ保護ポリシーが適用される最初のユーザーのみです。
  * **Microsoft Word**、**Excel**、**PowerPoint** では、2 つ目のユーザー アカウントがブロックされることはありませんが、2 つ目のユーザー アカウントがアプリ保護ポリシーの影響を受けることはありません。  

  * **OneDrive アプリ**と **Outlook アプリ**では、職場のアカウントは 1 つだけ使用できます。 これらのアプリに複数の職場のアカウントを追加することはできません。 ただし、デバイス上のユーザーを削除して、別のユーザーを追加することはできます。

* アプリ保護ポリシーを展開する前にデバイスに複数の既存のユーザー アカウントがある場合は、アプリ保護ポリシーが展開される最初のアカウントが Intune アプリ保護ポリシーによって管理されます。


次のサンプル シナリオを読んで、複数のユーザー アカウントがどのように処理されるかを深く理解してください。

ユーザー A は、**会社 X** と会社 **会社 Y** という 2 つの会社で働いています。ユーザー A は各会社の作業アカウントを持っており、どちらの会社も Intune を使用してアプリ保護ポリシーを展開しています。 **会社 X** は、**会社 Y** の**前に**アプリ保護ポリシーを展開しています。アプリ保護ポリシーは、**会社 X** に関連付けられたアプリ保護ポリシーに適用され、会社 Y に関連付けられたアカウントには適用されません。会社 Y に関連付けられたユーザー アカウントをアプリ保護ポリシーで管理する場合は、会社 X に関連付けられたユーザー アカウントを削除する必要があります。

### <a name="add-a-second-account"></a>2 つ目のアカウントを追加する

iOS デバイスを使用している場合は、そのデバイスに 2 つ目の作業アカウントを追加しようとすると、ブロック メッセージが表示されることがあります。 アカウントが表示され、削除するアカウントを選択できるようになります。

## <a name="next-steps"></a>次のステップ
[アプリ保護ポリシーを使用して Android アプリを管理するときの注意点](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### <a name="see-also"></a>関連項目
[Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)

