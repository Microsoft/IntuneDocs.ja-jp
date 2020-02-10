---
title: Windows Phone 8.1 ストア アプリを Microsoft Intune に追加する
titleSuffix: ''
description: このトピックでは、Windows Phone 8.1 ストア アプリを Microsoft Intune に追加する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d43e0f913020e3e2e8b0ac463d5983447d7c1fa2
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754951"
---
# <a name="add-windows-phone-81-store-apps-to-microsoft-intune"></a>Windows Phone 8.1 ストア アプリを Microsoft Intune に追加する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

アプリをデバイスまたはユーザーのグループに割り当てる前に、最初にアプリを Microsoft Intune に追加する必要があります。 

## <a name="add-an-app-to-intune"></a>Intune にアプリを追加する
次の操作を行うことで、Azure Portal から Intune に Windows Phone 8.1 ストア アプリを追加できます。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** の順に選択します。
3. **[アプリの種類の選択]** ペインの使用できる **[ストア アプリ]** の種類で、 **[Windows Phone 8.1 ストア アプリ]** を選択します。
4. **[選択]** をクリックします。<br>
   **[アプリの追加]** 手順が表示されます。
5. Windows Phone 8.1 ストア アプリの **[アプリ情報]** を構成するには、[Microsoft ストア](https://www.microsoft.com/store/apps/windows-phone)に移動し、展開するアプリを検索します。 アプリのページを表示し、アプリの詳細をメモしておきます。 
6. **[アプリ情報 ]** ページで、アプリの詳細を追加します。
    - **名前**:アプリの名前を入力します。この名前は会社のポータルに表示されます。 使用するアプリ名が一意であることを確認してください。 アプリ名が重複している場合、会社のポータルでは 1 つの名前のみがユーザーに表示されます。
    - **説明**:アプリの説明を入力します。 この説明は会社のポータルでユーザーに表示されます。
    - **[発行元]** : アプリの発行元の名前を入力します。
    - **[アプリ ストアの URL]** : 作成するアプリのアプリ ストア URL を入力します。
    - **[カテゴリ]** : (省略可能) 1 つ以上の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 そうすると、会社のポータルを閲覧するときに、ユーザーがアプリを探しやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]** : ユーザーがアプリを参照するとき、会社のポータルのメイン ページにアプリ スイートが目立つように表示するには、このオプションを選びます。
    - **[情報 URL]** : このアプリに関する情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[プライバシー URL]** : このアプリのプライバシー情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[開発者]** : (省略可能) アプリ開発者の名前を入力します。
    - **[所有者]** : (省略可能) このアプリの所有者の名前 ("*人事部*" など) を入力します。
    - **[メモ]** : (省略可能) このアプリに関連付けるメモを入力します。
    - **[ロゴ]** : (省略可能) アプリに関連付けるアイコンをアップロードします。 ユーザーが会社のポータルを参照するとき、アプリにこのアイコンが表示されます。
7. **[次 へ]** をクリックして **[スコープ タグ]** ページを表示します。
8. **[スコープ タグを選択]** をクリックして、必要に応じてアプリのスコープ タグを追加します。 詳細については、「[分散 IT にロールベースのアクセス制御 (RBAC) とスコープのタグを使用する](~/fundamentals/scope-tags.md)」を参照してください。
9. **[次へ]** をクリックして、 **[割り当て]** ページを表示します。
10. アプリのグループ割り当てを選択します。 詳細については、「[ユーザーとデバイスを整理するためのグループを追加する](~/fundamentals/groups-add.md)」を参照してください。 
11. **[次へ]** をクリックして、 **[確認と作成]** ページを表示します。 アプリに入力した値と設定を確認します。
12. 完了したら、 **[作成]** をクリックしてアプリを Intune に追加します。

作成したアプリの **[概要]** ブレードが表示されます。


作成したアプリはアプリの一覧に表示され、選択したグループに割り当てることができるようになります。

## <a name="next-steps"></a>次のステップ

- [アプリをグループに割り当てる](apps-deploy.md)
