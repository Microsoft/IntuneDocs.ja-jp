---
title: Microsoft Intune - Azure での Windows 10 用のキオスクの設定 | Microsoft Docs
description: スタート メニューのカスタマイズ、アプリの追加、タスク バー、Web ブラウザーの構成など、シングル アプリ キオスクおよびマルチ アプリ キオスクとして Windows 10 (およびそれ以降) デバイスを構成します。 また、Microsoft Intune でマルチ アプリ キオスクとして Windows Holographic for Business デバイスを構成します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9dd7608981da1454c1f3be29eb6ff40a5d7f3394
ms.sourcegitcommit: 23adbc50191f68c4b66ea845a044da19c659ac84
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45562869"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Intune での Windows 10 (以降) 用のキオスクの設定

キオスク プロファイルは、1 つのアプリ、または複数のアプリを実行するように Windows 10 デバイスを構成するために使用されます。 キオスク プロファイルを作成する際に、スタート メニューを表示するか、Web ブラウザーをインストールするかなどを選ぶこともできます。

## <a name="kiosk-settings"></a>キオスクの設定

1. **Azure Portal** で、[[すべてのサービス]](https://portal.azure.com) を選択し、**[Intune]** をフィルター処理して **[Microsoft Intune]** を選びます。
2. **[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

   - **名前**: 新しいプロファイルのわかりやすい名前を入力します。
   - **説明**: プロファイルの説明を入力します  これは省略可能ですが、入力することをお勧めします。
   - **[プラットフォーム]**: **[Windows 10 以降]** を選択します
   - **[プロファイルの種類]**: **[キオスク (プレビュー)]** を選択します
   
4. **[キオスク]**、**[追加]** の順に選択します。
5. ご利用のキオスクの **[キオスク構成名]** を入力します。 この名前により、アプリケーションのグループ、スタート メニューでのアプリケーションのレイアウト、このキオスク構成に割り当てられているユーザーが識別されます。
6. **[キオスク モード]** を選択します。 **[キオスク モード]** では、ポリシーによってサポートされるキオスク モードの種類を識別します。 次のオプションがあります。

    - **[未構成]** (既定): このポリシーでは、キオスク モードが有効になりません。
    - **[シングル全画面表示アプリ キオスク]**: このプロファイルでは、デバイスを単一のユーザー アカウントとして実行でき、単一のユニバーサル Windows プラットフォーム (UWP) アプリにロックします。 したがって、ユーザーがサインインすると、特定のアプリが起動します。 また、このモードでは、ユーザーによる新しいアプリを開く操作や、実行中のアプリを変更する操作が制限されます。
    - **[マルチ アプリ キオスク]**: このプロファイルの場合、デバイスで複数のユニバーサル Windows プラットフォーム (UWP) アプリ、または Win32 アプリを実行できます。 ユーザー アカウントによって異なるアプリを割り当てることもできます。 ユーザーは追加されているアプリだけを利用できます。 マルチ アプリ キオスク (または固定目的デバイス) の利点は、ユーザーがアクセスできるのは必要なアプリだけなので、わかりやすいエクスペリエンスがユーザーに提供されることです。 また、必要のないアプリはビューから削除されます。

#### <a name="single-full-screen-app-kiosks"></a>シングル全画面表示アプリ キオスク
次の設定を入力します。

- **[Universal Windows Platform (UWP) app identifier]\(ユニバーサル Windows プラットフォーム (UWP) アプリ識別子\)**: キオスク アプリの**アプリケーション ユーザー モデル ID (AUMID)** を入力します。 または、[クライアント アプリ](apps-add.md)を使用して追加した既存の管理対象アプリを選択します。

    「[Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)」 (インストール済みアプリのアプリケーション ユーザー モデル ID を見つける) を参照してください。

- **[ユーザー アカウントの種類]**: 次のようなオプションがあります。

  - **[自動ログオン]**: 自動ログオンが有効になっている公開環境のキオスクの場合、最小特権 (ローカルの標準ユーザー アカウントなど) を持つユーザーを使用する必要があります。 キオスク モードの Azure Active Directory (AD) アカウントを構成するには、`AzureAD\user@contoso.com` 形式を使用します。
  - **[ローカル ユーザー アカウント]**: (デバイスの) ローカル ユーザー アカウントか、キオスク アプリに関連付けられている Azure AD アカウント ログインを入力します。 Azure AD ドメインに参加しているアカウントについては、`domain\username@tenant.org` 形式を使用してアカウントを入力します。

#### <a name="multi-app-kiosks"></a>マルチ アプリ キオスク
このモードのアプリはスタート メニューから使用できます。 ユーザーはこれらのアプリのみを開くことができます。 

[マルチ アプリ キオスク](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune)は、許可されているアプリがリストされているキオスク構成と、その他の設定を使います。

次の設定を入力します。

- **[Add Win32 App]\(Win32 アプリを追加\)**: Win32 アプリは従来のデスクトップ アプリです。 **[アプリ名]**、および **[識別子]** を入力します。 **[識別子]** は、デバイスに関する、実行可能ファイルの完全修飾パス名です。
- **[管理対象アプリを追加]**: [Intune のクライアント アプリ](apps-add.md)を使用して追加した既存の管理対象アプリを選択します。
- **[Add app by AUMID]\(AUMID でアプリを追加\)**: [アプリの AUMID](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) を入力します (UWP アプリ)。
- **[タスク バー]**: キオスクでのタスク バーを **[有効]** (表示) にするか、**[未構成]** (非表示) のままにします。
- **[スタート メニューのレイアウト]**: アプリの順序を含む、アプリをスタート メニューに表示する方法を説明する XML ファイルを入力します。 ガイダンスおよび XML のサンプルについては、「[スタート画面のレイアウトのカスタマイズとエクスポート](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout)」をご覧ください。

  XML ファイルの使用と作成については、「[複数のアプリを実行する Windows 10 キオスクを作成する](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file)」をご覧ください。

- **[ユーザー アカウントの種類]**: 追加したアプリを使用できる 1 つ以上のユーザー アカウントを追加します。 サインインしたアカウントは、構成で定義されているアプリのみを利用できます。 アカウントは、デバイスのローカル アカウントか、キオスク アプリに関連付けられている Azure AD アカウント ログインになります。

    自動ログオンが有効になっている公開環境のキオスクの場合、最小特権 (ローカルの標準ユーザー アカウントなど) を持つユーザーの種類を使用する必要があります。 キオスク モードの Azure Active Directory (AD) アカウントを構成するには、`domain\user@tenant.com` 形式を使用します。

## <a name="kiosk-web-browser-settings"></a>キオスク Web ブラウザー設定

これらの設定で、キオスクの Web ブラウザー アプリを制御します。 [クライアント アプリ](apps-add.md)を使用してキオスク デバイスに Web ブラウザー アプリを展開したことを確認してください。

1. 次の設定を入力します。

    - **[既定のホーム ページ URL]**: キオスク ブラウザーが開いたときや再起動したときに、ブラウザーで開く既定の URL を入力します。

    - **[ホーム] ボタン**: キオスク ブラウザーの [ホーム] ボタンを表示する (**[許可]**) か、非表示にします (**[未構成]**)。 既定では、ボタンは未構成です。

    - **[移動] ボタン**: [進む] ボタンと [戻る] ボタンを表示する (**[許可]**) か、非表示にします (**[未構成]**)。 既定では、移動ボタンは未構成です。

    - **[セッションの終了] ボタン**: [セッションの終了] ボタンを表示する (**[許可]**) か、非表示にします (**[未構成]**)。 表示されている場合、ユーザーがボタンを選択すると、アプリでセッションの終了が求められます。 確認すると、ブラウザーで閲覧データ (Cookie やキャッシュなど) がすべてクリアされ、既定の URL に戻ります。 既定では、ボタンは未構成です。 

    - **[ユーザーがアイドル時間の制限を超えるとブラウザーを最新の情報に更新する]**: キオスク ブラウザーを初期状態で再起動するまでの、セッションのアイドル時間を分数で入力します。 値は整数の 1 から 1440 分です。 既定では、値は空または空白となります。これは、アイドル タイムアウトがないことを意味します。

    - **[ブロックされた Web サイト]**: ブロックされた Web サイト URL のリスト (ワイルドカードがサポートされます)。 この設定を使用して、ブラウザーで特定のサイトを開けないようにします。 リストを含む .csv ファイルを**インポート**することもできます。 または、追加するサイトを含む .csv ファイルを作成 (**エクスポート**) します。

    - **[Web サイト例外]**: ブロックされた Web サイト URL の例外のリスト (ワイルドカードがサポートされます)。 この設定を使用して、ブラウザーで特定のサイトを開けるようにします。 これらの例外は、ブロックされた URL のサブセットです。 URL がブロックされた Web サイト リストと Web サイト例外リストにある場合、例外は有効です。

    リストを含む .csv ファイルを**インポート**することもできます。 または、追加するサイトを含む .csv ファイルを作成 (**エクスポート**) します。

2. **[OK]** を選択して変更を保存します。

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business デバイスでは、シングル アプリ キオスク モード、またはマルチ アプリ キオスク モードで実行するようにこれらのデバイスを構成することができます。 

#### <a name="single-full-screen-app-kiosks"></a>シングル全画面表示アプリ キオスク
次の設定を入力します。

- **[Universal Windows Platform (UWP) app identifier]\(ユニバーサル Windows プラットフォーム (UWP) アプリ識別子\)**: キオスク アプリの**アプリケーション ユーザー モデル ID (AUMID)** を入力します。 または、[Mobile Apps](apps-add.md) を使用して追加した既存の管理対象アプリを選択します。

    ID を取得する場合は、「[Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)」 (インストール済みアプリのアプリケーション ユーザー モデル ID を見つける) を参照してください。

- **[ユーザー アカウントの種類]**: **[ローカル ユーザー アカウント]** を選択して、(デバイスの) ローカル ユーザー アカウントか、キオスク アプリに関連付けられている Microsoft (MSA) アカウント ログインを入力します。 **[自動ログオン]** というユーザー アカウントの種類は、Windows Holographic for Business ではサポートされていません。

#### <a name="multi-app-kiosks"></a>マルチ アプリ キオスク
このモードのアプリはスタート メニューから使用できます。 ユーザーはこれらのアプリのみを開くことができます。

次の設定を入力します。

- **[管理対象アプリを追加]**: [Intune のクライアント アプリ](apps-add.md)を使用して追加した既存の管理対象アプリを選択します。
- **[Add app by AUMID]\(AUMID でアプリを追加\)**: [アプリの AUMID](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) を入力します (UWP アプリ)。
- **[スタート メニューのレイアウト]**: アプリの順序を含む、アプリをスタート メニューに表示する方法を説明する XML ファイルを入力します。 [[スタート画面のレイアウトのカスタマイズとエクスポート]](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) ではいくつかのガイダンスが提供され、Windows Holographic for Business デバイス用の特定の XML ファイルが含まれます。
- **[ユーザー アカウントの種類]**: 追加したアプリを使用できる 1 つ以上のユーザー アカウントを追加します。 サポートされているオプションは次のとおりです。 
  - **[HoloLens の訪問者]**: 訪問者のアカウントはゲスト アカウントであり、「[共有 PC モードの概念](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts)」の説明のとおり、ユーザーの資格情報や認証は必要ありません。
  - **[Azure AD ユーザー]**: デバイスへのサインインにはユーザーの資格情報が必要です。 `domain\user@tenant.com` という形式を使用します。
  - **[ローカル ユーザー アカウント]**: デバイスへのサインインにはユーザーの資格情報が必要です。 

サインインしたアカウントは、構成で定義されているアプリのみを利用できます。

## <a name="next-steps"></a>次の手順
[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
