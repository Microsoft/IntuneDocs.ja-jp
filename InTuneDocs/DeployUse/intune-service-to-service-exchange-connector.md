---
title: "Exchange Online 用の Exchange Connector | Microsoft Intune"
description: "Exchange ActiveSync モバイル デバイス管理 (MDM) をサポートするために、Intune を Office 365 Exchange サービスに接続する。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: a6438bb3ca21e5c46dca5ebe69266fd9bce9a4b8


---

# Exchange Online 用の Intune Service to Service Connector の構成

Microsoft Intune と Exchange Online サービスまたは新しい Exchange Online Dedicated サービスを接続するには、この情報を使用します。 Exchange Online Dedicated 環境が**新しい**ものか**従来の**ものかを確認するには、アカウント マネージャーに問い合わせてください。 Intune は、サブスクリプションごとに任意の種類の Exchange Connector 接続を 1 つだけサポートします。

## Service to Service Connector の要件
**Service to Service Connector** は、Exchange Online または新しい Exchange Online Dedicated のみをサポートします。また、社内インフラストラクチャの要件はありません。

|要件|説明|
|---------------|--------------------|
|Exchange Online が構成済みで実行中である|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|モバイル デバイス管理機関| [モバイル デバイスの管理機関を Microsoft Intune に設定します](prerequisites-for-enrollment.md#set-mobile-device-management-authority)|
|Microsoft Exchange のバージョン|Exchange Online サービスまたは新しい Exchange Online Dedicated サービス|
|Active Directory の同期|Intune Connector を使用できるようにするには、[Active Directory の同期をセットアップ](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3)して、ローカル ユーザーとセキュリティ グループが Azure Active Directory のインスタンスと同期されるようにする必要があります。|

### Exchange コマンドレットの要件

Intune Exchange Connector が使用する Exchange Online ユーザー アカウントも作成する必要があります。 このアカウントは、Intune 管理コンソールを使用し、次の必要な Windows PowerShell Exchange コマンドレットを実行するアクセス許可を持っている必要があります。

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy、Set-MobileDeviceMailboxPolicy、New-MobileDeviceMailboxPolicy、Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule、Set-ActiveSyncDeviceAccessRule、New-ActiveSyncDeviceAccessRule、Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## Service to Service Connector のセットアップ

1. Exchange 管理者権限と[上記](#exchange-cmdlet-requirements)のコマンドレットのアクセス許可を持つユーザー アカウントで、[Microsoft Intune 管理コンソール](http://manage.microsoft.com)を開きます。 Microsoft Intune は、現在ログインしているユーザーの電子メール アドレスを使用して、接続をセットアップします。

2.  ワークスペースのショートカット ウィンドウで**[管理]** を選択し、**[モバイル デバイス管理]** > **[Microsoft Exchange]**  > **[Exchange 接続のセットアップ]** に進みます。
![[Service To Service Connector のセットアップ] ページ](../media/intunesa5cservicetoserviceconnector.png)

3.  **[Exchange 接続のセットアップ]** ページで **[Service To Service Connector のセットアップ]**を選びます。


Service to Service Connector は自動的に構成され、Exchange Online 環境または新しい Exchange Online Dedicated 環境と同期されます。

## Exchange 接続の確認

Exchange Connector の構成が正常に完了したら、[Microsoft Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** を選択し、**[モバイル デバイス管理]** > **[Microsoft Exchange]** に進んで、**[Exchange の接続情報]** に表示される設定内容の詳細を確認します。

また、前回いつ同期が完了したかも確認することができます。



<!--HONumber=Sep16_HO4-->


