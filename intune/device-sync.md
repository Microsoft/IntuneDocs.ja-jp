---
title: デバイスを Microsoft Intune と同期する - Azure | Microsoft Docs
description: 登録または管理されているデバイスを Microsoft Intune と同期して最新のポリシーとアクションを取得します。 Azure Portal を使用して同期するための手順を示し、再試行できるエラー コードを一覧表示します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6f13e00abad5b48dcd7996cf9df1cc5756f250d3
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57388108"
---
# <a name="sync-devices-to-get-the-latest-policies-and-actions-with-intune"></a>デバイスを Intune と同期して最新のポリシーとアクションを取得する


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

デバイスの**同期**のアクションは、選択したデバイスの Intune との即座の同期を強制的に実行します。 チェックインしたデバイスには、それに対して保留中のアクションまたはポリシーが即座に割り当てられます。 この機能により、次のスケジュールされたチェックインを待たずに、割り当てられたポリシーの検証およびトラブルシューティングを即座に実行できるようになります。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="sync-a-device"></a>デバイスを同期する

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、 **[Intune]** をフィルターとして適用し、 **[Microsoft Intune]** を選択します。 
3. **Intune** で、 **[デバイス]**  >  **[すべてのデバイス]** の順に選択します。
4. 管理するデバイスの一覧で、デバイスを選択して、 **[詳細]** 、 **[同期]** の順に選択します。
5. 確定するには、 **[はい]** を選択します。

同期操作の状態を表示するには、 **[デバイス]**  >  **[デバイス アクション]** の順に選択します。

標準的な Intune ポリシーのチェックイン頻度は、[サイクル時間の更新](device-profiles.md)で確認することができます。

## <a name="retryable-error-codes"></a>再試行可能なエラー コード

管理者が **[同期]** デバイス アクションを実行したときに、失敗したものの再試行可能なエラー コードが生成された iOS アプリおよび Android アプリは、引き続きデバイスで使用できます。 ただし、再試行不可能なエラー コードが生成されたアプリは、デバイスで使用できるようになるまでに 7 日間待機する必要があります。


| エラー コード  | 提案された説明 | 再試行可能 |
|---|---|---|
| 2016330898 | 原因不明のエラーが発生しました。 | [いいえ] |
| 2016330897 | Intune への接続がタイムアウトになりました。接続をリセットします。 | はい |
| 2016330896 | インターネットへの接続が失われました。 接続をリセットします。 | はい |
| 2016330895 | インターネットへの接続が失われました。 接続をリセットします。 | はい |
| 2016330894 | インターネットへの接続が失われました。 接続をリセットします。 | はい |
| 2016330893 | インターネットへの接続が失われました。 接続をリセットします。 | はい|
| 2016330892 | 海外ローミングが無効です。 | [いいえ]|
| 2016330891 | 通話中は、このデバイスの携帯データ ネットワーク接続にアクセスできません。 通話が終了するまでお待ちください。 | はい|
| 2016330890 | このデバイスの移動体通信ネットワークです。 この時点で、これらのデバイスを使用できませんでした。 | [いいえ]|
| 2016330889 | セキュリティで保護された接続に失敗しました。 接続をリセットします。 | はい|
| 2016330888 | サーバーの信頼評価に失敗しました。 | [いいえ]|

## <a name="next-steps"></a>次の手順

デバイスの[詳細を確認する](device-inventory.md)ことができます。
 
