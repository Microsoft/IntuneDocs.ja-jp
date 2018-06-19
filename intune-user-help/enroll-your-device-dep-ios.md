---
title: iOS デバイスを Device Enrollment Program に登録する | Microsoft Docs
description: Intune で DEP に iOS デバイスを登録する方法について説明します
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f4e7d87e-56d1-43e4-8e88-2f62cf0999e2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 9d1154d942069ad69294d4235c894f88513dd848
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31016409"
---
# <a name="enroll-your-ios-device-in-intune-with-the-device-enrollment-program"></a>Intune で iOS デバイスを Device Enrollment Program に登録する

Device Enrollment Program は、大量の iOS デバイスを企業が容易に管理できるようにするため、Apple により提供されています。 個人所有のデバイスが許可されている会社のユーザーは、このページの手順ではなく、[標準的な iOS 登録手順](enroll-your-device-in-intune-ios.md)に従います。 会社から Device Enrollment Program の対象になっている iOS デバイスを支給されているユーザーは、以下を読んでください。

1. iOS デバイスをオンにします。 
2. **[Language\(言語\)]** を選択した後、デバイスを Wi-Fi に接続します。
3. **[Set up iOS device]\(iOS デバイスのセットアップ\)** 画面で、次を行うかどうかを選択します。 
 
   - **Set up as new device\(新しいデバイスとして設定する\)**
   - **Restore from iCloud backup\(iCloud のバックアップから復元する\)**
   - **Restore from iTunes backup\(iTunes のバックアップから復元する\)**

4. Wi-Fi に接続すると、**[Configuration\(構成\)]** 画面が表示されます。 **[[Your Company] will automatically configure your device]\([会社] がデバイスを自動的に構成します\)** と表示されます。

   **Configuration allows [Your Company] to manage this device over the air\(構成により [会社] はデバイスを無線で管理できます。\)An administrator can help you set up email and network accounts, install and configure apps, and manage settings remotely.\(メール アカウントとネットワーク アカウントの設定、アプリのインストールと構成、設定のリモート管理については、管理者が支援します。\)An administrator may disable features, install and remove apps, monitor and restrict your Internet traffic and remotely erase this device.\(管理者は、機能の無効化、アプリのインストールと削除、インターネット トラフィックの監視と制限、このデバイスのリモート消去を行うことができます。\)**
 
   **Configuration is provided by: [Your Company's] iOS Team [Address]\(構成の提供元: [会社の] iOS チーム [アドレス]\)**

5. Apple ID でログインします。 ログインすると、ポータル サイト アプリをインストールし、会社が電子メールやアプリなどの自社のリソースにアクセスできるようにする、管理プロファイルをインストールすることができます。 
6. **使用条件**に同意し、診断情報を Apple に送信するかどうかを決定します。
7. 登録が完了すると、他の操作の実行を要求される場合があります。 これらの手順には、電子メールにアクセスするためのパスワードの入力や、パスコードの設定が含まれる場合があります。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
