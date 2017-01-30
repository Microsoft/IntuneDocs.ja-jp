---
title: "iOS アプリと MAM ポリシー | Microsoft Docs"
description: "このトピックでは、iOS アプリがモバイル アプリ管理ポリシーを使用して管理されている場合に予想される結果について説明します。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b068da7685792757825a4bc0d555e28ee0168cb1
ms.openlocfilehash: f5a26d3d5ed060571892d91637dc12cae08f1a69


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-mam-policies"></a>MAM ポリシーを使用して iOS アプリを管理するときの注意点

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

 このトピックでは、MAM (モバイル アクセス管理) ポリシーを使用する場合のアプリのユーザー エクスペリエンスについて説明します。 MAM ポリシーが適用されるのは、仕事でアプリが使用される場合に限られます。たとえば、職場のアカウントを使用してアプリにアクセスしたり、会社の OneDrive 事業拠点に格納されたファイルにアクセスしたりする場合です。

##  <a name="access-apps"></a>アプリにアクセスする

デバイスが**Intune に登録されていない**場合、ユーザーはアプリを初めて使用すると、アプリの再起動を求められます。  再起動すると、MAM ポリシーをアプリに適用することができます。 

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

**Intune の管理対象として登録された**デバイスの場合、ユーザーにはアプリが管理された状態にあることを示すメッセージが表示されます。

![iOS デバイスのスクリーンショット。アプリが会社により管理されていることを伝えるメッセージと PIN プロンプト。](../media/appmanagement/ios-managed-devices-pin-prompt.png)

##  <a name="use-apps-with-multi-identity-support"></a>複数の ID に対応しているアプリを使用する

MAM ポリシーは仕事関連でのみ適用されます。 そのため、仕事で使用する場合と個人的に使用する場合でアプリの動作が異なることがあります。

 たとえば、ユーザーが職場のデータにアクセスすると、暗証番号 (PIN) を求めるプロンプトが表示されます。 **Outlook アプリ**の場合、ユーザーにはアプリの起動時に、暗証番号 (PIN) の入力を求めるプロンプトが表示されます。 **OneDrive アプリ**の場合、ユーザーが職場のアカウントを入力するとき、PIN の入力が求められます。  Microsoft **Word**、**PowerPoint**、**Excel** の場合、会社の OneDrive for Business 拠点に保存されているドキュメントにユーザーがアクセスするとき、PIN の入力が求められます。

##  <a name="manage-user-accounts-on-the-device"></a>デバイスのユーザー アカウントの管理

Intune では、MAM ポリシーの展開は、デバイスごとに 1 ユーザー アカウントに限られます。

* 2 つ目のユーザーがデバイスでブロックされるかどうかは、使用中のアプリによって決まります。 ただし、どの場合でも、ポリシーの影響を受けるのは、MAM ポリシーが適用される最初のユーザーだけです。
  * **Microsoft Word**、**Excel**、および **PowerPoint** では、2 つ目のユーザー アカウントがブロックされることはありませんが、2 つ目のユーザー アカウントが MAM ポリシーの影響を受けることはありません。  

  * **OneDrive アプリ**と **Outlook アプリ**では、職場のアカウントは 1 つだけ使用できます。 これらのアプリに複数の職場のアカウントを追加することはできません。 ただし、デバイス上のユーザーを削除して、別のユーザーを追加することはできます。

* MAM ポリシーを展開する前にデバイスに複数の既存のユーザー アカウントがある場合は、MAM ポリシーが展開される最初のアカウントが Intune MAM ポリシーによって管理されます。


次のサンプル シナリオを読んで、複数のユーザー アカウントがどのように処理されるかを深く理解してください。

ユーザー A は、**会社 X** と会社 **会社 Y** という 2 つの会社で働いています。ユーザー A は各会社の作業アカウントを持っており、どちらの会社も Intune を使用してMAM ポリシーを展開しています。 **会社 X** は、**会社 Y** の**前に** MAM ポリシーを展開しています。MAM ポリシーは、**会社 X** に関連付けられた MAM ポリシーに適用され、会社 Y に関連付けられたアカウントには適用されません。会社 Y に関連付けられたユーザー アカウントを MAM ポリシーで管理する場合は、会社 X に関連付けられたユーザー アカウントを削除する必要があります。

### <a name="add-a-second-account"></a>2 つ目のアカウントを追加する

iOS デバイスを使用している場合は、そのデバイスに 2 つ目の作業アカウントを追加しようとすると、ブロック メッセージが表示されることがあります。 アカウントが表示され、削除するアカウントを選択できるようになります。

![ブロック メッセージと、[はい] と [いいえ] オプショを表示しているダイアログ ボックスのスクリーンショット](../media/AppManagement/iOS_SwitchUser.PNG)
## <a name="next-steps"></a>次のステップ
[MAM ポリシーを使用して Android アプリを管理するときの注意点](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### <a name="see-also"></a>関連項目
[Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO3-->


