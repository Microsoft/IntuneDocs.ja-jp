---
title: "登録済みのデバイス管理機能 | Microsoft Intune"
description: "登録するデバイスの管理における Intune の利点についてはこのトピックを参照してください。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: 710295f0eaeee71bba549c22706ecbfd062ffcb1


---
# Microsoft Intune の登録済みデバイス管理機能

Microsoft Intune では、サービスにデバイスを*登録*することによって、さまざまなデバイスを管理できます。 管理者が自分でデバイスの種類を登録することも、ユーザーが*ポータル サイト* アプリを使って登録することもできます。 ユーザーは、アプリの参照とインストール、デバイスが会社のポリシーに準拠していることの確認、IT サポートへの問い合わせなどの操作を行うこともできます。

このトピックでは、デバイスを登録した後で可能になるすべての機能を示します。

管理、インベントリ、アプリの展開、プロビジョニング、インベントリからの削除はすべて Intune 管理コンソールを介して処理されます。 ユーザーは、ポータル サイトへのアクセスを取得して、アプリをインストールし、デバイスを登録および削除し、IT 部門やヘルプデスクに連絡できます。



## デバイスのセキュリティと構成

|機能|説明|詳細情報|
|--------------|-----------|--------------------|
|構成ポリシー<br><br>カスタム ポリシー| 組織内のモバイル デバイスの多くの設定や機能を管理できます。 たとえば、パスワード必須、試行失敗の回数制限、画面をロックするまでの時間の制限、パスワードの有効期限の設定、以前に使用したパスワードの禁止を利用できます。 また、デバイス カメラや Web ブラウザーなど、ハードウェアとソフトウェアの機能の使用を制御することもできます。<br><br>カスタム ポリシーは、必要な設定が構成ポリシーに含まれていない場合に使用します。 iOS デバイスの場合は、Apple Configurator ツールからエクスポートした設定をインポートできます。 その他のデバイスの場合は、Open Mobile Alliance Uniform Resource Identifier (OMA-URI) 設定を使用して、デバイスの設定と機能を構成できます。|[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)<br />|
|リモート ワイプ、リモート ロック、パスコードのリセット|デバイスの紛失時または盗難時に、機密性の高いデータを消去します。 たとえば、遠隔操作でデバイスをロックしたり、工場出荷時の設定に戻したり、会社のデータのみをワイプしたりできます。<br><br>ユーザーがデバイスにアクセスできなくなった場合にパスコードをリセットしたり、紛失または盗難にあったデバイスをロックしたり、紛失または盗難にあったデバイスのデータをワイプしたりできます。|[Help protect your devices with remote lock and passcode reset (リモート ロックとパスコード リセットでデバイスを保護する)](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune)、[Retire devices from Intune management (Intune の管理からデバイスを削除する)](/intune/deploy-use/retire-devices-from-microsoft-intune-management)|
|キオスク モード|画面キャプチャや電源スイッチなど、モバイル デバイスの特定の機能をロックダウンすることができます。 デバイスが指定した 1 つのアプリを実行するように制限することもできます。|[Microsoft Intune の iOS 構成ポリシー設定](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|

## アプリ管理

|機能|説明|詳細情報|
|--------------|-----------|--------------------|
|アプリの展開と管理|インストール ファイルと App Store からのアプリの展開、アプリの状態の詳細な監視、アプリの削除など、モバイル アプリのライフ サイクルを通じて管理に役立つさまざまなツールを提供します。|[Deploy apps in Microsoft Intune (Microsoft Intune でアプリを展開する)](/intune/deploy-use/deploy-apps)|
|準拠アプリと非準拠アプリ|準拠アプリ (ユーザーによるインストールが許可されるアプリ) と非準拠アプリ (ユーザーによるインストールが許可されないアプリ) の一覧を指定できます。|[Microsoft Intune の iOS ポリシー設定](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|
|モバイル アプリケーション管理|Intune で管理されるものと Intune で管理されないもの両方のすべてのデバイスについて、モバイル アプリケーション管理を使用してアプリの制限を構成します。 コピー/貼り付け、データの外部バックアップ、アプリ間でのデータ転送などの操作を制限することにより、会社のデータのセキュリティを強化することができます。|[Microsoft Intune コンソールでモバイル アプリケーション管理ポリシーを構成して展開する](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)<br><br>[Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)<br /><br />[Microsoft Intune アプリ ラッピング ツールでモバイル アプリケーション管理のために iOS アプリを準備する](/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)<br /><br />[Microsoft Intune アプリ ラッピング ツールでモバイル アプリケーション管理のために Android アプリを準備する](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)|
|iOS モバイル アプリの構成|モバイル アプリ構成ポリシーを使用して、ユーザーがアプリを実行するときに必要となる可能性がある設定を iOS アプリに指定できます。 たとえば、アプリによってはユーザーがポート番号やログオン情報を指定しなければなりません。 これは、アプリの構成を簡素化し、サポート コールの数を減らすのに役立ちます。|[Microsoft Intune でのモバイル アプリ構成ポリシーを使用した iOS アプリの構成](/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|iOS モバイル アプリ プロビジョニング プロファイル|有効期限が近づいている iOS アプリにプロビジョニング プロファイルを展開できます。 |[iOS モバイル プロビジョニング プロファイルのポリシーを使用して、アプリが期限切れにならないようにする](/intune/deploy-use/ios-mobile-app-provisioning-profiles)|
|管理対象ブラウザー|管理対象ブラウザー ポリシーを構成し、デバイスのユーザーがアクセスできる Web サイトを管理します。 さらに、モバイル アプリケーション管理ポリシーを管理対象ブラウザーに適用することもできます。|[Microsoft Intune と Managed Browser のポリシーを使用したインターネット アクセスの管理](/intune/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Windows Hello for Business|Windows Hello for Business と統合できます。Windows Hello for Business は、パスワード、スマート カード、または仮想スマート カードの代わりにオンプレミスの Active Directory または Azure Active Directory による Windows 10 への代替サインイン方法です。|[Microsoft Intune を使用したデバイスで Windows Hello for Business の設定を制御する](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|
|ボリューム購入アプリ|ボリューム購入プログラムを通じて購入したアプリを管理するために、アプリ ストアからライセンス情報をインポートし、使用ライセンス数を監視して、所有しているアプリより多くインストールできないようにします。|[Microsoft Intune を使用してボリューム購入アプリを管理する](/intune/deploy-use/manage-volume-purchased-apps-in-microsoft-intune)|

## 会社のリソースへのアクセス

|機能|説明|詳細情報|
|--------------|-----------|--------------------|
|証明書プロファイル|信頼できる証明書プロファイルや、Wi-Fi プロファイル、VPN プロファイル、および電子メール プロファイルのセキュリティ保護と認証に使用できる Simple Certificate Enrollment Protocol (SCEP) 証明書を作成および展開します。|[Secure resource access with certificate profiles in Microsoft Intune (Microsoft Intune の証明書プロファイルでリソースへのアクセスを保護する)](/intune/deploy-use/secure-resource-access-with-certificate-profiles)|
|Wi-Fi プロファイル|ワイヤレス ネットワークの設定をユーザーに展開します。 これらの設定を展開して、企業ネットワークに接続するために必要なユーザーの作業を最小化します。|[Wi-Fi connections in Microsoft Intune (Microsoft Intune での Wi-Fi 接続)](/intune/deploy-use/wi-fi-connections-in-microsoft-intune)|
|電子メール プロファイル|電子メールの設定を作成し、デバイスに展開します。 これにより、ユーザー側で特別な設定を行わなくても、各自が個人用端末で会社の電子メールにアクセスできます。|[Microsoft Intune で電子メール プロファイルを使用して会社の電子メールへのアクセスを構成にする](/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|VPN プロファイル|組織内のユーザーとデバイスに VPN の設定を展開します。 これらの設定を展開して、企業ネットワーク上のリソースに接続するために必要なユーザーの作業を最小化します。|[VPN connections in Microsoft Intune (Microsoft Intune での VPN 接続)](/intune/deploy-use/vpn-connections-in-microsoft-intune)|
|条件付きアクセス ポリシー|Intune で管理されていないデバイスから Microsoft Exchange 電子メールおよび SharePoint Online へのアクセスを管理します。|[Restrict access to email and SharePoint with Microsoft Intune (Microsoft Intune を使用して電子メールと SharePoint へのアクセスを制限する)](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## インベントリとレポート

|機能|説明|詳細情報|
|--------------|-----------|--------------------|
|インベントリとレポート|管理対象のデバイスと、デバイスが使用しているソフトウェアの詳細が記載されています。|[Microsoft Intune でインベントリを使用してデバイスを把握する](/intune/deploy-use/understand-your-devices-with-inventory-in-microsoft-intune)|


### 関連項目
[Microsoft Intune の Windows PC 管理機能](windows-pc-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Oct16_HO4-->


