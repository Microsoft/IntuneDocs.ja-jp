---
title: Microsoft Intune を使用して Azure Monitor にログをルーティングする - Azure | Microsoft Docs
description: '[診断設定] を使用して、Microsoft Intune の監査ログと操作ログを Azure ストレージ アカウント、イベントハブ、または Log Analytics に送信します。 データを保持する期間を選択し、さまざまなサイズのテナントについて見積もりコストを確認します。'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 95191d64-9895-4f2e-8c5b-f0e85be086d8
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66acf4d8b88097c3262f44493ab72b3900781eed
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504968"
---
# <a name="send-log-data-to-storage-event-hubs-or-log-analytics-in-intune-preview"></a>Intune でストレージ、イベントハブ、または Log Analytics にログ データを送信する (プレビュー)

Microsoft Intune には、お客様の環境に関する情報を提供する組み込みのログがあります。

- **監査ログ**には、Intune で発生したさまざまなイベントまたはタスクの詳細が表示されます。
- **操作ログ (プレビュー)** には、登録に成功した (または失敗した) ユーザーとデバイスの詳細、およびコンプライアンス非対応のデバイスの詳細が表示されます。
- **デバイス コンプライアンス組織ログ (プレビュー)** には、Intune のデバイス コンプライアンスに関する組織レポート、およびコンプライアンス非準拠のデバイスの詳細が表示されます。

これらのログは、ストレージ アカウント、イベント ハブ、Log Analytics などの Azure Monitor サービスに送信することもできます。 具体的には次のことができます。

* Intune ログを Azure ストレージ アカウントにアーカイブしてデータを保持するか、一定時間アーカイブする。
* Intune ログを Azure イベント ハブにストリームし、Splunk や QRadar などの一般的なセキュリティ情報およびイベント管理 (SIEM) ツールを使用して分析する。
* Intune ログをイベント ハブにストリームして、独自のカスタム ログ ソリューションと統合する。
* Intune ログを Log Analytics に送信して、接続されているデータの高度な視覚化、監視、および警告を実現する。

このような機能は、Intune の**診断設定**の一部です。

この記事では、 **[診断設定]** を使用してログ データをさまざまなサービスに送信する方法について説明し、例とコストの見積もりを示し、よく寄せられる質問に回答します。 この機能を有効にすると、選択した Azure Monitor サービスにログがルーティングされます。

## <a name="prerequisites"></a>必要条件

この機能を使用するには、以下が必要です。

* Azure サブスクリプション:Azure サブスクリプションをお持ちでない場合は、[無料試用版にサインアップ](https://azure.microsoft.com/free/)することができます。
* Azure 内の Microsoft Intune 環境 (テナント)
* Intune テナントの**全体管理者**または **Intune サービス管理者**であるユーザー。

監査ログ データをルーティングする場所によっては、次のいずれかのサービスが必要になります。

* *ListKeys* アクセス許可を持つ [Azure ストレージ アカウント](https://docs.microsoft.com/azure/storage/common/storage-account-overview)。 BLOB ストレージ アカウントではなく、一般的なストレージ アカウントを使用することをお勧めします。 ストレージの価格情報については、[Azure Storage 料金計算ツール](https://azure.microsoft.com/pricing/calculator/?service=storage)のページを参照してください。 
* サードパーティ製ソリューションと統合するための [Azure イベント ハブ名前空間](https://docs.microsoft.com/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace)。
* Log Analytics にログを送信するための [Azure Log Analytics ワークスペース](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace)。

## <a name="send-logs-to-azure-monitor"></a>ログを Azure Monitor に送信する

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[監視]** で **[診断設定]** を選択します。 初めて開いたときに有効にします。 それ以外の場合、設定を追加します。

    ![Intune の [診断設定] を有効にして、Azure Monitor にログを送信する](./media/review-logs-using-azure-monitor/diagnostics-settings-turn-on.png)

3. 次のプロパティを入力します。

    - **名前**: 診断設定の名前を入力します。 この設定には、入力したすべてのプロパティが含まれます。 たとえば、「`Route audit logs to storage account`」と入力します。
    - **[ストレージ アカウントへのアーカイブ]** :ログ データを Azure ストレージ アカウントに保存します。 データを保存またはアーカイブする場合は、このオプションを使用します。

        1. このオプションを選択し、 **[構成]** を選択します。 
        2. 一覧から既存のストレージ アカウントを選択し、 **[OK]** を選択します。

    - **[イベント ハブへのストリーム]** :ログを Azure イベント ハブにストリームします。 Splunk や QRadar などの SIEM ツールを使用してログ データを分析する場合は、このオプションを選択します。

        1. このオプションを選択し、 **[構成]** を選択します。 
        2. 一覧から既存のイベント ハブ名前空間とポリシーを選択し、 **[OK]** を選択します。

    - **[Log Analytics への送信]** :Azure Log Analytics にデータを送信します。 ログの視覚化、監視、アラートを使用する場合は、このオプションを選択します。

        1. このオプションを選択し、 **[構成]** を選択します。 
        2. 新しいワークスペースを作成し、ワークスペースの詳細を入力します。 または、一覧から既存のワークスペースを選択し、 **[OK]** を選択します。

            このような設定の詳細については、[Azure Log Analytics ワークスペース](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace)に関するページを参照してください。

    - **[ログ]**  >  **[AuditLogs]** :[Intune 監査ログ](../monitor-audit-logs.md)をストレージ アカウント、イベント ハブ、または Log Analytics に送信するには、このオプションを選択します。 監査ログには、Intune で変更を生成したすべてのタスクの履歴 (誰がいつ行ったのかなど) が表示されます。

      ストレージ アカウントの使用を選択した場合は、データを保持する日数 (リテンション期間) も入力します。 データを永続的に保持するには、 **[リテンション期間 (日数)]** を `0` (ゼロ) に設定します。

    - **[ログ]**  >  **[OperationalLogs]** :操作ログ (プレビュー) には、Intune に登録したユーザーとデバイスの成功または失敗と、コンプライアンス非対応のデバイスの詳細が表示されます。 登録ログをストレージ アカウント、イベント ハブ、または Log Analytics に送信するには、このオプションを選択します。

      ストレージ アカウントの使用を選択した場合は、データを保持する日数 (リテンション期間) も入力します。 データを永続的に保持するには、 **[リテンション期間 (日数)]** を `0` (ゼロ) に設定します。

      > [!NOTE]
      > 操作ログはプレビュー段階です。 操作ログに含まれる情報など、フィードバックを提供するには、[UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback) にアクセスしてください。

    - **LOG** > **DeviceComplianceOrg**:デバイス コンプライアンス組織ログ (プレビュー) には、Intune のデバイス コンプライアンスに関する組織レポート、およびコンプライアンス非準拠のデバイスの詳細が表示されます。 コンプライアンス ログをストレージ アカウント、イベント ハブ、または Log Analytics に送信するには、このオプションを選択します。

      ストレージ アカウントの使用を選択した場合は、データを保持する日数 (リテンション期間) も入力します。 データを永続的に保持するには、 **[リテンション期間 (日数)]** を `0` (ゼロ) に設定します。
 
      > [!NOTE]
      > デバイス コンプライアンス組織ログはプレビューの段階にあります。 レポートに含まれる情報など、フィードバックを提供するには、[UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback) にアクセスしてください。

    完了すると、設定は次のようになります。 

    ![Intune 監査ログが Azure ストレージ アカウントに送信されるサンプル画像](./media/review-logs-using-azure-monitor/diagnostics-settings-example.png)

4. 変更内容を**保存**します。 一覧に設定が表示されます。 作成された後は、 **[設定の編集]**  >  **[保存]** を選択して設定を変更できます。

## <a name="use-audit-logs-throughout-intune"></a>Intune 全体で監査ログを使用する

登録、コンプライアンス、構成、デバイス、クライアント アプリなど、Intune の他の部分で監査ログをエクスポートすることもできます。

たとえば、デバイスのコンプライアンスを使用するときに監査ログをエクスポートするには、次の手順を実行します。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイス コンプライアンス]**  >  **[監視]**  >  **[監査ログ]** の順に選択します。

    ![Intune データを Azure Monitor ストレージ、イベント ハブ、または分析にルーティングする監査ログを選択する](./media/review-logs-using-azure-monitor/audit-logs-under-monitor-in-compliance.png)

3. **[データ設定のエクスポート]** を選択します。 有効になっていない場合は、 **[診断設定]** をオンにできます。 また、「[ログを Azure Monitor に送信する](#send-logs-to-azure-monitor)」 (この記事内) で説明されているように、ログの送信先を選択することもできます。

## <a name="cost-considerations"></a>コストの考慮事項

Microsoft Intune ライセンスを既にお持ちの場合は、ストレージ アカウントとイベント ハブを設定するために Azure サブスクリプションが必要です。 通常、Azure サブスクリプションは無料です。 ただし、アーカイブ用のストレージ アカウントやストリーム用のイベント ハブなど、Azure のリソース使用には料金がかかります。 データやコストの合計は、テナントの規模によって変わります。

### <a name="storage-size-for-activity-logs"></a>アクティビティ ログのストレージ サイズ

各監査ログ イベントでは、データ ストレージに約 2 KB が使用されます。 ユーザー数が 100,000 のテナントの場合、1 日に約 150 万個のイベントが発生する可能性があります。 1 日に約 3 GB のデータ ストレージが必要になる可能性があります。 通常、書き込みは 5 分単位のバッチで行われるため、1 か月あたり約 9,000 個の書き込み操作が予想されます。

次の表は、テナントの規模に応じたコスト見積もりを示しています。 また、少なくとも 1 年間のデータ保持のために、米国西部の汎用 v2 ストレージ アカウントも含まれています。 ログについて予想されるデータ量の見積もりを取得するには、[Azure Storage 料金計算ツール](https://azure.microsoft.com/pricing/details/storage/blobs/)を使用します。

**100,000 ユーザーの監査ログ**

| | |
|---|---|
|1 日あたりのイベント| 150 万|
|1 か月あたりの推定データ量| 90 GB|
|1 か月あたりの推定コスト (USD)| $1.93|
|1 年あたりの推定コスト (USD)| $23.12|

**1,000 ユーザーの監査ログ**

| | |
|---|---|
|1 日あたりのイベント| 15,000|
|1 か月あたりの推定データ量| 900 MB|
|1 か月あたりの推定コスト (USD)| $0.02|
|1 年あたりの推定コスト (USD)| $0.24|

### <a name="event-hub-messages-for-activity-logs"></a>アクティビティ ログのイベント ハブ メッセージ

通常、イベントは 5 分間隔でバッチ処理され、その時間枠内のすべてのイベントを含む単一のメッセージとして送信されます。 イベント ハブ内のメッセージの最大サイズは 256 KB です。 時間枠内のすべてのメッセージの合計サイズがその量を超えると、複数のメッセージが送信されます。

たとえば、ユーザーが 100,000 人を超える大規模なテナントの場合、通常、1 秒間に約 18 個のイベントが発生します。 これは、5 分ごとに 5,400 イベント (300 秒 x 18 イベント) に相当します。 監査ログはイベントごとに約 2 KB です。 これは 10.8 MB のデータに相当します。 そのため、この 5 分間隔で 43 個のメッセージがイベント ハブに送信されます。

次の表は、イベント データの量に応じた、米国西部の基本的なイベント ハブの 1 か月あたりの推定コストを示します。 ログについて予想されるデータ量の見積もりを取得するには、[イベント ハブ料金計算ツール](https://azure.microsoft.com/pricing/details/event-hubs/)を使用します。

**100,000 ユーザーの監査ログ**

| | |
|---|---|
|イベント/秒| 18|
|5 分間隔ごとのイベント| 5,400|
|間隔あたりの量| 10.8 MB|
|間隔あたりのメッセージ| 43|
|1 か月あたりのメッセージ| 371,520|
|1 か月あたりの推定コスト (USD)| $10.83|

**1,000 ユーザーの監査ログ**

| | |
|---|---|
|イベント/秒|0.1 |
|5 分間隔ごとのイベント| 52|
|間隔あたりの量|104 KB |
|間隔あたりのメッセージ|1 |
|1 か月あたりのメッセージ|8,640 |
|1 か月あたりの推定コスト (USD)|$10.80 |

### <a name="log-analytics-cost-considerations"></a>Log Analytics コストの考慮事項

Log Analytics ワークスペースの管理に関連するコストを確認するには、[Log Analytics でデータ量とリテンション期間を制御することでコストを管理する方法](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage)に関するページを参照してください。

## <a name="frequently-asked-questions"></a>よく寄せられる質問

ここでは、よく寄せられる質問に対して回答を示し、Azure Monitor での Intune ログに関する既知の問題について説明します。

### <a name="which-logs-are-included"></a>どのログが含まれていますか。

監査ログと操作 (プレビュー) ログは、いずれもこの機能を使用したルーティングのために使用できます。

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-event-hub"></a>アクションの後、対応するログがイベント ハブに表示されるのはいつですか。

通常、ログはアクションが実行されてから数分以内にイベント ハブに表示されます。 詳細については、[Azure Event Hubs の概要](https://docs.microsoft.com/azure/event-hubs/)に関するページを参照してください。

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-storage-account"></a>アクションの後、対応するログがストレージ アカウントに表示されるのはいつですか。

Azure ストレージ アカウントの場合、待ち時間はアクションの実行後 5 分から 15 分です。

### <a name="what-happens-if-an-administrator-changes-the-retention-period-of-a-diagnostic-setting"></a>管理者が診断設定の保持期間を変更するとどうなりますか。

新しいアイテム保持ポリシーは、変更後に収集されたログに適用されます。 ポリシーの変更前に収集されたログは影響を受けません。

### <a name="how-much-does-it-cost-to-store-my-data"></a>データの保存にかかるコストはどのくらいですか。

ストレージ コストは、ログのサイズと選択した保持期間によって変わります。 生成されるログの量に応じたテナントの推定コストの一覧については、「[アクティビティ ログのストレージ サイズ](#storage-size-for-activity-logs)」(この記事) を参照してください。

### <a name="how-much-does-it-cost-to-stream-my-data-to-an-event-hub"></a>データをイベント ハブにストリームするためにかかるコストはどのくらいですか。

ストリーム コストは、1 分間に受信するメッセージ数によって変わります。 メッセージ数に基づくコストの計算方法とコスト見積もりの詳細については、「[アクティビティ ログのイベント ハブ メッセージ](#event-hub-messages-for-activity-logs)」(この記事) を参照してください。

### <a name="how-do-i-integrate-intune-audit-logs-with-my-siem-system"></a>Intune の監査ログを SIEM システムと統合するにはどうすればよいですか。

Azure Monitor を Event Hubs と共に使用して、ログを SIEM システムにストリームします。 まず、[ログをイベント ハブにストリーム](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)します。 次に、構成したイベント ハブを使用して [SIEM ツールを設定](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#access-data-from-your-event-hub)します。 

### <a name="what-siem-tools-are-currently-supported"></a>現在サポートされている SIEM ツールは何ですか。

現在、Azure Monitor は、[Splunk](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-integrate-activity-logs-with-splunk)、QRadar、および [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory) でサポートされています (新しい Web サイトが開きます)。 コネクタのしくみの詳細については、「[外部ツールで使用する Azure 監視データのイベント ハブへのストリーミング](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs)」を参照してください。

### <a name="can-i-access-the-data-from-an-event-hub-without-using-an-external-siem-tool"></a>外部の SIEM ツールを使用せずにイベント ハブのデータにアクセスできますか。

はい。 カスタム アプリケーションからログにアクセスするには、[Event Hubs API](https://docs.microsoft.com/azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph) を使用できます。

### <a name="what-data-is-stored"></a>どのデータが保存されますか。

Intune では、パイプラインを介して送信されたデータは保存されません。 Intune では、テナントの権限でデータが Azure Monitor パイプラインにルーティングされます。 詳細については、「[Azure Monitor の概要](https://docs.microsoft.com/azure/azure-monitor/overview)」を参照してください。

## <a name="next-steps"></a>次の手順

* [アクティビティ ログをストレージ アカウントにアーカイブする](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-azure-monitor-route-logs-to-storage-account)
* [アクティビティ ログをイベント ハブにルーティングする](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)
* [アクティビティ ログを Log Analytics と統合する](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)
