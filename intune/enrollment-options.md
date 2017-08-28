---
title: "Intune の登録オプション"
description: 
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cf4ad6d4-423f-4826-ab8d-6eb7a7cfb559
ms.openlocfilehash: 3514b580a4e35cc9e0813d6dd7fd0e1eee550d7c
ms.sourcegitcommit: af013af8d9a63c9aa16e5e9eddf38ad9c5a77898
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/12/2017
---
# <a name="enrollment-options-for-intune"></a>Intune の登録オプション

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
