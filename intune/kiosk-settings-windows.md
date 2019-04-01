---
title: Microsoft Intune - Azure での Windows 10 用のキオスクの設定 | Microsoft Docs
description: Microsoft Intune でシングル アプリおよびマルチ アプリ キオスクとして Windows 10 (およびそれ以降) デバイスを構成し、スタート メニューのカスタマイズ、アプリの追加、タスク バーの表示、および Web ブラウザーの構成を行います。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/11/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55a0cb45cd3e3a8e367b0bff7bd8e856b02af953
ms.sourcegitcommit: aab39bf86707ccaef45fd6527fff4f1c89336710
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58429693"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Intune で Windows 10 以降のデバイスをキオスクとして実行するための設定

Windows 10 以降のデバイスでは、シングル アプリ キオスク モード、またはマルチ アプリ キオスク モードで実行するようにこれらのデバイスを構成することができます。

この記事では、Windows 10 以降のデバイスで制御できるさまざまな設定の一覧を示して説明します。 モバイル デバイス管理 (MDM) ソリューションの一環として、これらの設定を使って Windows 10 以降のデバイスを構成し、キオスク モードで実行させます。

Intune 管理者は、デバイスに対してこれらの設定を作成し、割り当てることができます。

Intune での Windows キオスク機能の詳細については、[キオスク設定の構成](kiosk-settings.md)に関するページを参照してください。

## <a name="before-you-begin"></a>始める前に

- [プロファイルを作成します](kiosk-settings.md#create-the-profile)。

- このキオスク プロファイルに直接関連して、デバイス制限プロファイルを使用して作成した、 [Microsoft Edge のキオスク設定](device-restrictions-windows-10.md#microsoft-edge-browser)します。 まとめ

  1. デバイスをキオスク モードで実行するには、このキオスク プロファイルを作成します。
  2. 作成、[デバイス制限プロファイル](device-restrictions-windows-10.md#microsoft-edge-browser)、および特定の機能と Microsoft Edge で許容される設定を構成します。

> [!IMPORTANT] 
> このキオスク プロファイルを割り当てると同じデバイスに必ず、 [Microsoft Edge プロファイル](device-restrictions-windows-10.md#microsoft-edge-browser)します。

## <a name="single-full-screen-app-kiosks"></a>シングル全画面表示アプリ キオスク

デバイスでは、1 つだけのアプリを実行します。

- **キオスク モードを選択して**: 選択**1 つのアプリ、全画面表示のキオスク**します。

- **[ユーザーのログオンの種類]**: 追加するアプリは、入力したユーザー アカウントとして実行します。 次のようなオプションがあります。

  - **[Auto logon (Windows 10 version 1803 and later)]\(自動ログオン (Windows 10 バージョン 1803 以上)\)**: ゲスト アカウントと同様、ユーザーのサインインを必要としないパブリックに公開された環境のキオスクで使用します。 この設定では [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp) を使用します。
  - **[ローカル ユーザー アカウント]**: (デバイスの) ローカル ユーザー アカウントを入力します。 サインインをキオスクに入力したアカウント。

- **アプリケーションの種類**: アプリケーションの種類を選択します。 次のようなオプションがあります。

  - **Microsoft Edge ブラウザーを追加する**: 選択**Microsoft Edge ブラウザー**を選択し、**キオスク モードの種類をエッジ**:

    - **/対話型のデジタル サイネージ**: URL の全画面表示を開き、その web サイトでのみ、コンテンツが表示されます。 [デジタル署名を設定](https://docs.microsoft.com/windows/configuration/setup-digital-signage)この機能について詳しく説明します。
    - **パブリック (InPrivate) を参照する**: Microsoft Edge の制限 タブを複数バージョンを実行します。 ユーザーでは、パブリックに参照したり、自分の閲覧セッションを終了することができます。

    これらのオプションの詳細については、次を参照してください。[キオスク モードの Microsoft Edge のデプロイ](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types)します。

    > [!NOTE]
    > この設定は、デバイス上の Microsoft Edge ブラウザーを有効にします。 Microsoft Edge に固有の設定を構成するには、デバイス構成プロファイルを作成 (**デバイス構成** > **プロファイル** > **プロファイルの作成** >  **Windows 10**プラットフォーム >**デバイス制限** >  **Microsoft Edge ブラウザー**)。 [Microsoft Edge ブラウザー](device-restrictions-windows-10.md#microsoft-edge-browser)使用可能な設定について説明します。

    **[OK]** を選択して変更を保存します。

  - **キオスク ブラウザーを追加する**: 選択**キオスク ブラウザー設定**します。 これらの設定で、キオスクの Web ブラウザー アプリを制御します。 [キオスク ブラウザー アプリ](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP)をストアから取得し、これを[クライアント アプリ](apps-add.md)として Intune に追加してから、キオスク デバイスにアプリを割り当ててください。

    次の設定を入力します。

    - **[既定のホーム ページ URL]**: キオスク ブラウザーが開いたときや再起動したときに表示される既定の URL を入力します。 たとえば、「`http://bing.com`」や「`http://www.contoso.com`」と入力します。

    - **[ホーム] ボタン**: キオスク ブラウザーの [ホーム] ボタンを**表示**または**非表示**にします。 既定では、ボタンは表示されません。

    - **ナビゲーション ボタン**: [進む] および [戻る] ボタンを**表示**または**非表示**にします。 既定では、ナビゲーション ボタンは表示されません。

    - **[セッションの終了] ボタン**: [セッションの終了] ボタンを**表示**または**非表示**にします。 表示されている場合、ユーザーがボタンを選択すると、アプリでセッションの終了が求められます。 確認すると、ブラウザーで閲覧データ (Cookie やキャッシュなど) がすべてクリアされ、既定の URL が開きます。 既定では、ボタンは表示されません。

    - **[Refresh browser after idle time]\(アイドル時間後にブラウザーを最新の情報に更新する\)**: キオスク ブラウザーを初期状態で再起動するまでのアイドル時間 (1 から 1,440 分) で入力します。 アイドル時間は、ユーザーが最後に操作してからの分数です。 既定では、値は空または空白となります。これは、アイドル タイムアウトがないことを意味します。

    - **[Allowed websites]\(許可されている Web サイト\)**: 特定の Web サイトを開けるようにするには、この設定を使用します。 つまり、デバイス上で Web サイトを制限またはブロックするには、この機能を使用します。 たとえば、`http://contoso.com*` のすべての Web サイトが開くようにすることができます。 既定では、すべての Web サイトが許可されます。

      特定の web サイトを許可するには、許可される Web サイトが 1 行に 1 つずつ列記されているファイルをアップロードします。 ファイルを追加しない場合、すべての Web サイトが許可されます。 Intune では、`*` (アスタリスク) がワイルド カードとしてサポートされます。

      ファイルの例を次に示します。

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`  

    **[OK]** を選択して変更を保存します。

  - **追加のストア アプリ**: 選択**ストア アプリを追加**、し、一覧からアプリを選択します。

    アプリが何も表示されない場合は、 [クライアント アプリ](apps-add.md)ごとの手順を使用して追加してください。

  **[OK]** を選択して変更を保存します。

## <a name="multi-app-kiosks"></a>マルチ アプリ キオスク

このモードのアプリはスタート メニューから使用できます。 ユーザーはこれらのアプリのみを開くことができます。 別のアプリでのアプリに依存した場合、許可されているアプリの一覧に取り込まれる必要があります。 たとえば、Internet Explorer の 64 ビットは、"C:\Program \internet explorer explorer\iexplore.exe"と"C:\Program Files (x86) \Internet Explorer\iexplore.exe"の両方を許可する必要がありますので、Internet Explorer の 32 ビット、依存関係を持ちます。 

- **キオスク モードを選択して**: 選択**マルチ アプリ キオスク**します。

- **[S モード デバイスで Windows 10 を対象とする]**:
  - **[はい]**: キオスク プロファイルでストア アプリおよび AUMID アプリ (Win32 アプリを除く) を許可します。
  - **[いいえ]**: キオスク プロファイルでストア アプリ、Win32 アプリ、AUMID アプリを許可します。 このキオスク プロファイルは S モードのデバイスに展開されません。

- **[ユーザーのログオンの種類]**: 追加するアプリは、入力したユーザー アカウントとして実行します。 次のようなオプションがあります。

  - **[Auto logon (Windows 10 version 1803 and later)]\(自動ログオン (Windows 10 バージョン 1803 以上)\)**: ゲスト アカウントと同様、ユーザーのサインインを必要としないパブリックに公開された環境のキオスクで使用します。 この設定では [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp) を使用します。
  - **[ローカル ユーザー アカウント]**: (デバイスの) ローカル ユーザー アカウントを**追加**します。 サインインをキオスクに入力したアカウント。
  - **[Azure AD user or group (Windows 10 version 1803 and later)]\(Azure AD のユーザーまたはグループ (Windows 10 バージョン 1803 以上)\)**: **[追加]** を選択して、一覧から Azure AD のユーザーまたはグループを選択します。 複数のユーザーおよびグループを選択することができます。 **[選択]** を選んで変更を保存します。
  - **[HoloLens の訪問者]**: 訪問者のアカウントはゲスト アカウントであり、「[共有 PC モードの概念](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts)」の説明のとおり、ユーザーの資格情報や認証は必要ありません。

- **[Browser and Applications]\(ブラウザーとアプリケーション\)**: キオスク デバイスで実行するアプリを追加します。 複数のアプリを追加することができます。

  - **ブラウザー**

    - **Microsoft Edge の追加**: Microsoft Edge がアプリのグリッドに追加され、すべてのアプリケーションは、このキオスクで実行できます。 選択、**キオスク モードの種類の Microsoft Edge**:

      - **通常モード (完全なバージョンの Microsoft Edge)**: すべての参照機能と Microsoft Edge の完全版を実行します。 ユーザー データと状態は、セッション間で保存されます。
      - **パブリック (InPrivate) を参照する**: 全画面表示モードで実行されているキオスクをカスタマイズして、マルチタブのバージョンの Microsoft Edge の InPrivate を実行します。

      これらのオプションの詳細については、次を参照してください。[キオスク モードの Microsoft Edge のデプロイ](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types)します。

      > [!NOTE]
      > この設定は、デバイス上の Microsoft Edge ブラウザーを有効にします。 Microsoft Edge に固有の設定を構成するには、デバイス構成プロファイルを作成 (**デバイス構成** > **プロファイル** > **プロファイルの作成** >  **Windows 10**プラットフォーム >**デバイス制限** >  **Microsoft Edge ブラウザー**)。 [Microsoft Edge ブラウザー](device-restrictions-windows-10.md#microsoft-edge-browser)使用可能な設定について説明します。

      **[OK]** を選択して変更を保存します。

    - **[キオスク ブラウザーの追加]**: これらの設定で、キオスクの Web ブラウザー アプリを制御します。 [クライアント アプリ](apps-add.md)を使用してキオスク デバイスに Web ブラウザー アプリを展開したことを確認してください。

      次の設定を入力します。

      - **[既定のホーム ページ URL]**: キオスク ブラウザーが開いたときや再起動したときに表示される既定の URL を入力します。 たとえば、「`http://bing.com`」や「`http://www.contoso.com`」と入力します。

      - **[ホーム] ボタン**: キオスク ブラウザーの [ホーム] ボタンを**表示**または**非表示**にします。 既定では、ボタンは表示されません。

      - **ナビゲーション ボタン**: [進む] および [戻る] ボタンを**表示**または**非表示**にします。 既定では、ナビゲーション ボタンは表示されません。

      - **[セッションの終了] ボタン**: [セッションの終了] ボタンを**表示**または**非表示**にします。 表示されている場合、ユーザーがボタンを選択すると、アプリでセッションの終了が求められます。 確認すると、ブラウザーで閲覧データ (Cookie やキャッシュなど) がすべてクリアされ、既定の URL が開きます。 既定では、ボタンは表示されません。

      - **[Refresh browser after idle time]\(アイドル時間後にブラウザーを最新の情報に更新する\)**: キオスク ブラウザーを初期状態で再起動するまでのアイドル時間 (1 から 1,440 分) で入力します。 アイドル時間は、ユーザーが最後に操作してからの分数です。 既定では、値は空または空白となります。これは、アイドル タイムアウトがないことを意味します。

      - **[Allowed websites]\(許可されている Web サイト\)**: 特定の Web サイトを開けるようにするには、この設定を使用します。 つまり、デバイス上で Web サイトを制限またはブロックするには、この機能を使用します。 たとえば、`contoso.com*` のすべての Web サイトが開くようにすることができます。 既定では、すべての Web サイトが許可されます。

        特定の web サイトを許可するには、許可されている Web サイトの一覧が含まれる .csv ファイルをアップロードします。 .csv ファイルを追加しない場合、すべての Web サイトが許可されます。

      **[OK]** を選択して変更を保存します。

  - **アプリケーション**

    - **[ストア アプリの追加]**: ビジネス向け Microsoft Store からアプリを追加します。 アプリが何も表示されない場合は、アプリを取得して [Intune に追加する](store-apps-windows.md)ことができます。 たとえば、キオスク ブラウザー、Excel、OneNote などを追加できます。

      **[OK]** を選択して変更を保存します。

    - **[Add Win32 App]\(Win32 アプリの追加\)**: Win32 アプリは Visual Studio Code や Google Chrome などの従来のデスクトップ アプリです。 次のプロパティを入力します。

      - **[アプリケーション名]**: 必須です。 アプリケーションの名前を入力します。
      - **[ローカル パス]**: 必須です。 `C:\Program Files (x86)\Microsoft VS Code\Code.exe` や `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe` などの、実行可能ファイルのパスを入力します。
      - **[アプリケーション ユーザー モデル ID (AUMID)]**: Win32 アプリのアプリケーション ユーザー モデル ID (AUMID) を入力します。 この設定により、デスクトップ上のタイルのスタート画面のレイアウトが決まります。 この ID を取得するには、「[Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps)」を参照してください。

      **[OK]** を選択して変更を保存します。

    - **[Add by AUMID]\(AUMID による追加\)**: このオプションを使用して、メモ帳や電卓などの受信トレイ Windows アプリを追加します。 次のプロパティを入力します。

      - **[アプリケーション名]**: 必須です。 アプリケーションの名前を入力します。
      - **[アプリケーション ユーザー モデル ID (AUMID)]**: 必須です。 Windows アプリのアプリケーション ユーザー モデル ID (AUMID) を入力します。 この ID を取得する場合は、「[Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)」 (インストール済みアプリのアプリケーション ユーザー モデル ID を見つける) を参照してください。

      **[OK]** を選択して変更を保存します。

    - **自動的**: 省略可能です。 ユーザーがサインインするときに自動的にアプリケーションを選択します。 1 つのアプリのみが AutoLaunched できます。
    - **[タイルのサイズ]**: 必須です。 小、中、全体、大の、アプリ タイルのサイズを選択します。

  > [!TIP]
  > すべてのアプリを追加したら、一覧内のアプリをクリックしてドラッグすることで、表示順序を変更することができます。  

- **[Use alternative Start layout]\(スタート画面の別のレイアウトを使用する\)**: **[はい]** を選択して、アプリの順序を含む、アプリをスタート メニューに表示する方法を説明する XML ファイルを入力します。 [スタート] メニューでさらにカスタマイズが必要な場合は、このオプションを使用します。 ガイダンスおよび XML のサンプルについては、「[スタート画面のレイアウトのカスタマイズとエクスポート](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout)」をご覧ください。

- **[Windows タスク バー]**: タスク バーを**表示**または**非表示**にします。 既定では、タスク バーは表示されません。 Wi-Fi アイコンなどのアイコンが表示されますが、エンドユーザーが設定を変更することはできません。

- **ダウンロード フォルダーへのアクセスを許可する**: 選択**はい**Windows エクスプ ローラーの [ダウンロード] フォルダーにアクセスできるようにします。 既定では、ダウンロード フォルダーへのアクセスは無効になります。 この機能は、ブラウザーからダウンロードされたアイテムにアクセスするエンドユーザーのよく使用されます。

**[OK]** を選択して変更を保存します。

## <a name="next-steps"></a>次の手順

[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

また、[Android](device-restrictions-android.md#kiosk)、[Android エンタープライズ](device-restrictions-android-for-work.md#dedicated-device-settings)、[Windows Holographic for Business](kiosk-settings-holographic.md) デバイス用のキオスク プロファイルを作成することもできます。
