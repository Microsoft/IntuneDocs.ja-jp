---
title: 電力の最適化が電子メール アクセスを妨げる |Microsoft ドキュメント
description: Android で電子メールを受け取るために電力の最適化をオフにする方法について説明します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ad713f18-40a9-421f-aa2b-f8c21028d57c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 98b8d4636b3f402b2b7246311e8027722fa01953
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838114"
---
# <a name="outlook-wont-sync-managed-email-when-battery-optimization-for-android-is-turned-on"></a>Android のバッテリー最適化が有効になっていると Outlook が管理対象電子メールを同期しない

> [!IMPORTANT]
> ユーザーからの報告件数が増えているため、この問題についてここで説明します。 ここで説明する手順を実行してもこの問題が発生する場合は、[会社のサポート](https://go.microsoft.com/fwlink/?linkid=2010980)にさらに支援を依頼してください。

Intune にデバイスを登録すると、会社のリソースにアクセスできるようになります。 最も一般的なリソースの 1 つはメール アクセスです。 Android デバイス用 Outlook によるメール アクセスでの問題は、バッテリー最適化を有効にすると発生します。 デバイスのバッテリーをできるだけ長く持たせるため、バッテリー最適化が自動的に有効になる場合があります。 バッテリー最適化は、メールの自動ダウンロードの停止を試みるため、バッテリーの維持に部分的には効果があります。

Microsoft Intune チームはこの問題の解決に取り組んでいます。 デバイスが省電力モードになるのを防ぐ方法の 1 つは、バッテリーの残量を 30% より高く維持することです。 省電力モードになったときに問題が発生しないようにするには、バッテリーの最適化と省電力設定の影響を受けるアプリの一覧からポータル サイトと Outlook を削除する必要があります。

多くの製造元によって多くの Android デバイスが製造されています。 すべてのデバイスについて、必要な手順を正確に記すことはできません。 この操作は、システム設定だけで済むことも、特定の製造元に固有の設定も必要な場合もあります。 Android デバイスでこの問題を解決できる方法の一般的な例をいくつか示します。

## <a name="unmodified-android-devices"></a>変更されていない Android デバイス

多くの製造元は、Android デバイスに変更を加えています。 これにより、テーマや通知など、デバイスと対話する特定の方法が変更される場合があります。 Google は、通常、この種の変更を携帯電話に対して行うことはありません。 たとえば、Android 7.0 以降を搭載した Google Pixel デバイスでは、以下の手順でバッテリー最適化からこれらのアプリを削除します。

1. **[設定]** を開きます。
2. **[Battery\(バッテリー\)]** > **[More\(詳細\)]** > **[Battery optimization\(バッテリーの最適化\)]** の順にタップします。
3. 下向きの矢印をタップし、**[Not optimized\(最適化しない\)]** をタップします。
4. ポータル サイト アプリと Outlook アプリを選び、バッテリーの最適化をオフにします。

## <a name="samsung-devices"></a>Samsung デバイス

Android 7.0 以降を搭載した Samsung デバイスなどの他のタイプの Android デバイスでは、Outlook アプリとポータル サイト アプリをバッテリー最適化から削除する手順が異なる場合があります。

1. **[設定]** を開きます。
2. **[Menu (…)\(メニュー (...)\)]** > **[Special access\(特殊なアクセス\)]** > **[Optimize battery usage\(バッテリー使用の最適化\)]** の順にタップします。
3. ドロップダウンから **[All apps\(すべてのアプリ\)]** を選びます。
4. ポータル サイト アプリと Outlook アプリの隣のトグルを **[オフ]** にして、バッテリーの最適化をオフにします。

さらに、古いバージョンの Android を搭載した Samsung デバイスを使っている場合は、以下の手順で省電力モードからこれらのアプリを削除する必要があります。

1. **[設定]** を開きます。
2. **[Device maintenance\(デバイスの保守\)]** > **[Battery\(バッテリー\)]** > **[Unmonitored apps\(監視しないアプリ\)]** の順にタップします。
3. **[Add apps\(アプリの追加\)]** をタップします。
4. ポータル サイト アプリと Outlook アプリを選び、**[Done\(完了\)]** をタップします。

## <a name="oneplus-devices"></a>OnePlus デバイス

これらの設定を探す方法のもう 1 つの例は、システム設定を検索することです。 たとえば、Android 7.1.1 を搭載した OnePlus 3 では次のようにします。 

1. **[System Settings\(システム設定\)]** を開きます。 
2. **[検索]** ボタンをタップします。 画面の右上にある虫眼鏡のようなボタンです。 
3. 検索に「**battery optimization\(バッテリーの最適化\)**」と入力し、表示される **[設定]** 画面で **[Battery Optimization\(バッテリーの最適化\)]** オプションを選びます。 
4. **[Battery\(バッテリー\)]** > **[Battery optimization\(バッテリーの最適化\)]** の順にタップします。
5. ポータル サイト アプリと Outlook アプリを選び、**[Don't optimize\(最適化しない\)]** を選びます。 **[完了]** をタップします。

<!--On a OnePlus 5 device with Android 7.1.1, you would follow these steps to remove these apps from battery optimization:
1. Open **Settings**.
2. Tap **Battery** > **Battery optimization**.
3. Select the Company Portal and Outlook apps, then select **Don’t optimize**. Tap **Done**.-->

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。
