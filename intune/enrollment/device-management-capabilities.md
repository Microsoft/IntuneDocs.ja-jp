---
title: Microsoft Intune のデバイス管理機能
description: 登録するデバイスの管理における Intune の利点についてはこのトピックを参照してください。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1bac049aebfb0fec6c9d86e1e08e81237867175d
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723113"
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Microsoft Intune の登録済みデバイス管理機能

Microsoft Intune では、サービスにデバイスを*登録*することによって、さまざまなデバイスを管理できます。 管理者が自分でデバイスの種類を登録することも、ユーザーが*ポータル サイト* アプリを使って登録することもできます。 登録すると、アプリを参照してインストールし、デバイスが会社のポリシーに準拠していることを確認し、IT サポートに連絡することができます。

この記事では、デバイスの登録後に使用できるようになるすべての機能について説明します。

管理、インベントリ、アプリの展開、プロビジョニング、インベントリからの削除はすべて、Azure portal 内で Intune を介して処理されます。

ユーザーは、ポータル サイトへのアクセスを取得して、アプリをインストールし、デバイスを登録および削除し、IT 部門やヘルプデスクに連絡できます。



## <a name="device-security-and-configuration"></a>デバイスのセキュリティと構成

|機能|説明|詳細情報|
|--------------|-----------|--------------------|
|構成ポリシー<br><br>カスタム ポリシー| 組織内のモバイル デバイスの多くの設定や機能を管理できます。 たとえば、パスワード必須、試行失敗の回数制限、画面をロックするまでの時間の制限、パスワードの有効期限の設定、以前に使用したパスワードの禁止を利用できます。 また、デバイス カメラや Web ブラウザーなど、ハードウェアとソフトウェアの機能の使用を制御することもできます。<br><br>カスタム ポリシーは、必要な設定が構成ポリシーに含まれていない場合に使用します。 iOS デバイスの場合は、Apple Configurator ツールからエクスポートした設定をインポートできます。 その他のデバイスの場合は、Open Mobile Alliance Uniform Resource Identifier (OMA-URI) 設定を使用して、デバイスの設定と機能を構成できます。|[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](../protect/device-compliance-get-started.md)|
|リモート ワイプ、リモート ロック、パスコードのリセット|デバイスの紛失時または盗難時に、機密性の高いデータを消去します。 たとえば、遠隔操作でデバイスをロックしたり、工場出荷時の設定に戻したり、会社のデータのみをワイプしたりできます。<br><br>ユーザーがデバイスにアクセスできなくなった場合にパスコードをリセットしたり、紛失または盗難にあったデバイスをロックしたり、紛失または盗難にあったデバイスのデータをワイプしたりできます。|[リモート ロック](../remote-actions/device-remote-lock.md)と[パスコードのリセット](../remote-actions/device-passcode-reset.md)によってデバイスを保護する|
|キオスク モード|画面キャプチャや電源スイッチなど、モバイル デバイスの特定の機能をロックダウンすることができます。 デバイスが指定した 1 つのアプリを実行するように制限することもできます。 |[Microsoft Intune の iOS 構成ポリシー設定](../configuration/device-restrictions-ios.md)|

## <a name="app-management"></a>アプリ管理

|機能|説明|詳細情報|
|--------------|-----------|--------------------|
|アプリの展開と管理|インストール ファイルと App Store からのアプリの展開、アプリの状態の詳細な監視、アプリの削除など、モバイル アプリのライフ サイクルを通じて管理に役立つさまざまなツールを提供します。|[Microsoft Intune でアプリを展開する](../apps/apps-deploy.md)|
|準拠アプリと非準拠アプリ|準拠アプリ (ユーザーによるインストールが許可されるアプリ) と非準拠アプリ (ユーザーによるインストールが許可されないアプリ) の一覧を指定できます。|[Microsoft Intune の iOS ポリシー設定](../configuration/device-restrictions-ios.md)|
|モバイル アプリケーション管理|Intune で管理されるものと Intune で管理されないもの両方のすべてのデバイスについて、モバイル アプリケーション管理を使用してアプリの制限を構成します。 コピー/貼り付け、データの外部バックアップ、アプリ間でのデータ転送などの操作を制限することにより、会社のデータのセキュリティを強化することができます。|[Microsoft Intune コンソールでモバイル アプリケーション管理ポリシーを構成して展開する](../developer/app-wrapper-prepare-android.md)|
|iOS モバイル アプリの構成|モバイル アプリ構成ポリシーを使用して、ユーザーがアプリを実行するときに必要となる可能性がある設定を iOS アプリに指定できます。 たとえば、アプリによってはユーザーがポート番号やログオン情報を指定しなければなりません。 アプリの構成を整理し、サポート コールの数を減らすことができます。|[Microsoft Intune でのモバイル アプリ構成ポリシーを使用した iOS アプリの構成](../apps/app-configuration-policies-use-ios.md)|
|iOS モバイル アプリ プロビジョニング プロファイル|有効期限が近づいている iOS アプリにプロビジョニング プロファイルを展開できます。 |[iOS モバイル プロビジョニング プロファイルのポリシーを使用して、アプリが期限切れにならないようにする](../apps/app-provisioning-profile-ios.md)|
|管理対象ブラウザー|管理対象ブラウザー ポリシーを構成し、デバイスのユーザーがアクセスできる Web サイトを管理します。 さらに、モバイル アプリケーション管理ポリシーを管理対象ブラウザーに適用することもできます。|[Microsoft Intune と Managed Browser のポリシーを使用したインターネット アクセスの管理](../apps/app-configuration-managed-browser.md)|
|Windows Hello for Business|Windows Hello for Business と統合できます。Windows Hello for Business は、パスワード、スマート カード、または仮想スマート カードの代わりにオンプレミスの Active Directory または Azure Active Directory による Windows 10 への代替サインイン方法です。|[Microsoft Intune を使用したデバイスで Windows Hello for Business の設定を制御する](../protect/windows-hello.md)|
|ボリューム購入アプリ|ボリューム購入プログラムを通じて購入したアプリを管理するために、アプリ ストアからライセンス情報をインポートし、使用ライセンス数を監視して、所有しているアプリより多くインストールできないようにします。|[Microsoft Intune を使用してボリューム購入アプリを管理する](../apps/vpp-apps.md)|

## <a name="company-resource-access"></a>会社のリソースへのアクセス

|機能|説明|詳細情報|
|--------------|-----------|--------------------|
|証明書プロファイル|信頼できる証明書プロファイルや、Wi-Fi プロファイル、VPN プロファイル、および電子メール プロファイルのセキュリティ保護と認証に使用できる Simple Certificate Enrollment Protocol (SCEP) 証明書を作成および展開します。|[Secure resource access with certificate profiles in Microsoft Intune](../protect/certificates-configure.md) (Microsoft Intune の証明書プロファイルでリソースへのアクセスを保護する)|
|Wi-Fi プロファイル|ワイヤレス ネットワークの設定をユーザーに展開します。 これらの設定を展開して、企業ネットワークに接続するために必要なユーザーの作業を最小化します。|[Microsoft Intune での Wi-Fi 接続](../configuration/wi-fi-settings-configure.md)|
|電子メール プロファイル|電子メール設定を作成し、デバイスに展開することで、ユーザー側で特別な設定を行わなくても、各自が個人用端末で会社の電子メールにアクセスできるようになります。|[Microsoft Intune で電子メール プロファイルを使用して会社の電子メールへのアクセスを構成にする](../configuration/email-settings-configure.md)|
|VPN プロファイル|組織内のユーザーとデバイスに VPN の設定を展開します。 これらの設定を展開して、企業ネットワーク上のリソースに接続するために必要なユーザーの作業を最小化します。|[Microsoft Intune での VPN 接続](../configuration/device-profiles.md#vpn)|
|条件付きアクセス ポリシー|Intune で管理されていないデバイスから Microsoft Exchange 電子メールおよび SharePoint Online へのアクセスを管理します。|[Microsoft Intune を使用して電子メールと SharePoint へのアクセスを制限する](../protect/app-based-conditional-access-intune.md)|

## <a name="next-steps"></a>次の手順

[管理できるデバイスの一覧を参照してください](../remote-actions/device-management.md)。
