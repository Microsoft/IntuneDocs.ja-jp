---
title: "Intune のネットワーク帯域幅の使用 | Microsoft Docs"
description: "Intune のネットワーク帯域幅の使用法"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: 5211d2222e5e8ef9328f60ed13f0146925194c5f
ms.lasthandoff: 04/26/2017


---

# <a name="intune-network-bandwidth-use"></a>Intune のネットワーク帯域幅の使用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

このガイダンスは、Intune 管理者が Intune サービスのネットワーク要件を理解するのに役立ちます。 帯域幅の要件およびプロキシの設定に必要な IP アドレスとポートの設定を理解できます。

## <a name="average-network-traffic"></a>ネットワーク トラフィックの平均
次の表は、各クライアントのネットワークで通信される一般的なコンテンツの概算のサイズと頻度を一覧にしたものです。

> [!NOTE]
> Intune サービスから提供される必要な更新プログラムとコンテンツをコンピューターとモバイル デバイスで確実に受信するためには、定期的にインターネットに接続する必要があります。 更新プログラムまたはコンテンツを受信するのにかかる時間は一定ではありませんが、ガイドラインとして、毎日、少なくとも 1 時間はインターネットに接続したままにしておく必要があります。

|コンテンツの種類|概算サイズ|頻度と詳細|
|----------------|--------------------|-------------------------|
|Intune クライアントのインストール<br /><br />**以下の要件が、Intune クライアントのインストールに追加されます**|125 MB|**1 回限り**<br /><br />クライアントのダウンロード サイズは、クライアント コンピューターのオペレーティング システムによって異なります。|
|クライアントの登録パッケージ|15 MB|**1 回限り**<br /><br />追加のダウンロードは、このコンテンツの種類の更新プログラムが存在する場合に発生することがあります。|
|Endpoint Protection エージェント|65 MB|**1 回限り**<br /><br />追加のダウンロードは、このコンテンツの種類の更新プログラムが存在する場合に発生することがあります。|
|Operations Manager エージェント|11 MB|**1 回限り**<br /><br />追加のダウンロードは、このコンテンツの種類の更新プログラムが存在する場合に発生することがあります。|
|ポリシー エージェント|3 MB|**1 回限り**<br /><br />追加のダウンロードは、このコンテンツの種類の更新プログラムが存在する場合に発生することがあります。|
|Microsoft Easy Assist によるリモート アシスタンス|6 MB|**1 回限り**<br /><br />追加のダウンロードは、このコンテンツの種類の更新プログラムが存在する場合に発生することがあります。|
|日常のクライアントの操作|6 MB|**毎日**<br /><br />Intune クライアントは、更新プログラムやポリシーを確認したり、クライアントの状態をサービスに報告したりするために、定期的に Intune サービスと通信します。|
|Endpoint Protection のマルウェア定義の更新|不定<br /><br />通常 40 KB ～ 2 MB|**毎日**<br /><br />最大で 1 日に 3 回。|
|Endpoint Protection エンジンの更新プログラム|5 MB|**毎月**|
|ソフトウェア更新プログラム|不定<br /><br />サイズは、展開する更新プログラムによって異なります。|**毎月**<br /><br />通常、ソフトウェアの更新プログラムのリリースは、毎月の第 2 火曜日です。<br /><br />新しく登録された、または、展開されたコンピューターは、以前にリリースされた更新プログラムのフル セットをダウンロードする間、多くのネットワーク帯域幅を使用することがあります。|
|Service Pack|不定<br /><br />サイズは、展開する各サービス パックによって異なります。|**随時**<br /><br />サービス パックを展開する時間に依存します。|
|ソフトウェアの配布|不定<br /><br />サイズは、展開するソフトウェアによって異なります。|**随時**<br /><br />ソフトウェアを展開する時間に依存します。|

## <a name="ways-to-reduce-network-bandwidth-use"></a>ネットワーク帯域幅の使用量を削減する方法
次の方法を使用して、Intune クライアントのネットワーク帯域幅の使用量を削減できます。

### <a name="use-a-proxy-server-to-cache-content-requests"></a>コンテンツ要求のキャッシュにプロキシ サーバーを使用する
コンテンツをキャッシュするプロキシ サーバーを使用して、重複するダウンロードを削減し、インターネットからコンテンツを要求するクライアントのネットワーク帯域幅の使用量を減らすことができます。

キャッシュを行うプロキシ サーバーは、ネットワーク上のクライアント コンピューターからの要求を受け取り、インターネットからコンテンツを取得して、HTTP 応答とバイナリのダウンロード両方をキャッシュできます。 サーバーは、キャッシュされた情報を使用して、Intune クライアント コンピューターからの後続の要求に応答します。

Intune クライアント用にコンテンツをキャッシュするプロキシ サーバーの一般的な設定を以下に示します。

|設定|推奨される値|説明|
|-----------|---------------------|-----------|
|キャッシュ サイズ|5 ～ 30 GB|この値は、ネットワークにあるクライアント コンピューターの台数と、使用する構成によって異なります。 ファイルが短時間で削除されないようにするには、環境のキャッシュのサイズを調整します。|
|キャッシュする個々のファイルのサイズ|950 MB|キャッシュ機能付きサーバーによっては、この設定がないものがあります。|
|キャッシュするオブジェクトの種類|HTTP<br /><br />HTTPS<br /><br />BITS|Intune パッケージは、HTTP 経由でバックグラウンド インテリジェント転送サービス (BITS) のダウンロードで取得される CAB ファイルです。|
コンテンツをキャッシュするプロキシ サーバーの仕様に関する詳細については、使用するプロキシ サーバー ソリューションのドキュメントを参照してください。

### <a name="use-background-intelligent-transfer-service-on-computers"></a>コンピューターで、バック グラウンド インテリジェント転送サービスを使用する
Intune は、Windows コンピューターでのバックグラウンド インテリジェント転送サービス (BITS) の使用をサポートしています。BITS を使用して、構成する時間中に使用するネットワーク帯域幅を削減できます。 BITS のポリシーは、Intune エージェント ポリシーの **[ネットワーク帯域幅]** ページで構成できます。

BITS と Windows コンピューターの詳細については、TechNet ライブラリの「[バックグラウンド インテリジェント転送サービス](http://technet.microsoft.com/library/bb968799.aspx)」を参照してください。

### <a name="use-branchcache-on-computers"></a>コンピューターで BranchCache を使用する
Intune クライアントは、BranchCache を使用してワイド エリア ネットワーク (WAN) トラフィックを削減できます。 クライアントとしてサポートされる次のオペレーティング システムでも、BranchCache がサポートされます。

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

BranchCache を使用するには、クライアント コンピューターで BranchCache を有効にして、**分散キャッシュモード**に構成する必要があります。

Intune クライアントをインストールすると、既定で、コンピューターの BranchCache と分散キャッシュ モードは有効です。 ただし、クライアントに BranchCache を無効にするグループ ポリシーが既にある場合、Intune はそのポリシーを優先し、そのコンピューターで BranchCache は無効なままになります。

BranchCache を使用する場合、グループ ポリシーと Intune ファイアウォール ポリシーを管理する組織内の他の管理者にも伝えて、BranchCache を無効にするポリシーやファイアウォールの例外を展開しないようにします。 BranchCache の詳細については、「[BranchCache の概要](http://technet.microsoft.com/library/hh831696.aspx)」を参照してください。

## <a name="network-communication-requirements"></a>ネットワーク通信の要件

Intune のサブスクリプションを管理するために管理および使用するデバイスと、クラウド ベースのサービスのために必要な Web サイトの間の、ネットワーク通信を可能にする必要があります。

Intune は、Intune ソフトウェアを実行するサーバーのようなオンプレミスのインフラストラクチャを使用することはありませんが、Exchange や Active Directory の同期ツールなどのオンプレミスのインフラストラクチャを使用できます。

ファイアウォールとプロキシ サーバーの背後にあるコンピューターを管理するには、Intune の通信を許可するようにファイアウォールとプロキシ サーバーをセットアップする必要があります。

### <a name="requirements-for-proxy-servers"></a>プロキシ サーバーの要件
プロキシ サーバーの背後にあるコンピューターを管理するには、次の点に注意してください。

-   Intune クライアントは、**HTTP** と **HTTPS** を使用しているため、プロキシ サーバーは両方のプロトコルをサポートする必要があります
-   Intune は認証されていないプロキシ サーバーをサポートしています

個々のクライアント コンピューターでプロキシ サーバーの設定を変更するか、グループ ポリシー設定を使用して、特定のプロキシ サーバーの背後にあるすべてのコンピューターの設定を変更します。

### <a name="requirements-for-firewalls-ports-and-domains"></a>ファイアウォール、ポート、およびドメインの要件
管理対象デバイスは、**[すべてのユーザー]** がファイアウォール経由でサービスにアクセスできるように構成する必要があります。

次の表は、Intune クライアントがアクセスするポートとサービスの一覧です。

|**ドメイン**|**ポート**|**IP アドレス**|
|------|----|---|
|manage.microsoft.com<br>a.manage.microsoft.com<br>admin.manage.microsoft.com<br>enterpriseenrollment.manage.microsoft.com<br>enterpriseenrollment-s.manage.microsoft.com<br>i.manage.microsoft.com<br>p.manage.microsoft.com<br>r.manage.microsoft.com|80 および 443|134.170.168.254<br>134.170.51.126
|m.manage.microsoft.com|80 および 443| 13.91.59.243<br>40.68.30.140
|portal.manage.microsoft.com|80 および 443|40.121.50.69<br>52.169.30.159
|account.manage.microsoft.com|80 および 443|157.56.13.59
|fef.msua01.manage.microsoft.com|80 および 443|138.91.243.97
|fef.msua02.manage.microsoft.com|80 および 443|23.96.112.46
|fef.msua04.manage.microsoft.com|80 および 443|23.96.112.28
|fef.msua05.manage.microsoft.com|80 および 443|138.91.244.151
|fef.msub01.manage.microsoft.com|80 および 443|137.135.128.214
|fef.msub02.manage.microsoft.com|80 および 443|137.135.130.29
|fef.msub03.manage.microsoft.com|80 および 443|23.97.165.17
|fef.msub05.manage.microsoft.com|80 および 443|23.97.166.52
|fef.msuc01.manage.microsoft.com|80 および 443|207.46.225.1
|fef.msuc02.manage.microsoft.com|80 および 443|23.98.66.118
|fef.msuc03.manage.microsoft.com|80 および 443|23.101.0.100
|fef.msuc05.manage.microsoft.com|80 および 443|207.46.154.33
|fef.msua06.manage.microsoft.com|80 および 443|104.42.188.1
|fei.msua01.manage.microsoft.com|80 および 443|138.91.240.131
|fei.msua02.manage.microsoft.com|80 および 443|23.96.112.143
|fei.msua04.manage.microsoft.com|80 および 443|23.96.112.147
|fei.msua05.manage.microsoft.com|80 および 443|138.91.240.163
|fei.msub01.manage.microsoft.com|80 および 443|137.135.130.85
|fei.msub02.manage.microsoft.com|80 および 443|137.135.132.149
|fei.msub03.manage.microsoft.com|80 および 443|23.97.160.232
|fei.msub05.manage.microsoft.com|80 および 443|23.97.162.250
|fei.msuc01.manage.microsoft.com|80 および 443|207.46.224.73
|fei.msuc02.manage.microsoft.com|80 および 443|23.98.66.194
|fei.msuc03.manage.microsoft.com|80 および 443|23.101.2.105
|fei.msuc05.manage.microsoft.com|80 および 443|207.46.147.126
|fei.msua06.manage.microsoft.com|80 および 443|138.91.149.190
|m.fei.msua01.manage.microsoft.com|80 および 443|138.91.240.131
|m.fei.msua02.manage.microsoft.com|80 および 443|23.96.112.143
|m.fei.msua04.manage.microsoft.com|80 および 443|23.96.112.147
|m.fei.msua05.manage.microsoft.com|80 および 443|138.91.240.163
|m.fei.msub01.manage.microsoft.com|80 および 443|137.135.130.85
|m.fei.msub02.manage.microsoft.com|80 および 443|137.135.132.149
|m.fei.msub03.manage.microsoft.com|80 および 443|23.97.160.232
|m.fei.msub05.manage.microsoft.com|80 および 443|23.97.162.250
|m.fei.msuc01.manage.microsoft.com|80 および 443|207.46.224.73
|m.fei.msuc02.manage.microsoft.com|80 および 443|23.98.66.194
|m.fei.msuc03.manage.microsoft.com|80 および 443|23.101.2.105
|m.fei.msuc05.manage.microsoft.com|80 および 443|207.46.147.126
|m.fei.msua06.manage.microsoft.com|80 および 443|138.91.149.190
|m.msua01.manage.microsoft.com|80 および 443|157.55.50.182
|m.msua02.manage.microsoft.com|80 および 443|134.170.49.121
|m.msua04.manage.microsoft.com|80 および 443|134.170.49.126
|m.msua05.manage.microsoft.com|80 および 443|157.55.240.190
|m.msua06.manage.microsoft.com|80 および 443|134.170.49.114
|m.msub01.manage.microsoft.com|80 および 443|94.245.121.50
|m.msub02.manage.microsoft.com|80 および 443|94.245.121.58
|m.msub03.manage.microsoft.com|80 および 443|94.245.121.56
|m.msub05.manage.microsoft.com|80 および 443|157.56.113.123
|m.msuc01.manage.microsoft.com|80 および 443|104.44.84.187
|m.msuc02.manage.microsoft.com|80 および 443|104.44.84.188
|m.msuc03.manage.microsoft.com|80 および 443|104.44.84.189
|m.msuc05.manage.microsoft.com|80 および 443|111.221.76.60
|msua01.manage.microsoft.com|80 および 443|157.55.50.182
|msua02.manage.microsoft.com|80 および 443|134.170.49.121
|msua04.manage.microsoft.com|80 および 443|134.170.49.126
|msua05.manage.microsoft.com|80 および 443|157.55.240.190
|msub01.manage.microsoft.com|80 および 443|94.245.121.50
|msub02.manage.microsoft.com|80 および 443|94.245.121.58
|msub03.manage.microsoft.com|80 および 443|94.245.121.56
|msub05.manage.microsoft.com|80 および 443|157.56.113.123
|msuc01.manage.microsoft.com|80 および 443|104.44.84.187
|msuc02.manage.microsoft.com|80 および 443|104.44.84.188
|msuc03.manage.microsoft.com|80 および 443|104.44.84.189
|msuc05.manage.microsoft.com|80 および 443|111.221.76.60
|msua06.manage.microsoft.com|80 および 443|134.170.49.114
|ncufun.account.manage.microsoft.com|80 および 443|157.55.252.224
|neufun.account.manage.microsoft.com|80 および 443|65.52.229.134
|portal.fei.msua01.manage.microsoft.com|80 および 443|138.91.240.131
|portal.fei.msua02.manage.microsoft.com|80 および 443|23.96.112.143
|portal.fei.msua04.manage.microsoft.com|80 および 443|23.96.112.147
|portal.fei.msua05.manage.microsoft.com|80 および 443|138.91.240.163
|portal.fei.msub01.manage.microsoft.com|80 および 443|137.135.130.85
|portal.fei.msub02.manage.microsoft.com|80 および 443|137.135.132.149
|portal.fei.msub03.manage.microsoft.com|80 および 443|23.97.160.232
|portal.fei.msub05.manage.microsoft.com|80 および 443|23.97.162.250
|portal.fei.msuc01.manage.microsoft.com|80 および 443|207.46.224.73
|portal.fei.msuc02.manage.microsoft.com|80 および 443|23.98.66.194
|portal.fei.msuc03.manage.microsoft.com|80 および 443|23.101.2.105
|portal.fei.msuc05.manage.microsoft.com|80 および 443|207.46.147.126
|portal.fei.msua06.manage.microsoft.com|80 および 443|138.91.149.190
|portal.msua01.manage.microsoft.com|80 および 443|157.55.50.182
|portal.msua02.manage.microsoft.com|80 および 443|134.170.49.121
|portal.msua04.manage.microsoft.com|80 および 443|134.170.49.126
|portal.msua05.manage.microsoft.com|80 および 443|157.55.240.190
|portal.msub01.manage.microsoft.com|80 および 443|94.245.121.50
|portal.msub02.manage.microsoft.com|80 および 443|94.245.121.58
|portal.msub03.manage.microsoft.com|80 および 443|94.245.121.56
|portal.msub05.manage.microsoft.com|80 および 443|157.56.113.123
|portal.msuc01.manage.microsoft.com|80 および 443|104.44.84.187
|portal.msuc02.manage.microsoft.com|80 および 443|104.44.84.188
|portal.msuc03.manage.microsoft.com|80 および 443|104.44.84.189
|portal.msuc05.manage.microsoft.com|80 および 443|111.221.76.60
|portal.msua06.manage.microsoft.com|80 および 443|134.170.49.114
|ssu2.manage.microsoft.com|80 および 443|157.55.99.181
|status.manage.microsoft.com|80 および 443|157.55.99.170
|swda01.manage.microsoft.com<br>swda02.manage.microsoft.com<br>swdb01.manage.microsoft.com<br>swdb02.manage.microsoft.com<br>swdc01.manage.microsoft.com<br>swdc02.manage.microsoft.com|80 および 443|93.184.215.200
|*.microsoftonline-p.com|80 および 443||
|has.spserv.microsoft.com<br>デバイスの正常性証明書サービスで必須|443||
|*.microsoftonline-p.net|80 および 443||
|*.portal.office.com|80 および 443||
|*.spynet2.microsoft.com|443||
|c.microsoft.com|80 および 443||
|c1.microsoft.com|80 および 443||
|blob.core.windows.net|80 および 443||
|ajax.aspnetcdn.com|80 および 443||
|*.googleapis.com<br>このドメインは、ポータル サイト Web サイトを使用する場合の JQuery サポートに必要です。|80 および 443||
|wustat.microsoft.com|80 および 443||
|Microsoft Update サービス|\*.update.microsoft.com<br>download.microsoft.com<br>update.microsoft.com<br>\*.download.windowsupdate.com<br>download.windowsupdate.com<br>\*.windowsupdate.com<br>windowsupdate.microsoft.com<br>ntservicepack.microsoft.com|80 および 443|
|DNS ルックアップ要求|manage.microsoft.com.nsatc.net|80|
|ファイアウォールを介した Samsung KNOX Standard デバイス通信|Samsung KNOX Standard デバイスがファイアウォールを介して KNOX Standard サーバーに接続できるようにするには、Samsung KNOX Standard FAQ の手順に従ってください。||
|条件付きアクセス通信|443|204.79.197.200|
|ドキュメント、ヘルプ、およびサポート:</br></br>*.livemeeting.com<br>\*.microsoftonline.com<br>\*.social.technet.microsoft.com<br>blogs.technet.com<br>go.microsoft.com<br>onlinehelp.microsoft.com<br>www.microsoft.com|80|||


>[!div class="step-by-step"]

>[&larr; **前提条件**](what-to-know-before-you-start-microsoft-intune.md)     [**サブスクリプション** &rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)  

