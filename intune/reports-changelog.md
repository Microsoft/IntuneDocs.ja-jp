---
title: "Intune データ ウェアハウスの変更ログ | Microsoft Docs"
description: "Intune のデータ ウェアハウス API の変更一覧。"
keywords: "Intune データ ウェアハウス"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6d675a36cd5ea4c11d755174bf2b0bbc5d4b18ec
ms.sourcegitcommit: 5279a0bb8c5aef79aa57aa247ad95888ffe5a12b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2017
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Intune データ ウェアハウス API の変更ログ

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

常に Intune データ ウェアハウスの最新の更新プログラムをインストールしてください。

## <a name="1710"></a>1710
_リリース日: 2017 年 11 月_

### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>ユーザー エンティティにデータ ウェアハウス データ モデルの最新のユーザー データが含まれている<!-- 1544273 -->

Intune データ ウェアハウス データ モデルの最初のバージョンでは、最近の Intune 履歴データのみが含まれていました。 レポートの作成者は、ユーザーの最新の状態をキャプチャできませんでした。 今回の更新プログラムでは、最新のユーザー データを使用して[**ユーザー エンティティ**](reports-ref-user.md)が設定されます。

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>データ ウェアハウス データ モデルの新しいエンティティ <!-- 1479526 --><!-- -->

 - [**UserDeviceAssociation**](reports-ref-user-device.md) というエンティティが追加されました。 **UserDeviceAssociation** には、組織内のユーザー デバイスの関連付けが含まれています。
 - [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md) というエンティティが追加されました。 **IntuneManagementExtension** には、バージョンやインストール状態などの情報を追跡するモバイル デバイスのエンティティが含まれます。

## <a name="next-steps"></a>次のステップ
 - [週ごとにまとめた Intune の新機能](whats-new.md)を参照してください。 今後の変更、サービスに関する重要なお知らせ、過去のリリースに関する情報も確認できます。 
 - [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)を参照してください。