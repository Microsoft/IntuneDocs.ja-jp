---
title: "デバイス コンプライアンスを監視する"
titlesuffix: Microsoft Intune
description: "デバイス コンプライアンスを監視する方法を説明します。\""
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 708ed5a335d3475c213a536da9072afb1ad32ef9
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="monitor-device-compliance-in-intune"></a>Intune でのデバイス コンプライアンスの監視

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[概要]** ブレードでは、**コンプライアンス プロファイル**の状態の概要を確認できます。
対話形式でグラフをクリックスルーして、詳細にドリルダウンできます。 コンプライアンス プロファイルが複数構成されている場合、**[管理]** > **[レポート]** の下のポリシー ブレードでポリシーの状態を参照できます。

##  <a name="device-compliance"></a>デバイスのポリシー準拠

デバイス コンプライアンス レポートの概要ビューには、次のいずれかとして報告されたデバイスの数に関する集計情報が表示されます。

- **[準拠]**: デバイスが、指定したコンプライアンスのプロファイル設定に準拠していると最近評価されました。
- **[非準拠]**: デバイスは評価され、非準拠と判断されました。  プロファイルで猶予期間が指定されていた場合、猶予期間が終了して、デバイスが非準拠状態になっています。
- **[猶予期間]**: デバイスは評価され、非準拠と判断されました。 ただし、デバイスが非準拠としてマークされるまでの猶予期間がまだ適用されています。

各セクションにドリルダウンすると、個々のデバイスとユーザーの詳細を表示できます。

## <a name="setting-compliance"></a>コンプライアンスの設定

コンプライアンスの設定レポートには、次のような各コンプライアンス設定の詳細が表示されます。

- 設定に準拠していないデバイスの数。
- 設定が適用されているプラットフォーム。

各設定をドリルダウンすると、これらの設定が有効になっているプロファイルの詳細情報と設定の値を表示できます。
