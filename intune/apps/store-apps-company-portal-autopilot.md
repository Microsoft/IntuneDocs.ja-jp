---
title: Autopilot でプロビジョニングされたデバイス用に Windows 10 ポータル サイト アプリを追加して割り当てる
titleSuffix: Microsoft Intune
description: Autopilot でプロビジョニングされたデバイス用に Windows 10 ポータル サイト アプリを Intune に追加して割り当てる
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c13d8d774037f0d2db5832af7f39c864330fef30
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/25/2020
ms.locfileid: "77577286"
---
# <a name="add-and-assign-the-windows-10-company-portal-app-for-autopilot-provisioned-devices"></a>Autopilot でプロビジョニングされたデバイス用に Windows 10 ポータル サイト アプリを追加して割り当てる

デバイスの管理およびアプリのインストールのために、ユーザーはポータル サイト アプリを使用できます。 Windows 10 ポータル サイト アプリを Intune から直接割り当てることができます。 

## <a name="prerequisites"></a>[前提条件]

Windows 10 Autopilot でプロビジョニングされたデバイスの場合は、ビジネス向け Microsoft Store アカウントを Intune に関連付けることをお勧めします。 詳細については、「[ビジネス向け Microsoft Store のボリューム購入アプリを Microsoft Intune で管理する方法](~/apps/windows-store-for-business.md)」を参照してください。

以下の手順を使用して、ポータル サイト (オフライン) がインストールされるように選択します。 ポータル サイト アプリは、Autopilot グループに割り当てられるとデバイスのコンテキストでインストールされ、ユーザーがログインする前にデバイスにインストールされます。 

## <a name="configure-settings-to-show-offline-apps"></a>オフライン アプリ表示するように設定を構成する
1. 自分の管理アカウントを使って[ビジネス向け Microsoft Store](https://www.microsoft.com/business-store) にサインインします。
2. ウィンドウの上部付近にある **[管理]** タブを選択します。
3. 左側のウィンドウで、 **[設定]** を選択します。
4. **[Shopping experience]\(ショッピング体験\)** の **[Show offline apps]\(オフライン アプリの表示\)** を **[オン]** に設定します。  
    オフラインのライセンスされたアプリが表示されます。

## <a name="get-the-offline-company-portal-app"></a>オフラインのポータル サイト アプリを入手する
1. **ポータル サイト** アプリを検索して選択します。
2. **[ライセンスの種類]** を **[オフライン]** に設定します。
3. **[アプリの取得]** を選択し、オフラインのポータル サイト アプリを取得して、インベントリに追加します。

## <a name="assign-the-company-portal-app"></a>ポータル サイト アプリを割り当てる
1. 管理者アカウントを使用して  [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431)  にサインインします。 
2. 右側のペインで  **[アプリ]**   タブを選択します。 
3.  **[プラットフォーム別]** で **[Windows]** を選択します。 
4.  **[Company Portal (Offline)]\(ポータル サイト (オフライン)\)** を選択します。   
5. 同期スケジュールの完了を待つか、Microsoft Endpoint Manager admin center から手動による同期を実行する必要があります。
6. 選択した Autopilot デバイス グループに、必要なアプリとしてポータル サイト アプリを割り当てます。

## <a name="next-steps"></a>次のステップ

- アプリの割り当てに関する詳細については、[グループへのアプリの割り当て](apps-deploy.md)に関するページを参照してください。

