---
title: iOS デバイスで管理対象アプリを使用する | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3232c5c1-cb9f-45ca-806f-7e74eeb3533e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5ae4e454a0ca41858cb670790fd5acd4d6bf998a
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2019
ms.locfileid: "67546614"
---
# <a name="use-managed-apps-on-your-ios-device"></a>iOS デバイスで管理対象アプリを使用する

管理対象アプリとは、そのアプリでアクセス可能な会社のデータを保護できるよう会社のサポートがセットアップ可能なアプリです。 管理対象アプリ内の会社のデータに iOS デバイスでアクセスする場合、アプリの動作が予期したものとは少し異なる場合があります。 たとえば、保護された会社のデータをコピーして貼り付けできない、またはそのデータを特定の場所に保存できない場合があります。

また、異なる管理対象アプリがデバイス上で連携して動作し、会社のデータを保護しながら、日常のタスクを実行することもできます。 たとえば、1 つの管理対象アプリで会社のファイルを開き、別の管理対象アプリでそのファイルを表示する必要がある場合、ファイルを表示できるようにする管理対象アプリが自動的に開きます。 必要なアプリが使用できない場合、管理されているドキュメント内からドキュメントを開くまたは Web リンクにアクセスするなどの特定の操作が行えない可能性があります。

管理対象アプリで会社のデータにアクセスすると、開こうとしているアプリが管理されていることを通知する以下のようなメッセージが表示されます。

![managed-apps-message-ios](./media/managed-apps-message.png)

## <a name="how-do-i-get-managed-apps"></a>管理対象アプリを取得する方法  
管理対象アプリはいくつかの方法で取得できます。

- デバイスが Microsoft Intune に登録されるときに、ポータル サイト アプリまたはポータル Web サイトからアプリをインストールするか、または会社のサポートがアプリをデバイスにインストールする場合があります。 登録については、「[Intune に iOS デバイスを登録する](enroll-your-device-in-intune-ios.md)」または「[Intune に macOS デバイスを登録する](enroll-your-device-in-intune-macos.md)」を参照してください。

- アプリ ストアからアプリをインストールし、Intune で管理されている会社のユーザー アカウントでサインインします。

会社のサポートは、ユーザーがインストールするアプリ用に複数のライセンスを購入している場合があります。 Apple Volume Purchase Program 契約の同意を求めるメッセージが表示された場合、これは正常であり、同意することができます。 同意しない場合は、アプリをインストールすることができません。

## <a name="available-apps"></a>Available apps   
 組織では、職場または学校で適切かつ便利なアプリを選択します。 ポータル サイト内にはこうしたアプリのみが存在します。   

 アプリは、デバイスの種類に基づいて使用が許可されます。 たとえば、iOS 用ポータル サイト アプリを使用している場合、iOS アプリにはアクセスできますが、Android アプリにはアクセスできません。   

## <a name="request-an-app-for-work-or-school"></a>職場または学校用のアプリを要求する   
 必要なアプリがあるが、ポータル サイト内に存在しない場合は、そのアプリを要求できます。 ポータル サイト アプリの **[サポート]** タブで、**ヘルプデスク**の連絡先詳細を確認してください。同じ連絡先情報は、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)でも確認できます。   
 

## <a name="what-can-my-company-support-manage-in-an-app"></a>会社のサポートがアプリで管理できるもの  
以下は、会社のサポートがアプリで管理でき、デバイス上での会社データとのやり取りに影響するオプションの例です。

- 特定の web サイトへのアクセス

- アプリケーション間のデータ転送

- ファイルの保存

- コピーと貼り付けの操作

- 暗証番号 (pin) のアクセスの要件

- 会社の資格情報を使用したサインイン

- クラウドへのバックアップ機能

- スクリーン ショットを撮る機能

- データの暗号化の要件

デバイスの管理対象アプリの詳細については、会社のサポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。
