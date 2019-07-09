---
title: Intune 用の Windows 10 配信最適化の設定 | Microsoft Docs
description: Intune を使用して展開できる Windows 10 デバイス向けの配信最適化の設定。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: ab4871da52f5df0aec0a698f31daa5608a57c1c3
ms.sourcegitcommit: 116ef72b9da4d114782d4b8dd9f57556c9b01511
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2019
ms.locfileid: "67493901"
---
# <a name="delivery-optimization-settings-for-intune"></a>Intune 用の配信最適化の設定

この記事では、Windows 10 以降が実行されているデバイスに対して Intune でサポートされる配信最適化の設定の一覧を示します。  

Intune コンソールのほとんどのオプションは、Windows ドキュメントで詳しく説明されている配信最適化の設定に直接対応しており、関連するコンテンツへのリンクが示されています。  Intune 固有の設定またはオプションには、追加コンテンツへのリンクは含まれません。  

後述の表には次のものが含まれます。  

- **設定**: Intune に表示される設定。 リンクになっている設定の場合は、Windows ドキュメントの [Windows 10 更新プログラム用の配信最適化の構成](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)に関する記事の関連するエントリが開き、設定についてさらに詳しく確認できます。

- **Windows のバージョン**: この設定のサポートが含まれる Windows 10 の最小バージョン。  

- **詳細**: Intune の既定値など、Intune での設定の実装方法についての簡単な説明。 これがある場合は、[配信最適化のポリシー構成サービス プロバイダー](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization) (CSP) のエントリにリンクしています。  

Intune を構成してこれらの設定を使用するには、[更新プログラムの配信](delivery-optimization-windows.md)に関する記事を参照してください。  

## <a name="delivery-optimization"></a>配信の最適化  

|Setting  |Windows Version  |説明  |
|---------|-----------------|---------|
| [ダウンロード モード](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#download-mode)     | 1511         | コンテンツをダウンロードするには、配信最適化で使用されるダウンロード方法を指定します。<br><ul><li>**[未構成]** : エンド ユーザーはそれぞれ独自の方法を使って各デバイスを更新します。 *[Windows の更新プログラム]* や、オペレーティング システムで使用できる [配信の最適化] 設定が使われる場合があります。 </li> <li> **[HTTP のみ、ピアリングなし (0)]** : 更新プログラムをインターネットからのみ取得します。 ネットワーク上の他のコンピューターからは更新プログラムを取得しません (ピア ツー ピア)。 </li> <li> **[HTTP と同じ NAT でのピアリングの組み合わせ (1)]** : インターネットおよびネットワーク上の他のコンピューターから更新プログラムを取得します。 </li> <li> **[HTTP とプライベート グループでのピアリングの組み合わせ (2)]** : ピアリングは、同じ Active Directory サイト (存在する場合) または同じドメイン内にあるデバイス上で発生します。 このオプションを選択した場合、ピアリングはネットワーク アドレス変換 (NAT) の IP アドレスを越えます。 </li> <li> **[HTTP とインターネット ピアリングの組み合わせ (3)]** : インターネットおよびネットワーク上の他のコンピューターから更新プログラムを取得します。 </li> <li> **[ピアリングなしの簡易ダウンロード モード (99)]** : インターネットを介して、Microsoft などの更新プログラムの所有者から更新プログラムを直接取得します。 これは配信の最適化クラウド サービスに接続しません。 </li> <li> **[バイパス モード (100)]** : バックグラウンド インテリジェント転送サービス (BITS) を使って更新プログラムを取得します。 配信の最適化を使いません。 </li></ul> **既定値**: 未構成  <br><br> ポリシー CSP: [DODownloadMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodownloadmode)  <br><br>  |
| [ピアの選択の制限](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#select-a-method-to-restrict-peer-selection)          | 1803        | **[ダウンロード モード]** を *[HTTP と同じ NAT でのピアリングの組み合わせ (1)]* または *[HTTP とプライベート グループでのピアリングの組み合わせ (2)]* に設定することを要求します。<br/><br/>ピアの選択を特定のデバイス グループに制限します。<br/><br/>**既定値**: 未構成 <br/><br/>ポリシー CSP: [DORestrictPeerSelectionBy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dorestrictpeerselectionby)<br><br>      |
| [グループ ID のソース](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#select-the-source-of-group-ids)     | 1803        | **[ダウンロード モード]** を *[HTTP とプライベート グループでのピアリングの組み合わせ]* に設定することを要求します。<br><br>ピアの選択をソースごとに特定のデバイス グループに制限します。<br><br>**[カスタム]** を選択した場合は、 **[Group ID (as GUID)]\(グループ ID (GUID として))** を構成します。 異なるドメイン上にあるブランチまたは同じ LAN 上にないブランチに対するローカル ネットワーク ピアリング用に 1 つのグループを作成する必要がある場合は、グループ ID として GUID を使用します。<br><br>**既定値**: 未構成 <br><br>ポリシー CSP: [DOGroupId](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dogroupid)     |

## <a name="bandwidth"></a>帯域幅  

|Setting  |Windows Version  |説明  |
|---------|---------|---------|
|帯域幅の最適化の種類     | *詳細を参照*        | すべての同時ダウンロード アクティビティでの配信最適化で使用できる最大帯域幅を Intune で決定する方法を選択します。<br><br>次のオプションがあります。<br><ul><li>**未構成**</li><br><li>**[絶対]** – すべての同時配信最適化のダウンロード アクティビティで使用できる [[最大ダウンロード帯域幅 (KB/秒)]](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#maximum-download-bandwidth) と [[最大アップロード帯域幅 (KB/秒)]](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#max-upload-bandwidth) を指定します。<br><br>Windows 1607 が必要です<br><br>ポリシー CSP: [DOMaxDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxdownloadbandwidth) および [DOMaxUploadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxuploadbandwidth)</li><br><li>**[割合]** – すべての同時配信最適化のダウンロード アクティビティで使用できる [[フォアグラウンド ダウンロードの最大帯域幅 (%)]](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#maximum-foreground-download-bandwidth) と [[最大バックグラウンド ダウンロード帯域幅 (%)]](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#maximum-foreground-download-bandwidth) を指定します。<br><br>Windows 1803 が必要です<br><br>ポリシー CSP: [DOPercentageMaxForegroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxforegroundbandwidth) および [DOPercentageMaxBackgroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxbackgroundbandwidth)    <br><br><li>**[Percent with business hours]\(営業時間での割合\)** – 最大[フォアグラウンド](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#set-business-hours-to-limit-foreground-download-bandwidth) ダウンロード帯域幅および最大[バックグラウンド](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#set-business-hours-to-limit-background-download-bandwidth) ダウンロード帯域幅では、営業時間の開始時刻と終了時刻を構成した後、営業時間内と営業時間外に使用する帯域幅の割合を構成します。 <br><br>Windows 1803 が必要です <br><br>ポリシー CSP: [DOSetHoursToLimitBackgroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitbackgrounddownloadbandwidth) および [DOSetHoursToLimitForegroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitforegrounddownloadbandwidth)<br><br>   |
|[HTTP のバックグラウンド ダウンロードの遅延 (秒)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#delay-background-download-from-http-in-secs) | 1803        | HTTP 経由でのコンテンツのバックグラウンド ダウンロードの遅延に対して最大時間を構成するには、この設定を使用します。 これは、ピア ツー ピア ダウンロード ソースをサポートするダウンロードに対してのみ適用されます。 この遅延の間、デバイスでは利用可能なコンテンツがあるピアの検索が行われます。 ピア ソースを待機している間、エンド ユーザーにはダウンロードがスタックしているように見えます。   <br><br>**既定値**: "*値の構成なし*"  <br><br>**推奨値**: 60 秒   <br><br>ポリシー CSP: [DODelayBackgroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelaybackgrounddownloadfromhttp) <br><br>    |
| [HTTP のフォアグラウンド ダウンロードの遅延 (秒)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#delay-foreground-download-from-http-in-secs)      | 1803       | HTTP 経由でのコンテンツのフォアグラウンド (対話型) ダウンロードの遅延に対して最大時間を構成します。 これは、ピア ツー ピア ダウンロード ソースをサポートするダウンロードに対してのみ適用されます。 この遅延の間、デバイスでは利用可能なコンテンツがあるピアの検索が行われます。 ピア ソースを待機している間、エンド ユーザーにはダウンロードがスタックしているように見えます。   <br><br>**既定値**: "*値の構成なし*"  <br><br>**推奨値**: 60 秒   <br><br>ポリシー CSP: [DODelayForegroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelayforegrounddownloadfromhttp) <br><br>         |


## <a name="caching"></a>キャッシュ  

|Setting  |Windows Version  |説明  |
|---------|---------|---------|
|[ピア キャッシュに必要な最小 RAM (GB)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#minimum-ram-inclusive-allowed-to-use-peer-caching)      | 1703        | デバイスでピア キャッシュを使用するために必要な最小 RAM サイズを GB 単位で指定します。 <br><br>**既定値**: "*値の構成なし*"  <br><br>**推奨**: 4 GB <br><br>ポリシー CSP: [DOMinRAMAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominramallowedtopeer) <br><br>        |
|[ピア キャッシュに必要な最小ディスク サイズ (GB)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#minimum-disk-size-allowed-to-use-peer-caching)      | 1703        | デバイスでピア キャッシュを使用するために必要な最小ディスク サイズを GB 単位で指定します。 <br><br>**既定値**: "*値の構成なし*"  <br><br>**推奨**: 32 GB   <br><br>ポリシー CSP: [DOMinDiskSizeAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domindisksizeallowedtopeer) <br><br>    |
|[ピア キャッシュの最小のコンテンツ ファイル サイズ (MB)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#minimum-peer-caching-content-file-size)      | 1703        | ピア キャッシュを使用するためにファイルが満たす必要のある最小サイズを MB 単位で指定します。  <br><br>**既定値**: "*値の構成なし*"  <br><br>**推奨値**: 10 MB   <br><br>ポリシー CSP: [DOMinFileSizeToCache](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominfilesizetocache)  <br><br>      |
|[アップロードに必要な最小バッテリ レベル (%)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#allow-uploads-while-the-device-is-on-battery-while-under-set-battery-level)      | 1709        | ピアにデータをアップロードするためにデバイスで必要な最小バッテリ レベルを割合で指定します。 バッテリ レベルが指定した値まで低下した場合、アクティブなアップロードは自動的に一時停止します。   <br><br>**既定値**: "*値の構成なし*"  <br><br>**推奨**: 40%   <br><br>ポリシー CSP: [DOMinBatteryPercentageAllowedToUpload](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominbatterypercentageallowedtoupload) <br><br>        |
|[キャッシュ ドライブの変更](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#modify-cache-drive)        | 1607        | 配信最適化でキャッシュに使用するドライブを指定します。 環境変数、ドライブ文字、または完全なパスを使用できます。  <br><br>**既定値**: %SystemDrive% <br><br>ポリシー CSP: [DOModifyCacheDrive](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domodifycachedrive) <br><br>        |
| [最大キャッシュ時間 (日数)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#max-cache-age)    | 1511         | 各ファイルが正常にダウンロードされた後、デバイス上の配信最適化キャッシュにファイルが保持されている期間を指定します。   <br><br>Intune では、キャッシュの期間を日数で構成します。 定義した日数は、この設定が Windows で定義されるときのように、適切な秒数に変換されます。 たとえば、Intune 構成での 3 日は、デバイスでは 259,200 秒 (3 日) に変換されます。  <br><br>**既定値**: "*値の構成なし*"     <br><br>**推奨**: 7   <br><br>ポリシー CSP: [DOMaxCacheAge](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)  <br><br>          |
| 最大キャッシュ サイズの種類  | *詳細を参照*    | デバイス上で配信最適化によって使用されるディスク領域の量を管理する方法を選択します。 構成しない場合、キャッシュ サイズは使用可能な空きディスク領域の 20% に既定で設定されます。  <br><ul><li>**[未構成]** (既定値)</li><br><li>**[絶対]** – [[絶対最大キャッシュ サイズ (GB)]](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#absolute-max-cache-size) を指定して、デバイスで配信最適化に使用できるドライブ領域の最大量を構成します。 0 (ゼロ) に設定すると、キャッシュ サイズは無制限になりますが、デバイスのディスク領域が少なくなると配信最適化によってキャッシュがクリアされます。 <br><br>Windows 1607 が必要です<br><br> ポリシー CSP: [DOAbsoluteMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-doabsolutemaxcachesize) </li><br><li>**[割合]** – [[最大キャッシュ サイズ (%)]](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#max-cache-size) を指定して、デバイスで配信最適化に使用できるドライブ領域の最大量を構成します。 割合はドライブの空き領域を指し、配信最適化では常にドライブの空き容量が評価され、最大キャッシュ サイズが設定されている割合を超えないようにキャッシュがクリアされます。 <br><br>Windows 1511 が必要です<br><br>ポリシー CSP: [DOMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcachesize)  |
| [VPN ピア キャッシュ](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#enable-peer-caching-while-the-device-connects-via-vpn)  | 1709  | VPN によってドメイン ネットワークに接続されている間はピア キャッシュに参加するようデバイスを構成するには、 **[有効]** を選択します。 有効に設定したデバイスでは、VPN または会社のドメイン ネットワーク上にある他のドメイン ネットワーク デバイスとの間で、ダウンロードまたはアップロードを行うことができます。  <br><br>**既定値**: 未構成  <br><br>ポリシー CSP: [DOAllowVPNPeerCaching](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)    |

## <a name="next-steps"></a>次の手順

[Intune で配信最適化を構成する](delivery-optimization-windows.md)
