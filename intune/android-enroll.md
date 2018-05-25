---
title: Intune で Android デバイスを登録する
titlesuffix: Microsoft Intune
description: Intune で Android デバイスを登録する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3212d1a3d3454542dd9d34409fc788558f2d7eed
ms.sourcegitcommit: af0cc27b05bf0743f7d0970f5f3822f0aab346af
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2018
---
# <a name="enroll-android-devices"></a>Android デバイスの登録

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 管理者は、Samsung Knox Standard デバイスを含む、Android デバイスを管理できます。 [Android for Work デバイス](#enable-enrollment-of-android-for-work-devices)で仕事用プロファイルを管理することもできます。

Samsung Knox Standard を実行するデバイスが、Intune によるマルチ ユーザー管理のサポート対象になりました。 つまり、ユーザーは Azure AD 資格情報を使用してデバイスに対してサインインしたりサインアウトしたりすることができます。 使用中かどうかに関係なく、デバイスは中央管理されます。 サインインしたユーザーはアプリにアクセスできるのに加え、適用されるポリシーを受け取ります。 ユーザーがサインアウトすると、すべてのアプリ データがクリアされます。

## <a name="prerequisite"></a>前提条件

モバイル デバイスの管理を準備するには、MDM (モバイル デバイス管理) 機関を **Microsoft Intune** に設定する必要があります。 手順については、[MDM 機関の設定](mdm-authority-set.md)に関するページを参照してください。 この項目は、モバイル デバイス管理について初めて Intune を設定するときに一度だけ設定します。

## <a name="set-up-android-enrollment"></a>Android の登録を設定する

Intune では、既定で Android および Samsung Knox Standard デバイスの登録が許可されています。

Android デバイスをブロックする場合や、個人所有の Android デバイスのみの登録をブロックする場合は、「[Set device type restrictions](enrollment-restrictions-set.md)」 (デバイスの種類の制限を設定する) を参照してください。

デバイス管理を有効にするには、ユーザーは Intune ポータル サイト アプリ (Google Play から入手可能) をダウンロードし、アプリを開き、画面の指示に従って、デバイスを登録する必要があります。 Android デバイスを管理対象にすると、[コンプライアンス ポリシーの割り当て](compliance-policy-create-android.md)や[アプリの管理](app-management.md)などを行うことができます。

## <a name="enable-enrollment-of-android-for-work-devices"></a>Android for Work デバイスの登録を有効にする

[Android for Work をサポートする](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)デバイスで作業プロファイルの管理を有効にするには、Android for Work バインディングを Intune に追加する必要があります。 以前は通常の Android デバイスとして登録されていたデバイスを Android for Work のデバイスとして登録するには、デバイスの登録を解除してから再登録する必要があります。

[デバイス登録マネージャー](device-enrollment-manager-enroll.md) アカウントを使用して Android for Work デバイスを登録する場合、アカウントあたりの登録可能なデバイスは 10 台に制限されます。

詳細については、「[Intune から Google に送られるデータ](data-intune-sends-to-google.md)」を参照してください。

## <a name="add-android-for-work-binding-for-intune"></a>Intune 用に Android for Work のバインディングを追加する

> [!NOTE]
> Google ドメインと Microsoft ドメインの間の相互作用のため、この手順では、正常に完了するためにブラウザー設定の調整が必要な場合があります。  "portal.azure.com" と "play.google.com" がブラウザーの同じセキュリティ ゾーンにあることを確認してください。

1. **Intune MDM をセットアップする**<br>
**Microsoft Intune** を[モバイル デバイス管理機関](mdm-authority-set.md)に設定し、モバイル デバイス管理の準備をします (この作業をまだ行っていない場合)。
2. **Android for Work のバインディングを構成する**<br>
    
   」を参照します。 [Azure Portal の Intune](https://aka.ms/intuneportal) にサインインして、**[デバイスの登録]** > **[Android の登録]** > **[managed Google Play]** を選択します。  カスタム Intune 管理者ロールを使用している場合、このアクセスには組織の読み取りと更新のアクセス許可が必要です。
   
   ![Android for Work の登録画面](./media/android-work-bind.png)

   b. **[同意する]** を選択して、Microsoft が[ユーザーとデバイスの情報を Google に送信](data-intune-sends-to-google.md)できるようにします。 
   
   c. **[Launch Google to connect now]\(Google を起動して今すぐ接続)** 選択して、Google Play の Android for Work Web サイトを開きます。 ブラウザーの新しいタブで Web サイトが開きます。
  
   d. **Google にサインインする**<br>
   Google のサインイン ページで、このテナントのすべての Android for Work 管理タスクに関連付ける Google アカウントを入力します。 これは、会社の IT 管理者が Play for Work コンソールでアプリを管理および公開するときに共有する Google アカウントです。 既存の Google アカウントを使用するか、新しい Google アカウントを作成できます。  選択したアカウントを G-Suite ドメインと関連付けることはできません。

   e. **組織の詳細を指定する**<br>
   **[組織名]** に会社名を入力します。 **エンタープライズ モビリティ管理 (EMM) プロバイダー**の場合、**Microsoft Intune** と表示されます。 Android for Work の使用条件に同意し、**[確認]** を選択します。 要求が処理されます。

## <a name="specify-android-for-work-enrollment-settings"></a>Android for Work 登録設定を指定する
Android for Work は、特定の Android デバイスでのみサポートされています。 Google の [Android for Work の要件](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22)に関するページを参照してください。 Android for Work をサポートするすべてのデバイスでは、従来の Android 管理もサポートされます。 Intune では、Android for Work をサポートするデバイスを[登録制限](enrollment-restrictions-set.md)内から管理する方法を指定できます。

- **ブロック (既定で設定)**: Android for Work をサポートするデバイスを含め、すべての Android デバイスが従来の Android デバイスとして登録されます。
- **許可**: Android for Work をサポートするすべてのデバイスが Android for Work デバイスとして登録されます。 Android for Work をサポートしないすべての Android デバイスは、従来の Android デバイスとして登録されます。

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>管理対象の Google Play ストアのポータル サイト アプリを承認する
アプリの自動更新を確実に受け取るには、管理対象の Google Play ストアの Android 用ポータル サイト アプリを承認する必要があります。 アプリを承認しないと、ポータル サイトはいずれ使われていない状態になってしまい、Microsoft からリリースされた重要なバグ修正プログラムや新しい機能を受け取らなくなることがあります。

Intune ポータル サイトを承認するには、次の手順のようにします。

1.  [管理対象の Google Play ストア](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal)のポータル サイト アプリを参照します。
2.  Android for Work のバインディングを構成するときに使ったものと同じ Google アカウントで、管理対象の Google Play ストアにサインインします。
3.  **[承認]** をクリックすると、新しいダイアログが開きます。
4.  このダイアログでアクセス許可を確認し、**[承認]** をクリックします。 ポータル サイト アプリがデバイスの仕事用プロファイルを管理できるようにするには、これらのアクセス許可を許可する必要があります。
5.  **[Keep approved when app requests new permissions]\(アプリが新しいアクセス許可を要求したときに承認済みのままにする\)** を選び、**[保存]** をクリックします。

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
    Intune 管理者として [Azure Portal](https://portal.azure.com) で **[すべてのサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。  **[Intune]** ウィンドウで、**[デバイスの登録]**、**[Android for Work への登録]** の順に選択してから、**[バインドの解除]** を選択します。

2. **Android for Work のバインドの削除に同意する**<br>
  **[はい]** を選択してバインドを削除し、Intune からすべての Android for Work デバイスの登録を解除します。

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Samsung KNOX デバイス登録時のエンドユーザー エクスペリエンス
Samsung Knox デバイスを登録する場合、次のいくつかの考慮事項があります。
-   ポリシーで PIN が要求されない場合でも、デバイスを登録するには少なくとも 4 桁の PIN が必要です。 デバイスに PIN がない場合、ユーザーに作成を求めるメッセージが表示されます。
-   Workplace Join Certificates (WPJ) に関するユーザーの操作はありません。
-   ユーザーにサービス登録情報とアプリで実行できる内容を示すメッセージが表示されます。
-   ユーザーに Knox 登録情報と Knox で実行できる内容を示すメッセージが表示されます。
-   暗号化ポリシーが適用されている場合、ユーザーはデバイス パスコードの 6 文字の複雑なパスワードを設定する必要があります。
-   会社のリソースへのアクセスのサービスでプッシュされる証明書のインストールをユーザーに求める追加のメッセージは表示されません。
- 一部の古い Knox デバイスでは、会社のリソースへのアクセスで使用される追加の証明書を求めるメッセージがユーザーに表示されます。
- Samsung Mini デバイスで WPJ のインストールに失敗し、"**証明書が見つかりません**" または "**デバイスを登録できません**" などのエラーが表示された場合は、最新の Samsung Firmware Updates をインストールします。
