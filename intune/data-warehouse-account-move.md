---
title: Intune データ ウェアハウスのアカウント データを移動する
titlesuffix: Microsoft Intune
description: アカウントを移動するときに Intune データ ウェアハウス データをバックアップする方法について理解します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ee3ccbf9-82fc-4fbf-9d3d-8f05e431d090
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.openlocfilehash: 470bafba548c38870e57a545c4514459dde219b4
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189392"
---
# <a name="move-your-intune-data-warehouse-account-data"></a>Intune データ ウェアハウスのアカウント データを移動する 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

アカウントの移動を要求することで、データ センターを別の場所に変更することを要求します。 移動後、データ ウェアハウスはリセットされ、指定された移動開始日に基づいて、新しい場所でデータの記録が始まります。 以前のデータ ウェアハウス データをバックアップする場合は、アカウントが移動される**前に**以下の手順を完了してください。 ほとんどのデータ ウェアハウス テーブルにはデータが 30 日間保持されます。したがって、アカウントが移動されてから 30 日後にこれらのテーブルのデータ ギャップは利用できなくなります。 特定のテーブルの保有期間の詳細については、「[データ ウェアハウスのデータ モデル](reports-ref-data-model.md)」を参照してください。 

## <a name="back-up-your-data-warehouse-data"></a>データ ウェアハウス データをバックアップする 

データ ウェアハウス データをバックアップするには、次のようにデータ ウェアハウス API を使用して、データ ウェアハウス データを *.csv* ファイルに保存する必要があります。  

1. データ ウェアハウス API を初めて使用する場合は、「[REST クライアントを使用して Intune データ ウェアハウス API からデータを取得する](reports-proc-data-rest.md)」の記事に示されている 1 回限りのプロセスに従ってください。
2. 「[Access the Intune Data Warehouse with PowerShell](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/PowerShell)」 (PowerShell を使用して Intune データ ウェアハウスにアクセスする) というタイトルの PowerShell サンプルを使用して、CSV ファイルにすべてのデータをダウンロードします。 

## <a name="back-up-your-trend-charts-from-the-azure-portal"></a>Azure Portal からトレンド グラフをバックアップする

Azure Portal のビュー内の一部のトレンド グラフがリセットされます。 **[グラフ]** で次のスクリプトを実行することで、これらのグラフをバックアップすることができます。   

### <a name="terms--conditions-acceptance-reports"></a>使用条件への同意レポート
1. Azure Portal で、**[Microsoft Intune]** -> **[デバイスの登録]** -> **[使用条件]** の順に移動します。
2. **[使用条件]** の各項目について、**[同意レポート]**、**[エクスポート]** の順に選択します。
3. レポートをローカルに保存します。
 
### <a name="app-protection-reports"></a>アプリの保護レポート  
1. Azure portal で、**[Microsoft Intune]** -> **[クライアント アプリ]** -> **[アプリの保護の状態]** の順に移動します。
2. ダウンロード アイコン ( ⤓ ) をクリックして、各レポートを保存します。

### <a name="device-configuration-charts"></a>デバイス構成のグラフ 
1. Azure Portal で、**[Microsoft Intune]** -> **[DeviceConfiguration]** の順に移動します。
2. Microsoft [グラフ エクスプローラー](https://developer.microsoft.com/graph/graph-explorer)を使用して、グラフの背後にあるデータをダウンロードします。 
    - すべてのデバイスのすべてのデバイス構成プロファイルの展開ステータスについては、[デバイスの展開ステータス](https://graph.microsoft.com/beta/reports/deviceConfigurationDeviceActivity/content)に関するページを参照してください。

    - すべてのユーザーのすべてのデバイス構成プロファイルの展開ステータスについては、[ユーザーの展開ステータス](https://graph.microsoft.com/beta/reports/deviceConfigurationUserActivity/content)に関するページを参照してください。

    - プロファイルの展開ステータスについては、[展開ステータスの提供](https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations?$select=id,displayName,lastModifiedDateTime,deviceStatusOverview&$expand=deviceStatusOverview)に関するページを参照してください。
  
    > [!NOTE]
    > デバイスの構成と展開のステータス情報にアクセスするには、有効な認証トークンが必要です。

## <a name="device-enrollment-charts"></a>デバイス登録のグラフ
1. Azure Portal で、**[Microsoft Intune]** -> **[DeviceEnrollment]** の順に移動します。
2. Microsoft [グラフ エクスプローラー](https://developer.microsoft.com/graph/graph-explorer)を使用して、グラフの背後にあるデータをダウンロードします。
    - 登録ステータスの場合は、この[登録ステータス クエリ](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentFailureTrends()/content)をコピーして、[グラフ エクスプローラー](https://developer.microsoft.com/graph/graph-explorer)に貼り付けます。
    - 今週の上位の登録エラーの場合は、この[登録エラー クエリ](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentTopFailures(period=null)/content)をコピーして、[グラフ エクスプローラー](https://developer.microsoft.com/graph/graph-explorer)に貼り付けます。

    > [!NOTE]
    > デバイスの登録データにアクセスするには、有効な認証トークンが必要です。 

## <a name="after-a-data-warehouse-account-move"></a>データ ウェアハウス アカウントの移動後

データ ウェアハウス アカウントの移動後に、データ ウェアハウスがリセットされ、データが新しい場所に格納されていることが Intune に表示されます。 グラフとエクスポートのオプションがリセットされ、通知が表示されます。これをクリックすると、グラフがリセットされた理由を説明する記事に移動します。  

## <a name="data-warehouse-move-example"></a>データ ウェアハウスの移動例 

顧客 X は、2018 年 1 月 6 日にアカウントの移動を開始することを要求しています。 この要求に対する応答で、顧客は、以前のデータ ウェアハウスをバックアップする場合に実行する手順を詳しく説明するドキュメントを表示するリンクを受け取ります。 2018 年 1 月 6 日に、データ ウェアハウスとサポートされるグラフがリセットされ、新しいデータ センターでのデータの格納が開始されます。 

## <a name="next-steps"></a>次の手順

 - [週ごとにまとめた Intune の新機能](whats-new.md)を参照してください。 今後の変更、サービスに関する重要なお知らせ、過去のリリースに関する情報も確認できます。
 - [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)を参照してください。
