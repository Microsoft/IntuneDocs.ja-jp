---
title: アプリのデータ転送ポリシーの例外
titleSuffix: Microsoft Intune
description: Intune モバイル アプリケーション管理 (MAM) データ転送ポリシーの例外を作成します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1910334093a416933912c9cdeedac85e36d66e92
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>Intune モバイル アプリケーション管理 (MAM) データ転送ポリシーの例外を作成する方法

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

管理者の場合、Intune モバイル アプリケーション管理 (MAM) データ転送ポリシーの例外を作成することができます。 例外を使用すると、管理対象アプリとの間でデータをやりとりできる管理対象ではないアプリを指定できます。 管理者が例外一覧に追加した管理対象ではないアプリは、IT 部門に信頼されている必要があります。 

>[!WARNING] 
> 管理者は、データ転送の例外ポリシーを変更する責任があります。 管理対象ではないアプリ (Intune によって管理されていないアプリケーション) は、このポリシーに追加すると、管理対象アプリによって保護されているデータにアクセスできるようになります。 このような保護されたデータのアクセスで、データ セキュリティの漏えいが発生する可能性があります。 組織で使用する必要があり、Intune APP (アプリケーション保護ポリシー) をサポートしていないアプリについてのみ、データ転送の例外を追加してください。 また、データ漏えいのリスクとは見なされないアプリについてのみ、例外を追加してください。

この機能は、データ転送が**管理対象アプリのみ**に設定されている Intune アプリケーション保護ポリシーを作成する場合に適用されます。 データ転送ポリシーを**管理対象アプリのみ**に設定すると、作成した例外以外については、やはりデータ転送が Intune で管理されているアプリだけに制限されます。 プロトコル (iOS) またはパッケージ (Android) を使って制限を作成することができます。

この機能を構成して、Intune MAM アプリケーション保護ポリシーの**データ転送を制限する**の例外を有効にすることができます。 このポリシーは、Intune APP をサポートしていないアプリにデータを転送する場合にのみ必要です。 このポリシーは、データ転送設定が**管理対象アプリのみ**に設定され、Intune によって管理されているアプリケーションに対して、URL プロトコル (iOS) またはパッケージ名 (Android) に基づいて管理対象ではないアプリケーションを呼び出すことを許可します。 Intune の既定の例外一覧には、重要なネイティブ アプリケーションが追加されています。 

## <a name="ios-data-transfer-exceptions"></a>iOS データ転送の例外
iOS をターゲットとするポリシーの場合、URL プロトコルでデータ転送の例外を構成できます。 例外を追加するには、アプリの開発者が提供するドキュメントを参照して、サポートされている URL プロトコルに関する情報を確認してください。 iOS のデータ転送の例外の詳細については、[「iOS アプリ保護ポリシー設定」の「データ転送の除外対象」](app-protection-policy-settings-ios.md#data-transfer-exemptions)を参照してください。

## <a name="android-data-transfer-exceptions"></a>Android のデータ転送の例外
Android をターゲットとするポリシーの場合、アプリ パッケージ名でデータ転送の例外を構成できます。 例外を追加するアプリの **Google Play** ストア ページで、アプリのパッケージ名を検索することができます。 Android のデータ転送の例外の詳細については、[「Android アプリ保護ポリシー設定」の「データ転送の除外対象」](app-protection-policy-settings-android.md#data-transfer-exemptions)を参照してください。


>[!TIP]
> Google Play ストアでアプリを参照して、アプリのパッケージ ID を確認できます。 パッケージ ID は、アプリのページの URL に含まれます。 たとえば、Microsoft Word アプリのパッケージ ID は **com.microsoft.office.word** です。

### <a name="example"></a>例
**Webex** パッケージを MAM データ転送ポリシーの例外として追加すると、管理対象の Outlook 電子メール メッセージ内の Webex リンクを Webex アプリケーションで直接開くことができるようになります。 他の管理対象ではないアプリではデータ転送が制限されます。

- iOS の **Webex** の例: **Webex** アプリを除外対象にして、Intune の管理対象アプリから呼び出すことができるようにするには、<code>wbx</code> という文字列についてデータ転送の例外を追加する必要があります。

- Android の **Webex** の例: **Webex** アプリを除外対象にして、Intune の管理対象アプリから呼び出すことができるようにするには、<code>com.cisco.webex.meetings</code> という文字列についてデータ転送の例外を追加する必要があります。 

## <a name="next-steps"></a>次の手順

- [アプリ保護ポリシーを作成して展開する](app-protection-policies.md)
- [「iOS アプリ保護ポリシー設定」の「データ転送の除外対象」](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [「Android アプリ保護ポリシー設定」の「データ転送の除外対象」](app-protection-policy-settings-android.md#data-transfer-exemptions)
