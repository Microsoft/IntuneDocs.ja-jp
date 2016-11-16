---
title: "Intune の管理対象 iOS デバイスをバックアップから復元する | Microsoft Intune"
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
translationtype: Human Translation
ms.sourcegitcommit: e6bb539c87c4a13a490ba98c016d814bea5c7bbc
ms.openlocfilehash: 6395e50b3e4c06e7363acc136b5ed9eb2ef75abd


---

# Intune の管理対象 iOS デバイスをバックアップから復元する

ユーザーが新しいデバイスを入手した場合など、管理者またはユーザーがバックアップから iOS デバイスを復元する状況があります。 このトピックでは、デバイスの復元後に必要になる可能性がある Intune 管理のセットアップについて説明します。

## 同じデバイスにバックアップを復元する

同じデバイスにバックアップを復元する場合、そのデバイスの登録状態も復元されます。 追加の操作は必要ありません。

## 別のデバイスにバックアップを復元する

別のデバイスにバックアップを復元する場合、登録の状態は新しいデバイスに自動的に復元されません。 ユーザーはポータル サイト アプリ バージョン 2.1.22 以降で、通常の登録手順に従って [iOS デバイスを Intune に登録する](/Intune/EndUser/enroll-your-device-in-intune-ios)必要があります。

> [!NOTE]
> 条件付きアクセス ポリシーでエンド ユーザーを対象にしている場合、再登録するまでエンド ユーザーは会社の電子メールにはアクセスできなくなります。

> [!TIP]
> ユーザーが通信するには、次のような手順が必要になります。まず、新しいデバイスで登録する場合、ポータル サイト アプリがバージョン 2.1.22 以降であることを確認します。 バージョンを確認するには、ポータル サイト アプリを開き、右上にある [メニュー] ボタンをタップし、[バージョン情報] をタップします。 古いバージョンの場合はポータル サイト アプリを終了し、App Store を開きます。 右下の [更新プログラム] ボタンをタップし、一覧のポータル サイト項目の横にある [更新] ボタンをタップします。 更新が完了したら、ポータル サイト アプリを起動し、[iOS デバイスを Intune に登録します](/Intune/EndUser/enroll-your-device-in-intune-ios)。

## 復元に関する既知の問題の解決

会社のポータル バージョン 2.1.21 以前を使用しているとき、デバイスを復元して、会社のポータル アプリを起動すると、問題が発生することがあります。 これらの問題は、ユーザーの状況に適した手順を実行することで対処できます。

### 新しいデバイスのみを使用するユーザーの場合
会社のポータル アプリを起動し、現在のデバイス タイルを選択して __[削除]__ ボタンをタップすることにより、登録を解除します。 削除した後、標準の登録手順に従って、[Intune に iOS デバイスを登録](/Intune/EndUser/enroll-your-device-in-intune-ios)します。

### 新旧両方のデバイスを使用するユーザーの場合
__[設定]__ > __[Safari]__ > __[Clear History and Website Data]__ (履歴と Web サイトのデータをクリア) をタップして、Safari から Cookie を消去します。 消去後、会社のポータル アプリをアンインストールして再インストールし、標準登録手順で [Intune に iOS デバイスを登録](/Intune/EndUser/enroll-your-device-in-intune-ios)します。



<!--HONumber=Oct16_HO3-->


