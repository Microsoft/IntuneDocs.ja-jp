---
title: Windows PC を保護するためのポリシー
titlesuffix: Microsoft Intune
description: これらのポリシーを使用すると、Intune クライアント ソフトウェアで管理しているときに Windows PC のセキュリティを確保できます。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d081f466-45dd-41d1-ab25-6d974c72a52a
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic-keep
ms.openlocfilehash: 10f19c0b9823adcd40ce38bae1c6cbaacd59c0db
ms.sourcegitcommit: 116be0eaa44fd5518ff34780d39569224ef4746b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36310489"
---
# <a name="use-policies-to-help-protect-windows-pcs-that-run-the-intune-client-software"></a>Intune クライアント ソフトウェアを実行する Windows PC の保護に有用なポリシーを使用する

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Microsoft Intune には 3 つのポリシーが用意されており、これらを使用すれば、[Intune クライアント ソフトウェア](manage-windows-pcs-with-microsoft-intune.md)が管理する Windows PC のセキュリティを容易に確保できます。


## <a name="software-updates"></a>ソフトウェア更新プログラム

Intune では、Microsoft および他社からソフトウェアの重要な更新プログラムが入手可能になるとその旨が通知されるため、[管理する Windows PC を最新の状態に保つ](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)ことができます。 これらの更新プログラムは、承認または拒否することができます。 承認した更新プログラムは、該当するすべての PC に自動的にインストールされます。

## <a name="windows-firewall"></a>Windows ファイアウォール

Windows ファイアウォールは、ハッカー、マルウェア、およびその他の脅威から Windows PC を保護するのに役立ちます。 Intune を使用すると、管理するすべての PC での [Windows ファイアウォールの設定および機能を管理する](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)ことができます。

## <a name="endpoint-protection"></a>Endpoint Protection

IT 管理者として最も優先度が高い事項の 1 つは、[管理する Windows PC をマルウェアやウイルスのない状態に保つことです](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)。 Intune は Endpoint Protection と統合することで、マルウェアの脅威に対するリアルタイムの保護を実現し、マルウェア定義を最新の状態に保ち、自動的にコンピューターをスキャンします。 また、Endpoint Protection は、マルウェアの攻撃の管理と監視に役立つツールも提供します。



### <a name="see-also"></a>関連項目
[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
