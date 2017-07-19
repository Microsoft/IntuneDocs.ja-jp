---
title: "Intune をセットアップする"
description: "Intune サブスクリプションの使用を開始するための要件と前提条件"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/05/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 966183f0da7a48148a193a1823f74b9e416f4004
ms.sourcegitcommit: bee30f4c9e04129d70305fcafc4152c6e062a8b0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2017
---
# <a name="set-up-intune"></a>Intune をセットアップする

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

セットアップ手順では、モバイル デバイス管理の環境を準備します。  

現在コンピューターとサーバーの管理に Microsoft System Center Configuration Manager を使用している場合は、[Configuration Manager を拡張してモバイル デバイスを管理する](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)ことができます。

>[!TIP]
>対象となるプランで Intune のライセンスを 150 以上購入した場合は、*FastTrack センター特典*をご利用いただけます。 このサービスでは、Microsoft のスペシャリストが Intune 用の環境の準備をお手伝いします。 「[Enterprise Mobility + Security (EMS) 用の FastTrack センター特典](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program)」を参照してください。

| 手順 | 状態  |
| ------------- |-------------|
| 1  | [前提条件](supported-devices-browsers.md) - 開始前に知っておく必要がある情報です|
| 2 |  [Intune にサインインする](account-sign-up.md) - 試用版サブスクリプションにサインインするか、新しいサブスクリプションを作成します |  
| 3 | [ドメイン名を構成する](custom-domain-name-configure.md) - 会社のドメイン名を Intune と接続するために DNS の登録を設定します  |
| 4 | [ユーザーを追加する](users-add.md) - 手動でユーザーを追加するか、Active Directory を接続して Intune とユーザーを同期します  |
| 5 | [ライセンスを割り当てる](licenses-assign.md) - Intune を使用するためのアクセス許可をユーザーに付与します|
| 6 |  [グループを追加する](groups-add.md) - ユーザー グループとデバイス グループを使って管理タスクを簡略化します |
| 7 | [アプリを追加する](apps-add.md) - ユーザーに展開できる設定とアプリを有効にします。 |
| 8 | [デバイスを構成する](device-profiles.md) - デバイスを管理して会社のリソースにアクセスするプロファイルを設定します |
| 9 | [ポータル サイトをカスタマイズする](company-portal-app.md) - Intune ポータル サイトをカスタマイズします   |
| 10 | [デバイスの登録を有効にする](mdm-authority-set.md) - iOS、Windows、Android、Mac デバイスの Intune 管理を有効にします |
