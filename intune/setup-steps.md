---
title: Microsoft Intune をセットアップする
description: Intune サブスクリプションの使用を開始するための要件と前提条件
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: dougeby
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: be8a04b28494e5806a1e5127d4d0bbdf4cd98f36
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="set-up-intune"></a>Intune をセットアップする

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

これらのセットアップで、Intune を使用してモバイル デバイス管理 (MDM) を有効にできます。 会社のリソースにアクセスする許可をユーザーに与える前に、あるいはデバイスの設定を管理する前に、デバイスを管理対象にする必要があります。

Intune サブスクリプションの設定や MDM 権限の設定など、一部の手順はほとんどのシナリオで必須となります。 カスタム ドメインの構成やアプリの追加など、その他の手順が必要かどうかは会社次第です。

現在コンピューターとサーバーの管理に Microsoft System Center Configuration Manager を使用している場合は、[Configuration Manager を拡張してモバイル デバイスを管理する](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)ことができます。

>[!TIP]
>対象となるプランで Intune のライセンスを 150 以上購入した場合は、*FastTrack センター特典*をご利用いただけます。 このサービスでは、Microsoft のスペシャリストが Intune 用の環境の準備をお手伝いします。 「[Enterprise Mobility + Security (EMS) 用の FastTrack センター特典](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program)」を参照してください。



| 手順 | 状態  |
| ------------- |-------------|
| 1  | [サポートされる構成](supported-devices-browsers.md) - 開始前に知っておく必要がある情報です。 サポートされる構成やネットワーク要件などです。|
| 2 |  [Intune にサインインする](account-sign-up.md) - 試用版サブスクリプションにサインインするか、新しい Intune サブスクリプションを作成します。 |  
| 3 | [ドメイン名を構成する](custom-domain-name-configure.md) - 会社のドメイン名を Intune と接続するために DNS の登録を設定します。 Intune に接続し、リソースを利用するとき、なじみのあるドメインがユーザーに与えられます。  |
| 4 | [ユーザーを追加する](users-add.md) - 手動でユーザーを追加するか、Active Directory を接続して Intune とユーザーを同期します。 デバイスがたとえば "ユーザーなし" のキオスク デバイスでない限り、必須となります。 |
| 5 | [ライセンスを割り当てる](licenses-assign.md) - Intune を使用するためのアクセス許可をユーザーに付与します。 サービスにアクセスするには、ユーザーまたはユーザーレス デバイスごとに Intune ライセンスが必要になります。|
| 6 |  [グループを追加する](groups-add.md) - ユーザー グループとデバイス グループを使って管理タスクを簡略化します。 アプリ、設定、その他のリソースを割り当てるためにグループが使用されます。 |
| 7 | [アプリを追加する](apps-add.md) - アプリはグループに割り当て、自動的に、あるいは任意でインストールできます。 |
| 8 | [デバイスを構成する](device-profiles.md) - デバイス設定を管理するプロファイルを設定します。 デバイス プロファイルでは、電子メール、VPN、Wi-Fi、デバイス機能の設定を事前構成できます。 デバイスを制限し、デバイスとデータの両方を保護することもできます。  |
| 9 | [ポータル サイトをカスタマイズする](company-portal-app.md) - ユーザーがデバイスの登録とアプリのインストールに使用する Intune ポータル サイトをカスタマイズします。 これらの設定は、ポータル サイト アプリと Intune ポータル サイト Web サイトの両方に表示されます。 |
| 10 | [デバイス登録を有効にする](mdm-authority-set.md) - MDM 権限を設定し、特定のプラットフォームを有効にすることで、iOS、Windows、Android、Mac デバイスの Intune 管理を有効にします。 |
| 11 | [アプリ ポリシーを構成する](app-protection-policy.md) - Microsoft Intune でのアプリ保護ポリシーに基づいて特定の設定を指定します。 |
