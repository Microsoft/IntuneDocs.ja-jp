---
title: "Intune の用語集"
titleSuffix: Azure portal
description: "Microsoft Intune で使用される用語について説明します"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 07/28/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd7b5613-ee9f-4dc3-990c-ab4c1d40720d
ms.custom: intune-azure
ms.openlocfilehash: 5d094e59b374ca306482cd1cb87f8a950df7fe14
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2017
---
# <a name="microsoft-intune-glossary"></a>Microsoft Intune の用語集

## <a name="a"></a>A

|||
|-|-|
|アプリ割り当て|ユーザーが必要なアプリを[検索、ダウンロード、およびインストール](/intune/app-management)できるようにします。 以前は*アプリの展開*と呼ばれていました。|
|アプリ構成プロファイル <br/><br/>アプリ構成ポリシー|ベンダー固有の構成でモバイル アプリを利用できます。 [iOS](/intune/app-configuration-policies-use-ios) または [Android](/intune/app-configuration-policies-use-android) アプリを、実行前に固有の設定で構成します。|
|アプリの監視|アプリ割り当てに関連する[最新の状態やアクティビティを確認](/intune/apps-monitor)できます。|
|アプリ保護データ削除タスク|ユーザーのデバイスから[アプリ データを削除](/intune/app-protection-policies)します。|
|アプリ保護ポリシー|Enterprise Mobility + Security (EMS) テクノロジと統合されたモバイル アプリを利用できます。 ユーザーのアプリを[会社のデータ保護ポリシー](/intune/app-protection-policies)に準拠させます。|
|アプリ SDK|[Microsoft Intune App SDK](/intune/app-sdk) を使用すると、社内で作成したアプリに、Intune アプリ保護ポリシーで管理できる機能を追加できます。|
|アプリのアンインストール アクション|ユーザーのデバイスから[アプリをアンインストール](/intune/apps-deploy)できます。|
|アプリ ラッピング ツール|基幹業務アプリのラッパーを作成する[コマンド ライン アプリケーション](/intune/apps-prepare-mobile-application-management)です。このラッパーにより、アプリを Intune アプリ保護ポリシーで管理できるようになります。|
|割り当てアクション|[アプリを割り当てる](/intune/apps-deploy)ときに選択するものです。 アプリのインストールを必須 (必要) または任意 (使用可能) にしたり、アプリをアンインストールしたりできます。|
|利用可能なインストール|この操作でアプリを割り当てると、アプリがポータル サイトに表示され、ユーザーは[オンデマンドでこれをインストール](/intune/apps-deploy)できます。|
|Azure Portal|Intune の新しいコンソールです。詳しくは[こちら](/intune/what-is-intune)をご覧ください。|

## <a name="b"></a>B
|||
|-|-|
|BYOD|[Bring Your Own Device](/intune/device-enrollment)。 ユーザーは自分のデバイスに Intune ポータル サイト アプリをインストールし、登録できます。電子メール、会社のアプリ、会社のデータ、サポートなど、会社のリソースにアクセスできます。|

## <a name="c"></a>C
|||
|-|-|
|証明書プロファイル|Wi-Fi、電子メール、または VPN プロファイルを使用するときに証明書で[企業リソースへのアクセスを保護する](/intune/certificates-configure)ためのポリシーの種類です。|
|代金引換払い|[会社所有のデバイス](/intune/device-enrollment)を、会社のニーズや管理されたデバイスの種類に合わせ、さまざまな方法で登録できます。|
|[ポータル サイト]|[会社のデータとアプリに対するアクセス権](/intune/company-portal-customize)をユーザーに付与するアプリまたは Web サイトです。|
|コンプライアンス ポリシー|デバイスが、デバイスにアクセスする場合の PIN の使用や、デバイスに格納されるデータの暗号化など、[特定のルールに準拠している](/intune/device-compliance)ことを確認します。|
|準拠アプリと非準拠アプリ|[デバイスの制限プロファイル](/intune/device-restrictions-configure)の一部であり、ユーザーが実行できるアプリと実行できないアプリの一覧を定義できます。 Intune は、 非準拠アプリがインストールまたは実行されたことをレポートで管理者に通知します。 プラットフォームによっては、Intune は非準拠アプリのインストールをブロックすることもできます。|
|条件付きアクセス|設定したルールに準拠しているデバイスからのみ、[会社の電子メール、Office 365、その他のサービスにアクセスできる](/intune/conditional-access)ようにします。|
|カスタム ポリシー|全般構成ポリシーに含まれる組み込み設定ではニーズを満たすことができない場合は、[カスタム ポリシーを使用](/intune/custom-settings-configure)します。 カスタム ポリシーを使用すると、Apple Configurator や OMA-URI などの他の方法で設定を作成できる場合があります。|

## <a name="d"></a>D
|||
|-|-|
|展開|管理対象のデバイスまたはユーザーにアプリまたはポリシーを送信することです。 このアクションは、*割り当て*と呼ばれるようになりました。|
|デバイス登録マネージャー|組織は Intune を使用して、単一のユーザー アカウントで多数のモバイル デバイスを管理することができます。 [デバイス登録マネージャー (DEM) アカウント](/intune/device-enrollment-program-enroll-ios)は、最大で 1,000 台のデバイスを登録できる特別な Intune アカウントです。|
|デバイス プロファイル|[これらのプロファイル](/intune/device-profile-create)では、管理するデバイスのセキュリティ、機能、アクセス設定を幅広く構成できます。|

## <a name="e"></a>E
|||
|-|-|
|電子メールのプロファイル|このポリシーを使用すると、モバイル デバイス上の[電子メール アクセス設定](/intune/email-settings-configure)をセットアップし、エンド ユーザーが行う必要のある設定の量を最小限に抑えることができます。|
|EMS|Microsoft Enterprise Mobility + Security (旧称 Enterprise Mobility Suite) は、会社のデータを保護しながら、ユーザーには[必要なアプリとコンテンツにアクセスできる](https://www.microsoft.com/cloud-platform/enterprise-mobility)ようにします。|
|エンド ユーザー|Intune を使用して管理される[スマートフォンや PC などのデバイスのユーザー](/intune/end-user-educate)です。|
|登録|Microsoft Intune は、[登録](/intune/device-enrollment)を使用して、デバイスを管理対象にし、リソースへのアクセスを許可します。|

## <a name="f"></a>F
|||
|-|-|
|FastTrack|対象となるプランで 150 のライセンスを持つ Intune ユーザー向けの [Microsoft サービス](https://technet.microsoft.com/library/mt228265.aspx)です。 このサービスを利用すると、Microsoft スペシャリストが Intune の使用開始をお手伝いします。|

## <a name="g"></a>G
|||
|-|-|
|[グループ]|グループを使用すると、[ユーザーまたはデバイスを論理的にまとめる](/intune/groups-get-started)ことができます。 たとえば、すべての Windows PC のグループを作成できます。 その後、これらのグループにアプリとプロファイルを割り当てることができます。|

## <a name="h"></a>H
|||
|-|-|
|ハイブリッド|System Center Configuration Manager コンソールから Intune に登録されたデバイスを管理できる構成です。|

## <a name="i"></a>I
|||
|-|-|
|Azure ポータル|ほとんどの Intune 管理操作に使用できる Azure Portal です。|
|Intune ソフトウェア クライアント|[一部の Windows PC を管理](/intune-classic/get-started/choose-how-to-manage-devices) する代替手段です。使用する方法を決定する場合に役に立ちます。|
|Intune ソフトウェア パブリッシャー|[展開するアプリを定義してクラウドの記憶域スペースにアップロードする](/intune-classic/deploy-use/add-apps)ために使用するツールです。|
|インベントリ|管理対象デバイスの[ハードウェアとインストールされているソフトウェア](/intune/device-inventory)を表示するために使用します。|

## <a name="k"></a>K
|||
|-|-|
|キオスク モード|[デバイスの制限プロファイル](/intune/device-restrictions-configure)の一部として構成されます。このモードを使用すると、デバイスをロック ダウンできます。 たとえば、一部のアプリだけを実行できるようにリテール デバイスを構成できます。|

## <a name="m"></a>M
|||
|-|-|
|Managed Browser|[Web を参照するためのアプリケーション](/intune/app-configuration-managed-browser)です。Intune を使用して組織内で割り当てることができます。 Managed Browser ポリシーは、Managed Browser のユーザーがアクセスできる Web サイトを制限する許可リストまたはブロック リストを構成するものです。|
|MDM 機関|[MDM 機関](/intune/mdm-authority-set)では、一連のデバイスを管理するためのアクセス許可を持つ管理サービスを定義します。 MDM 機関のオプションには、Intune 単体で使用するか、Intune を Configuration Manager と連携させて使用する方法があります。|
|モバイル アプリ構成ポリシー|ベンダー固有の構成でモバイル アプリを利用できます。 たとえば、実行時に互換性のあるアプリに設定を提供するために使用される [iOS](/intune/app-configuration-policies-use-ios) または [Android](/intune/app-configuration-policies-use-android) ポリシー (会社名やサーバー アドレスなど)。|
|モバイル アプリ プロビジョニング ポリシー|割り当てる iOS アプリ用[プロビジョニング プロファイル](/intune/app-provisioning-profile-ios)が期限切れにならないようにできる iOS ポリシーです。|
|モバイル アプリケーション管理|[モバイル アプリケーション管理 (MAM)](/intune/app-lifecycle) を使用すると、ユーザーのモバイル アプリを公開、プッシュ、構成、セキュリティ保護、監視、および更新できます。
|モバイル デバイス管理|[モバイル デバイス管理 (MDM)](/intune/device-lifecycle) を使用すると、デバイスのプロビジョニング、構成、監視、管理ができるように、デバイスを Intune に登録できます。



## <a name="o"></a>O
|||
|-|-|
|OMA-DM|Open Mobile Alliance Device Management。 モバイル デバイスと PC の機能を制御できるようにするために多くのハードウェア メーカーによって使用される業界標準のデバイス管理プロトコルです。|
|OMA-URI|Open Mobile Alliance Uniform Resource Identifier。 OMA-DM 標準に準拠する個々のデバイス設定を識別します。 ニーズを満たす組み込み設定がない場合は、これらの設定を [Intune カスタム プロファイル](/intune/custom-settings-configure)で使用できます。|

## <a name="p"></a>P
|||
|-|-|
|パスコードのリセット|サポートされているデバイスでエンド ユーザーに[パスコードのリセット](/intune/device-passcode-reset)を強制できる Intune の機能です。|

## <a name="r"></a>R
|||
|-|-|
|リモート ロック|デバイスを所有していない場合でも[サポートされているデバイスをロック](/intune/device-remote-lock)できる Intune の機能です。|
|必須のインストール|このアクションでアプリを割り当てると、インストールを完了するのに[ユーザーの介入](/intune/apps-deploy)は必要ありません。 一部のプラットフォームでは、エンド ユーザーがインストールを許可する必要がある場合があります。|


## <a name="s"></a>S
|||
|-|-|
|選択的ワイプ|[選択的ワイプ](/intune/device-company-data-remove)は、デバイスの設定および電子メールのプロファイルを含め、アプリの保護ポリシーで保護されている会社データのみを削除します。 選択的ワイプでは、ユーザーの個人データはデバイス上にそのまま保持されます。|
|サイドローディング|アプリ ストアからアクセスせずに、基幹業務アプリをインストールするアクション。|
|Subscription|Intune テナントへのアクセスを許可することを示す同意。|

## <a name="t"></a>T
|||
|-|-|
|TeamViewer|Intune で管理される Android デバイスの[リモート アシスタンス機能](/intune/device-profile-android-teamviewer)を提供するために Intune と連携するサード パーティ製アプリケーションです。|
|テナント|サブスクリプションでアクセスできる Intune サービスの単一インスタンス。|
|Intune の登録および会社アクセスに関する使用条件|ユーザーに割り当てられ、ユーザーがポータル サイトを使用して作業を登録およびアクセスする前に[読んで同意](/intune/terms-and-conditions-create)する必要のある情報を含むポリシーの種類です。|

## <a name="v"></a>V
|||
|-|-|
|ボリューム購入アプリとブック|一部のアプリ ストアでは、社内で使用するアプリやブックの複数のライセンスを購入できます。 Intune を使用すれば、[このようなプログラムを通じて購入した](/intune/vpp-apps)アプリとブックを管理できます。 アプリ ストアからライセンス情報をインポートし、使用したライセンスの数を追跡し、所有しているライセンス数よりも多くのアプリをインストールしないようにすることができます。|
|VPN プロファイル|エンド ユーザーが必要なセットアップを最小限に抑えるために、管理されたデバイスに [VPN 設定](/intune/vpn-settings-configure)を割り当てるポリシーです。|

## <a name="w"></a>W
|||
|-|-|
|Wi-Fi プロファイル|ユーザーが設定を知らなくても、または構成しなくても、会社のネットワークに接続できるようにする[ワイヤレス ネットワーク設定](/intune/wi-fi-settings-configure)をデバイスに割り当てるポリシーです。
