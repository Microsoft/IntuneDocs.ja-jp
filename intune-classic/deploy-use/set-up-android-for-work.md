---
title: "Android for Work のセットアップ"
description: "Microsoft Intune を使用して Android for Work デバイスのモバイル デバイス管理 (MDM) を有効にします。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b2fdcea9-9ad7-4d73-88e2-854b7a774bb2
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: 366e2b281c05e1233c61f7f35a50700677ad4b79
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="enable-enrollment-of-android-for-work-devices"></a>Android for Work デバイスの登録を有効にする

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Android for Work デバイスの管理を有効にするには、Android for Work バインディングを Intune に追加する必要があります。 Android for Work をサポートするデバイスで、以前に Android デバイスとして登録していたデバイスを登録するには、デバイスの登録を解除してから、再登録する必要があります。

## <a name="add-android-for-work-binding-for-intune"></a>Intune 用に Android for Work のバインディングを追加する

1. **Intune をセットアップする**<br>
**Microsoft Intune** を[モバイル デバイス管理機関に設定](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-8#enable-device-enrollment)して、MDM の設定を行うことにより、モバイル デバイス管理を準備します (この作業をまだ行っていない場合)。

2. **Android for Work のバインディングを構成する**<br>
    Intune 管理者として [Microsoft Intune 管理コンソール](https://manage.microsoft.com)を開き、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Android for Work]** の順に選択し、 **[構成]** をクリックして Google Play の Android for Work Web サイトを開きます。 この操作で、ブラウザーの新しいタブが開きます。

3. **Google にログインする**<br>
   Google のサインイン ページで、このテナントのすべての Android for Work 管理タスクに関連付ける Google アカウントを入力します。 これは、お客様の組織の IT 管理者が Play for Work コンソールでアプリを管理および公開するときに共有する Google アカウントです。

4. **組織の詳細を指定する**<br>
   **[組織名]** に会社名を入力します。 **エンタープライズ モビリティ管理 (EMM) プロバイダー**の場合、*Microsoft Intune* と表示されます。 Android for Work の使用条件に同意し、**[確認]** をクリックします。 要求が処理されます。

## <a name="specify-android-for-work-enrollment-settings"></a>Android for Work 登録設定を指定する
   Android for Work は、特定の Android デバイスでのみサポートされています。 Google の [Android for Work の要件](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window")に関するページを参照してください。  Android for Work をサポートするデバイスは、従来の Android 管理もサポートします。  Intune では、Android for Work をサポートするデバイスの管理方法を指定できます。

   - **[すべてのデバイスを Android として管理する]** - Android for Work をサポートするデバイスを含め、すべて Android デバイスを従来の Android デバイスとして登録します。
   - **[サポートされるデバイスを Android for Work として管理する]** - Android for Work をサポートするすべてのデバイスが Android for Work デバイスとして登録されます。 Android for Work をサポートしないすべての Android デバイスは、従来の Android デバイスとして登録されます。
   - **[Manage supported devices for users only in these user groups as Android for Work (ユーザー グループのユーザーについてのみ、サポートされるデバイスを Android for Work として管理する)]** - Android for Work の管理を特定のユーザーのみを対象にします。 Android for Work をサポートするデバイスを登録した、選択したグループのメンバーのみが、Android for Work デバイスとして登録されます。 その他すべてのデバイスは Android デバイスとして登録されます。 これは Android for Work のパイロット中に役立ちます。

## <a name="next-steps-for-android-for-work"></a>Android for Work の次の手順
Android for Work のバインディングと設定を構成したら、次を実行できます。
- [Android for Work アプリを展開する](android-for-work-apps.md)
- [Android for Work 構成ポリシーを追加する](android-for-work-policy-settings-in-microsoft-intune.md)

## <a name="unbinding-your-android-for-work-administrative-account"></a>Android for Work 管理者アカウントのバインドを解除する

Android for Work の登録と管理を無効にすることもできます。 Intune の管理コンソールで **[バインドの解除]** をクリックすると、登録されているすべての Android for Work デバイスの登録が削除され、Android for Work アカウントと Intune 間の関係が削除されます。

### <a name="how-to-unbind-an-android-for-work-account"></a>Android for Work アカウントのバインドを解除する方法

1. **Android for Work のバインドを解除する**<br>
    管理者として [Microsoft Intune 管理コンソール](https://manage.microsoft.com)を開き、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Android for Work]** の順に選択し、**[バインドの解除]** をクリックします。

2. **Android for Work のバインドの削除に同意する**<br>
  **[はい]** をクリックしてバインドを削除し、Intune からすべての Android for Work デバイスの登録を解除します。
