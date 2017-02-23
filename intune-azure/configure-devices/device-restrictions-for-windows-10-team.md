---
title: "Windows 10 Team 向けの Intune デバイスの制限設定 | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Windows 10 Team デバイスで使用できるデバイス制限について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 677c41a2-5344-4c52-85f0-809dce3a5d5b
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e6e0540acd5488077ae5217f8862e3bc5462ed71
ms.openlocfilehash: 342681922944fd1ea4be6aa4ddcb0725f6cfd42b


---

# <a name="windows-10-team-device-restriction-settings-in-intune-azure-preview"></a>Intune Azure プレビューでの Windows 10 Team デバイスの制限設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

- **[ユーザーの入室時に画面のスリープ状態を解除する]** - 部屋にだれかがいるとセンサーで検出したときに、デバイスのスリープ状態を自動的に解除します。
- **[ワイヤレス投影の PIN]** - デバイスのワイヤレス投影機能を使用する前に暗証番号 (PIN) を入力しなければならないかどうかを指定します。
- **[Miracast ワイヤレス投影]** - Windows 10 Team デバイスで Miracast が有効になっているデバイスを使用して投影する場合は、このオプションを有効にします。
- **[ようこそ画面に表示される会議情報]** - このオプションを有効にすると、ようこそ画面の [Meetings (会議)] タイルに表示される情報を選択できます。 次の操作を行います。
    - **[開催者と時刻のみの表示]**
    - **[開催者、時刻、議題の表示 (非公開なミーティングの場合は議題を非表示)]**
- **[ようこそ画面の背景画像の URL]** - Windows 10 Team デバイスの**ようこそ**画面に指定した URL のカスタム背景を表示する場合は、この設定を有効にします。<br>画像は PNG 形式である必要があり、URL は **https://** で始まっている必要があります。
- **[更新プログラムのメンテナンス期間]** - デバイスで更新を実行する期間を構成します。 期間の開始時刻と長さ (1 ~ 5 時間) を設定できます。
- **[Azure Operational Insights]** - Microsoft Operations Manager Suite の一部である Azure Operational Insights は、Windows 10 Team デバイスからログ ファイルのデータを収集、格納、分析します。<br>Azure Operational insights に接続するには、**ワークスペース ID** と **ワークスペース キー**を指定する必要があります。



<!--HONumber=Feb17_HO1-->


