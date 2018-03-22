---
title: "Microsoft Intune を使用して Office 365 を macOS デバイスにインストールする"
titlesuffix: 
description: "Microsoft Intune を使用し、Office 365 アプリを macOS デバイスにインストールする方法について説明します。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8de14184c4d23adc79d5b519fdcf272f0d7f6804
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>Microsoft Intune を使用して Office 365 を macOS デバイスに割り当てる方法

**ストア アプリ**という種類では、Office 365 アプリを macOS デバイスに簡単に割り当てることできます。 このアプリの種類では、Word、Excel、PowerPoint、Outlook、OneNote をインストールできます。 これらのアプリには Microsoft AutoUpdate (MAU) も付属しており、アプリをより安全かつ最新に保つことができます。 必要なアプリは、Intune コンソールのアプリ一覧に 1 つのアプリとして表示されます。


## <a name="before-you-start"></a>開始する前に

macOS に Office 365 を追加し始める前に、次の詳細を理解する必要があります。

- これらのアプリを展開するデバイスでは、macOS 10.10 以降を実行している必要があります。
- Intune は、Office 2016 for Mac スイートに含まれる Office アプリの追加のみをサポートします。
- Intune でアプリ スイートをインストール中に Office アプリを開くと、エンド ユーザーは保存されていないファイルのデータを失う可能性があります。

## <a name="create-and-configure-the-app-suite"></a>アプリ スイートの作成と構成

**[アプリ]** ブレードを使用して Office 365 を追加します。
1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]**、**[監視 + 管理]**、**[Intune]** の順に選択します。
3. **[Intune]** ブレードから **[モバイル アプリ]** を選択します。
4. **[モバイル アプリ]** ワークロードで、**[管理]** セクションの **[アプリ]** を選択します。 
5. **[追加]** を選択し、**[アプリの追加]** ブレードを表示します。
6. **[アプリの種類]** 一覧で、**[Office 365 スイート]** グループの **[macOS]** を選択します。
7. **[アプリ スイートの情報]** を選択し、アプリ スイートに関する情報を指定します。 この情報は、Intune でアプリ スイートを識別したり、ユーザーが会社のポータル サイト アプリで探したりする場合に役立ちます。
8.  次の情報を指定します。
    - **[スイート名]** - 会社のポータルに表示される、アプリ スイートの名前を入力します。 使用するスイート名はすべて一意にします。 同じアプリ スイート名が 2 つ存在する場合、会社のポータルではそのアプリのいずれかのみがユーザーに表示されます。
    - **[スイートの説明]** - アプリ スイートの説明を入力します。
    - **[発行者]** - Microsoft が発行者として表示されます。
    - **[カテゴリ]** - 1 つまたは複数の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 この設定を行うと、会社のポータルを閲覧するときに、ユーザーがアプリ スイートを探しやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]** - この設定では、ユーザーがアプリを探すときに、会社のポータルのメイン ページでアプリ スイートが目立つように表示されます。
    - **[情報 URL]** (省略可能) - このアプリに関する情報が含まれる Web サイトの URL を入力します。 この URL は会社のポータルでユーザーに表示されます。
    - **[プライバシー URL]** (省略可能) - このアプリのプライバシー情報が含まれる Web サイトの URL を入力します。 この URL は会社のポータルでユーザーに表示されます。
    - **[開発者]** - Microsoft が開発者として表示されます。
    - **[所有者]** - Microsoft が所有者として表示されます。
    - **[メモ]** (省略可能) - このアプリに関連付けるメモを入力します。
    - **[ロゴ]** - ユーザーがポータル サイトを閲覧するとき、Office 365 ロゴがアプリと共に表示されます。
9.  **[アプリ情報]** ブレードで **[OK]** をクリックします。
10. **[アプリの追加]** ブレードで **[追加]** をクリックします。
    アプリの一覧に、このスイートが 1 つのエントリとして表示されます。

## <a name="configure-app-assignments"></a>アプリの割り当てを構成する

この手順では、アプリ スイートの割り当てを構成します。 

1. アプリの一覧で **[Office 365]** アプリ スイートを選択し、**[Office 365]** 概要ブレードを表示します。
2. **[Office 365]** ブレードから **[割り当て]** をクリックします。
3. **[グループの追加]** をクリックし、アプリ スイートを使用するグループを追加します。 **[グループの追加]** ブレードが表示されます。
3. **[割り当ての種類]** を **[必須]** に設定します。
4. 選択したグループにスイートを割り当てます。 詳細については、「[How to assign apps to groups with Microsoft Intune (Microsoft Intune を使ってアプリをグループに割り当てる方法)](apps-deploy.md)」を参照してください。

    >[!Note]
    > Office 365 アプリ スイートが必須のグループの場合、Microsoft Intune からアンインストールすることはできません。

5. **[割り当て]** ブレードで **[OK]** を選択します。
6. **[グループの追加]** ブレードで **[OK]** を選択します。
7. **[保存]** を選択して割り当てを確定します。

## <a name="next-steps"></a>次の手順

- Windows 10 デバイスに Office 365 アプリを追加する方法については、「[How to assign Office 365 ProPlus 2016 apps to Windows 10 devices with Microsoft Intune (Microsoft Intune で Windows 10 デバイスに Office 365 ProPlus 2016 アプリを割り当てる方法)](apps-add-office365.md)」をご覧ください。
- アプリ割り当てをユーザーのグループに追加したり、除外したりする方法については、「[アプリ割り当ての組み込みと除外](apps-inc-exl-assignments.md)」を参照してください。
