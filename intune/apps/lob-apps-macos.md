---
title: macOS の基幹業務アプリを Microsoft Intune に追加する方法
titleSuffix: ''
description: macOS の基幹業務 (LOB) アプリを Microsoft Intune に追加する方法について学習します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c7aa6af751e5ab3e1e3cdff6b1d2e3d6693f65df
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755172"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>macOS の基幹業務 (LOB) アプリを Microsoft Intune に追加する方法

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

この記事の情報を使用して、Microsoft Intune に macOS の基幹業務アプリを追加できます。 基幹業務ファイルを Microsoft Intune にアップロードする前に、外部ツールをダウンロードして *.pkg* ファイルを前処理する必要があります。 *.pkg* ファイルの前処理は、macOS デバイス上で行う必要があります。

> [!NOTE]
> macOS Catalina 10.15 のリリースからは、アプリを Intune に追加する前に、macOS LOB アプリが公証になっていることを確認してください。 LOB アプリの開発者がそれぞれのアプリを公証していなかった場合、お客様のユーザーの macOS デバイス上でそのアプリを実行することはできません。 アプリが公証かどうかを確認する方法について詳しくは、[macOS Catalina に備えた macOS アプリの公証](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Notarizing-your-macOS-apps-to-prepare-for-macOS/ba-p/808579)に関するページをご覧ください。

> [!NOTE]
> macOS デバイスのユーザーは Stocks や Maps などの一部の macOS 組み込みアプリを削除できますが、Intune を使ってこれらのアプリを再展開することはできません。 エンド ユーザーがこれらのアプリを削除した場合は、アプリ ストアから手動で再インストールする必要があります。

## <a name="before-your-start"></a>開始する前に

基幹業務ファイルを Microsoft Intune にアップロードするには、外部ツールをダウンロードし、ダウンロードしたツールを実行可能ファイルとしてマークし、 *.pkg* ファイルをツールで前処理しておく必要があります。 *.pkg* ファイルの前処理は、macOS デバイス上で行う必要があります。 Mac 用の Intune アプリ ラッピング ツールを使って、Mac アプリを Microsoft Intune で管理できるようにします。

> [!IMPORTANT]
> *.pkg* ファイルは、Apple Developer アカウントから取得した "Developer ID Installer" 証明書を使用して署名されている必要があります。 Microsoft Intune への macOS LOB アプリのアップロードに使うことができるのは、 *.pkg* ファイルだけです。 *.dmg* から *.pkg* など、他の形式への変換はサポートされていません。
>

1. [Mac 用 Intune アプリ ラッピング ツール](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac)をダウンロードします。

    > [!NOTE]
    > **Mac 用 Intune アプリ ラッピング ツール**は、macOS コンピューター上で実行する必要があります。 

2. ダウンロードしたツールを実行可能ファイルとしてマークします。
   - ターミナル アプリを起動します。
   - ディレクトリを `IntuneAppUtil` が配置されている場所に変更します。
   - 次のコマンドを実行して、ツールを実行可能ファイルにします。<br> 
       `chmod +x IntuneAppUtil`

3. **Mac 用 Intune アプリ ラッピング ツール**内で `IntuneAppUtil` コマンドを使って、 *.intunemac* ファイルから *.pkg* LOB アプリ ファイルをラッピングします。<br>

    macOS 用 Intune アプリ ラッピング ツールMicrosoft Intune アプリ ラッピング ツールで使用するサンプル コマンド:
    > [!IMPORTANT]
    > `IntuneAppUtil` コマンドを実行する前に、引数 `<source_file>` にスペースが含まれていないことを確認してください。

    - `IntuneAppUtil -h`<br>
    このコマンドでは、ツールの使用情報が表示されます。
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    このコマンドは、 *.pkg* LOB アプリ ファイルを *.intunemac* ファイルにラッピングします。
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    このコマンドは、作成された *.intunemac* ファイルで検出されたパラメーターとバージョンを抽出します。

## <a name="select-the-app-type"></a>アプリの種類を選択する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** の順に選択します。
3. **[アプリの種類の選択]** ペインの **[その他]** のアプリの種類で、 **[基幹業務アプリ]** を選択します。
4. **[選択]** をクリックします。 **[アプリの追加]** 手順が表示されます。

## <a name="step-1---app-information"></a>ステップ 1 - アプリ情報

### <a name="select-the-app-package-file"></a>アプリ パッケージ ファイルを選択する

1. **[アプリの追加]** ペインで、 **[アプリ パッケージ ファイルの選択]** をクリックします。 
2. **[アプリのパッケージ ファイル]** ウィンドウで、参照ボタンを選択します。 次に、拡張子が *.intunemac* の macOS インストール ファイルを選択します。
   アプリの詳細が表示されます。
3. 操作を完了したら、 **[アプリ パッケージ ファイル]** ペインの **[OK]** を選択してアプリを追加します。

### <a name="set-app-information"></a>アプリ情報を設定する

1. **[アプリ情報]** ページで、アプリの詳細を追加します。 選択したアプリによっては、このウィンドウ内の一部の値が自動的に入力されている場合があります。
    - **名前**:アプリの名前を入力します。これは会社のポータルに表示されます。 使用するアプリ名はすべて一意にします。 同じアプリ名が 2 つ存在する場合、いずれか 1 つのアプリのみが会社のポータルに表示されます。
    - **説明**:アプリの説明を入力します。 説明はポータル サイトに表示されます。
    - **[発行元]** : アプリの発行元の名前を入力します。
    - **[最低限のオペレーティング システム]** :アプリをインストールできる最小限のオペレーティング システム バージョンを一覧から選択します。 これよりも前のオペレーティング システムがアプリの割り当て先デバイスにインストールされている場合、そのアプリはインストールされません。
    - **[カテゴリ]** :1 つまたは複数の組み込みアプリ カテゴリを選択するか、ご自身で作成したカテゴリを選択します。 カテゴリを使用すれば、ユーザーはポータル サイトを参照する際にアプリを見つけやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]** : ユーザーがアプリを参照するとき、会社のポータルのメイン ページにアプリが目立つように表示されます。
    - **[情報 URL]** : このアプリに関する情報が含まれる Web サイトの URL を入力することもできます。 この URL はポータル サイトに表示されます。
    - **[プライバシー URL]** : このアプリのプライバシー情報が含まれる Web サイトの URL を入力することもできます。 この URL はポータル サイトに表示されます。
    - **[開発者]** : (省略可能) アプリ開発者の名前を入力します。
    - **[所有者]** : (省略可能) このアプリの所有者の名前を入力します。 たとえば、「**人事部**」と入力します。
    - **[メモ]** : このアプリに関連付けるメモを入力します。
    - **[ロゴ]** : アプリに関連付けるアイコンをアップロードします。 ユーザーが会社のポータルを参照するとき、アプリにアイコンが表示されます。
2. **[次 へ]** をクリックして **[スコープ タグ]** ページを表示します。

## <a name="step-2---select-scope-tags-optional"></a>ステップ 2 - スコープのタグを選択する (省略可能)
スコープのタグを使って、Intune のクライアント アプリの情報を表示できるユーザーを決定することができます。 スコープのタグの詳細については、[分散 IT のためのロールベースのアクセス制御とスコープのタグの使用](../fundamentals/scope-tags.md)に関するページをご覧ください。

1. **[スコープ タグを選択]** をクリックして、必要に応じてアプリのスコープ タグを追加します。 
2. **[次へ]** をクリックして、 **[割り当て]** ページを表示します。

## <a name="step-3---assignments"></a>ステップ 3 - 割り当て

1. アプリのグループ割り当てについて、 **[必須]** 、 **[登録済みデバイスで使用可能]** 、または **[アンインストール]** を選択します。 詳細については、「[ユーザーとデバイスを整理するためのグループを追加する](~/fundamentals/groups-add.md)」と「[Microsoft Intune を使用してアプリをグループに割り当てる](apps-deploy.md)」を参照してください。
2. **[次へ]** をクリックして、 **[確認と作成]** ページを表示します。 

## <a name="step-4---review--create"></a>ステップ 4 - 確認と作成

1. アプリに入力した値と設定を確認します。
2. 完了したら、 **[作成]** をクリックしてアプリを Intune に追加します。

    基幹業務アプリの **[概要]** ブレードが表示されます。

作成したアプリはアプリの一覧に表示され、選択したグループに割り当てることができるようになります。 詳細については、[アプリをグループに割り当てる方法](apps-deploy.md)に関するページを参照してください。

> [!NOTE]
> *.pkg* ファイルに複数のアプリまたはアプリ インストーラーが含まれる場合、Microsoft Intune は、インストールされるすべてのアプリがデバイス上で検出された場合にのみ、"*アプリ*" が正常にインストールされたことを報告します。

## <a name="update-a-line-of-business-app"></a>基幹業務アプリを更新する

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Intune サービスで新しい *.pkg* ファイルをデバイスに正常に展開するには、パッケージの `version` と、 *.pkg* パッケージ内の *packageinfo* ファイルの `CFBundleVersion` 文字列をインクリメントする必要があります。

## <a name="next-steps"></a>次のステップ

- 作成したアプリがアプリの一覧に表示されます。 選択したグループにアプリを割り当てることができます。 詳細については、[アプリをグループに割り当てる方法](apps-deploy.md)に関するページを参照してください。

- アプリのプロパティと割り当てを監視する方法について説明します。 詳細については、「[アプリ情報と割り当てを監視する方法](apps-monitor.md)」を参照してください。

- Intune におけるアプリのコンテキストについて説明します。 詳細については、「[デバイスとアプリのライフサイクルの概要](../fundamentals/device-lifecycle.md)」を参照してください。
