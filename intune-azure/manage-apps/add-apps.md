---
title: "アプリを Microsoft Intune に追加する方法"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: この手順では、Intune にアプリを追加して、ユーザーとデバイスに割り当てる準備を行います。 "
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: d85544bdfaa3a369e1d2d03e5454ff7aa2d75467
ms.lasthandoff: 04/19/2017

---

# <a name="how-to-add-an-app-to-microsoft-intune"></a>アプリを Microsoft Intune に追加する方法

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

ユーザー用アプリを管理して割り当てるには、そのアプリを Intune に追加する必要があります。 Intune ではさまざまな種類のアプリがサポートされ、オプションは種類ごとに異なる可能性があります。

Intune では、以下の種類のアプリを追加して割り当てることができます。

![Intune でサポートされているアプリの種類](./media/app-types.png)

次のプラットフォームがサポートされます。 各種のアプリを追加する方法の詳細については、次のいずれかのトピックをクリックします。

- [Android ストア アプリ](/intune-azure/manage-apps/android-store-app)
- [Android LOB アプリ](/intune-azure/manage-apps/android-lob-app)
- [iOS ストア アプリ](/intune-azure/manage-apps/ios-store-app)
- [iOS LOB アプリ](/intune-azure/manage-apps/ios-lob-app)
- [Web アプリ (すべてのプラットフォーム)](/intune-azure/manage-apps/web-app)
- [Windows Phone 8.1 ストア アプリ](/intune-azure/manage-apps/windows-phone-8-1-store-app)
- [Windows ストア アプリ](/intune-azure/manage-apps/windows-store-app)

さらに、テナントを設定すると、Intune によって一部の Microsoft アプリは自動的に追加されます。 それらの一覧は、このトピックの後のほうで確認できます。

## <a name="before-you-start"></a>アップグレードを開始する前に

アプリの追加と割り当てを始める前に、次の点を検討してください。

- ストアからアプリを追加し、展開するとき、エンド ユーザーがそのアプリをインストールするには、そのストアのアカウントをエンド ユーザーが用意する必要があります。
- 展開するアプリまたは項目が、組み込みの iOS アプリに依存する場合があります。 たとえば、iOS ストアからブックを展開する場合は、デバイス上に iBooks アプリが存在する必要があります。 iBooks の組み込みアプリを削除した場合は、Intune を使用してそれを元に戻すことはできません。

## <a name="cloud-storage-space"></a>クラウドの記憶域の容量
ソフトウェア インストーラーのインストールの種類を使用して作成したすべてのアプリ (たとえば、基幹業務アプリ) は、パッケージ化され、Microsoft Intune クラウドの記憶域にアップロードされます。 Intune の試用版サブスクリプションでは、管理対象のアプリと更新プログラムの保管用として、2 ギガバイト (GB) 分のクラウドの記憶域を使用できます。 完全版のサブスクリプションには、20 GB のストレージ領域が含まれています。

Intune の追加ストレージは、当初の購入方法を使用して購入できます。  請求書やクレジット カードでお支払いの場合は、[サブスクリプション管理ポータル](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions)をご覧ください。  それ以外の場合は、パートナーまたは営業担当者にお問い合わせください。

クラウドの記憶域の容量の要件は次のとおりです。

-   すべてのアプリのインストール ファイルは、同じフォルダーにある必要がある。
-   アップロードするファイルの最大ファイルサイズは 2 GB。

## <a name="how-to-create-and-edit-categories-for-apps"></a>アプリのカテゴリを作成して編集する方法

エンド ユーザーが会社のポータルでアプリを見つけやすいように、そのアプリはカテゴリを使って並べ替えることができます。 アプリには、**デベロッパー アプリ**、**通信アプリ**など、1 つ以上のカテゴリを割り当てることができます。
アプリを Intune に追加するときに、必要なカテゴリを選択するためのオプションが表示されます。 プラットフォーム固有のトピックを使用してアプリを追加し、カテゴリを割り当てます。 独自のカテゴリを作成して編集するには、次の手順を実行します。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[アプリの管理]** を選択します。
4. **[モバイル アプリ]** ワークロードで、**[セットアップ]** > **[アプリのカテゴリ]** の順に選択します。
5. **[アプリのカテゴリ]** ブレードで、現在のカテゴリの一覧が表示されます。 次の操作のいずれかを選択します。
    - **[カテゴリの作成]** - **[Create category (カテゴリの作成)]** ブレードで、新しいカテゴリの名前を入力します。 名前を入力できる言語は 1 つのみです。Intune では翻訳されません。 完了したら [**作成**] をクリックします。
    - **[カテゴリの編集]** - 一覧の任意のカテゴリについては、"**...**" を選択します。 **[プロパティ]** ブレードで、カテゴリの新しい名前を入力するか、カテゴリを削除できます。


## <a name="apps-added-automatically-by-intune"></a>Intune によって自動的に追加されるアプリ

マイクロソフトによって発行された次のアプリは、Intune に組み込まれており、割り当てられる状態になっています。

|||
|-|-|
|名前|プラットフォーム|アプリの種類|
|Azure Information Protection|Android|管理対象の Android ストア アプリ|
|携帯端末用 Dynamics CRM|Android|管理対象の Android ストア アプリ|
|タブレット PC 用 Dynamics CRM|Android|管理対象の Android ストア アプリ|
|Excel|iOS|管理対象の iOS ストア アプリ|
|Excel|Android|管理対象の Android ストア アプリ|
|Managed Browser|Android|管理対象の Android ストア アプリ|
|Managed Browser|iOS|管理対象の iOS ストア アプリ|
|携帯端末の Microsoft Dynamics CRM|iOS|管理対象の iOS ストア アプリ|
|タブレット PC の Microsoft Dynamics CRM|iOS|管理対象の iOS ストア アプリ|
|Microsoft Power BI|iOS|管理対象の iOS ストア アプリ|
|Microsoft Power BI|Android|管理対象の Android ストア アプリ|
|Microsoft SharePoint|iOS|管理対象の iOS ストア アプリ|
|Microsoft SharePoint|Android|管理対象の Android ストア アプリ|
|Microsoft Teams|Android|管理対象の Android ストア アプリ|
|Microsoft Teams|iOS|管理対象の iOS ストア アプリ|
|OneDrive|iOS|管理対象の iOS ストア アプリ|
|OneDrive|Android|管理対象の Android ストア アプリ|
|OneNote|iOS|管理対象の iOS ストア アプリ|
|Outlook|Android|管理対象の Android ストア アプリ|
|Outlook|iOS|管理対象の iOS ストア アプリ|
|Outlook グループ|Android|管理対象の Android ストア アプリ|
|Outlook グループ|iOS|管理対象の iOS ストア アプリ|
|PowerPoint|iOS|管理対象の iOS ストア アプリ|

