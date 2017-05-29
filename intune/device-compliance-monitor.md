---
title: "デバイス コンプライアンスを監視する方法"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: デバイス コンプライアンスを監視する方法。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: e073ca318d7db23239fc68b79718198dbee54b6e
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-monitor-device-compliance-in-intune-azure-preview"></a>Intune Azure プレビューでデバイス コンプライアンスを監視する方法

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

**[概要]** ブレードでは、**コンプライアンス プロファイル**の状態の概要を確認できます。
対話形式でグラフをクリックスルーして、詳細にドリルダウンできます。 複数のコンプライアンス プロファイルを構成している場合は、ポリシー ブレードに移動し、**[管理]** セクションで **[レポート]** を選択して、各ポリシーの状態を表示することもできます。  プレビューで表示できるレポートの詳細を以下に示します。

##  <a name="device-compliance"></a>デバイスのポリシー準拠

デバイス コンプライアンス レポートの概要ビューには、次のいずれかとして報告されたデバイスの数に関する集計情報がまず表示されます。

- **[準拠]**: デバイスは最近コンプライアンスが評価され、指定したコンプライアンス プロファイル設定に準拠していると判断されました。
- **[非準拠]**: デバイスは評価され、非準拠と判断されました。  プロファイルで猶予期間が指定されていた場合、猶予期間が終了して、デバイスが非準拠状態になっています。
- **[猶予期間]**: デバイスは評価され、非準拠と判断されました。 ただし、デバイスが実際に非準拠としてマークされるまでの猶予期間がまだ適用されています。

各セクションにドリルダウンすると、個々のデバイスとユーザーの詳細を表示できます。

## <a name="setting-compliance"></a>コンプライアンスの設定

コンプライアンスの設定レポートには、次のような各コンプライアンス設定の詳細が表示されます。

- 設定に準拠していないデバイスの数。
- 設定が適用されているプラットフォーム。

各設定をドリルダウンすると、これらの設定が有効になっているプロファイルの詳細情報と設定の値を表示できます。

