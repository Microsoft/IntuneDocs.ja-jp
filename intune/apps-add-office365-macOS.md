---
title: "Intune を使用して Office 365 を macOS デバイスにインストールする"
titlesuffix: Azure portal
description: "Intune を使用して、Office 365 アプリを macOS デバイスに簡単にインストールする方法について説明します。"
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5e0ad0b99a2c8a602b5e542530a1d437065461b2
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>Microsoft Intune を使用して Office 365 を macOS デバイスに割り当てる方法

このアプリの種類では、Office 365 アプリを macOS デバイスに簡単に割り当てることできます。 この新しいアプリの種類では、Word、Excel、PowerPoint、Outlook、OneNote をインストールできます。 これらのアプリには Microsoft AutoUpdate (MAU) も付属しており、アプリをより安全かつ最新に保つことができます。 必要なアプリは、Intune コンソールのアプリ一覧に 1 つのアプリとして表示されます。


## <a name="before-you-start"></a>開始する前に

- これらのアプリを展開するデバイスでは、macOS 10.10 以降を実行している必要があります。
- Intune は、Office 2016 for Mac スイートに含まれる Office アプリの追加のみをサポートします。
- Intune でアプリ スイートをインストール中に Office アプリを開くと、エンド ユーザーは保存されていないファイルのデータを失う可能性があります。


## <a name="get-started"></a>作業開始
**[アプリ]** ブレードを使用して Office 365 を追加します。
1.  Azure Portal にサインインします。
2.  **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3.  **[Intune]** ブレードで、**[モバイル アプリ]** を選びます。
4.  **[モバイル アプリ]** ワークロードで、**[管理]** グループの **[アプリ]** を選択します。 **[追加]** を選びます。
5.  **[アプリの追加]** ブレードで、**[Office 365]** > **[macOS]** を選択します。
6.  **[追加]** を選択します。

## <a name="configure-the-app-suite"></a>アプリ スイートの構成

アプリ スイートに関する情報を指定します。 この情報は、アプリ スイートを Intune で識別したり、ユーザーが会社のポータル サイト アプリで探したりする場合に役立ちます。

1.  **[アプリの追加]** ブレードで、**[アプリ スイートの情報]** を選択します。
2.  次の情報を指定します。
    - **[スイート名]** - 会社のポータルに表示される、アプリ スイートの名前を入力します。 使用するスイート名はすべて一意にします。 同じアプリ スイート名が 2 つ存在する場合、会社のポータルではそのアプリのいずれかのみがユーザーに表示されます。
    - **[スイートの説明]** - アプリ スイートの説明を入力します。
    - **[発行者]** - Microsoft が発行者として表示されます。
    - **[カテゴリ]** - 必要に応じて、1 つ以上の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 この操作を行うと、会社のポータルを閲覧するときに、ユーザーがアプリ スイートを探しやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]** - ユーザーがアプリを探すときに、会社のポータルのメイン ページでアプリ スイートを目立つように表示します。
    - **[情報 URL]** - 必要に応じて、このアプリに関する情報が含まれる Web サイトの URL を入力します。 この URL は会社のポータルでユーザーに表示されます。
    - **[プライバシー URL]** - 必要に応じて、このアプリのプライバシー情報が含まれる Web サイトの URL を入力します。 この URL は会社のポータルでユーザーに表示されます。
    - **[開発者]** - Microsoft が開発者として表示されます。
    - **[所有者]** - Microsoft が所有者として表示されます。
    - **[メモ]** - このアプリに関連付けるメモを入力します。
    - **[アイコンのアップロード]** - ユーザーが会社のポータルを参照するときに、アプリに表示されるアイコンをアップロードします。
3.  **[OK]** を選択します。 アプリの一覧に、このスイートが 1 つのエントリとして表示されます。

## <a name="configure-app-assignments"></a>アプリの割り当てを構成する

この手順では、アプリ スイートの割り当てを構成します。 使用可能なアプリの種類はまもなく公開されます。

1.  アプリの一覧でアプリのスイートを選択し、**[割り当て]** を選択します。
2.  **[グループの選択]** を選択します。
3.  選択したグループにスイートを割り当てます。 詳細については、「[How to assign apps to groups with Microsoft Intune (Microsoft Intune を使ってアプリをグループに割り当てる方法)](/intune/apps-deploy)」を参照してください。
4.  各グループに、**[Require Install]\(インストールが必要\)** を選択します。
        >[!Note]
        > You cannot uninstall Office 365 through Intune.

5. **[保存]** を選択して割り当てを確定します。

## <a name="next-steps"></a>次の手順

Windows 10 デバイスに Office 365 アプリを追加する方法については、「[How to assign Office 365 ProPlus 2016 apps to Windows 10 devices with Microsoft Intune (Microsoft Intune で Windows 10 デバイスに Office 365 ProPlus 2016 アプリを割り当てる方法)](/intune/apps-add-office365)」をご覧ください。
