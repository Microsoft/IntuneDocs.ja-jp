---
title: Microsoft Intune を使用して Office 365 を macOS デバイスにインストールする
titleSuffix: ''
description: Microsoft Intune を使用し、Office 365 アプリを macOS デバイスにインストールする方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3cf4c2abb5506f297af8a4e77145abea5360381b
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755359"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Microsoft Intune を使用して macOS デバイスに Office 365 を割り当てる

このアプリの種類では、Office 365 2016 アプリを macOS デバイスに簡単に割り当てることができます。 このアプリの種類を使用すると、Word、Excel、PowerPoint、Outlook、OneNote をインストールできます。 アプリケーションのセキュリティを強化し、最新の状態に保つために、これらのアプリには Microsoft AutoUpdate (MAU) が付属しています。 必要なアプリは、Intune コンソールのアプリ一覧に 1 つのアプリとして表示されます。


## <a name="before-you-start"></a>開始する前に

macOS に Office 365 を追加し始める前に、次の詳細を理解してください。

- これらのアプリを展開するデバイスでは、macOS 10.10 以降を実行している必要があります。
- Intune は、Office 2016 for Mac スイートに含まれる Office アプリの追加のみをサポートします。
- Intune でアプリ スイートをインストールするときに、Office アプリが開いている場合は、ユーザーは保存されていないファイルのデータを失う可能性があります。

## <a name="select-the-office-365-suite-app-type"></a>Office 365 スイート アプリの種類を選択する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** の順に選択します。
3. **[アプリケーションの種類の選択]** ペインの **[Office 365 スイート]** セクションで **[macOS]** を選択します。
4. **[選択]** をクリックします。 **[Add Office 365 Suite]\(Office 365 スイートの追加 \)** ステップが表示されます。

## <a name="step-1---app-suite-information"></a>ステップ 1 - アプリ スイートの情報

この手順では、アプリ スイートに関する情報を指定します。 この情報は、Intune でアプリ スイートを識別し、ユーザーが会社のポータルでアプリを探す場合に役立ちます。

1. **[アプリ スイートの情報]** ページで、既定値を確認または変更できます。
    - **[スイート名]** : 会社のポータルに表示される、アプリ スイートの名前を入力します。 使用するスイート名はすべて一意にします。 同じアプリ スイート名が 2 つ存在する場合、会社のポータルではそのアプリのいずれかのみがユーザーに表示されます。
    - **[スイートの説明]** : アプリ スイートの説明を入力します。 たとえば、含めるように選択したアプリを一覧表示できます。
    - **[発行元]** : Microsoft が発行者として表示されます。
    - **[カテゴリ]** : (省略可能) 1 つ以上の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 この設定を行うと、会社のポータルを閲覧するときに、ユーザーがアプリ スイートを探しやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]** : ユーザーがアプリを参照するとき、会社のポータルのメイン ページにアプリ スイートが目立つように表示するには、このオプションを選びます。
    - **[情報 URL]** : このアプリに関する情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[プライバシー URL]** : このアプリのプライバシー情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[開発者]** : Microsoft が開発者として表示されます。
    - **[所有者]** : Microsoft が所有者として表示されます。
    - **[メモ]** : このアプリに関連付けるメモを入力します。
    - **[ロゴ]** : ユーザーがポータル サイトを閲覧するとき、アプリと一緒に Office 365 のロゴが表示されます。
2. **[次へ]** をクリックして **[スコープ タグ]** ページを表示します。

## <a name="step-2---select-scope-tags-optional"></a>ステップ 2 - スコープのタグを選択する (省略可能)
スコープのタグを使って、Intune のクライアント アプリの情報を表示できるユーザーを決定することができます。 スコープのタグの詳細については、[分散 IT のためのロールベースのアクセス制御とスコープのタグの使用](../fundamentals/scope-tags.md)に関するページをご覧ください。

1. **[スコープ タグを選択]** をクリックして、必要に応じてアプリ スイートのスコープ タグを追加します。 
2. **[次へ]** をクリックして、 **[割り当て]** ページを表示します。

## <a name="step-3---assignments"></a>ステップ 3 - 割り当て

1. アプリ スイートに **[必須]** または **[登録済みデバイスで使用可能]** グループ割り当てを選択します。 詳細については、「[ユーザーとデバイスを整理するためのグループを追加する](~/fundamentals/groups-add.md)」と「[Microsoft Intune を使用してアプリをグループに割り当てる](apps-deploy.md)」を参照してください。

    >[!Note]
    > Intune を使用して Office 365 for macOS アプリ スイートをアンインストールすることはできません。

2. **[次へ]** をクリックして、 **[確認と作成]** ページを表示します。 

## <a name="step-4---review--create"></a>ステップ 4 - 確認と作成

1. アプリ スイートに入力した値と設定を確認します。
2. 完了したら、 **[作成]** をクリックしてアプリを Intune に追加します。

    作成した Office 365 Window 10 アプリ スイートの **[概要]** ブレードが表示されます。 アプリの一覧に、このスイートが 1 つのエントリとして表示されます。

## <a name="next-steps"></a>次のステップ

- Windows 10 デバイスに Office 365 アプリを追加する方法については、[Microsoft Intune を使用して Windows 10 デバイスに Office 365 ProPlus 2016 アプリを割り当てる方法](apps-add-office365.md)に関するページを参照してください。
- アプリ割り当てをユーザーのグループに追加したり、除外したりする方法については、「[アプリ割り当ての組み込みと除外](apps-inc-exl-assignments.md)」を参照してください。
