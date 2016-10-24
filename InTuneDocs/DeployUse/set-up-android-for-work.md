---
title: "Android for Work の管理をセットアップする | Microsoft Intune"
description: "Microsoft Intune を使用して Android for Work デバイスのモバイル デバイス管理 (MDM) を有効にします。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b2fdcea9-9ad7-4d73-88e2-854b7a774bb2
translationtype: Human Translation
ms.sourcegitcommit: 519b66c94f3d056e060ed11e1a3d7d6d118a94fb
ms.openlocfilehash: 5f48303dd28627f961f8c2cfd38f8977354e2724


---

# Android for Work デバイスの登録を有効にする

Android for Work デバイスの管理を有効にするには、Android for Work バインディングを Intune に追加する必要があります。 Android for Work をサポートするデバイスで、以前に Android デバイスとして登録していたデバイスを登録するには、デバイスの登録を解除してから、再登録する必要があります。

## Intune 用に Android for Work のバインディングを追加する

1. **Intune をセットアップする**<br>
**Microsoft Intune** を[モバイル デバイス管理機関に設定](prerequisites-for-enrollment.md#set-mobile-device-management-authority)して、MDM の設定を行うことにより、モバイル デバイス管理を準備します (この作業をまだ行っていない場合)。

2. **Android for Work のバインディングを構成する**<br>
    管理者として [Microsoft Intune 管理コンソール](http://manage.microsoft.com)を開き、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Android for Work]** の順に選択し、**[構成]** をクリックして Google Play の Android for Work Web サイトを開きます。 この操作で、ブラウザーの新しいタブが開きます。

3. **Google にログインする**<br>
   Google のサインイン ページで、このテナントのすべての Android for Work 管理タスクに関連付ける Google アカウントを入力します。 Intune を管理する複数の管理者で共有する Google アカウントを指定することもできます。 これは、お客様の組織が Play for Work コンソールでアプリを管理および公開するときに使用する Google アカウントです。

4. **組織の詳細を指定する**<br>
   **[組織名]** に会社名を入力します。 **エンタープライズ モビリティ管理 (EMM) プロバイダー**の場合、*Microsoft Intune* と表示されます。 Android for Work の使用条件に同意し、**[確認]** をクリックします。 要求が処理されます。

## Android for Work 登録設定を指定する
   Android for Work は、特定の Android デバイスでのみサポートされています。 Google の [Android for Work の要件](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window")に関するページを参照してください。  Android for Work をサポートするデバイスは、従来の Android 管理もサポートします。  Intune では、Android for Work をサポートするデバイスの管理方法を指定できます。

   - **[Manage all devices as Android]** (すべてのデバイスを Android として管理する) - (無効) Android for Work をサポートするデバイスを含め、すべて Android デバイスを従来の Android デバイスとして登録します。
   - **[Manage supported devices as Android for Work]** (サポートされるデバイスを Android for Work として管理する) - (有効) Android for Work をサポートするすべてのデバイスが Android for Work デバイスとして登録されます。 Android for Work をサポートしないすべての Android デバイスは、従来の Android デバイスとして登録されます。
   - **[Manage supported devices for users only in these user groups as Android for Work]** (ユーザー グループのユーザーについてのみ、サポートされるデバイスを Android for Work として管理する) - (テスト中) Android for Work の管理を特定のユーザーのみを対象にします。 Android for Work をサポートするデバイスを登録した、選択したグループのメンバーのみが、Android for Work デバイスとして登録されます。 その他すべてのデバイスは Android デバイスとして登録されます。

## Android for Work の次の手順
Android for Work のバインディングと設定を構成したら、次の管理機能を実行できます。
- [Android for Work アプリを展開する](android-for-work-apps.md)
- [Android for Work 構成ポリシーを追加する](android-for-work-policy-settings-in-microsoft-intune.md)

## Android for Work 管理者アカウントのバインドを解除する

Android for Work の登録と管理を無効にすることもできます。 **[バインドの解除]** をクリックすると、登録されているすべての Android for Work デバイスが登録から削除され、Android for Work アカウントと Intune 間の関係が削除されます。

### Android for Work アカウントのバインドを解除する方法

1. **Android for Work のバインドを解除する**<br>
    管理者として [Microsoft Intune 管理コンソール](http://manage.microsoft.com)を開き、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Android for Work]** の順に選択し、**[バインドの解除]** をクリックします。

2. **Android for Work のバインドの削除に同意する**<br>
  **[はい]** をクリックしてバインドを削除し、Intune からすべての Android for Work デバイスの登録を解除します。



<!--HONumber=Oct16_HO2-->


