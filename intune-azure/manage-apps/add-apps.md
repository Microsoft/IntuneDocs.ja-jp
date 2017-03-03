---
title: "アプリを Microsoft Intune に追加する方法 | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: この手順では、Intune にアプリを追加して、ユーザーとデバイスに割り当てる準備を行います。 "
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 472e65be196d1090e89b46271bb97a82b6fb1a9c
ms.lasthandoff: 02/16/2017

---

# <a name="how-to-add-an-app-to-microsoft-intune"></a>アプリを Microsoft Intune に追加する方法

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

ユーザー用アプリを管理して割り当てるには、そのアプリを Intune に追加する必要があります。 Intune ではさまざまな種類のアプリがサポートされ、オプションは種類ごとに異なる可能性があります。

Intune で追加と割り当てがサポートされるアプリの種類を次に示します。

![Intune でサポートされているアプリの種類](./media/app-types.png)

次のプラットフォームがサポートされます。 各種のアプリを追加する方法の詳細については、次のいずれかのトピックをクリックします。

- [Android の基幹業務アプリ](/intune-azure/manage-apps/android-lob-app)
- [Android ストア アプリ](/intune-azure/manage-apps/android-store-app)
- [iOS の基幹業務アプリ](/intune-azure/manage-apps/ios-lob-app)
- [iOS ストア アプリ](/intune-azure/manage-apps/ios-store-app)
- [Web アプリ (すべてのプラットフォーム)](/intune-azure/manage-apps/web-app)
- [Windows Phone 8.1 ストア アプリ](/intune-azure/manage-apps/windows-phone-8-1-store-app)
- [Windows ストア アプリ](/intune-azure/manage-apps/windows-store-app)

> [!NOTE]
> ストアからアプリを追加し、展開するとき、エンド ユーザーがそのアプリをインストールするには、そのストアのアカウントをエンド ユーザーが用意する必要があります。

## <a name="cloud-storage-space"></a>クラウドの記憶域の容量
ソフトウェア インストーラーのインストールの種類を使用して作成したすべてのアプリ (たとえば、基幹業務アプリ) は、パッケージ化され、Microsoft Intune クラウドの記憶域にアップロードされます。 Intune の試用版サブスクリプションでは、管理対象のアプリと更新プログラムの保管用として、2 ギガバイト (GB) 分のクラウドの記憶域を使用できます。 完全版のサブスクリプションには、20 GB のストレージ領域が含まれています。

Intune の追加ストレージは、当初の購入方法を使用して購入できます。  請求書やクレジット カードでお支払いの場合は、[サブスクリプション管理ポータル](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions)をご覧ください。  それ以外の場合は、パートナーまたは営業担当者にお問い合わせください。

クラウドの記憶域の容量の要件は次のとおりです。

-   すべてのアプリのインストール ファイルは、同じフォルダーにある必要がある。
-   アップロードするファイルの最大ファイルサイズは 2 GB。

## <a name="how-to-create-and-edit-categories-for-apps"></a>アプリのカテゴリを作成して編集する方法 

エンド ユーザーが会社のポータルでアプリを見つけやすいように、そのアプリはカテゴリを使って並べ替えることができます。 アプリには、**デベロッパー アプリ**、**通信アプリ**など、1 つ以上のカテゴリを割り当てることができます。 アプリを Intune に追加するときに、必要なカテゴリを選択するためのオプションが表示されます。 プラットフォーム固有のトピックを使用してアプリを追加し、カテゴリを割り当てます。 独自のカテゴリを作成して編集するには、次の手順を実行します。 

1. Azure ポータルにサインインします。 
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。 
3. **[Intune]** ブレードで、**[アプリの管理]** を選択します。 
4. **[モバイル アプリ]** ワークロードで、**[セットアップ]** > **[アプリのカテゴリ]** の順に選択します。 
5. **[アプリのカテゴリ]** ブレードで、現在のカテゴリの一覧が表示されます。 次の操作のいずれかを選択します。 
    - **[カテゴリの作成]** - **[Create category (カテゴリの作成)]** ブレードで、新しいカテゴリの名前を入力します。 名前を入力できる言語は&1; つのみです。Intune では翻訳されません。 完了したら [**作成**] をクリックします。
    - **[カテゴリの編集]** - 一覧の任意のカテゴリについては、"**...**" を選択します。 **[プロパティ]** ブレードで、カテゴリの新しい名前を入力するか、カテゴリを削除できます。




