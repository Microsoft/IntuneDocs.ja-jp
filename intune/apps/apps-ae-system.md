---
title: Microsoft Intune に Android Enterprise システム アプリを追加する
titleSuffix: ''
description: Microsoft Intune に Enterprise システム アプリを追加する方法について説明します。
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
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d45455a97f8016527dce49839b5493f16b173d43
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563659"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Microsoft Intune に Android Enterprise システム アプリを追加する

アプリをデバイスまたはユーザーのグループに割り当てる前に、最初にアプリを Microsoft Intune に追加する必要があります。 システム アプリは Android Enterprise デバイスでサポートされています。 システム アプリは [Android Enterprise 専用デバイス](../enrollment/android-kiosk-enroll.md)または[フル マネージド デバイス](../enrollment/android-fully-managed-enroll.md)に対して有効にすることができます。

## <a name="add-the-app"></a>アプリを追加する

Azure portal から Intune に Android Enterprise システム アプリを追加するには、次の手順を実行します。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** の順に選択します。
3. **[アプリの追加]** ウィンドウで、使用可能な **[その他]** の種類に **[Android Enterprise システム アプリ]** を選択します。
4. アプリ情報を構成するには、 **[構成]** を選択し、次の情報を指定します。
    - **[アプリ名]** :アプリの名前を入力します。
    - **[発行元]** : アプリの発行元の名前を入力します。  
    - **[パッケージ名]** :パッケージ名を入力します。 Intune によって、パッケージ名が有効であることが検証されます。
5. **[OK]** を選択します。
6. **[追加]** を選択します。

> [!NOTE]
> デバイスの OEM と連携して、有効または無効にするアプリのパッケージ名を検索する必要があります。

作成したアプリはアプリの一覧に表示され、選択したグループに割り当てることができるようになります。 

Android Enterprise システム アプリでは、既にプラットフォームに含まれているアプリを有効または無効にします。 アプリを有効にするには、システム アプリを **[必須]** に割り当てます。 アプリを無効にするには、システム アプリを **[アンインストール]** として割り当てます。 システム アプリを利用可能として、ユーザーに割り当てることはできません。


## <a name="next-steps"></a>次の手順

- [アプリをグループに割り当てる](apps-deploy.md)
