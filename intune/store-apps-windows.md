---
title: Microsoft Store アプリを Microsoft Intune に追加する
titleSuffix: ''
description: Microsoft Store (Windows ストア) アプリを Microsoft Intune に追加する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 990226cba088585021db691753c6a3a8063927d3
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347255"
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Microsoft Store アプリを Microsoft Intune に追加する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

アプリの割り当て、監視、構成、または保護を行うには、対象のアプリを事前に Intune に追加しておく必要があります。 

## <a name="add-an-app-to-intune"></a>Intune にアプリを追加する
次の操作を行うことで、Intune に Microsoft Store アプリを追加できます。

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。  
    Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[クライアント アプリ]** を選択します。
4. **[クライアント アプリ]** ワークロード ウィンドウで、**[管理]** の **[アプリ]** を選択します。
5. **[アプリ]** ウィンドウで **[追加]** を選択します。
6. **[アプリの追加]** ウィンドウの **[アプリの種類]** で **[Windows]** を選び、**[アプリ情報]** を選択します。
7. **[アプリ情報]** ウィンドウで、アプリの情報を追加します。 選択したアプリによっては、このウィンドウ内の一部の値が自動的に入力されている場合があります。
    - **[名前]**: アプリの名前を入力します。この名前は会社のポータルに表示されます。 使用するアプリ名が一意であることを確認してください。 アプリ名が重複している場合、会社のポータルでは 1 つの名前のみがユーザーに表示されます。
    - **[説明]**: アプリの説明を入力します。 この説明は会社のポータルでユーザーに表示されます。
    - **[発行元]**: アプリの発行元の名前を入力します。
    - **[アプリ ストアの URL]**: 作成するアプリのアプリ ストア URL を入力します。
    - **[カテゴリ]**: 必要に応じて、1 つ以上の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 そうすると、会社のポータルを閲覧するときに、ユーザーがアプリを探しやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]**: この設定では、ユーザーがアプリを探すときに、会社のポータルのメイン ページでアプリ スイートが目立つように表示されます。
    - **[情報 URL]**: 必要に応じて、このアプリに関する情報が含まれる Web サイトの URL を入力します。 この URL は会社のポータルでユーザーに表示されます。
    - **[プライバシー URL]**: 必要に応じて、このアプリのプライバシー情報が含まれる Web サイトの URL を入力します。 この URL は会社のポータルでユーザーに表示されます。
    - **[開発者]**: 必要に応じて、アプリ開発者の名前を入力します。
    - **[所有者]**: 必要に応じて、このアプリの所有者の名前 (*人事部*など) を入力します。
    - **[メモ]**: (省略可能) このアプリに関連付けるメモを入力します。
    - **[ロゴ]**: 必要に応じて、アプリに関連付けるアイコンをアップロードします。 ユーザーが会社のポータルを参照するとき、アプリにこのアイコンが表示されます。
8. **[OK]** を選択します。
9. **[追加]** を選択します。

作成したアプリはアプリの一覧に表示され、選択したグループに割り当てることができるようになります。 

## <a name="next-steps"></a>次の手順
- [アプリをグループに割り当てる](apps-deploy.md)
