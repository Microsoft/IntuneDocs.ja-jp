---
title: iOS の基幹業務アプリを Microsoft Intune に追加する
titleSuffix: ''
description: iOS の基幹業務 (LOB) アプリを Microsoft Intune に追加する方法について学習します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4c9b11e8968426a39c3bfc3d13a0a42c97a04f27
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72497811"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>iOS の基幹業務アプリを Microsoft Intune に追加する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

この記事の情報を使用して、Microsoft Intune に iOS の基幹業務 (LOB) アプリを追加できます。 基幹業務 (LOB) アプリとは、IPA アプリのインストール ファイルから Intune に追加するアプリのことです。 通常、この種類のアプリは社内で作成されます。 まず、iOS Developer Enterprise Program に参加する必要があります。 これを行う方法の詳細については、[Apple の Web サイト](https://developer.apple.com/programs/ios/enterprise/)を参照してください。

>[!NOTE]
>iOS デバイスのユーザーは Stocks や Maps などの一部の iOS 組み込みアプリを削除できます。 Intune を使用してこれらのアプリを再展開することはできません。 ユーザーがこれらのアプリを削除した場合は、アプリ ストアから手動で再インストールする必要があります。
>
>iOS の LOB アプリには、アプリごとに最大 4 GB のサイズ制限があります。

## <a name="step-1-specify-the-software-setup-file"></a>手順 1.ソフトウェアのセットアップ ファイルを指定する

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
3. **[Intune]** ウィンドウで、 **[クライアント アプリ]** を選択します。
4. **[クライアント アプリ]** ワークロードで、 **[管理]**  >  **[アプリ]** の順に選択します。
5. アプリの一覧の上にある **[追加]** を選択します。
6. **[アプリの追加]** ウィンドウで、 **[基幹業務アプリ]** を選択します。

## <a name="step-2-configure-the-app-package-file"></a>手順 2: アプリのパッケージ ファイルを構成する

1. **[アプリの追加]** ウィンドウで、 **[アプリのパッケージ ファイル]** を選択します。
2. **[アプリのパッケージ ファイル]** ウィンドウで、参照ボタンを選択します。 次に、拡張子が **.ipa** の iOS インストール ファイルを選択します。
3. 完了したら **[OK]** を選択します。


## <a name="step-3-configure-app-information"></a>手順 3: アプリ情報の構成

1. **[アプリの追加]** ウィンドウで、 **[アプリ情報]** を選択します。
2. **[アプリ情報]** ウィンドウで、アプリの詳細を追加します。 選択したアプリによっては、このウィンドウ内の一部の値が自動的に入力されている場合があります。
    - **名前**: アプリの名前を入力します。これは会社のポータルに表示されます。 使用するアプリ名はすべて一意にします。 同じアプリ名が 2 つ存在する場合、いずれか 1 つのアプリのみが会社のポータルに表示されます。
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
3. 完了したら **[OK]** を選択します。

## <a name="step-4-finish-up"></a>手順 4:完了

1. **[アプリの追加]** ウィンドウで、アプリの詳細が正しいことを確認します。
2. **[追加]** を選択して、アプリを Intune にアップロードします。

作成したアプリがアプリ一覧に表示されます。 一覧から、選択したグループにアプリを割り当てることができます。 詳細については、[アプリをグループに割り当てる方法](apps-deploy.md)に関するページを参照してください。

> [!NOTE]
> iOS LOB アプリのプロビジョニング プロファイルは、期限切れになる 30 日前に通知されます。

## <a name="step-5-update-a-line-of-business-app"></a>手順 5:基幹業務アプリを更新する

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

基幹業務アプリの更新プログラムは自動的にインストールされます。

> [!NOTE]
> Intune サービスで新しい IPA ファイルをデバイスに正常に展開するには、IPA パッケージの Info.plist ファイルの `CFBundleVersion` 文字列をインクリメントする必要があります。

## <a name="next-steps"></a>次の手順

- 作成したアプリはアプリの一覧に表示されます。 選択したグループにアプリを割り当てることができます。 詳細については、[アプリをグループに割り当てる方法](apps-deploy.md)に関するページを参照してください。

- アプリのプロパティと割り当てを監視する方法について説明します。 「[アプリ情報と割り当てを監視する方法](apps-monitor.md)」を参照してください。

- Intune におけるアプリのコンテキストについて説明します。 「[デバイスとアプリのライフサイクルの概要](../fundamentals/device-lifecycle.md)」を参照してください。
