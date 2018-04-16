---
title: "Exchange ActiveSync デバイス管理"
description: "Exchange Connector を使用した Exchange ActiveSync (EAS) 管理によるモバイル デバイスの管理"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f5e9bd3dd2026096c323858fc7faa915895ed55d
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="exchange-activesync-mobile-device-management-with-microsoft-intune"></a>Microsoft Intune を使用した Exchange ActiveSync モバイル デバイスの管理

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune でモバイル デバイスを直接管理するには、デバイスが [Intune に登録](prerequisites-for-enrollment.md)されている必要があります。 別の方法として、管理者は Exchange Connector と Exchange ActiveSync (EAS) 管理を組み合わせて使用する、より限定的な管理ソリューションを有効にすることもできます。 オンプレミスの Exchange サーバーで、または Office 365 を使用した Exchange Onlineで、デバイスを管理することができます。 Intune は、サブスクリプションごとに任意の種類の Exchange Connector 接続を 1 つだけサポートします。

## <a name="exchange-access-rules-for-mobile-devices"></a>モバイル デバイスの Exchange アクセス ルール ##

Exchange では、モバイル デバイスが EAS への接続を試みたときの処理を定義する一連のルールが必要です。 これらのルールは、Intune 管理コンソールで管理します。

[モバイル デバイスの Exchange アクセス ルール](exchange-access-rules-for-mobile-devices.md)

## <a name="install-the-exchange-connector"></a>Exchange Connector をインストールする
Exchange Connector を使用すると、Intune コンソールで Exchange の展開を管理できます。 最初に、適切な Intune-to-Exchange Connector をインストールしてセットアップする必要があります。 Exchange サーバーがオンプレミスか、クラウドにサービスとしてホストされているかに応じて、適切なオプションを選択します。

-   [Exchange Online または新しい Exchange Online Dedicated 環境に対して Intune を構成する](intune-service-to-service-exchange-connector.md)
-   [オンプレミスの Exchange サーバーおよび従来の Exchange Online Dedicated 環境で Intune コネクタをインストールする](intune-on-premises-exchange-connector.md)


## <a name="apply-policy-for-exchange-managed-mobile-devices"></a>Exchange で管理されているモバイル デバイスのポリシーを適用する
Intune コンソールを使用すれば、[EAS ポリシー設定](exchange-activesync-policy-settings-in-microsoft-intune.md)を管理し、[会社のリソースへのアクセスを制限](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)することができます。 各モバイル デバイスでサポートされる Exchange ActiveSync のポリシー設定と機能の一覧については、「[Exchange ActiveSync Client Comparison Table](http://go.microsoft.com/fwlink/?LinkId=247270)」 (Exchange ActiveSync クライアントの比較表) を参照してください。

> [!NOTE]
> Intune を Microsoft Exchange 環境に接続すると、Intune で管理されているすべてのユーザーの EAS ポリシーは、Intune 内で特定のポリシーが定義されていない限り、Microsoft Exchange サーバーの現在の既定のポリシーにリセットされます。

## <a name="wipe-company-data-from-mobile-devices"></a>会社のデータをモバイル デバイスから消去する
最後に、会社のデータが不要になったとき、またはデバイスをなくしたり盗まれたりしたときは、[EAS で管理されたモバイル デバイスから会社のデータを消去](wipe-for-exchange-managed-mobile-devices.md)できます。
