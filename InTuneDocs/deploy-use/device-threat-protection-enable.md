---
title: "Intune で Lookout MTP を有効にする | Microsoft Docs"
description: "Intune 管理者コンソールで Lookout Mobile Threat Protection を有効にします。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 53862e49c922b75b414fd5aceec3bba2b10299a6
ms.openlocfilehash: 1297522d0f7b52ebe14eb7b938f3458e7308ae27


---

# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Intune 管理者コンソールで Lookout MTP 接続を有効にする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune で Lookout MTP (Malicious Threat Protection) 接続を有効にするには、Lookout コンソールで Intune コネクタが構成済みである必要があります。  まだ構成していない場合は、[Lookout Mobile Threat Protection 用にサブスクリプションをセットアップする](set-up-your-subscription-with-lookout-mtp.md)必要があります。

Intune で Lookout MTP 接続を有効にするには、[Microsoft Intune 管理者コンソール](https://manage.microsoft.com)の **[管理]** ページで、**[Third Party Service Integration]** (サードパーティ サービスの統合) を選択します。 **[Lookout status]** (Lookout の状態) を選択し、トグル ボタンを使用して **[Synchronization with MTP]** (MTP との同期) を有効にします。

![有効トグル ボタンが強調して示されている Lookout 同期ページのスクリーンショット](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> コンプライアンス ポリシー ルールを作成して条件付きアクセスを構成する前に、Lookout for Work アプリを構成する**必要があります**。 これにより、アプリはエンド ユーザーがインストールできる状態になり、アプリをインストールするとエンド ユーザーは電子メールや他の会社のリソースにアクセスできます。

以上で、Intune 管理者コンソールでの Lookout と Intune の統合のセットアップは完了です。  このソリューションを実装するこの後の手順では、[Lookout for Work アプリ](configure-and-deploy-lookout-for-work-apps.md)を展開し、[コンプライアンス](enable-device-threat-protection-rule-in-compliance-policy.md) ポリシーを設定します。


## <a name="next-steps"></a>次のステップ
[Lookout for Work アプリを構成する](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Jan17_HO2-->


