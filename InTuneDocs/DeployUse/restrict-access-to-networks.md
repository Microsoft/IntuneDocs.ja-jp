---
title: "Cisco ISE でネットワークへのアクセスを制限する | Microsoft Intune"
description: "Cisco ISE で制御されている Wi-Fi および VPN にアクセスする前に、デバイスが登録されポリシーに準拠するように、Intune で Cisco ISE を使用します。"
keywords: 
author: nbigman
manager: angrobe
ms.date: 06/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5631bac3-921d-438e-a320-d9061d88726c
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 40194f4359d0889806e080a4855b8e1934b667f9
ms.openlocfilehash: 9d6b7198e3c2e30898a8ec83785c7f3b777eda5f


---

# Microsoft Intune で Cisco ISE を使用する
Intune を Cisco Identity Services Engine (ISE) と統合すると、Intune のデバイス登録と準拠の状態を使用して、ISE 環境内でネットワーク ポリシーを作成することができます。 これらのポリシーを使用すると、会社のネットワークへのアクセスが、Intune で管理され Intune ポリシーに準拠しているデバイスに制限されるように処理することができます。

## 構成手順

この統合を有効にするために、Intune テナントでセットアップを行う必要はありません。 Intune テナントにアクセスするアクセス許可を、Cisco ISE サーバーに与える必要があります。 これを行った後、セットアップの残りの部分は Cisco ISE サーバーで行われます。 この記事では、Intune テナントにアクセスする権限を持つ ISE サーバーを提供する手順について説明します。

### 手順 1: 証明書を管理する
1. Azure Active Directory (Azure AD) コンソールで、証明書をエクスポートします。

#### Internet Explorer 11


   a. 管理者として Internet Explorer を実行して、Azure AD コンソールにサインインします。

   b. アドレス バーでロック アイコンを選択して、**[証明書の表示]** を選択します。

   c. 証明書のプロパティの **[詳細]** タブで、**[ファイルにコピー]** を選択します。

   d. **証明書のエクスポート ウィザードの** [ようこそ] ページで、**[次へ]** を選択します。

   e. **[エクスポート ファイル形式]** ページで、既定値の **[DER encoded binary X.509 (.CER)]** のままにして、**[次へ]** を選択します。  

   f. **[エクスポートするファイル]** ページで、**[参照]** をクリックして、ファイルを保存する場所を選択し、ファイル名を指定します。 エクスポートするファイルを選択するのと似ていますが、実際にエクスポートする証明書が保存されるファイルに名前を付けます。 **[次へ]** &gt; **[完了]** を選択します。

#### Safari

 a. Azure AD コンソールにサインインします。

b. ロック アイコン &gt; **[詳細]** をクリックします。

   c. **[証明書の表示]** &gt; **[詳細]** を選択します。

   d. 証明書を選択し、**[エクスポート]** を選択します。  

> [!IMPORTANT]
>
> 証明書の有効期限が切れた場合、新しい証明書をエクスポートしてインポートする必要があるため、証明書の有効期限を確認します。


2. ISE コンソール内から、Intune 証明書 (エクスポートしたファイル) を **[信頼できる証明書]** にインポートします。


### ISE からの自己署名証明書の取得 

1.  ISE コンソールで、**[Administration]** (管理)  > **[Certificates]** (証明書)  > **[System Certificates]** (システム証明書)  > **[Generate Self Signed Certificate]** (自己署名証明書の生成) の順に選択します。  
2.       自己署名証明書をエクスポートします。
3. テキスト エディターで、エクスポートした証明書を編集します。
 - ** -----BEGIN CERTIFICATE-----** を削除する
 - ** -----END CERTIFICATE-----**を削除する
 
すべてのテキストが単一行であることを確認する


### 手順 2: Azure AD テナントで ISE のアプリを作成する
1. Azure AD コンソールで、**[アプリケーション]** > **[アプリケーションの追加]** > **[組織で開発中のアプリケーションを追加]** の順に選択します。
2. アプリの名前と URL を指定します。 URL は、会社の Web サイトである可能性があります。
3. アプリ マニフェスト (JSON ファイル) をダウンロードします。
4. マニフェストの JSON ファイルを編集します。 **[keyCredentials]** と呼ばれる設定で、手順 1 で編集した証明書のテキストを設定値として指定します。
5. 名前を変更しないで、ファイルを保存します。
6. Microsoft Graph と Microsoft Intune API へのアクセス許可を持つアプリを指定します。

 a. Microsoft Graph の場合は、次のように選択します。
    - **アプリケーションのアクセス許可**: ディレクトリ データの読み取り
    - **委任されたアクセス許可**:
        - ユーザーのデータへの常時アクセス
        - ユーザーのサインイン

 b. Microsoft Intune API では、**[アプリケーションのアクセス許可]** で、**[Intune からデバイスの状態とコンプライアンスを所得する]** を選択します。

7. **[エンドポイントの表示]** を選択して、ISE 設定の構成で使用する次の値をコピーします。

|Azure AD ポータルでの値|ISE ポータルの対応フィールド|
|-------------------|---------------------------------|
|Microsoft Azure AD Graph API エンドポイント|自動検出 URL|
|OAuth 2.0 トークン エンドポイント|トークン発行 URL|
|クライアント ID でコードを更新する|クライアント ID|


### 手順 3: ISE 設定を構成する
ISE 管理コンソールで、次の設定値を指定します。
  - **サーバーの種類**: Mobile Device Manager
  - **認証の種類**: OAuth – クライアントの資格情報
  - **自動検出**: はい
  - **自動検出 URL**: *手順 1 の値を入力します。*
  - **クライアント ID**: *手順 1 の値を入力します。*
  - **トークンの発行 URL**: *手順 1. の値を入力します。*



## Intune テナントと Cisco ISE サーバー間で共有される情報
次の表には、Intune テナントと Intune によって管理されるデバイス用の Cisco ISE サーバー間で共有される情報を一覧します。

|プロパティ|  説明|
|---------------|------------------------------------------------------------|
|complianceState|デバイスが準拠か非準拠かを示す true または false の文字列。|
|isManaged|クライアントが Intune で管理されるかどうかを示す true または false の文字列。|
|macAddress|デバイスの MAC アドレス。|
|serialNumber|デバイスのシリアル番号。 iOS デバイスにのみ適用されます。|
|imei|IMEI (15 桁の 10 進数: 14 桁とチェック ディジット) または IMEISV (16 桁) 番号には、デバイスの製造元、モデル、およびシリアル番号の情報が含まれています。 この番号の構造は、3GPP TS 23.003 で指定されます。 SIM カードのあるデバイスのみに適用されます。|
|udid|一意のデバイス ID。40 個の文字と数字から成ります。 これは、iOS デバイスに固有です。|
|meid|モバイル デバイス ID。CDMA モバイル ステーション装置の物理パーツを識別するグローバル一意識別番号です。 値の形式は、3GPP2 レポート S. R0048 によって定義されています。 ただし、IMEI のように見えますが、実際には 16 進数です。 MEID は 56 ビット長 (14 桁の 16 進数) です。 8 ビットの地域コード (RR)、24 ビットの製造元コード、24 ビットの製造元によって割り当てられたシリアル番号を含む、3 つのフィールドで構成されます。|
|osVersion|デバイスのオペレーティング システムのバージョン。
|対象となるのは、モデル|デバイスのモデル。
|manufacturer|デバイスの製造元。
|azureDeviceId|Azure AD に社内参加した後のデバイス ID。 参加していないデバイスの場合は空の GUID です。|
|lastContactTimeUtc|デバイスが Intune の管理サービスで最後に確認された日付と時刻。


## ユーザー側の表示と操作

ユーザーが登録したデバイスを使用してリソースにアクセスしようとすると、次のように、登録するように求めるメッセージが表示されます。

![登録プロンプトの例](../media/cisco-ise-user-iphone.png)

ユーザーが登録を選択すると、Intune の登録プロセスにリダイレクトされます。 次のトピックでは、Intune のユーザー登録エクスペリエンスについて説明します。

- [Intune に Android デバイスを登録する](/intune/enduser/enroll-your-device-in-Intune-android)</br>
- [Intune に iOS デバイスを登録する](/intune/enduser/enroll-your-device-in-intune-ios)</br>
- [Intune に Mac OS X デバイスを登録する](/intune/enduser/enroll-your-device-in-intune-mac-os-x)</br>
- [Intune に Windows デバイスを登録する](/intune/enduser/enroll-your-device-in-intune-windows)</br>

また、ユーザー エクスペリエンスのためにカスタマイズされたガイダンスを作成できる、[ダウンロード可能な一連の登録手順](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a)もあります。


### 関連項目

[Cisco Identity Services Engine 管理者ガイド、リリース 2.1](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html#task_820C9C2A1A6647E995CA5AAB01E1CDEF)



<!--HONumber=Sep16_HO1-->


