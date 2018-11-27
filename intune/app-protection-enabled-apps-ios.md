---
title: アプリ保護ポリシーのある iOS アプリ
titlesuffix: Microsoft Intune
description: 保護ポリシー付きの iOS アプリでできることについて説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 586d9440-3813-4dec-b865-8bd319befde0
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 667d5df5d53a9248137274cf7abe5b7fde5bf8bb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181940"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>アプリ保護ポリシーを使用して iOS アプリを管理するときの注意点

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

アプリ保護ポリシーを使用する場合の iOS アプリのユーザー エクスペリエンスについて説明します。 アプリ保護ポリシーは、アプリが作業コンテキストで使用されている場合にのみ適用されます。 たとえば、仕事用アカウントを使用してアプリにアクセスするときや、会社の OneDrive の保存先に格納されているファイルにアクセスするときです。
##  <a name="accessing-apps"></a>アプリへのアクセス

デバイスが **Intune に登録されていない**場合、ユーザーはアプリを初めて使用すると、アプリの再起動を求められます。  再起動すると、アプリ保護ポリシーをアプリに適用することができます。 次のスクリーンショットは、Skype アプリを使用した場合の例を示しています。


![暗証番号 (PIN) を求めるプロンプトを表示している iOS のスクリーン ショット](./media/ios-pin-prompt.png)

**Intune の管理対象として登録された**デバイスの場合、エンドユーザーにはアプリが管理された状態にあることを示すメッセージが表示されます。

![会社によって管理された状態にあることを示すメッセージと、暗証番号 (PIN) を求めるプロンプトが表示されている iOS デバイスのスクリーンショット](./media/ios-managed-devices-pin-prompt.png)

##  <a name="using-apps-with-multi-identity-support"></a>複数の ID を使用するアプリのサポート

アプリ保護ポリシーは、ユーザーが作業に関連するデータにアクセスしようとした場合にのみ有効になります。 ユーザーが個人的に使用するためにアプリへのアクセスを試みた場合には、異なる動作になる場合があります。 まだ保存されていない新しいコンテンツにもポリシーは適用されません。 新しいコンテンツは、SharePoint や OneDrive for Business などの企業内の場所に保存された後でのみ、会社の情報と見なされます。

複数の ID をサポートするアプリの場合、Intune は、ユーザーが作業データにアクセスする場合のみアプリ保護ポリシーを適用します。  たとえば、ユーザーに PIN プロンプトが表示されるとします。  **Outlook アプリ**では、ユーザーがアプリを起動したときにプロンプトが表示されます。 **OneDrive アプリ** では、ユーザーが作業アカウントを入力するときに、プロンプトが表示されます。  Microsoft **Word**、**PowerPoint**、**Excel** では、ユーザーが会社の OneDrive のドキュメントにアクセスしたときに、プロンプトが表示されます。
##  <a name="managing-user-accounts-on-the-device"></a>デバイスのユーザー アカウントの管理

Intune では、アプリ保護ポリシーをデバイスごとに 1 つのユーザー アカウントのみに展開することがサポートされます。

* 2 つ目のユーザーがデバイスでブロックされるかどうかは、使用中のアプリによって決まります。 ただし、どの場合でも、ポリシーの影響を受けるのは、アプリ保護ポリシーが適用される最初のユーザーのみです。
  * **Microsoft Word**、**Excel**、**PowerPoint** は、追加のユーザー アカウントへのアクセスをブロックしません。 ただし、ユーザー アカウントは、アプリ保護ポリシーの影響を受けません。

  * **OneDrive アプリと Outlook アプリ**では、作業アカウントは 1 つだけ使用できます。  作業アカウントを複数追加しようとしても、これらのアプリでブロックされます。  ただし、デバイスからユーザーを削除し、デバイスに別のユーザーを追加することができます。

* アプリ保護ポリシーが展開される前に、デバイスに複数のユーザー アカウントが既に存在していることがあります。 この場合、アプリ保護ポリシーが展開される最初のアカウントは、Intune アプリ保護ポリシーによって管理されます。


Intune が複数のユーザー アカウントを処理する方法については、次のサンプル シナリオをご覧ください。

ユーザー A は、**会社 X** と**会社 Y** という 2 つの会社で働いています。ユーザー A は各会社の作業アカウントを持っており、どちらの会社も Intune を使用してアプリ保護ポリシーを展開しています。 **会社 X** は、**会社 Y** の**前に**アプリ保護ポリシーを展開しています。アプリ保護ポリシーは、**会社 X** に関連付けられたアカウントに適用されますが、会社 Y に関連付けられたアカウントには適用されません。会社 Y のユーザー アカウントをアプリ保護ポリシーで管理するには、ユーザー A が、会社 X のユーザー アカウントを削除する必要があります。
### <a name="adding-a-second-account"></a>2 つ目のアカウントの追加

iOS デバイスを使用している場合は、同じデバイスに 2 つ目の作業アカウントを追加しようとすると、ブロック メッセージが表示されることがあります。  アカウントが表示され、削除するアカウントを選択できるようになります。

![ブロック メッセージと、[はい] と [いいえ] オプショを表示しているダイアログ ボックスのスクリーンショット](./media/ios-switch-user.PNG)

## <a name="next-steps"></a>次の手順
[アプリ保護ポリシーを使用して Android アプリを管理するときの注意点](app-protection-enabled-apps-android.md)
### <a name="see-also"></a>関連項目
[Microsoft Intune でのアプリ保護ポリシーの作成と展開](app-protection-policies.md)
