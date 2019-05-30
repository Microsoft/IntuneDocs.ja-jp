---
title: Microsoft Intune を使用して Office 365 を macOS デバイスにインストールする
titleSuffix: ''
description: Microsoft Intune を使用し、Office 365 アプリを macOS デバイスにインストールする方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 618557c129b693ad035dd82c823db43dcca2ee4d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66049459"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Microsoft Intune を使用して macOS デバイスに Office 365 を割り当てる

このアプリの種類では、Office 365 2016 アプリを macOS デバイスに簡単に割り当てることができます。 このアプリの種類を使用すると、Word、Excel、PowerPoint、Outlook、OneNote をインストールできます。 アプリケーションのセキュリティを強化し、最新の状態に保つために、これらのアプリには Microsoft AutoUpdate (MAU) が付属しています。 必要なアプリは、Intune コンソールのアプリ一覧に 1 つのアプリとして表示されます。


## <a name="before-you-start"></a>開始する前に

macOS に Office 365 を追加し始める前に、次の詳細を理解してください。

- これらのアプリを展開するデバイスでは、macOS 10.10 以降を実行している必要があります。
- Intune は、Office 2016 for Mac スイートに含まれる Office アプリの追加のみをサポートします。
- Intune でアプリ スイートをインストールするときに、Office アプリが開いている場合は、ユーザーは保存されていないファイルのデータを失う可能性があります。

## <a name="create-and-configure-the-app-suite"></a>アプリ スイートの作成と構成

**[アプリ]** ウィンドウから Office 365 を追加します。
1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ウィンドウで、**[クライアント アプリ]** を選択します。
4. **[クライアント アプリ]** ワークロード ウィンドウで、**[管理]** の **[アプリ]** を選択します。 
5. **[追加]** を選択します。
6. **[アプリの種類]** 一覧で、**[Office 365 スイート]** グループの **[macOS]** を選択します。
7. アプリ スイートに関する情報を指定するには、**[アプリ スイートの情報]** を選択します。  
    この情報は、Intune でアプリ スイートを識別し、ユーザーが会社のポータルでアプリを探す場合に役立ちます。
8. 次の情報を入力します。
    - **[スイート名]**: 会社のポータルに表示される、アプリ スイートの名前を入力します。 使用するスイート名はすべて一意にします。 同じアプリ スイート名が 2 つ存在する場合、会社のポータルではそのアプリのいずれかのみがユーザーに表示されます。
    - **[スイートの説明]**: アプリ スイートの説明を入力します。
    - **[発行元]**: Microsoft が発行者として表示されます。
    - **[カテゴリ]**: 1 つ以上の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 この設定を行うと、会社のポータルを閲覧するときに、ユーザーがアプリ スイートを探しやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]**: ユーザーがアプリを参照するとき、会社のポータルのメイン ページにアプリ スイートが目立つように表示するには、このオプションを選びます。
    - **[情報 URL]**: このアプリに関する情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[プライバシー URL]**: このアプリのプライバシー情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[開発者]**: Microsoft が開発者として表示されます。
    - **[所有者]**: Microsoft が所有者として表示されます。
    - **[メモ]**: (省略可能) このアプリに関連付けるメモを入力します。
    - **[ロゴ]**: ユーザーがポータル サイトを閲覧するとき、アプリと一緒に Office 365 のロゴが表示されます。
9. **[OK]** を選択します。
10. **[アプリの追加]** ウィンドウで **[追加]** を選択します。  
    アプリの一覧に、このスイートが 1 つのエントリとして表示されます。

## <a name="configure-app-assignments"></a>アプリの割り当てを構成する

この手順では、アプリ スイートの割り当てを構成します。 

1. アプリの一覧で **[Office 365]** アプリ スイートを選択し、**[Office 365]** 概要ウィンドウを表示します。
2. **[Office 365]** ウィンドウで **[割り当て]** を選択します。
3. アプリ スイートを使用するグループを追加するには、**[グループの追加]** を選択します。  
    **[グループの追加]** ウィンドウが表示されます。
4. **[割り当ての種類]** を **[必須]** または **[使用可能]** に設定します。
5. 選択したグループにスイートを割り当てます。 詳細については、「[Microsoft Intune を使用してアプリをグループに割り当てる方法](apps-deploy.md)」を参照してください。

    >[!Note]
    > Intune を使用して Office 365 アプリ スイートをアンインストールすることはできません。

5. **[割り当て]** ウィンドウで **[OK]** を選択します。
6. **[グループの追加]** ウィンドウで **[OK]** を選択します。
7. 割り当てを確定するには、**[保存]** を選択します。

## <a name="next-steps"></a>次の手順

- Windows 10 デバイスに Office 365 アプリを追加する方法については、[Microsoft Intune を使用して Windows 10 デバイスに Office 365 ProPlus 2016 アプリを割り当てる方法](apps-add-office365.md)に関するページを参照してください。
- アプリ割り当てをユーザーのグループに追加したり、除外したりする方法については、「[アプリ割り当ての組み込みと除外](apps-inc-exl-assignments.md)」を参照してください。
