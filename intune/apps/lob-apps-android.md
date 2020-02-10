---
title: Android の基幹業務アプリを Microsoft Intune に追加する
description: Android の基幹業務 (LOB) アプリを Microsoft Intune に追加する方法について学習します。
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
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cd3736a08f09fcb5ee953626c63e336ca7f9af81
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755206"
---
# <a name="add-an-android-line-of-business-app-to-microsoft-intune"></a>Android の基幹業務アプリを Microsoft Intune に追加する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

基幹業務 (LOB) アプリとは、アプリのインストール ファイルから Intune に追加するアプリのことです。 通常、この種類のアプリは社内で作成されます。 Intune によって、ユーザーのデバイス上に LOB アプリがインストールされます。 

> [!Note]
> LOB アプリと Google Play Developer Console の詳細については、「[Google Developer Console を使用したマネージド Google Play プライベート (LOB) アプリの公開](apps-add-android-for-work.md?#managed-google-play-private-lob-app-publishing-using-the-google-developer-console)」を参照してください。 

> [!Note]
> Android for Work については、「[Intune で Google Play マネージド アプリを Android Enterprise デバイスに追加する](apps-add-android-for-work.md)」を参照してください。 

## <a name="select-the-app-type"></a>アプリの種類を選択する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** の順に選択します。
3. **[アプリの種類の選択]** ペインの **[その他]** のアプリの種類で、 **[基幹業務アプリ]** を選択します。
4. **[選択]** をクリックします。 **[アプリの追加]** 手順が表示されます。

## <a name="step-1---app-information"></a>ステップ 1 - アプリ情報

### <a name="select-the-app-package-file"></a>アプリ パッケージ ファイルを選択する

1. **[アプリの追加]** ペインで、 **[アプリ パッケージ ファイルの選択]** をクリックします。 
2. **[アプリのパッケージ ファイル]** ウィンドウで、参照ボタンを選択します。 次に、拡張子が **.apk** の Android インストール ファイルを選択します。
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

## <a name="step-5-update-a-line-of-business-app"></a>手順 5:基幹業務アプリを更新する

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

Android デバイスで **[Check apps from external sources]\(外部ソースのアプリを確認する\)** が有効な場合、更新プログラムをインストールする前にユーザーにプロンプトが表示されます。 それ以外の場合は、更新プログラムが自動的にインストールされます。

> [!Note]
> Intune サービスで新しい APK ファイルをデバイスへ正常に展開するには、APK パッケージの AndroidManifest.xml ファイルの `android:versionCode` 文字列をインクリメントする必要があります。

## <a name="next-steps"></a>次のステップ

- 作成したアプリはアプリの一覧に表示されます。 選択したグループにアプリを割り当てることができます。 詳細については、[アプリをグループに割り当てる方法](apps-deploy.md)に関するページを参照してください。

- アプリのプロパティと割り当てを監視する方法について説明します。 「[アプリ情報と割り当てを監視する方法](apps-monitor.md)」を参照してください。

- Intune におけるアプリのコンテキストについて説明します。 「[デバイスとアプリのライフサイクルの概要](../fundamentals/device-lifecycle.md)」を参照してください。
