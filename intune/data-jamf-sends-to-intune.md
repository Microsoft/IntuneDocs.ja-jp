---
title: JAMF Pro から Intune に送られるデータ
titleSuffix: Microsoft Intune
description: Jamf Pro を統合して Intune で Mac を管理する場合に、Jamf Pro から Microsoft Intune に送られるデータの一覧を確認します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86f2f47322e668815d1ff37ce6c2de1e4d6cdc16
ms.sourcegitcommit: 99b74d7849fbfc8f5cf99cba33e858eeb9f537aa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2019
ms.locfileid: "68670891"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Jamf Pro から Intune に送られるデータ

Intune でエンドユーザーの Mac を管理する目的で [Jamf Pro](https://www.jamf.com) を使用するとき、Jamf Pro によって管理対象 macOS デバイスに関するインベントリ情報がキャプチャされます。 Jamf Pro は、Intune に次の情報をレポートします。

* デバイスの Azure AD ID
* JAMF のインベントリ状態 (過去 24 時間以内に Jamf Pro でチェックインされたコンピューターのインベントリ状態)
* OS のバージョン
* ユーザーの Azure AD ID
* 暗号化 (FileVault 2)
* Gatekeeper ステータス
* パスワード: 文字セットの最小数
* パスワードの有効期限 (日)
* パスワードの種類 - 簡易、英数字、または不明
* 自動ログインの防止
* 必要なパスコードの長さ
* パスワード: 再利用を防止する前のパスワードの数
* システム整合性の保護
* 最後のチェックイン時刻
* アーキテクチャの種類
* 使用可能な RAM スロット
* バッテリ容量
* ブート ROM
* バス速度
* キャッシュ サイズ
* デバイス名
* ドメイン参加
* Jamf ID
* MAC アドレス
* Make
* モデル
* モデル識別子
* NIC 速度
* コア数
* プロセッサ数
* OS
* プラットフォーム
* プロセッサ速度
* プロセッサの種類
* セカンダリ MAC アドレス
* シリアル番号
* SMC バージョン
* RAM 合計
* UDID
* ユーザーの電子メール


**[すべてのデバイス]** ビューで **[削除]** を選択することで、Intune コンソールから Jamf で管理されるデバイスを削除できます。 複数のデバイスを選択し、 **[削除]** をクリックすることで、デバイスの一括削除を有効にすることができます。

Jamf で管理されるデバイスの削除方法については、[Jamf Pro のドキュメント](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)を参照してください。[Jamf サポート](https://www.jamf.com/support/)にサポート チケットを提出して、さらなる支援を受けることもができます。 

