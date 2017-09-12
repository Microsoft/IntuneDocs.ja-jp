---
title: "Exchange On-Premises および Exchange Online の条件付きアクセス コンプライアンスを監視する"
titlesuffix: Azure portal
description: "Intune Azure ポータルを使用して、Exchange On-Premises および Exchange Online の条件付きアクセス コンプライアンスを監視します"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: be0c1cef0dd6562feb54724edbf8ae22072e3d95
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="monitor-conditional-access-compliance-for-on-premises-exchange-and-exchange-online-in-intune"></a>Intune で Exchange On-Premises および Exchange Online の条件付きアクセス コンプライアンスを監視する

Intune 1704 リリース以降では、管理者は、内部設置型 Exchange Connector またはサービス間コネクタ (Exchange Online Connector) を使って、Intune と同期化される Exchange ActiveSync デバイス レコードに関するレポート情報を見ることができます。 条件付きアクセス コンプライアンス レポートでは、さまざまな同期状態のデバイスの概要が提供されます。

-   **許可**

-   **ブロック**

-   **検疫**

## <a name="to-monitor-conditional-access-compliance"></a>条件付きアクセス コンプライアンスを監視するには

1.  [Azure Portal](https://portal.azure.com/) に移動し、Intune の資格情報でサインインします。

2.  正常にサインインすると、**Azure ダッシュボード**が開きます。

3.  左側のメニューから **[その他のサービス]** を選択し、テキスト ボックス フィルターに「**Intune**」と入力します。

4.  **[Intune]** を選択すると、**Intune ダッシュボード**が表示されます。

5.  **[条件付きアクセス]** を選択し、**[概要]** を選択します。

6.  チャートの 3 つの領域 (**[ブロック済み]**、**[検疫]**、または **[許可]**) のいずれかを選び、条件付きアクセス コンプライアンス レポートを表示します。

    ![条件付きアクセス ダッシュボード](./media/CA-reporting-intune-1.png)

3 つの領域のいずれかを選ぶと、許可、ブロック、または検疫されているデバイスについての詳細を確認できます。

特定のデバイスにドリルダウンしてさらに詳細な情報を見ることもできます。 たとえば、次の図で選ばれているデバイスはブロックされています。 Intune では、条件付きアクセス コンプライアンス レポート ブレードから企業データを削除できます。

![条件付きアクセス デバイス詳細レポート](./media/CA-reporting-intune-3.png)

デバイスの詳細ブレードでは、さらに情報を表示できます。

-   **[概要]:** OS のバージョン、デバイス モデル、所有権、シリアル番号、デバイスの製造元、電話番号、デバイスの最終チェックイン日時など、デバイスのプロパティを見ることができます。

-   **[プロパティ]:** デバイスの所有権 (個人または企業) を設定できます。

-   **[ハードウェア]:** [概要] の情報に加えて、ストレージの詳細 (合計容量と空き容量)、システム エンクロージャ、ネットワークの詳細、ネットワーク サービス、およびその他の条件付きアクセスのブロックの詳細が表示されます。

-   **[検出されたアプリ]:** デバイスにインストールされているすべてのアプリケーションが表示されます。 インストールされているアプリの一覧を .CSV 形式にエクスポートすることもできます。

-   **[ポリシー準拠状況]:** すべてのデバイス コンプライアンス ポリシーの詳細が表示されます。

-   **[デバイス構成]:** すべてのデバイス構成の詳細が表示されます。

-   **[Exchange へのアクセス]:** 条件付きアクセス ポリシーを適用した後のデバイスの状態についてさらに詳しく確認できます。
