---
title: アプリケーションの展開に関する問題のトラブルシューティング
description: このトピックは、Microsoft Intune でのアプリの展開の問題を解決するために役立ちます。
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 09/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ec4116a54377b3db7ea58d8e24e49c44edf73a7a
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="troubleshoot-app-deployment-problems-in-microsoft-intune"></a>Microsoft Intune のアプリ展開に関する問題のトラブルシューティング

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune でのアプリの展開と管理に関して問題がある場合は、ここから始めてください。 このトピックでは、発生する可能性がある一般的な問題とその解決策が示されています。

## <a name="common-app-deployment-error-codes"></a>アプリ展開時の一般的なエラー コード

|エラー コード|問題|推奨される解決策|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (クライアント エラー)|このアプリケーションをインストールするには、サイドローディング対応のシステムが必要です。|アプリ パッケージを信頼できる署名を使用して署名し、AllowAllTrustedApps ポリシーを有効にしたドメインに参加するデバイス、または AllowAllTrustedApps ポリシーを有効にした Windows サイドローディング ライセンスを持つデバイスにインストールします。|
|0x80073CF0|パッケージを開くことができませんでした。|次の原因が考えられます。<br /><br />-   パッケージが署名されていません。<br />-   発行元の名前が、署名している証明書の件名と一致しません。<br /><br />詳細については、AppxPackagingOM イベント ログを確認してください。|
|0x80073CF3|パッケージの更新、依存関係、または競合の検証に失敗しました|次の原因が考えられます。<br /><br />-   受信パッケージがインストール済みのパッケージと競合しています。<br />-   指定したパッケージの依存関係が見つかりません。<br />-   パッケージは正しいプロセッサ アーキテクチャをサポートしていません。<br /><br />詳細については、AppXDeployment-Server イベント ログを確認してください。|
|0x80073CFB|指定したパッケージは既にインストールされており、パッケージの再インストールがブロックされます|既にインストールされているパッケージと同じではないパッケージをインストールしようとすると、このエラーが発生することがあります。 デジタル署名がパッケージにも含まれることを確認します。 パッケージを再ビルドまたは再署名すると、パッケージは以前にインストールしたパッケージとビット単位で同じではなくなります。 このエラーを修正するには、次のように 2 つの選択肢が考えられます。<br /><br />-   アプリのバージョン番号を増やして、パッケージの再ビルドと再署名を行います。<br />-   システムのすべてのユーザーの古いパッケージを削除してから、新しいパッケージをインストールします。|
|0x87D1041C|アプリケーションがインストールされましたが、検出されません。|- アプリは Intune によって正しくデプロイされ、(おそらくエンド ユーザーにより) その後、アンインストールされました。 ユーザーは、ポータル サイトからアプリを再インストールするように指示されます。 デバイスが次回チェックインするときに、必要なアプリが自動的に再インストールされます。|

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Microsoft ストア アプリのトラブルシューティング

トピック「[Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx)」 (Microsoft ストア アプリのパッケージ化、展開、およびクエリのトラブルシューティング) に記載されている情報は、Microsoft ストアからアプリをインストールする際に発生する可能性がある一般的な問題のトラブルシューティングで役に立ちます (Intune を使用する場合、または他の手段を使用する場合に関係なく)。

## <a name="troubleshooting-app-deployment-to-pcs-managed-by-the-intune-software-client"></a>Intune ソフトウェア クライアントによって管理されている PC へのアプリ展開で発生した問題のトラブルシューティング
Intune ソフトウェア クライアントによって管理されている PC にアプリを展開する際に問題が発生した場合、次の 2 つのログ ファイルがトラブルシューティングに役立ちます。
- %ProgramFiles%\Microsoft\OnlineManagement\Logs folder
- %ProgramFiles%\Microsoft\OnlineManagement\Updates\ReportingEvents.log

さらに、Intune のサポート事例を開く必要がある場合は、これらのログを Microsoft に送信することも効果的です。


### <a name="next-steps"></a>次の手順
このトラブルシューティング情報を使っても問題が解決しない場合は、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」の説明に従って Microsoft サポートにお問い合わせください。
