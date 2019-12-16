---
title: 企業 ID を Intune に追加する
titleSuffix: ''
description: 企業 ID (登録方法、IMEI 番号、シリアル番号) を Microsoft Intune に追加する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4e1ee8ae54d81a050f3c8983269f40e8f61b5e75
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955475"
---
# <a name="identify-devices-as-corporate-owned"></a>デバイスの企業所有としての識別

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 管理者は、会社所有のデバイスを特定することで、管理と識別の対象を絞り込むことができます。 Intune は追加の管理タスクを実行して、会社所有のデバイスの完全な電話番号やアプリのインベントリなどの追加情報を収集できます。 また、デバイス制限を設定し、会社所有ではないデバイスによる登録を防止できます。

Intune は登録時に、次のようなデバイスに会社所有の状態を自動的に割り当てます。

- [デバイス登録マネージャー](device-enrollment-manager-enroll.md) アカウントで登録されている (すべてのプラットフォーム)
- Apple [Device Enrollment Program](device-enrollment-program-enroll-ios.md)、[Apple School Manager](apple-school-manager-set-up-ios.md)、[Apple Configurator](apple-configurator-enroll-ios.md) (iOS のみ) で登録されている
- IMEI (International Mobile Equipment Identifier/国際携帯機器識別) 番号 (IMEI 番号を持つすべてのプラットフォーム) またはシリアル番号 (iOS と Android) で、[登録前に会社所有として識別されている](#identify-corporate-owned-devices-with-imei-or-serial-number)
- 職場または学校の資格情報を使用して Azure Active Directory に参加します。 [Azure Active Directory に登録されているデバイス](https://docs.microsoft.com/azure/active-directory/devices/overview)は個人用とマークされます。
- [デバイスのプロパティ一覧](#change-device-ownership)で、会社として設定されている

登録後、**[個人]** と **[企業]** のどちらかで[所有権の設定を変更する](#change-device-ownership)ことができます。

## <a name="identify-corporate-owned-devices-with-imei-or-serial-number"></a>IMEI またはシリアル番号により、会社所有デバイスとして特定される

Intune 管理者は、14 桁の IMEI 番号またはシリアル番号をリストしたコンマ区切り値 (.csv) ファイルを作成して、インポートできます。 Intune は、デバイス登録時、この識別子を使用し、デバイスの所有権を会社として指定します。 各 IMEI またはシリアル番号の一覧には管理目的で詳細を追加できます。

この機能は、次のプラットフォームでサポートされます。

| プラットフォーム | IMEI 番号 | シリアル番号 |
|---|---|---|
| Windows | サポートされています (Windows Phone) | サポートされていません |
| iOS/macOS | サポートされていません | サポート |
| デバイス管理者によって管理されている Android OS v10 | サポートされていません | サポートされていません |
| その他の Android | サポートされていません | サポート |

<!-- When you upload serial numbers for corporate-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as corporate-owned. -->

Apple デバイスのシリアル番号の検索方法については、[こちら](https://support.apple.com/HT204308)をご覧ください。<br>
Android デバイスのシリアル番号の検索方法については、[こちら](https://support.google.com/store/answer/3333000)をご覧ください。

## <a name="add-corporate-identifiers-by-using-a-csv-file"></a>.csv ファイルを使用して企業 ID を追加する
リストを作成するには、ヘッダーなしの 2 列のコンマ区切り値 (.csv) リストを作成します。 14 桁の IMEI またはシリアル番号を左側の列に、詳細を右側の列に追加します。 1 つの .csv ファイルにインポートできるのは、1 種類の ID、IMEI、またはシリアル番号のみです。 詳細の上限は 128 文字です。また、管理者のみが使用できます。 詳細はデバイスに表示されません。 現在の上限は .csv ファイルあたり 5,000 行です。

**シリアル番号が含まれている .csv ファイルをアップロード** – csv ファイル 1 つあたりデバイス 5,000 個または 5 MB を上限とする、2 つの列を持つヘッダーなしのコンマ区切り値のリスト (.csv) を作成します。

|||
|-|-|
|&lt;ID #1&gt;|&lt;デバイス 1 の詳細&gt;|
|&lt;ID #2&gt;|&lt;デバイス 2 の詳細&gt;|

この .csv ファイルをテキスト エディターで開くと、次のように表示されます。

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> 一部の Android および iOS デバイスには複数の IMEI 番号があります。 Intune は、登録済みデバイスごとに 1 つの IMEI 番号のみを読み取ります。 IMEI 番号をインポートするときに、その番号が Intune にインベントリされている IMEI ではない場合、デバイスは会社所有のデバイスではなく個人のデバイスとして分類されます。 1 台のデバイスに複数の IMEI 番号をインポートすると、インベントリされていない番号の登録状態は **[不明]** と表示されます。<br>
>次の点にも注意してください。シリアル番号は、iOS デバイスの ID の推奨される形式です。
>Android のシリアル番号は一意であることと存在することが保証されていません。 シリアル番号が信頼できるデバイス ID であるかどうかは、デバイスの供給元にご確認ください。
>デバイスから Intune に報告されたシリアル番号は、Android デバイスの [設定]/[バージョン情報] メニューに表示される ID と一致しない場合があります。 デバイスの製造元から報告されたシリアル番号の種類をご確認ください。
>ドット (.) が含まれるシリアル番号のファイルをアップロードしようとすると、アップロードが失敗します。 ドット (.) が含まれるシリアル番号はサポートされていません。

### <a name="upload-a-csv-list-of-corporate-identifiers"></a>企業 ID の .csv リストをアップロードする

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインし、**[デバイス]** > **[デバイスの登録]** > **[業務用デバイスの ID]** > **[追加]** > **[CSV ファイルをアップロード]** の順に選択します。

2. **[ID の追加]** ブレードで、ID の種類として **[IMEI]** または **[シリアル]** を指定します。

3. フォルダー アイコンをクリックし、インポートするリストのパスを指定します。 .csv ファイルに移動して、**[追加]** を選択します。 

4. .csv ファイルに含まれる企業 ID が既に Intune 内に存在しているが、その詳細は異なる場合、**[重複した ID を確認する]** ポップアップが表示されます。 Intune に上書きする ID を選択し、**[OK]** を選択して、ID を追加します。 各識別子について、最初の重複のみが比較されます。

## <a name="manually-enter-corporate-identifiers"></a>企業 ID を手動で入力する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインし、**[デバイス]** > **[デバイスの登録]** > **[業務用デバイスの ID]** > **[追加]** > **[手動で入力]** の順に選択します。

2. **[ID の追加]** ブレードで、ID の種類として **[IMEI]** または **[シリアル]** を指定します。

3. 追加する ID ごとに、**[ID]** と **[詳細]** を入力します。 ID の入力を完了したら、**[追加]** を選択します。

5. 入力した企業 ID は Intune 内に既に存在しているが、その詳細が異なる場合は、**[重複した ID を確認する]** ポップアップが表示されます。 Intune に上書きする ID を選択し、**[OK]** を選択して、ID を追加します。 各識別子について、最初の重複のみが比較されます。

**[更新]** をクリックすると、新しいデバイス ID が表示されます。

インポートされたデバイスが必ずしも登録されているとは限りません。 デバイスは **[登録済み]** または **[未接続]** のどちらかの状態になります。 **未接続** の場合、デバイスは Intune サービスで通信に使われていません。

## <a name="delete-corporate-identifiers"></a>企業 ID を削除する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインし、**[デバイス]** > **[デバイスの登録]** > **[業務用デバイスの ID]** の順に選択します。
2. 削除するデバイス識別子を選択し、**[削除]** を選択します。
3. 削除を確認します。

登録済みデバイスの企業識別子を削除すると、デバイスの所有権が変更されます。 デバイスの所有権を変更するには、**[デバイス]** に進み、デバイスを選択し、**[プロパティ]** を選択し、**[デバイスの所有者]** を変更します。

## <a name="imei-specifications"></a>IMEI の仕様
International Mobile Equipment Identifier の詳しい仕様については、「[3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729)」を参照してください。

## <a name="change-device-ownership"></a>デバイス所有権を変更する

デバイスのプロパティには、Intune のデバイス レコード別の**所有権**が表示されます。 管理者はデバイスを**個人用**または**企業所有**として指定できます。 デバイスの所有権の種類が個人から会社に変更されると、Intune ではそのデバイスから以前に収集されたすべてのアプリ情報が 7 日以内に削除されます。 該当する場合、Intune ではレコード上の電話番号も削除されます。 

**デバイス所有権を変更するには:**
1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインして、**[デバイス]** > **[すべてのデバイス]** の順に選択し、デバイスを選択します。
2. **[プロパティ]** を選択します。
3. **[デバイスの所有権]** に **[個人]** または **[企業]** を指定します。

   ![デバイスのカテゴリと所有権のオプションが表示されたデバイス プロパティ](./media/corporate-identifiers-add/device-properties.png)
