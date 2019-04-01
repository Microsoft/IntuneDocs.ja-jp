---
title: Intune の Windows 10 の配信の最適化の設定 |Microsoft Docs
description: Intune を使用してを展開する Windows 10 デバイス用の配信の最適化設定します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/09/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6e90828da8c209b534b830af7fe522b254374bf
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57695281"
---
# <a name="delivery-optimization-settings-for-intune"></a>Intune の配信の最適化の設定

この記事では、Intune は、10 以降、Windows を実行するデバイスでサポートされる配信の最適化設定を一覧表示します。  

Intune コンソールでほとんどのオプションは、関連コンテンツへのリンクが提供されている、Windows ドキュメントで詳しく取り上げられている配信の最適化の設定に直接マップします。  設定または Intune に固有のオプションは、その他のコンテンツへのリンクは含まれません。  

次の表は、次のとおりです。  

- **設定**: Intune で、設定が表示されます。 リンクされている設定に関連するエントリを開く[Windows 10 用の配信の最適化の構成を更新](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)Windows のドキュメント、設定の詳細を学習できます。

- **Windows バージョン**: この設定のサポートが含まれる Windows 10 の最小バージョン。  

- **詳細**: Intune で Intune の既定値を含む、設定を実装する方法について簡単に説明します。 リンクがあるときに使用可能な[配信の最適化 Policy configuration service プロバイダー](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization) (CSP) のエントリ。  

Intune を使用して、これらの設定を構成するを参照してください。[更新プログラムを配信](delivery-optimization-windows.md)します。  

## <a name="delivery-optimization"></a>配信の最適化  

|Setting  |Windows Version  |説明  |
|---------|-----------------|---------|
| [ダウンロード モード](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode)     | 1511         | ダウンロード方法を指定する配信の最適化を使用してコンテンツをダウンロードします。<br><ul><li>**[未構成]**: エンド ユーザーはそれぞれ独自の方法を使って各デバイスを更新します。*[Windows の更新プログラム]* や、オペレーティング システムで使用できる [配信の最適化] 設定が使われる場合があります。 </li> <li> **[HTTP のみ、ピアリングなし (0)]**: 更新プログラムをインターネットからのみ取得します。 しない (ピア ツー ピア)、ネットワーク上の他のコンピューターから更新プログラムを取得します。 </li> <li> **ピアリングで同じ NAT (1) の背後にあると HTTP のブレンド**: インターネットおよびネットワーク上の他のコンピューターから更新プログラムを取得します。 </li> <li> **プライベート グループ (2) 間のピアリングと HTTP のブレンド**。 ピアリングで同じデバイス上に発生します (存在する) 場合、Active Directory サイトまたは同じドメイン。 このオプションを選択した場合、ピアリングはネットワーク アドレス変換 (NAT) の IP アドレスを越えます。 </li> <li> **[HTTP とインターネット ピアリングの組み合わせ (3)]**: インターネットおよびネットワーク上の他のコンピューターから更新プログラムを取得します。 </li> <li> **[ピアリングなしの簡易ダウンロード モード (99)]**: インターネットを介して、Microsoft などの更新プログラムの所有者から更新プログラムを直接取得します。 これは配信の最適化クラウド サービスに接続しません。 </li> <li> **[バイパス モード (100)]**: バックグラウンド インテリジェント転送サービス (BITS) を使って更新プログラムを取得します。 配信の最適化を使いません。 </li></ul> **既定の**: 未構成  <br><br> ポリシー CSP: [DODownloadMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodownloadmode)  <br><br>  |
| [ピアの選択を制限します。](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#select-a-method-to-restrict-peer-selection)          | 1803        | 必要があります**ダウンロード モード**に設定する*ピアリングで同じ NAT (1) の背後にあると HTTP のブレンド*または*プライベート グループ (2) 間のピアリングと HTTP のブレンド*します。<br/><br/>デバイスの特定のグループには、ピアの選択範囲を制限します。<br/><br/>**既定の**: 未構成 <br/><br/>ポリシー CSP: [DORestrictPeerSelectionBy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dorestrictpeerselectionby)<br><br>      |
| [グループの ID ソース](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#select-the-source-of-group-ids)     | 1803        | 必要があります**ダウンロード モード**に設定する*プライベート グループ間のピアリングと HTTP のブレンド*します。<br><br>ソースごとのデバイスの特定のグループには、ピアの選択範囲を制限します。<br><br>選択した場合**カスタム**、し構成する**グループ ID (GUID) として**します。 別のドメインで、同じ LAN 上にないブランチのローカル ネットワークのピアリングの 1 つのグループを作成する必要がある場合は、グループ ID を GUID を使用します。<br><br>**既定の**: 未構成 <br><br>ポリシー CSP: [DOGroupId](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dogroupid)     |

## <a name="bandwidth"></a>帯域幅  

|Setting  |Windows Version  |説明  |
|---------|---------|---------|
|帯域幅の最適化の種類     | *詳細を参照*        | Intune が最大値を決定する方法を選択します。 帯域幅、配信の最適化は、すべての同時ダウンロード アクティビティ間で使用できます。<br><br>次のオプションがあります。<br><ul><li>**未構成**</li><br><li>**絶対**– 指定、 [(KB/秒) のダウンロードの帯域幅の最大](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#maximum-download-bandwidth)と[最大アップロード帯域幅 (KB/秒)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#max-upload-bandwidth)デバイスがそのすべての同時実行の配信の最適化ダウンロード全体で使用できることアクティビティ。<br><br>Windows 1607 が必要です<br><br>ポリシー CSP: [DOMaxDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxdownloadbandwidth)と[DOMaxUploadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxuploadbandwidth)</li><br><li>**%** – 指定、[最大フォア グラウンド ダウンロードの帯域幅 (%) で](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#maximum-foreground-download-bandwidth)と[(%) でバック グラウンド ダウンロードの帯域幅を最大](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#maximum-foreground-download-bandwidth)をデバイスでの同時実行のすべての配信で使用できます最適化では、アクティビティをダウンロードします。<br><br>Windows 1803 が必要です<br><br>ポリシー CSP: [DOPercentageMaxForegroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxforegroundbandwidth)と[DOPercentageMaxBackgroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxbackgroundbandwidth)    <br><br><li>**営業時間の割合**– 最大[フォア グラウンド](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#set-business-hours-to-limit-foreground-download-bandwidth)ダウンロードの帯域幅、および最大[バック グラウンド](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#set-business-hours-to-limit-background-download-bandwidth)ダウンロードの帯域幅、構成の営業時間の開始時刻と終了時刻をクリックし、中に、勤務時間外に使用する帯域幅の割合。 <br><br>Windows 1803 が必要です <br><br>ポリシー CSP: [DOSetHoursToLimitBackgroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitbackgrounddownloadbandwidth)と[DOSetHoursToLimitForegroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitforegrounddownloadbandwidth)<br><br>   |
|[秒単位で遅延 HTTP バック グラウンドでダウンロード](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#delay-background-download-from-http-in-secs) | 1803        | HTTP 経由でバック グラウンドでのコンテンツのダウンロードを遅延するのに最大時間を構成するのにには、この設定を使用します。 これは、ピア ツー ピアのダウンロード ソースをサポートするためのダウンロードにのみ適用されます。 この遅延中には、デバイスは、利用可能なコンテンツをピアを検索します。 ピア ソースを待っている間に、ダウンロードは、エンドユーザーのスタックが表示されます。   <br><br>**既定の**:*値が構成されていません*  <br><br>**推奨**: 60 秒   <br><br>ポリシー CSP: [DODelayBackgroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelaybackgrounddownloadfromhttp) <br><br>    |
| [秒単位で遅延フォア グラウンド HTTP ダウンロード](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#delay-foreground-download-from-http-in-secs)      | 1803       | HTTP 経由でコンテンツの前景色 (対話型) ダウンロードを遅延する最大時間を構成します。 これは、ピア ツー ピアのダウンロード ソースをサポートするためのダウンロードにのみ適用されます。 この遅延中には、デバイスは、利用可能なコンテンツをピアを検索します。 ピア ソースを待っている間に、ダウンロードは、エンドユーザーのスタックが表示されます。   <br><br>**既定の**:*値が構成されていません*  <br><br>**推奨**: 60 秒   <br><br>ポリシー CSP: [DODelayForegroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelayforegrounddownloadfromhttp) <br><br>         |


## <a name="caching"></a>キャッシュ  

|Setting  |Windows Version  |説明  |
|---------|---------|---------|
|[ピア キャッシュ (GB) のために必要な最小 ram 容量](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#minimum-ram-allowed-to-use-peer-caching)      | 1703        | Gb 単位のピア キャッシュを使用するデバイスに必要な最小の RAM サイズを指定します。 <br><br>**既定の**:*値が構成されていません*  <br><br>**推奨**: 4 GB <br><br>ポリシー CSP: [DOMinRAMAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominramallowedtopeer) <br><br>        |
|[ピア キャッシュ (GB) のために必要な最小ディスク サイズ](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#minimum-disk-size-allowed-to-use-peer-caching)      | 1703        | Gb 単位のピア キャッシュを使用するデバイスに必要な最小ディスク サイズを指定します。 <br><br>**既定の**:*値が構成されていません*  <br><br>**推奨**: 32 GB   <br><br>ポリシー CSP: [DOMinDiskSizeAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domindisksizeallowedtopeer) <br><br>    |
|[ピア キャッシュ (単位は MB) のコンテンツ ファイルの最小サイズ](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#minimum-peer-caching-content-file-size)      | 1703        | ファイルが満たす必要があります、またはピア キャッシュを使用するを超えています (mb) の最小サイズを指定します。  <br><br>**既定の**:*値が構成されていません*  <br><br>**推奨**: 10 MB   <br><br>ポリシー CSP: [DOMinFileSizeToCache](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominfilesizetocache)  <br><br>      |
|[(%) にアップロードするために必要な最小のバッテリ レベル](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#allow-uploads-while-the-device-is-on-battery-while-under-set-battery-level)      | 1709        | ピアにデータをアップロードするデバイスに必要な最小のバッテリ レベル、割合として指定します。 場合は、バッテリ レベルは、指定した値になった、アクティブなアップロードが自動的に一時停止します。   <br><br>**既定の**:*値が構成されていません*  <br><br>**推奨**: 40%   <br><br>ポリシー CSP: [DOMinBatteryPercentageAllowedToUpload](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominbatterypercentageallowedtoupload) <br><br>        |
|[キャッシュ ドライブを変更します。](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#modify-cache-drive)        | 1607        | ドライブを指定のキャッシュの配信の最適化を使用します。 環境変数、ドライブ文字、または完全なパスを使用することができます。  <br><br>**既定の**: %systemdrive% <br><br>ポリシー CSP: [DOModifyCacheDrive](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domodifycachedrive) <br><br>        |
| [キャッシュの最大経過時間 (日数)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#max-cache-age)    | 1511         | 各ファイルが正常にファイルがデバイスに配信の最適化のキャッシュに保持されていることをダウンロードした後、時間の長い、方法を指定します。   <br><br>Intune では、日間にキャッシュ有効期間を構成します。 定義する日数は、どの Windows 定義この設定は適用可能な秒数に変換されます。 たとえば、3 日間の Intune の構成は、259200 秒 (3 日間) にデバイスに変換されます。  <br><br>**既定の**:*値が構成されていません*     <br><br>**推奨**: 7   <br><br>ポリシー CSP: [DOMaxCacheAge](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)  <br><br>          |
| 最大キャッシュ サイズの種類  | *詳細を参照*    | 配信の最適化によって使用されるデバイス上のディスク領域の量を管理する方法を選択します。 構成しない場合は、使用可能な空きディスク領域の 20% にキャッシュ サイズが既定値です。  <br><ul><li>**[未構成]** (既定値)</li><br><li>**絶対**– 指定、[絶対最大キャッシュ サイズ (GB) で](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#absolute-max-cache-size)配信の最適化のデバイスで使用するドライブの領域の最大量を構成します。 0 (ゼロ) に設定すると、キャッシュ サイズが限られておりが、配信の最適化、デバイスのディスク領域が不足している場合、キャッシュがクリアされます。 <br><br>Windows 1607 が必要です<br><br> ポリシー CSP: [DOAbsoluteMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-doabsolutemaxcachesize) </li><br><li>**割合**– 指定、 [(%) で最大キャッシュ サイズ](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#max-cache-size)配信の最適化のデバイスで使用するドライブの領域の最大量を構成します。 ドライブの空き領域の割合が、および配信の最適化は常にドライブの空き容量を評価し、割合を設定] の [最大キャッシュ サイズを保持するキャッシュがクリアされます。 <br><br>Windows 1511 が必要です<br><br>ポリシー CSP: [DOMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcachesize)  |
| [VPN ピア キャッシュ](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#enable-peer-caching-while-the-device-connects-via-vpn)  | 1709  | 選択**有効**ドメイン ネットワークに VPN で接続されているピアがキャッシュに参加するデバイスを構成します。 有効になっているデバイスからダウンロードしたり、他のドメイン ネットワーク デバイス、VPN または、会社のドメイン ネットワークのいずれかにアップロードすることができます。  <br><br>**既定の**: 未構成  <br><br>ポリシー CSP: [DOAllowVPNPeerCaching](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)    |

## <a name="next-steps"></a>次の手順

[Intune での配信の最適化を構成します。](delivery-optimization-windows.md)
