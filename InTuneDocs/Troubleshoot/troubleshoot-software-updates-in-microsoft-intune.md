---
title: "ソフトウェアの更新に関するトラブルシューティング | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ca4d4197ac1ece3e9abf44ad462d8ec7a807b4b2
ms.openlocfilehash: d8470be236ac7b7a9431e07c5ca651cb6bd9fbc0


---

# Microsoft Intune でのソフトウェア更新のトラブルシューティング
Microsoft Intune のソフトウェア更新の問題を解決するには、このセクションの情報を参考にしてください。

この情報で問題が解決しない場合、さらに役立つ方法を探すには、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」を参照してください。

## 更新エージェントのエラー コード

次の表に、Intune **更新エージェント**のエラー コードを示します。 発生したエラーのコードが、この表に見つからない場合は、「 [Windows Update Agent Result Codes (Windows 更新エージェントの結果コード)](http://go.microsoft.com/fwlink/?LinkID=221542)」を参照してください。

|エラー コード|シンボリック名|詳細情報|
|--------------|-----------------|--------------------|
|**0x00cf0001**|OM_S_SERVICE_STOP|エージェントが正常に停止されました。|
|**0x00cf0003**|OM_S_UPDATE_ERROR|処理は完了しましたが、更新プログラムの適用中にエラーが発生しました。|
|**0x00cf0004**|OM_S_MARKED_FOR_DISCONNECT|コールバックの実行中に操作の切断要求を受け取ったため、コールバックが後で切断するようにマークされました。|
|**0x00cf0005**|OM_S_REBOOT_REQUIRED|更新プログラムのインストールを完了するには、システムを再起動する必要があります。|
|**0x00cf0006**|OM_S_ALREADY_INSTALLED|インストールしようとしている更新プログラムは、システムに既にインストールされています。|
|**0x00cf0007**|OM_S_ALREADY_UNINSTALLED|削除しようとしている更新プログラムは、システムから既に削除されています。|
|**0x00cf2015**|OM_S_UH_INSTALLSTILLPENDING|更新プログラムのインストールが進行中です。|
|**0x80cf0001**|OM_E_NO_SERVICE|エージェントがサービスを提供できませんでした。|
|**0x80cf0002**|OM_E_MAX_CAPACITY_REACHED|サービスの最大容量を超えました。|
|**0x80cf0003**|OM_E_UNKNOWN_ID|ID が見つかりません。|
|**0x80cf0004**|OM_E_NOT_INITIALIZED|オブジェクトを初期化できませんでした。|
|**0x80cf0007**|OM_E_INVALIDINDEX|コレクションのインデックスが無効です。|
|**0x80cf0008**|OM_E_ITEMNOTFOUND|クエリされた項目のキーが見つかりませんでした。|
|**0x80cf0009**|OM_E_OPERATIONINPROGRESS|競合する操作が実行されていました。 操作によっては、同時に実行できないものがあります (複数のインストールの同時進行など)。|
|**0x80cf000B**|OM_E_CALL_CANCELLED|操作が取り消されました。|
|**0x80cf000C**|OM_E_NOOP|操作は必要ありません。|
|**0x80cf000D**|OM_E_XML_MISSINGDATA|エージェントが、更新プログラムの XML データ内に必要な情報を見つけられませんでした。|
|**0x80cf000E**|OM_E_XML_INVALID|エージェントが更新プログラムの XML データ内で見つけた情報が無効です。|
|**0x80cf000F**|OM_E_CYCLE_DETECTED|メタデータに、更新プログラムの循環している関係が見つかりました。|
|**0x80cf0010**|OM_E_TOO_DEEP_RELATION|更新プログラムの入れ子関係が深すぎるため評価できません。|
|**0x80cf0011**|OM_E_INVALID_RELATIONSHIP|更新プログラムの無効な関係が見つかりました。|
|**0x80cf0012**|OM_E_REG_VALUE_INVALID|読み取られたレジストリ値が無効です。|
|**0x80cf0013**|OM_E_DUPLICATE_ITEM|重複する項目を一覧に追加しようとしました。|
|**0x80cf0014**|OM_E_INVALID_INSTALL_REQUESTED|呼び出し元がインストールを要求した更新プログラムをインストールできません。|
|**0x80cf0016**|OM_E_INSTALL_NOT_ALLOWED|別のインストールの実行中、またはシステムの必須の再起動が保留中になっている間に、インストールしようとしました。|
|**0x80cf0017**|OM_E_NOT_APPLICABLE|適用可能な更新プログラムがないため、操作が実行されませんでした。|
|**0x80cf0018**|OM_E_NO_USERTOKEN|必要なユーザー トークンがないため、操作に失敗しました。|
|**0x80cf0019**|OM_E_EXCLUSIVE_INSTALL_CONFLICT|排他的な更新プログラムを他の更新プログラムと同時にインストールすることはできません。|
|**0x80cf001A**|OM_E_POLICY_NOT_SET|ポリシーの値が設定されていません。|
|**0x80cf001D**|OM_E_INVALID_UPDATE|更新プログラムに無効なメタデータが含まれています。|
|**0x80cf001E**|OM_E_SERVICE_STOP|サービスまたはシステムがシャットダウン中だったため、操作を完了できませんでした。|
|**0x80cf001F**|OM_E_NO_CONNECTION|ネットワーク接続を利用できなかったため、操作を完了できませんでした。|
|**0x80cf0020**|OM_E_NO_INTERACTIVE_USER|対話するユーザーが誰もログオンしていないため、操作を完了できませんでした。|
|**0x80cf0021**|OM_E_TIME_OUT|タイムアウトしたため、操作を完了できませんでした。|
|**0x80cf0022**|OM_E_ALL_UPDATES_FAILED|すべての更新プログラムの操作に失敗しました。|
|**0x80cf0024**|OM_E_NO_UPDATE|更新プログラムがありません。|
|**0x80cf0025**|OM_E_USER_ACCESS_DISABLED|グループ ポリシーの設定により、Windows Update にアクセスできませんでした。|
|**0x80cf0026**|OM_E_INVALID_UPDATE_TYPE|更新プログラムの種類が無効です。|
|**0x80cf0028**|OM_E_UNINSTALL_NOT_ALLOWED|要求元が WSUS サーバーではないため、更新プログラムをアンインストールできませんでした。|
|**0x80cf0029**|OM_E_INVALID_PRODUCT_LICENSE|一部の更新プログラムを検索できなかったか、ライセンスされていないアプリケーションがシステムに存在する可能性があります。|
|**0x80cf002C**|OM_E_BIN_SOURCE_ABSENT|増分圧縮された更新プログラムをインストールできませんでした。ソースが必要です。|
|**0x80cf002D**|OM_E_SOURCE_ABSENT|完全なファイルの更新プログラムをインストールできませんでした。ソースが必要です。|
|**0x80cf002E**|OM_E_WU_DISABLED|管理されていないサーバーにはアクセスできません。|
|**0x80cf002F**|OM_E_CALL_CANCELLED_BY_POLICY|**DisableWindowsUpdateAccess** ポリシーが設定されていたため、操作を完了できませんでした。|
|**0x80cf0030**|OM_E_INVALID_PROXY_SERVER|プロキシ一覧の形式が無効です。|
|**0x80cf0031**|OM_E_INVALID_FILE|ファイルの形式が間違っています。|
|**0x80cf0032**|OM_E_INVALID_CRITERIA|検索条件の文字列が無効です。|
|**0x80cf0034**|OM_E_DOWNLOAD_FAILED|更新プログラムをダウンロードできませんでした。|
|**0x80cf0035**|OM_E_UPDATE_NOT_PROCESSED|更新プログラムが処理されませんでした。|
|**0x80cf0036**|OM_E_INVALID_OPERATION|オブジェクトの現在の状態では操作不可能です。|
|**0x80cf0037**|OM_E_NOT_SUPPORTED|この操作はサポートされていません。|
|**0x80cf0038**|OM_E_WINHTTP_INVALID_FILE|ダウンロードされたファイルに、予期しないコンテンツの種類が含まれています。|
|**0x80cf0039**|OM_E_TOO_MANY_RESYNC|サーバーがエージェントに再同期を要求する回数が多すぎます。|
|**0x80cf0043**|OM_E_NO_UI_SUPPORT|WUA UI はサポートされていません。|
|**0x80cf0044**|OM_E_PER_MACHINE_UPDATE_ACCESS_DENIED|コンピューターごとの更新では、この操作は管理者しか行えません。|
|**0x80cf0045**|OM_E_UNSUPPORTED_SEARCHSCOPE|検索しようとした範囲はサポートされていません。|
|**0x80cf0046**|OM_E_BAD_FILE_URL|URL がファイルを指していません。|
|**0x80cf0047**|OM_E_NOTSUPPORTED|要求された操作はサポートされていません。|
|**0x80cf0049**|OM_E_OUTOFRANGE|データが範囲外です。|
|**0x80cf004A**|OM_E_INVALIDWUAVERSION|データに無効なバージョンが含まれています。|
|**0x80cf004B**|OM_E_SEARCH_COMPLETED_WITH_SOME_FAILURES|検索の呼び出しは完了しましたが、更新プログラムのいくつかを検出できませんでした。|
|**0x80cf004C**|OM_E_DOWNLOAD_COMPLETED_WITH_SOME_FAILURES|ダウンロードの呼び出しは完了しましたが、更新プログラムのいくつかをダウンロードできませんでした。|
|**0x80cf004D**|OM_E_INSTALL_COMPLETED_WITH_SOME_FAILURES|インストールの呼び出しは完了しましたが、更新プログラムのいくつかをインストールできませんでした。|
|**0x80cf004E**|OM_E_WINUPDATE_CACHE_UNINITIALIZED|Windows Update キャッシュが空です。初期化されていません。|
|**0x80cf0436**|OM_E_PT_CATALOG_SYNC_REQUIRED|サーバーが、カテゴリ別の検索をサポートしていません。 代わりに、フル カタログ検索を発行する必要があります。|
|**0x80cf0437**|OM_E_PT_SECURITY_VERIFICATION_FAILURE|サービスの認証で問題が発生しました。|
|**0x80cf0438**|OM_E_PT_ENDPOINT_UNREACHABLE|エンドポイントへの経路が存在しないか、ネットワーク接続されていません。|
|**0x80cf0439**|OM_E_PT_INVALID_FORMAT|受信したデータは、データ コントラクトの条件を満たしていません。|
|**0x80cf043A**|OM_E_PT_INVALID_URL|URL が無効です。|
|**0x80cf043B**|OM_E_PT_NWS_NOT_LOADED|NWS ランタイムを読み込めません。|
|**0x80cf043C**|OM_E_PT_PROXY_AUTH_SCHEME_NOT_SUPPORTED|プロキシ認証スキームがサポートされていません。|
|**0x80cf043D**|OM_E_SERVICEPROP_NOTAVAIL|要求されたサービス プロパティは使用できません。|
|**0x80cf043E**|OM_E_PT_ENDPOINT_REFRESH_REQUIRED|エンドポイント プロバイダー プラグインのオンライン更新が必要です。|
|**0x80cf043F**|OM_E_PT_ENDPOINTURL_NOTAVAIL|要求されたサービス エンドポイントの URL は使用できません。|
|**0x80cf0440**|OM_E_PT_ENDPOINT_DISCONNECTED|サービス エンドポイントとの接続が切断されました。|
|**0x80cf0441**|OM_E_PT_INVALID_OPERATION|この操作は無効です。プロトコル トーカーの状態が適切ではありません。|
|**0x80cf0FFF**|OM_E_UNEXPECTED|操作に失敗しました。このエラーの原因に該当する別のエラー コードはありません。|
|**0x80cf1001**|OM_E_MSI_WRONG_VERSION|Windows インストーラーのバージョンが 3.1 より古いため、一部の更新プログラムを検索できなかった可能性があります。|
|**0x80cf1002**|OM_E_MSI_NOT_CONFIGURED|Windows インストーラーが構成されていないため、一部の更新プログラムを検索できなかった可能性があります。|
|**0x80cf1003**|OM_E_MSP_DISABLED|Windows インストーラーでの修正プログラムの適用がポリシーで無効にされているため、一部の更新プログラムを検索できなかった可能性があります。|
|**0x80cf1004**|OM_E_MSI_WRONG_APP_CONTEXT|このアプリケーションはユーザーごとにインストールされるため、更新プログラムを適用できませんでした。|
|**0x80cf2000**|OM_E_UH_REMOTEUNAVAILABLE|使用可能なリモート プロセスがないため、リモート更新ハンドラーの要求を完了できませんでした。|
|**0x80cf2001**|OM_E_UH_LOCALONLY|ハンドラーはローカル専用のため、リモート更新ハンドラーの要求を完了できませんでした。|
|**0x80cf2003**|OM_E_UH_REMOTEALREADYACTIVE|リモート更新ハンドラーは既に存在するため作成できませんでした。|
|**0x80cf2004**|OM_E_UH_DOESNOTSUPPORTACTION|更新プログラムがインストール (アンインストール) をサポートしていないため、更新ハンドラーへの更新プログラムのインストール (アンインストール) 要求が完了しませんでした。|
|**0x80cf2005**|OM_E_UH_WRONGHANDLER|間違ったハンドラーが指定されたため、操作を完了できませんでした。|
|**0x80cf2006**|OM_E_UH_INVALIDMETADATA|更新プログラムに無効なメタデータが含まれていたため、ハンドラーの操作を完了できませんでした。|
|**0x80cf2007**|OM_E_UH_INSTALLERHUNG|インストーラーの実行時間の制限を超えたため、操作を完了できませんでした。 展開用に承認されている更新プログラムが、ユーザーの介入を必要とするプログラムかどうかを確認してください。 ユーザーの介入が必要な場合は、サイレント インストールできるように、インストール パラメーターを変更してください。|
|**0x80cf2008**|OM_E_UH_OPERATIONCANCELLED|更新ハンドラーによって実行されていた操作が取り消されました。|
|**0x80cf2009**|OM_E_UH_BADHANDLERXML|ハンドラー固有のメタデータが無効なため、操作を完了できませんでした。|
|**0x80cf200B**|OM_E_UH_INSTALLERFAILURE|インストーラーでインストール (アンインストール) できなかった更新プログラムがあります。|
|**0x80cf200D**|OM_E_UH_NEEDANOTHERDOWNLOAD|更新プログラムを再度ダウンロードする必要があるため、更新ハンドラーが更新プログラムをインストールしませんでした。|
|**0x80cf200E**|OM_E_UH_NOTIFYFAILURE|更新ハンドラーが、インストール (アンインストール) 操作のステータスの通知を送信できませんでした。|
|**0x80cf2014**|OM_E_UH_POSTREBOOTSTILLPENDING|更新時の再起動後の操作が進行中です。|
|**0x80cf2015**|OM_E_UH_POSTREBOOTRESULTUNKNOWN|更新時の再起動後の操作結果を判別できませんでした。|
|**0x80cf2016**|OM_E_UH_POSTREBOOTUNEXPECTEDSTATE|更新時の再起動後の操作が完了した後で、予期しない更新状態になりました。|
|**0x80cf2017**|OM_E_UH_NEW_SERVICING_STACK_REQUIRED|この更新プログラムをダウンロードまたはインストールする前に、オペレーティング システムのサービス スタックを更新する必要があります。|
|**0x80cf2018**|OM_E_UH_CALLED_BACK_FAILURE|コールバック インストーラーがコール バックしましたが、エラーが発生しました。|
|**0x80cf2019**|OM_E_UH_CUSTOMINSTALLER_INVALID_SIGNATURE|カスタム インストーラーの署名が、更新プログラムに必要な署名と一致しませんでした。|
|**0x80cf201A**|OM_E_UH_UNSUPPORTED_INSTALLCONTEXT|インストーラーが、インストール構成をサポートしていません。|
|**0x80cf201B**|OM_E_UH_INVALID_TARGETSESSION|インストールの対象セッションが無効です。|
|**0x80cf2FFF**|OM_E_UH_UNEXPECTED|更新ハンドラー エラーが発生しました。このエラーに該当する別の OM_E_UH_&#42; コードはありません。|
|**0x80cf3FFD**|OM_E_NON_UI_MODE|UI モードでないときは、UI を表示できません。 Windows Update クライアントの UI モジュールがインストールされていない可能性があります。|
|**0x80cf3FFE**|OM_E_WUCLTUI_UNSUPPORTED_VERSION|このバージョンの WU クライアント UI からエクスポートされた機能はサポートされていません。|
|**0x80cf3FFF**|OM_E_AUCLIENT_UNEXPECTED|ユーザー インターフェイス エラーが発生しました。このエラーに該当する別の OM_E_AUCLIENT_&#42; エラー コードはありません。|
|**0x80cf4007**|OM_E_PT_SOAPCLIENT_SOAPFAULT|**SOAPCLIENT_SOAPFAULT** と同じです。 **OM_E_PT_SOAP_&#42;** というエラー コードの種類に該当する SOAPの不具合のために、SOAP クライアントで問題が発生しました。|
|**0x80cf4008**|OM_E_PT_SOAPCLIENT_PARSEFAULT|**SOAPCLIENT_PARSEFAULT_ERROR** と同じです。  SOAP クライアントが SOAP のエラーを解析できませんでした。|
|**0x80cf400A**|OM_E_PT_SOAPCLIENT_PARSE|**SOAPCLIENT_PARSE_ERROR** と同じです。  SOAP クライアントがサーバーからの応答を解析できませんでした。|
|**0x80cf400B**|OM_E_PT_SOAP_VERSION|**SOAP_E_VERSION_MISMATCH** と同じです。 SOAP クライアントが、SOAP エンベロープに認識不可能な名前空間を見つけました。|
|**0x80cf400C**|OM_E_PT_SOAP_MUST_UNDERSTAND|**SOAP_E_MUST_UNDERSTAND** と同じです。 SOAP クライアントがヘッダーを解釈できませんでした。|
|**0x80cf400D**|OM_E_PT_SOAP_CLIENT|**SOAP_E_CLIENT** と同じです。 SOAP クライアントが、メッセージの形式が間違っていることを検出しました。 修正してから再送信してください。|
|**0x80cf400E**|OM_E_PT_SOAP_SERVER|**SOAP_E_SERVER** と同じです。 サーバー エラーが原因で、SOAP メッセージを処理できませんでした。 後で再送信してください。|
|**0x80cf4010**|OM_E_PT_EXCEEDED_MAX_SERVER_TRIPS|サーバーへの往復回数が許容最大数を超えました。|
|**0x80cf4012**|OM_E_PT_DOUBLE_INITIALIZATION|オブジェクトが既に初期化されていたため、初期化できませんでした。|
|**0x80cf4013**|OM_E_PT_INVALID_COMPUTER_NAME|コンピューター名を判別できませんでした。|
|**0x80cf4015**|OM_E_PT_REFRESH_CACHE_REQUIRED|サーバーからの応答は、サーバーが変更されたか、クッキーが無効だったことを示しています。 内部キャッシュを更新して、もう一度やり直してください。|
|**0x80cf4016**|OM_E_PT_HTTP_STATUS_BAD_REQUEST|**HTTP 状態 400** と同じです。 構文が無効なため、サーバーが要求を処理できませんでした。|
|**0x80cf4017**|OM_E_PT_HTTP_STATUS_DENIED|**HTTP 状態 401** と同じです。 要求されたリソースには、ユーザー認証が必要です。|
|**0x80cf4018**|OM_E_PT_HTTP_STATUS_FORBIDDEN|**HTTP 状態 403** と同じです。 サーバーは要求を理解しましたが、要求を満たすことを拒否しました。|
|**0x80cf4019**|OM_E_PT_HTTP_STATUS_NOT_FOUND|**HTTP 状態 404** と同じです。 サーバーが要求された URL (Uniform Resource Identifier) を見つけることができません。|
|**0x80cf401A**|OM_E_PT_HTTP_STATUS_BAD_METHOD|**HTTP 状態 405** と同じです。 HTTP メソッドは許可されていません。|
|**0x80cf401B**|OM_E_PT_HTTP_STATUS_PROXY_AUTH_REQ|**HTTP 状態 407** と同じです。 プロキシ認証が必要です。|
|**0x80cf401C**|OM_E_PT_HTTP_STATUS_REQUEST_TIMEOUT|**HTTP 状態 408** と同じです。 要求を待機中にサーバーがタイムアウトしました。|
|**0x80cf401D**|OM_E_PT_HTTP_STATUS_CONFLICT|**HTTP 状態 409** と同じです。 リソースの現在の状態と競合しているため、要求が完了しませんでした。|
|**0x80cf401E**|OM_E_PT_HTTP_STATUS_GONE|**HTTP 状態 410** と同じです。 要求されたリソースはサーバーにありません。|
|**0x80cf401F**|OM_E_PT_HTTP_STATUS_SERVER_ERROR|**HTTP 状態 500** と同じです。 サーバーの内部エラーが原因で、要求を満たすことができませんでした。|
|**0x80cf4020**|OM_E_PT_HTTP_STATUS_NOT_SUPPORTED|**HTTP 状態 500** と同じです。 サーバーは、要求を満たすために必要な機能をサポートしていません。|
|**0x80cf4021**|OM_E_PT_HTTP_STATUS_BAD_GATEWAY|**HTTP 状態 502** と同じです。 サーバーがゲートウェイまたはプロキシとして動作しているときに、要求を満たすためにアクセスした上流のサーバーから無効な応答を受け取りました。|
|**0x80cf4022**|OM_E_PT_HTTP_STATUS_SERVICE_UNAVAIL|**HTTP 状態 503** と同じです。 サービスが一時的に過負荷になっています。|
|**0x80cf4023**|OM_E_PT_HTTP_STATUS_GATEWAY_TIMEOUT|**HTTP 状態 503** と同じです。 ゲートウェイを待機中に要求がタイムアウトしました。|
|**0x80cf4024**|OM_E_PT_HTTP_STATUS_VERSION_NOT_SUP|**HTTP 状態 505** と同じです。 要求で使用されている HTTP のバージョンをサーバーがサポートしていません。|
|**0x80cf4025**|OM_E_PT_FILE_LOCATIONS_CHANGED|ファイルの場所が変更されたため操作に失敗しました。 内部状態を更新して再送信してください。|
|**0x80cf4027**|OM_E_PT_NO_AUTH_PLUGINS_REQUESTED|空の認証情報一覧がサーバーから返されました。|
|**0x80cf4028**|OM_E_PT_NO_AUTH_COOKIES_CREATED|エージェントが、有効な認証クッキーを作成できませんでした。|
|**0x80cf4029**|OM_E_PT_INVALID_CONFIG_PROP|構成のプロパティの値が間違っています。|
|**0x80cf402A**|OM_E_PT_CONFIG_PROP_MISSING|構成のプロパティの値がありません。|
|**0x80cf402B**|OM_E_PT_HTTP_STATUS_NOT_MAPPED|HTTP 要求を完了できませんでした。このエラーの原因に該当する **OM_E_PT_HTTP_&#42;** エラー コードはありません。|
|**0x80cf402C**|OM_E_PT_WINHTTP_NAME_NOT_RESOLVED|**ERROR_WINHTTP_NAME_NOT_RESOLVED** と同じです。 プロキシ サーバー名または接続先サーバー名を解決できません。|
|**0x80cf402F**|OM_E_PT_ECP_SUCCEEDED_WITH_ERRORS|外部 .cab ファイルの処理は完了しましたが、エラーが発生しました。|
|**0x80cf4030**|OM_E_PT_ECP_INIT_FAILED|外部 .cab ファイルのプロセッサの初期化が完了しませんでした。|
|**0x80cf4031**|OM_E_PT_ECP_INVALID_FILE_FORMAT|メタデータ ファイルの形式が無効です。|
|**0x80cf4032**|OM_E_PT_ECP_INVALID_METADATA|外部 .cab ファイルのプロセッサが無効なメタデータを見つけました。|
|**0x80cf4033**|OM_E_PT_ECP_FAILURE_TO_EXTRACT_DIGEST|ファイルのダイジェストを外部 .cab ファイルから抽出できませんでした。|
|**0x80cf4034**|OM_E_PT_ECP_FAILURE_TO_DECOMPRESS_CAB_FILE|外部 .cab ファイルを圧縮解除できませんでした。|
|**0x80cf4035**|OM_E_PT_ECP_FILE_LOCATION_ERROR|外部 .cab ファイルのプロセッサがファイルの場所を取得できませんでした。|
|**0x80cf4FFF**|OM_E_PT_UNEXPECTED|通信エラーが発生しました。このエラーに該当する別の **OM_E_PT_&#42;** エラー コードはありません。|
|**0x80cf6001**|OM_E_DM_URLNOTAVAILABLE|要求されたファイルに URL がないため、ダウンロード マネージャーの操作を完了できませんでした。|
|**0x80cf6002**|OM_E_DM_INCORRECTFILEHASH|ファイルのダイジェストを認識できなかったため、ダウンロード マネージャーの操作を完了できませんでした。|
|**0x80cf6003**|OM_E_DM_UNKNOWNALGORITHM|ファイルのメタデータに、認識不可能なハッシュ アルゴリズムが指定されていたため、ダウンロード マネージャーの操作を完了できませんでした。|
|**0x80cf6005**|OM_E_DM_NONETWORK|ネットワーク接続できなかったため、ダウンロード マネージャーの操作を完了できませんでした。|
|**0x80cf6007**|OM_E_DM_NOTDOWNLOADED|更新プログラムはダウンロードされていません。|
|**0x80cf6008**|OM_E_DM_FAILTOCONNECTTOBITS|ダウンロード マネージャーがバックグラウンド インテリジェント転送サービス (BITS) に接続できなかったため、操作に失敗しました。|
|**0x80cf6009**|OM_E_DM_BITSTRANSFERERROR|バックグラウンド インテリジェント転送サービス (BITS) で不特定の転送エラーが発生したため、ダウンロード マネージャーの操作に失敗しました。|
|**0x80cf600a**|OM_E_DM_DOWNLOADLOCATIONCHANGED|ダウンロードするソースの場所が変更されているため、ダウンロードし直す必要があります。|
|**0x80cf600B**|OM_E_DM_CONTENTCHANGED|更新プログラムの新しいリビジョンでコンテンツが変更されているため、ダウンロードし直す必要があります。|
|**0x80cf6FFF**|OM_E_DM_UNEXPECTED|ダウンロード マネージャー エラーが発生しました。このエラーに該当する別の **OM_E_DM_&#42;** エラー コードはありません。|
|**0x80cf7003**|OM_E_INVALID_EVENT_PAYLOAD|指定されたイベント ペイロードが無効です。|
|**0x80cf7004**|OM_E_INVALID_EVENT_PAYLOADSIZE|送信されたイベント ペイロードのサイズが無効です。|
|**0x80cf7005**|OM_E_SERVICE_NOT_REGISTERED|サービスが登録されていません。|
|**0x80cf8000**|OM_E_DS_SHUTDOWN|エージェントがシャットダウンしているため、操作に失敗しました。|
|**0x80cf8001**|OM_E_DS_INUSE|データ ストアが使用中のため、操作に失敗しました。|
|**0x80cf8002**|OM_E_DS_INVALID|データ ストアの現在の状態と、予期された状態が一致しません。|
|**0x80cf8003**|OM_E_DS_TABLEMISSING|データ ストアにテーブルがありません。|
|**0x80cf8004**|OM_E_DS_TABLEINCORRECT|データ ストアに、予期しない列のあるテーブルが含まれています。|
|**0x80cf8005**|OM_E_DS_INVALIDTABLENAME|テーブルを開けませんでした。このテーブルはデータ ストアにありません。|
|**0x80cf8006**|OM_E_DS_BADVERSION|データ ストアの現在のバージョンと、予期されたバージョンが一致しません。|
|**0x80cf8007**|OM_E_DS_NODATA|要求された情報は、データ ストアにありません。|
|**0x80cf8008**|OM_E_DS_MISSINGDATA|データ ストアに必要な情報がないか、Null 以外の値を必要とするテーブルの列に Null 値があります。|
|**0x80cf8009**|OM_E_DS_MISSINGREF|データ ストアに必要な情報がないか、存在しないライセンス情報かファイルの参照、ローカライズされたプロパティ、またはリンクされた行が含まれています。|
|**0x80cf800A**|OM_E_DS_UNKNOWNHANDLER|更新ハンドラーを認識できなかったため、更新プログラムが処理されませんでした。|
|**0x80cf800B**|OM_E_DS_CANTDELETE|更新プログラムが 1 つまたは複数のサービスで参照されているため、削除されませんでした。|
|**0x80cf800C**|OM_E_DS_LOCKTIMEOUTEXPIRED|データ ストアのセクションを許容時間内にロックできませんでした。|
|**0x80cf800E**|OM_E_DS_ROWEXISTS|行が追加されませんでした。同じプライマリ キーの行が既に存在します。|
|**0x80cf800F**|OM_E_DS_STOREFILELOCKED|データ ストアが別のプロセスでロックされていたため、初期化できませんでした。|
|**0x80cf8010**|OM_E_DS_CANNOTREGISTER|現在のプロセスでは、データ ストアを COM に登録することはできません。|
|**0x80cf8011**|OM_E_DS_UNABLETOSTART|データ ストア オブジェクトを別のプロセスで作成できませんでした。|
|**0x80cf8013**|OM_E_DS_DUPLICATEUPDATEID|サーバーが、同じ更新プログラムに異なる 2 つのリビジョン ID を付けてクライアントに送信しました。|
|**0x80cf8014**|OM_E_DS_UNKNOWNSERVICE|サービスがデータ ストアにないため、操作を完了できませんでした。|
|**0x80cf8015**|OM_E_DS_SERVICEEXPIRED|サービスの登録の有効期限が切れたため、操作を完了できませんでした。|
|**0x80cf8016**|OM_E_DS_DECLINENOTALLOWED|更新プログラムを非表示にする要求が拒否されました。この更新プログラムは、必須更新プログラムか、期限付きで展開されています。|
|**0x80cf8017**|OM_E_DS_TABLESESSIONMISMATCH|テーブルがセッションと関連付けられていないため、閉じられませんでした。|
|**0x80cf8018**|OM_E_DS_SESSIONLOCKMISMATCH|テーブルがセッションと関連付けられていないため、閉じられませんでした。|
|**0x80cf8019**|OM_E_DS_NEEDWINDOWSSERVICE|サービスを削除、または自動更新との登録を解除する要求が拒否されました。これは、このサービスが組み込みサービスであるか、自動更新サービスを別のサービスに切り替えられないためです。|
|**0x80cf801A**|OM_E_DS_INVALIDOPERATION|要求が拒否されました。この操作は許可されていません。|
|**0x80cf801B**|OM_E_DS_SCHEMAMISMATCH|現在のデータ ストアのスキーマと、バックアップの XML ドキュメントにあるテーブルのスキーマが一致しません。|
|**0x80cf801C**|OM_E_DS_RESETREQUIRED|データ ストアで、セッションのリセットを必要としています。 このセッションを解放してから、新しいセッションでもう一度やり直してください。|
|**0x80cf801D**|OM_E_DS_IMPERSONATED|データ ストアの操作を完了できませんでした。この操作は、借用した ID で要求されています。|
|**0x80cf8FFF**|OM_E_DS_UNEXPECTED|データ ストア エラーが発生しました。このエラーに該当する別の **OM_E_DS_&#42;** コードはありません。|
|**0x80cfA000**|OM_E_AU_NOSERVICE|自動更新サービスで、着信要求を処理できませんでした。|
|**0x80cfA004**|OM_E_AU_PAUSED|自動更新が一時停止されていたため、着信した要求を処理できませんでした。|
|**0x80cfA005**|OM_E_AU_NO_REGISTERED_SERVICE|管理されていないサービスは、自動更新に登録されていません。|
|**0x80cfA006**|OM_E_AU_DETECT_SVCID_MISMATCH|自動更新に登録されている既定のサービスが、検索中に変更されました。|
|**0x80cfA007**|OM_E_AU_ALREADY_PROMPTING_FOR_REBOOT|自動更新サービスは、ユーザーに再起動のメッセージを既に表示しています。|
|**0x80cfAFFF**|OM_E_AU_UNEXPECTED|自動更新エラーが発生しました。このエラーに該当する別の **OM_E_AU &#42;** コードはありません。|
|**0x80cfE001**|OM_E_EE_UNKNOWN_EXPRESSION|式を認識できなかったため、式の評価を完了できませんでした。|
|**0x80cfE002**|OM_E_EE_INVALID_EXPRESSION|式が無効なため、式の評価を完了できませんでした。|
|**0x80cfE003**|OM_E_EE_MISSING_METADATA|式に含まれているメタデータのノードの数が正しくないため、式の評価を完了できませんでした。|
|**0x80cfE004**|OM_E_EE_INVALID_VERSION|シリアル化された式のデータのバージョンが無効なため、式の評価を完了できませんでした。|
|**0x80cfE005**|OM_E_EE_NOT_INITIALIZED|式エバリュエーターを初期化できませんでした。|
|**0x80cfE006**|OM_E_EE_INVALID_ATTRIBUTEDATA|属性が無効なため、式の評価を完了できませんでした。|
|**0x80cfE007**|OM_E_EE_CLUSTER_ERROR|コンピューターのクラスターの状態を判別できなかったため、式の評価を完了できませんでした。|
|**0x80cfEFFF**|OM_E_EE_UNEXPECTED|式の評価エラーが発生しました。このエラーに該当する別の **OM_E_EE_&#42;** エラー コードはありません。|
|**0x80cfF001**|OM_E_REPORTER_EVENTCACHECORRUPT|イベントのキャッシュ ファイルに問題があります。|
|**0x80cfF002**|OM_E_REPORTER_EVENTNAMESPACEPARSEFAILED|イベントの名前空間記述子の XML を解析できませんでした。|
|**0x80cfF003**|OM_E_INVALID_EVENT|イベントの名前空間記述子の XML が無効です。|
|**0x80cfF004**|OM_E_SERVER_BUSY|サーバーがビジー状態だったため、イベントを拒否しました。|
|**0x80cfFFFF**|OM_E_REPORTER_UNEXPECTED|レポーター エラーが発生しました。このエラーに該当する別のエラー コードはありません。|
|**0x80af0005**|OMC_E_INSTALL_NOT_ALLOWED_REBOOT_REQUIRED|必要な再起動が保留中になっているため、インストールできませんでした。|
|**0x80af0006**|OMC_E_DOWNLOAD_CANCELLED|ダウンロードが取り消されました。|

## 置き換えられた更新プログラムが大量にある Windows 7 ベース コンピューターで Microsoft Intune コンソールへの報告が停止する
**問題**: Microsoft Intune クライアントで次の症状が 1 つ以上発生する場合があります。
- 突然、Microsoft 管理コンソールに報告しなくなる。  
- CPU 使用率が高くなる。
- Intune ポータルからアプリケーションをインストールするときに、インストールの処理速度が遅くなる。 
- Microsoft Intune Center で次のエラーが発生する。*"このコンピューターを更新中にエラーが発生しました。エラーが見つかりました: コード 0x800705b4*。
- Intune 管理コンソールの [グループ] の [すべてのデバイス] の下にあるステータス フィールドに、次のメッセージが表示される。*"このコンピューターにインストールされているエージェントでエラーが発生しました。このコンピューターの情報は、正確でないか最新のものでない可能性があります*。

この問題は、別の更新によって置き換えられた更新プログラムが長期間拒否されていない場合に発生することがあります。 Windows がアプリケーションのインストールなどの特定の処理を行う際、置き換えられた更新プログラムと置き換え後の更新プログラムを正しく関連付けるために、置き換えられた更新プログラムを順番にすべてチェックします。 置き換えられた更新プログラムが多くなりすぎると、このチェック処理に負荷と時間がかかるため、CPU 使用率が高くなる場合があります。 Windows 7 では置き換えられた更新プログラムが大量に提供されているため、この問題は主に Windows 7 を実行しているクライアントに影響します。 Windows 8 以降のオペレーティング システムでは置き換えられた更新プログラムがそれほど多く提供されていないため、この問題の影響はあまりありません。

**解決方法**: この問題を解決するには、次の手順に従います。
1. [Intune 管理コンソール](https://manage.microsoft.com)にログオンします。
2. **[更新プログラム]** > **[All Updates]** (すべての更新プログラム) の順に選択します。
3. 上部のツールバーのフィルター機能を使用して、置き換えられた更新プログラムのみを表示します。
4. 影響を受けているクライアントにインストールされている Windows 7 またはアプリケーション (Microsoft Office など) に適用される置き換えられた更新プログラムをすべて拒否します。 
5. 影響を受けているクライアントを再起動します。

さらに、Windows 7 を実行している場合は、次の更新プログラムがインストールされていることを確認します。[3050265 Windows Update Client for Windows 7: June 2015](https://support.microsoft.com/kb/3050265)

### 次のステップ
このトラブルシューティング情報を使っても問題が解決しない場合は、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」の説明に従って Microsoft サポートにお問い合わせください。




<!--HONumber=Jun16_HO5-->


