---
title: Windows Phone の基幹業務アプリを Microsoft Intune に追加する
titleSuffix: ''
description: Microsoft Intune を使って Windows Phone の基幹業務 (LOB) アプリを追加する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e1540abcc9ff7a5958da55154258e1fc1d9555dd
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507163"
---
# <a name="add-a-windows-phone-line-of-business-app-to-microsoft-intune"></a>Windows Phone の基幹業務アプリを Microsoft Intune に追加する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

この記事の情報を使用して、Microsoft Intune に Windows Phone の基幹業務 (LOB) アプリを追加できます。 LOB アプリとは、アプリのインストール ファイルから Intune に追加するアプリのことです。 通常、この種類のアプリは社内で作成されます。 Intune によって、ユーザーのデバイス上に LOB アプリがインストールされます。 

## <a name="step-1-specify-the-software-setup-file"></a>手順 1.ソフトウェアのセットアップ ファイルを指定する

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
3. **[Intune]** ウィンドウで、 **[クライアント アプリ]** を選択します。
4. **[クライアント アプリ]** ワークロードで、 **[管理]**  >  **[アプリ]** の順に選択します。
5. アプリの一覧の上にある **[追加]** を選択します。
6. **[アプリの追加]** ウィンドウで、 **[基幹業務アプリ]** を選択します。

## <a name="step-2-configure-the-app-package-file"></a>手順 2: アプリのパッケージ ファイルを構成する

1. **[アプリの追加]** ウィンドウで、 **[アプリのパッケージ ファイル]** を選択します。
2. **[アプリのパッケージ ファイル]** ウィンドウで、参照ボタンを選択します。 次に、拡張子が **.xap** の Windows Phone インストール ファイルを選択します。
3. 完了したら **[OK]** を選択します。


## <a name="step-3-configure-app-information"></a>手順 3: アプリ情報の構成

1. **[アプリの追加]** ウィンドウで、 **[アプリ情報]** を選択します。
2. **[アプリ情報]** ウィンドウで、アプリの情報を構成します。 選択したアプリによっては、このウィンドウ内の一部の値が自動的に入力されている場合があります。
    - **名前**: アプリの名前を入力します。これは会社のポータルに表示されます。 使用するアプリ名はすべて一意にします。 同じアプリ名が 2 つ存在する場合、いずれか 1 つのアプリのみが会社のポータルに表示されます。
    - **説明**:アプリの説明を入力します。 説明はポータル サイトに表示されます。
    - **[発行元]** : アプリの発行元の名前を入力します。
    - **[カテゴリ]** : 1 つまたは複数の組み込みアプリ カテゴリを選択するか、ご自身で作成したカテゴリを選択します。 カテゴリを使用すれば、ユーザーはポータル サイトを参照する際にアプリを見つけやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]** : ユーザーがアプリを参照するとき、会社のポータルのメイン ページにアプリが目立つように表示されます。
    - **[情報 URL]** : このアプリに関する情報が含まれる Web サイトの URL を入力することもできます。 この URL はポータル サイトに表示されます。
    - **[プライバシー URL]** : このアプリのプライバシー情報が含まれる Web サイトの URL を入力することもできます。 この URL はポータル サイトに表示されます。
    - **[開発者]** : (省略可能) アプリ開発者の名前を入力します。
    - **[所有者]** : (省略可能) このアプリの所有者の名前を入力します。 たとえば、「**人事部**」と入力します。
    - **[メモ]** : このアプリに関連付けるメモを入力します。
    - **[ロゴ]** : アプリに関連付けるアイコンをアップロードします。 ユーザーが会社のポータルを参照するとき、アプリにアイコンが表示されます。
3. 完了したら **[OK]** を選択します。

## <a name="step-4-finish-up"></a>手順 4:完了

1. **[アプリの追加]** ウィンドウで、情報を正しく構成したことを確認します。
2. **[追加]** を選択して、アプリを Intune にアップロードします。

## <a name="next-steps"></a>次の手順

- 作成したアプリはアプリの一覧に表示されます。 選択したグループにアプリを割り当てることができます。 詳細については、[アプリをグループに割り当てる方法](apps-deploy.md)に関するページを参照してください。

- アプリのプロパティと割り当てを監視する方法について説明します。 「[アプリ情報と割り当てを監視する方法](apps-monitor.md)」を参照してください。

- Intune におけるアプリのコンテキストについて説明します。 「[デバイスとアプリのライフサイクルの概要](../fundamentals/device-lifecycle.md)」を参照してください。
