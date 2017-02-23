---
title: "管理デバイスを使用して作業する | Microsoft Docs"
description: "ポータル サイト アプリの詳細を確認します。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 68c7a23dc8769330c14f74e6aebb07eeb188a991
ms.openlocfilehash: 1ca19828902585bf6011713ab214619b7f8c12c5


---

# <a name="using-managed-devices-to-get-work-done"></a>管理デバイスを使用して作業する
Microsoft Intune は、組織がデバイス (スマートフォン、タブレット、PC など)、アプリ、その他の企業リソース (電子メールなど) を管理できるようにするソフトウェアです。 これを利用すると、企業の情報の安全性を確保しつつ、従業員が事実上どこからでも、ほぼすべてのデバイスで業務情報にアクセスできるようになります。

デバイスを Intune による管理対象として登録すると、IT 部門はそのような職場または学校のリソースを管理してより安全な状態に維持できるようになる一方で、従業員は自分好みのデバイスを使用して業務を進めることができるようになります。 主な登録方法は、ポータル サイトを通じてデバイスを管理対象として登録する方法です。

ポータル サイトは&2; 通りの方法で入手できます。

- ポータル サイト アプリをデバイスにインストールします。 一般的に、ポータル サイト アプリはお使いのデバイスのアプリ ストアに移動して入手しますが、IT 管理者が代わりにポータル サイト アプリをインストールすることもできます。
- IT 管理者が設定した[ポータル Web サイト](http://portal.manage.microsoft.com)にアクセスします。

## <a name="whats-the-difference-between-the-app-and-the-website"></a>アプリと Web サイトの違い
ポータル サイトとポータル サイト Web サイトには微妙な違いがいくつかありますが、ほとんどのタスクは同じように実行できます。 実行できるいくつかのタスクを以下に示します。

- デバイスを登録して管理する
- デバイスの状態の確認
- 組織に必要な推奨アプリをダウンロードする
- デバイスの名前の変更
- デバイスの PIN またはパスワードをリセットする
- IT 部門に連絡し、サポートを求める

次のリンクで、ポータル サイトとポータル サイト Web サイトで可能な操作を比較できます。

- [Android デバイスを使用する](using-your-android-device-with-intune.md)
- [iOS または macOS デバイスを使用する](using-your-ios-or-macOS-device-with-intune.md)
- [Windows デバイスを使用する](using-your-windows-device-with-intune.md)
- [ポータル Web サイトを使用する](using-the-intune-company-portal-website.md)

## <a name="what-happens-when-you-add-a-computer-or-device-to-the-company-portal"></a>コンピューターやデバイスをポータル サイトに追加すると、どうなりますか。
コンピューターやデバイスをポータル サイトに追加すると、なんらかのソフトウェアがインストールされるか、アプリがダウンロードされる場合があります (デバイスによって異なります)。 また、デバイスの管理を IT 管理者に許可することで、デバイス上の会社情報を保護しやすくすることもできます。

お使いのデバイスで IT 管理者が閲覧できる情報と閲覧できない情報については、お使いのデバイスの種類に該当するリンクを参照してください。

- [Android 用ポータル サイト アプリのインストール](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-android.md)
- [iOS および macOS 用ポータル サイト アプリのインストール](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md)
- [Windows 用ポータル サイト アプリのインストール](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)

## <a name="what-kind-of-computers-or-devices-can-you-add-to-the-company-portal"></a>ポータル サイトにはどのような種類のコンピューターまたはデバイスを追加できますか。
-   iOS (iPhone や iPad など) および macOS (MacBook や iMac など) を使用する Apple デバイス
-   Android デバイス
-   Windows デバイス
    -   [Windows] 10 Mobile
    -   [Windows] 10 Desktop
    -   Windows Phone 8。1
    -   Windows 8.1

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>ポータル サイトからコンピューターまたはデバイスを削除できますか。
ポータル サイトのコンピューターまたはデバイスは、削除またはリセットできます。 **削除**と**リセット**には違いがあります。

コンピューターまたはデバイスを*削除*すると、デバイスの登録が Intune で解除されます。 登録が解除されると、そのデバイスからポータル サイトにはアクセスできなくなります。また、一部の会社データがデバイスから削除される場合があります。 ポータル サイトからデバイスを削除する方法については、次のいずれかのリンクを参照してください。

- [Android デバイスの登録解除](unenroll-your-device-from-intune-android.md)
- [iOS または macOS デバイスの登録解除](unenroll-your-device-from-intune-ios.md)
- [Windows デバイスの登録解除](unenroll-your-device-from-intune-windows.md)

コンピューターまたはデバイスを*リセット*すると、ポータル サイトは、コンピューターまたはデバイスを製造元の既定の設定にリセットしようとします。 デバイスをリセットすると、デバイスから会社データと個人データがすべて削除されます。 デバイスを紛失した場合、ポータル サイト Web サイトからリモート リセットできます。

デバイスをリセットする方法については、次のいずれかのリンクを参照してください。

- [Android デバイスをリセット (消去) する](reset-erase-your-lost-or-stolen-device-android.md)
- [iOS または macOS デバイスをリセット (消去) する](reset-erase-your-lost-or-stolen-device-ios.md)
- [Windows デバイスをリセットする](reset-erase-your-lost-or-stolen-device-windows.md)
- [ポータル Web サイトからデバイスをリセットする](reset-your-device-cpwebsite.md)

## <a name="what-if-i-cant-see-my-device-in-the-company-portal"></a>ポータル サイトでデバイスを表示できない場合の対処方法
デバイスを表示するには、ポータル サイトに追加する必要があります。 管理者から推奨されたポータル サイトを開き、ご利用のデバイス向けの手順に従ってください。 会社が所有および管理しているデバイスは表示されません。

## <a name="if-you-have-questions-contact-your-it-admin"></a>疑問点については、IT 管理者に問い合わせてください。
サポートが必要な場合は、IT 管理者に問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。



<!--HONumber=Feb17_HO2-->


