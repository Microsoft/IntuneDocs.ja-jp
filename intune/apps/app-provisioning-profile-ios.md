---
title: Microsoft Intune での iOS アプリ プロビジョニング プロファイル
titleSuffix: ''
description: Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルを事前に割り当てるツールが用意されています。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 31bad59c33a34d0b92d93979b20b58f70fd042ef
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564096"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>iOS アプリ プロビジョニング プロファイルを使用して、アプリが期限切れにならないようにする

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

## <a name="introduction"></a>概要

iPhone および iPad に割り当てられた Apple iOS 基幹業務アプリは、含まれるプロビジョニング プロファイルおよび証明書で署名されたコードで構築されます。 アプリを実行すると、iOS は iOS アプリの整合性を確認し、プロビジョニング プロファイルで定義されたポリシーを適用します。 次の検証が行われます。

- **インストール ファイルの整合性** - iOS は、アプリの詳細と、エンタープライズ署名証明書の公開キーを比較します。 これらが異なる場合はアプリの内容が変更されている可能性があり、アプリは実行を許可されません。
- **機能の強制** - iOS は、アプリのインストール (.ipa) ファイルに含まれる、(個々の開発者プロビジョニング プロファイルではなく) エンタープライズ プロビジョニング プロファイルからアプリの機能の適用を試行します。


アプリの署名に使用するエンタープライズ署名証明書は、通常 3 年間は継続します。 ただし、プロビジョニング プロファイルは 1 年後に期限が切れます。 証明書が有効である期間中、Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルを事前に割り当てるツールが用意されています。
証明書の期限が切れると、新しい証明書を使用してアプリを再び署名して、新しい証明書のキーを持つ新しいプロビジョニング プロファイルを埋め込む必要があります。

管理者は、セキュリティ グループを追加/除外することで、iOS アプリ プロビジョニング構成を割り当てることができます。 たとえば、すべてのユーザーに iOS アプリ プロビジョニング構成を割り当て、エグゼクティブ グループのみ除外することができます。

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>iOS モバイル アプリ プロビジョニング プロファイルを作成する方法

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[iOS アプリ プロビジョニング プロファイル]**  >  **[プロファイルの作成]** を選択します。
3. **[基本]** ページで、次の値を追加します。
    - **名前** - このモバイル プロビジョニング プロファイルの名前を指定します。
    - **説明** - 必要に応じて、ポリシーの説明を指定します。
    - **プロファイル ファイルのアップロード** - **[開く]** アイコンを選択し、[Apple Developer Web サイト](https://developer.apple.com/)からダウンロードした Apple モバイル構成プロファイル ファイル (拡張子 `.mobileprovision`) を選択します。

   **[有効期限]** は、上記で追加した Apple モバイル構成プロファイル ファイル内の値から設定されます。<br>

   <img alt="Create profile - Basics" src="~/apps/media/app-provisioning-profile-ios/app-provisioning-profile-ios-01.png">

4. **[次へ]:[スコープ タグ]** をクリックします。<br>
   **[スコープ タグ]** ページでは、必要に応じて、スコープ タグを構成することにより Intune で iOS アプリ プロビジョニング プロファイルを表示できるユーザーを決定できます。 スコープのタグの詳細については、[分散 IT のためのロールベースのアクセス制御とスコープのタグの使用](../fundamentals/scope-tags.md)に関するページをご覧ください。
5. **[次へ]:[割り当て]** をクリックします。<br>
   **[割り当て]** ページでは、ユーザーとデバイスにプロファイルを割り当てることができます。 デバイスが Intune で管理されているかどうかに関係なく、デバイスにプロファイルを割り当てることができることに注意してください。このことは重要です。
6. **[次へ]:[確認と作成]** をクリックして、プロファイルに対して入力した値を確認します。
7. 終了したら、 **[作成]** をクリックして、Intune で iOS アプリ プロビジョニング プロファイルを作成します。 

## <a name="next-steps"></a>次の手順

必要な iOS デバイスにプロファイルを割り当てます。 詳細については、「[デバイス プロファイルを割り当てる方法](../device-profile-assign.md)」の手順をご覧ください。
