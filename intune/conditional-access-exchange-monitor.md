---
title: Microsoft Intune で Exchange の条件付きアクセスを監視する
titlesuffix: ''
description: Intune Azure ポータルを使用し、Exchange On-Premises と Exchange Online の条件付きアクセス コンプライアンスを監視します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2ff5686e2d83831259bd21bee164b3c187e1c0ee
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231357"
---
# <a name="monitor-conditional-access-compliance-for-on-premises-exchange-and-exchange-online-in-intune"></a>Intune で Exchange On-Premises および Exchange Online の条件付きアクセス コンプライアンスを監視する

Intune 1704 リリース以降では、管理者は、内部設置型 Exchange Connector またはサービス間コネクタ (Exchange Online Connector) を使って、Intune と同期化される Exchange ActiveSync デバイス レコードに関するレポート情報を見ることができます。 条件付きアクセス コンプライアンス レポートでは、さまざまな同期状態のデバイスの概要が提供されます。

-   **許可**

-   **ブロック**

-   **検疫**

## <a name="to-monitor-conditional-access-compliance"></a>条件付きアクセス コンプライアンスを監視するには

1.  [Azure Portal](https://portal.azure.com/) に移動し、Intune の資格情報でサインインします。

2.  正常にサインインすると、**Azure ダッシュボード**が開きます。

3.  左側のメニューから **[すべてのサービス]** を選択し、テキスト ボックス フィルターに「**Intune**」と入力します。

4.  **[Intune]** を選ぶと、**Intune ダッシュボード**が表示されます。

5.  **[条件付きアクセス]** を選択し、**[概要]** を選択します。

6.  チャートの 3 つの領域 (**[許可]**、**[ブロック済み]**、 **[検疫]**) のいずれかを選択し、条件付きアクセス コンプライアンス レポートを表示します。

    ![条件付きアクセス ダッシュボードの画像](./media/CA-reporting-intune-1.png)

3 つの領域のいずれかを選択すると、許可、ブロック、または検疫されているデバイスについての詳細を確認できます。

特定のデバイスにドリルダウンしてさらに詳細な情報を見ることもできます。 たとえば、次の画像で選択されているデバイスはブロックされています。 Intune では、条件付きアクセス コンプライアンス レポート ウィンドウから企業データを削除できます。

![条件付きアクセス デバイス詳細レポートの画像](./media/CA-reporting-intune-3.png)

デバイスの詳細ウィンドウでは、さらに情報を表示できます。

-   **[概要]:** OS のバージョン、デバイス モデル、所有権、シリアル番号、デバイスの製造元、電話番号、デバイスの最終チェックイン日時など、デバイスのプロパティを見ることができます。

-   **[プロパティ]:** デバイスの所有権 (個人または企業) を設定できます。

-   **[ハードウェア]:** [概要] の情報に加えて、ストレージの詳細 (合計容量と空き容量)、システム エンクロージャ、ネットワークの詳細、ネットワーク サービス、およびその他の条件付きアクセスのブロックの詳細が表示されます。

-   **[検出されたアプリ]:** デバイスにインストールされているすべてのアプリケーションが表示されます。 インストールされているアプリの一覧を .CSV 形式にエクスポートすることもできます。

-   **[ポリシー準拠状況]:** すべてのデバイス コンプライアンス ポリシーの詳細が表示されます。

-   **[デバイス構成]:** すべてのデバイス構成の詳細が表示されます。

-   **[Exchange へのアクセス]:** 条件付きアクセス ポリシーを適用した後のデバイスの状態についてさらに詳しく確認できます。
