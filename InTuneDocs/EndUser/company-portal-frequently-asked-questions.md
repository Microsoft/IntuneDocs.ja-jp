---
title: "ポータル サイトの概要 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9ddbcde20fac83289c4622f69538ff00fa0cb65b
ms.openlocfilehash: adf7fc0b7ddeb7fa8361d37efd0fdd5c714a72e4


---

# <a name="about-the-company-portal"></a>ポータル サイトの概要

## <a name="what-is-the-company-portal-and-what-can-you-do-with-it"></a>ポータル サイトの概要とサイトで実行できる操作
Microsoft Intune ポータル サイトでは、会社や学校のデータとアプリにアクセスできます。 ポータル サイトは 2 通りの方法で入手できます。

- ポータル サイト アプリをデバイスにインストールします。 一般的に、ポータル サイト アプリはお使いのデバイスのアプリ ストアで入手しますが、IT 管理者がポータル サイト アプリを代理でインストールすることもできます。
- IT 管理者が設定した[ポータル サイト Web サイト](http://portal.manage.microsoft.com)にアクセスします。

ポータル サイトとポータル サイト Web サイトには微妙な違いがいくつかありますが、ほとんどのタスクは同じように実行できます。 主に次のタスクを実行できます。

- デバイスの登録
- デバイスの状態の確認
- 会社や学校が用意したアプリのダウンロード
- デバイスの名前の変更
- PIN またはパスワードの設定
- IT 部門に連絡し、サポートを求める

次のリンクで、ポータル サイトとポータル サイト Web サイトで可能な操作を比較できます。

> [!div class="op_single_selector"]
- [Android](using-your-android-device-with-intune.md)
- [iOS および Mac OS X](using-your-ios-or-mac-os-x-device-with-intune.md)
- [Windows](using-your-windows-device-with-intune.md)
- [ポータル Web サイト](using-the-intune-company-portal-website.md)

## <a name="what-happens-when-you-add-a-computer-or-device-to-the-company-portal"></a>コンピューターやデバイスをポータル サイトに追加すると、どうなりますか。
コンピューターやデバイスをポータル サイトに追加すると、なんらかのソフトウェアがインストールされるか、アプリがダウンロードされる場合があります (デバイスによって異なります)。  また、使用しているデバイスの管理を IT 管理者に許可することで、デバイスに保存されている会社情報を保護しやすくすることもできます。

お使いのデバイスで IT 管理者に表示される情報と表示されない情報については、お使いのデバイスのリンクを参照してください。

> [!div class="op_single_selector"]
- [Android](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-android.md)
- [iOS および Mac OS X](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md)
- [Windows](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)

## <a name="what-kind-of-computers-or-devices-can-you-add-to-the-company-portal"></a>ポータル サイトにはどのような種類のコンピューターまたはデバイスを追加できますか。

-   iPhone、iPad、Mac OS X デバイス

-   Android モバイル デバイス

-   Windows デバイス
    -   [Windows] 10 Mobile
    -   [Windows] 10 Desktop
    -   Windows Phone 8。1
    -   Windows 8.1

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>ポータル サイトからコンピューターまたはデバイスを削除できますか。
ポータル サイトのコンピューターまたはデバイスは、削除またはリセットできます。 **削除**と**リセット**には違いがあります。

コンピューターまたはデバイスを*削除*すると、デバイスの登録が Intune で解除されます。 登録が解除されると、そのデバイスからポータル サイトにはアクセスできなくなります。また、一部の会社データがデバイスから削除される場合があります。 ポータル サイトからデバイスを削除する方法については、次のいずれかのリンクを参照してください。

> [!div class="op_single_selector"]
- [Android](unenroll-your-device-from-intune-android.md)
- [iOS および Mac OS X](unenroll-your-device-from-intune-ios.md)
- [Windows](unenroll-your-device-from-intune-windows.md)

コンピューターまたはデバイスを*リセット*すると、ポータル サイトは、コンピューターまたはデバイスを製造元の既定の設定にリセットしようとします。 デバイスをリセットすると、デバイスから会社データと個人データがすべて削除されます。 デバイスを紛失した場合、ポータル サイト Web サイトからリモート リセットできます。

デバイスをリセットする方法については、次のいずれかのリンクを参照してください。

> [!div class="op_single_selector"]
- [Android](reset-erase-your-lost-or-stolen-device-android.md)
- [iOS および Mac OS X](reset-erase-your-lost-or-stolen-device-ios.md)
- [Windows](reset-erase-your-lost-or-stolen-device-windows.md)
- [ポータル Web サイトからデバイスをリセットする](reset-your-device-cpwebsite.md)

## <a name="you-do-not-see-all-of-your-devices-in-the-company-portal"></a>ポータル サイトに表示されないデバイスがあります。
デバイスを表示するには、ポータル サイトに追加する必要があります。 管理者に指定されたポータル サイトを開き、手順に従ってデバイスを追加してください。 会社が所有および管理しているデバイスは表示されません。

## <a name="if-you-have-questions-contact-your-it-administrator"></a>ご質問がございましたら、IT 管理者に問い合わせてください。
サポートが必要な場合は、IT 管理者に問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。



<!--HONumber=Nov16_HO1-->


