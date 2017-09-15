---
title: "アプリを Microsoft Intune に追加する方法"
titlesuffix: Azure portal
description: "この手順では、Intune にアプリを追加して、ユーザーとデバイスに割り当てられる状態にします。 \""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 108f789f16304498cf54387326d112353bf70aa2
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-add-an-app-to-microsoft-intune"></a>アプリを Microsoft Intune に追加する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

ユーザー用アプリを管理して割り当てるには、そのアプリを Intune に追加する必要があります。 Intune ではさまざまな種類のアプリがサポートされ、オプションは種類ごとに異なる可能性があります。

Intune では、以下の種類のアプリを追加して割り当てることができます。

![Intune でサポートされているアプリの種類](./media/app-types.png)

次のプラットフォームがサポートされます。

- Android ストア アプリ
- Android 基幹業務 (LOB) アプリ
- iOS ストア アプリ
- iOS 基幹業務 (LOB) アプリ
- Web アプリ
- Windows Phone 8.1 ストア アプリ
- Windows Phone 基幹業務アプリ (.xap ファイル)
- Windows ストア アプリ
- Windows 基幹業務アプリ (.msi ファイルのみ)

>[!TIP]
> 基幹業務 (LOB) アプリは、アプリ ストアからではなく、アプリのインストール ファイルからインストールするアプリです。 たとえば、iOS LOB アプリをインストールするには、アプリケーションのアーカイブ ファイル (拡張子 .ipa) を追加します。 これらは通常、社内で作成したアプリです。

## <a name="before-you-start"></a>アップグレードを開始する前に

アプリの追加と割り当てを始める前に、次の点を検討してください。

- ストアからアプリを追加して割り当てる場合、エンド ユーザーがそのアプリをインストールするには、そのストアのアカウントをエンド ユーザーが用意する必要があります。
- 割り当てるアプリまたは項目は、組み込みの iOS アプリに依存する場合があります。 たとえば、iOS ストアからブックを割り当てる場合は、デバイス上に iBooks アプリが存在する必要があります。 iBooks の組み込みアプリを削除した場合は、Intune を使用してそれを元に戻すことはできません。

## <a name="cloud-storage-space"></a>クラウドの記憶域の容量
ソフトウェア インストーラーのインストールの種類を使用して作成したすべてのアプリ (たとえば、基幹業務アプリ) は、パッケージ化され、Intune クラウドの記憶域にアップロードされます。 Intune の試用版サブスクリプションでは、管理対象のアプリと更新プログラムの保管用として、2 ギガバイト (GB) 分のクラウドの記憶域を使用できます。 完全版のサブスクリプションには、20 GB の記憶領域が含まれています。

Intune の追加ストレージは、当初の購入方法を使用して購入できます。  請求書やクレジット カードでお支払いの場合は、[サブスクリプション管理ポータル](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions)をご覧ください。  それ以外の場合は、パートナーまたは営業担当者にお問い合わせください。

クラウドの記憶域の容量の要件は次のとおりです。

-   すべてのアプリのインストール ファイルは、同じフォルダーにある必要がある。
-   アップロードするファイルの最大ファイルサイズは 2 GB。

## <a name="how-to-create-and-edit-categories-for-apps"></a>アプリのカテゴリを作成して編集する方法

ユーザーがポータル サイトでアプリを見つけやすいように、そのアプリをカテゴリを使って並べ替えることができます。 アプリには、**デベロッパー アプリ**、**通信アプリ**など、1 つ以上のカテゴリを割り当てることができます。
アプリを Intune に追加するときに、必要なカテゴリを選択するためのオプションが表示されます。 プラットフォーム固有のトピックを使用してアプリを追加し、カテゴリを割り当てます。 独自のカテゴリを作成して編集するには、次の手順を実行します。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[モバイル アプリ]** を選択します。
4. **[モバイル アプリ]** ワークロードで、**[セットアップ]** > **[アプリのカテゴリ]** の順に選択します。
5. **[アプリのカテゴリ]** ブレードで、現在のカテゴリの一覧が表示されます。 次の操作のいずれかを選択します。
    - **[カテゴリの作成]** - **[Create category (カテゴリの作成)]** ブレードで、新しいカテゴリの名前を入力します。 名前を入力できる言語は 1 つのみです。Intune では翻訳されません。 完了したら [**作成**] をクリックします。
    - **[カテゴリの編集]** - 一覧の任意のカテゴリについては、"**...**" を選択します。 **[プロパティ]** ブレードで、カテゴリの新しい名前を入力するか、カテゴリを削除できます。


## <a name="apps-added-automatically-by-intune"></a>Intune によって自動的に追加されるアプリ

以前は、Intune に簡単に割り当てができる組み込みのアプリが多数含まれていました。 お客様からのフィードバックに基づき、この一覧を削除しました。組み込みのアプリは今後表示されません。
ただし、組み込みのすべてのアプリが既に割り当てられている場合、そのアプリはアプリの一覧に引き続き表示されます。 これらのアプリの割り当ては必要に応じて続行することができます。
今後のリリースでは、Azure Portal から組み込みのアプリをより簡単に選択して割り当てる方法を追加する予定です。

## <a name="next-steps"></a>次のステップ

次のトピックのいずれかを選択して、各プラットフォーム用のアプリを Intune に追加する方法を確認してください。

- [Android ストア アプリ](store-apps-android.md)
- [Android LOB アプリ](lob-apps-android.md)
- [iOS ストア アプリ](store-apps-ios.md)
- [iOS LOB アプリ](lob-apps-ios.md)
- [Web アプリ (すべてのプラットフォーム)](web-app.md)
- [Windows Phone 8.1 ストア アプリ](store-apps-windows-phone-8-1.md)
- [Windows Phone LOB アプリ](lob-apps-windows-phone.md)
- [Windows ストア アプリ](store-apps-windows.md)
- [Windows LOB アプリ](lob-apps-windows.md)
- [Windows 10 用の Office 365 アプリ](apps-add-office365.md)

