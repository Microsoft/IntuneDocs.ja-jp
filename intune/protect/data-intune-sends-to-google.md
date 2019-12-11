---
title: Intune から Google に送られるデータ
titleSuffix: Microsoft Intune
description: Intune から Google に送られるデータの一覧。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f6ab8a4e8e46373a536949c13ceaebb267f34cd
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504458"
---
# <a name="data-intune-sends-to-google"></a>Intune から Google に送られるデータ

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

デバイスで Android エンタープライズ デバイスの管理が有効になっている場合、Microsoft Intune は Google との接続を確立し、ユーザーとデバイスの情報を Google と共有します。 Microsoft Intune が接続を確立する前に、Google アカウントを作成する必要があります。

次の表は、デバイスでデバイス管理が有効になっているときに Microsoft Intune が Google に送信するデータの一覧です。


| Google に送信されるデータ | 説明 | 使用目的 | 例 |
|:---:|:---:|:---:|:---:|
| EnterpriseId | Gmail アカウントを Intune にバインドするときに、Google で開始されます。 | Intune と Google の間の通信に使用されるプライマリ識別子。  この通信には、ポリシーの設定、デバイスの管理、Android エンタープライズと Intune のバインド/バインド解除が含まれます。 | 一意の識別子 (形式の例:LC04eik8a6) |
| ポリシーの本文 | 新しいアプリや構成ポリシーを保存するときに、Intune で開始されます。 | デバイスにポリシーを適用します。 | アプリケーションまたは構成ポリシーのすべての構成済み設定のコレクションです。 ポリシーの一部として提供される場合、ネットワーク名、アプリケーション名、アプリ固有の設定など、顧客情報が含まれる可能性があります。 |
| デバイス データ | 仕事用プロファイルのデバイスのシナリオは、Intune への登録から始まります。 マネージド デバイスのデバイスのシナリオは、Google への登録から始まります。 | Intune と Google 間で、ポリシーの適用、デバイスの管理、一般的なレポート処理など、さまざまな操作のためにデバイス データ情報が送信されます。 | **デバイス名を表す一意の識別子。** 例: enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**ユーザー名を表す一意の識別子。** 例:Enterprises/LC04ebru7b/users/116838519924207449711<br>**デバイスの状態。** 例:アクティブ、無効、プロビジョニング。<br>**コンプライアンスの状態。** 例:設定はサポートされていません。必要なアプリがありません<br>**ソフトウェア情報。** 例: ソフトウェアのバージョン、パッチ レベル。<br>**ネットワーク情報。** 例:IMEI、MEID、WifiMacAddress<br>**デバイスの設定。** 例:暗号化レベルの情報、デバイスが不明なアプリを許可するかどうかの情報。<br> JSON メッセージの例については後述します。 |
| newPassword | Intune で開始されます。 | デバイスのパスコードをリセットします。 | 新しいパスワードを表す文字列。 |
| Google ユーザー | Google | 仕事用プロファイル (BYOD) シナリオの場合に仕事用プロファイルを管理します。 | リンクされている Gmail アカウントを表す一意の識別子。 例:114223373813435875042 |
| アプリケーション データ | アプリケーション ポリシーを保存するときに Intune で開始されます。 |  | アプリケーション名の文字列。 例: app:com.microsoft.windowsintune.companyportal |
| エンタープライズ サービス アカウント | Intune の要求時に Google で開始されます。 | このユーザーが関係するトランザクションに対して Intune と Google 間の認証に使用されます。 | 複数の部分に分かれています。<br> **エンタープライズ ID**: 以前に説明されています。<br>**UPN**: ユーザーの代理で認証に使用される UPN が生成されます。<br>例: w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**キー**:認証要求で使用され、暗号化されてサービスに格納された Base64 でエンコードされた BLOB ですが、次のような BLOB です。<br> ユーザーのキーを表す一意の識別子<br>例: a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |


Microsoft Intune で Android エンタープライズ デバイス管理の使用を停止してデータを削除するには、Microsoft Intune の Android エンタープライズ デバイス管理を無効にし、Google アカウントも削除する必要があります。 詳細については、Google アカウントのアカウントの管理方法を参照してください。


