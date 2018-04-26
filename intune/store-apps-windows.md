---
title: Microsoft Store アプリを Microsoft Intune に追加する方法
titleSuffix: ''
description: Microsoft Store (Windows ストア) アプリを Microsoft Intune に追加する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 511cf2e01a2f5db93f0e0db9dbe2a32326c17723
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Microsoft Store アプリを Microsoft Intune に追加する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

アプリの割り当て、監視、構成、または保護を行うには、対象のアプリを事前に Intune に追加しておく必要があります。 次の手順で、Microsoft Intune に Microsoft Store アプリを追加することができます。

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]**、**[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[モバイル アプリ]** を選択します。
4. **[モバイル アプリ]** ワークロードで、**[管理]** > **[アプリ]** の順に選択します。
5. アプリの一覧の上にある **[追加]** を選択します。
6. **[アプリの追加]** ウィンドウの **[アプリの種類]** で **[Windows]** を選択し、**[アプリ情報]** を選択します。
7. **[アプリ情報]** ウィンドウで、以下の情報を構成します。 構成が終わったら、**[OK]** をクリックします。 選択したアプリによっては、このウィンドウ内の一部の値が自動的に入力されている場合があります。
    - **名前** - アプリの名前を入力します。この名前は会社のポータルに表示されます。 使用するアプリ名はすべて一意にします。 同じアプリ名が 2 つ存在する場合、会社のポータルではそのいずれかのみがユーザーに表示されます。
    - **説明** - ポータル サイトでユーザーに表示するアプリの説明を入力します。
    - **[発行元]** - アプリの発行元の名前を入力します。
    - **[アプリ ストアの URL]** - 作成するアプリのアプリ ストア URL を入力します。
    - **カテゴリ (省略可能)** - ポータル サイトを閲覧するときにユーザーがアプリを検索しやすくする、組み込みアプリのカテゴリまたは作成したカテゴリを 1 つ以上選択します。
    - **[会社のポータルでおすすめアプリとして表示します]** - ユーザーがアプリを探す際に、会社のポータルのメイン ページでアプリを目立つように表示します。
    - **[情報 URL]** - 必要に応じて、このアプリに関する情報が含まれる Web サイトの URL を入力します。 この URL は会社のポータルでユーザーに表示されます。
    - **[プライバシー URL]** - 必要に応じて、このアプリのプライバシー情報が含まれる Web サイトの URL を入力します。 この URL は会社のポータルでユーザーに表示されます。
    - **[開発者]** - 必要に応じて、アプリ開発者の名前を入力します。
    - **[所有者]** - 必要に応じて、このアプリの所有者の名前 ("**人事部**" など) を入力します。
    - **[メモ]** - このアプリに関連付けるメモを入力します。
    - **[ロゴ]** -- アプリに関連付けるアイコンをアップロードします。 ユーザーが会社のポータルを参照するとき、アプリにこのアイコンが表示されます。
8. 完了したら、**[アプリの追加]** ウィンドウで、**[追加]** を選択します。

作成したアプリはアプリの一覧に表示され、選択したグループに割り当てることができるようになります。 

## <a name="next-steps"></a>次の手順
- [アプリをグループに割り当てる方法](apps-deploy.md)