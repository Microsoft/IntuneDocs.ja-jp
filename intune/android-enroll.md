---
title: "Intune に Android デバイスを登録する | Microsoft Docs"
titlesuffix: Azure portal
description: "Intune で Android デバイスを登録する方法について説明します。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 68d93fe98b89f27c947e07d79eca9a0e02dea582
ms.sourcegitcommit: ce35790090ebe768d5f75c108e8d5934fd19c8c7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="enroll-android-devices"></a>Android デバイスの登録

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 管理者は、Samsung Knox Standard デバイスを含む、Android デバイスを管理できます。 [Android for Work デバイス](#enable-enrollment-of-android-for-work-devices)で仕事用プロファイルを管理することもできます。

Samsung Knox Standard を実行するデバイスが、Intune によるマルチ ユーザー管理のサポート対象になりました。 つまり、ユーザーは Azure AD 資格情報を使用してデバイスに対してサインインしたりサインアウトしたりすることができます。 使用中かどうかに関係なく、デバイスは中央管理されます。 サインインしたユーザーはアプリにアクセスできるのに加え、適用されるポリシーを受け取ります。 ユーザーがサインアウトすると、すべてのアプリ データがクリアされます。

## <a name="prerequisite"></a>前提条件

モバイル デバイスの管理を準備するには、MDM (モバイル デバイス管理) 機関を **Microsoft Intune** に設定する必要があります。 手順については、[MDM 機関の設定](mdm-authority-set.md)に関するページを参照してください。 この項目は、モバイル デバイス管理について初めて Intune を設定するときに一度だけ設定します。

## <a name="set-up-android-enrollment"></a>Android の登録を設定する

Intune では、既定で Android および Samsung Knox Standard デバイスの登録が許可されています。

Android デバイスをブロックする場合や、個人所有の Android デバイスのみの登録をブロックする場合は、「[Set device type restrictions](enrollment-restrictions-set.md)」 (デバイスの種類の制限を設定する) を参照してください。

デバイス管理を有効にするには、ユーザーは Intune ポータル サイト アプリ (Google Play から入手可能) をダウンロードし、アプリを開き、画面の指示に従って、デバイスを登録する必要があります。 Android デバイスを管理対象にすると、[コンプライアンス ポリシーの割り当て](compliance-policy-create-android.md)や[アプリの管理](app-management.md)などを行うことができます。

## <a name="enable-enrollment-of-android-for-work-devices"></a>Android for Work デバイスの登録を有効にする

[Android for Work をサポートする](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)デバイスで作業プロファイルの管理を有効にするには、Android for Work バインディングを Intune に追加する必要があります。 Android for Work をサポートするデバイスで、以前に通常の Android デバイスとして登録していたデバイスを登録するには、デバイスの登録を解除してから再登録する必要があります。

[デバイス登録マネージャー](device-enrollment-manager-enroll.md) アカウントを使用して Android for Work デバイスを登録する場合、アカウントあたりの登録可能なデバイスは 10 台に制限されます。

## <a name="add-android-for-work-binding-for-intune"></a>Intune 用に Android for Work のバインディングを追加する

1. **Intune MDM をセットアップする**<br>
**Microsoft Intune** を[モバイル デバイス管理機関](mdm-authority-set.md)に設定し、モバイル デバイス管理の準備をします (この作業をまだ行っていない場合)。
2. **Android for Work のバインディングを構成する**<br>
    Intune 管理者として Azure Portal で **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

   a. **[Intune]** ブレードで、**[デバイスの登録]** > **[Android for Work への登録]** の順に選択し、**[構成]** を選択して Google Play の Android for Work の Web サイトを開きます。 ブラウザーの新しいタブで Web サイトが開きます。
   ![Android for Work バインディングを構成するためのリンクを示すスクリーンショット](./media/android-work-bind.png)

   b. **Google にサインインする**<br>
   Google のサインイン ページで、このテナントのすべての Android for Work 管理タスクに関連付ける Google アカウントを入力します。 これは、会社の IT 管理者が Play for Work コンソールでアプリを管理および公開するときに共有する Google アカウントです。

   c. **組織の詳細を指定する**<br>
   **[組織名]** に会社名を入力します。 **エンタープライズ モビリティ管理 (EMM) プロバイダー**の場合、**Microsoft Intune** と表示されます。 Android for Work の使用条件に同意し、**[確認]** を選択します。 要求が処理されます。

## <a name="specify-android-for-work-enrollment-settings"></a>Android for Work 登録設定を指定する
   Android for Work は、特定の Android デバイスでのみサポートされています。 Google の [Android for Work の要件](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window")に関するページを参照してください。 Android for Work をサポートするすべてのデバイスでは、従来の Android 管理もサポートされます。 Intune では、Android for Work をサポートするデバイスの管理方法を指定できます。

   - **すべてのデバイスを Android として管理する**。 Android for Work をサポートするデバイスを含め、すべての Android デバイスが従来の Android デバイスとして登録されます。
   - **サポートされているデバイスを Android for Work として管理する**。 Android for Work をサポートするすべてのデバイスが Android for Work デバイスとして登録されます。 Android for Work をサポートしないすべての Android デバイスは、従来の Android デバイスとして登録されます。
   - **これらのユーザー グループに所属するユーザーのサポートされているデバイスのみを Android for Work として管理する**。 Android for Work の管理対象を一部のユーザーのみに制限できます。 Android for Work をサポートするデバイスを登録した、選択したグループのメンバーのみが、Android for Work デバイスとして登録されます。 その他すべてのデバイスは Android デバイスとして登録されます。 これは Android for Work のパイロット中に役立ちます。

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>デバイスを登録して会社のリソースにアクセスする方法をユーザーに知らせる

Google Play に移動して Intune ポータル サイト アプリをダウンロードしてから、アプリを開き、画面の指示に従ってデバイスを登録するようにユーザーに指示します。 アプリに登録プロセスが示されます。このプロセスでは、登録により可能になる操作、および IT 管理者が見ることのできるデバイス上のデータと見ることのできないデータが説明されます。

オンライン登録の手順 (「[Intune に Android デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)」) へのリンクを送信することもできます。

その他のユーザー タスクについては、次の記事を参照してください。

- [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](end-user-educate.md)
- [Android デバイスを Intune で使用する](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbind-your-android-for-work-administrative-account"></a>Android for Work 管理者アカウントのバインドを解除する

Android for Work の登録と管理を無効にすることもできます。 Intune 管理コンソールで **[バインドの解除]** を選択すると、登録済みのすべての Android for Work デバイスが登録から削除されます。 また、Android for Work アカウントと Intune 間のリレーションシップも削除されます。

### <a name="to-unbind-an-android-for-work-account"></a>Android for Work アカウントのバインドを解除するには

1. **Android for Work のバインドを解除する**<br>
    Intune 管理者として Azure Portal で **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。  **[Intune]** ブレードで、**[デバイスの登録]**、**[Android for Work への登録]** の順に選択してから、**[バインドの解除]** を選択します。

2. **Android for Work のバインドの削除に同意する**<br>
  **[はい]** を選択してバインドを削除し、Intune からすべての Android for Work デバイスの登録を解除します。
