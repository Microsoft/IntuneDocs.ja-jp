---
title: Microsoft Intune のネットワーク要件と帯域幅の詳細
titleSuffix: ''
description: Intune のネットワーク構成の要件と帯域幅の詳細を確認します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40f9ada715570de7b5b2f95292b7ed0d238242d2
ms.sourcegitcommit: 04d29d47b61486b3586a0e0e5e8e48762351f2a3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/11/2019
ms.locfileid: "59570794"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Intune のネットワーク構成の要件と帯域幅

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

このガイダンスは、Intune 管理者が Intune サービスのネットワーク要件を理解するのに役立ちます。 帯域幅の要件およびプロキシの設定に必要な IP アドレスとポートの設定を理解できます。

## <a name="average-network-traffic"></a>ネットワーク トラフィックの平均
次の表は、各クライアントのネットワークで通信される一般的なコンテンツの概算のサイズと頻度を一覧にしたものです。

> [!NOTE]
> デバイスで確実に Intune から更新プログラムとコンテンツを受信するには、定期的にインターネットに接続する必要があります。 更新プログラムやコンテンツを受信するのに必要な時間は一定ではない場合がありますが、毎日、少なくとも 1 時間はインターネットに接続したままにしておく必要があります。

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
プロキシ サーバーは、重複するダウンロードを削減し、インターネットのコンテンツで使用されるネットワーク帯域幅を減らすために、コンテンツをキャッシュできます。

クライアントからコンテンツ要求を受信するキャッシュ機能付きプロキシ サーバーは、そのコンテンツを取得し、Web 応答とダウンロードの両方をキャッシュできます。 サーバーは、キャッシュされたデータを使用して、クライアントからの後続の要求に応答します。

Intune クライアント用にコンテンツをキャッシュするプロキシ サーバーの一般的な設定を以下に示します。


|          Setting           |           推奨される値           |                                                                                                  説明                                                                                                  |
|----------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         キャッシュ サイズ         |             5 ～ 30 GB             | この値は、ネットワークにあるクライアント コンピューターの台数と、使用する構成によって異なります。 ファイルが短時間で削除されないようにするには、環境のキャッシュのサイズを調整します。 |
| キャッシュする個々のファイルのサイズ |                950 MB                 |                                                                     キャッシュ機能付きサーバーによっては、この設定がないものがあります。                                                                     |
|   キャッシュするオブジェクトの種類    | HTTP<br /><br />HTTPS<br /><br />BITS |                                               Intune パッケージは、HTTP 経由でバックグラウンド インテリジェント転送サービス (BITS) のダウンロードで取得される CAB ファイルです。                                               |
> [!NOTE]
> プロキシ サーバーを使用してコンテンツ要求をキャッシュする場合、通信はクライアントとプロキシとの間、およびプロキシから Intune へのみ暗号化されます。 クライアントから Intune への接続は、エンドツーエンドで暗号化されることはありません。

コンテンツをキャッシュするプロキシ サーバーの仕様に関する詳細については、使用するプロキシ サーバー ソリューションのドキュメントを参照してください。

### <a name="use-background-intelligent-transfer-service-bits-on-computers"></a>コンピューターでバックグラウンド インテリジェント転送サービス (BITS) を使用する
構成する時間中は、Windows コンピューター上で BITS を使用して、ネットワーク帯域幅を減らすことができます。 BITS のポリシーは、Intune エージェント ポリシーの **[ネットワーク帯域幅]** ページで構成できます。

> [!NOTE]
> Windows 上の MDM 管理については、MobileMSI アプリの種類用の OS の管理インターフェイスのみで、ダウンロードに BITS が使用されます。 AppX/MsiX では、BITS 以外の配信の最適化を使用する Intune エージェント経由で、独自の BITS 以外のダウンロード スタックと Win32 アプリを使用します。

BITS と Windows コンピューターの詳細については、TechNet ライブラリの「[バックグラウンド インテリジェント転送サービス](http://technet.microsoft.com/library/bb968799.aspx)」を参照してください。

### <a name="use-branchcache-on-computers"></a>コンピューターで BranchCache を使用する
Intune クライアントは、BranchCache を使用してワイド エリア ネットワーク (WAN) トラフィックを削減できます。 次のオペレーティング システムでは、BranchCache をサポートします。

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

BranchCache を使用するには、クライアント コンピューターで BranchCache を有効にして、**分散キャッシュモード**に構成する必要があります。

Intune クライアントをコンピューターにインストールすると、既定で、BranchCache と分散キャッシュ モードが有効になります。 ただし、グループ ポリシーで BranchCache が無効になっている場合、Intune でそのポリシーがオーバーライドされることはなく、BranchCache は無効のままになります。

BranchCache を使用する場合、グループ ポリシーと Intune ファイアウォール ポリシーを管理する組織内の他の管理者と共同作業を行います。 他の管理者が、BranchCache を無効にするポリシーやファイアウォールの例外を展開しないようにしてください。 BranchCache の詳細については、「[BranchCache の概要](http://technet.microsoft.com/library/hh831696.aspx)」を参照してください。

## <a name="network-communication-requirements"></a>ネットワーク通信の要件

管理するデバイスと、クラウド ベースのサービスに必要な Web サイトの間の、ネットワーク通信を有効にします。

クラウド専用のサービスとして、Intune ではサーバーやゲートウェイなど、オンプレミスのインフラストラクチャは必要ありません。

ファイアウォールとプロキシ サーバーの背後にあるデバイスを管理するには、Intune に対する通信を有効にする必要があります。

- Intune クライアントは、**HTTP (80)** と **HTTPS (443)** を使用しているため、プロキシ サーバーは両方のプロトコルをサポートする必要があります
- Intune では、一部のタスク (ソフトウェア更新プログラムのダウンロードなど) で、manage.microsoft.com への認証されていないプロキシ サーバー アクセスが必要です

個々のクライアント コンピューターでプロキシ サーバーの設定を変更できます。 また、グループ ポリシーの設定を使用して、指定したプロキシ サーバーの背後にあるすべてのクライアント コンピューターの設定を変更することもできます。


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

マネージド デバイスは、 **[すべてのユーザー]** がファイアウォール経由でサービスにアクセスできるように構成する必要があります。

次の表は、Intune クライアントがアクセスするポートとサービスの一覧です。

|**ドメイン**|**IP アドレス**|
|---------------------|-----------|
|login.microsoftonline.com | 詳細については、「[Office 365 URL および IP アドレス範囲](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)」を参照してください。 |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |52.175.12.209<br>20.188.107.228<br>52.138.193.149<br>51.144.161.187<br>52.160.70.20<br>52.168.54.64 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 40.83.123.72<br>13.76.177.110<br>52.169.9.87<br>52.174.26.23<br>104.40.82.191<br>13.82.96.212|
|fei.msua01.manage.microsoft.com<br>portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com<br>fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>fei.msua04.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.amsua0202.manage.microsoft.com <br>portal.fei.amsua0202.manage.microsoft.com <br>m.fei.amsua0202.manage.microsoft.com<br>fei.amsua0402.manage.microsoft.com <br>portal.fei.amsua0402.manage.microsoft.com <br>m.fei.amsua0402.manage.microsoft.com|52.160.70.20<br>52.168.54.64 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>fei.amsub0202.manage.microsoft.com <br>portal.fei.amsub0202.manage.microsoft.com <br>m.fei.amsub0202.manage.microsoft.com<br>fei.amsub0302.manage.microsoft.com <br>portal.fei.amsub0302.manage.microsoft.com <br>m.fei.amsub0302.manage.microsoft.com|52.138.193.149<br>51.144.161.187|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com|52.175.12.209<br>20.188.107.228|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|52.169.82.238|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
|fef.amsua0202.manage.microsoft.com|52.165.165.17|
|fef.amsua0402.manage.microsoft.com|40.69.157.122|
|fef.amsua0502.manage.microsoft.com|13.85.68.142|
|fef.amsua0602.manage.microsoft.com|52.161.28.64|
|fef.amsub0102.manage.microsoft.com|40.118.98.207|
|fef.amsub0202.manage.microsoft.com|40.69.208.122|
|fef.amsub0302.manage.microsoft.com|13.74.145.65|
|enterpriseregistration.windows.net|52.175.211.189|
|Admin.manage.microsoft.com|52.224.221.227<br>52.161.162.117<br>52.178.44.195<br>52.138.206.56<br>52.230.21.208<br>13.75.125.10|
|wip.mam.manage.microsoft.com|52.187.76.84<br>13.76.5.121<br>52.165.160.237<br>40.86.82.163<br>52.233.168.142<br>168.63.101.57|
|mam.manage.microsoft.com|104.40.69.125<br>13.90.192.78<br>40.85.174.177<br>40.85.77.31<br>137.116.229.43<br>52.163.215.232<br>52.174.102.180|






### <a name="apple-device-network-information"></a>Apple デバイス ネットワークの情報


|使用目的|ホスト名 (IP アドレス/サブネット)|プロトコル|ポート|
|-----|--------|------|-------|
|Apple Push Notification Service (APNS) 経由で Intune サービスからプッシュ通知を受信する。 Apple のドキュメントは、[こちら](https://support.apple.com/en-us/HT203609)をご覧ください。|                                    gateway.push.apple.com (17.0.0.0/8)                                  |    TCP     |     2195     |
|Apple Push Notification Service (APNS) 経由でフィードバックを Intune サービスに送信する|                                  feedback.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2196     |
|Apple サーバーからコンテンツを取得して表示する|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br> \*.phobos.itunes-apple.com.akadns.net |    HTTP    |      80      |
|APNS サーバーとの通信|#-courier.push.apple.com (17.0.0.0/8)<br>'#' は、0 から 50 の乱数です。|    TCP     |  5223 および 443  |
|さまざまな関数には、World Wide Web、iTunes Store、macOS アプリ ストア、iCloud、メッセージングなどへのアクセスが含まれます。 |phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net| HTTP/HTTPS |  80 または 443   |

詳細については、Apple の「[Apple ソフトウェア製品で使われている TCP および UDP ポート](https://support.apple.com/en-us/HT202944)」、「[macOS、iOS、iTunes のサーバホスト接続と iTunes のバックグラウンドプロセスについて](https://support.apple.com/en-us/HT201999)」、「[macOS および iOS クライアントで Apple プッシュ通知が届かない場合](https://support.apple.com/en-us/HT203609)」を参照してください。
