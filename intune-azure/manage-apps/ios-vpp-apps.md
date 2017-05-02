---
title: "iOS のボリューム購入アプリの管理"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: iOS ストアからボリューム購入したアプリを Intune に同期し、その使用状況を管理および追跡する方法について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: a981b0253f56d66292ce77639faf4beba8832a9e
ms.openlocfilehash: 1c13d39b8b193c56439602a6e9d9a34e547aef81
ms.lasthandoff: 04/19/2017

---

# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

iOS アプリ ストアでは、社内で実行するアプリの複数のライセンスを購入できます。 これは、購入したアプリの複数コピーを追跡する管理オーバーヘッドを削減するのに役立ちます。

Microsoft Intune では、このプログラムを通じて購入したアプリを管理するために、アプリ ストアからライセンス情報をインポートし、使用したライセンスの数を追跡し、所有しているより多くのアプリをインストールできないようにします。

さらに、Apple ボリューム購入プログラム ストアから購入した本と Intune との間で同期、管理、割り当てを行い、これらをユーザーに割り当てることができます。 Intune ポータルで **ブック** ワークロードを使用して本を管理します。 ブックを管理するための手順は、アプリを管理する手順と同じです。
これを行うには、Apple Volume Purchase Program トークンをアップロードしている必要があります。 現時点では、ブックは**必須**インストールとしてのみ割り当てることができます。
デバイスに本を割り当てる場合、そのデバイスには、組み込みの iBooks アプリがインストールされている必要があります。 そうでない場合は、エンド ユーザーが本を読むためにアプリを再インストールする必要があります。 現時点では、Intune を使用して、削除された組み込みのアプリを復元することはできません。


## <a name="manage-volume-purchased-apps-for-ios-devices"></a>iOS デバイス用のボリューム購入アプリの管理
iOS アプリの複数のライセンスを購入するには、[ビジネス向け Apple Volume Purchase Program](http://www.apple.com/business/vpp/) または[教育向け Apple Volume Purchase Program](http://volume.itunes.apple.com/us/store) を利用します。 このためには、Apple Web サイトから Apple VPP アカウントをセットアップし、Apple VPP トークンの Intune へのアップロードを行います。  その後、ボリューム購入情報を Intune と同期し、ボリューム購入アプリの使用を追跡することができます。

## <a name="before-you-start"></a>アップグレードを開始する前に
開始する前に、Apple から VPP トークンを取得し、これを Intune アカウントにアップロードする必要があります。 さらに、次の点を理解する必要があります。

* Intune アカウントを使用して複数の Volume Purchase Program トークンを関連付けることができます。
* 以前に異なる製品で VPP トークンを使用していた場合は、Intune で使用するための新しい VPP トークンを生成する必要があります。
* 各トークンは、1 年間有効です。
* 既定では、Intune は 1 日に 2 回、Apple VPP サービスと同期します。 いつでも手動での同期を開始できます。
* Intune に VPP トークンをインポートした後、同じトークンを他のデバイス管理ソリューションにインポートすることはできません。 これを行うと、ライセンスの割り当てとユーザー レコードが失われる恐れがあります。
* Intune で iOS VPP の使用を開始する前に、他のモバイル デバイス管理 (MDM) ベンダーで作成された既存の VPP ユーザー アカウントを削除してください。 Intune は、セキュリティ対策として、そのようなユーザー アカウントを Intune と同期しません。 Intune は、Intune によって作成された Apple VPP サービスからのデータのみを同期します。

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Apple VPP トークンを取得およびアップロードするには

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[その他]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[アプリの管理]** を選択します。
1.  **[アプリの管理]** ワークロードで、**[セットアップ]** > **[iOS VPP トークン]** の順に選択します。
2.  VPP トークンの一覧ブレードで、**[追加]** をクリックします。
3.  [新しい VPP トークン] ブレードで、次の情報を指定します。
    - **[VPP トークン ファイル]** - サインアップしていない場合は、ビジネス向け Volume Purchase Program または教育向け Volume Purchase Program にサインアップします。 サインアップした後、アカウントの Apple VPP トークンをダウンロードし、ここで選択します。
    - **[Apple ID]** - Volume Purchase Program に関連付けられているアカウントの Apple ID を入力します。
    - **[VPP アカウントの種類]** - **[ビジネス]** または **[教育]** を選択します。
4. 終了したら、**[保存]** をクリックします。

トークンがトークンの一覧ブレードに表示されます。


**[今すぐ同期]** を選択すると、いつでも、Apple が保持しているデータと Intune を同期することができます。

## <a name="to-assign-a-volume-purchased-app"></a>ボリューム購入アプリを割り当てるには

1. **[アプリの管理]** ワークロードで、**[管理]** > **[ライセンスされたアプリ]** の順に選択します。
2. アプリの一覧ブレードで、割り当てるアプリを選択し、**[...]** > **[グループの割り当て]** の順に選択します。
3. **[<*アプリ名*> - 割り当てられたグループ]** ブレードで、**[管理]** > **[割り当てられたグループ]** の順に選択します。
4. **[グループの割り当て]** を選択し、**[グループの選択]** ブレードで、アプリを割り当てる Azure AD ユーザーまたはデバイス グループを選択します。
**[必須]** の割り当て操作を選択する必要があります。 デバイス グループへの割り当ては、2017 年 1 月以降に作成された新しいテナントでも使用できます。 テナントがそれより前に作成されており、VPP アプリをデバイス グループに割り当てることができない場合は、Intune のサポートに連絡してください。
5. 完了したら、**[保存]** を選択します。

アプリの割り当てを監視するのに役立つ情報については、[アプリを監視する方法](monitor-apps.md)に関する記事を参照してください。

## <a name="further-information"></a>詳細情報

アプリを **[必須]** インストールとして割り当てると、アプリをインストールする各ユーザーがライセンスを使用します。

ライセンスを再利用するには、割り当てアクションを **[アンインストール]** に変更する必要があります。 アプリをアンインストールすると、ライセンスは回収されます。

対象となるデバイスを持つユーザーが初めて VPP アプリをインストールしようとすると、Apple Volume Purchase Program に参加するように求められます。 アプリのインストールを実行する前に、このプログラムに参加する必要があります。

VPP アプリを利用可能として展開すると、アプリのコンテンツとライセンスは、アプリ ストアから直接展開されます。

