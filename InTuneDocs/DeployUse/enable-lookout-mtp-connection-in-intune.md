---
title: "Intune で Lookout MTP を有効にする | Microsoft Intune"
description: "Intune 管理者コンソールで Lookout Mobile Threat Protection を有効にします。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ceaeba74f8671caf4125252fce02fd06752c3fe8
ms.openlocfilehash: 2052aca24baa752bc4fad3bd7a75f8efa109e9e9


---

# Intune 管理者コンソールで Lookout MTP 接続を有効にする
このトピックでは、Intune で Lookout MTP 接続を有効にする方法を説明します。 この手順を実行する前に、Lookout コンソールで Intune コネクタを構成しておく必要があります。  これをまだ行っていない場合は、「[Lookout Mobile Threat Protection 用にサブスクリプションを設定する](set-up-your-subscription-with-lookout-mtp.md)」で説明されている手順を実行します。

Intune で Lookout MTP 接続を有効にするには、[Microsoft Intune 管理者コンソール](https://manage.microsoft.com)の **[管理]** ページで、**[Third Party Service Integration]** (サードパーティ サービスの統合) を選択します。 **[Lookout status]** (Lookout の状態) を選択し、トグル ボタンを使用して **[Synchronization with MTP]** (MTP との同期) を有効にします。

![有効トグル ボタンが強調して示されている Lookout 同期ページのスクリーンショット](../media/mtp/lookout-intune-synchronization.png)

以上で、Intune 管理者コンソールでの Lookout と Intune の統合のセットアップは完了です。  このソリューションを実装するこの後の手順では、[Lookout for Work アプリ](configure-and-deploy-lookout-for-work-apps.md)を展開し、[コンプライアンス](enable-device-threat-protection-rule-in-compliance-policy.md) ポリシーを設定します。

>[!IMPORTANT]
> コンプライアンス ポリシー ルールを作成して条件付きアクセスを構成する前に、Lookout for Work アプリを構成する**必要があります**。 これにより、アプリはエンド ユーザーがインストールできる状態になり、アプリをインストールするとエンド ユーザーは電子メールや他の会社のリソースにアクセスできます。
## 次のステップ
[Lookout for Work アプリを構成する ](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Sep16_HO4-->


