---
title: サード パーティの証明機関をオンボードするための API
titlesuffix: Microsoft Intune
description: Microsoft Intune のデバイスに SCEP 証明書を発行するには、サード パーティの証明機関 (CA) に SCEP GitHub ソリューションを追加または統合します。 このソリューションには、Intune に成功および失敗の通知を検証、送信する、Intune との通信時に SSL ソケット ファクトリを使用する Java および C# の API が含まれています。 SCEP の CA 構成をテストする手順の概要も参照してください。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c7178ae7231586e781766adb1fea45b375a76920
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842050"
---
# <a name="use-apis-to-add-third-party-cas-for-scep-to-intune"></a>SCEP 用のサード パーティ CA を Intune に追加するための API の使用

Microsoft Intune では、サード パーティの証明機関 (CA) を追加し、これらの CA に Simple Certificate Enrollment Protocol (SCEP) を使用して証明書を発行および検証させることができます。 「[Add third-party certification authority](certificate-authority-add-scep-overview.md)」 (サード パーティ証明機関の追加) では、この機能の概要と Intune での管理者のタスクについて説明しています。

Microsoft が GitHub.com に公開しているオープンソース ライブラリを使用する管理者向けのタスクもいくつかあります。 このライブラリには、以下を行う API が含まれています。

- Intune が動的に生成した SCEP パスワードの検証
- SCEP 要求を送信するデバイスで作成された証明書の Intune への通知

この API を使用すると、サードパーティ SCEP サーバーが MDM デバイス用の Intune SCEP 管理ソリューションと統合されます。 ライブラリが、認証、サービスの場所および ODATA Intune Service API などをそのユーザーから抽象化します。

## <a name="scep-management-solution"></a>SCEP 管理ソリューション

![サード パーティの SCEP 証明機関を Microsoft Intune に統合する方法](./media/scep-certificate-vendor-integration.png)

管理者は、Intune を使用して、SCEP プロファイルを作成し、これらのプロファイルを MDM デバイスに割り当てます。 SCEP プロファイルには、以下などのパラメーターが含まれます。

- SCEP サーバーの URL
- 証明機関の信頼されたルート証明書
- 証明書の属性など

Intune を使用してチェックインするデバイスには、SCEP プロファイルが割り当てられ、これらのパラメーターで構成されます。 動的生成の SCEP チャレンジ パスワードが Intune によって作成され、デバイスに割り当てられます。

このチャレンジの内容:

- 動的に生成されたチャレンジ パスワード
- デバイスによって SCEP サーバーに発行される証明書署名要求 (CSR) に求められるパラメーターの詳細
- チャレンジの有効期限

Intune によってこの情報が暗号化され、暗号化された blob に署名が与えられ、これらの詳細が SCEP パスワードにパッケージ化されます。

証明書を要求する目的でデバイスから SCEP サーバーにコンタクトが取られ、この SCEP チャレンジ パスワードが与えられます。 SCEP サーバーから Intune に検証目的で CSR と暗号化された SCEP チャレンジ パスワードが送信されます。  このチャレンジ パスワードと CSR は、デバイスに証明書を発行するために、SCEP サーバーの検証に合格する必要があります。 SCEP チャレンジが検証されるとき、以下のチェックが実行されます。


- 暗号化された blob の署名の検証
- チャレンジの有効期限が切れていないことの検証
- プロファイルのターゲットがまだデバイスであることの検証
- CSR 内のデバイスによって要求されている証明書プロパティが期待値と一致することの検証

SCEP 管理ソリューションには、レポート機能も含まれます。 管理者は SCEP プロファイルの展開のステータスの情報や、デバイスに発行された証明書の情報を得ることができます。

## <a name="integrate-with-intune"></a>Intune との統合

Intune SCEP と統合するためのライブラリのコードは、「[Microsoft/Intune-Resource-Access GitHub リポジトリ](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)」からダウンロードできます。

製品にライブラリを統合する場合、次の手順を踏む必要があります。 これらの手順は、GitHub リポジトリの使用と、Visual Studio でのソリューションおよびプロジェクトの作成に関する知識が必要です。

1. リポジトリから通知を受け取るための登録
2. リポジトリの複製またはダウンロード
3. `\src\CsrValidation` フォルダー (https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) 下のライブラリ実装に進みます。
4. README ファイルの手順に従ってライブラリをビルドします
5. SCEP サーバーをビルドするためのライブラリをプロジェクトに含めます
6. SCEP サーバーで次のタスクを完了します。

    - ライブラリが認証に使用する (この記事の) [Azure アプリケーション ID、Azure アプリケーション キー、テナント ID](#onboard-scep-server-in-azure) の構成を管理者に許可します。 管理者には、Azure アプリケーション キーを更新する権限が必要です。
    - Intune によって生成された SCEP パスワードを含む SCEP 要求を識別します
    - **検証要求 API** ライブラリを使用し、Intune によって生成された SCEP パスワードを検証します
    - ライブラリ通知 API を使用し、Intune によって生成された SCEP パスワードを持つ SCEP 要求用に発行された証明書を Intune に通知します。 また、これらの SCEP 要求の処理時に発生する可能性があるエラーを Intune に通知します。
    - 管理者が問題をトラブルシューティングできる十分な情報をサーバーが記録していることを確認します。

7. (この記事の) [統合テスト](#integration-testing)を完了し、問題を解決します
8. 以下を説明する指導書をお客様に提供します。

    - SCEP サーバーを Azure Portal にオンボードする方法
    - ライブラリの構成に必要な Azure アプリケーション ID と Azure アプリケーション キーの取得方法

### <a name="onboard-scep-server-in-azure"></a>Azure への SCEP サーバーのオンボード

Intune に対して認証するには、SCEP サーバーには Azure アプリケーション ID と Azure アプリケーション キーとテナント ID が必要です。 また、SCEP サーバーには Intune API への認証されたアクセスが必要です。

SCEP サーバーの管理者がこのデータを取得するには、Azure Portal にサインインし、アプリケーションを登録し、アプリケーションに **Microsoft Intune API\SCEP チャレンジ検証**権限を付与し、アプリケーションのキーを作成し、アプリケーション ID、そのキー、テナント ID をダウンロードする必要があります。

アプリケーションの登録手順および ID とキーの取得方法については、「[リソースにアクセスできる Azure Active Directory アプリケーションとサービス プリンシパルをポータルで作成する](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)」を参照してください。

### <a name="java-library-api"></a>Java ライブラリ API

Java ライブラリは、ビルド時にその依存関係のプルする Maven プロジェクトとして実装されます。 この API は、`IntuneScepServiceClient` クラスにより、`com.microsoft.intune.scepvalidation` 名前空間下で実装されます。

#### <a name="intunescepserviceclient-class"></a>IntuneScepServiceClient クラス

`IntuneScepServiceClient` クラスには、SCEP パスワードを検証したり、作成された証明書を Intune に通知したり、すべてのエラーを列挙する SCEP サービスによって使用されるメソッドが含まれています。

##### <a name="intunescepserviceclient-constructor"></a>IntuneScepServiceClient コンストラクター

署名:

```java
IntuneScepServiceClient(
    Properties configProperties)
```

説明:

`IntuneScepServiceClient` オブジェクトをインスタンス化し構成します。

パラメーター:

    - configProperties    クライアント構成情報を含むプロパティ オブジェクト

構成には、次のプロパティが必要です。

    - AAD_APP_ID="オンボード処理時に取得した Azure アプリケーション ID"
    - AAD_APP_KEY="オンボード処理時に取得した Azure アプリケーション キー"
    - TENANT="オンボード処理時に取得したテナント ID"
    - PROVIDER_NAME_AND_VERSION="製品とそのバージョンを識別するために使用する情報"
    
ソリューションで認証を使用するかまたは使用しないプロキシが必要な場合は、次のプロパティを追加できます。

    - PROXY_HOST="プロキシがホストされているホスト。"
    - PROXY_PORT="プロキシがリッスンしているポート。"
    - PROXY_USER ="プロキシで基本認証が使用されている場合に使用するユーザー名。"
    - PROXY_PASS ="プロキシで基本認証が使用されている場合に使用するパスワード。"

スロー:

    - IllegalArgumentException    適切なプロパティ オブジェクトなしにコンストラクターが実行された場合にスローされます。

> [!IMPORTANT]
> このクラスのインスタンスはインスタンス化し、複数の SCEP 要求の処理に使用するのが最良です。 これを行うと、これが認証トークンとサービスの場所の情報をキャッシュするので、オーバーヘッドが減少します。

**セキュリティのメモ**  
SCEP サーバーの導入者は、記憶域に永続化された構成プロパティに入力されたデータを、改ざんや漏洩から保護する必要があります。 情報をセキュリティで保護するには、適切な ACL と暗号化を使用することをお勧めします。

##### <a name="validaterequest-method"></a>ValidateRequest メソッド

署名:

```java
void ValidateRequest(
    String transactionId,
    String certificateRequest)
```

説明:

SCEP 証明書要求を検証します。

パラメーター:

    - transactionId         SCEP トランザクション ID
    - certificateRequest    文字列としてエンコードされた DER によってエンコードされた PKCS #10 証明書要求 Base64

スロー:

    - IllegalArgumentException      無効なパラメーターで呼び出された場合にスローされます
    - IntuneScepServiceException    証明書が無効であることがわかるとスローされます
    - Exception                     予期せぬエラーが発生した場合にスローされます

> [!IMPORTANT]
> このメソッドによってスローされる例外は、サーバーで記録される必要があります。 なお、`IntuneScepServiceException` プロパティには、証明書要求の検証が失敗した理由の詳細な情報があります。

**セキュリティのメモ**  

  - このメソッドで例外がスローされる場合、SCEP サーバーはクライアントに証明書を発行**しないようにする**必要があります。
  - SCEP 証明書要求の検証が失敗するということは、Intune のインフラストラクチャに問題があることが示唆されます。 または、証明書を取得しようとしている攻撃者がいることが示唆されます。

##### <a name="sendsuccessnotification-method"></a>SendSuccessNotification メソッド

署名:

```java
void SendSuccessNotification(
    String transactionId,
    String certificateRequest,
    String certThumbprint,
    String certSerialNumber,
    String certExpirationDate,
    String certIssuingAuthority)
```

説明:

証明書が SCEP 要求の処理の一環として作成されたことを Intune に通知します。

パラメーター:

    - transactionId           SCEP のトランザクション ID
    - certificateRequest    文字列としてエンコードされた DER によってエンコードされた PKCS #10 証明書要求 Base64
    - certThumprint           プロビジョニングされた証明書のサムプリント
    - certSerialNumber        プロビジョニングされた証明書のシリアル番号
    - certExpirationDate      プロビジョニングされた証明書の有効期限 日付の文字列は、Web UTC 時間 (YYYY-MM-DDThh:mm:ss.sssTZD) ISO 8601 を使用してフォーマットされる必要があります。
    - certIssuingAuthority    証明書を発行した機関の名前

スロー:

    - IllegalArgumentException      無効なパラメーターで呼び出された場合にスローされます
    - IntuneScepServiceException    証明書が無効であることがわかるとスローされます
    - Exception                     予期せぬエラーが発生した場合にスローされます

> [!IMPORTANT]
> このメソッドによってスローされる例外は、サーバーで記録される必要があります。 なお、`IntuneScepServiceException` プロパティには、証明書要求の検証が失敗した理由の詳細な情報があります。

**セキュリティのメモ**

  - このメソッドで例外がスローされる場合、SCEP サーバーはクライアントに証明書を発行**しないようにする**必要があります。
  - SCEP 証明書要求の検証が失敗するということは、Intune のインフラストラクチャに問題があることが示唆されます。 または、証明書を取得しようとしている攻撃者がいることが示唆されます。

##### <a name="sendfailurenotification-method"></a>SendFailureNotification メソッド

署名:

```java
void SendFailureNotification(
    String transactionId,
    String certificateRequest,
    long  hResult,
    String errorDescription)
```

説明:

SCEP 要求の処理中にエラーが発生したことを Intune に通知します。 このメソッドは、このクラスのメソッドによってスローされる例外に対して呼び出すことはできません。

パラメーター:

    - transactionId         SCEP トランザクション ID
    - certificateRequest    文字列としてエンコードされた DER によってエンコードされた PKCS #10 証明書要求 Base64
    - hResult               発生したエラーを最も正しく説明する Win32 エラー コード。 「[Win32 エラー コード](https://msdn.microsoft.com/library/cc231199.aspx)」を参照してください。
    - errorDescription      発生したエラーの説明

スロー:

    - IllegalArgumentException      無効なパラメーターで呼び出された場合にスローされます
    - IntuneScepServiceException    証明書が無効であることがわかるとスローされます
    - Exception                     予期せぬエラーが発生した場合にスローされます

> [!IMPORTANT]
> このメソッドによってスローされる例外は、サーバーで記録される必要があります。 なお、`IntuneScepServiceException` プロパティには、証明書要求の検証が失敗した理由の詳細な情報があります。

**セキュリティのメモ**

  - このメソッドで例外がスローされる場合、SCEP サーバーはクライアントに証明書を発行**しないようにする**必要があります。
  - SCEP 証明書要求の検証が失敗するということは、Intune のインフラストラクチャに問題があることが示唆されます。 または、証明書を取得しようとしている攻撃者がいることが示唆されます。

##### <a name="setsslsocketfactory-method"></a>SetSslSocketFactory メソッド

署名:

```java
void SetSslSocketFactory(
    SSLSocketFactory factory)
```

説明:

このメソッドは、Intune との通信時、(既定ではなく) 指定された SSL ソケット ファクトリを使用する必要があることをクライアントに通知するために使用します。

パラメーター:

    - factory    クライアントが HTTPS 要求に使用する SSL ソケット ファクトリ

スロー:

    - IllegalArgumentException    無効なパラメーターで呼び出された場合にスローされます

> [!NOTE]
> このクラスの他のメソッドを実行する前に必要である場合、SSL ソケット ファクトリを設定する必要があります。

## <a name="integration-testing"></a>統合テスト

ソリューションが Intune に正しく統合されているかの検証およびテストは必須です。 手順の概要を次に列挙します。

1. [Intune 試用版アカウント](account-sign-up.md)を設定します。
2. [Azure Portal に SCEP サーバーを](#onboard-scep-server-in-azure) (この記事) オンボードします。
3. SCEP サーバーのオンボード時に作成した ID とキーを使用して [SCEP サーバーを構成](certificates-scep-configure.md)します。
4. 「[scenario testing matrix](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv)」 (シナリオのテスト マトリックス) のシナリオをテストするために[デバイスを登録](device-enrollment.md)します。
5. 証明機関をテストするために、[信頼されたルート証明書プロファイルを作成](certificates-scep-configure.md)します。
6. 「[scenario testing matrix](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv)」 (シナリオのテスト マトリックス) で列挙されたシナリオをテストするための SCEP プロファイルを作成します。
7. デバイスを登録したユーザーに[プロファイルを割り当て](device-profile-assign.md)ます。
8. デバイスが Intune と同期されるまで待機します。 または、[デバイスを手動で同期](device-sync.md)します。
9. 信頼されたルート証明書と SCEP [プロファイルがデバイスに展開されたことを](device-profile-monitor.md)確認します。
10. 信頼されたルート証明書がすべてのデバイスにインストールされたことを確認します。
11. 割り当てられたプロファイルの SCEP 証明書がすべてのデバイスにインストールされたことを確認します。
12. インストールされた証明書のプロパティが SCEP プロファイルのプロパティ セットと一致することを確認します。
13. 発行された証明書が Intune のコンソールに正しく列挙されていることを確認します。

## <a name="see-also"></a>関連項目

- [サード パーティ CA の追加の概要](certificate-authority-add-scep-overview.md)
- [Intune をセットアップする](setup-steps.md)
- [デバイスの登録](device-enrollment.md)
- [SCEP 証明書プロファイルの構成](certificates-scep-configure.md#create-a-scep-certificate-profile) (このシナリオでは、Microsoft NDES サーバー\Connector 設定は使用されません)
