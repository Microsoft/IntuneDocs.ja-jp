---
title: Microsoft Intune によって管理されるデバイスの登録オプション
titleSuffix: ''
description: Microsoft Intune によって管理されるデバイスに対して管理者が設定できる登録オプションの一覧。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: cf4ad6d4-423f-4826-ab8d-6eb7a7cfb559
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 441ae9549ef6fda093a69268b5aa698b9c6855c5
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57390230"
---
# <a name="enrollment-options-for-devices-managed-by-intune"></a>Intune によって管理されるデバイスの登録オプション

Intune 管理者は、ユーザーのためにデバイスを登録して Intune の機能を有効にすることができます。  Intune には次の登録オプションが含まれています。

## <a name="terms-and-conditions"></a>Intune の登録および会社アクセスに関する使用条件

ユーザーが会社の使用条件に同意しないと、ポータル サイトで自分のデバイスの登録や会社のアプリや電子メールなどのリソースへのアクセスができないという要件を設定できます。 使用条件の構成は任意です。 [使用条件](terms-and-conditions-create.md)について詳しくはこちらをご覧ください。

## <a name="enrollment-restrictions"></a>登録制限

次の条件でデバイスの登録を制限することができます。
- デバイスのプラットフォーム
- ユーザーごとのデバイスの数
- 個人デバイスのブロック

[登録の制限](enrollment-restrictions-set.md)について詳しくはこちらをご覧ください。

## <a name="enable-apple-device-enrollment"></a>Apple のデバイス登録を有効にする

iOS および macOS デバイスの登録には、MDM プッシュ証明書が必要です。 [MDM プッシュ証明書](apple-mdm-push-certificate-get.md)について詳しくはこちらをご覧ください。

## <a name="corporate-identifiers"></a>企業 ID

International Mobile Equipment Identifier (IMEI) 番号とシリアル番号を一覧表示して、会社が所有するデバイスを識別できます。 [企業 ID](corporate-identifiers-add.md) について詳しくはこちらをご覧ください。
## <a name="multi-factor-authentication"></a>Multi-Factor Authentication

ユーザーがデバイスを登録するとき、スマートフォン、PIN、生体認証データなど、追加の検証方法を使用するようにユーザーに要求できます。 多要素認証については[こちら](multi-factor-authentication.md)をご覧ください。

## <a name="device-enrollment-manager"></a>デバイス登録マネージャー
ユーザーをデバイス登録マネージャーにすることができます。  DEM ユーザーは、単一のユーザー アカウントで多数のモバイル デバイスを登録できます。 デバイス登録マネージャー (DEM) アカウントは、最大で 1,000 台のデバイスを登録できます。 [デバイス登録マネージャー](device-enrollment-manager-enroll.md)について詳しくはこちらをご覧ください。

## <a name="device-categories"></a>デバイス カテゴリ

デバイス カテゴリを使うと、定義したカテゴリに基づいてデバイスをグループに自動的に追加できます。 デバイスをグループに整理すると、デバイスを管理しやすくなります。 [デバイス カテゴリ](device-group-mapping.md)について詳しくはこちらをご覧ください。
