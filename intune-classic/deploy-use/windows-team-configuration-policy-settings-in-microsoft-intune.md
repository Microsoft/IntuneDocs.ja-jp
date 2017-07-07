---
title: "Windows Team 構成ポリシー設定"
description: "Microsoft Intune **Windows 10 Team 全般構成ポリシー** を使用して、Microsoft Surface Hub などの登録済みの Windows 10 Team デバイスの設定を構成します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6e0f0ea969ed78f2daf482438b056c8b4eb1a316
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="windows-team-configuration-policy-settings-in-microsoft-intune"></a>Microsoft Intune の Windows Team 構成ポリシー設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune **Windows 10 Team 全般構成ポリシー**を使用して、Microsoft Surface Hub などの登録済みの Windows 10 Team デバイスの設定を構成します。

|設定の名前|説明|
|----------------|-----------|
|**部屋にだれかがいるときに画面のスリープ状態を自動的に解除する**|部屋にだれかがいるとセンサーで検出したときに、デバイスのスリープ状態を自動的に解除します。|
|**ワイヤレス投影には PIN を必要とする**|デバイスのワイヤレス投影機能を使用する前に暗証番号 (PIN) を入力しなければならないかどうかを指定します。|
|**デバイスの更新プログラムのメンテナンス期間を設定する**|デバイスで更新を実行する期間を設定します。 期間の開始時刻と長さ (1 ~ 5 時間) を設定できます。|
|**Azure Operational Insights を有効にする**|Microsoft Operations Manager Suite の一部である Azure Operational Insights は、Windows 10 Team デバイスからログ ファイルのデータを収集、格納、分析します。<br /><br />Azure Operational insights に接続するには、**ワークスペース ID** と **ワークスペース キー**を指定する必要があります。|
|**Miracast ワイヤレス投影を有効にする**|Windows 10 Team デバイスで Miracast が有効になっているデバイスを使用して投影する場合は、このオプションを有効にします。<br /><br />このオプションを有効にする場合は、「**Miracast チャネル**」から、コンテンツの投影に使用する Miracast チャネルを選択します。|
|**[ようこそ] 画面に表示される会議の情報を選択する**|このオプションを有効にすると、**[ようこそ]** 画面の **[会議]** タイルに表示される情報を選択できます。 次の操作を行います。<br /><br />-   **開催者と時刻のみを表示する**<br />-   **開催者、時刻、議題を表示する (非公開なミーティングの場合は議題を非表示)**|
|**ロック画面の背景画像 URL**|Windows 10 Team デバイスの **[ようこそ]** 画面に指定した URL のカスタム背景を表示する場合は、この設定を有効にします。<br /><br />画像は PNG 形式である必要があり、URL は **https://** で始まっている必要があります。|


### <a name="see-also"></a>関連項目
[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

