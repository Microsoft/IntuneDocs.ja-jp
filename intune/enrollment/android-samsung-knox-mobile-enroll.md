---
title: Samsung の Knox Mobile Enrollment を使用して Android デバイスを自動的に登録する
titleSuffix: Microsoft Intune
description: Samsung KME を使用して Android デバイスを登録する方法について説明します
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5f290370dd6ec05677a7073d9ca3edd854c9aa5e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505574"
---
# <a name="automatically-enroll-android-devices-by-using-samsungs-knox-mobile-enrollment"></a>Samsung の Knox Mobile Enrollment を使用して Android デバイスを自動的に登録する

このトピックでは、Samsung Knox Mobile Enrollment (KME) を使用してサポートされる Android デバイスを登録するための Intune の設定について説明します。 Samsung KME で Intune を使うと、会社が所有する多数の Android デバイスを、エンド ユーザーが初めてデバイスの電源を入れて WiFi または移動体通信ネットワークに接続したときに、登録することができます。 また、Knox Deployment App を使っている場合は、Bluetooth または NFC を使ってデバイスを登録することもできます。

Samsung KME を使って Intune の登録を有効にするには、Intune と Samsung Knox 両方のポータルを次の順序で使います。

1. Knox ポータルで次のことを行います。
    1. [MDM プロファイルを作成します](#create-mdm-profile)
    2. [デバイスを追加します](#add-devices)
    3. [MDM プロファイルをデバイスに割り当てます](#assign-an-mdm-profile-to-devices)
2. Knox ポータルで、[エンド ユーザーのサインインを構成します](#configure-how-end-users-sign-in)。
3. [デバイスを配布します](#distribute-devices)。


Knox Deployment Program に参加している承認されたリセラーからデバイスを購入すると、デバイス識別子 (シリアル番号と IMEI) の一覧が Knox ポータルに自動的に追加されます。


## <a name="prerequisites"></a>必要条件

KME を使って Intune に登録するには、最初に、次の手順に従って、Samsung Knox ポータルで会社を登録する必要があります。
1. [お住まいの国/地域で KME が使用可能であることを確認する](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries):KME は 55 を超える国/地域で使用できます。 展開する国/地域がサポートされていることを確認します。

2. [サポートされているデバイス](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+):KME は、Android の登録については Knox 2.4 以降、Android エンタープライズの登録については Knox 2.8 以降の、すべての Samsung デバイスで使用できます。

3. [ネットワーク要件](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm):必要なファイアウォール ルールとネットワーク アクセス ルールが、ネットワークで許可されていることを確認します。

4. [Samsung アカウントの登録](https://www2.samsungknox.com/en/user/register):KME に登録して有効にし、Knox Enterprise のすべての権利を一元管理するには、Samsung アカウントが必要です。

5. 登録の確認:プロファイルが完成して送信されると、Samsung によってお客様のアプリケーションが確認され、すぐに承認されるか、またはさらなるフォローアップのために確認保留状態になります。 アカウントが承認された後は、以降の手順に進むことができます。

## <a name="create-mdm-profile"></a>MDM プロファイルを作成する

会社が正常に登録されると、以下の情報を使用して Knox ポータルで Microsoft Intune の MDM プロファイルを作成できます。 Android と Android エンタープライズ両方の MDM プロファイルを、Knox ポータルで作成できます。 

### <a name="for-android-enterprise"></a>Android エンタープライズの場合

| MDM プロファイルのフィールド| 必須 | 値 | 
|-------------------|-----------|-------| 
|MDM Server URI (MDM サーバーの URI)     | [いいえ]        |空白のままにします。 
|プロファイル名       | はい       |選択したプロファイル名を入力します。 
|説明        | [いいえ]        |プロファイルを説明するテキストを入力します。 
|MDM Agent APK (MDM エージェント APK)      | はい       |https://aka.ms/intune_kme_deviceowner 
|Enable this app as a Google Device Owner (このアプリを Google デバイスの所有者として有効にする) | はい | Android エンタープライズに登録するには、このオプションを選択します。 
|Supported MDM (サポートされる MDM)      | はい       |Microsoft Intune 
|Leave all system apps enabled (すべてのシステム アプリを有効のままにする) | [いいえ] | すべてのアプリを有効にして、プロファイルで使用できるようにするには、このオプションを選択します。 このオプションを選択しない場合は、限られたシステム アプリのセットのみがデバイスのアプリ トレイに表示されます。 メール アプリなどのアプリが非表示のままになります。 
|Custom JSON (カスタム JSON)        | [いいえ]        |{"com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN":"Intune 登録トークン文字列を入力してください"}。 [登録プロファイルの作成方法](android-kiosk-enroll.md)に関する記事をご覧ください。 
| Add legal agreements (法的契約を追加する) | [いいえ] | 空白のままにします。 

### <a name="for-android"></a>Android の場合

詳しい手順については、[Samsung Knox Profile Setup Wizard](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm) の説明をご覧ください。

| MDM プロファイルのフィールド| 必須 | 値 |
|-------------------|-----------|-------|
|MDM Server URI (MDM サーバーの URI)     | [いいえ]        |空白のままにします。
|プロファイル名       | はい       |選択したプロファイル名を入力します。
|説明        | [いいえ]        |プロファイルを説明するテキストを入力します。
|MDM Agent APK (MDM エージェント APK)      | はい       |https://aka.ms/intune_kme
|Enable this app as a Google Device Owner (このアプリを Google デバイスの所有者として有効にする) | [いいえ] | Android の場合はオフのままにします。 このオプションは Android エンタープライズに対してのみ適用されます。
|Skip Setup wizard (セットアップ ウィザードをスキップ)  | [いいえ]        |エンド ユーザーに対する標準のデバイス セットアップ プロンプトをスキップするには、このオプションを選択します。
|Allow End User to Cancel Enrollment (エンド ユーザーが登録をキャンセルするのを許可) | [いいえ] | ユーザーが KME をキャンセルできるようにするには、このオプションを選択します。
|Custom JSON (カスタム JSON)        | [いいえ]        |空白のままにします。
| Add legal agreements (法的契約を追加する) | [いいえ] | 空白のままにします。
Associate a Knox license with this profile (このプロファイルと Knox ライセンスを関連付け) | [いいえ] | オフのままにします。 KME を使った Intune への登録には、Knox ライセンスは必要ありません。

## <a name="add-devices"></a>デバイスを追加する

デバイスに MDM プロファイルを割り当てるには、次の方法のどれかで、サポートされる Samsung Knox デバイスを Knox ポータルに追加する必要があります。
- **Samsung-承認リセラーの使用:** Samsung 承認リセラーのいずれかからデバイスを購入する場合は、この方法を使います。 承認すると、リセラーはデバイスを自動アップロードできます。 [リセラーの追加方法は、Samsung Knox 登録ユーザー ガイドをご覧ください](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm)。

- **Knox Deployment App (KDA) の使用:** KME を使って登録する必要がある既存のデバイスがある場合は、この方法を使います。 Bluetooth または NFC を使って、この方法で Knox ポータルにデバイスを追加できます。 [KDA の使い方は、Samsung Knox 登録ユーザー ガイドをご覧ください](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm)。

## <a name="assign-an-mdm-profile-to-devices"></a>デバイスに MDM プロファイルを割り当てる
登録する前に、Knox ポータルで追加するデバイスに MDM プロファイルを割り当てる必要があります。 [デバイス構成については、Samsung Knox 登録ユーザー ガイドをご覧ください](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm)。

## <a name="configure-how-end-users-sign-in"></a>エンドユーザーのサインイン方法を構成する

KME for Android を使用して Intune に登録されたデバイスの場合、エンド ユーザーがサインインする方法を次のように構成できます。

- **ユーザー名の関連付けなし:** Knox ポータルの **[Device details]\(デバイスの詳細\)** で、追加したデバイスの **[User ID]\(ユーザー ID\)** と **[Password]\(パスワード\)** フィールドを空白のままにします。 このオプションを使うと、エンド ユーザーは、Intune に登録するときにユーザー名とパスワードの両方を入力するよう求められます。

- **ユーザー名の関連付けあり:** Knox ポータルの **[Device details]\(デバイスの詳細\)** で、追加したデバイスの **[User ID]\(ユーザー ID\)** (割り当てられたユーザーのユーザー名、または[デバイス登録マネージャー](device-enrollment-manager-enroll.md) アカウントなど) を提供します。 このオプションを使うと、Intune への登録時にユーザー名が事前入力され、エンド ユーザーはパスワードを入力するよう求められます。

> [!NOTE]
>
>ユーザーの関連付けは、Android デバイス管理者の登録にのみ適用されます。 ユーザー関連付けを定義すると、関連付けられたユーザーだけが KME を使ってデバイスを登録できます。 これは、デバイスの工場出荷時リセット後も当てはまります。 Knox ポータルでユーザー関連付けを定義しないと、有効な Intune ライセンスを持つすべてのユーザーが KME を使ってデバイスを登録できます。
>Android Enterprise のフル マネージド デバイスでは、ユーザーの関連付けが定義されている場合でも、デバイスに渡されたり、デバイスがユーザーに関連付けられたりすることはありません。
>

## <a name="distribute-devices"></a>デバイスを配布する

MDM プロファイルを作成して割り当て、ユーザー名を関連付け、Intune でデバイスを企業所有として識別した後、ユーザーにデバイスを配布できます。

サポートが必要な場合は、 完全な [KME ユーザー ガイド](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm)に関するページをご覧ください。

## <a name="frequently-asked-questions"></a>よく寄せられる質問

- **デバイス所有者のサポート:**  - **デバイス所有者のサポート:** Intune では、KME ポータルを使用した専用およびフル マネージド デバイスの登録がサポートされています。 他の Android エンタープライズ デバイス所有者モードは、Intune で利用可能になったらサポートされます。

- **仕事用プロファイルのサポートなし**:KME は会社のデバイスを登録する方法であり、デバイスを Android 仕事用プロファイルに登録することにより、個人のデバイスの仕事用データと個人用データが別々に管理されるようになります。 そのため Intune では、KME を使用してデバイスを仕事用プロファイルに登録するシナリオはサポートされていません。

- **Android エンタープライズに対する登録への工場出荷時リセット:** 既に設定されているデバイスを用途変更する場合は、Android エンタープライズに登録するときに、デバイスを工場出荷時の状態にリセットする必要があります。

- **Google Play アカウントを使用した更新:** Microsoft Intune にデバイスを登録するために、Google Play アカウントは必要ありません。 ただし、Android デバイス管理者の登録の場合、Intune ポータル サイト アプリの今後の更新では、デバイスの Google Play アカウントが必要になる場合があります。 Google デバイス所有者に登録するときは、Google Play アカウントは必要ありません。

- **"パスワード" フィールドが無視される:** Knox ポータルの **[デバイスの詳細]** で **[パスワード]** フィールドが設定されている場合、これは Android 登録の間に Intune ポータル サイト アプリで無視されます。 エンド ユーザーは、デバイス登録を完了するにはデバイスでパスワードを入力する必要があります。


## <a name="getting-support"></a>サポートの入手
詳細については、[Samsung KME のサポートを取得する方法](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm)をご覧ください。


