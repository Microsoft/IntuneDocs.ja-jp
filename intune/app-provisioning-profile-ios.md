---
title: "Microsoft Intune での iOS アプリ プロビジョニング プロファイル"
titlesuffix: 
description: "Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルを事前に割り当てるツールが用意されています。\""
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7637dcb3aba4f46a3e97c8de47d974b46af27b47
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="use-ios-mobile-provisioning-profiles-in-intune-to-prevent-your-apps-from-expiring"></a>Intune で iOS モバイル プロビジョニング プロファイルを使用して、アプリが期限切れにならないようにする

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>概要

iPhone および iPad に割り当てられた Apple iOS 基幹業務アプリは、含まれるプロビジョニング プロファイルおよび証明書で署名されたコードで構築されます。 アプリを実行すると、iOS は iOS アプリの整合性を確認し、プロビジョニング プロファイルで定義されたポリシーを適用します。 次の検証が行われます。

- **インストール ファイルの整合性** - iOS は、アプリの詳細と、エンタープライズ署名証明書の公開キーを比較します。 これらが異なる場合はアプリの内容が変更されている可能性があり、アプリは実行を許可されません。
- **機能の強制** - iOS は、アプリのインストール (.ipa) ファイルに含まれる、(個々の開発者プロビジョニング プロファイルではなく) エンタープライズ プロビジョニング プロファイルからアプリの機能の適用を試行します。


アプリの署名に使用するエンタープライズ署名証明書は、通常 3 年間は継続します。 ただし、プロビジョニング プロファイルは 1 年後に期限が切れます。 証明書が有効である期間中、Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルを事前に割り当てるツールが用意されています。
証明書の期限が切れると、新しい証明書を使用してアプリを再び署名して、新しい証明書のキーを持つ新しいプロビジョニング プロファイルを埋め込む必要があります。


## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>iOS モバイル アプリ プロビジョニング プロファイルを作成する方法

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[モバイル アプリ]** を選びます。
1.  **[モバイル アプリ]** ワークロードで、**[管理]** > **[iOS アプリ プロビジョニング プロファイル]** の順に選択します。
2.  プロファイルの一覧ウィンドウで、**[プロファイルの作成]** を選択します。
3. **[プロファイルの作成]** ウィンドウで、次の値を構成します。
    - **名前** - このモバイル プロビジョニング プロファイルの名前を指定します。
    - **説明** - 必要に応じて、ポリシーの説明を指定します。
    - **プロファイル ファイルのアップロード** - **[インポート]** を選択し、Apple Developer Web サイトからダウンロードした Apple モバイル構成プロファイル ファイル (拡張子 **.mobileprovision**) を選択します。
4. 終了したら、**[作成]** を選択します。

## <a name="next-steps"></a>次の手順

必要な iOS デバイスにプロファイルを割り当てます。 詳細については、「[デバイス プロファイルを割り当てる方法](device-profile-assign.md)」の手順をご覧ください。
