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
ms.sourcegitcommit: 6f687a1db84b49bc173d2067ab95598b4485daa8
ms.openlocfilehash: 618819ff8dded925bc4745160dde8c9e75694faf


---

# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Intune 管理者コンソールで Lookout MTP 接続を有効にする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune で Lookout MTP (Malicious Threat Protection) 接続を有効にするには、Lookout コンソールで Intune コネクタが構成済みである必要があります。  まだ構成していない場合は、[Lookout Mobile Threat Protection 用にサブスクリプションをセットアップする](set-up-your-subscription-with-lookout-mtp.md)必要があります。

Intune で Lookout MTP 接続を有効にするには、[Microsoft Intune 管理者コンソール](https://manage.microsoft.com)の **[管理]** ページで、**[Third Party Service Integration]** (サードパーティ サービスの統合) を選択します。 **[Lookout status]** (Lookout の状態) を選択し、トグル ボタンを使用して **[Synchronization with MTP]** (MTP との同期) を有効にします。

![有効トグル ボタンが強調して示されている Lookout 同期ページのスクリーンショット](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> コンプライアンス ポリシー ルールを作成して条件付きアクセスを構成する前に、Lookout for Work アプリを構成する**必要があります**。 これにより、アプリはエンド ユーザーがインストールできる状態になり、アプリをインストールするとエンド ユーザーは電子メールや他の会社のリソースにアクセスできます。

以上で、Intune 管理者コンソールでの Lookout と Intune の統合のセットアップは完了です。  このソリューションを実装するこの後の手順では、[Lookout for Work アプリ](https://docs.microsoft.com/intune/deploy-use/device-threat-protection-apps)を展開し、[コンプライアンス](https://docs.microsoft.com/intune/deploy-use/device-threat-protection-policy) ポリシーを設定します。


## <a name="next-steps"></a>次のステップ
[Lookout for Work アプリを構成する](https://docs.microsoft.com/intune/deploy-use/device-threat-protection-apps)



<!--HONumber=Feb17_HO4-->


