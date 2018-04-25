---
title: Intune で Skycure Mobile Threat Defense を有効にする
description: Intune クラシック ポータルで Skycure Mobile Threat Defense を有効にします。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0cc4e59d-819a-47a2-a26f-4f8d0f8df7bf
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: da4197a41798f4e47ff35d2dfab36c5317f92e21
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>Intune で Skycure Mobile Threat Defense を有効にする

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Skycure Mobile Threat Defense を有効にするには、[Skycure コンソールで Intune コネクタ](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)が構成済みである必要があります。

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>Intune で Skycure MTD の接続を有効にする

1.  [Intune クラシック ポータル](https://manage.microsoft.com/)に進み、資格情報を入力します。

2.  **[管理]** &gt; **[Third Party Service Integration (サード パーティ サービスの統合)]** の順に選択し、**[Skycure の状態]** を選択し、切り替えボタンで **[Synchronization with MTD (MTD と同期)]** を有効にします。

    ![Intune クラシック ポータルで Skycure 切り替えを有効にする](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> コンプライアンス ポリシー ルールを作成して条件付きアクセスを構成する前に、Skycure アプリを構成する必要があります。 これにより、アプリはエンド ユーザーがインストールできる状態になり、アプリをインストールするとエンド ユーザーは電子メールや他の会社のリソースにアクセスできます。

以上で、Intune 管理者コンソールでの Skycure と Intune の統合のセットアップは完了です。 このソリューションを実装するこの後の手順では、Skycure for Work アプリを展開し、コンプライアンス ポリシーを設定します。

## <a name="next-steps"></a>次の手順

[Skycure Mobile Threat Defense コンプライアンス ポリシーを作成する](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
