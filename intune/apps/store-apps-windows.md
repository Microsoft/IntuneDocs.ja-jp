---
title: Microsoft Store アプリを Microsoft Intune に追加する
titleSuffix: ''
description: Microsoft Store (Windows ストア) アプリを Microsoft Intune に追加する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3c13d7960c0bb5c73908a0a574ab7d6c169d6460
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563434"
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Microsoft Store アプリを Microsoft Intune に追加する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

アプリの割り当て、監視、構成、または保護を行うには、対象のアプリを事前に Intune に追加しておく必要があります。 

## <a name="add-an-app-to-intune"></a>Intune にアプリを追加する
次の操作を行うことで、Intune に Microsoft Store アプリを追加できます。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** を選択します。
3. **[アプリの追加]** ウィンドウの **[アプリの種類]** で **[Windows]** を選び、 **[アプリ情報]** を選択します。
4. **[アプリ情報]** ウィンドウで、アプリの情報を追加します。 選択したアプリによっては、このウィンドウ内の一部の値が自動的に入力されている場合があります。
    - **名前**: アプリの名前を入力します。この名前は会社のポータルに表示されます。 使用するアプリ名が一意であることを確認してください。 アプリ名が重複している場合、会社のポータルでは 1 つの名前のみがユーザーに表示されます。
    - **説明**:アプリの説明を入力します。 この説明は会社のポータルでユーザーに表示されます。
    - **[発行元]** : アプリの発行元の名前を入力します。
    - **[アプリ ストアの URL]** : 作成するアプリのアプリ ストア URL を入力します。 URL は、目的のアプリの [Microsoft Store](https://store.microsoft.com) を検索することで見つけることができます。 ブラウザーのアドレス バーから URL を使用します。
    - **[カテゴリ]** : (省略可能) 1 つ以上の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 そうすると、会社のポータルを閲覧するときに、ユーザーがアプリを探しやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]** : ユーザーがアプリを参照するとき、会社のポータルのメイン ページにアプリ スイートが目立つように表示するには、このオプションを選びます。
    - **[情報 URL]** : このアプリに関する情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[プライバシー URL]** : このアプリのプライバシー情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[開発者]** : (省略可能) アプリ開発者の名前を入力します。
    - **[所有者]** : (省略可能) このアプリの所有者の名前 ("*人事部*" など) を入力します。
    - **[メモ]** : (省略可能) このアプリに関連付けるメモを入力します。
    - **[ロゴ]** : (省略可能) アプリに関連付けるアイコンをアップロードします。 ユーザーが会社のポータルを参照するとき、アプリにこのアイコンが表示されます。
5. **[OK]** を選択します。
6. **[追加]** を選択します。

作成したアプリはアプリの一覧に表示され、選択したグループに割り当てることができるようになります。 Microsoft Store アプリは、割り当ての種類が **[登録済みデバイスで使用可能]** であるグループにのみ割り当てることができます (ユーザーは、Intune ポータル サイトまたは Web サイトからアプリをインストールします)。

## <a name="next-steps"></a>次の手順
- [アプリをグループに割り当てる](apps-deploy.md)
