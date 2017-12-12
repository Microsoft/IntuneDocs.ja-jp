---
title: "アプリのプロビジョニング プロファイル"
titlesuffix: Azure portal
description: "Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルを事前に割り当てるツールが用意されています。\""
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 05/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2b58fb0d9b69e875736b5d2ea884ae9d3453b481
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="use-ios-mobile-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>iOS モバイル プロビジョニング プロファイルを使用して、アプリが期限切れにならないようにする

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>概要

iPhone および iPad に割り当てられた Apple iOS 基幹業務アプリは、含まれるプロビジョニング プロファイルおよび証明書で署名されたコードで構築されます。 アプリを実行すると、iOS は iOS アプリの整合性を確認し、プロビジョニング プロファイルで定義されたポリシーを適用します。 次の検証が行われます。

- **インストール ファイルの整合性** - iOS は、アプリの詳細と、エンタープライズ署名証明書の公開キーを比較します。 これらが異なる場合はアプリの内容が変更されている可能性があり、アプリは実行を許可されません。
- **機能の強制** - iOS は、アプリのインストール (.ipa) ファイルに含まれる、(個々の開発者プロビジョニング プロファイルではなく) エンタープライズ プロビジョニング プロファイルからアプリの機能の適用を試行します。


アプリの署名に使用するエンタープライズ署名証明書は、通常 3 年間は継続します。 ただし、プロビジョニング プロファイルは 1 年後に期限が切れます。 証明書が有効である期間中、Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルを事前に割り当てるツールが用意されています。
証明書の期限が切れると、新しい証明書を使用してアプリを再び署名して、新しい証明書のキーを持つ新しいプロビジョニング プロファイルを埋め込む必要があります。


## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>iOS モバイル アプリ プロビジョニング プロファイルを作成する方法

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[モバイル アプリ]** を選択します。
1.  **[Mobile Apps]** ワークロードで、**[管理]**、**[iOS プロビジョニング プロファイル]** の順に選択します。
2.  プロファイルの一覧ブレードで、**[プロファイルの作成]** を選択します。
3. **[プロファイルの作成]** ブレードで、次の値を構成します。
    - **名前** - このモバイル プロビジョニング プロファイルの名前を指定します。
    - **説明** - 必要に応じて、ポリシーの説明を指定します。
    - **プロファイル ファイルのアップロード** - **[インポート]** を選択し、Apple Developer Web サイトからダウンロードした Apple モバイル構成プロファイル ファイル (拡張子 **.mobileprovision**) を選択します。
4. 終了したら、**[作成]** を選択します。

## <a name="next-steps"></a>次のステップ

必要な iOS デバイスにプロファイルを割り当てます。 詳細については、「[デバイス プロファイルを割り当てる方法](device-profile-assign.md)」の手順をご覧ください。
