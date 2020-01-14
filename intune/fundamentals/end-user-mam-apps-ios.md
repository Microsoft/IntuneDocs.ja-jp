---
title: アプリ保護ポリシーのある iOS アプリ
description: このトピックでは、アプリ保護ポリシーを使用して iOS アプリを管理するときの注意点について説明します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 165ce160339647e396b9cfc3a8374f21c77665f8
ms.sourcegitcommit: f9dc50642efa8656054ef67f9335b9b46b655f93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2020
ms.locfileid: "75606623"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>アプリ保護ポリシーを使用して iOS アプリを管理するときの注意点

Intune のアプリ保護ポリシーは、職場または学校用のアプリに適用されます。 つまり、従業員や学生が個人のコンテキストでアプリを使用しているときは、ユーザー エクスペリエンスの違いに気付かないことがあります。 ただし、職場または学校のコンテキストでは、アカウントに関する決定を求めるメッセージを受け取ったり、設定を更新したり、ヘルプを求めたりすることがあります。 この記事では、Intune で保護されたアプリにアクセスして使用するときのユーザー エクスペリエンスについて説明します。  

## <a name="access-apps"></a>アプリにアクセスする

デバイスが**Intune に登録されていない**場合、ユーザーはアプリを初めて使用すると、アプリの再起動を求められます。 アプリ保護ポリシーがアプリに適用されるように、再起動する必要があります。

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

**Intune の管理対象として登録された**デバイスの場合、ユーザーにはアプリが管理された状態にあることを示すメッセージが表示されます。

## <a name="use-apps-with-multi-identity-support"></a>複数の ID に対応しているアプリを使用する

複数の ID をサポートするアプリでは、異なる職場アカウントと個人アカウントを使用して同じアプリにアクセスできます。 デバイスの PIN の入力などのアプリ保護ポリシーは、ユーザーが職場または学校のコンテキストでこれらのアプリにアクセスするとアクティブ化されます。   

ポリシーの構成方法によっては、ユーザーに対する PIN のプロンプトがすべてのアプリで異なる場合があります。  たとえば、次のようにポリシーを構成することができます。       
* Microsoft Outlook では、ユーザーがアプリを起動すると PIN の入力を求めるプロンプトが表示されます。 
* OneDrive では、ユーザーが職場アカウントにサインインするときに PIN の入力を求められます。  
* Microsoft Word、PowerPoint、Excel では、会社の OneDrive for Business 拠点に保存されているドキュメントにユーザーがアクセスするときに、PIN の入力を求められます。  

- Intune で [アプリ保護と複数の ID](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) をサポートするアプリについての詳細を参照してください。  

## <a name="manage-user-accounts-on-the-device"></a>デバイスのユーザー アカウントの管理  

Intune のアプリ保護ポリシーでは、ユーザーはアプリごとに 1 つのマネージド職場または学校アカウントに制限されます。 アプリ保護ポリシーでは、ユーザーが追加できるアンマネージド アカウントの数は制限されません。   

- ユーザーが 2 つ目の管理アカウントを追加しようとすると、使用する管理アカウントの選択を求められます。 ユーザーが 2 番目のアカウントを追加すると、最初のアカウントは削除されます。
- ユーザーの別のアカウントに保護ポリシーを追加すると、ユーザーは使用するマネージド アカウントの選択を求められます。 その他のアカウントは削除されます。 

ユーザーによっては、マネージド アカウントの切り替えまたは選択のオプションが表示されない場合があります。 このオプションは、次のデバイスでは使用できません。
* Intune で管理されている  
* サードパーティのエンタープライズ モビリティ管理ソリューションによって管理され、IntuneMAMUPN の設定で構成されている 

次のシナリオ例では、複数のユーザー アカウントを処理する方法を説明します。  

ユーザー A は、**会社 X** と会社 **会社 Y** という 2 つの会社で働いています。ユーザー A は各会社の作業アカウントを持っており、どちらの会社も Intune を使用してアプリ保護ポリシーを展開しています。 **会社 X** は、**会社 Y** の**前に**アプリ保護ポリシーを展開しています。**会社 X** に関連付けられているアカウントが、最初にアプリの保護ポリシーを取得します。 会社 Y に関連付けられたユーザー アカウントをアプリ保護ポリシーで管理する場合は、会社 X に関連付けられたユーザー アカウントを削除して、会社 Y に関連付けられたアカウントを追加する必要があります。  

## <a name="next-steps"></a>次のステップ

[アプリ保護ポリシーを使用して Android アプリを管理するときの注意点](end-user-mam-apps-android.md)
