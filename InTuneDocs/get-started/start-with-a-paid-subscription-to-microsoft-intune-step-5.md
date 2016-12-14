---
title: "ユーザーとデバイスを編成するグループを作成する | Microsoft Intune"
description: "Intune サブスクリプションのユーザーとグループを作成します"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5fdf98c8-fe67-4d7a-9837-ed1234348014
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 85b2e7c50f4ea1e07bd1474e3902cebcbccc1467


---


# <a name="create-groups-to-organize-users-and-devices"></a>ユーザーとデバイスを編成するグループを作成する
Intune の [グループ] を使用すると、デバイスとユーザーを柔軟に管理できます。 グループは、組織ごとのニーズ (地理的位置、部門、ハードウェアの特性など) に合わせて設定できます。一連のユーザーに対するポリシーの展開から、一連のデバイスに対するアプリケーションの展開まで、まざまな管理タスクをそれらのグループを使って実行することができます。

## <a name="group-management-moving-to-azure-ad"></a>Azure AD へのグループ管理の移行

**2016 年 11 月以降**、Azure Active Directory (AD) ポータルでは新しいアカウントでユーザーとデバイス グループが管理されます。 2016 年 12 月には、Intune 製品チームは既存顧客の新しい Azure AD ベースのグループ管理操作環境への移行を開始します。 すべてのユーザーおよびデバイス グループは、Azure AD セキュリティ グループに移行されます。 お客様の日常業務への影響を最小限に抑えることができ、お客様のユーザーに影響がないものと予想されるまで、移行は開始されません。 また、アカウント移行前にはお客様にご連絡します。


>[!IMPORTANT]
>
>Intune ポータルでグループ ワークスペースを開いたときに、Azure Active Directory ポータルへのリンクと共に、"**Intune ユーザー グループは、Azure Active Directory のグループとして管理されるようになりました**" というメッセージが表示された場合は、Intune でのグループ管理に*新しい* Azure AD セキュリティ グループのアプローチが既に使用されています。 グループの作成方法の詳細については、「[Azure Active Directory でのグループの管理](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal)」を参照してください。
>
>Azure AD ポータルへのリンクが表示されない場合は、グループ管理にはまだ Intune ポータルが使用されています。

## <a name="group-management-in-the-intune-portal"></a>Intune ポータルでのグループ管理

デバイスとユーザー グループは両方とも Intune 管理コンソールの [グループ] ワークスペースで作成します。

![管理コンソールの [グループ] ワークスペース](./media/groups.png)


> [!TIP]
> グループの使用方法の詳細については、「[Microsoft Intune でユーザーとデバイスの管理にグループを使用する](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune)」をご覧ください。


## <a name="create-a-device-group"></a>デバイス グループを作成する
デバイス グループは、アプリや更新プログラムの展開のほか、各種機能の構成に使用します。 たとえば、"My Devices" というグループを設定するには、次の手順に従います。

1.  [Intune 管理コンソール](https://manage.microsoft.com/)で、**[グループ]** > **[概要]** > **[グループの作成]** を選択します。

2.  **[グループ名]** に「My Devices」と入力し、親グループ一覧から、**[すべてのデバイス]** を選択して、**[次へ]** を選択します。

3.  **[メンバーシップの基準の定義]** ページで、 **[すべてのデバイス]** を選択して、グループにモバイル デバイスとコンピューターの両方が含まれることを示します。

4.  **[ダイレクト メンバーシップの定義]** ページで、**[次へ]** をクリックします。 以前作成したグループに一部のデバイスが含まれていなかった場合、ここでデバイスを指定して、新しいグループに追加することができます。

5.  **[概要]** ページで、実行する操作を確認し、**[完了]** を選択します。

新しく作成したグループは、**[グループ]** 一覧の **[グループ]** ワークスペースにある **[すべてのデバイス]** の下に表示されます。 ここから、グループを編集または削除することもできます。

## <a name="create-a-user-group"></a>ユーザー グループを作成する
ソフトウェアやデバイスのポリシーは、ユーザー グループを使用して展開します。 たとえば、"Intune Users" というグループを設定するには、次の手順に従います。

1.  [Intune 管理コンソール](https://manage.microsoft.com/)で、**[グループ]** > **[概要]** > **[グループの作成]** を選択します。

2.  **[グループ名]** に「Intune Users」と入力し、親グループ一覧から、**[すべてのユーザー]** を選択して、**[次へ]** を選択します。

3.  **[メンバーシップの基準の定義]** ページで、 **[グループのメンバーシップ]** を **[親グループのすべてのユーザー]**に設定します。

4.  **[メンバーを除外するセキュリティ グループ]** の横の **[参照]** を選択し、**[Company Administrator]** を選択します。 この除外設定により、Company Administrator アカウント (またはテナント管理者) に影響することなく、Intune Users グループを管理できます。

5.  **[ダイレクト メンバーシップの定義]** ページで、**[次へ]** をクリックします。 ここでは何も操作する必要はありません。Company Administrator を除いて、Intune Users グループにすべてのユーザーを含めるからです。

6.  **[概要]** ページで、実行する操作を確認し、**[完了]** を選択します。

新しく作成したグループは、**[グループ]** 一覧の **[グループ]** ワークスペースにある **[すべてのユーザー]** の下に表示されます。 ここから、グループを編集または削除することもできます。

>[!div class="step-by-step"]

>[&larr;**Intune のライセンスを管理する**](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)       [**ポリシーとアプリを作成する**&rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)  



<!--HONumber=Dec16_HO2-->


