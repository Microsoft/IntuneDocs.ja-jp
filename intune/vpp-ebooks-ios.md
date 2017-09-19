---
title: "ボリューム購入した iOS 電子ブックの管理"
titlesuffix: Azure portal
description: "iOS ストアからボリューム購入したブックを Intune に同期し、その使用状況を管理および追跡する方法について説明します。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 08/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5617074-2384-4812-b913-dc94f64c0818
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 16f1e720e94ac8c6b35158477b41bfaeac9dc0a8
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-manage-ios-ebooks-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Volume Purchase Program で購入した iOS 電子ブックを Microsoft Intune で管理する方法


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Apple Volume Purchase Program (VPP) では、社内のユーザーに配布するブックの複数ライセンスを購入できます。 ブックは Business Store または Education Store から配布できます。

Microsoft Intune では、このプログラムを通して購入したブックを同期および管理し、割り当てることができます。 ストアからライセンス情報をインポートし、使用したライセンスの数を追跡できます。

ブックを管理する手順は、[VPP アプリを管理する](vpp-apps-ios.md)手順とほぼ同様です。

## <a name="manage-volume-purchased-books-for-ios-devices"></a>iOS デバイス用のボリューム購入ブックの管理
iOS ブックの複数のライセンスを購入するには、[ビジネス向け Apple Volume Purchase Program](http://www.apple.com/business/vpp/) または [教育向け Apple Volume Purchase Program](http://volume.itunes.apple.com/us/store) を利用します。 このためには、Apple Web サイトから Apple VPP アカウントをセットアップし、Apple VPP トークンを Intune にアップロードする必要があります。  その後、ボリューム購入情報を Intune に同期し、ボリューム購入ブックの使用状況を追跡することができます。

## <a name="before-you-start"></a>アップグレードを開始する前に
開始する前に、Apple から VPP トークンを取得し、これを Intune アカウントにアップロードします。 補足:

* Intune アカウントに関連付けられる VPP トークンは、最大 256 個です。
* 以前に異なる製品で VPP トークンを使用していた場合は、Intune で使用するための新しい VPP トークンを生成する必要があります。
* 各トークンは、1 年間有効です。
* 既定では、Intune は 1 日に 2 回、Apple VPP サービスと同期します。 いつでも手動での同期を開始できます。
* Intune に VPP トークンをインポートした後、同じトークンを他のデバイス管理ソリューションにインポートすることはできません。 これを行うと、ライセンスの割り当てとユーザー レコードが失われる恐れがあります。
* Intune で iOS ブックの使用を開始する前に、他のモバイル デバイス管理 (MDM) ベンダーで作成された既存の VPP ユーザー アカウントを削除してください。 Intune では、セキュリティ対策として、そのようなユーザー アカウントは Intune と同期されません。 Intune では、Intune で作成された Apple VPP サービスからのデータのみが同期されます。
* デバイスに本を割り当てる場合、そのデバイスには、組み込みの iBooks アプリがインストールされている必要があります。 そうでない場合は、エンド ユーザーがブックを読むには、アプリを再インストールする必要があります。 現時点では、Intune を使用して、削除された組み込みのアプリを復元することはできません。
* Apple Volume Purchase Program サイトから実行できるのは、ブックの割り当てのみです。 社内で作成したブックをアップロードしてから割り当てることはできません。
* 現時点では、アプリと同じようにブックをエンド ユーザー カテゴリに割り当てることはできません。
* 一度ブックを割り当てると、その後ライセンスを再利用することはできません。
* 対象となるデバイスを持つユーザーが初めて VPP ブックをインストールしようとすると、ブックをインストールする前に Apple Volume Purchase Program に参加する必要があります。 管理対象の Apple ID を使用して、セキュリティ グループにライセンスを割り当てることもできます。 このようにする場合、ユーザーはブックをインストールする際に Apple ID を求められることはありません。

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Apple VPP トークンを取得およびアップロードするには

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[モバイル アプリ]** を選択します。
1.  **[Mobile Apps]** ワークロードで、**[セットアップ]** > **[iOS VPP トークン]** の順に選択します。
2.  VPP トークンの一覧ブレードで、**[追加]** をクリックします。
3.  **[新しい VPP トークン]** ブレードで、次の情報を指定します。
    - **[VPP トークン ファイル]** - Volume Purchase Program for Business または Volume Purchase Program for Education にサインインしていることを確認します。 次に、アカウントの Apple VPP トークンをダウンロードし、ここでそのトークンを選択します。
    - **[Apple ID]** - Volume Purchase Program に関連付けられているアカウントの Apple ID を入力します。
    - **[VPP アカウントの種類]** - **[ビジネス]** または **[教育]** を選択します。
4. 終了したら、**[保存]** をクリックします。

トークンがトークンの一覧ブレードに表示されます。


**[今すぐ同期]** を選択すると、いつでも、Apple が保持しているデータと Intune を同期することができます。

## <a name="to-assign-a-volume-purchased-app"></a>ボリューム購入アプリを割り当てるには

1. **[電子ブック]** ワークロードで、**[管理]** > **[すべての電子ブック]** を選択します。
2. ブックの一覧ブレードで、割り当てるブックを選択し、**[...]**、**[グループの割り当て]** の順に選択します。
3. **[<*ブック名*> - 割り当てられたグループ]** ブレードで、**[管理]** > **[割り当てられたグループ]** の順に選択します。
4. **[グループの割り当て]** を選択し、**[グループの選択]** ブレードで、ブックを割り当てる Azure AD ユーザー グループを選択します。 現時点では、デバイス グループはサポートされていません。
割り当て操作として **[利用可能]** または **[必須]** を選択します。 
5. 完了したら、**[保存]** を選択します。

## <a name="next-steps"></a>次のステップ

ブックの割り当てを監視するのに役立つ情報については、[アプリを監視する方法](apps-monitor.md)に関する記事をご覧ください。






