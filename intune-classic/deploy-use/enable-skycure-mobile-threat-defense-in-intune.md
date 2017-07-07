---
title: "Intune で Skycure Mobile Threat Defense を有効にする"
description: "Intune クラシック コンソールで Skycure Mobile Threat Defense を有効にします。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0cc4e59d-819a-47a2-a26f-4f8d0f8df7bf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4dad45d15fec7189fdcf184839040b9e3f9a3a48
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>Intune で Skycure Mobile Threat Defense を有効にする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Skycure Mobile Threat Defense を有効にするには、[Intune Connector in the Skycure console]\(Skycure コンソールの Intune コネクタ\) が構成済みである必要があります (/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)。

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>Intune で Skycure MTD の接続を有効にする

1.  [Intune クラシック コンソール](https://manage.microsoft.com/)に進み、資格情報を入力します。

2.  **[管理]** &gt; **[Third Party Service Integration (サード パーティ サービスの統合)]** の順に選択し、**[Skycure の状態]** を選択し、切り替えボタンで **[Synchronization with MTD (MTD と同期)]** を有効にします。

    ![Intune クラシック コンソールで Skycure 切り替えを有効にする](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> コンプライアンス ポリシー ルールを作成して条件付きアクセスを構成する前に、Skycure アプリを構成する必要があります。 これにより、アプリはエンド ユーザーがインストールできる状態になり、アプリをインストールするとエンド ユーザーは電子メールや他の会社のリソースにアクセスできます。

以上で、Intune 管理者コンソールでの Skycure と Intune の統合のセットアップは完了です。 このソリューションを実装するこの後の手順では、Skycure for Work アプリを展開し、コンプライアンス ポリシーを設定します。

## <a name="next-steps"></a>次のステップ

[Skycure Mobile Threat Defense コンプライアンス ポリシーを作成する](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
