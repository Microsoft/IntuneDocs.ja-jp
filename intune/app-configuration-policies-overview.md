---
title: "Intune 用アプリ構成ポリシー | Microsoft Docs"
titlesuffix: Azure portal
description: "Intune 用アプリ構成ポリシーを使用する方法について説明します。"
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 727bf031a9e8a4c761d8d7b0c1d2737398a0fb7e
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="app-configuration-policies-for-intune"></a>Intune 用アプリ構成ポリシー

ユーザーが Microsoft Intune でアプリ構成ポリシーと共に iOS または Android アプリを実行するときの設定を指定します。 たとえば、アプリは次の内容を指定することをユーザーに要求することがあります。

- カスタム ポート番号。
- 言語設定。
- セキュリティ設定。
- 会社のロゴなどのブランドの設定。

ユーザーがこれらの設定を誤って入力すると、ヘルプ デスクの負荷が増加し、新しいアプリの採用が遅くなる可能性もあります。

アプリ構成ポリシーを使用すると、ユーザーがアプリを実行する前にこれらの設定をポリシー内のユーザーに割り当てることができるため、上記の問題を排除するのに役立ちます。 設定が自動的に指定されるため、ユーザーの操作は不要です。

これらのポリシーをユーザーとデバイスに直接割り当てないでください。 代わりに、ポリシーをアプリに関連付け、そのアプリを割り当てます。 ポリシー設定は、アプリがポリシーを確認する際に (通常は初めて実行したときに) 必ず使用されます。

Intune でアプリ構成を使用する方法には 2 つの選択肢があります。
 - **管理対象デバイス**  
   デバイスは、Intune で MDM (モバイル デバイス管理) プロバイダーとして管理されます。
 - **管理対象アプリ**  
   アプリはデバイスの登録なしで管理されます。

## <a name="apps-that-support-app-configuration"></a>アプリ構成をサポートするアプリ

サポートするアプリにアプリ構成ポリシーを使用できます。 Intune でアプリ構成をサポートするには、アプリ構成の使用をサポートするようにアプリが記述されている必要があります。 詳細については、アプリのベンダーに問い合わせてください。

Intune App SDK をアプリに組み込むか、アプリの開発後にラップして、基幹業務アプリを準備することができます。 iOS と Android の両方で使用可能な Intune App SDK で、Intune アプリ保護ポリシーに対してご使用のアプリを有効にすることができます。 アプリの開発者が必要なコード変更が最小限に抑えられます。 詳細については、「[Intune App SDK の概要](app-sdk.md)」を参照してください。

## <a name="graph-api-support-for-app-configuration"></a>Graph API のアプリ構成のサポート

アプリ構成タスクは、Graph API でも実行することができます。 詳細については、[Graph API のリファレンスの MAM を対象とした構成](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create)に関するページを参照してください。

## <a name="next-steps"></a>次のステップ

### <a name="managed-devices"></a>管理対象デバイス

 - iOS デバイスでアプリ構成を使用する方法について学びます。  「[管理対象の iOS デバイス用アプリ構成ポリシーを追加する](app-configuration-policies-use-ios.md)」を参照してください。
 - Android デバイスにアプリ構成を使用する方法について学びます。  「[管理対象の Android デバイス用アプリ構成ポリシーを追加する](app-configuration-policies-use-android.md)」を参照してください。

### <a name="managed-apps"></a>Managed apps

 - 管理対象アプリにアプリ構成を使用する方法について学びます。 「[デバイス登録なしで管理対象アプリ用アプリ構成ポリシーを追加する](app-configuration-policies-managed-app.md)」を参照してください。