---
title: Microsoft Intune reports
titleSuffix: Microsoft Intune
description: Intune には、一貫性のあるタイムリーなデータが含まれる、特定の種類のレポートが用意されています。
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3ae06ae3f9f76d86a792721d45f8319bfe6491fd
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654228"
---
# <a name="intune-reports"></a>Intune レポート
Microsoft Intune レポートを使用すると、組織全体のエンドポイントの正常性とアクティビティをより効果的かつ積極的に監視できるだけでなく、Intune 全体で他のレポート データを提供することもできます。 たとえば、デバイスのポリシー準拠、デバイスの正常性、デバイスの傾向に関するレポートを表示できます。 さらに、カスタム レポートを作成し、より具体的なデータを取得できます。 

> [!NOTE]
> ユーザーが新しい構造に備えて準備し、調整できるよう、Intune のレポート変更は一定の期間で徐々にロールアウトされます。

レポートの種類は次の対象領域に分類されます。
- **運用** - ユーザーが集中的に行動をとれるよう、対象を絞ったタイムリーなデータを提供します。 これらのレポートは、管理者、領域の専門家、ヘルプ デスクにとって最も役に立つと考えられます。
- **組織** - デバイス管理状態など、より広範な全体的なビューの概要を表示します。 これらのレポートは、マネージャーと管理者にとって最も役に立つと考えられます。
- **履歴** - 一定期間におけるパターンと傾向を提示します。 これらのレポートは、マネージャーと管理者にとって最も役に立つと考えられます。
- **スペシャリスト** - 生データを使用し、独自のカスタム レポートを作成できます。 これらのレポートは、管理者にとって最も役に立つと考えられます。

このレポート フレームワークでは、一貫性のある包括的なレポート機能が提供されます。 利用できるレポートには次の機能があります。
- **検索と並べ替え** - データセットの大きさに関係なく、すべての列で検索したり、並べ替えたりできます。
- **データ ページング** - ページングに基づいてデータをスキャンできます (ページごとにスキャンするか、特定のページにジャンプする)。
- **パフォーマンス** - 大規模なテナントから作成されたレポートを簡単に生成して表示できます。
- **エクスポート** - 大規模なテナントから生成されたレポート データを簡単にエクスポートできます。

### <a name="who-can-access-the-data"></a>データにアクセスできるユーザー

次のアクセス許可を持つユーザーがログを確認できます。

- グローバル管理者
- Intune サービス管理者
- **読み取り**アクセス許可が含まれる Intune ロールに割り当てられた管理者

## <a name="non-compliant-devices-report-operational"></a>非準拠デバイス レポート (運用)
非準拠デバイス レポートには、問題の特定や問題の修復に役立てる目的で、一般的にヘルプデスクや管理者ロールで使用されるデータがあります。 この種のレポートに含まれるデータはタイムリーで、予想外の動作について指摘するものであり、アクション可能であることを目的としています。 レポートはワークロードと共に利用でき、アクティブ ワークフローから離れることなく、非準拠デバイス レポートにアクセスできます。 このレポートには、フィルタリング機能、検索機能、ページング機能、並べ替え機能があります。 トラブルシューティングのためにドリルダウンすることもできます。

**非準拠デバイス**のレポートは次の手順で表示できます。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]**  >  **[モニター]**  >  **[非準拠デバイス]** を選択します。

    ![非準拠デバイス レポート](./media/intune-reports/intune-reports-02.png)

    > [!TIP]
    > 以前に Azure portal で Intune を使用したことがある場合は、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[デバイスのポリシー準拠]**  >  **[準拠していないデバイス]** を選択することで、Azure portal に上記の詳細が表示されます。

## <a name="device-compliance-report-organizational"></a>デバイスのポリシー準拠レポート (組織)
デバイスのポリシー準拠レポートは本質的に広範囲であり、集計されたメトリクスを識別する目的で、従来の方法に近いやり方でデータが表示されます。 このレポートは、デバイスのポリシー準拠の全体像を見るために、大きなデータセットを扱えるように設計されています。 たとえば、デバイスのポリシー準拠を確認するためのデバイスのポリシー準拠レポートには、データセットの大きさに関係なくデータを広範囲で見ることができるように、デバイスのあらゆるポリシー準拠状態が表示されます。 このレポートでは、集計されたメトリクスが表示されて便利なだけでなく、レコードが詳細に分類されます。 このレポートは、レポートにフィルターを適用し、[レポートの生成] ボタンを選択することで生成できます。 これでデータが更新され、集計データを構成する個々のレコードを表示できる最新の状態が表示されます。 新しいフレームワークのほとんどのレポートと同様に、これらのレコードは並べ替えたり、検索したりして必要な情報だけを表示できます。 

生成されたデバイスの状態レポートは次の手順で表示できます。
1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. レポートの概要を表示する **[レポート]** を選択します。
3. **[デバイスのポリシー準拠]** を選択します。
4. **[対応状態]** 、 **[OS]** 、 **[所有権]** フィルターを選択し、レポートの内容を絞り込みます。
5. **[レポートの生成]** (または **[再生成]** ) をクリックし、最新のデータを取得します。

    ![デバイスのポリシー準拠レポート](./media/intune-reports/intune-reports-02a.png)

    > [!NOTE]
    > この**レポートのポリシー準拠**レポートには、レポートが最後に生成された時刻のタイム スタンプが表示されます。 

関連情報については、「[Intune で条件付きアクセスによる Microsoft Defender ATP のコンプライアンスを強制する](~/protect/advanced-threat-protection.md)」を参照してください。

## <a name="reports-summary"></a>レポートの概要 

デバイスのポリシー準拠レポートは、**レポート** ワークロードで概要レポートとして入手できます。 デバイスのポリシー準拠レポートは次の手順で表示します。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. レポートの概要を表示する **[レポート]** を選択します。

    ![Intune レポートの概要](./media/intune-reports/intune-reports-01.png)

## <a name="device-compliance-trend-report-historical"></a>デバイスのポリシー準拠傾向レポート (履歴)
デバイスのポリシー準拠傾向レポートは多くの場合、デバイスのポリシー準拠の長期的傾向を確認する目的で、管理者や設計者によって使用されます。 集計されたデータが一定期間にわたって表示されるため、将来の投資を決定する、プロセスを改善する、異常が見つかった場合に調査を促す目的で役立ちます。 フィルターを適用し、特定の傾向を表示することもできます。 このレポートから提供されるデータは現在のテナント状態のスナップショットです (ほぼリアルタイム)。 

デバイスのポリシー準拠傾向のためのデバイスのポリシー準拠傾向レポートには、一定期間にわたってデバイスのポリシー準拠状態の傾向が表示されます。 コンプライアンス ピークの発生箇所を突き止め、適宜、時間と労力を集中させることができます。

**傾向**レポートは次の手順で表示できます。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[レポート]** 、 **[傾向]** の順に選択し、60 日間にわたるデバイスのポリシー準拠傾向を表示します。

    ![Intune 傾向レポート](./media/intune-reports/intune-reports-03.png)

## <a name="azure-monitor-integration-reports-specialist"></a>Azure Monitor 統合レポート (スペシャリスト)
独自のレポートをカスタマイズし、必要なデータを得ることができます。 レポートに含まれるデータは任意で、[Log Analytics](reports.md#log-analytics) と [Azure Monitor ブック](reports.md#workbooks)を使用することで、[Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) から利用できます。 これらのソリューションでは、カスタム クエリを作成したり、アラートを構成したり、自分が望む方法でデバイスのポリシー準拠データを表示するダッシュボードを作成したりできます。 また、自分の Azure ストレージ アカウントにアクティビティ ログを保存したり、[セキュリティ情報イベント管理 (SIEM) ツール](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)を利用してレポートと統合したり、レポートを Azure AD アクティビティ ログに関連付けたりできます。 Azure Monitor ブックはダッシュボードのインポートと併用し、カスタムのレポート ニーズのために使用できます。

> [!NOTE]
> 複雑なレポート機能を利用するには、Azure サブスクリプションが必要です。

サンプルのスペシャリスト レポートは、デバイスの所有権データをカスタム レポートのプラットフォーム登録データに関連付けます。 そうすると、このカスタム レポートは Azure Active Directory ポータルの既存のダッシュボードに表示できます。

カスタム レポートは次の手順で作成し、表示できます。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[レポート]** 、 **[診断設定]** の順に選択して[診断設定](reports.md#diagnostic-settings)を追加します。

    ![Intune レポートの概要](./media/intune-reports/intune-reports-04.png)

3. **[診断設定を追加する]** をクリックし、 **[診断設定]** ウィンドウを表示します。 
4. 診断設定の**名前**を追加します。 
5. **[Log Analytics への送信]** と **[DeviceComplianceOrg]** 設定を選択します。

    ![Intune レポートの概要](./media/intune-reports/intune-reports-04a.png)

6. **[Save]** (保存) をクリックします。
7. 次に、 **[ログ分析]** を選択し、[Log Analytics](reports.md#log-analytics) を利用して新しいログ クエリを作成して実行します。

   ![Log Analytics - ログ クエリ](./media/intune-reports/intune-reports-05.png)

8. **[ブック]** を選択し、[Azure Monitor ブック](reports.md#workbooks)を使用して対話型レポートを作成するか、開きます。

   ![ブック - 対話型レポート](./media/intune-reports/intune-reports-07.png)

### <a name="diagnostic-settings"></a>診断設定
各 Azure リソースには、独自の診断設定が必要です。 診断設定により、リソースについて次のものが定義されます。

- 設定で定義される、宛先に送信されるログとメトリック データのカテゴリ。 利用できるカテゴリはリソースの種類によって異なります。
- ログを送信する 1 つまたは複数の宛先。 現在の宛先には、Log Analytics ワークスペース、Event Hubs、Azure Storage が含まれます。
- Azure Storage に格納されているデータの保持ポリシー。

1 つの診断設定でいずれかの宛先を定義できます。 複数の種類の宛先にデータを送信する場合 (たとえば、2 つの異なる Log Analytics ワークスペース)、複数の設定を作成します。 各リソースには最大 5 つの診断設定を設定することができます。

診断設定の詳細については、「[Azure でプラットフォーム ログとメトリックを収集するための診断設定を作成する](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-settings)」を参照してください。

### <a name="log-analytics"></a>ログ分析
Log Analytics は、ログ クエリを作成し、クエリの結果を対話式で分析するための Azure portal の主要ツールです。 ログ クエリが Azure Monitor の別の場所で使用されている場合でも、通常、まず、Log Analytics を使用してクエリを作成し、テストします。 Log Analytics の使用とログ クエリの作成に関する詳細については、「[Azure Monitor のログ クエリの概要](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview)」を参照してください。 

### <a name="workbooks"></a>ブック
ブックでは、テキスト、分析クエリ、Azure メトリックス、パラメーターが、高機能の対話型レポートに結合されます。 ブックは、同じ Azure リソースにアクセスできる他のチーム メンバーが編集できます。 ブックの詳細については、[Azure Monitor ブック](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks)に関するページを参照してください。 また、ブック テンプレートを使用して操作したり、投稿したりできます。 詳細については、「[Azure Monitor Workbook テンプレート](https://go.microsoft.com/fwlink/?linkid=867045)」を参照してください。

## <a name="next-steps"></a>次のステップ 

次のテクノロジについて学習してください。
- [ブログ - Microsoft Intune レポート フレームワーク](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553)
- [Azure Monitor](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-activity-logs-azure-monitor)
- [Log Analytics とは](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview#what-is-log-analytics)
- [ログ クエリ](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview)
- [Azure Monitor で Log Analytics の使用を開始する](https://docs.microsoft.com/azure/azure-monitor/log-query/get-started-portal)
- [Azure Monitor ブック](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks)
- [セキュリティ情報とイベント管理 (SIEM) ツール](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)
