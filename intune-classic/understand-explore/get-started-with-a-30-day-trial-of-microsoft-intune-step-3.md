---
title: "無料試用版でユーザーとデバイスを編成するグループを作成する"
description: "Microsoft Intune の 30 日間無料試用版にサインアップするときに、デバイス グループとユーザー グループを作成する方法を説明します。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7162cad3-5c14-43f3-a760-833ffd7786b1
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 084cc155a64a58582e3008df10e86c1e5266054d
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="create-groups-to-organize-evaluation-subscription-users-and-devices"></a>試用版のサブスクリプションのユーザーとデバイスを編成するグループを作成する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune の [グループ] を使用すると、デバイスとユーザーを柔軟に管理できます。 グループは、組織ごとのニーズ (地理的位置、部門、ハードウェアの特性など) に合わせて設定できます。一連のユーザーに対するポリシーの設定から、一連のデバイスに対するアプリケーションの展開まで、さまざまな管理タスクをそれらのグループを使って一度に実行することができます。

## <a name="create-a-device-group"></a>デバイス グループを作成する
デバイス グループを使用してソフトウェアおよび更新を展開し、Microsoft Intune エージェントの設定と Windows ファイアウォールの設定に関するポリシーを構成します。 たとえば、"My Trial Devices" というグループを設定するには、次の手順に従います。

1.  [Intune 管理コンソール](https://manage.microsoft.com/)で、**[グループ]** &gt; **[概要]** &gt; **[グループの作成]** を選択します。

2.  **[グループ名]** に “My Trial Devices” と入力し、親グループ一覧から **[すべてのデバイス]** を選択して、**[次へ]** を選択します。

3.  **[メンバーシップの基準の定義]** ページで、 **[すべてのデバイス]** を選択して、グループにモバイル デバイスとコンピューターの両方が含まれることを示します。

4.  **[ダイレクト メンバーシップの定義]** ページで、**[次へ]** をクリックします。 以前作成したグループに一部のデバイスが含まれていない場合、ここでデバイスを指定して、新しいグループに追加することができます。

5.  **[概要]** ページで、実行する操作を確認し、**[完了]** を選択します。

新しく作成したグループは、 **[グループ]** 一覧の **[グループ]** ワークスペースにある **[すべてのデバイス]**の下に表示されます。 ここから、グループを編集または削除することもできます。

## <a name="create-a-user-group"></a>ユーザー グループを作成する
ソフトウェアやデバイスのポリシーは、ユーザー グループを使用して展開します。 たとえば、"My Trial Users" というグループを設定するには、次の手順に従います。

1.  [Intune 管理コンソール](https://manage.microsoft.com/)で、**[グループ]** &gt; **[概要]** &gt; **[グループの作成]** を選択します。

2.  **[グループ名]** に “My Trial Users” と入力し、親グループ一覧から **[すべてのユーザー]** を選択して、**[次へ]** を選択します。

3.  **[メンバーシップの基準の定義]** ページで、 **[グループのメンバーシップ]** を **[親グループのすべてのユーザー]**に設定します。

4.  **[メンバーを除外するセキュリティ グループ]** の横の **[参照]** を選択し、**[Company Administrator]** を選択します。 このように除外することにより、Company Administrator アカウント (またはテナント管理者とも呼ばれます) に影響することなく、My Trial Users グループを管理できます。

5.  **[ダイレクト メンバーシップの定義]** ページで、**[次へ]** をクリックします。 ここでは何も操作する必要はありません。Company Administrator を除いて、My Trial Users グループにすべてのユーザーを含めるからです。

6.  **[概要]** ページで、実行する操作を確認し、**[完了]** を選択します。

新しく作成したグループは、 **[グループ]** 一覧の **[グループ]** ワークスペースにある **[すべてのユーザー]**の下に表示されます。 ここから、グループを編集または削除することもできます。

グループの使用方法の詳細については、「[Microsoft Intune でユーザーとデバイスの管理にグループを使用する](/intune-classic/Deploy-Use/use-groups-to-manage-users-and-devices-with-microsoft-intune)」をご覧ください。

## <a name="next-steps"></a>次のステップ
[ポリシーを作成する](get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)  
