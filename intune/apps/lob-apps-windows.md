---
title: Windows の基幹業務アプリを Microsoft Intune に追加する
titleSuffix: ''
description: Microsoft Intune を使って Windows の基幹業務 (LOB) アプリを追加する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0d7a166e97cb9161df7c6d024e200adec0974715
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75204971"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Windows の基幹業務アプリを Microsoft Intune に追加する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

基幹業務 (LOB) アプリとは、アプリのインストール ファイルから追加するアプリのことです。 通常、この種類のアプリは社内で作成されます。 次に、Microsoft Intune に Windows の LOB アプリを追加するのに役立つ手順を示します。

> [!IMPORTANT]
> *.msi* の拡張子を持ったインストール ファイルを使って Win32 アプリを展開する場合は、[Intune 管理拡張機能](../apps/intune-management-extension.md)の使用を検討してください。 AutoPilot 登録中に Win32 アプリと基幹業務アプリのインストールを混在させると、アプリのインストールが失敗する場合があります。  

## <a name="step-1-specify-the-software-setup-file"></a>手順 1:ソフトウェアのセットアップ ファイルを指定する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** の順に選択します。
3. **[アプリの追加]** ウィンドウで、 **[アプリの種類]** として **[基幹業務アプリ]** を選択します。

## <a name="step-2-configure-the-app-package-file"></a>手順 2:アプリのパッケージ ファイルを構成する

1. **[アプリの追加]** ウィンドウで、 **[アプリのパッケージ ファイル]** を選択します。
2. **[アプリのパッケージ ファイル]** ウィンドウで、参照ボタンを選択します。 次に、拡張子が **.msi**、 **.appx**、または **.appxbundle** の Windows インストール ファイルを選択します。

    > [!NOTE]
    > Windows アプリのファイル拡張子には、 **.msi**、 **.appx**、 **.appxbundle**、 **.msix**、 **.msixbundle** が含まれます。  

1. 完了したら **[OK]** を選択します。


## <a name="step-3-configure-app-information"></a>手順 3:アプリ情報の構成

1. **[アプリの追加]** ウィンドウで、 **[アプリ情報]** を選択します。
2. **[アプリ情報]** ウィンドウで、以下の情報を構成します。 このウィンドウの一部の値は、自動的に入力される場合があります。
    - **名前**:アプリの名前を入力します。これは会社のポータルに表示されます。 使用するアプリ名はすべて一意にします。 同じアプリ名が 2 つ存在する場合、いずれか 1 つのアプリのみが会社のポータルに表示されます。
    - **説明**:アプリの説明を入力します。 説明はポータル サイトに表示されます。
    - **[発行元]** : アプリの発行元の名前を入力します。
    - **[アプリのバージョンを無視する]** :アプリ開発者がアプリを自動的に更新する場合は、 **[はい]** に設定します。 このオプションは、モバイル .msi アプリにのみ適用されます。
    - **[カテゴリ]** : 1 つまたは複数の組み込みアプリ カテゴリを選択するか、ご自身で作成したカテゴリを選択します。 カテゴリを使用すれば、ユーザーはポータル サイトを参照する際にアプリを見つけやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]** : ユーザーがアプリを参照するとき、会社のポータルのメイン ページにアプリが目立つように表示されます。
    - **[情報 URL]** :必要に応じて、このアプリに関する情報が含まれる Web サイトの URL を入力します。 この URL はポータル サイトに表示されます。
    - **[プライバシー URL]** :必要に応じて、このアプリのプライバシー情報が含まれる Web サイトの URL を入力します。 この URL はポータル サイトに表示されます。
    - **[コマンド ライン引数]** :必要に応じて、実行時に .msi ファイルに適用するコマンド ライン引数を入力します。  たとえば、「 **/q**」と入力します。 **/i** や **/x** などの msiexec コマンドまたは引数は、自動的に使用されるため、含めないでください。 詳細については、「[Command-Line Options (コマンド ライン オプション)](https://docs.microsoft.com/windows/desktop/Msi/command-line-options)」をご覧ください。 .MSI ファイルで追加のコマンドライン オプションが必要な場合は、[Win32 アプリ管理](app-management.md)の使用を検討してください。
    - **[開発者]** : (省略可能) アプリ開発者の名前を入力します。
    - **[所有者]** : (省略可能) このアプリの所有者の名前を入力します。 たとえば、「**人事部**」と入力します。
    - **[メモ]** : このアプリに関連付けるメモを入力します。
    - **[ロゴ]** : アプリに関連付けるアイコンをアップロードします。 ユーザーが会社のポータルを参照するとき、アプリにアイコンが表示されます。
3. 完了したら **[OK]** を選択します。

## <a name="step-4-finish-up"></a>手順 4:完了

1. **[アプリの追加]** ウィンドウで、アプリ情報を正しく構成したことを確認します。
2. **[追加]** を選択して、アプリを Intune にアップロードします。

## <a name="step-5-update-a-line-of-business-app"></a>手順 5:基幹業務アプリを更新する

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

   > [!NOTE]
   > Intune サービスで新しい appx ファイルをデバイスへ正常に展開するには、APK パッケージ内の AndroidManifest.xml ファイルの `Version` 文字列の値を増やす必要があります。

## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>バージョン チェック プロセスを無視する自己更新モバイル MSI アプリの構成

バージョン チェック プロセスを無視するように、既知の自己更新モバイル MSI アプリを構成することができます。

一部の MSI インストーラー ベースのアプリは、アプリケーション開発者または別の更新方法によって自動更新されます。 これらの自動更新される MSI アプリには、 **[アプリ情報]** ウィンドウで **[アプリのバージョンを無視する]** を設定できます。 この設定を **[はい]** に切り替えると、Microsoft Intune で Windows クライアントにインストールされているアプリのバージョンが強制されることはありません。

この機能は、競合状態になるのを防ぐのに役立ちます。 たとえば、アプリ開発者によってアプリが自動的に更新され、Intune によって更新される場合、競合状態が発生する可能性があります。 両方が Windows クライアント上のアプリのバージョンを強制しようとして、競合が発生することがあります。

## <a name="next-steps"></a>次のステップ

- 作成したアプリはアプリの一覧に表示されます。 選択したグループにアプリを割り当てることができます。 詳細については、[アプリをグループに割り当てる方法](apps-deploy.md)に関するページを参照してください。

- アプリのプロパティと割り当てを監視する方法について説明します。 「[アプリ情報と割り当てを監視する方法](apps-monitor.md)」を参照してください。

- Intune におけるアプリのコンテキストについて説明します。 「[Microsoft Intune のアプリ ライフサイクルの概要](app-lifecycle.md)」を参照してください。

- Win32 アプリの詳細について学習します。 「[Win32 アプリの管理](~/apps/apps-win32-app-management.md)」を参照してください。
