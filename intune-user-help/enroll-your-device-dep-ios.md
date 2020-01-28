---
title: 組織から提供された iOS デバイスを管理登録します。 | Microsoft Docs
description: 組織が購入して提供している iOS デバイスを Intune に登録する方法について説明します
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: f4e7d87e-56d1-43e4-8e88-2f62cf0999e2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 6c1b6417489d1443596113a18476b9cbc8f3832e
ms.sourcegitcommit: 8cc3eca2bce847b0c2b40d8531698e21df848878
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2020
ms.locfileid: "75951456"
---
# <a name="enroll-your-organization-provided-ios-device-in-management"></a>組織から提供された iOS デバイスを管理登録する

新しい iOS デバイスを Intune で管理する方法について説明します。  

職場または学校から支給される iOS デバイスは多くの場合、受け取る前に事前構成されています。 初めてデバイスの電源を入れてサインインすると、事前構成済みの設定が組織からデバイスに送信されます。 デバイスのセットアップが完了すると、職場または学校のリソースにアクセスできるようになります。  

セットアップを始めるには、デバイスの電源を入れ、職場または学校の資格情報でサインインします。 以下では、セットアップ アシスタントを使用する手順と表示される画面について説明します。

## <a name="what-is-apple-dep"></a>Apple DEP とは

組織は、*Apple Device Enrollment Program* (DEP) を利用してデバイスを購入することがあります。 Apple DEP を利用することで、組織は iOS または macOS デバイスを大量に購入できます。 その後、組織は Intune などの適切なモバイル デバイス管理プロバイダーでデバイスを構成して管理できます。 Apple DEP についての情報がさらに必要な管理者は、「[Apple の Device Enrollment Program を使用して iOS デバイスを自動登録する](/intune/enrollment/device-enrollment-program-enroll-ios)」をご覧ください。

## <a name="set-up-your-ios-device"></a>iOS デバイスを設定する

会社支給のデバイスではなく個人所有の iOS デバイスを使用している場合は、[個人デバイスと Bring Your Own デバイス](enroll-your-device-in-intune-ios.md)に関するページをご覧ください。  

1. iOS デバイスをオンにします。
2. **[Language\(言語\)]** を選択した後、デバイスを Wi-Fi に接続します。
3. **[Set up iOS device]\(iOS デバイスのセットアップ\)** 画面で、 **[Set up as new device]\(新しいデバイスとしてセットアップする\)** を選択します。  
4. Wi-Fi に接続すると、 **[Configuration\(構成\)]** 画面が表示されます。 **[[Your Company] will automatically configure your device]\([会社] がデバイスを自動的に構成します\)** と表示されます。

   **Configuration allows [Your Company] to manage this device over the air\(構成により [会社] はデバイスを無線で管理できます。\)An administrator can help you set up email and network accounts, install and configure apps, and manage settings remotely.\(メール アカウントとネットワーク アカウントの設定、アプリのインストールと構成、設定のリモート管理については、管理者が支援します。\)An administrator may disable features, install and remove apps, monitor and restrict your Internet traffic and remotely erase this device.\(管理者は、機能の無効化、アプリのインストールと削除、インターネット トラフィックの監視と制限、このデバイスのリモート消去を行うことができます。\)**

   **Configuration is provided by: [Your Company's] iOS Team [Address]\(構成の提供元: [会社の] iOS チーム [アドレス]\)**

5. Apple ID でログインします。 ログインすると、ポータル サイト アプリをインストールし、会社が電子メールやアプリなどの自社のリソースにアクセスできるようにする、管理プロファイルをインストールすることができます。
6. **使用条件**に同意し、診断情報を Apple に送信するかどうかを決定します。
7. 登録が完了すると、他の操作の実行を要求される場合があります。 これらの手順には、電子メールにアクセスするためのパスワードの入力や、パスコードの設定が含まれる場合があります。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。
