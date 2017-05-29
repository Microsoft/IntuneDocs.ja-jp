---
title: "Intune の管理対象 iOS デバイスをバックアップから復元する | Microsoft Docs"
description: "バックアップから復元した後にデバイスを再登録する方法のエンド ユーザー向けガイダンスについて説明します。"
keywords: "復元, 管理, iOS"
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 438a478be79bb4def8675856075ecedfe8290bb7
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="restore-intune-managed-ios-devices-from-backup"></a>Intune の管理対象 iOS デバイスをバックアップから復元する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

ユーザーが新しいデバイスを入手した場合など、管理者またはユーザーがバックアップから iOS デバイスを復元する状況があります。 このトピックでは、デバイスの復元後に必要になる可能性がある Intune 管理のセットアップについて説明します。

## <a name="restoring-backups-onto-the-same-device"></a>同じデバイスにバックアップを復元する

同じデバイスにバックアップを復元する場合、そのデバイスの登録状態も復元されます。 追加の操作は必要ありません。

## <a name="restoring-backups-onto-different-devices"></a>別のデバイスにバックアップを復元する

別のデバイスにバックアップを復元する場合、登録の状態は新しいデバイスに自動的に復元されません。 ユーザーはポータル サイト アプリ バージョン 2.1.22 以降で、通常の登録手順に従って [iOS デバイスを Intune に登録する](/intune-user-help/enroll-your-device-in-intune-ios)必要があります。

> [!NOTE]
> 条件付きアクセス ポリシーでエンド ユーザーを対象にしている場合、再登録するまでエンド ユーザーは会社の電子メールにはアクセスできなくなります。

> [!TIP]
> ユーザーが通信するには、次のような手順が必要になります。まず、新しいデバイスで登録する場合、ポータル サイト アプリがバージョン 2.1.22 以降であることを確認します。 バージョンを確認するには、ポータル サイト アプリを開き、右上にある [メニュー] ボタンをタップし、[バージョン情報] をタップします。 古いバージョンの場合はポータル サイト アプリを終了し、App Store を開きます。 右下の [更新プログラム] ボタンをタップし、一覧のポータル サイト項目の横にある [更新] ボタンをタップします。 更新が完了したら、ポータル サイト アプリを起動し、[iOS デバイスを Intune に登録します](/intune-user-help/enroll-your-device-in-intune-ios)。

## <a name="resolving-known-issues-with-restores"></a>復元に関する既知の問題の解決

会社のポータル バージョン 2.1.21 以前を使用しているとき、デバイスを復元して、会社のポータル アプリを起動すると、問題が発生することがあります。 これらの問題は、ユーザーの状況に適した手順を実行することで対処できます。

### <a name="for-users-who-will-only-use-their-new-device"></a>新しいデバイスのみを使用するユーザーの場合
会社のポータル アプリを起動し、現在のデバイス タイルを選択して __[削除]__ ボタンをタップすることにより、登録を解除します。 削除した後、標準の登録手順に従って、[Intune に iOS デバイスを登録](/intune-user-help/enroll-your-device-in-intune-ios)します。

### <a name="for-users-who-will-use-both-their-old-and-new-devices"></a>新旧両方のデバイスを使用するユーザーの場合
__[設定]__ > __[Safari]__ > __[Clear History and Website Data]__ (履歴と Web サイトのデータをクリア) をタップして、Safari から Cookie を消去します。 消去後、会社のポータル アプリをアンインストールして再インストールし、標準登録手順で [Intune に iOS デバイスを登録](/intune-user-help/enroll-your-device-in-intune-ios)します。

