---
title: iOS 用 Symantec Endpoint Protection Mobile が検出した脅威を解決する | Microsoft ドキュメント
description: iOS デバイスで検出された、セキュリティ上の脅威、ウイルス、アプリの脅威を解決する方法について説明します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b40595f0-a399-4aa1-aa6f-344c2a1cb883
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8353b704df7ebdc648e5b223b80e656ca05956a
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "55848680"
---
# <a name="resolve-a-threat-found-by-symantec-endpoint-protection-mobile"></a>Symantec Endpoint Protection Mobile で検出された脅威を解決する

Symantec Endpoint Protection (SEP) Mobile は Mobile Threat Defender サービスであり、Android デバイスの潜在的な脅威を識別します。 これらの脅威はポータル サイト アプリに報告され、非準拠に関する未解決の問題として示されます。 デバイスが非準拠であると識別された場合、以下を実行できない可能性があります。

* 会社の電子メールに接続する
* 会社の Wi-Fi に接続する
* SharePoint Online に接続する
* 企業ファイルを OneDrive に同期させる
* 会社のアプリにアクセスする

この記事では、SEP Mobile でセキュリティまたはアプリの脅威が検出された場合に、会社のリソースへのアクセスを回復する方法を説明します。  

## <a name="troubleshoot-a-virus-or-security-threat"></a>ウイルスやセキュリティ上の脅威をトラブルシューティングする

1. 会社の電子メールまたは Web サイトにアクセスしようとすると、次のスクリーンショットで示すようなメッセージが表示されます。 **デバイスの管理ポータル** リンクをタップして、[ポータル サイト Web サイト](https://portal.manage.microsoft.com/devices)を開きます。

    ![ポータル サイト Web サイトへのリンクと青色の [OK] ボタンを含む、Lookout for Work エラー メッセージのスクリーンショット例。](./media/mtd-go-to-device-management-portal-android.png)  

2. デバイスを選択します。  
3. デバイスの下に表示される警告を確認します。 SEP Mobile を開いてウイルスやセキュリティ上の脅威を解決するように指示されます。    

    ![SEP Mobile の警告を表示する、ポータル サイト デバイス ページのスクリーンショット例。](./media/CP-lookout-virus-banner-1808.png)

## <a name="troubleshoot-an-app-threat"></a>アプリの脅威をトラブルシューティングする

デバイスに対する脅威と考えられるアプリをインストールする場合、SEP Mobile アプリ内に通知が示されます。 影響を受けるアプリがデバイス上に残っている場合、会社のリソースにアクセスできなくなります。  

解決するには、SEP Mobile の脅威リストからアプリを選択します。 次に、画面上の指示に従って、アプリを削除してアンインストールします。  

サポートが必要な場合は、 会社のサポートに問い合わせてください。 連絡先の情報は、[会社のポータル Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)でわかります。   

