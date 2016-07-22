---
title: "Exchange ActiveSync および Microsoft Intune を使用したモバイル デバイス管理 | Microsoft Intune"
description: 
keywords: 
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: d24395786daa7aec103ec754895868a75983e099


---

# Exchange ActiveSync および Microsoft Intune を使用したモバイル デバイス管理
Microsoft Intune でモバイル デバイスを直接管理するには、ユーザーがデバイスを Intune に登録する必要があります。 ユーザーが登録していないモバイル デバイスの場合、Exchange Connector を使用して Exchange ActiveSync (EAS) 管理を有効にすることができます。 オンプレミスの Exchange サーバーまたはクラウドでホストされた Microsoft Office 365 の Exchange で、デバイスを管理できます。

## モバイル デバイスの Exchange アクセス ルール ##

Exchange では、モバイル デバイスが EAS への接続を試みたときの処理を定義する一連のルールが必要です。 これらのルールは、Intune 管理コンソールで管理します。

[モバイル デバイスの Exchange アクセス ルール](exchange-access-rules-for-mobile-devices.md)

## Exchange Connector をインストールする
Exchange Connector を使用すると、Intune コンソールで Exchange の展開を管理できます。 最初に、適切な Intune-to-Exchange Connector をインストールして構成する必要があります。 Exchange サーバーがオンプレミスか、クラウドにサービスとしてホストされているかに応じて、適切なオプションを選択します。

-   [オンプレミス Exchange 用の Intune コネクタをインストールする](intune-on-premises-exchange-connector.md)
-   [ホスト型 Exchange 用の Intune Service to Service Connector を構成する](intune-service-to-service-exchange-connector.md)

## Exchange で管理されているモバイル デバイスのポリシーを適用する
Intune コンソールから適用できるポリシー設定については、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)」を参照してください。 各モバイル デバイスでサポートされる Exchange ActiveSync のポリシー設定と機能の一覧については、「[Exchange ActiveSync Client Comparison Table](http://go.microsoft.com/fwlink/?LinkId=247270)」 (Exchange ActiveSync クライアントの比較表) を参照してください。

> [!NOTE]
> Intune を Microsoft Exchange 環境に接続すると、Intune で管理されているすべてのユーザーの EAS ポリシーは、Intune 内で特定のポリシーが定義されていない限り、Microsoft Exchange サーバーの現在の既定のポリシーにリセットされます。

## 会社のデータをモバイル デバイスから消去する
最後に、会社のデータが不要になったとき、またはデバイスをなくしたり盗まれたりしたときは、[EAS で管理されたモバイル デバイスから会社のデータを消去](wipe-for-exchange-managed-mobile-devices.md)できます。



<!--HONumber=Jun16_HO4-->


