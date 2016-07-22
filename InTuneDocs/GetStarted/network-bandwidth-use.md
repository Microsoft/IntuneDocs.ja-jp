---
title: "Intune のネットワーク帯域幅の使用 | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: e104dc52a8a9bdda4b2edb2939d8c7c36e8ecc12


---

# Intune のネットワーク帯域幅の使用

[!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] をセットアップする前に、このトピックと「[What to know before you start Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)」 (Microsoft Intune を開始する前に理解しておくこと) に挙げられているその他の要件を確認してください。

[!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] クライアントのネットワーク トラフィックを計画するには、次のセクションの情報を参照してください。

## ネットワーク トラフィックの平均
次の表は、各クライアントのネットワークで通信される一般的なコンテンツの概算のサイズと頻度を一覧にしたものです。

> [!NOTE]
> [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] サービスから提供される必要な更新プログラムとコンテンツをコンピューターとモバイル デバイスで確実に受信するためには、定期的にインターネットに接続する必要があります。 更新プログラムまたはコンテンツを受信するのにかかる時間は一定ではありませんが、ガイドラインとして、毎日、少なくとも 1 時間はインターネットに接続したままにしておく必要があります。

|コンテンツの種類|概算サイズ|頻度と詳細|
|----------------|--------------------|-------------------------|
|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] クライアントのインストール<br /><br />**以下の要件が、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] クライアントのインストールに追加されます。**|125 MB|**1 回**<br /><br />クライアントのダウンロード サイズは、クライアント コンピューターのオペレーティング システムによって異なります。|
|クライアントの登録パッケージ|15 MB|**1 回**<br /><br />追加のダウンロードは、このコンテンツの種類の更新プログラムが存在する場合に発生することがあります。|
|Endpoint Protection エージェント|65 MB|**1 回**<br /><br />追加のダウンロードは、このコンテンツの種類の更新プログラムが存在する場合に発生することがあります。|
|Operations Manager エージェント|11 MB|**1 回**<br /><br />追加のダウンロードは、このコンテンツの種類の更新プログラムが存在する場合に発生することがあります。|
|ポリシー エージェント|3 MB|**1 回**<br /><br />追加のダウンロードは、このコンテンツの種類の更新プログラムが存在する場合に発生することがあります。|
|Microsoft Easy Assist によるリモート アシスタンス|6 MB|**1 回**<br /><br />追加のダウンロードは、このコンテンツの種類の更新プログラムが存在する場合に発生することがあります。|
|日常のクライアントの操作|6 MB|**毎日**<br /><br />[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] クライアントは、更新プログラムやポリシーを確認したり、クライアントの状態をサービスに報告したりするために、定期的に [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] サービスと通信します。|
|Endpoint Protection のマルウェア定義の更新|不定<br /><br />通常 40 KB ～ 2 MB|**毎日**<br /><br />最大で 1 日に 3 回。|
|Endpoint Protection エンジンの更新プログラム|5 MB|**月単位**|
|ソフトウェア更新プログラム|不定<br /><br />サイズは、展開する更新プログラムによって異なります。|**月単位**<br /><br />通常、ソフトウェアの更新プログラムのリリースは、毎月の第 2 火曜日です。<br /><br />新しく登録された、または、展開されたコンピューターは、以前にリリースされた更新プログラムのフル セットをダウンロードする間、多くのネットワーク帯域幅を使用することがあります。|
|Service Pack|不定<br /><br />サイズは、展開する各サービス パックによって異なります。|**不定**<br /><br />サービス パックを展開する時間に依存します。|
|ソフトウェアの配布|不定<br /><br />サイズは、展開するソフトウェアによって異なります。|**不定**<br /><br />ソフトウェアを展開する時間に依存します。|

## ネットワーク帯域幅の使用量を削減する方法
次の方法を使用して、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] クライアントのネットワーク帯域幅の使用量を削減できます。

### コンテンツ要求のキャッシュにプロキシ サーバーを使用する
コンテンツをキャッシュするプロキシ サーバーを使用して、重複するダウンロードを削減し、インターネットからコンテンツを要求するクライアントのネットワーク帯域幅の使用量を減らすことができます。

キャッシュを行うプロキシ サーバーは、ネットワーク上のクライアント コンピューターからの要求を受け取り、インターネットからコンテンツを取得して、HTTP 応答とバイナリのダウンロード両方をキャッシュできます。 サーバーは、キャッシュされた情報を使用して、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] クライアント コンピューターからの後続の要求に応答します。

[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] クライアント用にコンテンツをキャッシュするプロキシ サーバーの一般的な設定を以下に示します。

|設定|推奨される値|説明|
|-----------|---------------------|-----------|
|キャッシュ サイズ|5 ～ 30 GB|この値は、ネットワークにあるクライアント コンピューターの台数と、使用する構成によって異なります。 ファイルが短時間で削除されないようにするには、環境のキャッシュのサイズを調整します。|
|キャッシュする個々のファイルのサイズ|950 MB|キャッシュ機能付きサーバーによっては、この設定がないものがあります。|
|キャッシュするオブジェクトの種類|HTTP<br /><br />HTTPS<br /><br />BITS|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] パッケージは、HTTP 経由でバックグラウンド インテリジェント転送サービス (BITS) のダウンロードで取得される CAB ファイルです。|
コンテンツをキャッシュするプロキシ サーバーの仕様に関する詳細については、使用するプロキシ サーバー ソリューションのドキュメントを参照してください。

### コンピューターで、バック グラウンド インテリジェント転送サービスを使用する
[!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] は、Windows コンピューターでのバックグラウンド インテリジェント転送サービス (BITS) の使用をサポートしています。BITS を使用して、構成する時間中に使用するネットワーク帯域幅を削減できます。 BITS のポリシーは、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] エージェント ポリシーの **[ネットワーク帯域幅]** ページで構成できます。

BITS と Windows コンピューターの詳細については、TechNet ライブラリの「[バックグラウンド インテリジェント転送サービス](http://technet.microsoft.com/library/bb968799.aspx)」を参照してください。

### コンピューターで BranchCache を使用する
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] クライアントは、BranchCache を使用してワイド エリア ネットワーク (WAN) トラフィックを削減できます。 クライアントとしてサポートされる次のオペレーティング システムでも、BranchCache がサポートされます。

-   [!INCLUDE[nextref_client_7](../includes/nextref_client_7_md.md)]

-   [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]

-   [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)]

BranchCache を使用するには、クライアント コンピューターで BranchCache を有効にして、**分散キャッシュモード**に構成する必要があります。

[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] クライアントをインストールすると、既定で、コンピューターの BranchCache と分散キャッシュ モードは有効です。 ただし、クライアントに BranchCache を無効にするグループ ポリシーが既にある場合、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] はそのポリシーを優先し、そのコンピューターで BranchCache は無効なままになります。

BranchCache を使用する場合、グループ ポリシーと [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] ファイアウォール ポリシーを管理する組織内の他の管理者にも伝えて、BranchCache を無効にするポリシーやファイアウォールの例外を展開しないようにします。 BranchCache の詳細については、「[BranchCache の概要](http://technet.microsoft.com/library/hh831696.aspx)」を参照してください。

### 関連項目
[Microsoft Intune を使い始める前に](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=Jun16_HO4-->


