---
title: "Exchange Online 用の Exchange Connector | Microsoft Docs"
description: "Exchange ActiveSync モバイル デバイス管理 (MDM) をサポートするために、Intune を Office 365 Exchange サービスに接続する。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 4b73767f585cfa6283c7fb0601e7061efe42c606
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="configure-the-intune-service-to-service-connector-for-exchange-online"></a>Exchange Online 用の Intune Service to Service Connector の構成

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune と Exchange Online サービスまたは新しい Exchange Online Dedicated サービスを接続するには、この情報を使用します。 Exchange Online Dedicated 環境が**新しい**バージョンか**従来の**バージョンかを確認するには、アカウント マネージャーに問い合わせてください。 Intune は、サブスクリプションごとに任意の種類の Exchange Connector 接続を 1 つだけサポートします。

## <a name="service-to-service-connector-requirements"></a>Service to Service Connector の要件
**Service to Service Connector** は、Exchange Online または Exchange Online Dedicated のみをサポートします。また、オンプレミス インフラストラクチャの要件はありません。

|要件|説明|
|---------------|--------------------|
|Exchange Online が構成済みで実行中である|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|モバイル デバイス管理機関| [モバイル デバイスの管理機関を Microsoft Intune に設定します。](prerequisites-for-enrollment.md#step-2-set-mdm-authority)|
|Microsoft Exchange のバージョン|Exchange Online サービスまたは新しい Exchange Online Dedicated サービス|
|Active Directory の同期|Intune Connector を使用できるようにするには、[Active Directory の同期をセットアップ](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3)して、ローカル ユーザーとセキュリティ グループが Azure Active Directory のインスタンスと同期されるようにする必要があります。|

### <a name="exchange-cmdlet-requirements"></a>Exchange コマンドレットの要件

Intune Exchange Connector が使用する Exchange Online ユーザー アカウントも作成する必要があります。 このアカウントは、Intune 管理コンソールを使用し、次の必要な Windows PowerShell Exchange コマンドレットを実行するアクセス許可を持っている必要があります。

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy、Set-MobileDeviceMailboxPolicy、New-MobileDeviceMailboxPolicy、Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule、Set-ActiveSyncDeviceAccessRule、New-ActiveSyncDeviceAccessRule、Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>Service to Service Connector を設定します。

1. Exchange 管理者権限と[上記](#exchange-cmdlet-requirements)のコマンドレットのアクセス許可を持つユーザー アカウントで、[Microsoft Intune 管理コンソール](https://manage.microsoft.com)を開きます。 Microsoft Intune は、現在サインインしているユーザーの電子メール アドレスを使用して、接続をセットアップします。

2.  ワークスペースのショートカット ウィンドウで **[管理]** > **[モバイル デバイス管理]** > **[Microsoft Exchange]** > **[Exchange 接続のセットアップ]** の順に進みます。
![Service To Service Connector のセットアップページ](../media/intunesa5cservicetoserviceconnector.png)

3.  **[Exchange 接続のセットアップ]** ページで **[Service To Service Connector のセットアップ]**を選びます。


Service to Service Connector は自動的に構成され、Exchange Online 環境または新しい Exchange Online Dedicated 環境と同期されます。

## <a name="validate-your-exchange-connection"></a>Exchange 接続の確認

Exchange Connector を正常に構成した後で、[Microsoft Intune 管理コンソール](https://manage.microsoft.com)に進みます。 [**管理**] > [**モバイル デバイス管理**] > [**Microsoft Exchange**] の順に選択します。 入力した詳細が [**Exchange の接続情報**] の下に表示されることを確認します。

また、前回いつ同期が完了したかも確認することができます。

