---
title: iOS デバイス用のアプリ通知を作成する - Microsoft Intune - Azure | Microsoft Docs
description: Microsoft Intune で iOS デバイス用のアプリ通知を追加または作成します。 通知を送信するアプリの選択し、ロック画面での通知設定の構成、サウンドの有効化、アラートの種類の選択、バッジの追加を行います。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 43068163c15c0588a8a6ef745d5b191f4547a94d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="configure-app-notifications-settings-on-ios-devices-in-intune"></a>Intune で iOS デバイスでのアプリ通知設定を構成する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

iOS デバイスにインストールされているアプリが通知を送信する方法を構成します。 これらの設定は、iOS 9.3 以降を実行している監視対象のデバイスをサポートします。

## <a name="add-the-app-notification"></a>アプリ通知を追加する

1. [Azure Portal](https://portal.azure.com) にサインインします。
2. iOS または macOS プロファイル内で、**[デバイス機能]** を選択します。 プロファイルの作成手順については、[iOS または macOS のデバイス機能](device-features-configure.md)に関するページをご覧ください。
3. **[アプリの通知 (監視のみ)]** を選択し、**[追加]** を選択します。![Intune で iOS または macOS のプロファイルにアプリ通知を追加する](./media/ios-macos-app-notifications.png)
4. 次のプロパティを入力します。

   - **[アプリ バンドル ID]**: 構成するアプリの**アプリ バンドル ID** を入力します。 詳しくは、このトピックの「**組み込み iOS アプリのバンドル ID リファレンス**」をご覧ください。
   - **[アプリ名]**: 構成するアプリの名前を入力します。 この名前はデバイスでは表示されず、一覧のアプリを識別するために使われます。
   - **[発行元]**: 構成するアプリの発行元を入力します。 発行元はデバイスでは表示されず、一覧のアプリを識別するためにのみ使われます。
   - **[通知]**: アプリがデバイスに通知を送信するのを有効または無効にします。 この設定を無効にすると、次の設定も無効になります。
     - **[通知センターに表示する]** - この設定を有効にすると、アプリがデバイスの通知センターに通知を表示することを許可します。
     - **[ロック画面に表示する]** - この設定を有効にすると、アプリからの通知がデバイスのロック画面に表示されます。
     - **[アラートの種類]** - デバイスのロックが解除されたときの通知の種類を、次から選びます。
       - **[なし]** - 通知は表示されません。
       - **[バナー]** - 通知を示すバナーが短時間表示されます。
       - **[モーダル]** - 通知が表示され、ユーザーはデバイスの使用を続ける前に、手動でこの通知を消す必要があります。
     - **[アプリ アイコンのバッジ]** - この設定を有効にすると、アプリが通知を送信したことを示すバッジがアプリ アイコンに追加されます。
     - **[サウンド]** - この設定を有効にすると、通知の配信時にサウンドを再生します。

5. 必要な数のアプリを追加します。 アプリを追加したら、**[OK]** を選択します。
6. **[作成]** を選択してプロファイルを保存します。

## <a name="bundle-id-reference-for-built-in-ios-apps"></a>組み込み iOS アプリのバンドル ID リファレンス

以下の一覧は、一般的な組み込み iOS アプリのバンドル ID を示しています。 他のアプリのバンドル ID を調べるには、ソフトウェア ベンダーにお問い合わせください。

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

## <a name="next-steps"></a>次の手順

選択したグループにデバイス プロファイルを割り当てます。 手順については、[Intune でデバイス プロファイルを割り当てる方法](device-profile-assign.md)に関するページをご覧ください。