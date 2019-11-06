---
title: Microsoft Intune のネットワーク要件と帯域幅の詳細
titleSuffix: ''
description: Intune のネットワーク構成の要件と帯域幅の詳細を確認します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0507d607bfac6c084f1ce0b1f59d7474810ec8b7
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415111"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Intune のネットワーク構成の要件と帯域幅

この情報を使用して、Intune 展開の帯域幅の要件を把握できます。

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

BITS と Windows コンピューターの詳細については、TechNet ライブラリの「[バックグラウンド インテリジェント転送サービス](https://technet.microsoft.com/library/bb968799.aspx)」を参照してください。

### <a name="delivery-optimization"></a>配信の最適化

配信の最適化では、Intune を使用して、Windows 10 デバイスでアプリケーションおよび更新プログラムをダウンロードするときに消費される帯域幅を削減することができます。 自己整理型の分散キャッシュを使用すると、従来のサーバーや代替ソース (ネットワーク ピアなど) からダウンロードをプルできます。

配信の最適化によってサポートされる Windows 10 のバージョンとコンテンツの種類の完全な一覧については、「[Windows 10 更新プログラムの配信の最適化](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#requirements)」をご覧ください。

デバイスの構成プロファイルの一部として、[配信の最適化を設定する](../configuration/delivery-optimization-settings.md)ことができます。

### <a name="use-branchcache-on-computers"></a>コンピューターで BranchCache を使用する

Intune クライアントは、BranchCache を使用してワイド エリア ネットワーク (WAN) トラフィックを削減できます。 次のオペレーティング システムでは、BranchCache をサポートします。

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

BranchCache を使用するには、クライアント コンピューターで BranchCache を有効にして、**分散キャッシュモード**に構成する必要があります。

Intune クライアントをコンピューターにインストールすると、既定で、BranchCache と分散キャッシュ モードが有効になります。 ただし、グループ ポリシーで BranchCache が無効になっている場合、Intune でそのポリシーがオーバーライドされることはなく、BranchCache は無効のままになります。

BranchCache を使用する場合、グループ ポリシーと Intune ファイアウォール ポリシーを管理する組織内の他の管理者と共同作業を行います。 他の管理者が、BranchCache を無効にするポリシーやファイアウォールの例外を展開しないようにしてください。 BranchCache の詳細については、「[BranchCache の概要](https://technet.microsoft.com/library/hh831696.aspx)」を参照してください。

> [!NOTE]
> Microsoft Intune を使用して、[モバイル デバイス管理 (MDM) によりモバイル デバイスとして](../enrollment/windows-enroll.md)、または Intune ソフトウェア クライアントによりコンピューターとして、Windows PC を管理できます。 Microsoft では、可能な場合は常に [MDM 管理ソリューションを使用する](../enrollment/windows-enroll.md)ことをお勧めします。 この方法で管理すると、BranchCache はサポートされません。 詳細については、「[Windows PC のコンピューターとしての管理とモバイル デバイスとしての管理の比較](../pc-management-comparison.md)」をご覧ください。


## <a name="next-steps"></a>次の手順

[Intune のエンドポイントを確認します](../intune-endpoints.md)

