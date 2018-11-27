---
title: macOS の基幹業務アプリを Microsoft Intune に追加する方法
titlesuffix: ''
description: Microsoft Intune への macOS の基幹業務 (LOB) アプリの追加について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 1b60610be892afd10ace568694b57cc18190eec1
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180011"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>macOS の基幹業務 (LOB) アプリを Microsoft Intune に追加する方法

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事の情報を使用して、Microsoft Intune に macOS の基幹業務アプリを追加できます。 基幹業務ファイルを Microsoft Intune にアップロードする前に、外部ツールをダウンロードして *.pkg* ファイルを前処理する必要があります。 *.pkg* ファイルの前処理は、macOS デバイス上で行う必要があります。

> [!NOTE]
> macOS デバイスのユーザーは Stocks や Maps などの一部の macOS 組み込みアプリを削除できますが、Intune を使ってこれらのアプリを再展開することはできません。 エンド ユーザーがこれらのアプリを削除した場合は、アプリ ストアから手動で再インストールする必要があります。

## <a name="before-your-start"></a>開始する前に

基幹業務ファイルを Microsoft Intune にアップロードする前に、外部ツールをダウンロードして *.pkg* ファイルを前処理する必要があります。 *.pkg* ファイルの前処理は、macOS デバイス上で行う必要があります。 Mac 用の Intune アプリ ラッピング ツールを使って、Mac アプリを Microsoft Intune で管理できるようにします。

> [!IMPORTANT]
> Microsoft Intune への macOS LOB アプリのアップロードに使うことができるのは、*.pkg* ファイルだけです。 *.dmg* から *.pkg* など、他の形式への変換はサポートされていません。

1. [Mac 用 Intune アプリ ラッピング ツール](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac)をダウンロードして実行します。

    > [!NOTE]
    > **Mac 用 Intune アプリ ラッピング ツール**は、macOS コンピューター上で実行する必要があります。

2. **Mac 用 Intune アプリ ラッピング ツール**内で `IntuneAppUtil` コマンドを使って、*.intunemac* ファイルから *.pkg* LOB アプリ ファイルをラッピングします。<br>

    macOS 用 Intune アプリ ラッピング ツールMicrosoft Intune アプリ ラッピング ツールで使用するサンプル コマンド:
    
    - `IntuneAppUtil -h`<br>
    このコマンドでは、ツールの使用情報が表示されます。
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    このコマンドは、*.pkg* LOB アプリ ファイルを *.intunemac* ファイルにラッピングします。
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    このコマンドは、作成された *.intunemac* ファイルで検出されたパラメーターとバージョンを抽出します。

## <a name="step-1---specify-the-software-setup-file"></a>手順 1 - ソフトウェアのセットアップ ファイルを指定する

1. [Azure ポータル](https://portal.azure.com) にサインインします。
2. **すべてのサービス** > **Intune** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[クライアント アプリ]** を選択します。
4. **[クライアント アプリ]** ワークロードで、**[管理]** > **[アプリ]** の順に選択します。
5. アプリの一覧の上にある **[追加]** を選択します。
6. **[アプリの追加]** ウィンドウで、**[基幹業務アプリ]** を選択します。

## <a name="step-2---configure-the-app-package-file"></a>手順 2 - アプリのパッケージ ファイルを構成する

1. **[アプリの追加]** ウィンドウで、**[アプリのパッケージ ファイル]** を選択します。
2. **[アプリのパッケージ ファイル]** ウィンドウで、参照ボタンを選び、拡張子 *.intunemac* が付いた macOS インストール ファイルを選択します。
3. 終了したら **[OK]** を選択します。


## <a name="step-3---configure-app-information"></a>手順 3 - アプリ情報を構成する

1. **[アプリの追加]** ウィンドウで、**[アプリ情報]** を選択します。
2. **[アプリ情報]** ウィンドウで、アプリの詳細を追加します。 選択したアプリによっては、このウィンドウ内の一部の値が自動的に入力されている場合があります。
    - **[名前]** - ポータル サイトに表示するアプリの名前を入力します。 使用するアプリ名はすべて一意にします。 同じアプリ名が 2 つ存在する場合、会社のポータルではそのいずれかのみがユーザーに表示されます。
    - **説明** - ポータル サイトでユーザーに表示するアプリの説明を入力します。
    - **[発行元]** - アプリの発行元の名前を入力します。
    - **[オペレーティング システムの最小要件]** - アプリをインストールできる最小限のオペレーティング システム バージョンを一覧から選択します。 これよりも前のオペレーティング システムがアプリの割り当て先デバイスにインストールされている場合、そのアプリはインストールされません。
    - **[カテゴリ]** - 1 つまたは複数の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 この操作を行うと、会社のポータルを閲覧するときに、ユーザーがアプリを探しやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]** - ユーザーがアプリを探す際に、会社のポータルのメイン ページでアプリを目立つように表示します。
    - **[情報 URL]** - 必要に応じて、このアプリに関する情報が含まれる Web サイトの URL を入力します。 この URL は会社のポータルでユーザーに表示されます。
    - **[プライバシー URL]** - 必要に応じて、このアプリのプライバシー情報が含まれる Web サイトの URL を入力します。 この URL は会社のポータルでユーザーに表示されます。
    - **[開発者]** - 必要に応じて、アプリ開発者の名前を入力します。
    - **[所有者]** - 必要に応じて、このアプリの所有者の名前 ("**人事部**" など) を入力します。
    - **[メモ]** - このアプリに関連付けるメモを入力します。
    - **[ロゴ]** - アプリに関連付けるアイコンをアップロードします。 ユーザーが会社のポータルを参照するとき、アプリにこのアイコンが表示されます。
3. 終了したら **[OK]** を選択します。

## <a name="step-4---finish-up"></a>手順 4. - 完了

1. **[アプリの追加]** ウィンドウで、アプリの詳細が正しいことを確認します。
2. **[追加]** を選択して、アプリを Intune にアップロードします。

作成したアプリはアプリの一覧に表示され、選択したグループに割り当てることができるようになります。 詳細については、[アプリをグループに割り当てる方法](apps-deploy.md)に関するページを参照してください。

> [!NOTE]
> *.pkg* ファイルに複数のアプリまたはアプリ インストーラーが含まれる場合、Microsoft Intune は、インストールされるすべてのアプリがデバイス上で検出された場合にのみ、"*アプリ*" が正常にインストールされたことを報告します。

## <a name="step-5---update-a-line-of-business-app"></a>手順 5 - 基幹業務アプリの更新

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Intune サービスで新しい *.pkg* ファイルをデバイスに正常に展開するには、パッケージの `version` と、*.pkg* パッケージ内の *packageinfo* ファイルの `CFBundleVersion` 文字列をインクリメントする必要があります。

## <a name="next-steps"></a>次の手順

- 作成したアプリがアプリの一覧に表示されます。 選択したグループにアプリを割り当てることができます。 詳細については、[アプリをグループに割り当てる方法](apps-deploy.md)に関するページを参照してください。

- アプリのプロパティと割り当てを監視する方法について説明します。 詳細については、「[アプリ情報と割り当てを監視する方法](apps-monitor.md)」を参照してください。

- Intune におけるアプリのコンテキストについて説明します。 詳細については、「[デバイスとアプリのライフサイクルの概要](introduction-device-app-lifecycles.md)」を参照してください。
