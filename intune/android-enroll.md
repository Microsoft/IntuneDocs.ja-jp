---
title: "Intune で Android デバイスを登録する"
titleSuffix: Intune on Azure
description: "Intune で Android デバイスを登録する方法について説明します。&quot;"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 6920a17d1be4ffa9ee83d2da0af6ba69996ae028
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="enroll-android-devices"></a>Android デバイスの登録

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune では、Intune 管理者は、Samsung Knox Standard デバイスを含む、Android デバイスを管理できます。 [Android for Work デバイス](#enable-enrollment-of-android-for-work-devices)で作業プロファイルを管理することもできます。

Samsung KNOX Standard を実行するデバイスが、Intune によるマルチ ユーザー管理のサポート対象になりました。 つまり、エンド ユーザーは Azure AD の資格情報を使ってデバイスのサインインとサインアウトを行うことができ、デバイスは使用中かどうかに関わらず一元管理されます。 サインインしたエンド ユーザーはアプリにアクセスでき、適用されるポリシーをさらに受け取ります。 ユーザーがサインアウトすると、すべてのアプリ データがクリアされます。

## <a name="prerequisite"></a>前提条件

モバイル デバイスの管理を準備するには、MDM 機関を **Microsoft Intune** に設定する必要があります。 手順については、[MDM 機関の設定](mdm-authority-set.md)に関するページを参照してください。 この項目は、モバイル デバイス管理について初めて Intune を設定するときに一度だけ設定します。したがって、これは既に設定されている可能性があります。

## <a name="set-up-android-enrollment"></a>Android の登録を設定する

Intune では、既定で Android および Samsung Knox Standard デバイスの登録が許可されています。

Android デバイスをブロックする場合や、個人所有の Android デバイスのみの登録をブロックする場合は、「[Set device type restrictions](enrollment-restrictions-set.md#set-device-type-restrictions)」 (デバイスの種類の制限を設定する) を参照してください。

ユーザーが登録できるデバイスの最大数を設定する場合は、「[Set device limit restrictions](enrollment-restrictions-set.md#set-device-limit-restrictions)」 (デバイス数の制限を設定する) を参照してください。

デバイス管理を有効にするには、ユーザーは Intune ポータル サイト アプリ (Google Play から入手可能) をダウンロードし、アプリを開き、登録に関する画面の指示に従って、デバイスを登録する必要があります。 Android デバイスを管理下に置いたら、[コンプライアンス ポリシーの割り当て](compliance-policy-create-android.md)や[アプリの管理](app-management.md)などを行うことができます。

## <a name="enable-enrollment-of-android-for-work-devices"></a>Android for Work デバイスの登録を有効にする

[Android for Work をサポートする](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)デバイスで作業プロファイルの管理を有効にするには、Android for Work バインディングを Intune に追加する必要があります。 Android for Work をサポートするデバイスで、以前に Android デバイスとして登録していたデバイスを登録するには、デバイスの登録を解除してから、再登録する必要があります。

## <a name="add-android-for-work-binding-for-intune"></a>Intune 用に Android for Work のバインディングを追加する

1. **Intune MDM をセットアップする**<br>
**Microsoft Intune** を[モバイル デバイス管理機関](mdm-authority-set.md)に設定し、モバイル デバイス管理の準備をします (この作業をまだ行っていない場合)。

2. **Android for Work のバインディングを構成する**<br>
    Intune 管理者として Azure Portal で **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

    1. **[Intune]** ブレードで、**[デバイスの登録]**、**[Android for Work への登録]** の順に選択し、**[構成]** をクリックして Google Play の Android for Work の Web サイトを開きます。 この操作で、ブラウザーの新しいタブが開きます。
  ![Android for Work バインディングを構成するためのリンクのスクリーンショット](./media/android-work-bind.png)

    2. **Google にログインする**<br>
   Google のサインイン ページで、このテナントのすべての Android for Work 管理タスクに関連付ける Google アカウントを入力します。 これは、お客様の組織の IT 管理者が Play for Work コンソールでアプリを管理および公開するときに共有する Google アカウントです。

    3. **組織の詳細を指定する**<br>
   **[組織名]** に会社名を入力します。 **エンタープライズ モビリティ管理 (EMM) プロバイダー**の場合、*Microsoft Intune* と表示されます。 Android for Work の使用条件に同意し、**[確認]** をクリックします。 要求が処理されます。

## <a name="specify-android-for-work-enrollment-settings"></a>Android for Work 登録設定を指定する
   Android for Work は、特定の Android デバイスでのみサポートされています。 Google の [Android for Work の要件](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window")に関するページを参照してください。 Android for Work をサポートするデバイスは、従来の Android 管理もサポートします。  Intune では、Android for Work をサポートするデバイスの管理方法を指定できます。

   - **[すべてのデバイスを Android として管理する]** - Android for Work をサポートするデバイスを含め、すべて Android デバイスを従来の Android デバイスとして登録します。
   - **[サポートされるデバイスを Android for Work として管理する]** - Android for Work をサポートするすべてのデバイスが Android for Work デバイスとして登録されます。 Android for Work をサポートしないすべての Android デバイスは、従来の Android デバイスとして登録されます。
   - **[Manage supported devices for users only in these user groups as Android for Work (ユーザー グループのユーザーについてのみ、サポートされるデバイスを Android for Work として管理する)]** - Android for Work の管理を特定のユーザーのみを対象にします。 Android for Work をサポートするデバイスを登録した、選択したグループのメンバーのみが、Android for Work デバイスとして登録されます。 その他すべてのデバイスは Android デバイスとして登録されます。 これは Android for Work のパイロット中に役立ちます。

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>デバイスを登録して会社のリソースにアクセスする方法をユーザーに知らせる

Google Play に移動して Intune ポータル サイト アプリをダウンロードしてから、アプリを開き、画面の指示に従ってデバイスを登録するようにエンド ユーザーに指示する必要があります。 アプリに登録プロセスが示されます。このプロセスでは、登録により可能になる操作、および IT 管理者が見ることのできるデバイス上のデータと見ることのできないデータが説明されます。

オンライン登録の手順 (「[Intune に Android デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)」) へのリンクを送信することもできます。

その他のエンドユーザー タスクの詳細については、次の記事を参照してください。

- [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](end-user-educate.md)
- [Android デバイスを Intune で使用する](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbinding-your-android-for-work-administrative-account"></a>Android for Work 管理者アカウントのバインドを解除する

Android for Work の登録と管理を無効にすることもできます。 Intune の管理コンソールで **[バインドの解除]** をクリックすると、登録されているすべての Android for Work デバイスの登録が削除され、Android for Work アカウントと Intune 間の関係が削除されます。

### <a name="how-to-unbind-an-android-for-work-account"></a>Android for Work アカウントのバインドを解除する方法

1. **Android for Work のバインドを解除する**<br>
    Intune 管理者として Azure Portal で **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。  **[Intune]** ブレードで、**[デバイスの登録]**、**[Android for Work への登録]** の順に選択し、**[バインドの解除]** をクリックします。

2. **Android for Work のバインドの削除に同意する**<br>
  **[はい]** をクリックしてバインドを削除し、Intune からすべての Android for Work デバイスの登録を解除します。

