---
title: Android の基幹業務アプリを Microsoft Intune に追加する
titlesuffix: ''
description: Android の基幹業務アプリを Microsoft Intune に追加する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: baf7ee4f1178b555a0fe311f0e3977941e1491fe
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905038"
---
# <a name="add-an-android-line-of-business-app-to-microsoft-intune"></a>Android の基幹業務アプリを Microsoft Intune に追加する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

基幹業務 (LOB) アプリとは、アプリのインストール ファイルから Intune に追加するアプリのことです。 通常、この種類のアプリは社内で作成されます。 Intune によって、ユーザーのデバイス上に LOB アプリがインストールされます。 

> [!Note]
> マネージド Google Play ストアの LOB アプリの詳細については、「[Working with a line-of-business app from the Managed Google Play store](apps-add-android-for-work.md?#working-with-a-line-of-business-app-from-the-managed-google-play-store)」 (マネージド Google Play ストアの基幹業務アプリを使用する) を参照してください。 

## <a name="step-1-specify-the-software-setup-file"></a>手順 1: ソフトウェアのセットアップ ファイルを指定する

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は、**[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[モバイル アプリ]** を選択します。
4. **[モバイル アプリ]** ワークロードで、**[管理]** > **[アプリ]** の順に選択します。
5. アプリの一覧の上にある **[追加]** を選択します。
6. **[アプリの追加]** ウィンドウで、**[基幹業務アプリ]** を選択します。

## <a name="step-2-configure-the-app-package-file"></a>手順 2: アプリのパッケージ ファイルを構成する

1. **[アプリの追加]** ウィンドウで、**[アプリのパッケージ ファイル]** を選択します。
2. **[アプリのパッケージ ファイル]** ウィンドウで、参照ボタンを選択します。 次に、拡張子が **.apk** の Android インストール ファイルを選択します。
3. 完了したら **[OK]** を選択します。


## <a name="step-3-configure-app-information"></a>手順 3: アプリ情報を構成する

1. **[アプリの追加]** ウィンドウで、**[アプリ情報]** を選択します。
2. **[アプリ情報]** ウィンドウで、アプリの詳細を追加します。 選択したアプリによっては、このウィンドウ内の一部の値が自動的に入力されている場合があります。
    - **[名前]**: アプリの名前を入力します。この名前は会社のポータルに表示されます。 使用するアプリ名はすべて一意にします。 同じアプリ名が 2 つ存在する場合、いずれか 1 つのアプリのみが会社のポータルに表示されます。
    - **[説明]**: アプリの説明を入力します。 説明はポータル サイトに表示されます。
    - **[発行元]**: アプリの発行元の名前を入力します。
    - **[オペレーティング システムの最小要件]**: アプリをインストールできる最小限のオペレーティング システム バージョンを一覧から選択します。 これよりも前のオペレーティング システムがアプリの割り当て先デバイスにインストールされている場合、そのアプリはインストールされません。
    - **[アプリのバージョンを無視する]**: アプリ開発者がアプリがを自動的に更新する場合は、**[はい]** に設定します。
    - **[カテゴリ]**: 1 つまたは複数の組み込みアプリ カテゴリを選択するか、作成したカテゴリを選択します。 カテゴリを使用すれば、ユーザーはポータル サイトを参照する際にアプリを見つけやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]**: ユーザーがアプリを参照する際に、ポータル サイトのメイン ページでアプリを目立つように表示します。
    - **[情報 URL]**: 必要に応じて、このアプリに関する情報が含まれる Web サイトの URL を入力します。 この URL はポータル サイトに表示されます。
    - **[プライバシー URL]**: 必要に応じて、このアプリのプライバシー情報が含まれる Web サイトの URL を入力します。 この URL はポータル サイトに表示されます。
    - **[開発者]**: 必要に応じて、アプリ開発者の名前を入力します。
    - **[所有者]**: 必要に応じて、このアプリの所有者の名前を入力します。 たとえば、「**人事部**」と入力します。
    - **[メモ]**: このアプリに関連付けるメモを入力します。
    - **[ロゴ]**: アプリに関連付けるアイコンをアップロードします。 ユーザーが会社のポータルを参照するとき、アプリにアイコンが表示されます。
3. 完了したら **[OK]** を選択します。

## <a name="step-4-finish-up"></a>手順 4: 完了

1. **[アプリの追加]** ウィンドウで、アプリの詳細が正しいことを確認します。
2. **[追加]** を選択して、アプリを Intune にアップロードします。

作成したアプリがアプリ一覧に表示されます。 一覧から、選択したグループにアプリを割り当てることができます。 詳細については、[アプリをグループに割り当てる方法](apps-deploy.md)に関するページを参照してください。

## <a name="step-5-update-a-line-of-business-app"></a>手順 5: 基幹業務アプリの更新

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!Note]
> Intune サービスで新しい APK ファイルをデバイスへ正常に展開するには、APK パッケージの AndroidManifest.xml ファイルの `android:versionCode` 文字列をインクリメントする必要があります。

## <a name="next-steps"></a>次の手順

- 作成したアプリはアプリの一覧に表示されます。 選択したグループにアプリを割り当てることができます。 詳細については、[アプリをグループに割り当てる方法](apps-deploy.md)に関するページを参照してください。

- アプリのプロパティと割り当てを監視する方法について説明します。 「[アプリ情報と割り当てを監視する方法](apps-monitor.md)」を参照してください。

- Intune におけるアプリのコンテキストについて説明します。 「[デバイスとアプリのライフサイクルの概要](introduction-device-app-lifecycles.md)」を参照してください。
