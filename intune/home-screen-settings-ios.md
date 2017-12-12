---
title: "Intune を使用した iOS デバイス向けのホーム画面のレイアウト設定"
titlesuffix: Azure portal
description: "iOS デバイスのホーム画面と Dock のカスタマイズに使用できる設定について説明します。\""
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6aba4491-afb9-43cd-9ccc-14e6a2a5a3b1
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0dcc8f5509afa5308f8ae91a3d60ee081d5daa0b
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="intune-home-screen-layout-settings-for-ios-devices"></a>Intune を使用した iOS デバイス向けのホーム画面のレイアウト設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

これらの設定を使用すると、iOS の Dock とホーム画面で、アプリとフォルダーのレイアウトを構成できます。

プロファイルを割り当てる iOS デバイスは、監視モードで、iOS 9.3 以降を実行している必要があります。

1. **[デバイス機能]** ブレードで、**[ホーム画面レイアウト (監視モードのみ)]** を選択します。
2. **[ホーム画面レイアウト (監視モードのみ)]** ブレードで、**Dock** または**ページ**のどちらのレイアウトを構成するかを選択します。

## <a name="add-items-to-the-dock"></a>Dock にアイテムを追加する

**[Dock]** ブレードで、iOS 画面の Dock に最大 6 つのアイテムまたはフォルダーを追加できます。 ただし、多くのデバイスではサポートされるアイテム数は少なく、たとえば iPhone では最大で 4 つのアイテムがサポートされます。 この場合、構成した最初の 4 つのアイテムのみがデバイスに表示されます。

1. **[追加]** を選択してアイテムを Dock に追加します。
2. **[行の追加]** ブレードで、**アプリ**または**フォルダー**のどちらを追加するかを選択します。
3. このトピックの情報を使って、Dock に表示するアプリとフォルダーを構成します。
4. アイテムの追加を続けます。 完了したら、**[プロファイルの作成]** ブレードに戻るまで、各ブレードで **[OK]** をクリックします。 **[作成]** を選択します。

>[!TIP]
> ホーム画面とページの一覧でアイテムをドラッグ & ドロップして、順序を変更できます。 

### <a name="example"></a>例

この例では、Dock 画面に Safari、メール、および株価アプリのみが表示されるように構成しました。 次の画像では、メール アプリが選択され、そのプロパティが表示されています。

![iOS Dock 設定のサンプル](http://i.imgur.com/FfFiUcP.png)

iPhone にポリシーを割り当てると、結果は次のスクリーンショットのような Dock になります。

![iPhone の iOS Dock のレイアウト サンプル](http://i.imgur.com/bAgCe8F.png)

## <a name="add-home-screen-pages"></a>ホーム画面ページを追加する

ホーム画面に表示するページと、各ページに表示されるアプリを追加します。 ページに追加したアプリは、一覧で指定した順序で左から右に配置されます。 1 つのページに収まるよりも多くのアプリを追加すると、残りのアプリは次のページに移動します。


1. **[ページ]** ブレードで **[追加]** を選択します。
2. **[行の追加]** ブレードで、**ページ名**を入力します。 この名前は Azure Portal での参照用に使われ、iOS デバイスでは*表示されません*。
3. **[追加]** を選択し、ページに**アプリ**または**フォルダー**のどちらを追加するかを選択します。
4. このトピックの情報を使って、ページに表示するアプリとフォルダーを構成します。

### <a name="example"></a>例

この例では、**Contoso** という名前の新しいページを構成しています。 ページには、"友達を探す" と "設定" アプリのみが表示されます。 次の画像では、設定アプリが選択され、そのプロパティが表示されています。

![iOS ホーム画面の設定例](http://i.imgur.com/Jc2OxyX.png)

iPhone にポリシーを割り当てると、結果は次のスクリーンショットのようなページになります。

![ホーム画面が変更された iOS デバイス](http://i.imgur.com/Bd37PHa.png)

## <a name="how-to-add-an-app-to-the-list"></a>アプリを一覧に追加する方法

1. **[アプリ名]** を入力します。 この名前は Azure Portal での参照用に使われ、iOS デバイスでは*表示されません*。
2. 表示するアプリの **[アプリ バンドル ID]** を入力します。 詳細については、このトピックで後述する「**組み込み iOS アプリのバンドル ID リファレンス**」をご覧ください。
3. **[OK]** をクリックして、アイテムを引き続き追加します。デバイスの Dock には最大 **6** 個、デバイスのページには最大 **60** 個までアイテムを追加できます。
4. 操作が完了したら、 **[OK]**をクリックします。

## <a name="how-to-add-a-folder-to-the-list"></a>フォルダーを一覧に追加する方法

フォルダー内のページに追加したアプリは、一覧で指定した順序で左から右に配置されます。 1 つのページに収まるよりも多くのアプリを追加すると、残りのアプリは次のページに移動します。

1. **[フォルダー名]** を入力します。 この名前は、デバイスでユーザーに表示されます。
2. **[追加]** を選択してフォルダー内にページを作成します。 最大 20 ページまで追加できます。
3. **[行の追加]** ブレードで、ページの名前を入力します。 この名前は Azure Portal での参照用に使われ、iOS デバイスでは*表示されません*。
3. **[アプリ名]** を入力します。 この名前は Azure Portal での参照用に使われ、iOS デバイスでは*表示されません*。
2. 表示するアプリの **[アプリ バンドル ID]** を入力します。 詳細については、「**アプリを一覧に追加する方法**」をご覧ください。
3. **[追加]** を選びます。 最大 60 アイテムまで追加できます。
4. 操作が完了したら、 **[OK]**をクリックします。


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>組み込み iOS アプリのバンドル ID リファレンス

この一覧は、一般的な組み込み iOS アプリのバンドル ID を示しています。 他のアプリのバンドル ID を調べるには、ソフトウェア ベンダーにお問い合わせください。 

|||
|-|-|
|アプリ名|バンドル ID|
|アプリ ストア|com.apple.AppStore|
|計算機|com.apple.calculator|
|予定表|com.apple.mobilecal|
|カメラ|com.apple.camera|
|時計|com.apple.mobiletimer|
|コンパス|com.apple.compass|
|連絡先|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|友達を探す|com.apple.mobileme.fmf1|
|Find iPhone|com.apple.mobileme.fmip1|
|Game Center|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|正常性|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes Store|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|メール|com.apple.mobilemail|
|マップ|com.apple.Maps|
|メッセージ|com.apple.MobileSMS|
|ミュージック|com.apple.Music|
|News|com.apple.news|
|注|com.apple.mobilenotes|
|数字|com.apple.Numbers|
|ページ|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|写真|com.apple.mobileslideshow|
|Podcast|com.apple.podcasts|
|リマインダー|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|Settings|com.apple.Preferences|
|株価|com.apple.stocks|
|ヒント|com.apple.tips|
|ビデオ|com.apple.videos|
|VoiceMemos|com.apple.VoiceMemos|
|Wallet|com.apple.Passbook|
|視聴する|com.apple.Bridge|
|天気|com.apple.weather|


## <a name="next-steps"></a>次のステップ

選択したグループにデバイス プロファイルを割り当てることができます。 詳しくは、「[デバイス プロファイルを割り当てる方法](device-profile-assign.md)」をご覧ください。
