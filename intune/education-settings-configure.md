---
title: Windows 10 用に Intune 教育設定を構成する
titleSuffix: Microsoft Intune
description: Intune を使用して、管理対象デバイスで Windows 10 の教育設定を構成する方法について説明します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 413ad0bab32353fc6f5b401f9a7b910b6c5cb390
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31023310"
---
# <a name="how-to-configure-windows-10-education-settings-in-microsoft-intune"></a>Microsoft Intune で Windows 10 教育設定を構成する方法

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

教育プロファイルには、Windows テスト アプリを構成する詳細 (アカウント詳細を含む) とテスト URL を指定できます。 これを構成するとき、テスト アプリが開き、指定したテストが表示されます。テストが完了するまで他のアプリはデバイスで実行できません。

テスト アプリに関する詳細については、「[Windows 10 でテストを受ける](https://docs.microsoft.com/education/windows/take-tests-in-windows-10)」を参照してください。

## <a name="create-a-device-profile-containing-education-profile-settings"></a>教育プロファイル設定を含むデバイス プロファイルの作成

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]**、**[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[デバイス構成]** を選択します。
2. **[デバイス構成]** ウィンドウの **[管理]** セクションで、**[プロファイル]** を選択します。
3. [プロファイル] ウィンドウで **[プロファイルの作成]** を選択します。
4. **[プロファイルの作成]** ウィンドウで、デバイスの制限プロファイルの **[名前]** と **[説明]** を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、**[Windows 10 以降]** を選択します。
6. **[プロファイルの種類]** ドロップダウン リストで、**[教育プロファイル]** を選択します。 
7. **[設定]、[構成]** の順に選択し、**[テスト]** ウィンドウで次のように構成します。
    - **[アカウントの種類]** - ドロップダウン フィールドからアカウントの種類を選択します。
    - **アカウント ユーザー名** - テストで使用するアカウントのユーザー名を入力します。 ユーザー名には、ドメイン アカウント、Azure Active Directory (AAD) アカウント、ローカルのコンピューター アカウントを指定できます。
    - **評価 URL** - ユーザーに受けさせるテストの URL を指定します。 詳細については、テストに関するドキュメントを参照してください。
    - **画面の監視** - ユーザーがテストを受けている間、画面の行動を監視できるかどうかを指定します。
    - **テキストの候補** - ユーザーがテストを受けている間、テキスト候補の表示を許可するか、禁止します。
8. 完了したら、**[プロファイルの作成]** ウィンドウに戻り、**[作成]** をクリックします。

プロファイルが作成され、プロファイルの一覧ウィンドウに表示されます。

## <a name="next-steps"></a>次の手順

このプロファイルをグループに割り当てる場合は、[デバイス プロファイルを割り当てる方法](device-profile-assign.md)に関する記事を参照してください。



