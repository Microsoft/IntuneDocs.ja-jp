---
title: アプリのデータ転送ポリシーの例外
titleSuffix: Microsoft Intune
description: Intune App Protection Policy (APP) データ転送ポリシーの例外を作成します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 09c8a8819c288663936174e9317267c39eac63bc
ms.sourcegitcommit: ecaff388038fb800f2e646f8efcf8f3b1e2fd1b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/18/2020
ms.locfileid: "77437853"
---
# <a name="how-to-create-exceptions-to-the-intune-app-protection-policy-app-data-transfer-policy"></a>Intune App Protection Policy (APP) データ転送ポリシーの例外を作成する方法

管理者は Intune App Protection Policy (APP) データ転送ポリシーの例外を作成できます。 例外を使用すると、管理対象アプリとの間でデータをやりとりできる管理対象ではないアプリを指定できます。 管理者が例外一覧に追加した管理対象ではないアプリは、IT 部門に信頼されている必要があります。 

>[!WARNING] 
> 管理者は、データ転送の例外ポリシーを変更する責任があります。 管理対象ではないアプリ (Intune によって管理されていないアプリケーション) は、このポリシーに追加すると、管理対象アプリによって保護されているデータにアクセスできるようになります。 このような保護されたデータのアクセスで、データ セキュリティの漏えいが発生する可能性があります。 組織で使用する必要があり、Intune APP (アプリケーション保護ポリシー) をサポートしていないアプリについてのみ、データ転送の例外を追加してください。 また、データ漏えいのリスクとは見なされないアプリについてのみ、例外を追加してください。

Intune アプリケーション保護ポリシーで、 **[このアプリから他のアプリにデータを転送できるようにする]** を **[ポリシーで管理されているアプリ]** に設定すると、アプリが Intune で管理されているアプリにのみデータを転送できることを意味します。 Intune アプリをサポートしていない特定のアプリへのデータ転送を許可する必要がある場合は、 **[除外するアプリを選択します]** を使用してこのポリシーの例外を作成できます。 除外すると、Intune で管理されるアプリケーションは、URL プロトコル (iOS) またはパッケージ名 (Android) に基づいて、管理されていないアプリケーションを起動できます。 既定では、Intune の例外一覧には、重要なネイティブ アプリケーションが追加されています。 

> [!NOTE]
> データ転送ポリシーの例外を変更または追加しても、切り取り、コピー、貼り付けの制限など、他のアプリ保護ポリシーには影響しません。 

## <a name="ios-data-transfer-exceptions"></a>iOS データ転送の例外
iOS/iPadOS をターゲットとするポリシーの場合、URL プロトコルでデータ転送の例外を構成できます。 例外を追加するには、アプリの開発者が提供するドキュメントを参照して、サポートされている URL プロトコルに関する情報を確認してください。 iOS/iPadOS のデータ転送の例外の詳細については、[「iOS アプリ保護ポリシー設定」の「データ転送の除外対象」](app-protection-policy-settings-ios.md#data-transfer-exemptions)を参照してください。

> [!NOTE]
> Microsoft では、サード パーティ製のアプリケーションに対してアプリの例外を作成するための URL プロトコルを手動で検索する方法を用意していません。 

## <a name="android-data-transfer-exceptions"></a>Android のデータ転送の例外
Android をターゲットとするポリシーの場合、アプリ パッケージ名でデータ転送の例外を構成できます。 例外を追加するアプリの **Google Play** ストア ページで、アプリのパッケージ名を検索することができます。 Android のデータ転送の例外の詳細については、[「Android アプリ保護ポリシー設定」の「データ転送の除外対象」](app-protection-policy-settings-android.md#data-transfer-exemptions)を参照してください。


>[!TIP]
> Google Play ストアでアプリを参照して、アプリのパッケージ ID を確認できます。 パッケージ ID は、アプリのページの URL に含まれます。 たとえば、Microsoft Word アプリのパッケージ ID は **com.microsoft.office.word** です。

### <a name="example"></a>例
**Webex** パッケージを MAM データ転送ポリシーの例外として追加すると、管理対象の Outlook 電子メール メッセージ内の Webex リンクを Webex アプリケーションで直接開くことができるようになります。 他の管理対象ではないアプリではデータ転送が制限されます。

- iOS/iPadOS **Webex** の例: **Webex** アプリを除外対象にして、Intune の管理対象アプリから呼び出すことができるようにするには、<code>wbx</code> という文字列についてデータ転送の例外を追加する必要があります。
    
- iOS/iPadOS **Maps** の例: ネイティブ **Maps** アプリを除外対象にして、Intune の管理対象アプリから呼び出すことができるようにするには、<code>maps</code> という文字列についてデータ転送の例外を追加する必要があります。

- Android **Webex** の例: **Webex** アプリを除外対象にして、Intune の管理対象アプリから呼び出すことができるようにするには、<code>com.cisco.webex.meetings</code> という文字列についてデータ転送の例外を追加する必要があります。
    
- Android **SMS** の例: ネイティブ **SMS** アプリを除外対象にして、異なるメッセージング アプリと Android デバイス全体で Intune の管理対象アプリから呼び出すことができるようにするには、次の文字列についてデータ転送の例外を追加する必要があります。 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

- Android **証明書インストーラー**の例:Outlook for Android で S/MIME 証明書 (電子メール添付として配信される) を Android KeyStore にインストールできるようにネイティブの**証明書インストーラー** アプリを除外するには、文字列 <code>com.android.certinstaller</code> のデータ転送例外を追加する必要があります。 詳細については、[iOS/iPadOS および Android 向け Outlook の秘密度ラベルと保護](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/sensitive-labeling-and-protection-outlook-for-ios-android)に関する記事をご覧ください。

## <a name="next-steps"></a>次のステップ

- [アプリ保護ポリシーを作成して展開する](app-protection-policies.md)
- [「iOS アプリ保護ポリシー設定」の「データ転送の除外対象」](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [「Android アプリ保護ポリシー設定」の「データ転送の除外対象」](app-protection-policy-settings-android.md#data-transfer-exemptions)
