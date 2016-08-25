---
title: "Windows 10 ポリシー設定 | Microsoft Intune"
description: "このトピックのポリシー設定の一覧を、登録済みの Windows 10 デスクトップおよび Windows 10 Mobile デバイスの組込み設定およびユーザー設定構成に役立ててください。"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0178bba517b0fc9e02ba67e6f3aba7a8a0ee445f
ms.openlocfilehash: 9daab32361cfdf8567d03a8ea6e6438e34b61aad


---

# Microsoft Intune の Windows 10 ポリシー設定

このトピックのポリシー設定の一覧を、登録済みの Windows 10 デスクトップおよび Windows 10 Mobile デバイスの組込み設定およびユーザー設定構成に役立ててください。

> [!IMPORTANT]
> 登録する、または Intune PC クライアント ソフトウェアをインストールするという 2 つの方法で Windows 10 PC を管理することができます。 それぞれの方法は、異なる機能を提供します (詳細については、[「デバイスを管理する方法を選択する」](/intune/get-started/choose-how-to-manage-devices)を参照してください)。
> Intune PC クライアント ソフトウェアを使用して Windows 10 PC を管理する場合は、このトピックで説明されているポリシーと設定を使用することはできません。 これらの設定を適用するには、Windows 10 デバイスが Intune に登録されている必要があります。

## 全般構成ポリシーの設定

Windows 10 用の Microsoft Intune **全般構成ポリシー**を使用して、登録済みの Windows 10 デスクトップと Windows 10 Mobile デバイスの全般設定を構成します。 


## - パスワード

|設定の名前|説明|
|----------------|----------------------|
|**デバイスのロック解除にパスワードを必要とする**|サポート対象デバイスのパスワードが必要です。|
|**必要なパスワードの種類**|数値のみや英数字など、必要なパスワードの種類を指定します。|
|**必要なパスワードの種類** - **文字セットの最小数**|文字セットには、小文字、大文字、数字、および記号の 4 種類があります。 この設定では、パスワードに含める必要がある文字セットの数を指定します。|
|**パスワードの最小文字数**|デバイスのパスワードに含める必要がある最小文字数を指定します。<br>(Windows 10 Mobile のみ)|
|**デバイスをワイプするまでの連続サインイン エラーの数**|ログインの試みがこの回数だけ失敗した場合は、デバイスがワイプされます。|
|**画面がオフになるまでの非アクティブな時間 (分)**|デバイスがどれだけの時間アイドル状態であると、画面がロックされるかを指定します。|
|**パスワードの有効期限 (日数)**|デバイスのパスワードを設定後、変更が必要になるまでの日数を指定します。|
|**パスワードの履歴を記憶する**|エンド ユーザーに対して、以前に使用されたことのあるパスワードの作成を制限するかどうかを指定します。|
|**パスワードの履歴を保存する** - **前のパスワードを再利用できないようにする**|デバイスで記憶される、以前に使用したパスワードの数を指定します。|
|**デバイスがアイドル状態から戻るときにパスワードを必須とする**|有効にすると、ユーザーはアイドル状態からデバイスのロックを解除するとき、パスワードを入力する必要があります。<br>(Windows 10 Mobile のみ)|

## - 暗号化

|設定の名前|説明|
|----------------|----------------------|
|**モバイル デバイスの暗号化を要求する**|対象デバイスの暗号化を有効にします。<br>(Windows 10 Mobile のみ)|

## - システム

|設定の名前|説明|
|----------------|----------------------|
|**画面のキャプチャを許可する**|ユーザーがデバイスの画面を画像としてキャプチャできるようにします。<br>(Windows 10 Mobile のみ)|
|**手動での登録解除を許可する**|ユーザーがデバイスから会社アカウントを手動で削除できるようにします。|
|**ルート証明書の手動インストールを許可する**|ユーザーがルート証明書を手動でインストールできるかどうかを指定します。<br>(Windows 10 Mobile のみ)|
|**診断と利用状況データの Microsoft への送信を許可する**|デバイスから Microsoft に送信される、診断データと使用状況データの量を決定します。<br><br>**[いいえ]** - データは Microsoft に送信されません。<br>**[基本]** - 一部の情報のみを Microsoft に送信します。<br>**[拡張]** - より詳細な診断データを Microsoft に送信します。<br>**[完全 (推奨)]** - **[拡張]** で送信されるデータに加えて、デバイスの状態に関する追加データを送信します。|


## - アカウントと同期

|設定の名前|説明|
|----------------|----------------------|---------------------|
|**Microsoft アカウントを許可する**|ユーザーがデバイスに Microsoft アカウントを関連付けられるようにします。|
|**Microsoft 以外のアカウントの手動追加を許可する**|Microsoft アカウントに関連付けられていないデバイスに、ユーザーが電子メール アカウントを追加できるようにします。|
|**Microsoft アカウントに対して設定同期を許可する**|Microsoft アカウントに関連付けられたデバイスとアプリの設定をデバイス間で同期できるようにします。|

## - Microsoft Edge

|設定の名前|説明|
|----------------|----------------------|
|**Web ブラウザーを許可する**|デバイスで Edge Web ブラウザーを使用できるようにします。<br>(Windows 10 Mobile のみ)|
|**アドレス バーで検索候補を許可する**|検索語句を入力したときに、検索エンジンからサイトが提案されるようになります。|
|**Internet Explorer へのイントラネット トラフィックの送信を許可する**|ユーザーが Internet Explorer でイントラネット Web サイトを開けるようになります。<br>(Windows 10 デスクトップのみ)|
|**追跡禁止を許可する**|ユーザーがアクセスする Web サイトへトラッキング拒否ヘッダーを送信できるように、Edge ブラウザーを構成します。|
|**SmartScreen を有効にする**|デバイスの SmartScreen ブラウザーの設定を有効にします。|
|**アクティブ スクリプティングを使用する**|JavaScript などのスクリプトが Edge ブラウザーで実行できるようにします。|
|**ポップアップを許可する**|ブラウザーのポップアップ ブロックを有効または無効にします。<br>(Windows 10 デスクトップのみ)|
|**Cookie を使用する**|Cookie を使用するか、または無効にします。|
|**オートコンプリートを使用する**|ユーザーがブラウザーのオートコンプリートの設定を変更できるようにします。<br>(Windows 10 デスクトップのみ)|
|**Password Manager を許可する**|Edge Password Manager 機能を有効または無効にします。|
|**エンタープライズ モード サイト リストの場所**|エンタープライズ モードで開く Web サイトの一覧を検索できる場所を指定します。 ユーザーは、この一覧を編集できません。<br>(Windows 10 デスクトップのみ)|

## - アプリ

|設定の名前|説明|
|----------------|----------------------|---------------------|
|**アプリケーション ストアを許可する**|ユーザーがデバイスからアプリ ストアにアクセスできるようにします。<br>(Windows 10 Mobile のみ)|



## - 移動体通信

|設定の名前|説明|
|----------------|----------------------|---------------------|
|**データ ローミングを許可する**|データへのアクセス中にネットワーク間のローミングを許可します。|
|**移動体通信で VPN を許可する**|移動体通信ネットワークに接続したときに、デバイスが VPN 接続にアクセスできるようにするかどうかを制御します。|
|**移動体通信で VPN ローミングを許可する**|移動体通信ネットワークでのローミング中に、デバイスが VPN 接続にアクセスできるようにするかどうかを制御します。|

## - ハードウェア

|設定の名前|説明|
|----------------|----------------------|
|**カメラを許可する**|デバイスのカメラを使用できるようにするかどうかを指定します。|
|**リムーバブル記憶域を許可する**|SD カードなどの外部記憶装置をデバイスで使用できるようにするかどうかを指定します。|
|**Wi-Fi を許可する**|デバイスの Wi-Fi 機能の使用を許可します。<br>(Windows 10 Mobile のみ)|
|**インターネット共有を許可する**|デバイスでインターネット接続の共有を使用できるようにします。|
|**Wi-Fi の手動設定を許可する**|ユーザーが独自に Wi-Fi 接続を構成できるようにするか、Wi-Fi プロファイルで構成された接続のみを使用できるようにするかを制御します。<br>(Windows 10 Mobile のみ)|
|**無料 Wi-Fi スポットへの自動接続を許可する**|デバイスが無料の Wi-Fi ホットスポットに自動的に接続し、接続の使用条件に自動的に同意するようにします。|
|**位置情報を許可する**|デバイスが位置情報サービスの情報を使用できるかどうかを指定します。|
|**NFC を許可する**|デバイスが近距離無線通信機能を使用できるようにします。|
|**Bluetooth を許可する**|デバイスの Bluetooth 機能の使用を有効にします。|
|**Bluetooth 検出可能モードを許可する**|その他の Bluetooth 対応デバイスにより、デバイスが検出されるようにします。|
|**Bluetooth 広告を許可する**|デバイスが Bluetooth 経由で公開通知を受信できるようにします。|
|**電話リセットを許可する**|ユーザーがデバイスを工場出荷時設定にリセットできるかどうかを制御します。|
|**USB 接続を許可する**|デバイスが USB 接続を介して外部記憶域装置にアクセスできるかどうかを制御します。|
|**盗難防止モードを許可する**|Windows の盗難防止モードを有効にするかどうかを構成します。|

## - 機能

|設定の名前|説明|
|----------------|----------------------|---------------------|
|**コピーと貼り付けを許可する**|デバイス上でのコピーと貼り付けの使用を有効または無効にします。<br>(Windows 10 Mobile のみ)|
|**音声録音を許可する**|デバイスの音声録音機能を有効または無効にします。<br>(Windows 10 Mobile のみ)|
|**Cortana を許可する**|Cortana による音声アシスタントを有効または無効にします。|
|**アクション センターの通知を許可する**|デバイス ロック画面上でのアクション センターの通知を有効または無効にします。<br>(Windows 10 Mobile のみ)|

## - Windows Defender

すべての設定は Windows 10 デスクトップのみに適用されます。

|設定の名前|説明|
|-|-|
|**リアルタイム監視を許可する**|マルウェアやスパイウェアなど、望ましくないソフトウェアについてのリアルタイム スキャンを有効にします。|
|**動作監視を許可する**|デバイス上で特定の既知のパターンで行われる疑わしい動作を、Defender がチェックできるようにします。|
|**ネットワーク検査システムを有効にする**|ネットワーク検査システム (NIS) は、ネットワークを利用した悪用からデバイスを保護するのに役立ちます。NIS は、Microsoft Endpoint Protection Center で把握している脆弱性のシグネチャを使用して、悪意のあるトラフィックを検出し、ブロックします。|
|**すべてのダウンロードをスキャンする**|Defender がインターネットからダウンロードされたすべてのファイルをスキャンするかどうかを制御します。|
|**スクリプトのスキャンを許可する**|Defender が Internet Explorer で使用されているスクリプトをスキャンできるようにします。|
|**ファイルとプログラムのアクティビティを監視する**|デバイス上のファイルとプログラムのアクティビティの監視を Defender に許可するには、この設定を有効にします。|
|**解決済みマルウェアを追跡する日数**|指定した日数の間、Defender で解決済みマルウェアの追跡を続けられるようにし、以前に影響を受けたデバイスを手動でチェックできるようにします。 日数を **0** に設定すると、マルウェアは検疫フォルダーに残り、自動的に削除されなくなります。 |
|**クライアント UI アクセスを許可する**|Windows Defender ユーザー インターフェイスをエンド ユーザーに対して非表示にするかどうかを制御します。<br>この設定の変更は、エンド ユーザーの PC が次に再起動されたときに有効になります。|
|**毎日のクイック スキャンのスケジュール**|毎日のクイック スキャンが選択した時間に実行されるように、スケジュール設定できるようにします。|
|**システム スキャンを予定に入れる**|システムのフル スキャンまたはクイック スキャンが選択した日時に定期的に実行されるように、スケジュール設定できるようにします。|
|**スキャン中の CPU 使用率の制限**|スキャンに使用できる CPU の使用率を制限できるようにします (**1** から **100** まで)。|
|**アーカイブ ファイルをスキャンする**|Zip ファイルや Cab ファイルなどのアーカイブ済みのファイルを Defender がスキャンできるようにします。|
|**電子メール メッセージをスキャンする**|デバイスに届いた電子メール メッセージを Defender が直ちにスキャンできるようにします。|
|**リムーバブル ドライブをスキャンする**|USB スティックなどのリムーバブル ドライブを Defender がスキャンできるようにします。|
|**マップされたネットワーク ドライブをスキャンする**|マップ済みネットワーク ドライブ上のファイルを Defender がスキャンできるようにします。<br>ドライブ上のファイルが読み取り専用である場合、Defender は検出したマルウェアを一切削除できません。|
|**ネットワークの共有フォルダーから開いたファイルをスキャンする**|共有ネットワーク ドライブ上のファイルを Defender がスキャンできるようにします (UNC パスからアクセスされたファイルなど)。<br>ドライブ上のファイルが読み取り専用である場合、Defender は検出したマルウェアを一切削除できません。|
|**署名更新間隔**|Defender が新しいシグネチャ ファイルをチェックする間隔を指定します。|
|**クラウド保護を許可する**|管理対象のデバイスからマルウェアのアクティビティに関する情報が Microsoft Active Protection Service に送信されるのを許可またはブロックします。 この情報は、将来的に本サービスの品質向上を目的として使用されます。|
|**ユーザーにサンプルの提出を指示する**|悪意の有無を判断するために、Microsoft による詳しい分析が必要な可能性のあるファイルを、Microsoft に自動的に送信するかどうかを制御します。|
|**望ましくない可能性があるアプリケーションの検出**|この設定を使えば、Windows Defender によって望ましくない可能性があると判断されたソフトウェアの実行から、登録済みの Windows デスクトップ デバイスを保護することができます。 このようなアプリケーションの実行からコンピューターを保護したり、望ましくない可能性があるアプリケーションがいつインストールされたのかを監査モードでレポートしたりできます。|
|**スキャンまたはリアルタイム保護から除外するファイルとフォルダー**|**C:\Path** や **%ProgramFiles%\Path\filename.exe** などのファイルやフォルダーを、除外リストに 1 つ以上追加します。 これらのファイルとフォルダーは、リアルタイムまたはスケジュールされたスキャンの対象外となります。|
|**スキャンの実行中、またはリアルタイム保護の使用時に除外するファイル拡張子**|**jpg** や **txt** などのファイル拡張子を、除外リストに 1 つ以上追加します。 これらの拡張子が付いたファイルは、リアルタイムまたはスケジュールされたスキャンの対象外となります。|
|**スキャンの実行中、またはリアルタイム保護の使用時に除外するプロセス**|**.exe**、**.com**、**.scr** などの種類のプロセスを、除外リストに 1 つ以上追加します。 これらのプロセスは、リアルタイムまたはスケジュールされたスキャンの対象外となります。| 


## - 更新

|設定の名前|説明|
|----------------|---------------|
|**自動更新を直ちにインストールすることを許可する**|自動更新を許可するには、この設定を有効にします。 次に、以下のいずれかの設定を構成して、更新動作を制御します。<br /><br />**ダウンロードを通知する**<br /><br />**メンテナンス時刻に自動的にインストールする**<br /><br />**メンテナンス時刻に自動的にインストールし、再起動する**<br /><br />**スケジュールした時刻に自動的にインストールして再起動する** **注:** このオプションを選択した場合は、**[エンド ユーザーに通知を表示しない]** と **[スケジュールされた更新プログラムのインストール日を定義してください]** の設定も構成できます。<br>(Windows 10 デスクトップのみ)|
|**プレリリース機能を有効にする**|Microsoft が Windows 10 デバイスにプレリリース版の設定と機能を展開できるようにします。 設定のみを許可するか、またはプレリリース版のすべての設定と機能のインストールを許可するかを選択できます。|

## カスタム ポリシー設定
Windows 10 および Windows 10 Mobile 用の Microsoft Intune **カスタム構成ポリシー**を使用して、Windows 10 および Windows 10 Mobile のデバイスで各機能の制御に使用できる OMA-URI (Open Mobile Alliance Uniform Resource Identifier) 設定を展開します。 これらの設定は、多くのデバイス製造元がデバイスの機能を制御するために使用する標準の設定です。

この機能は、Intune 全般構成ポリシーで構成できない Windows 10 設定を展開できるようにするためのものです。



## - 全般

|設定の名前|説明|
    |----------------|--------------------|
    |**名前**|ポリシーの一意の名前を入力すると、Intune コンソール内で容易に識別できます。|
    |**説明**|ポリシーの概要や、ポリシーを特定するのに役立つその他の関連情報についての説明を入力します。|

## - OMA-URI 設定

|設定の名前|説明|
    |--------|--------------------|
    |**設定の名前**|OMA-URI 設定の一意の名前を入力すると、設定リスト内で容易に識別できます。|
    |**設定の説明**|設定の概要と、それを特定するために役立つその他の関連情報についての説明を入力します。|
    |**データ型**|この OMA-URI 設定を指定する日付型を選択します。 次の中から選択します。<br /><br />-   **文字列型**<br />-   **文字列型 (XML)**<br />-   **日付と時刻**<br />-   **整数型**<br />-   **浮動小数点**<br />-   **ブール型**|
    |**OMA-URI (大文字と小文字を区別する)**|設定対象の OMA-URI を指定します。|
    |**値**|指定した OMA-URI に関連付ける値を指定します。|


## - Windows 10 URI 設定
このトピックでは、Microsoft Intune の **Windows 10 のカスタム ポリシー**で Windows 10 および Windows 10 Mobile デバイス用に構成できる設定を示します。

Windows のカスタム URI ポリシーを使用する場合は、すべてのデバイスが Intune に登録されている必要があります。

## - ポリシー

|ポリシー名|説明|
|---------------|------------|-----------|
|**​Allow Auto Update**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** - **5** (既定: **1**)|
|**Schedule Install Day**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 毎日 (既定値)<br>**1**: 日曜日<br>**2**: 月曜日<br>**3**: 火曜日<br>**4**: 水曜日<br>**5**: 木曜日<br>**6**: 金曜日<br>**7**: 土曜日|
|**Schedule Install Time**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** ～ **23** 時間 (**0** は午前 0 時) (既定: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: ユーザーはパスワードの猶予期間タイマーを設定できず、値は "毎回" に設定されます。<br>**1**: ユーザーはパスワードの猶予期間タイマーを設定できます (既定)。|
|**WiFi/AllowWiFi**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: **Wi-Fi 接続の使用**を許可しません。<br>**1**: **Wi-Fi 接続の使用を許可** します (既定)。|
|**WiFi/AllowInternetSharing**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : インターネット共有を許可しません。<br>**1**: インターネット共有を許可します (既定)。|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**WiFi/AllowManualWiFiConfiguration**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: MDM でプロビジョニングされていない Wi-Fi 接続を許可しません。<br>**1**: MDM で既にプロビジョニングされたネットワーク SSID 以外の新しいネットワーク SSID の追加を許可します (既定)。|
|**System/AllowLocation**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/System/AllowLocation<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**System/AllowTelemetry**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/System/AllowTelemetry<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません (Enterprise のみの設定)<br>**1** : 制限あり<br>**2**: すべて (既定)<br>**3**: すべてと診断情報|
|**System/AllowExperimentation**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/System/AllowExperimentation<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 設定のみ (既定)<br>**2**: 設定と実験|
|**Security/AntiTheftMode**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Security/AntiTheftMode<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 盗難防止モードを許可しません。<br>**1**: ユーザーの設定 (既定)|
|**Connectivity/AllowUSBConnection**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**System/AllowUserToResetPhone**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Connectivity/AllowCellularDataRoaming**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Connectivity/AllowVPNOverCellular**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: VPN で携帯電話による接続を許可しません。<br>**1**: VPN で携帯電話を含む任意の接続を使用できます (既定)。|
|**Connectivity/AllowVPNRoamingOverCellular**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Connectivity/AllowVPNRoamingOverCellular**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Connectivity/AllowBluetooth**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: ユーザーが Bluetooth を有効にすることを許可しません。<br>**1**: 予約済み。 ユーザーが Bluetooth を有効にして構成することができます (Windows Phone 8.1 (MDM または EAS 対応)、Windows 10 デスクトップ、Windows 10 Mobile ではサポートされていません)。<br>**2**: 許可済み。 ユーザーが Bluetooth を有効にして構成することができます (既定)。|
|**Experience/AllowScreenCapture**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Experience/AllowTaskSwitcher**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Experience/AllowVoiceRecording**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Experience/AllowSyncMySettings**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : ローミングを許可しません。<br>**1**: ローミングを許可します (既定)。|
|**Experience/AllowManualMDMUnenrollment**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Accounts/AllowMicrosoftAccountConnection**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Security/AllowManualRootCertificateInstallation**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Security/AllowAddProvisioningPackages**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Search/DisableBackoff**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Search/DisableBackoff<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** (既定)<br>**1**|
|**Search/PreventRemoteQueries**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**<br>**1** (既定)|
|**Search/AllowUsingDiacritics**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br> **0** (既定)<br>**1**|
|**Search/AlwaysUseAutoLangDetection**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** (既定)<br>**1**|
|**Search/DisableRemovableDriveIndexing**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** (既定)<br>**1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**<br>**1** (既定)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** (既定)<br>**1**|
|**Security/AllowRemoveProvisioningPackage**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Security/RequireProvisioningPackageSignature**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** (既定)<br>**1**|
|**AboveLock/AllowActionCenterNotifications**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**TextInput/AllowIMENetworkAccess**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>オープン拡張辞書がオフになります。<br>ユーザーは次の操作を実行できません。<br>新しいオープン拡張辞書を追加する<br /><br />新しい検索統合構成ファイルを追加する<br>クラウドの候補機能を使用する<br>ユーザーが登録した単語を送信する<br>補足:<br>このポリシー設定を有効にする前に追加されたオープン拡張辞書は、変換には使用されません。<br>このポリシー設定を有効にする前にインストールされた検索統合構成ファイルは使用されません。<br>**1**: 許可します。<br>オープン拡張辞書を追加して、既定で使用できます。 既定で検索統合機能も使用できます。<br>ユーザーは次の操作を実行できます。<br>クラウドの候補機能を使用する<br>ユーザーが登録した単語を送信する。|
|**TextInput/AllowIMELogging**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 誤変換記録機能が無効になります。 自動的に調整されたデータおよび入力履歴データはファイルには保存されません。<br>**1**: 誤変換記録機能が有効になります。 自動的に調整されたデータおよび入力履歴データはファイルに保存されます (既定)。|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**TextInput/AllowJapaneseIVSCharacters**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**TextInput/AllowJapaneseUserDictionary**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 文字はフィルター処理されません (既定)。<br>**1**: Shift JIS の文字を除くすべての文字をフィルター処理します。|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br /><br />**0**: 文字はフィルター処理されません (既定)。<br>**1**: JIS0208 の文字を除くすべての文字をフィルター処理します。|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 文字はフィルター処理されません (既定)。<br>**1**: JIS0208 の文字または外字の文字を除くすべての文字をフィルター処理します。|
|**TextInput/AllowInputPanel**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Bluetooth/AllowDiscoverableMode**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Bluetooth/AllowAdvertising**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Settings/AllowDataSense**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Settings/AllowDataSense<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Settings/AllowVPN**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Settings/AllowVPN<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Settings/AllowWorkplace**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Settings/AllowDateTime**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Settings/AllowDateTime<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Settings/AllowLanguage**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Settings/AllowLanguage<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Settings/AllowRegion**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Settings/AllowRegion<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Settings/AllowSignInOptions**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Settings/AllowYourAccount**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Settings/AllowPowerSleep**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Settings/AllowAutoPlay**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Experience/AllowCortana**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Experience/AllowCortana<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Search/SafeSearchPermissions**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 厳密。成人向けコンテンツに対して最高レベルのフィルター処理を実行します。<br>**1**: 中程度。成人向けコンテンツに対して中程度のフィルター処理を実行します (有効な検索結果はフィルター処理されません) (既定)。|
|**Experience/AllowCopyPaste**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**Force Start Size**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Start/ForceStartSize<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: ユーザーによるサイズ変更を許可します (既定)。<br>**1**: 非全画面表示を強制します。<br>**2**: 全画面表示を強制します。|
|**Update/RequireDeferUpgrade**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: アップグレードを遅延せず、CB (現在のブランチ) を維持します (既定)。<br>**1**: 更新とアップグレードの遅延を有効にします。デバイスは CBB (ビジネスの現在のブランチ) の規則に従います。<br /><br />詳細については、次をご覧ください。<br>[Windows 10 サービスの概要](https://technet.microsoft.com/library/mt598226.aspx)<br>[Windows 10 の展開計画](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>(デスクトップおよびモバイル)|**説明:** ソフトウェアの更新を最大 4 週間遅延させるポリシー。<br /><br />**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br> **0**: 直ちに更新プログラムを適用します (既定)。<br>**1 ** - **4**: ソフトウェアの更新を遅延する期間 (週)。<br /><br />詳細については、次をご覧ください。<br>[Windows 10 サービスの概要](https://technet.microsoft.com/library/mt598226.aspx)<br>[Windows 10 の展開計画](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>(デスクトップおよびモバイル)|**説明:** 機能のアップグレードを最大 8 か月間遅延させるポリシー。<br /><br />**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 直ちに更新プログラムを適用します (既定)。<br>**1** - **8**: 機能のアップグレードを遅延する期間 (月)。<br /><br />詳細については、次をご覧ください。<br>[Windows 10 サービスの概要](https://technet.microsoft.com/library/mt598226.aspx)<br>[Windows 10 の展開計画](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>(デスクトップおよびモバイル)|**説明:** CBB コンピューターが更新とアップグレードの受信を 5 週間停止できるようにします。 これは、更新プログラムに問題がある場合に使用してください。<br /><br />**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Update/PauseDeferrals<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 直ちに更新プログラムを適用します (既定)。<br>**1**: 更新とアップグレードを一時停止します (一時停止の期限は 5 週間です)。|

## - Windows Defender

|ポリシー名|説明|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**AllowBehaviorMonitoring**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**AllowIntrusionPreventionSystem**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**AllowIOAVProtection**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**AllowScriptScanning**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**AllowOnAccessProtection**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**RealTimeScanDirection**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: すべてのファイルを監視 (双方向) (既定)<br>**1** : 受信ファイルの監視<br>**2** : 送信ファイルの監視|
|**DaysToRetainCleanedMalware**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**  -  **90**: マルウェアを保持する時間を表します。<br>**既定値:** **0**: 永続的に検疫フォルダー内に保持します。自動的に削除しません。|
|**AllowUserUIAccess**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**ScanParameter**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/ScanParameter<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**1**: クイック スキャン (既定)<br>**2**: フル スキャン|
|**ScheduleScanDay**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 毎日 (既定)<br>**1**: 月曜日<br>**2**: 火曜日<br>**3**: 水曜日<br>**4**: 木曜日<br>**5**: 金曜日<br>**6**: 土曜日<br>**7**: 日曜日<br>**8** : スキャンはスケジュールされません|
|**ScheduleScanTime**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 午前 12:00<br>**60** : 午前 1:00<br>**120**: 午前 2:00 (既定)<br>**180** : 午前 3:00<br>**240** : 午前 4:00<br>**300** : 午前 5:00<br>**360** : 午前 6:00<br>**420** : 午前 7:00<br>**480** : 午前 8:00<br>**540** : 午前 9:00<br>**600** : 午前 10:00<br>**660** : 午前 11:00<br>**720** : 午後 0:00<br>**780** : 午後 1:00<br>**840** : 午後 2:00<br>**900** : 午後 3:00<br>**960** : 午後 4:00<br>**1020** : 午後 5:00<br>**1080** : 午後 6:00<br>**1140** : 午後 7:00<br>**1200** : 午後 8:00<br>**1260** : 午後 9:00<br>**1320** : 午後 10:00<br>**1381** : メンテナンス期間|
|**ScheduleQuickScanTime**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime<br>**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 午前 12:00<br>**60** : 午前 1:00<br>**120**: 午前 2:00 (既定)<br>**180** : 午前 3:00<br>**240** : 午前 4:00<br>**300** : 午前 5:00<br>**360** : 午前 6:00<br>**420** : 午前 7:00<br>**480** : 午前 8:00<br>**540** : 午前 9:00<br>**600** : 午前 10:00<br>**660** : 午前 11:00<br>**720** : 午後 0:00<br>**780** : 午後 1:00<br>**840** : 午後 2:00<br>**900** : 午後 3:00<br>**960** : 午後 4:00<br>**1020** : 午後 5:00<br>**1080** : 午後 6:00<br>**1140** : 午後 7:00<br>**1200** : 午後 8:00<br>**1260** : 午後 9:00<br>**1320** : 午後 10:00<br>**1380** : 午後 11:00|
|**AVGCPULoadFactor**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor<br /><br />**データ型:** 整数<br /><br />**有効な値: 0** - **100** (既定: **50**)|
|**AllowArchiveScanning**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**AllowEmailScanning**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning<br /><br />**データ型:** 整数<br>**有効な値:**<br>**0**: 許可しません (既定)。<br>**1** : 許可します。|
|**AllowFullScanRemovableDriveScanning**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 許可しません (既定)。<br>**1** : 許可します。|
|**AllowFullScanOnMappedNetworkDrives**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**AllowScanningNetworkFiles**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1:**: 許可します (既定): "許可" に設定されている場合は、RTP がオンのときにも実行されます。|
|**SignatureUpdateInterval**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 定期的に署名を確認しません。<br>**1**: 1 時間ごとにシグネチャを確認します。<br>**2** : 2 時間ごとに署名を確認します。3 以上の値も同様に、間隔を示します。<br>**24** : 毎日署名を確認します。<br>**既定値:** 8 - 8 時間ごとに署名を確認します。|
|**AllowCloudProtection**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0** : 許可しません。<br>**1**: 許可します (既定)。|
|**SubmitSamplesConsent**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 常に確認のメッセージを表示します (既定)。<br>**1** : 安全なサンプルを自動的に送信します。<br>**2** : 送信することはありません。<br>**3** : すべてのサンプルを自動的に送信します。|
|**ExcludedExtensions**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions<br /><br />**データ型:** 文字列<br /><br />**有効な値:**<br>*&lt;セミコロンで区切られた拡張子の一覧&gt;* 例:  **obj;lib**<br>**既定値:** 拡張子は除外されません。|
|**ExcludedPaths**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths<br /><br />**データ型:** 文字列<br /><br />**有効な値:**<br /><br />*&lt;セミコロンで区切られたパスの一覧&gt;*<br /><br />例: **c:\test;c:\test1.exe**<br /><br />**既定値:** 除外されるパスはありません。|
|**ExcludedProcesses**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses<br /><br />**データ型:** 文字列<br /><br />**有効な値:**<br>*&lt;セミコロンで区切られたパスの一覧&gt;*<br>例: **c:\test.exe;c:\test1.exe**<br>**既定値:** 除外されるプロセスはありません。|

## - Edge ブラウザー

|ポリシー名|説明|
|---------------|------------|-----------|
|**ブラウズを許可する**<br>(モバイルのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Browser/AllowBrowser<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: ブラウズを無効にします。<br>**1**: ブラウズを有効にします (既定)。|
|**AllowSearchSuggestionsinAddressBar**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 検索候補を表示しません。<br>**1**: 検索候補を表示します (既定)。|
|**SendIntranetTraffictoInternetExplorer**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 無効 (Edge ブラウザーでイントラネット サイトを開きます) (既定)。<br>**1**: 有効 (Internet Explorer でイントラネット サイトを開きます)。|
|**追跡禁止を許可する**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 無効 (DNT を送信しません) (既定)。<br>**1**: 有効 (DNT を送信します)。|
|**SmartScreen を構成する**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 許可しません。<br>**1**: 許可します (既定)。|
|**ポップアップを許可する**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Browser/AllowPopups<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: ポップアップをブロックします (既定)。<br>**1**: ポップアップを許可します。|
|**Cookie を使用する**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Browser/AllowCookies<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: ブロックしません。 すべての Web サイトの Cookie を許可します (既定)。<br>**1**: サード パーティの Cookie のみブロックします。<br>**2**: すべての Cookie をブロックします。|
|**パスワードの保存を許可する**<br>(デスクトップおよびモバイル)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: Password Manager を無効にします。 <br>**1**: Password Manager を有効にします (既定)。|
|**オートコンプリートを使用する**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Browser/AllowAutofill<br /><br />**データ型:** 整数<br /><br />**有効な値:**<br>**0**: 無効 (既定)。<br>**1**: 有効。|
|**エンタープライズ サイトのリストを構成する**<br>(デスクトップのみ)|**URI の完全なパス:** ./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList<br /><br />**データ型:** 文字列<br /><br />**使用できる値: <br>0**: 未構成<br>**1**: IE のエンタープライズ モード サイト リストが構成されている場合はそれを使用します (既定)。<br>**2**: エンタープライズ サイト リストの場所を指定します。|

### 関連項目
[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Aug16_HO2-->


