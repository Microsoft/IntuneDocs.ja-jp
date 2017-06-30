---
title: "Intune をセットアップする"
description: "Intune サブスクリプションの使用を開始するための要件と前提条件"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: f4f84acfa48c0de6e1478be3ee8624a7fd4841ad
ms.openlocfilehash: bc51fce749e9cd86ea057b59dc26424d49d7dd66
ms.contentlocale: ja-jp
ms.lasthandoff: 06/16/2017


---


# <a name="set-up-intune"></a>Intune をセットアップする

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

このセクションの手順では、モバイル デバイス管理の環境をセットアップします。  

現在コンピューターとサーバーの管理に Microsoft System Center Configuration Manager を使用している場合は、[Configuration Manager を拡張してモバイル デバイスを管理する](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)ことができます。

>[!TIP]
>対象となるプランで Intune のライセンスを 150 個以上ご購入いただいた場合に、*FastTrack センター特典*をご利用いただけます。これは、Intune 向けに環境を整えるために Microsoft スペシャリストの支援を受けることができるサービスです。 「[Enterprise Mobility + Security (EMS) 用の FastTrack センター特典](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program)」を参照してください。

## <a name="checklist"></a>チェックリスト

| 手順 | 状態  |
| ------------- |-------------|
| 1  | [前提条件](supported-devices-browsers.md) - 必要なものと事前に確認が必要な事項|
| 2 |  [Intune にサインインする](account-sign-up.md) - 試用版サブスクリプションにサインインするか、新しいサブスクリプションを作成し、組織の管理を開始します。   |  
| 3 | [カスタム ドメイン名を構成する](custom-domain-name-configure.md) - DNS 登録を更新し、会社のドメイン名で Intune を管理します。   |
| 4 | [ユーザーを追加し AD を同期する](users-permissions-add.md) - Active Directory に接続して、ユーザーを同期したり、Intune にユーザーを追加したりします。  |
| 5 | [Intune のライセンスを割り当てる](licenses-assign.md) - Intune を使用するためのアクセス許可をユーザーに付与します。|
| 6 | [ユーザー グループとデバイス グループを整理する](groups-get-started.md) - グループを使用して、ポリシー、アプリ、リソースの展開を整理します。 |
| 7 | [アプリを追加する](apps-add.md) - ユーザーに展開できる設定とアプリを有効にします。 |
| 8 | [ポータル サイトをカスタマイズする](company-portal-customize.md) - Intune で作業するときにユーザーに表示されるポータル サイト アプリをカスタマイズします。  |
| 9 | [モバイル デバイスの登録を有効にする](mdm-authority-set.md) - iOS、Windows、Android、Mac デバイスの Intune 管理を有効にします。 |

