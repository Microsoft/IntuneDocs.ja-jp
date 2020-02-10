---
title: Microsoft Intune に Android Enterprise システム アプリを追加する
titleSuffix: ''
description: Microsoft Intune に Enterprise システム アプリを追加する方法について説明します。
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
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 613369070d847265f371a7b228a2b6d81bf813fe
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755257"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Microsoft Intune に Android Enterprise システム アプリを追加する

アプリをデバイスまたはユーザーのグループに割り当てる前に、最初にアプリを Microsoft Intune に追加する必要があります。 システム アプリは Android Enterprise デバイスでサポートされています。 システム アプリは [Android Enterprise 専用デバイス](../enrollment/android-kiosk-enroll.md)または[フル マネージド デバイス](../enrollment/android-fully-managed-enroll.md)に対して有効にすることができます。

## <a name="add-the-app"></a>アプリを追加する

Azure portal から Intune に Android Enterprise システム アプリを追加するには、次の手順を実行します。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** の順に選択します。
3. **[アプリケーションの種類の選択]** ペインの使用できる **[その他]** の種類で、 **[Android Enterprise system app]\(Android Enterprise システム アプリ\)** を選択しします。
4. **[選択]** をクリックします。 **[アプリの追加]** 手順が表示されます。
**[アプリ情報 ]** ページで、アプリの詳細を追加します。
    - **[アプリ名]** :アプリの名前を入力します。
    - **[発行元]** : アプリの発行元の名前を入力します。  
    - **[パッケージ名]** :パッケージ名を入力します。 Intune によって、パッケージ名が有効であることが検証されます。
5. **[次 へ]** をクリックして **[スコープ タグ]** ページを表示します。
8. **[スコープ タグを選択]** をクリックして、必要に応じてアプリのスコープ タグを追加します。 詳細については、「[分散 IT にロールベースのアクセス制御 (RBAC) とスコープのタグを使用する](~/fundamentals/scope-tags.md)」を参照してください。
9. **[次へ]** をクリックして、 **[割り当て]** ページを表示します。
10. アプリのグループ割り当てを選択します。 詳細については、「[ユーザーとデバイスを整理するためのグループを追加する](~/fundamentals/groups-add.md)」を参照してください。 
11. **[次へ]** をクリックして、 **[確認と作成]** ページを表示します。 アプリに入力した値と設定を確認します。
12. 完了したら、 **[作成]** をクリックしてアプリを Intune に追加します。

作成したアプリの **[概要]** ブレードが表示されます。

> [!NOTE]
> デバイスの OEM と連携して、有効または無効にするアプリのパッケージ名を検索する必要があります。

作成したアプリはアプリの一覧に表示され、選択したグループに割り当てることができるようになります。 

Android Enterprise システム アプリでは、既にプラットフォームに含まれているアプリを有効または無効にします。 アプリを有効にするには、システム アプリを **[必須]** に割り当てます。 アプリを無効にするには、システム アプリを **[アンインストール]** として割り当てます。 システム アプリを利用可能として、ユーザーに割り当てることはできません。


## <a name="next-steps"></a>次のステップ

- [アプリをグループに割り当てる](apps-deploy.md)
