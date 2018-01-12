---
title: "Intune を使用して macOS デバイスに Office 365 をインストールします。"
titlesuffix: Azure portal
description: "MacOS デバイスに Office 365 アプリをインストールするが容易に Intune を使用する方法について説明します。"
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5e0ad0b99a2c8a602b5e542530a1d437065461b2
ms.sourcegitcommit: a9d734877340894637e03f4b4ef83f7d01ddedc8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2017
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>Office 365 を Microsoft Intune で macOS デバイスに割り当てる方法

このアプリの種類を簡単に Office 365 アプリを macOS デバイスに割り当てることできます。 この新しいアプリの種類では、Word、Excel、PowerPoint、Outlook、および OneNote をインストールすることができます。 これらのアプリで、Microsoft の自動更新 (MAU)、アプリをより安全かつ最新に保つためにも付属しています。 必要なアプリは、Intune コンソールのアプリ一覧に 1 つのアプリとして表示されます。


## <a name="before-you-start"></a>アップグレードを開始する前に

- これらのアプリを展開するデバイスは、macOS 10.10 またはそれ以降を実行されている必要があります。
- Intune は、Mac のスイートの Office 2016 に含まれている追加の Office アプリのみをサポートします。
- Intune アプリ suite のインストール時に Office のすべてのアプリを開くと、エンドユーザーは、保存されていないファイルからデータを失う可能性があります。


## <a name="get-started"></a>作業開始
Office 365 を使用して追加、**アプリ**ブレードです。
1.  Azure ポータルにサインインします。
2.  **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3.  **[Intune]** ブレードで、**[モバイル アプリ]** を選択します。
4.  **モバイル アプリ**ワークロード、選択**アプリ**で、**管理**グループ。 **[追加]** を選びます。
5.  **アプリの追加**ブレードで、選択**Office 365** > **macOS**です。
6.  **[追加]** を選択します。

## <a name="configure-the-app-suite"></a>アプリ スイートの構成

アプリのスイートに関する情報を提供します。 この情報は、アプリ スイートを Intune で識別したり、ユーザーが会社のポータル サイト アプリで探したりする場合に役立ちます。

1.  **[アプリの追加]** ブレードで、**[アプリ スイートの情報]** を選択します。
2.  次の情報を指定します。
    - **[スイート名]** - 会社のポータルに表示される、アプリ スイートの名前を入力します。 使用するスイート名はすべて一意にします。 同じアプリ スイート名が 2 つ存在する場合、会社のポータルではそのアプリのいずれかのみがユーザーに表示されます。
    - **[スイートの説明]** - アプリ スイートの説明を入力します。
    - **パブリッシャー** -パブリッシャーとしてマイクロソフトが表示されます。
    - **[カテゴリ]** - 必要に応じて、1 つ以上の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 この操作を行うと、会社のポータルを閲覧するときに、ユーザーがアプリ スイートを探しやすくなります。
    - **これは会社のポータルでおすすめアプリとして表示**-これは、アプリのスイート目立つように表示、会社のポータルのメイン ページで、ユーザーがアプリを参照するとき。
    - **[情報 URL]** - 必要に応じて、このアプリに関する情報が含まれる Web サイトの URL を入力します。 この URL は会社のポータルでユーザーに表示されます。
    - **[プライバシー URL]** - 必要に応じて、このアプリのプライバシー情報が含まれる Web サイトの URL を入力します。 この URL は会社のポータルでユーザーに表示されます。
    - **開発者**-開発者として、Microsoft が表示されます。
    - **所有者**-所有者として Microsoft が表示されます。
    - **[メモ]** - このアプリに関連付けるメモを入力します。
    - **[アイコンのアップロード]** - ユーザーが会社のポータルを参照するときに、アプリに表示されるアイコンをアップロードします。
3.  **[OK]** を選択します。 1 つのエントリとして、アプリの一覧で、スイートが表示されます。

## <a name="configure-app-assignments"></a>アプリの割り当てを構成します。

この手順では、アプリのスイートの割り当てを構成します。 使用可能なアプリの種類は近日に注意してください。

1.  アプリの一覧でアプリのスイートを選択し、選択**割り当て**です。
2.  選択**グループを選択して**です。
3.  スイートを選択したグループに割り当てます。 詳細については、「[How to assign apps to groups with Microsoft Intune (Microsoft Intune を使ってアプリをグループに割り当てる方法)](/intune/apps-deploy)」を参照してください。
4.  各グループを選択する**インストールが必要**です。
        >[!Note]
        > You cannot uninstall Office 365 through Intune.

5. 選択**保存**の割り当てをコミットします。

## <a name="next-steps"></a>次のステップ

Windows 10 デバイスに Office 365 アプリを追加する方法については、次を参照してください。 [Office 365 ProPlus 2016 アプリを Microsoft Intune で Windows 10 デバイスに割り当てる方法](/intune/apps-add-office365)です。
